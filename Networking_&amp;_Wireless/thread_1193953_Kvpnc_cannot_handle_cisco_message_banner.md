---
title: "Kvpnc cannot handle cisco message banner"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by tayran on 2009-06-22
Hi,

I am using Kvpnc for PPTP and cisco vpns for a while. Now i need connect to a cisco vpn again but this one has a banner asking to user whether he is sure to continue or to exit immediately. I have imported a pcf file for the connection and this way it works well in windows. I am suspecting of this banner in the beginning because in windows the cisco vpn client doesn't establish the connection until i click the continue button and in kubuntu i don't see any banners like this. Simply the connection times out after a period and it is not because of this period because i have tried with 50 secs. Still times out.

My system is:
Kubuntu Jaunty 9.04
Linux Kernel 2.6.30
KDE 4.2.2
Kvpn version is 0.9.0 (using KDE 3.5.10 it says!)
* same problem exists in Kvpn version 0.9.1 from source (KDE 4.2.2)

Thanks in advance

---

### Post by nonotford on 2010-01-03
I have the same issue. Interactive auth doesn't help either...

---

### Post by TomG on 2011-03-07
Any workaround for this ? :(

---

### Post by TomG on 2011-03-07
Problems seems not come form kvpnc  as I have the same from vpnc command line utility :

```
root@ubuntu:/etc/vpnc# vpnc
Enter password for user@vpn.*******.com: 
Connect Banner:
----------------------------------------------------------------------------
| This system must be used for approved business purposes only.

vpnc: no response from target
```

:(

---

