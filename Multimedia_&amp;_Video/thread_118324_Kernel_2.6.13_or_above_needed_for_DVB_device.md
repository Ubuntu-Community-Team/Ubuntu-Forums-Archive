---
title: "Kernel 2.6.13 or above needed for DVB device"
date: 2006-01-16
forum: Multimedia &amp; Video
---

### Post by DRF on 2006-01-16
Hello,

I've got a Freecom DVB-T USB stick which is supported by the DVB-USB and DVB-USB-DTT modules according to linuxtv.org however looking around the internet I remember seeing (and confirmed by checking up the kernel changelog [http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.13](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.13)) that the support for the device is introduced to the kernel in versions 2.6.13 and above, unfortunatly breezy is on 2.6.12. (won't even find a dvb-usb module to modprobe it let alone support for the device)

So I've got a few questions at this stage (been a while since I've done a kernel compile and think it was with the a kernel in the repositories rather than in a diff version all together)

Will changing the kernel from 2.6.12 to a newer version break any thing? (hard ware detection etc etc) or is it quite safe.
Would it be best to upgrade to the minimum needed kernel (2.6.13) or go to 2.6.15 (current stable according to kernel.org)
Where should I get the kernel source from? Wondering rather than downloading from the kernel.org site if the kernel source in the dapper repositories has any extra patch's added to it etc.
I don't think I use any restricted modules other than the ATI driver but if I'm wrong how hard would it be to sort out the restricted modules stuff?

Thank you for any help, hope I've not asked too many questions, I have looked at the wiki and forums for kernel compilation but the ones i found seem to assume you want the current kernel recompiled (eg apt-get linux-tree-2.6.12 as one of the first steps).

I've not got too much time to tinker with the system and as it's my main desktop so don't really want to break it so hoping for a nice easy: download this, use vanilla config like so, compile and package to .deb (easy to uninstall if I muck it up hehe). Then when everythings ready install the new kernel.
But if it gets too complicated may just leave it till I either find more time or till dapper is released (or at least more stable than it is now)

Daniel

---

### Post by Andrew Golightly on 2006-01-21
Hi Daniel,

I'm doing the same thing as you. Pretty much exactly! Do you know where we can find out when Ubuntu will release 2.6.13? It may be worth just to wait a bit then? Like you I don't really want to start messing around with the kernel itself unless I have to.

If you make any progress on getting the DVB stick going, could you let us know?

I'm sure we'll get it going soon. :razz: 
cheers,
Andrew

---

### Post by Andrew Golightly on 2006-02-03
Hi all,

I've got the device working now. I'm using kernel 2.6.15-14-386 and had to copy the firmware file dvb-usb-wt220u-01.fw from [http://www.linuxtv.org/download/dvb/firmware/](http://www.linuxtv.org/download/dvb/firmware/) to /lib/firmware/2.6.15-14-386/

I got the latest kernel, by downloading and installing Dapper Drake from [http://cdimage.ubuntu.com/cdimage/releases/dapper/flight-3/](http://cdimage.ubuntu.com/cdimage/releases/dapper/flight-3/)

Now I just need reception to get it tuning properly :)

hth,
Andrew

---

### Post by crispingatiesa on 2006-02-03
There is a thread (or more than one) regarding Kernel compilation and are very useful.

The short answer is: booting with the new kernel will break things, some drivers will have to be reinstalled etc.

Long answer: it is a safe procedure 'cause you can always boot back to the old version of the Kernel if you didn't unistalled (which is wise anyways NOT TO UNISTALL THE OLD KERNEL VERSION in case you have to go back)

I had a similar problem (ITE 8212 Raid) and compiled the 2.6.15 which is happily running now with no problems.

---

### Post by DRF on 2006-02-27
Sorry for not replying (totally slipped out my mind) until I noticed a post in a mailing list archive from Andrew Golightly.

Ok I got it working a different way, as upgrading the ubuntu kernel in breezy might break a few things (nothing too critical but didn't fancy it), I looked around and found the following link which is to the 2.6.12 DVB patch which was submitted and in 2.6.13 and above as standard, so I downloaded the kernel source applyed the patch and recompiled the kernel.

[http://www.linuxtv.org/downloads/patches/2.6.12/](http://www.linuxtv.org/downloads/patches/2.6.12/)

Also you will need to download the firmware from the same site. The address is:
[http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/)
the file you need is (I believe) dvb-usb-wt220u-01.fw 

I would assume that this also applys for other DVB cards that aren't supported in the 2.6.12 kernel. The DVB wiki at linuxtv.org is a good source of information. ([http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page))

Hope this helps give anyone else in this situation searching the forums for answers a few pointers (until the dapper release).

If you need any help with the kernel recompile and patch applying process please search the wiki here, or if you get stuck send me a private message on the forum and I'll try to remember what i did and reply when I can.

Daniel

---

