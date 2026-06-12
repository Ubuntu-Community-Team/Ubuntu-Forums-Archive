---
title: "Howto install BCM1390M as used in Dell D620"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by mhosken on 2006-06-09
If you are unfortunate enough to have a Dell D620 without the Intel wireless, getting the Dell 1390 wireless working can be tricky. Dell uses a Broadcom chip with an internal code of 0x4311 so this is sometimes referred to as a BCM4311.

The Linux kernel ships with a Broadcom wireless driver: bcm43xx, but looking at its strings I notice that it doesn't list the 4311 as one of its supported devices, so that is not going to work. Instead we need to use the older ndiswrapper approach.

But the ndiswrapper that ships with Dapper is rather old, v1.8, and doesn't work for this, and so instead we need to use an up to date version, v1.17, is the current release) - come on guys :rolleyes: 

I'm sure someone can refine this howto, but this I know works.

To build the latest ndiswrapper, download the tarball from: [http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.17.tar.gz?download]("http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.17.tar.gz?download") . In addition various dependencies need to be satisfied:

```
sudo apt-get install build-essential linux-headers-386 linux-headers-686
tar xvzf ndiswrapper-1.17.tar.gz
cd ndiswrapper-1.17
make
sudo make install
```

Extracting the firmware from the Dell windows drivers is a bit tricky. Download it from here: [R115321.EXE]("http://ftp.us.dell.com/network/R115321.EXE") and use wine (I used the latest 0.9.15) to run and extract the files. There is no need to actually run the installer, and mine crashed. The files you need are by default in ~/.wine/drive_c/dell/drivers/R115321/DRIVER. Since the driver is freely available, I enclose a .zip with the necessary files in to save the wine step. If you use that then change the cd command below accordingly.

```
cd ~/.wine/drive_c/dell/drivers/R115321/DRIVER
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
```

To test that everything works, manually load the ndiswrapper module and use dmesg to check that it ran OK:

```
sudo modprobe ndiswrapper
dmesg
```

From then on, you should see the wireless led lit, and be able to use the switch, etc.

---

### Post by animatt on 2006-06-09
Good post.  I just actually just figured this out myself and just came to post to help someone out.  

Just a few quick questions.

Did you need to edit the blacklist file.  I edited mine not sure it helped at all.  I also ran ndiswrapper with the -di and -da options as well.  NOt sure that was necessary either but I was getting tired of trying to get it to work

Oh also just a quick pointer.  The .exe file is/was a self extracting .zip file so you can just rename to .zip and unzip rather than running wine.  Much easier.  I just figured that trick out when I had to deal with the same file in question.

---

### Post by boakes on 2006-06-11
This worked for my Broadcom 4311 in a Dell e1705.

---

### Post by mick2021 on 2006-06-13
Thank you for posting it.  Finally got the wireless working on my d620.
Been trying to get it work over a month.  I am so happy!!!
:D

---

### Post by robgue on 2006-06-14
wow! it finally worked for me. thank you very much. i've tried so many other guides.
just a tip for those of you that have had many unsucessful attempts. i would run:
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

i got that from another guide as i tried this guide just twice. worked after removing other junk.
again thanks alot. i finally got everything going good on my e1505.

---

### Post by boakes on 2006-06-14
If you wanted to upgrade to a new kernel, how would you remove the previous installation so it would work with the new?  Also would it be possible to have it working on both kernels?  I'm currently running the 386 kernel and want to upgrade to the 686 smp.

---

### Post by scwoodal on 2006-06-14
This also worked for me as well, but I had to do one additional step. I was getting the error "FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument" . The stock Ubuntu kernel shipped with a "ndiswrapper.ko" module already installed. When I downloaded the v1.17 ndiswrapper source, I issued 

```

make uninstall

```

before running "make" and this removed the old module that ships with the stock dapper kernel and then everything started working. And just another step saver, you don't have to rename the .EXE file to .ZIP in order to unzip it

---

### Post by neuropsychguy on 2006-06-17
Thanks mhosken and others for telling me how to get that wireless card working. It was becoming a major pain. Props to you! I now have ubuntu working well on my E1505! :)

---

### Post by tirofiban on 2006-06-18
What about this and WPA and network manager???

These instructions worked great. My WiFi light on my Dell E1505 turned on and I can use Wifi with the Ubunu Networking program. 

But when I comment out all my interfaces except lo in etc/network/interfaces, the Wifi light turns off and Network manager doesn't see any wireless. If I uncomment WLAN0, network manager sees the wifi card and wireless networks, but can't connect.

Is anyone else having this problem with the Dell 1390, NDISWRAPPER and network manager?

---

### Post by Rebecca354 on 2006-06-22
I get the following error when I go to make

Can't find kernel build files in /lib/modules/2.6.15-23-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make

---

### Post by acowan99 on 2006-06-27
hey all, i am a first time linux user and i just got my Dell D620 in the mail and wanted to put linux on it so i did. Im not using ubuntu and im not sure if what u guys are talking about will work for me. Is this a fix for all/most linux's or will it only work with ubuntu?

PS. i am using a distro if that means anything.

---

### Post by boakes on 2006-06-29
[QUOTE=acowan99]hey all, i am a first time linux user and i just got my Dell D620 in the mail and wanted to put linux on it so i did. Im not using ubuntu and im not sure if what u guys are talking about will work for me. Is this a fix for all/most linux's or will it only work with ubuntu?

PS. i am using a distro if that means anything.[/QUOTE]What distro are you using?

[QUOTE=Rebecca354]I get the following error when I go to make

Can't find kernel build files in /lib/modules/2.6.15-23-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make[/QUOTE]
You need to install the kernel headers for your kernel. 

```
$ sudo apt-get install linux-headers-386
``` (if you're using the 386 kernel) i think is the command, or just use synaptic and search for 386.

---

### Post by acowan99 on 2006-06-29
i am using whoppix 2.7.1

---

### Post by spiritofreason on 2006-06-30
Ahhhh, I wish I could have the same success.  The wireless card only works momentarily before I have interrupt issues.  Dmesg outputs the following as it kills wireless functionality:

[4295830.250000] irq 177: nobody cared (try booting with the "irqpoll" option)
[4295830.250000]  [<c014c73a>] __report_bad_irq+0x2a/0xa0
[4295830.250000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295830.250000]  [<c014c857>] note_interrupt+0x87/0xf0
[4295830.250000]  [<c014c02d>] __do_IRQ+0xfd/0x110
[4295830.250000]  [<c0105c99>] do_IRQ+0x19/0x30
[4295830.250000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295830.250000]  [<c0111e49>] get_offset_pmtmr+0x19/0x1d0
[4295830.250000]  [<c01083ef>] do_gettimeofday+0x1f/0xd0
[4295830.250000]  [<c0129d07>] sys_gettimeofday+0x27/0xa0
[4295830.250000]  [<c0103457>] sysenter_past_esp+0x54/0x75
[4295830.250000] handlers:
[4295830.250000] [<f8e1e660>] (ndis_isr+0x0/0xe0 [ndiswrapper])
[4295830.250000] Disabling IRQ #177

I've tried several combinations of boot options to try fixing it.
irqpoll just renders the system unbootable
acpi=noirq still yields interrupt problems
acpi=force pci=noacpi had it working longer, but it yielded the same issues too

This is a Dell Inspiron E1705 w/ the True Mobile 1390 (BCM4311), using Dapper.
Any ideas on how to resolve this problem?

---

### Post by spiritofreason on 2006-07-01
Hm... perhaps I was just nutty when I booted with irqpoll before because it seems to be working fine now.  I wonder if there is anything I need to be aware of... like, what does this option do?  Somehow force a polling system with interrupts?

In any case, wireless is working! :)

---

### Post by martinhamel on 2006-07-08
Hi,

I tried "irqpoll" without success. With irqpoll, the wireless card is just working ok for a little while and stops with the same message. The difference is that the computer freeze for like 30 secondes when irqpoll is activated. 

Here id the message I get when it freeze (with irqpoll activated).
```
2006-07-08 10:59:54	localhost	kernel	[17180989.644000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20
2006-07-08 10:59:54	localhost	kernel	[17180989.644000]  [cpu_idle+111/192] cpu_idle+0x6f/0xc0
2006-07-08 10:59:54	localhost	kernel	[17180989.644000] Disabling IRQ #177
2006-07-08 10:59:54	localhost	kernel	[17180989.644000]  [__do_IRQ+253/272] __do_IRQ+0xfd/0x110
2006-07-08 10:59:54	localhost	kernel	[17180989.644000]  [do_IRQ+25/48] do_IRQ+0x19/0x30
2006-07-08 10:59:54	localhost	kernel	[17180989.644000]  [handle_IRQ_event+61/112] handle_IRQ_event+0x3d/0x70
2006-07-08 10:59:54	localhost	kernel	[17180989.644000] handlers:
2006-07-08 10:59:54	localhost	kernel	[17180989.644000] irq 177: nobody cared (try booting with the "irqpoll" option)
2006-07-08 10:59:54	localhost	kernel	[17180989.644000]  [note_interrupt+135/240] note_interrupt+0x87/0xf0
2006-07-08 10:59:54	localhost	kernel	[17180989.644000]  [pg0+943832731/1069184000] acpi_processor_idle+0x184/0x32d [processor]
2006-07-08 10:59:54	localhost	kernel	[17180989.644000] [pg0+947062368/1069184000] (ndis_isr+0x0/0xe0 [ndiswrapper])
2006-07-08 10:59:54	localhost	kernel	[17180989.644000]  [__report_bad_irq+42/160] __report_bad_irq+0x2a/0xa0
2006-07-08 10:59:54	localhost	kernel	[17180989.644000]  [start_kernel+410/512] start_kernel+0x19a/0x200
2006-07-08 10:59:54	localhost	kernel	[17180989.644000]  [unknown_bootoption+0/496] unknown_bootoption+0x0/0x1f0

```

I also tried acpi=noirq to no avail.

Does anybody have the same comportement or am I alone in the world?

---

### Post by martinhamel on 2006-07-09
I figured out that there is a link with my nvidia card. If I use the "nv" default driver, everything is ok. If I switch to the "nvidia" driver, the irq problem comes back and my wifi card becomes innactive after a while. 

The "nv" driver mean no 3D and bad acpi suspend support. :-(

I'm still stuck.

---

### Post by emaz on 2006-07-09
My portable is a Dell Inspiron 6400. I have the wireless card "Dell 1390" but it is not detected by ubuntu 6.06. When I do 'make' in the directory 'ndiswrapper...' I receive the next error:

[I]Can't find kernel build files in /lib/modules/2.6.15-23-386/build;
give the path to kernel build directory with
KBUILD=<path> argument to make[/I]

I've installed the kernel headers.

Can you help me? Thanks.

---

### Post by spiritofreason on 2006-07-10
OK, so it turns out irqpoll didn't work for me either.  I have the same problems you do, martinhamel.  It just happened to work for a good two hours for me, so I thought I was done.  Little did I know... I'll try out the nv driver too and see what happens.  Perhaps it's a problem Nvidia needs to fix.

@emaz: Did you have a file named /lib/modules/2.6.15-23-386/build? Maybe you installed the headers for a different version of the kernel?  If you didn't install the meta package, when you update to a newer kernel, you have to install the corresponding headers. For good measure, do a ```
sudo apt-get install linux-headers-2.6.15-23-386
```

---

### Post by johnnyloot on 2006-07-14
I am getting the same cant find kernel build files,

I would really love some help on this, been struggling to get it for 3 days

---

### Post by Gamebeavis on 2006-07-17
Ok, I followed the tutorial. Got the driver installed (yay). Now Knetworkmanager shows that I can enable/disable wireless, but my card still dosnt show up in the network settings (where my wired connections do). I commented out all of the pertenent lines in the configuration file that was mentioned, but STILL no listing of my card. When I check with ndiswrapper, it tells me my card is recognized, and the driver installed. Why cant I see my card??

I heard that there is native support in kernel 2.6.17, but when I tried to update my Ubuntu Dapper, with the kernel 2.6.17-5 from edgy, it seriously broke my samba, something about locals. I also tried to compile my own, but being a novice, when I was asked the 200 yes/no/maybe questions about its configuration, I think I did it wrong, so that was a no go either. Would getting 2.6.17 to run fix my problem with my wireless card, if so I am willing to keep trying to get it to run.

---

### Post by mxmike on 2006-07-25
I have the same Wireless card on a Dell E1505 inspiron, any ideas on this invalid argument error

mike@mike-alpha:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

---

### Post by spiritofreason on 2006-07-25
Looks like you need to rebuild and install the module.  Did you update your kernel recently?

So it seems that if you have the nvidia card on the E1705/9400, you can get the wireless to work if you don't use nvidia's proprietary driver or if you only use the 386 kernel.  Hm... maybe it's time I posted a bug on launchpad...

---

### Post by eus107709 on 2006-08-16
Okay, please disregard this post.  I'm an idiot.. just realized I had a space in "Installation Files".



I had gotten the Broadcom 4311 working properly a couple of months ago with basically the same steps using ndiswrapper.  Unfortunately, I ran the updates for Ubuntu and my wireless is no longer working.  I'm trying to reinstall ndiswrapper now, but I'm having no luck with "make".  Any help is appreciated.
-------------------------------------------
make -C driver
make[1]: Entering directory `/home/frank/Installation Files/ndiswrapper-1.17/driver'
make -C /lib/modules/2.6.15-26-686/build SUBDIRS=/home/frank/Installation Files/ndiswrapper-1.17/driver \
                DRIVER_VERSION=1.17
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-26-686'
make[2]: *** No rule to make target `Files/ndiswrapper-1.17/driver'.  Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-26-686'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/frank/Installation Files/ndiswrapper-1.17/driver'
make: *** [all] Error 2

---

### Post by acrossbetween on 2006-08-17
just wanted to report that my bcm4311 from broadcom in a dell e1505 worked with your instructions! Thank you very much for you contribution!

---

### Post by netposer on 2006-08-17
Thanks. I'm new to Linux once again and these directions worked on my Lattitude D820 running Ubuntu 6.06.

But as a previous poster asked; WPA support?

---

### Post by ivanst on 2006-08-22
The latest version of kubuntu 6.06.1 almost had wireless almost working on my D620 with this guide. Just add the line below to /etc/modprobe.d/blacklist

blacklist bcm43xx

I think the newer version was conflicting with ndiswrapper and trying to load a conflicting driver for the same hardware.

---

### Post by andiii on 2006-08-22
> **ivanst said:**
> Just add the line below to /etc/modprobe.d/blacklist

blacklist bcm43xx

I think the newer version was conflicting with ndiswrapper and trying to load a conflicting driver for the same hardware.

And that solved the problem for me, thank you! How good it feels to see the Wifi LED glowing with Ubuntu.

---

### Post by jedleman on 2006-09-01
First of all, I want to say thank you.  This is the closest I have come to getting my wireless up and running.  I followed the steps and I was able to connect!!!  But, upon reboot my wireless light stayed on, but I lost both the connection and the entry in my network manager.  So, I ran 

sudo modprobe ndiswrapper 

and I saw the wlan0 in my network manager.  But, I could not connect. I deactivated it and reactivated it and it worked.  Then it dropped and I am right back to where I started from with it lit, but not in network manager.

 What steps can I take now to continue to use my wireless?  Please lord, don't make me go back to windows.

I found another post where someone said to blacklist bcm43xx

I tried that with no affect to the performance.

So I am real close, but need some newbie guidance...

What could I post to give you guys more info to go on?


MORE INFO:
jedleman@jedleman-laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present
jedleman@jedleman-laptop:~$

jedleman@jedleman-laptop:~$ ndiswrapper -v
utils version: 1.8
driver version:        1.17rc2
vermagic:       2.6.15-26-386 preempt 486 gcc-4.0

jedleman@jedleman-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:6A61-736F-6E   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




Thanks in advance,
Jason

---

### Post by jaktylr on 2006-09-15
Hi, my name is Jake and I am new to Ubuntu and linux in general.  I have been trying the tips and suggestions on this forum and others, and nothing seems to work.  Could anybody possibly post a step by step instruction on how to get the wireless working.  I have a Dell E1705.  For the guide, could you start from the beginning and assume nothing.  Like start the guide at what you should do after a fresh install of ubuntu.  IT would be greatly aprreciated.

Thanks, Jake.

---

### Post by jaktylr on 2006-09-15
Also, I think Im pretty sure my kernel is 2.6.15-26-386.  Sorry if my post is super noobish, but I want to be a dedicated linux user because of its great benefits over Windows and Mac OSX. Again, Thanks.

---

### Post by jaktylr on 2006-09-17
Okay I am having trouble because of ndiswrapper.ko that came with Dapper.  When I go back and repeat the installation process and try to remove it, I get this message

 Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
/bin/rm: cannot remove `/sbin/loadndisdriver': Permission denied
make: *** [uninstall] Error 1


How should I repeat the installation process so I can remove the ndiswrapper.ko file that is causing this conflict?

---

### Post by ilushkin on 2006-10-05
I did as you suggested and I get this once i run dmesg:
.
[17179596.508000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179596.624000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'strrchr'
[17179596.624000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmFreeContiguousMemorySpecifyCache'
[17179596.624000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmAllocateContiguousMemorySpecifyCache'
[17179596.624000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmGetPhysicalAddress'
[17179596.624000] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
[17179596.624000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

what do i do next?

---

### Post by dragonfixed on 2006-10-06
Thanks for the great guide i am new to linux running kbuntu v6.0.6.1 and have a dell inspirion 9400 with a dell 1390 wireless which is a broadcom 1390 chipset

---

### Post by madhurjain on 2006-10-06
Thanks man,
i hope it works,
as i am really interested in dumping windows for good,
am sick n tired of it

---

### Post by twade on 2006-10-16
This how-to worked for me (Compaq V3000 with BCM4311) to some extent.  It connects fine at home (128 bit wep, broadcast essid) but not at work (64 bit wep, hidden essid).  In windows XP, both networks work fine.

the sudo ifup wlan0 command gives the following output:

```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan/XX.XX.XX.XX.XX.XX
Sending on   LPF/wlan/XX.XX.XX.XX.XX.XX
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
... etc ...
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping
```

I'm quite sure an ip address should be obtained using DHCP and that my essid and wep are correct in /etc/network/interfaces.
Any suggestions would be most appreciated.

---

### Post by twade on 2006-10-16
I should add that if I use

```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid XXXXX
sudo iwconfig wlan0 key open XXXXXXXXXX
sudo ifconfig wlan0 up
```

and then wait through several minutes of apparent inactivity, it does eventually connect.

---

### Post by Ryrie on 2006-10-25
> **twade said:**
> This how-to worked for me (Compaq V3000 with BCM4311) to some extent.  It connects fine at home (128 bit wep, broadcast essid) but not at work (64 bit wep, hidden essid).  In windows XP, both networks work fine.

the sudo ifup wlan0 command gives the following output:

```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan/XX.XX.XX.XX.XX.XX
Sending on   LPF/wlan/XX.XX.XX.XX.XX.XX
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
... etc ...
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping
```

I'm quite sure an ip address should be obtained using DHCP and that my essid and wep are correct in /etc/network/interfaces.
Any suggestions would be most appreciated.

 twade,

Did you ever find a solution to this.  I pretty much have the same situation happening to me except I NEVER get a DHCP address when I'm using the work wireless(128bit WEP, hidden ESSID)  I have been waiting about 10min and it's not getting a thing.  I can connect just fine to home AP with 128bit WEP and un-hidden ESSID.

Any help would be appreciated.

PS.  mhosken, thanks so much for the great how-to.  I had tried many others and could never get the wireless card to turn on or show up as a device.  Thanks again.

Ryrie

---

### Post by Ryrie on 2006-10-26
Well it looks like my problems are solved.  Since Edgy was released I decided to do the upgrade.  The upgrade worked like a champ and now my wireless card works flawlessly.  I got an IP address on my wireless card after the reboot from the upgrade.

All is right with the world.

---

### Post by Jamie Jackson on 2006-11-19
I'm trying to follow along. I've got a D620/Edgy, and this crummy wireless adaptor.

Here's the stuff I've compiled as I understand it, and here are the commands I've run. The following is not a script (don't know bash scripting well enough), it's just individual commands I've run, with some notes.

(Please let me know if you see anything wrong with this part, but my problem manifests itself in the snippet that follows this one.)

```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils wireless-tools
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

cd /media/sda9/garbage

sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-2.6.17-10-generic /lib/modules/2.6.17-10-generic/build
sudo apt-get install wireless-tools ndiswrapper-utils

# downloaded:
#   http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=superb-east&filename=ndiswrapper-1.28.tar.gz&51909466
# to:
#   /media/sda9/garbage

tar -zxvf ndiswrapper-1.28.tar.gz
# the above didn't work, so I unpacked manually
# ran it in wine, and ended up with drivers in ~/.wine/drive_c/dell/drivers/R115321/DRIVER

cd ndiswrapper-1.28
make uninstall
make 
sudo make install
cd /media/sda9/garbage

cd ~/.wine/drive_c/dell/drivers/R115321/DRIVER
 
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
```

Then, I get the following:

```
jamie@mercury:~/.wine/drive_c/dell/drivers/R115321/DRIVER$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
jamie@mercury:~/.wine/drive_c/dell/drivers/R115321/DRIVER$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 717.

```

That last line is the sad news; however, I don't know what it means or how to fix it.

Then, dutifully following the original poster's final instructions I get:

```
jamie@mercury:~/.wine/drive_c/dell/drivers/R115321/DRIVER$ sudo modprobe ndiswrapper
jamie@mercury:~/.wine/drive_c/dell/drivers/R115321/DRIVER$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
<snip a LOT of stuff, let me know what, if any of it, is worth posting for troubleshooting>

```

And no wifi LED. :( 

UPDATE: I left the machine alone for a while (hours), and when I came back, the wifi LED was lit?!?! I scanned for networks with KWifiManager, and actually saw networks, but could only connect for a second before it "dropped." I guess I have a different problem, and will reread through the thread to see if anyone had anything similar.

Thanks,
Jamie

---

### Post by Jamie Jackson on 2006-11-28
[This]("http://ubuntuforums.org/showpost.php?p=1780571&postcount=12") got me going.

Jamie

---

### Post by Jamie Jackson on 2006-11-30
And now I've got it going with WPA, NetworkManager, and NDISWrapper. I modified [this wiki]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#preview") to document what I did.

Thanks,
Jamie

---

### Post by jimspoon on 2007-01-24
Thank you very much for the info.  This worked for me using an HP pavilion dv1000 with which I had become somewhat frustrated.

Gracias

---

### Post by cheenu on 2007-02-25
Worked like a charm.

Thanks
Cheenu

---

### Post by joyolee on 2007-03-17
hi~ 

thx for the tips

but my wireless card still does not work~

it seems like there's something wrong with the bcmwl5 drive?

```

 ndiswrapper -l

bcmwl5 : invalid driver!



```

---

### Post by CrypticBlade on 2007-03-21
You might try this: [http://sourceforge.net/projects/lc4ul/]("http://sourceforge.net/projects/lc4ul/")

Regards,
CB

---

### Post by Jamie Jackson on 2007-07-06
Note, I posted a simplified howto for this card under Feisty [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). It should take under 5 minutes to get everything including WPA going, and it requires no compilation.

---

