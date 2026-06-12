---
title: "Removed Kubuntu packages, now lost wireless."
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by joeblurton on 2009-04-06
Hello all, I'm running an x86 system with Ubuntu 8.10... I installed Kubuntu Desktop just to see what that was like, and decided I prefered GNOME. I deleted the Kubuntu stuff using Synaptic, but have lost the wireless manager somehow. Is this KDE related? Should it disappear when I delete KDE-only packages? What can I do to get it back. I have another computer to download things on, but without the wireless/network interface I don't know if I can bridge the connection to allow Ubuntu to download the necessary packages.

First off, is there anything I can do to sort this offline? What packages would I need?

Thank you in advance for any help... I'm not a total novice, but near as damnit!

---

### Post by kreggz on 2009-04-06
What happens if you type the following in Terminal?
```
NetworkManager
```

---

### Post by joeblurton on 2009-04-07
> **kreggz said:**
> What happens if you type the following in Terminal?
```
NetworkManager
```

At the moment, nothing. I have Network Tools in System > Administration, but nothing else. After I removed the kubuntu-desktop packages the wireless manager disappeared from the GNOME panel and now it seems like it's gone for good. Can I get this package on the box via USB or CD?

---

### Post by kreggz on 2009-04-07
In the terminal type:

```
sudo apt-get install NetworkManager
```

---

### Post by joeblurton on 2009-04-17
Hi all... I managed to fix it by finding the Network Manager .deb in the repositories, and shifted it over using a USB stick. Obviously, without Network Manager there was no way of using apt-get in Terminal, as there was no net connection to do this over. Thanks!

---

### Post by Ayuthia on 2009-04-17
> **joeblurton said:**
> Hi all... I managed to fix it by finding the Network Manager .deb in the repositories, and shifted it over using a USB stick. Obviously, without Network Manager there was no way of using apt-get in Terminal, as there was no net connection to do this over. Thanks!

Actually, you are able to get a net connection without NetworkManager.  Here is a link that will help show you how to connect via the Terminal:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by joeblurton on 2010-01-21
Wow, thanks Ayuthia, that's very, very useful. Sorry it's taken me so long to notice the reply! The other day I had a problem running Debian sid on VB, where Network Manager didn't seem to install from the .iso. I gave up after a while, but with this I might just get it working! Spooky. Karmic...

---

