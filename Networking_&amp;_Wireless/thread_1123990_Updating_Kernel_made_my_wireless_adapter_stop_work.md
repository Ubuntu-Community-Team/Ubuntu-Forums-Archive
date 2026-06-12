---
title: "Updating Kernel made my wireless adapter stop working"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by VitaminBeer on 2009-04-12
Hi there,

 I'm rather new to the linux scene and have been for some time wanting to focus on using Linux more than Windows with all the problems I've had on Vista.

I have installed Xubuntu 8.10 with the kernel 2.6.27-7 and everything worked absolutley wonderful, I even got my Wireless adapter working no problems at all, it was all automatic.

My wireless adapter is a Sagem WL5061S they are almost unheard of, I got it on Ebay for $10.
It was installed as Z-Com Sitecom wireless network adapter 100G+ WL-125 
It worked fine, now... I updated the kernel to 2.6.27-11 because it was telling me I should update the system so I went ahead and did it.

Now upon booting Xubuntu it freezes at the boot screen and doesn't load, I have taken out the USB Dongle (Wireless Adapter) and it boots successfully. 
I had a look at the commands, and I've noticed this:

It says something about P54usb cannot find firmware, goto wireless.kernel.org - I have done this and cannot for the life of me work out how to go about installing that. 
It also said on that site under ubuntu I should try installing sudo apt-get install linux-backports-modules-intrepid

I have done that also and rebooted and still the same problem.

I also noticed when its trying to boot it gets stuck at Starting Bluetooth, but before that is the P54 usb cannot find firmware error.

Okay, so I have also got another USB wireless (netgear) and it works fine upon booting and during normal use, so that is what I am using for the moment, but I want my other one working since I plan on doing this on another machine

So I know it has to be something to do with firmware or drivers or something....

So..... I am not too sure what to do, any help is very much appreciated.

Thanks for your time,

VB,

---

### Post by kevdog on 2009-04-13
Boot into the old kernel -- use the grub menu at boot to select the old kernel, and then determine what driver you were using in the old kernel was.  This might give us a clue about what driver you are looking for.  

And just my opinion -- I've learned a long time ago that unless its a major security reason, upgrading kernels is pretty much worthless.  A lot of things can potentially break when updating kernels, and in most cases you don't gain anything with the newer kernel.

---

### Post by VitaminBeer on 2009-04-13
Thanks for your response I appreciate it

Okay so then, what should I do when it keeps coming up and bugging me about updating the system? I am a bit anal about having alerts and things that annoy me.

I also wanted to know how do I now get rid of the old kernel since I am using the newer one now. Do I just find a way to delete it from the GRUB loader?

I think now, I will just install the first kernel on the other PC and use the adapter that I was having trouble with on that one and I just won't update it, since it was working fine before the update.

I also had another quick question...
I am using a program called CPU Gear Box - it throttles the CPU to half speed when idling and what not.
My problem is it doesn't start automatically upon entering Xubuntu.
I have worked out a way to make it start automatically but it wants a password every single time I log on and it drives me a bit batty, I was wondering if there was something I could put in the command line to make it so it didn't ask me, if that's possible?

Alright well now officially 10 Hours later I now have everything running as it should be, including MetaTrader 4 which is a Windows program. and Avant bar, it's nifty, oh and you can't forget Compiz, what joy I had with that....!

Thanks for your time

---

### Post by Obituaryfreak on 2009-04-13
Guys Guys
I can use little help here
I used to have intrepid and those days were quite fun....
to make it short,It worked for me pretty cool and nothing was wrong 
I got an TX 2000 series HP pavilion(2070ee) preloaded with Vista..
I dont know what exactly  happened when I lost my wireless I did 
every thing from installing ndiswrraper ndisgtk and bla bla
so finally decided to upgrade to 9.04 and at the first boot
my roadcom Corporation BCM4312 started functioning,and I thought that did the trick...but after turning off the laptop and turning it back on the day after...boom there was no wireless and the same old scenario started happening to me ..now its playing with me,i mean if  I reset the machine 4 times may be the th time its wireless come back up ....
but when its no there ,,,it really not there ,,,,
and here is the out put of the command which may be useful for the diagnosis :
 

lshw is :
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 72:21:be:e6:5b:b7
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
-
and iwconfig output:
lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.
----------
The help is highly appreciated

---

### Post by VitaminBeer on 2009-04-13
> **Obituaryfreak said:**
> Guys Guys
I can use little help here
I used to have intrepid and those days were quite fun....
to make it short,It worked for me pretty cool and nothing was wrong 
I got an TX 2000 series HP pavilion(2070ee) preloaded with Vista..
I dont know what exactly  happened when I lost my wireless I did 
every thing from installing ndiswrraper ndisgtk and bla bla
so finally decided to upgrade to 9.04 and at the first boot
my roadcom Corporation BCM4312 started functioning,and I thought that did the trick...but after turning off the laptop and turning it back on the day after...boom there was no wireless and the same old scenario started happening to me ..now its playing with me,i mean if  I reset the machine 4 times may be the th time its wireless come back up ....
but when its no there ,,,it really not there ,,,,
and here is the out put of the command which may be useful for the diagnosis :
 

The help is highly appreciated

----------------------------------------------
There is a lot of problems with HP and Compaq laptops, mine included, the wireless on the motherboard comes and goes when it pleases, it's to do with the nvidia chipset overheating on the mainboard, it's a flaw in the design. I have actually opened mine up and made a better heatsink... long story short, it's not really worth the mucking around but I wanted my laptop to last. First make sure you do the firmware update.

Here is a link pertaining to the problem that you might be experiencing with your HP - read the whole thing. I'm pretty sure your model is covered there.. if not I'm mistaken.

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01296338&cc=au&dlc=en&lc=en&jumpid=reg_R1002_AUEN](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01296338&cc=au&dlc=en&lc=en&jumpid=reg_R1002_AUEN)

Mine is Broadcom 4311 as well - they are the general going unit with these laptops

All the best, and I hope that this helps you - update the firmware to the new one if you haven't already. That's about all you can do unless you have extended warranty

---

### Post by Obituaryfreak on 2009-04-13
dude thanx for the reply
but my Model is  HP pavilion TX 2070ee tablet series .
and I couldnt find the firmware in that site and my Broadcom model is 4312 not 4311

---

### Post by Obituaryfreak on 2009-04-13
vahid@RockerGeek:~$   sudo modprobe ndiswrapper
[sudo] password for vahid: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/wl, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
 the nidswrapper module is not present in the in the kernel modules
I guess I need to put it in the kernel module first

---

### Post by VitaminBeer on 2009-04-13
> **Obituaryfreak said:**
> vahid@RockerGeek:~$   sudo modprobe ndiswrapper
[sudo] password for vahid: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/wl, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
 the nidswrapper module is not present in the in the kernel modules
I guess I need to put it in the kernel module first

Hi mate

Sorry I jumped to conclusions there, it all sounded so similar to the models I was thinking of at the time.

Sorry I can't help you with the Ndiswrapper thing, as far as I know I have everything running through firmware stuff that was automatically installed upon booting Xubuntu for the first time.

I finally got the 3d Cube and everything worked out in Compiz, it is amazing!

Good luck with your wireless and I hope some one here can help you with it

---

### Post by sgosnell on 2009-04-13
To delete a kernel, use Synaptic.  Look for linux-image, and find the one you want to get rid of.  Mark it for removal, click Update, and it's gone, cleanly.  No need to muck around with grub.  I have several installed, because I like to try the latest kernels, trying to get my EEEPC working correctly without having to tweak.  The latest .29 kernel works very well for me, and might work with whatever laptop you have.  Intrepid didn't work well at all with my EEE, but Jaunty is much, much better, and the .29 kernel is even better.

---

