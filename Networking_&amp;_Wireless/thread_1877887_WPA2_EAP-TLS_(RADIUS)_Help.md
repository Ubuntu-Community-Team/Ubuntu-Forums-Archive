---
title: "WPA2 EAP-TLS (RADIUS) Help"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by yochaigal on 2011-11-08
Hi everybody!
I'm a fairly advanced sysadmin; I use Arch Linux at home and ubuntu in most of other cases.

Running xubuntu 11.10 on my work laptop (on a windows domain using centrify, though probably not relevant at the moment) - a Thinkpad T400.

My work uses a RADIUS server to handle wireless connectivity; in Windows and OS X connecting is a matter of providing a certificate+key to the OS (either in windows certifcate manager or in OS X login keychain).  
Note: OS X describes the network mode as EAP-TLS.  

I cannot get this to work in Xubuntu.  I've used WICD, Network-Manager, and simple wpa_supplicant - and I cannot get it to associate.

I created a wicd template that would allow me to choose a connection mode other than the default EAP-TLS which requires identity/passphrase, etc. I'm not at work at the moment so I don't have access to wicd logs but I can post them later. 

Network-Manager simply doesn't work; the "connect" button is completely grayed out until I complete all the non-relevant fields (username/password, for example).  

Details about the network: 
WPA2 AES (no passhprase), user certificate and key required.  

 
Basically, my question is: has anyone here successfully connected to an EAP-TLS network that does NOT use identity/username+password?  

Thanks!

---

