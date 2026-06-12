---
title: "Problem playing DVD's"
date: 2008-07-14
forum: Multimedia Software
---

### Post by espressobeanies on 2008-07-14
I cannot play my DVD in Totem. It says it doesn't have the correct plugin. So I removed it and use VLC. When I open it, the video is all choppy and artifacted. It doesn't work. I use VLC emulated under Wine, and I can see it very clearly, but I can't get back to Ubuntu. What is the problem?

---

### Post by Sn3ipen on 2008-07-14
Ubuntu don't have dvd support as standard because of some patents and legal rights in the us and some other countries. so you have to install it manually. Assuming that you are using Hardy you should do this:
Open a Terminal and type:
```
sudo gedit /etc/apt/sources.list
```
Paste at the end:
```
## Medibuntu - Ubuntu 8.04 "hardy" 
## Please report any bug on https://bugs.launchpad.net/medibuntu/ 
deb http://packages.medibuntu.org/ hardy free non-free
```
save and close then type:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update 
sudo apt-get install libdvdcss2
```

This should install the correct codecs for you.

---

### Post by espressobeanies on 2008-07-14
Okay. I did that and I got this error message:

W: GPG error: [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB53C4079072870B
W: You may want to run apt-get update to correct these problems
dave@swim4life:~$ sudo apt-get install libdvdcss2


Yes I am running Hardy Heron.

---

### Post by jre on 2008-07-14
This is a unrelated error message.
To get rid of it anyway you have to add the gpg key from that repository to your apt key database. Have a look at [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) for instructions.

---

### Post by espressobeanies on 2008-07-14
Oh, okay. Sorry I didn't see that advanced stuff. I did those instructions, but now VLC doesn't show anything. It just crashes or exits when I try to play from DVD or DVD Menu. I reinstalled Totem, and downloaded the Gstreamer extra plugins, but it says it cannot play from the resource. I'm not sure what else is wrong. I am using the Nvidia Hardware Driver.

---

### Post by Sn3ipen on 2008-07-15
Have you tried using another dvd?

---

