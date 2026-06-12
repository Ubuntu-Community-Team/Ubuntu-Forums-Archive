---
title: "Can't download over LAN with wired connection"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by Hashmere on 2010-07-20
Hey everyone,

Hope someone here can help me out. I'm running 10.04 and am having a strange problem. I have an NAS device (Synology 210j) attached to my LAN via ethernet, and my laptop is also attached via ethernet. I have the NAS device mapped using FTP and all the sudden am unable to download from my NAS. It downloads about 200kb then freezes. I am able to upload using the same mapping to the NAS with no problem. About a week ago, everything worked fine, and too my knowledge I have not changed anything.

I have tried FTP'ing through the command line and have the same result. I am able to download fine over wireless, and in Windows 7 everything works fine.

I also have access to the NAS over the internet, and when I map the internet address, everything works fine.

Please let me know if I can provide any more information. 

TL;DR: I can't download files from my NAS device when in Linux, with a wired LAN Connection.

---

### Post by Hashmere on 2010-07-21
Bump from Page 5. 

Does anyone even have any recommendations to try? Anything at all?

---

### Post by cariboo on 2010-07-22
A really simple thing to check is if they computer and the NAS are both in the same netblock.

---

### Post by Hashmere on 2010-07-22
cariboo907,

Thank you for the suggestion. If you are speaking of the subnet, then yes both devices are in the same subnet. I can access the NAS over wired, just not download file from it.

---

