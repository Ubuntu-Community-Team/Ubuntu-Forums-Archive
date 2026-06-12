---
title: "HOWTO: at76 for Ubuntu 8.10"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by claudio70b on 2009-01-03
Hi!

at76 (formerly at76c503a) is a driver for some Wireless LAN USB adapters like Netgear MA101 or one from Linksys. Unfortunatelly the old drivers stopped working with current Ubuntu without adaption. Ubuntu 8.10 ships only an ancient version (0.14beta1) of the driver which won't work properly with most devices. So here is how to get it working for Intrepid Ibex:

[LIST=1]
[*]Unplug your wlan usb device and start (to avoid complications).

[*]Eliminate the ancient driver that is included **sudo find /lib/modules/`uname -r` -name at76_usb.ko -exec rm '{}' \;** (or move it away for backup)

[*]Download at76_usb-0.17.tar.gz either from [http://developer.berlios.de/project/showfiles.php?group_id=727](http://developer.berlios.de/project/showfiles.php?group_id=727) or from [http://media.ubuntuusers.de/forum/attachments/1764277/at76_usb-0.17.tar.gz](http://media.ubuntuusers.de/forum/attachments/1764277/at76_usb-0.17.tar.gz) and unpack it: **tar xzf at76_usb-0.17.tar.gz**

[*]Download my little patch from [http://media.ubuntuusers.de/forum/attachments/1763750/at76_usb-0.17-.patch](http://media.ubuntuusers.de/forum/attachments/1763750/at76_usb-0.17-.patch) and apply it: **cd at76_usb-0.17 && patch -p1 <../at76_usb-0.17-.patch** (sorry, the forum software shortened the more verbose name of the patch)

[*]Compile and install: **make && sudo make install**
[/LIST]

Original post in german: [http://forum.ubuntuusers.de/post/1763750/](http://forum.ubuntuusers.de/post/1763750/)

---

### Post by NickeM on 2009-01-11
Thanks! :) This solves a bug i registered on launchpad two years ago.
[Click here to see bugreport.]("https://bugs.launchpad.net/ubuntu/+source/atmel-firmware/+bug/120800")

---

### Post by Hawkman on 2009-01-17
Noob question. I'm going to try this, but I'm not clear about one thing. Where does the file need to go? If I copy to my $HOME directory, and do the tar from that directory, I presume it creates a new folder in $HOME. Do I then do the make from the same directory?

---

### Post by claudio70b on 2009-01-30
Yeah, it seems like the bug will be solved soon! :p See [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152626](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152626)

A note about my work-around: A recent 0.17-version is actually included in the kernel source, in the staging-tree, (but isn't enabled in the Ubuntu kernel). So it is save to compile the sources of the kernel too. Sorry, I won't post how to do this.

@Hawkman: Choose whatever directory you like. I usually take /usr/src (or i.e. ~/source) so that I don't forget to compile it again when I update the kernel.

---

### Post by 1011101 on 2009-03-22
I'm new to ubuntu and after wasting about 6 hours trying to get my card to work, I finally found this post and it works great now. Thank you.

---

### Post by claudio70b on 2009-05-04
Good news!

Ubuntu 9.04 (Jaunty Jackalope) has been adopted as necesary. So it works out-of-the-box now! :P

---

### Post by pedor on 2009-09-13
Now in ubunti karmic 9.10 the at76_usb not working again :(
I get a wlan0 but can not connect or use with NM. 

any work around?

---

### Post by pedor on 2009-09-14
Now i have try with ndiswrapper  without good result,

Why should Linux community rewrite drivers some has works perfectively in years?   ](*,)

---

### Post by claudio70b on 2009-10-02
Thanks for the feedback pedor.

Let's move to a new thread: [http://ubuntuforums.org/showthread.php?p=8042683](http://ubuntuforums.org/showthread.php?p=8042683)

Please report there the output of those two commands:

```
find /lib -iname at76_usb.ko

find /lib -iname at76_usb.ko | xargs grep --text "Atmel at76x USB Wireless LAN Driver " 
```

...and more detailed problem description, please.

---

