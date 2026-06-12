---
title: "New User can't connect wirelessly"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by Grimmjow-Akutabi on 2009-07-12
Hey guys.

I've been trying out Ubuntu 9.04 on a CD Boot to test it out, and so far i'm loving it. However, my wireless dongle (TP-Link TL-WN620G) wont even turn on, meaning I can't access the internet.

I've heard off of others that if Ubuntu doesn't recognise straight away then it can be a real hassle getting online. Is this true?

I still have the disc with the drivers on, however it only offers Windows Vista, XP and 2000. 

Thanks for all the help guys, hopefully i'll be dual booting Linux soon!

Grimmjow-Akutabi

---

### Post by martinbaselier on 2009-07-13
Open a terminal and type:
lsusb
One of them will be your wireless card. Mine is internally and worked out of the box, but I have a bluetoothdongle, which is internally connected via usb, so I'll use that in my example. 
My output:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:200a Broadcom Corp. Bluetooth dongle
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Find your dongle (in my case it's 0a5c:200a)
sudo lsusb -d 0a5c:200a -v | less 
use up/down arrows to scroll and q to quit
Then use google to see if there's a kernel module available. 
0a5c:200a kernel module
Or use the productinfo you've found with lsusb.
Otherwise you would need ndiswrapper to use the windowsdriver under linux. It would still be easiest to google if someone has already solved the issue. Otherwise you could experiment a bit with ndiswrapper. I haven't got any experience with it, so I can't help you with that.

---

### Post by igorzwx on 2009-07-13
"I've heard off of others that if Ubuntu doesn't recognise straight away then it can be a real hassle getting online. Is this true?"

It is true, but now always.

I do not use wireless at all, I use cable.
On my notebook, it was no problems with getting online.
But the old box was a troulble.
The same was with DreamLinux.
I had learn that it is a kernal problem,
and it is a problem of all Debian sisters and brothers.
Eventually, I found on Ubuntu forums an old howto of
2005. It solved my problem.
There is a little probability that it may also help somebody else.
I told you from the very beginning that Ubuntu 9.04 is not a "new user friendly".

The "solution" that works for me:
gksu gedit /boot/grub/menu.lst

Add this 

acpi=force pci=noacpi

to the "kernel" line

NEW:

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        978b90c0-a552-4ecd-a041-8dec0730cbb1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=978b90c0-a552-4ecd-a041-8dec0730cbb1 ro quiet splash acpi=force pci=noacpi
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

----

OLD:

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        978b90c0-a552-4ecd-a041-8dec0730cbb1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=978b90c0-a552-4ecd-a041-8dec0730cbb1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

I told this: "it works for me", nothing more.

---

### Post by igorzwx on 2009-07-13
and reboot, of course.
If it does not work, ask somebody else.

---

### Post by Grimmjow-Akutabi on 2009-07-13
> **igorzwx said:**
> "
I told you from the very beginning that Ubuntu 9.04 is not a "new user friendly".

Then what may I ask, do you propose I do?

Use a different version of Ubuntu?

If 9.04 is really so horrible for new users, then can I ask for what you'd reccomend as an alternative?

---

### Post by igorzwx on 2009-07-13
Try Ubuntu Lite LiveCD
[http://u-lite.org/](http://u-lite.org/)

I am now experimenting with Beta version (netboot)
It has not Pulse inside!!!

You should take stable version LiveCD.
Do not expect fast results.

But this might be the best for "new user".

First, boot from LiveCD and check your internet connection.
If something is wrong, ask on the forum.

Good luck!

---

### Post by martinbaselier on 2009-07-13
I've tested a few distributions and so far I found ubuntu to be the most user friendly. I've read some good things about fedora too, but have never tried it. 

Whenever your hardware is not working out of the box, it will take quite some reserach and effort to get it working. It's of course a new operating system, which works differently from the one you're used to, most of the time that's windows. 

I do however find that when something's not working, you have far more tools to research the problem and find the cause. Most of the times it involves a terminal. So you should not be afraid to use it.

---

