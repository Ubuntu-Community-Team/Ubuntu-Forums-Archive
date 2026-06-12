---
title: "Asus 1215p, ubuntu 64bits, ethernet network transfers crash, bluetooth flaky"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by rcocchiararo on 2011-02-23
Hello

I just bought an Asus EEE 1215p netbook, and without testing more than wifi, i formated it and installed ubuntu 10.10 64bits on it.
(had to "try it first", cause the installer has no way of activating propietary drivers)

When i installed it, i had only wifi (tethering from my phone for internet).

Initially all was well, but then i noticed that after booting, bluetooth would say that it was "on" on the toolbar (or whatever ubuntu's nice looking black top bar is called :P), but if i went to Preferences>bluetooth, i could "activate" it from there, but nothing would happen.

Also, on the toolbar bluetooth icon, i only had the option to turn it off.

I ran /etc/init.d/bluetooth status, and it said it was not running, so after a few attepts at turning it on/of from terminal, it worked.

I had to repeat that each time i rebooted (i had a bluetooth mouse only).

Thats the first, but not really important, issue that i wanted to share and ask if it was normal under ubuntu and this netbook, or if it was a 64bit version issue.

Under the WIKI, it says it works well out of the box, but says nothing about 64/32 bits.

Now, on to the main or BIT issue, ETHERNET.

When i got back home, i decided to transfer some movies and other heavy files to my new netbook, from my debian home server. (i had transfered big files using wifi already, no problem there).

i connected my cat5e cable (my debian server has 4 1gigabit ethernet lan cards bridged), and started transfering files.

After a few hundred MBs, it stopped, and then the netbook was no longer accesible throug my internal LAN. (neither form the server, or from my windows 7 pcs).

I ran an ipconfig, and notices many errors under the eth interface.

I tried many cables, and even netbook to pc direct connection, always the same result. I had to reboot it each time for the ethernet card to work again. (sometimes it crashed after only 10mb).

If i just used internet, no big files transfers, all was fine.

Then i took it to my workplace, since we have a "real" network, but the same thing happened.

I then noticed that after the error, both the system monitor app and ifconfig showed that tons of data was still being transfered through ethernet.

only rebooting would fix it and stop the "phantom transfer".

I thought i had faulty hardware, but then i went back to windows 7, and file transfers over ethernet were fine.

Then i tested on the 32 bits live cd, and it was fine again.

Now im installing it.

Where my issues 64bit based ? i searched over the internet, no luck. (in fact, almost every search containing 1215p is of a site that sells it :P )

---

### Post by rcocchiararo on 2011-02-23
Ok, i installed 32 bits version.

Same network (ethernet issue)

Bluetooth takes some time to activate after booting, then it works.

Any ideas ? i really wanted to use this netbook with ubuntu, i don't want go back to win7 :(

---

### Post by rcocchiararo on 2011-02-24
the ethernet adapter on my netbook, based on the drivers for windows 7, is:

inside NDIS2 folder, inside a .inf:
Atheros AR8131/AR8132

inside the atheros folder:
8121
8132

---

### Post by rcocchiararo on 2011-02-24
after some more research, i found that my ethernet card/drivers are:

Atheros AR8152
Module/driveR: atl1c
(ATL1C, in case lower case makes it hard to read)

Dunno why thats not present on the windows lan drivers pack...

anyways, theres a linux 81** family driver downloadable from atheros.
I will see what i can do with that...

I got the info about my presice ethernet controller by:

lspci -vv | grep -A9 -i ethernet
(or  lspci -k | grep -A9 -i ethernet)

with lsmod | grep atl1c i confirmed it wa loaded

---

### Post by Le@ndro on 2011-03-02
Hi! I'm very interested in your research regarding Bluetoth and Ethernet conection, as my 1215p is arriving tomorrow! And I was thinking on formatting and installing Ubuntu 10.10 64bits without hesitation... (at least until Aurora comes out).

By the way, have you tried with Jupiter for the Bluetooth? Is the tool developed for EEEbuntu (now Aurora OS). Here are some links:

[http://www.auroraos.org/project/jupiter](http://www.auroraos.org/project/jupiter)

[http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html](http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html)

Apparently it also lets you use the SHE (Super Hybrid Engine)!!!

Some questions: What about mouse gestures? Does it supports Compiz or it's too much?

Thanks for your posts!!! Will prove really helpful!

Cheers!

---

### Post by rcocchiararo on 2011-03-02
hi

The ethernet chip is definitly AR8152, and by searching for that and not for my netbook model, i found out that the shipping kernel of ubuntu 10.10, and the uptades that you could get last week, have the ethernet problem.

Some people say that ethernet/wifi share the same driver.

Some people fixed the problem by compiling the lates AR81 family driver, downloaded from Atheros, but i could not compile it for the life of me. (it first asked for autoconf.h which was missing, but then it was not... it was in a non standard linux place for each kernel source i had, but until i found about that, i tried recreating it, and other stuff).

Then i went with installing the latest wifi-compat or something like that, but i failed again.

Finally, with Kernelcheck (or kerncheck) i compiled a newer kernel (2.6.37-candela), and there i changed some of the default stuff, like making it atom specific, and not generic.

Now it works.

Bluetooth sometimes refuces to start, so i was looking into setuid, so that i could make 2 scripts and automatically run /etc/init.d/bluetooth stop and then start, because running that without root privileges does nothing.

But i had other things to do.

i'll take a look at your links.

ps: i never thought i would be so masively ignored here :P

---

### Post by Le@ndro on 2011-03-02
Wooow... so I think I'll need a degree on programming to get it working... compiling a kernel does sound scarier than compiling a driver. I'm an absolute noob on those subjects.

On the other subject: I think the "ignored" situation is just because not many people wants a dual core laptop with great battery life, they prefer a more powerful ION one? I mean, in Amazon there's not even one review!!!

Cheers!

---

### Post by rcocchiararo on 2011-03-03
i didn't do much "manual" compiling of the kernel myself this time.

The app does most of the work for you :P

i did went over the configuration it had selected, removed some hardware support i considered useless for me, and changed from generic cpu to ATOM.

---

### Post by Le@ndro on 2011-03-11
Hi! So I've been fooling around with my new ASUS 1215p an my experience was exactly the opposite from yours! In my case, I could use the Ethernet adapter with no problem... LUCKILY because I wasn't able to activate the restricted drivers for the WiFi until I updated Ubuntu... so I ended doing the hole installation/actualization process by Ethernet cable.

Now the WiFi works fine, although some times it takes a bit to start working. Problem is Bluetooth, it's not being recognized. I googled a bit and that could be because I turned it off from Wondows 7 before installing Ubuntu, and, as I didn't keep Windows I cannot undo that... is there an easy way to try Windows without having to actually install it?

On the other things, I still cannot get the mousepad gestures to work (I'm stuck with one finger use... yet), and some of the Function Keys do not work (particularly the one to turn on/off the touchpad and the one that does the same with the led screen).

Any insight in how to fix those will be greatly appreciated!!!

Good thing is that I'm getting everything working, even Compiz efects! And in battery saving mode I get 7+ hrs of intermittent use (with WiFi off, about 6+ with WiFi on -allways using Jupiter in Power Saver Mode-)  when at work. I'm really happy with the netbook! Would be nice if ASUS gave more support to Linux users.

Cheers!

---

### Post by garycollins on 2011-03-15
Has anyone found an easy way to fix this?  I actually use the hardwire ethernet connection. It keeps crashing running ubuntu 10.10 32bit..  Some mentioned rebuilding kernel which made the problem go away..  Could someone please post steps to get kernel source.. i.e. Path to kernel source.. Any specific changes I may need to make to get the ethernet stuff to work.. I read something about
building kernel BASED on ATOM..  Could you elaborate on this more?

Thanks
Gary

---

### Post by rcocchiararo on 2011-03-19
[http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)

using that tool, i compiled the kernel with little effort.

you can leave it untouched (the kernel config), or remove/change stuff.

---

### Post by Dirk Jan on 2011-04-28
> **Le@ndro said:**
> 
Now the WiFi works fine, although some times it takes a bit to start working. Problem is Bluetooth, it's not being recognized. I googled a bit and that could be because I turned it off from Wondows 7 before installing Ubuntu, and, as I didn't keep Windows I cannot undo that... is there an easy way to try Windows without having to actually install it?.

Cheers!

Hello Le@ndro,

Don't know if your bleutooth problem still persists but did you try switchting it on through BIOS settings? Hit <esc> during boot and you will find yourself in the settings.

How is your experience with the 1215p so far? I am considiring buying one and installing 11.04

Regards,
Dirk Jan

P.S. This is my first post here, but I have been using Ubuntu since 8.04

---

