---
title: "Networking two computers to file share"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by Doctor1971 on 2009-06-28
Hi. I am a newby! Not for long I hope. I wish to network my laptop with my computer. I have a wireless modem which is hardwired to main computer running Ubuntu 8.04. My Laptop is using a usb wireless receiver running Linux Mint. 
How do I do this? And what further information do you need from me?

Thank you in advance!

---

### Post by 3rdalbum on 2009-06-28
It's exactly the same procedure for file sharing across wireless as it is for wired.

First, install the Samba package:

```
sudo apt-get install samba
```

When that's installed, right-click on the folder you want to share and go to Properties. Go to the Share tab.

Click "Share This Folder" and choose a name for the share that is not too long. Click "Allow other people to write in this folder". Then click "Create Share" and you're done.

If the desktop is the computer that is serving, then you might need to provide the desktop's username and password when logging in on the laptop. If this is not what you want, you can install the "system-config-samba" program on the desktop, that provides more options and greater flexibility in setting up shares.

---

