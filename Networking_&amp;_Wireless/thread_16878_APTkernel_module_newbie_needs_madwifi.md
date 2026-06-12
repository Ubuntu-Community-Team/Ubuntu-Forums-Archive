---
title: "APT/kernel module newbie needs madwifi"
date: 2005-02-24
forum: Networking &amp; Wireless
---

### Post by jtopping on 2005-02-24
I am a linux "user" of several years, but I have been babied by distros such as mandrake. While ubuntu isnt very hard, I have run into a huge problem with it detecting my atheros wireless card.

I have the AMD64 ubuntu warty installed on my AMD64 box, but the installer did not detect my Netgear 311t(Atheros-based) WLAN card. Suse 9.2 detects it just fine.

From what i can tell, the AMD64 version of warty does not include madwifi modules(to support my atheros WLAN PCI card) However, I have read that the restricted kernel modules apt package includes the madwifi drivers, but I do not have an internet connection on this computer, outside of the wireless.

So, reading on, I found that I can download the debs on another computer, put them onto my new ubuntu box and add the directory they are in as a apt source. Could someone help me add something like /home/<user> as a source for apt-ing the restricted modules?

And after i get that source loaded, and I apt the modules...what will I have to do to get them installed such that it is detected at bootup?


Forgive my newbness, I know linux fairly well(just enough to hurt something) but know nothing of apt, as I have never used a debian-esque distro, and I know nothing of driver installation, as I have been babied not to learn...

---

