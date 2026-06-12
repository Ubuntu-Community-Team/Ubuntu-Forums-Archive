---
title: "Please Help: 802.1X Authentication for LAN (wired connection)"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by fatfatwolf on 2010-03-15
Hi everyone:
  I am using ubuntu in my new office, and I can't get the network working. The "official" OS installed was a Windows, and it has a special "dial-up" app for the LAN connection (not wireless). My network admin is apparently not helpful, since he actually knows nothing about the internals for the "dial-up" app (he did not even ever heard of TTLS, PEAP, MD5, etc), and claimed that no OS except for Windows can work...

Well, I have tested various configurations with my Mac laptop, and apparently the LAN connection requires 802.1X authentication, and it's using a very weird combination "TTLS+PEAP+MD5" (if I check these options in Mac OS X, the connection works). However, in NetworkManager, I can't select both TTLS and PEAP, and moreover, TTLS does not work with MD5. So, is there anything I could try? Thanks in advance for any help.!!!

---

### Post by Brandon Williams on 2010-03-16
I think that TTLS+PEAP is redundant, since the P in PEAP stands for protected, and it always uses TTLS. That's my understanding anyway. Have you tried just selecting PEAP+MD5 in NetworkManager?

---

