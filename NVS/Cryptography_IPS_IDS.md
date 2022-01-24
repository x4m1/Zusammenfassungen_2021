## Network Security

Network Security focuses on these points:

- how network can be attacked
- how we can defend
- design architecture that are immune to attacks

> Internet was not designed to be secure at the begining



### Malware

**Virus:**

- not self-replicating

- infection by receiving/executing code

**Worm:**

- self-replicatiing
- infection by passively receiving object

**Spyware malware**:

- Can record keystrokes
- Websites visited
- Can be used for a botnet

### DoS

Attackers make resources unavailable to others by overwehelming resource with bogus traffic



### **Packet sniffing**

Promiscous network interface reads/records all packets passing by.

E.g.: Wireshark

### **Ip spoofing**

Send packet with false source address.



## Disirable Properties

**CIA ++:** 
**C**-confidentiality : only sender, intended receiver should "understand" message

**I**-integrety: sender, receiver want to ensure message not altered (summing,hashing)

**A**-authentication: sender, receiver want to confirm identity to each other

**+** acess and availability: services must be accessible to users; DoS attacks

**+** operational security



## Principles of cryptography

m = message (plain text)

K_a(m) = ciphertext, encrypted with key "K_a"

m = K_b(K_a(m))



### How to break encryption schemes

- cipher-text only attack: analyze ciphertext
- known-plaintext attack: plaintext corresponding to ciphertext
- chosen-plaintext attack: can get ciphertext for chosen plaintext
- brute force
- statistical analysis

## DES

- US encryption standard (NIST 1993)
- 56-bit symmetric key, 64-bit plaintext input (blocks)
- block cipher with cipher block chaining
- polyalphabetic cipher
- Security? Bruteforce in less than a day

How to make it more secure?

- 3DES : encrypt 3 times with 3 different keys



## AES

- Symmetric-key NISZ standard
- block cipher
- polyalphabetic cipher
- processes data in 128 bit blocks
- 128, 192 or 256 bit keys
- brute force is not possible



## Symmetric Cryptography

- sender and receiver share same secret key
- fast 
- How to agree on shared secret key?

## Asymmetric Cryptography

- sender, receiver do not share secret key
- public encryption key is known to all
- private decryiption key known only to receiver

m.. message

Kb+(m) = ciphertext

m = Kb-(Kb+(m))



### Requirements

1. need KB+(*) and KB-(*) such that:

   KB-(KB+(M)) = m = KB+(KB-(m))

2.  given public key KB+, it should be impossible to compute private key KB-



## RSA 

Creating public/private key:

1. choose two large prime numbers p, q.
   (e.g., 1024 bits each)

2. compute n = pq, z = (p-1)(q-1)
3. choose e (with e<n) that has no common factors
with z (e, z are “relatively prime”).
4. choose d such that ed-1 is exactly divisible by z.
(in other words: ed mod z = 1 ).
5.  public key is (n,e). private key is (n,d).

Important Property:

KB-(KB+(m)) = m = KB+(KB-(m))





## Purpose of Public key

- Signatures can be verified with the public key

  

## Purpose of Private key

- private key can be used to encrypt message

- privaze key can be used to sign message

  

## Hashing/ Message Digest

Problem/Goals:

- problem:computationally expesive to public-ley ecrypt long messages
- goal: fixed-length, easy-to-compute "fingerprint"
- goal:apply hash func H to m and get fixed size message

Hash funcs properties:

- many to 1
- produces fixes-size msg digest
- given message digest x, computationally infeasible to find m such that x = H(m)



## Digital Signature

- sender digitally signs docuemnt, estab,lishing he is the document owner
- verifable, nonfrgetable

Bob sings me by ecrypting with his private key KB-,creating signed message

Alice verifies that m signed by Bob applying Bobs public key and checks

KB+(KB-(m)) = m



## IDS

 Systems for the prompt detection of intrusion in computer systems 

They are passive!

Features:

- capture data
- detect attacks (and enables tracing),
- trigger alarms.

A major problem with the practical use of IDS is that they either
generate many false alerts (false positives) or fail to detect some attacks (false negatives).



### Host-based IDS -HIDS

- use host sensors
- evaluate log files
- require auditing agents at the host
- run on production systems (OS + NW)
- observe network traffic at the host.

### NW-based IDS -NIDS

- Network sensors

- run on separate infrastructure (OS + NW)

- observe network traffic on the network.
  Analysis methods:

  

  **Signature analysis - detect only known attacks**

- Anomaly detection - detect also previously unknown attacks

  Policy-based anomalies - policies are defined for types of NW devices
  Honeypot-based - it is anomalous if the honey pot is accessed

- Statistical methods - correlation methods, AI, machine learning, neural networks - detect
attacks that are staggered in time and distributed locally via sensors.
AI and machine learning learn from past attacks and improve detection.



## IPS

Systems for automatic prevention of instrusion in computer systems,set countermeasures - are actively!

Features:

- discard data packets
- interrupt connections
-  change the transmitted data.

- Incident Response: includes the technical-organizational handling of detected events,
e.g. escalation processes.
- NW Monitoring: measures and monitors operating states (utilization, ...).

IPSs, on the other hand, are designed to automatically initiate countermeasures once an attack has been detected.
Instead of just triggering an alarm, like an IDS, an IPS/ IRS is able to:


Various actions can be triggered in response to detected events:

- Documentation of the event (also IDS)
- alerting (also IDS)
- automatic activation of countermeasures (IPS/ IRS).


## Honeypots

A honeypot is designed to distract an attacker from the real target (production systems) and is intended to draw him into
an area that costs him time and makes his early detection possible.
Honeypots act as bait and are designed to attract attackers with their attractiveness. Thereby also new attack methods can be learned.

