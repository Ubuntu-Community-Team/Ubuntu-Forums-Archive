---
title: "Netgear WNA3100 + AMD 64-bit 11.04"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by AppSec on 2011-06-30
hi all..  first pardon the lack of caps, one of my shift keys on my laptop is dead and unfortunately it's the one i use the most (goes against all typing standards;-))

I just recently installed 11.04 64-bit AMD version of Ubuntu and I can't seem to get it to recognize the usb (netgear wna 3100) wireless router

```
uname -a: linux <server> 2.6.38-8-generic #42-ubuntu smp mon apr 11 03:31:24 utc 2011 x86_64 x86_64 x86_64 gnu/linux
```

```
lsusb:  bus 001 device002: ID 0846:9020 NetGear, inc.
```


i'm running an amd 64 anthlon processor on a home built machine (asus motherboard)


i'm having a little difficulty confirming the chipset.  one site has it listed as Atheros, but the ubuntu wireless has it listed as.

sudo modprobe wl returns FATAL: module not found.

So..  the question is.. how do I do this without having an internet connection (i really don't want to move my desktop down to my router).

Thanks for any help in advance.. and will be thanked later on..

---

### Post by chili555 on 2011-06-30
> i'm having a little difficulty confirming the chipset. one site has it listed as Atheros, but the ubuntu wireless has it listed as.
It's an obscure Broadcom. It is fairly complex to install. Please see here: [http://ubuntuforums.org/showthread.php?t=1549190&page=8](http://ubuntuforums.org/showthread.php?t=1549190&page=8)

and here: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)

Where modifications are referred to in .c files, they are referring to modifying the downloaded source code and then compiling it and installing it in place of the Ubuntu version so as to implement the changes. It's a bit more complex than usual, but certainly doable.> how do I do this without having an internet connectionYou'll need build-essential and linux-headers-generic. They are on the install CD, I believe. You can get ndiswrapper here: [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) Transfer it on a USB key to your desktop machine.

You will also need the Windows **XP** (not Vista, 7, etc.) .inf and .sys files.

Do you wish to proceed?

You could also return the device and look for a USB wireless device that works out of the box, although that's not nearly as fun as hacking .c code and compiling from a tarball.

PS - The module *wl* is incorrect for your device.

---

### Post by AppSec on 2011-06-30
chili  --

thanks for the info.. i saw all the other posts, but when i looked at the supported devices and saw the WNDA3100 was, i figured this one should be as well.

maybe i'll be daring and play with it.. but that is really annoying!

any recommendations on a usb wireless that is plug and play?

thanks.

---

### Post by chili555 on 2011-06-30
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I'm not quite sure I understand. Do you want to play with your current card and ndiswrapper or try a new card? ndiswrapper is a few steps that have to be done correctly, that's all.

---

### Post by AppSec on 2011-06-30
sorry for the confusion..

i'm going to try the wrapper.. if that doesn't work or winds up being too much of a pain in the neck, i'll probably just replace it.

thanks again for the help.

---

### Post by chili555 on 2011-07-01
> **AppSec said:**
> sorry for the confusion..

i'm going to try the wrapper.. if that doesn't work or winds up being too much of a pain in the neck, i'll probably just replace it.

thanks again for the help.Gosh, I wish you didn't say that. Please check here for many failed (that I have been able to see) attempts to get it to work in 64-bit. [http://ubuntuforums.org/showthread.php?t=1549190&page=8&highlight=wna3100](http://ubuntuforums.org/showthread.php?t=1549190&page=8&highlight=wna3100)

I am certainly willing to help you try, but I don't feel very optimistic. Please tell me what you'd like to do after reviewing the thread I linked.

---

### Post by AppSec on 2011-07-04
Well, I went and got the WNDA 3100 thinking that would be easier since according to the wireless support it was out of the box..

Of course, I didn't realize that was the V1 3100 not the v2 that I purchased.

It seems like these network adapters have been a pain in the 8&@*.

Looks like I'll be making another trek out to find a new adapter.

---

### Post by AppSec on 2011-07-04
Well, it looks like I was actually able to get the drivers installed.  And it seems like it is recognizing the device.

It just doesn't seem like it's still hitting the wireless device at all.  Not sure if it is because I'm still also running wired or not.

Any thoughts or command output I can submit?

Thanks.

---

### Post by Calgacus on 2012-01-26
Exact same problem on exact same v1 adapter for me lsusb reveals the usbs there but doesnt want to look for networks, it says the autorun drivers are invalid but the bcmn43xx64 drivers are installed

---

