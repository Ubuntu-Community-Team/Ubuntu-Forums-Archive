---
title: "Sharing files on network"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by Achel4Ever on 2011-12-16
Hello,

I have a laptop and a desktop, both running KDE. 
All I want to do is connect them through a network, so I can move files from 1 to the other. 
I was searching the internet a lot, and find out the easiest way should be with SAMBA (which I don't understand since everywhere it's said Samba is for windows?). 
Both computer have the same user name and password.
I shared a folder with SAMBA on both computer. On both PC I have the same problem. With Dolphin I browse to the shared directory if I want to open it, it ask me for a username and password, whatever I put there I can not connect.

I realize it might be a stupid question, but can anybody please tell me how I can get files the easiest way from one PC to the other. 

thanks a lot.

---

### Post by Buntumatic on 2011-12-16
UNIX native way is NFS. Setting it up is fairly easy, I'm sure there are thousands of good tutorials in Google. SAMBA/CIFS will do, too, although it's not needed when Windows is not involved.
Note, with simple NFS setup you need matching UID's on both (all) participating computers. For instance, if your UID in your computer is 1001 and your wife's UID in her computer is 1001 then her files appear as yours over NFS.

---

