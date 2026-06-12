---
title: "Errors from NDISWrapper with Dell Wireless 1390"
date: 2006-03-05
forum: Networking &amp; Wireless
---

### Post by directedition on 2006-03-05
It seems hardly anyone has the Dell 1390 chip and there are certainly no Linux drivers for it, so I thought I'd give NDISWrapper a try. Everything works fine until I modprobe ndiswrapper. No visible errors are given till I run dmesg. This is what the syslog gives me (using Dapper):

Mar  5 16:29:31 ubuntu loadndisdriver: loadndisdriver: load_driver(361): couldn't load driver bcmwl5 
Mar  5 16:29:31 ubuntu kernel: [4373482.946000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
Mar  5 16:29:31 ubuntu kernel: [4373482.949000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'strrchr'
Mar  5 16:29:31 ubuntu kernel: [4373482.949000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmFreeContiguousMemorySpecifyCache'
Mar  5 16:29:31 ubuntu kernel: [4373482.949000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmAllocateContiguousMemorySpecifyCache'
Mar  5 16:29:31 ubuntu kernel: [4373482.949000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmGetPhysicalAddress'
Mar  5 16:29:31 ubuntu kernel: [4373482.949000] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
Mar  5 16:29:31 ubuntu kernel: [4373482.950000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

I get the exact same errors on Knoppix. Does anyone know these errors?

---

### Post by Nolgthorn on 2006-04-07
Thanks for the tip. I won't buy that one then.

---

### Post by lee_connell on 2006-04-19
I have same chipset.  I am having problems too but mine are different.  when i use ndiswrapper-utils it complains that it can't read one of the conf files in the ndiswrapper dir.  I looked at the conf files and they are all BLANK?  

What's the deal here?  i followed directions on the howto, confused?

I also tried using bcm open source driver and cutting up the firmware and it doesn't even try to load them, not sure what's up here either.

---

### Post by lee_connell on 2006-04-19
[http://www.benwired.com/2006/03/15/my-new-laptop-dell-e1505/](http://www.benwired.com/2006/03/15/my-new-laptop-dell-e1505/)

---

### Post by lee_connell on 2006-04-19
downloading latest ndiswrapper has worked as far as the system recognizing it and listing it as a valid network device, but now my wireless light doesn't come on and am not sure if its a software switch or not?

---

### Post by lee_connell on 2006-04-19
I've tried using the bcm43xx firmware and the module however i get this:

sudo modprobe bcm43xx

FATAL: Module bcm43xx not found.

what is up with that? isn't that a built-in module?

---

### Post by lee_connell on 2006-04-20
seems as SMP processor on duo core was causing the issue.

---

### Post by blink2401 on 2006-04-21
where you able to get this to work? I have a friend that I am attempting to get his 1390 card up and running and the only error I can find is 

[4294690.541000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:strrchr
[4294690.541000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmFreeContiguousMemorySpecifyCache
[4294690.541000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmAllocateContiguousMemorySpecifyCache
[4294690.541000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmGetPhysicalAddress
[4294690.541000] ndiswrapper (load_sys_files:456): unable to prepare driver 'bcmwl5'
[4294690.541000] ndiswrapper (ndiswrapper_load_driver:92): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver'

---

### Post by shanep on 2006-04-21
Try using windows 2000 drivers. If they are availible for your device.

---

### Post by lee_connell on 2006-04-21
i did get it working and it works very slick too.

i will post you the steps i took later today as i have to get to work.

---

### Post by jebolles on 2006-05-03
I am having the same problem with a Dell E1705.  Lee, if you have a solution for this issue, please post it to the forum.  Thanks!  JEB

---

### Post by lee_connell on 2006-05-04
Hi,

Sorry bout not posting back here.  First off you have to grab the latest ndiswrapper from sourceforge.net and compile it on your system.

then you follow the ndiswrapper howto in ubuntuforums, one step that you do NOT follow is the bash script that loops and edits the ndiswrapper conf files.  skip that step and move on.

it worked for me, if you need more details i'll try to get back asap later on as im at work now.

---

### Post by digitalextortion on 2006-05-04
I would love a detailed explanation as I was unable to get the latest ndiswrapper installed ( errors ) on my e1705 if your up for it :)

---

### Post by lee_connell on 2006-05-04
what errors are you getting?

---

### Post by lee_connell on 2006-05-06
Well have you guys been able to do it, or produce some errors?

---

### Post by pspierce on 2006-05-11
Anything further you can add to this would be great.  My ndiswrapper install all looks good; however, I have no signal.  It seems the card needs to be turned "on" but FN+F2 isn't working.  atkbd error in syslog when I try.

---

### Post by pspierce on 2006-05-11
[QUOTE=pspierce]Anything further you can add to this would be great.  My ndiswrapper install all looks good; however, I have no signal.  It seems the card needs to be turned "on" but FN+F2 isn't working.  atkbd error in syslog when I try.[/QUOTE]

Fixed it.  Somewhere I was told to change RadioState|0 to |1.  It needs to be |0.

---

### Post by lee_connell on 2006-05-12
Yes, that's why at the beginning of this thread I said do not run the bash script that loops through those files and changes radio state.

If you leave that step out you're good.

---

### Post by robgue on 2006-05-24
any chance of writing a little "how to" here to set the 1390 up for those who haven't gotten it working yet?

---

### Post by saintpa on 2006-07-05
I just got mine working, thanks to all the posters that provided helpful information. Here's a simple howto:

1. You need to get the compilers and linkers in order to compile the ndiswrapper kernel module and userland utilities:
#sudo apt-get install build-essential
2. You need to get the kernel header files. There are several options here depending on what kernel you are using. Since I use the linux-686-smp, I grabbed the 686 kernel header:
#sudo apt-get install linux-headers-2.6.15-25-686
Note: linux-headers-2.6.15-25-686 depends on linux-headers-2.6.15-25-386. So you will have two linux-headers directories showing up in /usr/src directory. Don't remove the 386 directory!
3. Download the latest ndiswrapper STABLE release 1.19 tar ball from ndiswrapper.sourceforge.org and place it in /usr/src
4. Unpack the source tar ball:
#sudo tar xzvf ndiswrapper-1.19
5. Read the INSTALL file in ndiswrapper-1.19 directory.
6. Build the kernel module and utilities:
# cd /usr/src/ndiswrapper-1.19
# sudo make uninstall
# sudo make
# sudo make install
7. Remove the old ndiswrapper module in case you already inserted it in kernel:
# sudo modprobe -r ndiswrapper
8. Reinstall the winows driver:
# sudo ndiswrapper -e bcmwl5
# sudo ndiswrapper -i /lib/windrivers/bcmwl5.inf
Note that if your winows drivers are located elsewhere, change the /lib/windrivers/ to wherever you saved the windows drivers. I won't get into details about how to get the drivers.
9. Insert the kernel module
# sudo modprobe ndiswrapper
Your 1390 wireless card should be working by now. If you have problems with any steps, just ask questions.

---

### Post by csc14us on 2006-08-10
Whoever posted that mini-howto above, you're my pal!  It really helped a lot.  The ndiswrapper packages don't work, for some reason.  I just uninstalled them and went with the source code version.

Thanks!

---

### Post by mattjcowan on 2006-09-16
Thanks for the directions as well.
I just loaded Ubuntu, and Linux for the first time yesterday, and thought this was going to be an issue.

This made it work on my Dell E1705, using Broadcom Corporation BCM4401, and my Dell Wireless 1500, Minicard. :D 

One thing that tipped me off to search for this forum was looking at the kern.log file.

Sep 16 12:11:53 localhost kernel: [17179587.532000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
Sep 16 12:11:53 localhost kernel: [17179587.632000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'IoGetDeviceObjectPointer'
Sep 16 12:11:53 localhost kernel: [17179587.632000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmFreeContiguousMemorySpecifyCache'
Sep 16 12:11:53 localhost kernel: [17179587.632000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmAllocateContiguousMemorySpecifyCache'
Sep 16 12:11:53 localhost kernel: [17179587.632000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmGetPhysicalAddress'
Sep 16 12:11:53 localhost kernel: [17179587.632000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'strrchr'
Sep 16 12:11:53 localhost kernel: [17179587.636000] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
Sep 16 12:11:53 localhost kernel: [17179587.636000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

After applying your instructions, the kern.log showed everything was good to go:

Sep 16 14:44:48 localhost kernel: [17179585.832000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 177
Sep 16 14:44:48 localhost kernel: [17179585.836000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:15:c5:4a:1c:20
...
Sep 16 14:44:49 localhost kernel: [17179586.164000] ndiswrapper version 1.23 loaded (preempt=yes,smp=yes)
Sep 16 14:44:49 localhost kernel: [17179586.260000] ndiswrapper: driver bcmwl5 (Broadcom,06/21/2006, 4.80.28.5) loaded
...
Sep 16 14:44:49 localhost kernel: [17179586.908000] wlan0: ethernet device 00:16:cf:25:7e:f9 using NDIS driver bcmwl5, 14E4:4328.5.conf
Sep 16 14:44:49 localhost kernel: [17179586.908000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

Thanks again!

---

### Post by ilushkin on 2006-10-09
> **saintpa said:**
> I just got mine working, thanks to all the posters that provided helpful information. Here's a simple howto:

1. You need to get the compilers and linkers in order to compile the ndiswrapper kernel module and userland utilities:
#sudo apt-get install build-essential
2. You need to get the kernel header files. There are several options here depending on what kernel you are using. Since I use the linux-686-smp, I grabbed the 686 kernel header:
#sudo apt-get install linux-headers-2.6.15-25-686
Note: linux-headers-2.6.15-25-686 depends on linux-headers-2.6.15-25-386. So you will have two linux-headers directories showing up in /usr/src directory. Don't remove the 386 directory!
3. Download the latest ndiswrapper STABLE release 1.19 tar ball from ndiswrapper.sourceforge.org and place it in /usr/src
4. Unpack the source tar ball:
#sudo tar xzvf ndiswrapper-1.19
5. Read the INSTALL file in ndiswrapper-1.19 directory.
6. Build the kernel module and utilities:
# cd /usr/src/ndiswrapper-1.19
# sudo make uninstall
# sudo make
# sudo make install
7. Remove the old ndiswrapper module in case you already inserted it in kernel:
# sudo modprobe -r ndiswrapper
8. Reinstall the winows driver:
# sudo ndiswrapper -e bcmwl5
# sudo ndiswrapper -i /lib/windrivers/bcmwl5.inf
Note that if your winows drivers are located elsewhere, change the /lib/windrivers/ to wherever you saved the windows drivers. I won't get into details about how to get the drivers.
9. Insert the kernel module
# sudo modprobe ndiswrapper
Your 1390 wireless card should be working by now. If you have problems with any steps, just ask questions.
i get:
 ADDRCONF(NETDEV_UP): wlan0: link is not ready
once i run dmesg
I did all instructions ( i have dell 1390 on E1505)

---

### Post by ilushkin on 2006-10-09
wow. disregard my last post. Your tutorila really worked! thank you so much!

---

### Post by EnigmaThe0rem on 2006-10-10
When I go to place the ndiswrapper files into /usr/src I keep getting a window saying I dont have permission to do this anybody have any idea why this does this?

---

### Post by mekas2024 on 2006-10-11
> **saintpa said:**
> I just got mine working, thanks to all the posters that provided helpful information. Here's a simple howto:

1. You need to get the compilers and linkers in order to compile the ndiswrapper kernel module and userland utilities:
#sudo apt-get install build-essential
2. You need to get the kernel header files. There are several options here depending on what kernel you are using. Since I use the linux-686-smp, I grabbed the 686 kernel header:
#sudo apt-get install linux-headers-2.6.15-25-686
Note: linux-headers-2.6.15-25-686 depends on linux-headers-2.6.15-25-386. So you will have two linux-headers directories showing up in /usr/src directory. Don't remove the 386 directory!
3. Download the latest ndiswrapper STABLE release 1.19 tar ball from ndiswrapper.sourceforge.org and place it in /usr/src
4. Unpack the source tar ball:
#sudo tar xzvf ndiswrapper-1.19
5. Read the INSTALL file in ndiswrapper-1.19 directory.
6. Build the kernel module and utilities:
# cd /usr/src/ndiswrapper-1.19
# sudo make uninstall
# sudo make
# sudo make install
7. Remove the old ndiswrapper module in case you already inserted it in kernel:
# sudo modprobe -r ndiswrapper
8. Reinstall the winows driver:
# sudo ndiswrapper -e bcmwl5
# sudo ndiswrapper -i /lib/windrivers/bcmwl5.inf
Note that if your winows drivers are located elsewhere, change the /lib/windrivers/ to wherever you saved the windows drivers. I won't get into details about how to get the drivers.
9. Insert the kernel module
# sudo modprobe ndiswrapper
Your 1390 wireless card should be working by now. If you have problems with any steps, just ask questions.


Hey dude, i have this problem
When i do this i get this error :S :
mekas@mekas-laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-amd64-generic/misc/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I have installed the 1.19 like u!

do u know what can i do, i cant install my wireless, im in ubuntu 64 bits.

Thanks

Regards

MeKaS

---

### Post by fwenes on 2006-10-11
Hi,
I did all the steps you posted. And Finally, I checked the driver with 
sudo ndiswrapper -l
What I received was :
Installed ndis drivers:
bcmwl5          driver present, hardware present
However when checking with iwconfig, I received :
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Could you explain what happens?
Thanks for your help.

---

### Post by mekas2024 on 2006-10-11
> **fwenes said:**
> Hi,
I did all the steps you posted. And Finally, I checked the driver with 
sudo ndiswrapper -l
What I received was :
Installed ndis drivers:
bcmwl5          driver present, hardware present
However when checking with iwconfig, I received :
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Could you explain what happens?
Thanks for your help.

I have the same problem, plus what i said in my last post :(

Please can someone help us ?

Regards

MeKaS

---

### Post by ilushkin on 2006-10-13
no wireless networks are availeble in your area...?

This thread summarized :
[http://www.networkadministrationblog.com/dell-1390-wireless-problems-on-linux-setup/](http://www.networkadministrationblog.com/dell-1390-wireless-problems-on-linux-setup/)

---

### Post by mekas2024 on 2006-10-13
Yeha, i have wireless in my place... i think the problem its something that some ppl have, and im not pretty sure but think that theres something called fwcutter or something, i saw it yesterday, but today i had to format the laptop to install ubuntu server for a project at skool, soo... as soon i finish the project i will try it :D

Thx A lot man

Regards

MeKaS

---

### Post by ilushkin on 2006-10-13
good luck with you project bro :)
This Thread summarized can be found at: 
[http://www.networkadministrationblog.com/dell-1390-wireless-problems-on-linux-setup/](http://www.networkadministrationblog.com/dell-1390-wireless-problems-on-linux-setup/)

---

### Post by fwenes on 2006-10-13
Hi mekas2024,
I haven't figured out how to make the wireless card working ](*,) . Could you show me how to do that (in case u have free time) ?
Thanks alot!!! :mrgreen:

---

### Post by Psquared39 on 2006-10-14
After a reboot my wireless is gone. Not the connection the hardware no longer shows up in network settings?????

---

### Post by mlat on 2006-10-14
> **Psquared39 said:**
> After a reboot my wireless is gone. Not the connection the hardware no longer shows up in network settings?????I'm getting the same problem here my friend. I tried the listed tutorial, and it appears to get the wlan0 driver into network manager, but I can't seem to connect to any networks (manually through terminal nor anything else), there's no tray icon for the network, and it disappears after reboot. It's as if its listed but not really working or there at all. I tried both a WEP network and a unsecured network with my router, neither one worked for me.

This is my closest bet to getting my Ubuntu completely working... any help would be much appreciated.

---

### Post by Psquared39 on 2006-10-14
The guide in this thread did get me up and running, I'm posting with the laptop now. I wanted WPA so I installed Network Manager, the wlan0 did not show up,only eth0. On a reboot the wlan0 was no longer listed in network settings. I opened the terminal to install the driver again, returned it was already installed. Went back to network settings and there was wlan0.... Havent shut down since... Still want WPA, guess I'll keep reading...

---

### Post by mlat on 2006-10-14
Finally, I got it working.

The problem was that ndiswrapper isn't starting up with ubuntu. I THOUGHT it was, but apparently the #sudo ndiswrapper -m   command doesn't work properly. All you have to do is open up /etc/modules and edit it to include ndiswrapper, and wireless works. Thanks guys!

---

### Post by ilushkin on 2006-10-17
> **mlat said:**
> Finally, I got it working.

The problem was that ndiswrapper isn't starting up with ubuntu. I THOUGHT it was, but apparently the #sudo ndiswrapper -m   command doesn't work properly. All you have to do is open up /etc/modules and edit it to include ndiswrapper, and wireless works. Thanks guys!

same problem. once restarted , its aint working
how evere i have this in etc
mdadm/               mkinitrd/            mozilla-thunderbird/
menu-methods/        modprobe.d/          mysql/
mkinitramfs/         modutils/
only :( now /modules at all :(

---

### Post by mlat on 2006-10-17
modules is a file, not a directory.

---

### Post by ilushkin on 2006-10-17
which file? sorry im a noob

---

### Post by mlat on 2006-10-17
In windows you're used to all files having extentions like file.txt or whichever. In linux, its not required, and many files are just extentionless.

If we were talking about a directory, we'd say /etc/modules/ <-- trailing slash

However, we are talking about a file at /etc/modules

So all you have to do is go to the /etc/ directory, and look for an extentionless file named modules and edit it.

Better yet, type this in terminal:
sudo gedit /etc/modules

---

### Post by ilushkin on 2006-10-17
tnahks it worked i chmod modules to 777, edited it with vi by adding one line : ndiswrapper. saved the file, restarted, and my wireless card was there. thank you everyone for your help :) God Bless You ! :)

---

### Post by mlat on 2006-10-17
> **ilushkin said:**
> tnahks it worked i chmod modules to 777, edited it with vi by adding one line : ndiswrapper. saved the file, restarted, and my wireless card was there. thank you everyone for your help :) God Bless You ! :)

I'd chmod it back to what it was before, though.

---

### Post by ilushkin on 2006-10-17
what was it by default?

---

### Post by mlat on 2006-10-17
311.

The biggest difference between windows and linux you'll find is the premission system. The rule of thumb is, never give out more premissions then you have to, because if your computer ever gets comprimised, the intruder can't do much damage if he isn't allowed to edit important files.

---

### Post by jburos on 2006-10-18
> **fwenes said:**
> Hi,
I did all the steps you posted. And Finally, I checked the driver with 
sudo ndiswrapper -l
What I received was :
Installed ndis drivers:
bcmwl5          driver present, hardware present
However when checking with iwconfig, I received :
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Could you explain what happens?
Thanks for your help.

I also have the same problem, does anyone have a suggestion?

here is what i know in case it is helpful:

# after lshw the physical id is 0 
# the network controller is on the pci bus
# there is no driver associated with the device
# there is no logical id associated with the device

also, I noticed that my ndiswrapper kernel headers use 686 not 386 though I have 2 cpus each with width 32. it seems something here is incorrect - 2x32 is not the same thing as 1x64 (or is it?). might this explain problem?

any comments would be much appreciated, this is my first go at linux. it's probably something pretty basic i don't quite understand.

jacki


---- following are some terminal commands ----


$ sudo lshw -C network
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:dfdfc000-dfdfffff irq:11


$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present


$ sudo lspci | grep Network
0000:0c:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)


$ lspci -n | grep c:00.0
0000:0c:00.0 0280: 14e4:4311 (rev 01)


$ uname -r
2.6.15-27-686


$ sudo modprobe -l | grep ndiswrapper
/lib/modules/2.6.15-27-686/misc/ndiswrapper.ko


$ lshw -C cpu
  *-cpu:0
       product: Genuine Intel(R) CPU           T2400  @ 1.83GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.14.8
       serial: 0000-06E8-0000-0000-0000-0000
       size: 1833MHz
       capacity: 1833MHz
       width: 32 bits
       <...>
  *-cpu:1
       product: Genuine Intel(R) CPU           T2400  @ 1.83GHz
       vendor: Intel Corp.
       physical id: 2
       bus info: cpu@1
       version: 6.14.8
       serial: 0000-06E8-0000-0000-0000-0000
       size: 1833MHz
       capacity: 1833MHz
       width: 32 bits
       <...>


$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by ilushkin on 2006-10-18
roger that :)
thanks

> **mlat said:**
> 311.

The biggest difference between windows and linux you'll find is the premission system. The rule of thumb is, never give out more premissions then you have to, because if your computer ever gets comprimised, the intruder can't do much damage if he isn't allowed to edit important files.

---

### Post by Psquared39 on 2006-10-22
Thanks everyone for keeping this thread going. After adding "ndiswrapper" to the /etc/modules/ folder and saving it, my wlan0 is working on each boot now. Mabey this should be added as something to check in the guide we all used from this thread. Thanks again,  PP

---

### Post by sudipta_cht on 2006-10-23
v

---

### Post by polo2883 on 2006-10-26
I did all the steps here and still nothing. I still dont get a wlan0. Can anyone help? I do know its a Dell 1390 Wireless card.

> **saintpa said:**
> I just got mine working, thanks to all the posters that provided helpful information. Here's a simple howto:

1. You need to get the compilers and linkers in order to compile the ndiswrapper kernel module and userland utilities:
#sudo apt-get install build-essential
2. You need to get the kernel header files. There are several options here depending on what kernel you are using. Since I use the linux-686-smp, I grabbed the 686 kernel header:
#sudo apt-get install linux-headers-2.6.15-25-686
Note: linux-headers-2.6.15-25-686 depends on linux-headers-2.6.15-25-386. So you will have two linux-headers directories showing up in /usr/src directory. Don't remove the 386 directory!
3. Download the latest ndiswrapper STABLE release 1.19 tar ball from ndiswrapper.sourceforge.org and place it in /usr/src
4. Unpack the source tar ball:
#sudo tar xzvf ndiswrapper-1.19
5. Read the INSTALL file in ndiswrapper-1.19 directory.
6. Build the kernel module and utilities:
# cd /usr/src/ndiswrapper-1.19
# sudo make uninstall
# sudo make
# sudo make install
7. Remove the old ndiswrapper module in case you already inserted it in kernel:
# sudo modprobe -r ndiswrapper
8. Reinstall the winows driver:
# sudo ndiswrapper -e bcmwl5
# sudo ndiswrapper -i /lib/windrivers/bcmwl5.inf
Note that if your winows drivers are located elsewhere, change the /lib/windrivers/ to wherever you saved the windows drivers. I won't get into details about how to get the drivers.
9. Insert the kernel module
# sudo modprobe ndiswrapper
Your 1390 wireless card should be working by now. If you have problems with any steps, just ask questions.

---

### Post by geber22 on 2006-11-12
> **mekas2024 said:**
> I have the same problem, plus what i said in my last post :(

Please can someone help us ?

Regards

MeKaS

Hey,

I was about where your at, and then I found this post that suggested I do this:


blacklist bcm43xx driver, by adding following line in /etc/modprobe.d/blacklist

blacklist bcm43xx

Reboot after that.

Then everything worked.


the whole post can be found here:

[http://www.pervasivecomputing.net/ubuntu_edgy_on_dell_inspiron_e1505](http://www.pervasivecomputing.net/ubuntu_edgy_on_dell_inspiron_e1505)

Good Luck I'm posting using my wireless right now.  Despite the wireless hassles I love this distro already.

---

### Post by CBowers on 2006-11-21
I am having the same issue as jburos above. Please help a newbie with his laptop?

---

### Post by lee_connell on 2006-11-21
For some reason on a new edgy install i can't get ndiswrapper to work, however bcm43xx IS working.  I did have ndiswrapper working when i did an upgrade from dapper to edgy.

Try putting your firmware in /lib/firmware/<kernel> and see if it comes up using the bcm43xx driver which is part of the kernel.

---

### Post by FrodoB on 2006-11-21
Maybe one of you experts can comment on this doc that I made from my experience with the bcm4311:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

It has worked for at least one other person so far, besides myself.  I just want to make sure that nothing has been left out.  Getting the right NDIS file seems to make all of the difference.

---

### Post by jburos on 2006-11-21
I'm no expert, but for what it's worth I had this problem, and was frustrated so for lack of a better option I undid everything (removing all installed modules, etc) and started over. Probably not what you want to hear, but for some reason the instructions worked the second time even though they did not work the first.

I'm sorry I can't talk you through this (it was a while ago) but maybe someone else can? 

Don't lose hope, your wireless will work ... :) eventually.

---

### Post by FrodoB on 2006-11-21
It is working, I just want to make sure that it is documented correctly and that other folks can follow the documentation successfully.

---

### Post by jburos on 2006-11-21
frodoB: understood, and believe me i appreciate those efforts they have helped me more times than you know (thank you). i was replying to cbower's plea for help. sorry for the confusion

---

### Post by FrodoB on 2006-11-21
Sorry for not catching that.

---

