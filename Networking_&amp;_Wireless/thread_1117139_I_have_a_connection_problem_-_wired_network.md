---
title: "I have a connection problem - wired network"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by lukeinvancouver on 2009-04-05
Hello,

I'm new to Ubuntu though not to computing. (From DOS 2.4 to Vista). My programming “skills” are lousy.

I also made several previous (unsuccessful) attempts with different distros to get going with Linux.

I recently received my Ubuntu 8.10 CD (because I can't remember to do the mdsum thingie to check the integrity of the download) and was very happy when I installed it. I was also very optimistic after superfiically looking at Ubuntu.

Now 5 installations later I feel a little frustrated. 

But maybe with the help of some good people around here it might yet work out to be a beautiful switch.

Please let me tell the story to put things in context.

The installer found my internet connection (cable; router between modem and machine) automatically. After installation I rebooted as instructed.  I got the message:

“You are now connected to the wired network”. 

“Enable networking” was checked in the drop down box. Under Info (I believe this to be important) [B]“Auto eth0” was checked and it said “default”.
[/B]
I surfed a little to see if things were really fine. They were.

I downloaded and installed 283 updates (270.8 MB). I rebooted as instructed and the “wired network was disconnected”.

Under Info  **“Auto eth0” was changed to never.** Moreover it was greyed out and I could find no way to change this. Setting it to “auto eth0” was no solution (presumably because of the “never”0.


Rebooting and running it from the CD gives me access to the network. Rebooting subsequently from the hard drive resulted in frustration.

Information:

Active network connections.

Interface: Ethernet (eth0)
Hardware address (I'm not sure if the zeros should be Os): 00:1C:C0:8C:B4:48
Driver: r8169
Speed: 100 Mb/s
IP Adress: XXX.XXX.X.XXX
Broadcast Address: Same first 7 digits as above and 255
Subnet Mask:255.255.255.0
Default Route: Same first 7 digits as above and 1
Primary DNS: 64.59.144.90
Secondary DNS: 64.59.144.91


The hardware is a cheap machine connected to the net with the regular cable package.  I wanted to first see if it works out OK and I need to keep the Vista machine for business reasons.

Intel MB D945GCLF with an Atom processor and integrated graphics. 1 GB of RAM. LG DVD drive and burner.

Doing exactly the same thing over and over again is by some defined as insanity. I didn't do things exactly the same way, except for the last time to make sure I got it right and write down all the messages and settings. I by-passed the router: Same results. The idea to try the CD only came to me later. And the second time was ... well, hope. :)

---

### Post by CyberMando on 2009-04-05
I compliment youon your clear explanation. I hope my answer will be as clear. :) First is the module (driver) loaded?
lsmod | grep r8169
should show that it is loaded. If so it is a matter of getting it configured. I am thinking you got the aboe info from ifconfig, so the modules is loaded.


There are 2 ways to configure your network in Ubuntu. The applet you are seeing is part of network-manager. The other system is the Debian system that uses ifupdown. I am not sure just how your system got setup but here is where to look.

If /etc/NetworkManager/nm-system-settings.conf now says
[ifupdown]
managed=false
network-manager will not try to manage interfaces that are in the /etc/network/interfaces file.
Your /etc/network/interfaces file should have at least an entry for the loopback like this
auto lo
iface lo inet loopback

That tells the system to configure the loopback. If it also says
auto eth0
iface eth0 inet dhcp
ifupdown will configure eth0 using dhcp and network-manager should leave it alone. If your interfaces file does not ahve the eth0 entry you could add it and it should configure the network. If you want to use network-manager, which probably should be in use now, it might help to change nm-system-settings.conf to say true even though that should not matter if the interface is not in interfaces.

My guess is that eth0 is in interfaces and network-manager is trying to manage it even though nm-system-settings.conf tells it not to.

---

### Post by lukeinvancouver on 2009-04-05
Thank you for your reply.

It's not totally clear to me what changes the value from 1 [default] to 0 [never] after the upgrades are installed.

The problem starts with the reboot.

More importantly, how do I tell it to always use it (as it does when you start it from the CD).

Thanks for trying but my problem has not been solved.

---

### Post by marshump on 2009-04-05
I have been struggling with this problem today, too. I have a computer set up for my kids that uses a small Intel Atom-based motherboard. Everything works fine when booting from a LiveCD, but my wired ethernet just wasn't working after applying the last batch of updates. I tried rearranging various network settings, but that didn't help. In the end, I simply booted back into my system using the previous kernel. That worked just fine. No changes required to any configuration files. No removing Network Manager. Just running with the previous kernel. The updates had installed kernel version 2.6.27-11-generic. I went back to 2.6.27-9-generic. With that in place, my network is working just fine again. I didn't have to do anything complicated to go back to the earlier kernel. Just hit the 'ESC' key during a reboot when you see the message about "GRUB loading", then select the earlier version of the kernel from the list and hit 'Enter'. If that works for you, you can edit the /boot/grub/menu.lst file to default to the 2.6.27-9 kernel so that everything continues to work after the next reboot.

It looked like your hardware was similar to mine and your problems occurred after an update. If so, perhaps my solution will work for you, too. Good luck!

---

### Post by lukeinvancouver on 2009-04-06
> **marshump said:**
> If that works for you, you can edit the /boot/grub/menu.lst file to default to the 2.6.27-9 kernel so that everything continues to work after the next reboot.


Thank you for your help.

It didn't quite work the way it worked for you but I'm "sort of" on the way, meaning that I can get a connection if I select "Kernel 2.6.27-7 (recovery mode)" [I don't have the choice of 2.6.27-9] Then (on a hunch) I selected "Repair broken packages"

Then it asks: "Do you want to start the upgrade?" My yes answer is followed by "1 new package [size 22.3k] is going to be installed."

2 error messages follow:

rm: Cannot remove '/var/lib/apt/lists/partial/*': No such file or directory

rm: Cannot remove '/var/lib/apt/archives/partial/*': No such file or directory

Then it asks "Do you want to resume normal boot?"

Answering 'yes' finishes the boot process and gives me access to the net but only as long as I don't power down.

This process **has to be repeated every time** I turn the machine on.

It's been two and a half years since I last touched Linux and I've forgotten much (most?) of the little I knew.

Would you please tell me how I edit /boot/grub/menu.lst? Or would this even work for me since I have to do a repair every time I boot up?

---

### Post by marshump on 2009-04-06
What (downlevel) kernels you have in your boot list will depend on what level you originally installed, how many kernel updates you've installed since, and how many downlevel kernels your system is keeping around. I'm using an Ubuntu 8.10 image that I installed about 4 or 5 months ago off of a CD, and I have the -7, -9, and -11 kernels available. It looks like you had one less update than I did. I also have two entries for each kernel: the normal one, and a (recovery mode) option. Do you have the normal one for the -7 level kernel? If so, you can probably boot from it, not have to worry about the repair step you mentioned, and just have everything work. 

If you have the (non-recovery mode) option for the -7 level kernel, and if it works for you, here are some steps you can follow to make that kernel level your default boot option:

1. Open a terminal window and type "gksu gedit" (without the quotes :-) )
2. Click the "Open" icon and then choose the "Filesystem" icon on the left-hand side of the resulting dialog.
3. Browse to the /boot/grub directory and open the file named menu.lst
4. Scroll way down until you find the kernel entries near the bottom of the file. The top one is almost certainly your current default boot option. It is number 0 (zero). 
5. Count from it (remember you're starting from zero) until you get to the option to do a regular (non-recovery mode) boot of the -7 level of the kernel (it's probably the third entry from the top-- or entry number 2)
6. Scroll back up to the top of this file and look for an entry that says "default=0". Change it to say "default=2" (or whatever the correct number was in your file). This will cause the dash 7 level of the kernel to be the default boot option going forward.
7. Save your changes.
8. Reboot and hit the 'ESC' key again when the GRUB loading message appears.
9. Verify the correct kernel is listed.

This should get you going. Since things are working for you when running under the -7 level of the kernel, I think this is all you really have to do. It looks like the level of the network driver included in the newer kernel is not happy with the built-in ethernet on the little Intel Atom boards. I believe there is already a new driver that fixes this, so perhaps it will get picked up the next time a new kernel is available. It's possible to go and grab the new driver off of the Intel website, compile it, and install it yourself, but that's probably more trouble than you were interested in going through. Hopefully, this will make it relatively easy for you to get back to being productive with Linux without any additional stress.

---

### Post by lukeinvancouver on 2009-04-06
**Thank you so much for your kindness** giving me such detailed instructions that even I could do it.

WOW!

I now have a Ubuntu machine which will boot up with the -7 kernel. 


> **marshump said:**
> Do you have the normal one for the -7 level kernel? If so, you can probably boot from it, not have to worry about the repair step you mentioned, and just have everything work. ...

 It's possible to go and grab the new driver off of the Intel website, compile it, and install it yourself, but that's probably more trouble than you were interested in going through. ...

[*[I]or rather more than I am able to do at this point*[/I]] 

Hopefully, this will make it relatively easy for you to get back to being productive with Linux without any additional stress.


Time to start learning how to use Ubuntu.


Thank you very much again.

---

### Post by lukeinvancouver on 2009-04-06
Also my thanks again to CyberMando. 

Your help is a bit beyond my technical capablities right now but it might sure come in handy in the future.

---

