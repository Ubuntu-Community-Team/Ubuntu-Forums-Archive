---
title: "can't log on  uesing wireless"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by ntos on 2009-03-22
:p hello i am having a problem with wireless i can see my network  but can't log on and did some checking on posts and see that there is a fix in wicd sourceforge.net/download.php i tried what there saying on the page the synaptic package manager. settings/repositories/third-party/add is grayed out. i have ubuntu 8.10 and need a key .any help. p.s wired is fine.thank you

---

### Post by M70JRD on 2009-03-22
Hi

I had a similar problem with 8.04, it would work with no encryption, but as soon as I tried WEP or WPA it would not connect. Having tried WICD and NDIS Wrapper with no success, I resorted to the adaptors. My Neatgear and USR would not work but an unbranded one does and works perfectly everytime. I believe that it is down to the chipset type in the adaptor and how it passes through the security. Lastly I found that it worked best when Ubuntu is clean installed whilst the adaptor is connected.
There is a site with some details [http://tldp.org/HOWTO/Hardware-HOWTO/](http://tldp.org/HOWTO/Hardware-HOWTO/)

Hope this helps

John

---

### Post by ntos on 2009-03-23
hello trying to in stall inf files to ndiswrapper  i put inf  sys  files in a folder in the home folder cold divers .now i ran the terminal.with this cd drivers. sudo ndiswrapper -i *****.inf.then i get this couldn't open *****.inf on such file or directory at/usr/sbin/ndiswrapper-1.9 line 219. so is there away to install the inf in the /usr with the terminal.i tried to copy and paste ala windows that doesn't work its right protected. thank you in advance . ntos

---

