---
title: "New ubuntu user - setting up rt2570 wireless USB adaptor?"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by lindsayward on 2009-07-28
Hi there.
  I have been a ubuntu user for about 12 hours now :) Thanks in advance for anyone who can help me out.
I have an IT degree and know my way around the command line in unix, but this is my first real effort at Linux for managing my own computer, so things like installing modules and troubleshooting hardware is pretty new to me.
I've installed mythbuntu 9.04 on a brand new PC I intend to use for a HTPC. The install seemed to go well, but I want to get wireless networking on before I go further with the myth setup. I have plugged it in to my modem via Ethernet and updated all of the packages. In following some instructions, I have also installed ubuntu-desktop.

My wireless device is a Buffalo Wireless-G (lsusb shows "Melco. Inc.").
Apparently it uses the rt2570 chipset that should be supported in the kernel ([http://www.linuxquestions.org/hcl/showproduct.php?product=3053&cat=all](http://www.linuxquestions.org/hcl/showproduct.php?product=3053&cat=all) says it works). 
I tried following some suggestions here, but when I do iwconfig, it does not show wlan0, so I don't think it's installed properly or something.

Most of what I'm finding when I search is for compiling the drivers (which I understand is no longer needed) or setting up the actual wifi when the device is installed.
What is the process I should do to get it installed properly?

Thank you very much.

---

### Post by lindsayward on 2009-07-29
bump?
I tried following the suggestions here: ([http://ubuntuforums.org/showthread.php?t=992420](http://ubuntuforums.org/showthread.php?t=992420)) but nothing new.

lsusb says:
Bus 002 Device 002: ID 0411:0137 MelCo., Inc. 

lsmod doesn't show any wireless modules

iwconfig doesn't show wlan0

sudo lshw -C network only shows the Ethernet connection

iwlist scan tells me eth0 and pan0 (and lo) don't support scanning

uname -mr shows:
2.6.28-13-generic i686

sudo /etc/init.d/networking restart shows:
 * Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0

rutilt shows:
Can't find any wireless network interface.

Do I need to do anything with firmware, or something?

Thanks.

---

### Post by lindsayward on 2009-07-30
I had to reinstall to get dual-booting partitions better (Vista), and now I've used regular ubuntu 9.04 instead of mythbuntu.
I still really don't know what to do, and it's a deal-breaker since I can't move the PC to the TV room.
Is there something like the Device Manager in Windows?
ANY help would be really... helpful.
Thanks!

---

### Post by Crafty Kisses on 2009-07-30
Try to manually load the module and see if it works. Run as root:
```
modprobe rt2570
```

---

### Post by lindsayward on 2009-07-31
That says:
```
FATAL: Module rt2570 not found.
```I've read at [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads) that these drivers were part of the main kernel, so I didn't think I needed to compile them. (I'm a bit ignorant, picking up bits and pieces as I go.)

So, I used the Synaptic Package Manager to get the rt2570 source and the bits that came with it, then followed the instructions in the readme, but
```
module-assistant build rt2570
``` failed...
```
 &#9474; /usr/src/modules/rt2570/rtusb_init.c: In function &#8216;KillThreads&#8217;:           &#9618;
 &#9474; /usr/src/modules/rt2570/rtusb_init.c:1283: error: implicit declaration     &#9618;
 &#9474; of function &#8216;kill_proc&#8217;                                                    &#9618;
 &#9474; make[4]: *** [/usr/src/modules/rt2570/rtusb_init.o] Error 1                &#9618;
 &#9474; make[3]: *** [_module_/usr/src/modules/rt2570] Error 2                     &#9618;
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.28-14-generic'      &#9618;
 &#9474; rt2570.ko failed to build!                                                 &#9618;
 &#9474; make[2]: *** [module] Error 1                                              &#9618;
 &#9474; make[2]: Leaving directory `/usr/src/modules/rt2570'                       &#9618;
 &#9474; make[1]: *** [binary_modules] Error 2                                      &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/modules/rt2570'                       &#9646;
 &#9474; make: *** [kdist_build] Error 2  
```It surprises me that distributed code wouldn't compile/install, but I might have done something wrong.
So now I'm trying to follow the instructions at: [http://rt2x00.serialmonkey.com/wiki/index.php?title=Rt2x00_GIT_instructions](http://rt2x00.serialmonkey.com/wiki/index.php?title=Rt2x00_GIT_instructions) - but that doesn't seem like it's for installing, but committing change back?

When I type sudo modprobe rt2x00usb I don't get the "FATAL" response, and lsmod | grep rt2 shows:
rt2x00usb              18688  0 
rt2x00lib              37888  1 rt2x00usb
led_class              12036  1 rt2x00lib
mac80211              217592  2 rt2x00usb,rt2x00lib
cfg80211               38288  2 rt2x00lib,mac80211

I still see no wireless device anywhere. Is there ANYTHING I can do to find this device?
Please correct anything I'm not getting right.

---

### Post by lindsayward on 2009-08-01
Well, after far too many hours (I want my sleep back :), I have solved the problem, and it was as simple as this:


[LIST]
[*]turn off the computer
[*]unplug the Buffalo USB wireless card
[*]take the top off the computer
[*]put in a D-Link DWL-G520
[*]restart the computer
[*]setup the wireless for the device the computer recognised immediately
[/LIST]
I feel just a bit sad I couldn't get the other thing to work, but I've got a spare USB port (already used now) and hopefully I can get my money back on the Buffalo. I can't believe how much effort that all took, but now the problem is gone.
Now back to setting up MythTV...

---

### Post by Crafty Kisses on 2009-08-01
So what it looks like, now correct me if I'm wrong, is you're trying to compile this driver from source? Is this correct? If you're building this driver from source, you need the following package, so run as root:
```
apt-get install build-essential
```

EDIT: Wow I just seen your post, we posted at the same time. ;-) Glad you got the issue resolved.

---

### Post by sefs on 2009-09-07
> **Codename said:**
> So what it looks like, now correct me if I'm wrong, is you're trying to compile this driver from source? Is this correct? If you're building this driver from source, you need the following package, so run as root:
```
apt-get install build-essential
```

EDIT: Wow I just seen your post, we posted at the same time. ;-) Glad you got the issue resolved.

build-essential is not the issue here...the source in the repos simply will not compile.

---

