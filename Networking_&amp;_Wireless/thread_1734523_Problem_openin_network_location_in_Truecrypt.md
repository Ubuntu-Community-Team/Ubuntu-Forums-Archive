---
title: "Problem openin network location in Truecrypt"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by semsaudade on 2011-04-20
I have an encrypted file created with Truecrypt 7.0a on a network disk  (connected via usb to a Netgear N300 router). I am able to mount the  file from my Windows 7 pc, but the same operation is impossible on my  Ubuntu netbook and on a Mint Linux running on the same pc with Windows. I  always get the message: "Invalid argument: /media/samba_condividi/z",  where /media/samba_condividi/z is the path to the file on the mounted  network disk. 
 
This problem doesn't occur if I connect the same disk directly via usb  to the computer, so it should be definitely a network problem (but only  for linux, since in Windows mounting across network functions  correctly). 
 
Can anybody help me? Thank you very much!

---

### Post by oracle2b on 2011-04-20
ensure that you have smbfs installed.

> sudo apt-get install smbfs

cifs needs a username to be entered to gain access to the network share.

[https://help.ubuntu.com/community/MountWindowsSharesPermanently#cifs will not mount](https://help.ubuntu.com/community/MountWindowsSharesPermanently#cifs will not mount)

---

### Post by semsaudade on 2011-04-21
Thanks for your answer. Yes, smbfs is installed and network disk is correctly mounted at startup and shown in nautilus.

Any other suggestion?

---

