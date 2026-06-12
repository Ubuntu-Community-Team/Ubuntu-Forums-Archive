---
title: "ndiswrapper stuff"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by RoyalShrubber on 2006-06-06
hi, I'm n00b, I installed Ubuntu 6.06 3 days ago, and I got an issue with my wireless card (that's why i'm writing from xp partition).

Because I found that my Asus WL-138G wireless card isn't supported by native drivers I started playing with ndiswrapper. I am playing for about two days now and I've run out of ideas.. 

I downloaded the newest ndiswrapper 1.17 and compiled it (at first I did something wrong and 'modprobe ndiswrapper' gave me 'fatal: ... invalid argument', but after uninstalling and recompiling I don't get that error any more). The problem is that after loading recommended win98 dirvers, loading ndiswrapper with modprobe, I don't see wlan0 device (with iwconfig or any other program). 

Some text from terminal
> matej@matej-desktop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

matej@matej-desktop:~$ ndiswrapper -v
utils version: 1.8
driver version:        1.17
vermagic:       2.6.15-23-386 preempt 486 gcc-4.0
matej@matej-desktop:~$ ndiswrapper -l
Installed drivers:
mrv8k51         driver installed, hardware present
matej@matej-desktop:~$ sudo depmod -a
Password:
matej@matej-desktop:~$ sudo modprobe ndiswrapper
matej@matej-desktop:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

matej@matej-desktop:~$
If you need more info please ask!
What should I do?
Thx for help.

---

### Post by shamrock_uk on 2006-06-06
Well, for a start, you don't really have to go compiling many things for yourself in this day and age - Linux has come on a long way on that score and you will often run into fewer problems if you make use of the packages that are available. 

So first of all, I would try this instead:

```
sudo modprobe -r ndiswrapper
sudo apt-get install ndiswrapper-utils
```

Then it might be worth unloading and reloading the .ini file from ndiswrapper before you load it again.

```
sudo ndiswrapper -e *name of driver*
sudo ndiswrapper -l
sudo ndiswrapper -i *xxx.ini*
sudo ndiswrapper -l
sudo modprobe ndiswrapper 
sudo lsmod | grep ndi
```

Edit:

If that last command displays ndiswrapper then you should be all good to go. 

iwconfig will hopefully return a most positive answer then!

It's not that a compiled version won't work, but I'm just a little suspicious about that error message that you silenced by a recompile...my gut would be to try with the package in case something is still not quite right.

---

### Post by jml on 2006-06-06
If you have not checked out this site, you may want to.  Its well organized and may be of some help.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Joe

---

### Post by RoyalShrubber on 2006-06-06
thx for helping...

Instruction from shamrock_uk:
i've downloaded utils from here [http://packages.debian.org/stable/misc/ndiswrapper-utils]("http://packages.debian.org/stable/misc/ndiswrapper-utils") but 'sudo apt-get install ndiswrapper-utils' said i already have the newest package, synaptic also showed that package. After reinstalling sys driver the 'sudo lsmod | grep ndi' command returned this:
> matej@matej-desktop:~/WL138G/Drv98$ sudo lsmod | grep ndi
ndiswrapper           170512  0
usbcore               129668  5 ndiswrapper,usbhid,usb_storage,uhci_hcd
matej@matej-desktop:~/WL138G/Drv98$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.


Results from guide recommended by jml:
I've read guide, but I haven't found any solution. I think that module is loaded but somehow it doesn't work properly. Is problem somewhere in configuration files?
Some results (shortened with only data related to wireless card)
> lshw
        *-network UNCLAIMED
             description: Ethernet controller
             product: Marvell W8300 802.11 Adapter
             vendor: Marvell Technology Group Ltd.
             physical id: a
             bus info: pci@00:0a.0
             version: 07
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             resources: iomemory:ea000000-ea00ffff iomemory:ea010000-ea01ffff irq:11

lspci -v
0000:00:0a.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 138f
        Flags: 66MHz, medium devsel, IRQ 11
        Memory at ea000000 (32-bit, non-prefetchable) [size=64K]
        Memory at ea010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2

lsmod | grep ndis
ndiswrapper           170512  0
usbcore               129668  5 ndiswrapper,usbhid,usb_storage,uhci_hcd

If you need to see my configuration files just say which (and where can i find them), and I'll get them on net, and link it here.
Any new ideas?
thx ;)

---

### Post by daveZ on 2006-06-07
RoyalShrubber, I was having the exact same problem as you and I was finally able to fix it by removing the driver that comes with dapper.

Apparently, Dapper comes with a driver for this device already, but it doesn't actually work. This prevents ndiswrapper from operating properly.

What I did to fix it was I removed the non-working native driver from the kernel files. So search for "mrv8k.ko" somewhere in /lib/modules/<your kernel>/kernel/net, and (re)move it.

Once I did that, I rebooted and, after installing the windows 2k driver from the CD that came with the wireless device using ndiswrapper, my internet was recognized and worked. Happened about 10 minutes ago :)

Good luck.

~daveZ

---

### Post by Blind-Summit on 2006-06-07
I got hold of the latest ndiswrapper and the ndisgtk from a windows box I have downstairs. Installed those both fine and added my inf files and they said hardware detected.

Wyhen I went to configure the network - my Belkin card came up as eth2 instead of wlan0.

It wtill says wireless but I can't get onto my wifi connection at all.

Would this be a similar issue - remove that kernel driver? Is that still installed even after I loaded my inf files from the cd (from the harddrive, not direct from the cd)

It's so much easier to fix up the new 6.06 release and get it working for me when I have the internet working as opposed to having to boot to M$ Windoze and check ideas - back and forth

Any help would be most appreciated

Alex

---

### Post by nzruss on 2006-06-07
you might try this, 

[http://ubuntuforums.org/showthread.php?t=190967](http://ubuntuforums.org/showthread.php?t=190967)

but you'll need to change the name of your drivers to match what you have. Even though the cards are different the principle is the same.

---

### Post by RoyalShrubber on 2006-06-08
thx daveZ, now it's working :) :) :) :) 

To anybody who might have the same problem: the file which is causing troubles is following: /lib/modules/{your kernel}/kernel/drivers/net/wireless/mrv8k/mrv8k.ko. You just have to delete it and restart linux.

Now I can detect wlan0, but I haven't yet configured my adsl dial-up :( (it seems I have another buggy)

---

### Post by Blind-Summit on 2006-06-09
See, I just got told to do the same thing on another thread - remove my bcm43xx.ko file - I did that and now it won't boot at all. I can't even get the rescue mode to load up as that gives me some other error :(

---

### Post by Stinger on 2006-06-16
[QUOTE=RoyalShrubber]thx daveZ, now it's working :) :) :) :) 

To anybody who might have the same problem: the file which is causing troubles is following:[COLOR="Red"] /lib/modules/{your kernel}/kernel/drivers/net/wireless/mrv8k/mrv8k.ko.[/COLOR] You just have to delete it and restart linux.
[/QUOTE]
Thanks DaveZ and RoyalShrubber , I have a [COLOR="Red"]Asus WL-138g[/COLOR] and have been staring at my frozen boot screen for several hours now trying to figure this out.
Ndiswrapper worked so fine in breezy and now this ! :-& 

Your solution works for me too \\:D/

I have just upgraded to kernel 2.6.15-25-386 , I removed the bugerous module there too.
I will continue to do so until I know for sure that the  [COLOR="Red"]mrv8k.ko[/COLOR] module works with my Asus card.

Notice ! after removing my ethernet connection , to run wireless only , the boot sequence froze again when it tries to load the network interface.
Putting [COLOR="Red"]ndiswrapper at the end of the /etc/modules file[/COLOR] solved the problem for me.

Thanks again.

---

### Post by 0okami on 2006-08-17
First i had tried this: [http://ubuntuforums.org/showthread.php?t=190967](http://ubuntuforums.org/showthread.php?t=190967)

Then, it was this step that solved my problem. I can now go online with my
dwl-g510 revision a:1 marvel chipset card.

> **RoyalShrubber said:**
> thx daveZ, now it's working :) :) :) :) 

To anybody who might have the same problem: the file which is causing troubles is following: /lib/modules/{your kernel}/kernel/drivers/net/wireless/mrv8k/mrv8k.ko. You just have to delete it and restart linux.




Thanks!!!

---

### Post by 944jon on 2006-08-24
I have a DLink  AirPlus DWL-G630 with the Marvell W8300 chip which is Rev1 for this card I believe. Running Ubuntu 6.06 on a Compaq 1200Z. I removed the mrvk8.ko file as suggested, and it did not work right away. I first tried using ndiswrapper with the graphical "Windows Wireless Drivers" tool and the winXp driver from Dlinks website. It loaded and said the hardware was present, but no lights on the card. Then I tried the win98 driver and that worked right away. Thanks for the help everyone!

---

### Post by 944jon on 2006-08-24
Ahh! It stopped working after a restart. Now the Windows Wireless Driver app locks up when I try to load the driver. To correct my previous post it is Rev. A1 card not Rev1. I have found that there are different chipsets for the different versions of the card.

It seems to plug and play ok and be recognized in Device Manager and listed when I type lspci, but no driver is listed for it. I will switch to the DWL-G630 doesn't work after fresh install thread which is more specific to my problem.](*,)

---

### Post by demuro1 on 2007-05-09
so I'm ultra new to all this and I have a question.  I have a P5ad-e premium motherboard with onboard marvell wifi.  I posted anohter thread and a guy said I needed the ndiswrapper and the xp drivers.  I have both and have put the folders with these files onto my ubuntu machine.  I have no idea what to do now.  the install and readme both don't give me enough info on how to get the ndis info in the system.  I downloaded everything on my xp machine, this one I'm using now and transfered them to my ubuntu machine via flash drive.

I'd appreciate any help you can offer on installing this stuff as getting the wifi up is my first big task here.  also I have an x850xt gopu I'd like to get drivers for so if you can help with that at the same time I'd appreciate it


Thanks for the help

---

