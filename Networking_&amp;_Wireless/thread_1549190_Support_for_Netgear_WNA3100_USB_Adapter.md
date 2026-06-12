---
title: "Support for Netgear WNA3100 USB Adapter?"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by SooperDoode on 2010-08-09
Hi!

I just recently moved to a new apartment and got a new wireless setup. My roommate has the router on his computer and I have the wireless adapter on mine. I tried to connect to the internet in Ubuntu and found that I could not. I tried using ndiswrapper and a bunch of .inf and .sys files to force the adapter drivers to work and nothing happened. I even typed a bunch of stuff into the terminal (ifconfig, iwconfig etc..) and noticed that I had an eth1 connection listed and nothing else. I figured this was a problem.

I don't know much about networking and linux but would love some advice on this issue. The adapter I am trying to use is a Netgear WNA3100 Wireless USB N-300 Adapter. Is there something I can do to get this to work or is it just not going to be supported in linux?

---

### Post by SooperDoode on 2010-08-12
Anyone have any advice?  I'd really like to have internet with Ubuntu.  I think the WNA3100 adapter is absed on the Atheros chipset but I don't know which and why that is significant.  Any advice would be greatly appreciated.

---

### Post by Trazan on 2010-08-13
If you could post result from typing lsbusb in terminal we could hopefully help you...

open terminal then type
```
lsusb
```

result should be something like
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 07d1:3c0f D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by fredEbay on 2010-08-13
> **SooperDoode said:**
> Hi!

I just recently moved to a new apartment and got a new wireless setup. My roommate has the router on his computer and I have the wireless adapter on mine. I tried to connect to the internet in Ubuntu and found that I could not. I tried using ndiswrapper and a bunch of .inf and .sys files to force the adapter drivers to work and nothing happened. I even typed a bunch of stuff into the terminal (ifconfig, iwconfig etc..) and noticed that I had an eth1 connection listed and nothing else. I figured this was a problem.

I don't know much about networking and linux but would love some advice on this issue. The adapter I am trying to use is a Netgear WNA3100 Wireless USB N-300 Adapter. Is there something I can do to get this to work or is it just not going to be supported in linux?

SooperDoode - 

I have a WDNA3100v2 on an old Dell Latitude D600, dual boot w/xp. I can't remember the exact procedures, but you might try going to the top panel of Ubuntu (assuming Lucid is your OS), click system, administration, windows wireless drivers and add the correct driver for your wireless stick.

If 'windows wireless drivers' is not in the system|administration menu, you may have to install it (use the SPM - synaptic program manager). It may already be installed but not set into your menus.

The driver I used is bcmwlhigh5 which can be found in a couple of ways; 
I got it from my winxp installation for the netgear stick - c:\program files\netgear\wnda3100v2\driver\winxp2000\

There are supposedly some copies of this driver 'in the wild' so to speak, but I did not have to use them nor desired to use one of them. Apparently the mfr's drivers can only be extracted from the install CD via - what else, installing them.

Essentially, I am using the ndiswrapper for the wireless driver from netgear. works pretty good, but I have a problem trying to get connected to one of my wifi routers via ubuntu, a netgear unit with a main [?administrative) and a 'guest' profile. 

XP has no problems with any of my 4 wifi units (routers and an AP), ubuntu will not connect with my netgear sticks (also have a wn111v2) to the one particular router, although the same connection settings in network manager will allow me to connect to all wifi radios here via my linksys wpc54g. 

Hope at least the windows wireless drivers (ndiswrapper) will help you get closer. 

If this gets you closer but no joy, search thru the absolute beginners forum for posts containing ndiswrapper, netgear, windows wireless drivers. I will try to keep an eye on your thread as well and will see if I can find a more specific relative post which should be in my browser history but this goes back a couple months.


Good luck, enjoy.

---

### Post by mglynch67 on 2010-08-23
I have the same problem with the NetGear WNA3100.
I have a PC with XP and just added a partition with Ubuntu 10.04.
I have followed: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
In summary:

[LIST=1]
[*]mike@mike-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwlhigh5 : driver installed
    device (0846:9020) present

mike@mike-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mike@mike-desktop:~$
[*]mike@mike-desktop:~$ uname -m
i686
[*]mike@mike-desktop:~$ sudo lshw -C Network
[sudo] password for mike: 
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 02
       serial: 00:0f:1f:70:42:84
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000  driverversion=7.3.21-k5-NAPI duplex=full firmware=N/A ip=192.168.1.103  latency=64 link=yes mingnt=255 multicast=yes port=twisted pair  speed=100MB/s
       resources: irq:18 memory:fcfe0000-fcffffff ioport:df40(size=64)
mike@mike-desktop:~$
[*]mike@mike-desktop:~$ lsmod | grep ndis
ndiswrapper           184677  0
[*]mike@mike-desktop:~$ dmesg | grep -e ndis -e wlan
[   14.508061] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   15.628443] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[   15.628878] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh5'
[   15.629642] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[   15.629766] usbcore: registered new interface driver ndiswrapper
mike@mike-desktop:~$ dmesg | grep -e ndis -e wlan
[   14.508061] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   15.628443] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[   15.628878] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh5'
[   15.629642] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[   15.629766] usbcore: registered new interface driver ndiswrapper
mike@mike-desktop:~$
[/LIST]
As you can see I have installed the 32 bit drivers in ndiswrapper that the NetGear CD installed on the XP side. 
But the wireless  USB stick is not being seen.
What do the errors in step 5 mean?
What should be my next step?

Thanks

---

### Post by shortcircuit on 2010-09-03
Same results as mglynch. Anyone have any ideas?

```

sam@sam-linux:~/Downloads$ sudo ndiswrapper -i WNA3100\ Driver/WinXP2000/bcmwlhigh5.inf 
installing bcmwlhigh5 ...
sam@sam-linux:~/Downloads$ sudo ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwlhigh5 : driver installed
	device (0846:9020) present
sam@sam-linux:~/Downloads$ lsusb | grep -e NetGear
Bus 001 Device 007: ID 0846:9020 NetGear, Inc. 
sam@sam-linux:~/Downloads$ dmesg | grep -e ndis -e wlan
[ 4263.951756] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 4264.151147] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[ 4264.151219] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh5'
[ 4264.151398] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[ 4264.151417] usbcore: registered new interface driver ndiswrapper
sam@sam-linux:~/Downloads$ 

```

---

### Post by ssrikant71 on 2010-09-03
I am an utter novice with Linux or Ubuntu. Just finished installing Ubuntu 10.04 on my laptop. I am able to connect to my ISP (broadband) through wireless router. It shows as connected on ubuntu interface. Inspite of this, most unfortunately, Firefox is unable to load web pages. I understand that this requires installing a driver called "iwlwifi" which is included in Linux kernel. How do I instal this driver? Please give me a list of simple steps if you can. Also read about ndiswrapper and I am all jumbled up with linux jargon. Pl help me resolve my issue. I shall be eternally grateful for your assistance.

---

### Post by victoryred on 2010-09-10
Hi All,
 The problem we have is that ndiswrapper is reporting an unknown symbol- IoUnregisterPlugplayNotification. So ndiswrapper needs to be updated to handle this issue when the driver bcmwlhigh5 is being loaded. I also tried bcmwlhigh6 and the number of unknown symbols grew substantially. Anyway, the problem is in ndiswrapper and not anything you did. I have no idea when it might get fixed. I took a look over at sourceforge and I'm not hopeful.

---

### Post by victoryred on 2010-09-11
I did some followup on this. From the inf file that you find in a Windows system in C:\Program Files(x86)\Netgear you will see that the adapter uses a Broadcom BCM 43xx device. On their website they mention that they support Linux drivers. I wonder if a driver for this device isn't available for a different but similar adapter. I'm willing to try it if we can find it. Otherwise we're back to square one with what to do about the bad symbol that NDISWRAPPER can't handle.

---

### Post by victoryred on 2010-09-12
Hey all,
 I went through a big effort but successfully installed the WNA3100 wireless USB adapter in Linux. I'm using it right now to port to this thread. Each of you have the information in this thread to check the installation but you missed the fundamental problem. IoUnregisterPlugPlayNotification. Here's what is required.

1.) From the install disk, a copy of bcmwlhigh5- both the inf and sys file.
2.) go to Sourceforge and download ndiswrapper version 1.56
3.) the wrapper for IoUnregisterPlugPlayNotification needs to be added to ntoskernal_io.c at the bottom of the file-

wstdcall NTSTATUS WIN_FUNC(IoUnregisterPlugPlayNotification,1)
	(void *tag) /* Don't ever use this pointer */
{
	TRACE2("%p", tag);
	TODO(); /* Probably Not, legacy function abandoned in Windows 7 */
	IOEXIT(return STATUS_SUCCESS); /* Linux doesn't use it either */
}

follow the make instructions and then follow the instructions in this thread. There is more work to do on this function but it's a start. If someone else knows of a better way share it.

Hope I helped....a little

---

### Post by jric on 2010-09-16
This is a promising thread.  Only issue is that:

1.  My OS is 64 bit Vista, and thus the driver is bcmwlhigh6 instead of 5, and according to this thread, that has a bunch of undefined symbols in it.  Also, I'm guessing that it's not likely to work with my 32-bit Ubuntu.
2.  There was mention of the bcmwlhigh5 driver "in the wild", but after an hour of searching, I've given up.  Would someone be so kind as to post the files here?

I have posted my bcmwlhigh6 files, which came from a Vista 64 install, in case they are useful to anybody.

---

### Post by victoryred on 2010-09-17
Hi Jric,
 If you are running a 32 bit version of Ubuntu then yes you will need the bcmwlhigh5.ini and sys files. As I recall both the high 5 and high6 versions get loaded into the Netgear directory under drivers setup.exe executes. You should have the files on the cdrom that came with the adapter. I don't know if you can legally just put the files out without permission from Broadcom but I have seen it out on the web.
 
Another note for others using the WNDA3100 which is the dual band N adapter. It doesn't use the Broadcom chipset so trying to use the BCMWL files won't work for you. I mention it because I found someone in another thread mention using the bcmwl files after  I posted information here. BCMWL means BroadCom WireLess so be careful.
 
Finally (IMHO) I believe that what makes the USB wireless adapters more prone to problems is the plug and play aspect of the drivers that Windows supports that so far it looks like Linux doesn't. The funtions calls that I see problems with when I use ndiswrapper -l are all plug and play related. When you look at the ndiswrapper source code it is peppered with todo() function calls. That's part of the reason I posted what I did.
 
I like Linux, I think it's cool. But I don't mind spending $100 to buy something that is well supported directly by the suppliers so that I don't go into a reversionary programming mode that I left 20 years ago. However, it's good to know I can still make some sense of the source code.

---

### Post by jric on 2010-09-22
Thanks Victory.  I did not find the bcmwl5 files in the same directory.  Even if I could find my install CD, I would probably have no luck, since I've read somewhere that the only way to get the files is to do the actual install, and of course, I am back to the 64 bit problem.

I hate to admit defeat, but I give up on this one.  Better luck to the next happy Linux traveler with an extra $100 to spend, or better internet searching skills.

I'll bypass this problem after I move into my new place which I wired with cat5.

---

### Post by victoryred on 2010-09-22
Jric,
   My fault actually. I found that the bcmwlhigh5 files got installed on my Windows XP laptop in my quest for the 32 bit files. You are absolutely right i your observation. Here's what I suggest. Don't give up....just take a break and come back and revisit a little later. I think you will have a fresh start, Broadcom or someone might fully solve the problem (maybe even me). You have to remember that this stuff really isn't simple after all. Part of the thrill is solving a problem that hasn't been solved before. Finally, there is tons of information sitting in your log files waiting for you to discover it, make sense of it then add it to the puzzle, one piece at a time. You will have a very proud moment when you see the light and do something you didn't think you could do. Don't ever give up......ever! Be a Bulldog.
 
Best,
VictoryRed

---

### Post by FluidBlow on 2010-09-24
> **victoryred said:**
> Hey all,
 I went through a big effort but successfully installed the WNA3100 wireless USB adapter in Linux. I'm using it right now to port to this thread.

Hello, you said you succeed in using WNA3100 usb adaptater on Linux didn't you ? 
Well, can you tell us what distrib and version of linux are you using, what drivers and what version did you use ? (32 or 64 bits)

I tried both bcmwlhigh6 and bcmwlhigh5 (64 bits) drivers with ndiswrapper, with the 5: 64 bits, when I connect the usb adaptater, ndiswrapper functionnalities are frozen for example, when I type "lsusb" nothing happens (and the shell don't let me type another command).
With the 6, (always 64 bits),  the driver is installed well and the hardware is detected, but they are plenty of ndiswrapper errors so the driver isn't loaded and nothing happens.

Thank's for help.

---

### Post by victoryred on 2010-10-04
As I mentioned in a previous reply. bcmwlhigh6 yielded many errors while trying to load with ndiswrapper. bcmwlhigh5 yielded 1 error and I supplied a copy of a handler routine that I added to the ndiswrapper source code that I then recompiled and ran. The problem that I see with using Windows drivers running on Linux with wrapper functionality is that the plug & play capability that exists in windows isn't handled well in ndiswrapper. If you get a copy of the source code you will see what I'm talking about. The snippet of code I provided is a copy of a piece of such code. A simple patch to get things operating. The real problem is cleaning up all the other functions (traps) that really need to handle and pass valid arguments back and forth to the Windows driver you are attempting to use. All this can be done, please feel free to press on.

---

### Post by flash63 on 2010-10-05
Hello,
optimized Driver 32/64bit for Netgear WNDA-3100 v3 ID 0846:9020 here

[http://forum.ubuntuusers.de/topic/belkin-play-wireless-adapter-f7d4101-nicht-er/#post-2612284](http://forum.ubuntuusers.de/topic/belkin-play-wireless-adapter-f7d4101-nicht-er/#post-2612284)

Supported ID's:
050D:825C (Belkin)
050D:6050 (Belkin)
050D:615A (Belkin)
0846:9020 (Netgear)

---

### Post by koffkoffus on 2010-10-05
Can anyone recommend a USB wireless adapter that works "out of the box" with Linux/Ubuntu?

Thanks - much appreciated.

---

### Post by victoryred on 2010-10-05
wnda3100 is a dual band device. Not the same as wna3100.

---

### Post by victoryred on 2010-10-05
**<H1>[SIZE=4]Try this as a lead.....[/SIZE]**

**[SIZE=4]BCM4323 - Intensi-fi® XLR Single-Chip 802.11n USB Solution[/SIZE]**

</H1>

---

### Post by victoryred on 2010-10-08
Everyone,
    I have been in touch directly with Broadcom regarding the WNA3100. I gave them the information they requested and are willing to assist. They recently released other new Linux drivers. Let's see what happens. I will post whatever news I get, when I get it. Please check back.
 
-M

---

### Post by victoryred on 2010-10-12
Update 10/11/10. 
 
Very much appreciate Broadcom's support. They have been very helpful. I think this will get solved for everyone. Stay hopeful.
 
If a moderator is monitoring this thread, I have a question. If a fix is found how is configuration managed and implementation released?
 
VR

---

### Post by soderstrom on 2010-10-14
> **flash63 said:**
> Hello,
optimized Driver 32/64bit for Netgear WNDA-3100 v3 ID 0846:9020 here

[http://forum.ubuntuusers.de/topic/belkin-play-wireless-adapter-f7d4101-nicht-er/#post-2612284](http://forum.ubuntuusers.de/topic/belkin-play-wireless-adapter-f7d4101-nicht-er/#post-2612284)

Supported ID's:
050D:825C (Belkin)
050D:6050 (Belkin)
050D:615A (Belkin)
0846:9020 (Netgear)

> **victoryred said:**
> wnda3100 is a dual band device. Not the same as wna3100.

I didn't read your note and installed the driver he recommended. It actually got activated and could see the access points, but when trying to connect it failed after a while. Maybe there is a way to find out?

---

### Post by victoryred on 2010-10-14
soderstrom
 
That's actually interesting. On p[oint that needs to be made is that the bcmwlhigh5 driver is used with a 32bit OS and the bcmwlhigh6 is used with a 64 bit OS. What I find interesting is that the ID is the same for BOTH NetGear devices (WNA3100 & WNDA3100). I stand by my statement that the "D is for a dual band device. Since I don't own a WNDA3100 I expected the ID to be different. But it may be immaterial.
 
As I mentioned Broadcom is working this issue and I believe they may also be in contact with the NdisWrapper contributors to solve the single symbol error I describe in an earlier post. I am very willing to offer my support to either of them because I do enjoy solving problems.
 
Finally, as I mentioned in an earlier post I did get the Ndiswrapper source, copy a code block to make the stub and compiled as I described. Alas, I did find that wlan would disconnect. It took more energy than I had at the time so I started looking for another solution just like many of the rest of you. This is just my opinion, but I have a hunch that an NdisWrapper maintainer will fix this for both 32 bit & 64 bit Linux OSes but I'm not a fan of wrapping handler functions around drivers written for another OS. Drivers should ne native.
 
One other piece of the puzzle- There have been several very good guides written and distributed on this forum regarding troubleshooting ndiswrapper etc. Everyone has made a good contribution to the community. In my efforts I tired I think at least three of the guides. The part that sent my WNA3100 down hard is that there are at least a couple of Networking Configuration programs available to the Linux user. ndisgtk is one and I'm looking throuhg my notes for the other. What I think I ran into again is side effects of using one versus the other. When I used ndisgtk I ran into the case where the wlan would run a wile and disconnect. The other program (I will post the program name when I find it) listed detailed information about the WNA3100 device but after I exited the program without making any changes, I was unable to get the WNA3100 started at all after that. My suggestion is to be conservative and careful. This whole proccess is personally time consuming for you to perform and if it breaks you'll be frustrated.
 
I hope I'm helping.
 
VR

---

### Post by victoryred on 2010-10-14
soderstrom,
   The 32 bit bcmwlhigh5 and 64 bit bcmwlhigh6 distinction is IMPORTANT. I assumed someone would catch on. In an earlier post I mentioned that bcmwlhigh6 had more symbol errors while loading with NdisWrapper than bcmwlhigh5. I believe this is because of the 32 vs. 64 bit OS difference. Maybe someone with a 64 bit Linux OS can shed some light on this.
 
VR

---

### Post by victoryred on 2010-10-14
Last post for this evening. There is source code for the Broadcom B43xx chipset available. Unfortunately, they are for a PCI based device. In the source they include a precompiled object file that is the interface to the chipset. The open source is mostly for the PCI interface. My hope is that they release the source for a USB version or at least give the community a loadable native USB wlan driver. I'm willing to give them the benefit of the doubt.
 
However, USB wlan networking appears to be a "class of" type problem across many devices looking for Linux drivers. You see it on other boards. Can anyone tell me where I can find Linux system architecture documentation?
 
VR

---

### Post by victoryred on 2010-10-15
Oct 15, 2010

Ok, finally. I have just retraced my steps posted earlier on this thread. Yes Ndiswrapper with bcmwlhigh5 is working right now on a 32 bit Linux system. Yes, I am using Linux and my wna3100 to post this. Here are the quick steps.

1.) Get the ndiswrapper source from sourceforge latest is version 1.56
2.) add the code I posted earlier
then
       sudo make uninstall
      make
      make install

then
ndiswrapper -v         it should report version 1.56 not 1.55
then
 cd over to the directory that has both the bcmwlhigh5.inf and bcmwlhigh5.sys files in it.
finally
ndiswrapper -i bcmwlhigh5.inf

At this point use the wireless network manager to create the wireless network and don't forget WEP if your wlan uses it.

Not simple but it does work.
VR

---

### Post by victoryred on 2010-10-15
michael@michael-desktop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-24-generic-pae/misc/ndiswrapper.ko
version:        1.56
vermagic:       2.6.32-24-generic-pae SMP mod_unload modversions 586TSC 

michael@michael-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwlhigh5 : driver installed
    device (0846:9020) present


michael@michael-desktop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto ] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

---

### Post by victoryred on 2010-10-16
I just submitted the code stub and supporting information to the Ndiswrapper maintainers. They can implement the releaseable fix. 

Best Wishes,
VR

---

### Post by victoryred on 2010-10-16
Oct 16, 2010

Well everything is running fine, but I have an update .........about updates.

After successfully getting my wba3100 adapter up and running, this afternoon I decided to go into update manager and get everything.......well up to date. The update manager dutifully did this. I'm loving having a connection to the 'net again.

Well, the update manager also updated the OS to 2.6.32.25 from 2.6.32.23. As you can imagine the 2.6.32.25 kernal didn't have the "special" version of ndiswrapper. At the reboot it was just like I hadn't fixed th problem.

Fortunately, I caught it and did the following:

sudo make uninstall
sudo make install

then rebooted.........everything is fine again. Word to the wise. Once you get your WNA3100 running until the ndiswrapper fix gets into distribution when the kernel gets updated perform the two steps above to keep your system on the net.

Best,
VR

---

### Post by flash63 on 2010-10-20
> **soderstrom said:**
> I didn't read your note and installed the driver he recommended. It actually got activated and could see the access points, but when trying to connect it failed after a while. Maybe there is a way to find out?
Hi,
please show the output of
```
sudo iwlist scan
```
mark your own network.

Take a look at the security configuration at your Router. Change it to pure WPA2-AES (CCMP) and try again.

---

### Post by victoryred on 2010-10-23
We are making progress with the Ndiswrapper maintainance side. 
Still trying hard to help everyone.
 
Best,
VR
 
For those trying to add the patch mentioned earlier remember to:
 
sudo make uninstall
sudo make install
 
this will make sure your patch gets executed by the kernal at boot time. It will work per everything discussed on this thread after that. Many have put a good effort into trouleshooting this. Thank you all.

---

### Post by soderstrom on 2010-10-24
> **flash63 said:**
> Hi,
please show the output of
```
sudo iwlist scan
```mark your own network.

Take a look at the security configuration at your Router. Change it to pure WPA2-AES (CCMP) and try again.

Hey

I have done the following now to get an active stable connection that also shows an acceptable strength at 70%.

Installed ndiswrapper with ndisgtk from ubuntu software center

Downloaded the modified Broadcom 43xx 32-bit driver as posted earlier

Installed with ndisgtk

Changed my WIFI security from WPA2 Personal (TKIP) to WPA2 Personal (PSK) + AES

Rebooted the computer

Connected

Works :)

Thanks for sharing your advice about to change the WPA2 security. Maybe that was the problem? But I have a feeling it was the ndiswrapper ndisgtk that did the trick. Everything installed automatically from the gui and no need to tinker with any settings. I'm using the latest ndsiwrapper with Ubuntu 10.10 btw.

Hope it works for everyone else.

Edit: after using it for a few hours I notice the connection is very slow. I tried disable ipv6 but no change. Is there a way to check the connection for errors?

---

### Post by flash63 on 2010-10-24
> Thanks for sharing your advice about to change the WPA2 security. Maybe that was the problem?
This is a problem of the Network-Manager
> But I have a feeling it was the ndiswrapper ndisgtk that did the trick.
Not really. Manual commands bring about the same as ndisgtk
```
sudo ndisrapper -i <driver.inf-file>
sudo ndiswrapper -ma
```
> after using it for a few hours I notice the connection is very slow.

More Output please
```
iwconfig
ifconfig
sudo iwlist scan
```

---

### Post by ueghio on 2010-11-05
Hi guys,any news about this device on a 64bit architecture?
Thanks in advance,regards.
Marco

---

### Post by AMMOnium on 2010-11-06
Hi all,

I'm currently experiencing an issue with the Netgear WNA3100 adapter on a Lucid box (based on ASROCK 330 ION board). 

The system was set up from:
[LIST]
[*]a minimal 10.04 server distro,
[*]ndiswrapper built from source with patched IoUnregisterPlugPlayNotification procedure stub 
[*]original win32 dirvers extracted from the CD bundled with adapter (also tried the drivers posted here with precisely the same result).
[/LIST]

I was able to make the adapter scan for access points and receive valid results, but I could not even associate it using [FONT="Courier New"]iwconfig[/FONT] to my wireless AP (rather old but still stable D-Link 2640U, WPA2 PSK, AES, hidden SSID).
The AP itself receives no assoc request from the card, so the association issue is on the client's side, not the AP's.

Here go some logs & stats:

```

**root@htpc:~# cat /etc/issue**
Ubuntu 10.04.1 LTS \n \l
**root@htpc:~# uname -a**
Linux htpc 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux
**root@htpc:~# lsusb**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9020 NetGear, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**root@htpc:~# dmesg | grep -i ndis**
[    5.014510] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[    6.212132] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[    6.479503] wlan0: ethernet device XX:XX:XX:XX:XX:XX using NDIS driver: bcmn43xx32, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[    6.482605] usbcore: registered new interface driver ndiswrapper
**root@htpc:~# ifconfig wlan0**
wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**root@htpc:~# iwconfig wlan0**
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:300 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**root@htpc:~# ndiswrapper -v**
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-25-generic/misc/ndiswrapper.ko
version:        1.56
vermagic:       2.6.32-25-generic SMP mod_unload modversions 586
**root@htpc:~# ndiswrapper -l**
bcmn43xx32 : driver installed
        device (0846:9020) present

```

---

### Post by ueghio on 2010-11-07
It works flawlessly on my Debian Squeeze 32bit system using the patched driver bcmwlhigh5.inf..
debian:/home/marco# ndiswrapper -l
bcmwlhigh5 : driver installed
        device (0846:9020) present
Probably it's a bcmn43xx32 driver's issue.

---

### Post by AMMOnium on 2010-11-07
**ueghio**, have you tried it with WPA2-PSK & hidden SSID? Could you please explain what do you mean by "patched driver bcmwlhigh5.inf"? Have you just patched the ndiswrapper source as recommended by **victoryred** earilier in this thread, or you have changed something in the *.inf file or even modified the *.sys driver binary?
Please also post your *.sys driver version ( dmesg | grep "ndiswrapper: driver" )

And now some more detailed info on the hardware.
Netgear WNA3100 uses Broadcom BCM94323 chip (aka BCM 4323), which is a USB-enabled version of BCM94322 (aka BCM 4322). 

As usual, no detailed datasheets were seen in public, only some brief press releases like [_this_]("http://www.netcheif.com/Reviews/DSL-2760U/4322_4323-PB01-R.pdf").

Here are some pics of the device's PCB, two U.FL sockets for external MIMO antennas present:
[[IMG]http://img149.imageshack.us/img149/7730/image001gq.th.jpg[/IMG]](http://img149.imageshack.us/i/image001gq.jpg/)

[[IMG]http://img825.imageshack.us/img825/1525/image002iy.th.jpg[/IMG]](http://img825.imageshack.us/i/image002iy.jpg/)

---

### Post by ueghio on 2010-11-07
Hi that's the output ```
marco@debian:~$ dmesg | grep "ndiswrapper: driver"
[    5.877145] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
```
and here [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100) you can find the howto.
Hope this helps

---

### Post by AMMOnium on 2010-11-07
Thanks for the info, this is the same driver I have used during the first attempt and it seems to be the latest. 

I am contacting Broadcom and will post any progress here.

---

### Post by petrus250 on 2010-11-13
Hi, here is the bcmwlhigh5 driver, not a lot of good but if you want it... :)

---

### Post by saltynut on 2010-11-14
After a bunch of everything I got the wna3100 usb adapter recognized and picking up networks and i can access unprotected networks but not my own proteced one it asks for password but wont connect any idea whats goin on there?

---

### Post by victoryred on 2010-11-15
Well I haven't checked in for a while but I pleased to see everyone making progress. If you check one of my earlier posts you will see that I too found the first installation slow. However, I did exactly what I said I did and uninstalled the ndiswrapper stuff and did a fresh install and it's worked fine ever since.
   It looks like the ndiswrapper maintainers rolled the version number to v 1.9 so I hope that the code I stubbed out got put into the newer ndiswrapper source. If so your lives will be easier. simply get the right version of the bcmwlhigh driver and follow the installation guidelines for wlans in the help part of the forum. At the end of the day you'll look back and realize how easy it was. It's just a learning curve.....

---

### Post by victoryred on 2010-11-15
Just a note: I loaded an old Windows XP machine with the Broadcom driver CDROM as if I was going to use it on that machine. Then I copied the bcmwlhigh5.inf and bcmwlhigh5.sys files onto a USB flash drive. Then I put the usb flash drive on the Linux machine and moved the files over from there. If you are using a 64 bit version of Linux then you are on new ground. I think you will need the bcmwlhigh6 files. I don't know because I haven't tried it.

---

### Post by victoryred on 2010-11-15
The fix I performed is on sourceforge. The link is on an earlier post.

---

### Post by lucky07 on 2010-11-26
> **saltynut said:**
> After a bunch of everything I got the wna3100 usb adapter recognized and picking up networks and i can access unprotected networks but not my own proteced one it asks for password but wont connect any idea whats goin on there?

i'm in the same boat ... any fix for it yet?

---

### Post by victoryred on 2010-11-27
Hi Lucky07,
    The problem sounds to me like the fix didn't get properly installed into the right directories and the OS didn't get updated.

   To recap-

Make sure that the bcmwlhigh5.inf and bcmwlhigh5.sys files are located in the following place. You may need to create the bcmwlhigh5 directory and physically move the files but as I recall it was done by the makefile as long as all the files for the build process are where they need to be. If not just move them. Since others have already done so, I am including the file from that directory for educational purposes only. Please see the attachments. I hope I've helped.

michael@michael-desktop:/etc/ndiswrapper/bcmwlhigh5$ ls *
0846:9020.F.conf  bcmwlhigh5.inf  bcmwlhigh5.sys

If not move them there. Notice the config file is there too. ndiswrapper requires the 0846:9020.F.conf file as well. It is part of the build process.

This should clear up any remaining mysteries. I think you will be successful.

Victoryred

---

### Post by victoryred on 2010-11-28
Hi Lucky07,
      More info......check the following as well.

michael@michael-desktop:/sys/module/ndiswrapper$ ls
drivers  initstate  parameters  sections    version
holders  notes      refcnt      srcversion

Make sure this area was updated during the makefile build. Version should be 1.56. You will know that the fix went in when you run ndiswrapper. There should be no symbol error messages.

Remember to read the ndiswrapper makefile and notes. Follow them- they work.

BTW, I updated my security to WPA2 using 63 characters. I had to reboot for it to work right but once I was done. No problemo.

So, I want to say to the Linux community and the folks at Ubuntu........I like it very much. 

Now I have to get my old IMSAI 8080 out of the box.

Victoryred

---

### Post by sdaremnant on 2010-12-17
cant get my netgear n600 wnda3100 usb wireless adapter to work, please help

---

### Post by Windsor62 on 2010-12-30
Hi, purchased Netgear WNA3100 Wireless USB Adapter for the purpose of using it with W7 on my desktop pc. I have now installed Ubuntu 10.10 on this machine and this adapter will not work but my old BT Voyager adapter will. I'm using a BT Homehub 2 wireless router. I'm new to Linux and have been searching the internet for some time now to find a solution. Thanks :guitar:

---

### Post by dbvolante on 2011-01-03
I'm stuck as well with WPA2 on 10.10, I got the drivers easily recognized by ndiswrapper 1.56-3 and all the files are in the correct positions, I can see all the access points around me but once I put in the password for my own access point, which has a WPA2 protection, nothing happens, it keeps trying and trying and then asks me again for the password (which is, of course, already the right one).
Any help?
Because I can't use Ubuntu without the wna3100 working. :(

---

### Post by jrinehart76 on 2011-01-05
I didn't modify the 'ntoskernel_io.c' and am using the 64bit BCM drivers found in this thread. I can connect to the G side of my router but not the N side. 

I'm using a Netgear WNDA3100v1 Atheros 9001U 9010 adapter. Strangely enough, I couldn't get the Win7 x64 drivers to work through ndiswrapper so I gave the BCM drivers a shot just for fun. They worked half way. With the OOB ar9170usb drivers, it was behaving the same way.

Ubuntu 10.10 2.6.35-24-generic x86_64, ndiswrapper 1.56

Here is the output of the syslog if anyone might have any ideas:

Jan  5 13:35:49 Office NetworkManager[987]: <info> Activation (wlan0) starting connection 'Auto Home_N'
Jan  5 13:35:49 Office NetworkManager[987]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jan  5 13:35:49 Office NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  5 13:35:49 Office NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  5 13:35:49 Office NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  5 13:35:49 Office NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  5 13:35:49 Office NetworkManager[987]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Jan  5 13:35:49 Office NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  5 13:35:49 Office NetworkManager[987]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jan  5 13:35:49 Office NetworkManager[987]: <info> Activation (wlan0/wireless): access point 'Auto Home_N' has security, but secrets are required.
Jan  5 13:35:49 Office NetworkManager[987]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jan  5 13:35:49 Office NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  5 13:35:49 Office kernel: [   38.262233] cfg80211: All devices are disconnected, going to restore regulatory settings
Jan  5 13:35:49 Office kernel: [   38.262240] cfg80211: Restoring regulatory settings
Jan  5 13:35:49 Office kernel: [   38.262244] cfg80211: Calling CRDA to update world regulatory domain
Jan  5 13:35:50 Office NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  5 13:35:50 Office NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  5 13:35:50 Office NetworkManager[987]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jan  5 13:35:50 Office NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  5 13:35:50 Office NetworkManager[987]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  5 13:35:50 Office NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  5 13:35:50 Office NetworkManager[987]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jan  5 13:35:50 Office NetworkManager[987]: <info> Activation (wlan0/wireless): connection 'Auto Home_N' has security, and secrets exist.  No new secrets needed.
Jan  5 13:35:50 Office NetworkManager[987]: <info> Config: added 'ssid' value 'Home_N'
Jan  5 13:35:50 Office NetworkManager[987]: <info> Config: added 'scan_ssid' value '1'
Jan  5 13:35:50 Office NetworkManager[987]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  5 13:35:50 Office NetworkManager[987]: <info> Config: added 'psk' value '<omitted>'
Jan  5 13:35:50 Office NetworkManager[987]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  5 13:35:50 Office NetworkManager[987]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  5 13:35:50 Office NetworkManager[987]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  5 13:35:50 Office kernel: [   38.275798] cfg80211: World regulatory domain updated:
Jan  5 13:35:50 Office kernel: [   38.275802]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  5 13:35:50 Office kernel: [   38.275806]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  5 13:35:50 Office kernel: [   38.275809]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  5 13:35:50 Office kernel: [   38.275811]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  5 13:35:50 Office kernel: [   38.275814]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  5 13:35:50 Office kernel: [   38.275817]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  5 13:35:50 Office NetworkManager[987]: <info> Config: set interface ap_scan to 1
Jan  5 13:35:50 Office NetworkManager[987]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan  5 13:35:54 Office wpa_supplicant[1015]: Trying to associate with 00:24:b2:12:bd:a6 (SSID='Home_N' freq=5180 MHz)
Jan  5 13:35:54 Office NetworkManager[987]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan  5 13:35:54 Office kernel: [   42.510120] wlan0: authenticate with 00:24:b2:12:bd:a6 (try 1)
Jan  5 13:35:54 Office kernel: [   42.511166] wlan0: authenticated
Jan  5 13:35:54 Office kernel: [   42.511189] wlan0: associate with 00:24:b2:12:bd:a6 (try 1)
Jan  5 13:35:54 Office kernel: [   42.512593] wlan0: RX AssocResp from 00:24:b2:12:bd:a6 (capab=0x11 status=0 aid=2)
Jan  5 13:35:54 Office kernel: [   42.512597] wlan0: associated
Jan  5 13:35:54 Office wpa_supplicant[1015]: Associated with 00:24:b2:12:bd:a6
Jan  5 13:35:54 Office NetworkManager[987]: <info> (wlan0): supplicant connection state:  associating -> associated
Jan  5 13:35:54 Office NetworkManager[987]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Jan  5 13:35:54 Office wpa_supplicant[1015]: WPA: Key negotiation completed with 00:24:b2:12:bd:a6 [PTK=CCMP GTK=CCMP]
Jan  5 13:35:54 Office wpa_supplicant[1015]: CTRL-EVENT-CONNECTED - Connection to 00:24:b2:12:bd:a6 completed (reauth) [id=0 id_str=]
Jan  5 13:35:54 Office NetworkManager[987]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jan  5 13:35:54 Office NetworkManager[987]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Jan  5 13:35:54 Office NetworkManager[987]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Home_N'.
Jan  5 13:35:54 Office NetworkManager[987]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  5 13:35:54 Office NetworkManager[987]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan  5 13:35:54 Office NetworkManager[987]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Jan  5 13:35:54 Office NetworkManager[987]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  5 13:35:54 Office NetworkManager[987]: <info> dhclient started with pid 1783
Jan  5 13:35:54 Office NetworkManager[987]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan  5 13:35:54 Office dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  5 13:35:54 Office dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jan  5 13:35:54 Office dhclient: All rights reserved.
Jan  5 13:35:54 Office dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  5 13:35:54 Office dhclient: 
Jan  5 13:35:54 Office NetworkManager[987]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan  5 13:35:54 Office dhclient: Listening on LPF/wlan0/00:22:3f:06:8d:92
Jan  5 13:35:54 Office dhclient: Sending on   LPF/wlan0/00:22:3f:06:8d:92
Jan  5 13:35:54 Office dhclient: Sending on   Socket/fallback
Jan  5 13:35:54 Office dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan  5 13:35:55 Office kernel: [   43.451281] wlan0: no IPv6 routers present
Jan  5 13:35:57 Office dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan  5 13:36:00 Office dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan  5 13:36:03 Office dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jan  5 13:36:10 Office dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jan  5 13:36:19 Office dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Jan  5 13:36:35 Office dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Jan  5 13:36:40 Office NetworkManager[987]: <warn> (wlan0): DHCPv4 request timed out.
Jan  5 13:36:40 Office NetworkManager[987]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1783
Jan  5 13:36:40 Office NetworkManager[987]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan  5 13:36:40 Office NetworkManager[987]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan  5 13:36:40 Office NetworkManager[987]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
Jan  5 13:36:40 Office NetworkManager[987]: <warn> Activation (wlan0) failed for access point (Home_N)
Jan  5 13:36:40 Office NetworkManager[987]: <info> Marking connection 'Auto Home_N' invalid.
Jan  5 13:36:40 Office NetworkManager[987]: <warn> Activation (wlan0) failed.
Jan  5 13:36:40 Office NetworkManager[987]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan  5 13:36:40 Office NetworkManager[987]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jan  5 13:36:40 Office NetworkManager[987]: <info> (wlan0): deactivating device (reason: 0).
Jan  5 13:36:40 Office kernel: [   88.571349] wlan0: deauthenticating from 00:24:b2:12:bd:a6 by local choice (reason=3)
Jan  5 13:36:40 Office wpa_supplicant[1015]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  5 13:36:40 Office kernel: [   88.602068] cfg80211: All devices are disconnected, going to restore regulatory settings
Jan  5 13:36:40 Office kernel: [   88.602077] cfg80211: Restoring regulatory settings
Jan  5 13:36:40 Office kernel: [   88.602083] cfg80211: Calling CRDA to update world regulatory domain
Jan  5 13:36:40 Office kernel: [   88.607994] cfg80211: World regulatory domain updated:
Jan  5 13:36:40 Office kernel: [   88.607999]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  5 13:36:40 Office kernel: [   88.608005]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  5 13:36:40 Office kernel: [   88.608010]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  5 13:36:40 Office kernel: [   88.608015]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  5 13:36:40 Office kernel: [   88.608020]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  5 13:36:40 Office kernel: [   88.608025]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  5 13:36:43 Office NetworkManager[987]: <info> Activation (wlan0) starting connection 'Auto Home_G'

---

### Post by Cutlesnap on 2011-01-09
I had the same problems: 
Card didn't work at first, so I installed ndiswrapper. It still doesn't work with WPA2 (AES), so I changed the router encryption to WPA (TKIP). This does work, although I haven't checked at which speed it works (In Windows, it only works at 54 Mb/s).

For now this is fine, but when someone thinks of something better, I'd be interested.

---

### Post by iceboy99 on 2011-01-10
I got my WNA3100 working, thanks largely to this thread. It was working fine for about a month, until my wife apparently upgraded. Now, the adapter times out after a certain time (somewhere around an hour maybe?). I have to reboot, in order to get the adapter to respond.

Here's the output from dmesg:

[19830.476698] ndiswrapper (mp_set_power_state:375): wlan1 does not support power management; halting the device
[19831.063297] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[19831.063301] ndiswrapper (mp_set_power_state:344): wlan1: couldn't set power to state 1; device not resumed
[19831.063305] ndiswrapper (NdisDispatchPower:1362): couldn't set power to 1: C0000001
[19831.322060] ndiswrapper (ndis_remove_device:1963): couldn't obtain tx_ring_mutex
[19831.322072] ndiswrapper (mp_halt:262): device ea1723a0 is not initialized - not halting
[19831.322077] ndiswrapper: device wlan1 removed
[19831.984329] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[19832.677317] wlan1: ethernet device 30:46:9a:3a:77:75 using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[19832.682213] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

The kernel is now at 2.6.32-27. I've recompiled ndiswrapper.

Any help would be greatly appreciated.

---

### Post by iceboy99 on 2011-01-14
> **iceboy99 said:**
> I got my WNA3100 working, thanks largely to this thread. It was working fine for about a month, until my wife apparently upgraded. Now, the adapter times out after a certain time (somewhere around an hour maybe?). I have to reboot, in order to get the adapter to respond.

Here's the output from dmesg:

[19830.476698] ndiswrapper (mp_set_power_state:375): wlan1 does not support power management; halting the device
[19831.063297] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[19831.063301] ndiswrapper (mp_set_power_state:344): wlan1: couldn't set power to state 1; device not resumed
[19831.063305] ndiswrapper (NdisDispatchPower:1362): couldn't set power to 1: C0000001
[19831.322060] ndiswrapper (ndis_remove_device:1963): couldn't obtain tx_ring_mutex
[19831.322072] ndiswrapper (mp_halt:262): device ea1723a0 is not initialized - not halting
[19831.322077] ndiswrapper: device wlan1 removed
[19831.984329] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[19832.677317] wlan1: ethernet device 30:46:9a:3a:77:75 using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[19832.682213] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

The kernel is now at 2.6.32-27. I've recompiled ndiswrapper.

Any help would be greatly appreciated.

I've tried a number of things, with no success. I've tried to change power-related setting in the config file in /etc/ndiswrapper/[driver name]/. Nothing sees to have an effect. Has no one else see this problem?

---

### Post by iceboy99 on 2011-01-14
> **iceboy99 said:**
> I got my WNA3100 working, thanks largely to this thread. It was working fine for about a month, until my wife apparently upgraded. Now, the adapter times out after a certain time (somewhere around an hour maybe?). I have to reboot, in order to get the adapter to respond.

Here's the output from dmesg:

[19830.476698] ndiswrapper (mp_set_power_state:375): wlan1 does not support power management; halting the device
[19831.063297] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[19831.063301] ndiswrapper (mp_set_power_state:344): wlan1: couldn't set power to state 1; device not resumed
[19831.063305] ndiswrapper (NdisDispatchPower:1362): couldn't set power to 1: C0000001
[19831.322060] ndiswrapper (ndis_remove_device:1963): couldn't obtain tx_ring_mutex
[19831.322072] ndiswrapper (mp_halt:262): device ea1723a0 is not initialized - not halting
[19831.322077] ndiswrapper: device wlan1 removed
[19831.984329] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[19832.677317] wlan1: ethernet device 30:46:9a:3a:77:75 using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[19832.682213] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

The kernel is now at 2.6.32-27. I've recompiled ndiswrapper.

Any help would be greatly appreciated.

I've tried a number of things, with no success. I've tried to change power-related setting in the config file in /etc/ndiswrapper/[driver name]/. Nothing sees to have an effect. Has no one else see this problem?

---

### Post by solitario on 2011-01-22
Is there any way someone who understands what has been said in this thread to write up a step by step tutorial? That would be great.

---

### Post by manolos on 2011-01-26
**Hi all! I would like to ask why i cant install ndiswrapper 1.56? What are the needed packages? i am on ubuntu 10.10 32bit.**

```
ubuntu@ubuntu:~/Desktop$ cd ndiswrapper-1.56/
ubuntu@ubuntu:~/Desktop/ndiswrapper-1.56$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
removing /usr/sbin/ndiswrapper
removing /lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
ubuntu@ubuntu:~/Desktop/ndiswrapper-1.56$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
ubuntu@ubuntu:~/Desktop/ndiswrapper-1.56$ make
make -C driver
make[1]: Entering directory `/home/ubuntu/Desktop/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.35-22-generic M=/home/ubuntu/Desktop/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  LD      /home/ubuntu/Desktop/ndiswrapper-1.56/driver/built-in.o
  MKEXPORT /home/ubuntu/Desktop/ndiswrapper-1.56/driver/crt_exports.h
  MKEXPORT /home/ubuntu/Desktop/ndiswrapper-1.56/driver/hal_exports.h
  MKEXPORT /home/ubuntu/Desktop/ndiswrapper-1.56/driver/ndis_exports.h
  MKEXPORT /home/ubuntu/Desktop/ndiswrapper-1.56/driver/ntoskernel_exports.h
  MKEXPORT /home/ubuntu/Desktop/ndiswrapper-1.56/driver/ntoskernel_io_exports.h
  MKEXPORT /home/ubuntu/Desktop/ndiswrapper-1.56/driver/rtl_exports.h
  MKEXPORT /home/ubuntu/Desktop/ndiswrapper-1.56/driver/usb_exports.h
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/crt.o
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/hal.o
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/iw_ndis.o
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/loader.o
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/ndis.o
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/ntoskernel.o
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/ntoskernel_io.o
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/pe_linker.o
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/pnp.o
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/proc.o
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/rtl.o
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapmem.o
  CC [M]  /home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapndis.o
/home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapndis.c: In function &#8216;set_multicast_list&#8217;:
/home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapndis.c:953: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_count&#8217;
/home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapndis.c:956: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_count&#8217;
/home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapndis.c:960: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_count&#8217;
/home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapndis.c:960: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_min2&#8217;
/home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapndis.c:960: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_count&#8217;
/home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapndis.c:967: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_list&#8217;
/home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapndis.c:968: error: dereferencing pointer to incomplete type
/home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapndis.c:969: error: dereferencing pointer to incomplete type
/home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapndis.c:971: error: dereferencing pointer to incomplete type
make[3]: *** [/home/ubuntu/Desktop/ndiswrapper-1.56/driver/wrapndis.o] Error 1
make[2]: *** [_module_/home/ubuntu/Desktop/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/ubuntu/Desktop/ndiswrapper-1.56/driver'
make: *** [all] Error 2
ubuntu@ubuntu:~/Desktop/ndiswrapper-1.56$ 
```[B]Im trying to install it for windows drivers for wna3100 v1 n300 0846:9020 atheros ar9170usb.
Ofc i know i could install from apt-get or deb the ndiswrapper but i need to add the lines that [/B][victoryred]("http://ubuntuforums.org/member.php?u=1146750")[B] told us to add in order to make usb adapter work.

[SIZE=4][COLOR=Red]edit:[/COLOR][/SIZE]
problem solved [http://sourceforge.net/projects/ndiswrapper/forums/forum/323168/topic/3965193](http://sourceforge.net/projects/ndiswrapper/forums/forum/323168/topic/3965193)

I got another problem though! When i make uninstall, ndiswrapper module is gone. After make & make install i dont see anywhere ndiswrapper.ko again so i cant modprobe it. Im so confused..

[/B]```
ubuntu@ubuntu:~/Desktop/ndiswrapper-1.56/utils$ ndiswrapper -v
ERROR: modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
ERROR: modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net
```

---

### Post by phh on 2011-02-02
Can someone please explain how to find and edit *ntoskernal_io.c*

I cant find it anywhere in my ndiswrapper folders.

Many thanks

---

### Post by phh on 2011-02-09
I have downloaded and installed Ndiswrapper from Sourceforge, but I cant seem to find ntoskernal_io.c anywhere on my system. Do you have any insight to this problem?

---

### Post by AMMOnium on 2011-02-11
> **phh said:**
> I have downloaded and installed Ndiswrapper from Sourceforge, but I cant seem to find ntoskernal_io.c anywhere on my system. Do you have any insight to this problem?

The file should be called "ntoskern**[COLOR="Red"]e[/COLOR]**l_io.c"! And "ntoskern**[COLOR="Red"]a[/COLOR]**l_io.c" is just a typo.

And you should of course patch the source **before** compiling and installing. So look where you have extracted the ndiswrapper source, patch the ntoskernel_io.c as recommended earlier in this thread and only after that make && make install.

```

# svn co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk

... SKIPPED SKIPPED SKIPPED ...

A    trunk\ndiswrapper\driver\hal.c
A    trunk\ndiswrapper\driver\wrapmem.c
[COLOR="Red"]A    trunk\ndiswrapper\driver\ntoskernel_io.c[/COLOR]
A    trunk\ndiswrapper\driver\wrapmem.h
A    trunk\ndiswrapper\driver\wrapper.c

... SKIPPED SKIPPED SKIPPED ...

A    trunk\ndiswrapper\README
Checked out revision 2728.



```

---

### Post by blocks on 2011-02-27
> **dbvolante said:**
> I'm stuck as well with WPA2 on 10.10, I got the drivers easily recognized by ndiswrapper 1.56-3 and all the files are in the correct positions, I can see all the access points around me but once I put in the password for my own access point, which has a WPA2 protection, nothing happens, it keeps trying and trying and then asks me again for the password (which is, of course, already the right one).
Any help?
Because I can't use Ubuntu without the wna3100 working. :(

Having this same problem. :(

---

### Post by blocks on 2011-03-02
Finally figured it out a few days ago and forgot to come back to this thread...

Here is a great how-to, especially for Ubuntu 10.10 and newer kernel users (on newer kernels, you need to patch ndiswrapper 1.56 before you compile, otherwise you will get compiling errors):

[http://reminiscenza.livejournal.com/2969.html](http://reminiscenza.livejournal.com/2969.html)

After following those steps listed above, if you have problems authenticating connection to your WAP...I'd try setting your router security settings strictly to WPA2...I'm not sure how that fixed the issue, but it did the trick for me.

Good luck.

---

### Post by dschwab on 2011-03-21
I tried the above and still can't get connection to show up...everything seems like it should be working:

lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 004: ID 0846:9020 NetGear, Inc. **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dougsc@Upstairs:~/Downloads/ndiswrapper-1.56/driver$ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9020) present
dougsc@Upstairs:~/Downloads/ndiswrapper-1.56/driver$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.35-28-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.56
vermagic:       2.6.35-28-generic SMP mod_unload modversions 686 

Any ideas on what I might be missing?

---

### Post by dschwab on 2011-03-21
Well, never mind, got it working, not sure how.   Last reboot seems to have done it.

Thanks for the thread.

---

### Post by seddare on 2011-04-14
Oi!

I'm fairly new to Ubuntu, I have just recently downloaded 11.04 (64bit amd). Me also wanted to use the WNA3100 USB adapter, but until now me failed. I followed all the steps given in other threads (and this one too). So first I got my ndiswrapper patched and the ntoskernel_io.c updated and it looks as indicated

```
david@ubuntu:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.38-8-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.56
vermagic:       2.6.38-8-generic SMP mod_unload modversions 

```

tried all the possible drivers (*bcmn43xx64*, *bcmwlhigh5* and *bcmwlhigh6*) and all of them found the device (e.g.: my latest attempt)

```

david@ubuntu:~$ ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9020) present

david@ubuntu:~$ sudo lsusb | grep NetGear
Bus 008 Device 002: ID 0846:9020 NetGear, Inc.

```

But 

```

david@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

**freaks** me out. This problem starts to seem unsolvable... ](*,)

---

### Post by jaccarmac on 2011-05-02
I have also just gotten this device and want it (heh-heh) to update a 10.10 install to 11.04. I hope that we can resolve this problem; the thread is scaring me a little :)

---

### Post by RoboCat on 2011-05-07
Hello I have spent 8 hours now and have had no luck!! This guy

[http://matthew-4gl.wikispaces.com/wna3100_ubuntu_linux](http://matthew-4gl.wikispaces.com/wna3100_ubuntu_linux)

posted the .sys and .inf files and extended your tutorial so it is real straight forward but I am still having no LUCK! First time I saved everything in temp and upon reboot I lost it all. (Is the tmp folder all RAM?) So I followed the tutorial  all over. I made sure to remove the old bcmwlhigh5.inf from ndiswrapper and then reinstall it:

[B]#sudo ndiswrapper -i bcmwlhigh5.inf

I do not get any errors but 

#*sudo iwlist wlan0 scanning      * 

is giving:     wlan0     Interface doesn't support scanning : Network is down

[/B][B]I can get my wireless card in my gateway to work with b43-fw cutter but I need the USB wireless adapter for the embedded computer at school, the gateway is just the test bed.

#*lsusb *     sees it

Bus 001 Device 004: ID 0846:9020 NetGear, Inc. 

But the little icon with the two PC's in the bottom right corner of Linux Mint does not.

I tried to shut the wlan0 down and bring it back up:

#[I]sudo ifconfig wlan0 down
[/I]#*sudo ifconfig wlan0 up* 

#*but still iwlist wlan0 scanning* 

gives same error. I tried shutting down without the usb wireless --> rebooting and only plugging it in after the desktop started and I get nothing. :< 

I tried restarting the PC with the [/B][B]0846:9020 device plugged in and I still get nothing?   

first this page:
a
[http://linuxwireless.org/en/users/Drivers/b43#support](http://linuxwireless.org/en/users/Drivers/b43#support)

and then the top post on this page

[http://forums.fedoraforum.org/archive/index.php/t-18566.html](http://forums.fedoraforum.org/archive/index.php/t-18566.html)

were ultimatly what got my built in gateway wireless working. This USB [/B]**0846:9020 device is recognized and works fine on my windows machiene so it is obviously not the device. Any help guys?**

---

### Post by RoboCat on 2011-05-07
Hello Didn't realize there was more than one page to this. I guess the only problem was the module did not get inserted into the kernel. After following:

[http://matthew-4gl.wikispaces.com/wna3100_ubuntu_linux](http://matthew-4gl.wikispaces.com/wna3100_ubuntu_linux)

If it doesnt work make sure to insert the module:

sudo insmod ndiswrapper.ko  

Someone needs to tell this guy to add it to his Wiki! (for completion of course) Also he needs to figure out how to make it sticky on the top of the Google search. 

gateway@gateway-laptop ~/programs/ndiswrapper-1.56/driver $ ls
built-in.o     Makefile              ntoskernel.h             usb_exports.h
crt.c          mkexport.sh           ntoskernel_io.c          usb.h
crt_exports.h  mkstubs.sh            ntoskernel_io_exports.h  usb.o
crt.o          Module.markers        ntoskernel_io.o          win2lin_stubs.S
divdi3.c       modules.order         ntoskernel.o             winnt_types.h
divdi3.o       Module.symvers        pe_linker.c              workqueue.c
hal.c          ndis.c                pe_linker.h              wrapmem.c
hal_exports.h  ndis_exports.h        pe_linker.o              wrapmem.h
hal.o          ndis.h                pnp.c                    wrapmem.o
iw_ndis.c      ndis.o                pnp.h                    wrapndis.c
iw_ndis.h      ndiswrapper.h         pnp.o                    wrapndis.h
iw_ndis.o      ndiswrapper.ko        proc.c                   wrapndis.o
lin2win.h      ndiswrapper.mod.c     proc.o                   wrapper.c
loader.c       ndiswrapper.mod.o     rtl.c                    wrapper.h
loader.h       ndiswrapper.o         rtl_exports.h            wrapper.o
loader.o       ntoskernel.c          rtl.o
longlong.h     ntoskernel_exports.h  usb.c
gateway@gateway-laptop ~/programs/ndiswrapper-1.56/driver $ sudo insmod ndiswrapper.ko  
gateway@gateway-laptop ~/programs/ndiswrapper-1.56/driver $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan2     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gateway@gateway-laptop ~/programs/ndiswrapper-1.56/driver $ iwlist wlan2 scan
wlan2     Scan completed :
          Cell 01 - Address: C0:3F:0E:03:EC:66
                    ESSID:"GHOSTSHIP-Wireless"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


As you can see the usb wireless is showing up as wlan2 after
#sudo  iwlist wlan2 scan

If you still cant get it to work make your ip's static from the top of this thread. [http://forums.fedoraforum.org/archive/index.php/t-18566.html](http://forums.fedoraforum.org/archive/index.php/t-18566.html)

also your probably going to have to make a boot file to run the insmod everytime you reboot. Not sure yet, just happy I can see my Router!!!!

Thanks,
Steve

---

### Post by Wahlgren on 2011-05-13
Someone managed to get this to work under Ubuntu 11.04? I've had it working in Ubuntu 10.10 without any problems, but in 11.04 I can't compile ndiswrapper with the extra code and kernel patch as described here [http://reminiscenza.livejournal.com/2969.html](http://reminiscenza.livejournal.com/2969.html)

Maybe because Ubuntu 11.04 use kernel 2.6.38?

---

### Post by pfc2k8 on 2011-06-05
Just get this to work under Ubuntu 11.04 32bit.

1. add this lines to the end of the file "ntoskernel-io.c"
```
wstdcall NTSTATUS WIN_FUNC(IoUnregisterPlugPlayNotification,1)
    (void *tag)
{
    TRACE2("%p", tag);
    TODO(); /* Probably Not, legacy function abandoned in Windows 7 */
    IOEXIT(return STATUS_SUCCESS); /* Linux doesn't use it either */
}
```2. Patches:

[LIST]
[*][http://launchpadlibrarian.net/58046844/ndiswrapper-suse.patch](http://launchpadlibrarian.net/58046844/ndiswrapper-suse.patch)
[*][http://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-x86/net-wireless/ndiswrapper/files/ndiswrapper-1.56-2.6.35.patch?revision=1.1](http://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-x86/net-wireless/ndiswrapper/files/ndiswrapper-1.56-2.6.35.patch?revision=1.1)
[/LIST]
```
$ cd ndiswrapper-1.56
$ patch -Np0 < ../ndiswrapper-suse.patch
$ patch -Np0 < ../ndiswrapper-1.56-2.6.35.patch

or how you named them...
```In case to get no errors during compiling you need to change a few lines in "wrapndis.c".
Change this:
```
#include "ndis.h"
#include "iw_ndis.h"
#include "pnp.h"
#include "loader.h"
#include "wrapndis.h"
#include <linux/inetdevice.h>
#include <linux/ip.h>
#include <linux/tcp.h>
#include <linux/udp.h>
#include <linux/in.h>
#include "wrapper.h"
```to this:
```
#include <linux/inetdevice.h>
#include <linux/ip.h>
#include <linux/tcp.h>
#include <linux/udp.h>
#include <linux/in.h>
#include "ndis.h"
#include "iw_ndis.h"
#include "pnp.h"
#include "loader.h"
#include "wrapndis.h"
#include "wrapper.h"
```Now you could compile it without errors.

Just do make, make install, install the bcmwlhigh5.inf, do:
```
$ sudo ndiswrapper -m
$ sudo modprobe ndiswrapper
```to load the module at any startup and now the WNA3100 should work.
At least it works so for me.

---

### Post by Flying Pikachu on 2011-06-12
> **pfc2k8 said:**
> Just get this to work under Ubuntu 11.04 32bit.

1. add this lines to the end of the file "ntoskernel-io.c"
```
wstdcall NTSTATUS WIN_FUNC(IoUnregisterPlugPlayNotification,1)
    (void *tag)
{
    TRACE2("%p", tag);
    TODO(); /* Probably Not, legacy function abandoned in Windows 7 */
    IOEXIT(return STATUS_SUCCESS); /* Linux doesn't use it either */
}
```2. Patches:

[LIST]
[*][http://launchpadlibrarian.net/58046844/ndiswrapper-suse.patch](http://launchpadlibrarian.net/58046844/ndiswrapper-suse.patch)
[*][http://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-x86/net-wireless/ndiswrapper/files/ndiswrapper-1.56-2.6.35.patch?revision=1.1](http://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-x86/net-wireless/ndiswrapper/files/ndiswrapper-1.56-2.6.35.patch?revision=1.1)
[/LIST]
```
$ cd ndiswrapper-1.56
$ patch -Np0 < ../ndiswrapper-suse.patch
$ patch -Np0 < ../ndiswrapper-1.56-2.6.35.patch

or how you named them...
```In case to get no errors during compiling you need to change a few lines in "wrapndis.c".
Change this:
```
#include "ndis.h"
#include "iw_ndis.h"
#include "pnp.h"
#include "loader.h"
#include "wrapndis.h"
#include <linux/inetdevice.h>
#include <linux/ip.h>
#include <linux/tcp.h>
#include <linux/udp.h>
#include <linux/in.h>
#include "wrapper.h"
```to this:
```
#include <linux/inetdevice.h>
#include <linux/ip.h>
#include <linux/tcp.h>
#include <linux/udp.h>
#include <linux/in.h>
#include "ndis.h"
#include "iw_ndis.h"
#include "pnp.h"
#include "loader.h"
#include "wrapndis.h"
#include "wrapper.h"
```Now you could compile it without errors.

Just do make, make install, install the bcmwlhigh5.inf, do:
```
$ sudo ndiswrapper -m
$ sudo modprobe ndiswrapper
```to load the module at any startup and now the WNA3100 should work.
At least it works so for me.

Does this work with 64-Bit Ubuntu 11.04?

---

### Post by skalig on 2011-06-30
Any news on 64bit for this Adapter?

---

### Post by wetzeldc on 2011-06-30
I to have a WNA3100 that I bought because someone has it running.  I have been following along and apparently have the driver is installed on my system and NetGear shows up in the lsusb listing.  If the drivers are properly installed, how do you connect to the router and enter the security key?  Or did I miss that somewhere?

---

### Post by parsim on 2011-06-30
Well I don't have a solution, but thought I'd summarize my failed attempts to get this thing working under Ubuntu 11.04 64-bit.

```
$ lsusb
...
Bus 002 Device 003: ID 0846:9020 NetGear, Inc.
```

Using driver **bcmwlhigh6**, obtained from C:\Program Files\NETGEAR\ after installing the WNA3100_v1.1.3.22_Setup.exe file downloadable from the netgear.com site on a Windows 7 64-bit machine:
```
 $ sudo dmesg -c
[ 2435.380021] usb 2-1: new high speed USB device using ehci_hcd and address 4
[ 2435.660023] usb 2-1: reset high speed USB device using ehci_hcd and address 4
[ 2435.814253] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[ 2435.814270] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoRegisterPlugPlayNotification'
[ 2435.814289] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 2435.814295] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 2435.814300] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 2435.814308] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[ 2435.814314] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[ 2435.814320] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 2435.814325] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 2435.814331] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 2435.814337] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 2435.814344] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[ 2435.814353] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 2435.814358] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMFreePort'
[ 2435.814364] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 2435.814369] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[ 2435.814375] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 2435.814380] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 2435.814386] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[ 2435.814392] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 2435.814397] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[ 2435.814403] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[ 2435.814409] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[ 2435.814415] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 2435.814421] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 2435.814431] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 2435.814436] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 2435.814442] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 2435.814448] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 2435.814457] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 2435.814470] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 2435.814475] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[ 2435.814480] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[ 2435.814484] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[ 2435.814489] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[ 2435.814492] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh6'
[ 2435.814822] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
```

Messing around with a modified ntoskernel_io.c and a custom-installed ndiswrapper as per instructions earlier in this thread gets rid of the first warning, but otherwise same result:
```
$ sudo dmesg -c
[ 4245.700034] usb 2-1: new high speed USB device using ehci_hcd and address 11
[ 4245.880337] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 4246.000020] usb 2-1: reset high speed USB device using ehci_hcd and address 11
[ 4246.153758] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoRegisterPlugPlayNotification'
[ 4246.153780] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 4246.153786] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 4246.153791] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 4246.153799] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[ 4246.153805] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[ 4246.153810] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 4246.153816] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 4246.153822] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 4246.153827] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 4246.153835] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[ 4246.153843] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 4246.153849] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMFreePort'
[ 4246.153854] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 4246.153860] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[ 4246.153866] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 4246.153871] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 4246.153877] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[ 4246.153882] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 4246.153888] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[ 4246.153893] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[ 4246.153900] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[ 4246.153906] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 4246.153911] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 4246.153922] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 4246.153927] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 4246.153933] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 4246.153938] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 4246.153948] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 4246.153961] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 4246.153965] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[ 4246.153970] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[ 4246.153975] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[ 4246.153979] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[ 4246.153982] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh6'
[ 4246.154318] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
[ 4246.154469] usbcore: registered new interface driver ndiswrapper
```

No luck with the Broadcom 32-bit driver **bcmn43xx32**:
```
$ sudo ndiswrapper -l
bcmn43xx32 : driver installed
bcmn43xx64 : driver installed
bcmwl6 : driver installed
bcmwlhigh5 : driver installed
bcmwlhigh6 : driver installed
$ sudo dmesg -c
[ 4106.696609] usb 2-1: USB disconnect, address 9
[ 4114.011744] usbcore: deregistering interface driver ndiswrapper
[ 4114.012561] ndiswrapper (ntoskernel_exit:2677): object ffff8800c5e5c030(2) was not freed, freeing it now
[ 4114.012565] ndiswrapper (ntoskernel_exit:2677): object ffff88003b843a30(2) was not freed, freeing it now
[ 4114.012568] ndiswrapper (ntoskernel_exit:2677): object ffff880036f66e30(2) was not freed, freeing it now
[ 4170.030023] usb 2-1: new high speed USB device using ehci_hcd and address 10
[ 4170.209674] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 4170.330027] usb 2-1: reset high speed USB device using ehci_hcd and address 10
[ 4170.483027] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 4170.483032] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmn43xx32'
[ 4170.483365] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
[ 4170.483511] usbcore: registered new interface driver ndiswrapper
```

And the 64-bit one **bcmn43xx64** crashes, after which commands like 'lsusb' hang indefinitely and I have to reboot:
```
$ sudo dmesg -c
[ 4260.661786] usb 2-1: USB disconnect, address 11
[ 4264.111912] usbcore: deregistering interface driver ndiswrapper
[ 4264.112710] ndiswrapper (ntoskernel_exit:2677): object ffff88008c028a30(2) was not freed, freeing it now
[ 4282.030027] usb 2-1: new high speed USB device using ehci_hcd and address 12
[ 4282.209619] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 4282.330022] usb 2-1: reset high speed USB device using ehci_hcd and address 12
[ 4282.483727] ndiswrapper (link_pe_images:566): fixing KI_USER_SHARED_DATA address in the driver
[ 4282.485637] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 4282.487693] BUG: unable to handle kernel paging request at 00000000ffffffd0
[ 4282.487698] IP: [<ffffffffa0ff8d89>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[ 4282.487726] PGD 1242a4067 PUD 0 
[ 4282.487730] Oops: 0000 [#1] SMP 
[ 4282.487733] last sysfs file: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/bInterfaceSubClass
[ 4282.487736] CPU 1 
[ 4282.487738] Modules linked in: ndiswrapper(+) rndis_host cdc_ether usbnet cryptd aes_x86_64 aes_generic binfmt_misc vboxnetadp vboxnetflt vboxdrv vmnet vmblock vsock vmci vmmon parport_pc ppdev vesafb nvidia(P) snd_hda_codec_realtek arc4 rt61pci rt2x00pci rt2x00lib mac80211 snd_hda_intel snd_hda_codec snd_hwdep joydev snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event cfg80211 snd_seq eeprom_93cx6 snd_timer snd_seq_device snd serio_raw asus_atk0110 soundcore snd_page_alloc firewire_sbp2 firewire_core crc_itu_t lp parport hid_microsoft raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov usbhid hid pata_marvell ahci libahci atl1 raid6_pq async_tx raid1 raid0 multipath linear [last unloaded: ndiswrapper]
[ 4282.487790] 
[ 4282.487793] Pid: 9816, comm: modprobe Tainted: P            2.6.38-8-generic #42-Ubuntu System manufacturer P5K SE/EPU/P5K SE/EPU
[ 4282.487799] RIP: 0010:[<ffffffffa0ff8d89>]  [<ffffffffa0ff8d89>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[ 4282.487818] RSP: 0018:ffff880121be3740  EFLAGS: 00010286
[ 4282.487820] RAX: ffffffffa0ff8d80 RBX: ffff88008c2fe000 RCX: ffff880036ca2b00
[ 4282.487823] RDX: 000000000000000a RSI: ffff880121001200 RDI: 00000000ffffff38
[ 4282.487825] RBP: ffff880121be3740 R08: 0000000000000000 R09: 0000000000000000
[ 4282.487828] R10: ffffffffa0fe9a90 R11: ffff880121001318 R12: ffff880037d40c00
[ 4282.487830] R13: 0000000000000000 R14: ffff880121000430 R15: ffff880121000230
[ 4282.487833] FS:  00007f8003bc9720(0000) GS:ffff8800cfc80000(0000) knlGS:0000000000000000
[ 4282.487836] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[ 4282.487838] CR2: 00000000ffffffd0 CR3: 0000000126dff000 CR4: 00000000000006e0
[ 4282.487840] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 4282.487843] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 4282.487846] Process modprobe (pid: 9816, threadinfo ffff880121be2000, task ffff880037d716e0)
[ 4282.487847] Stack:
[ 4282.487849]  ffff8801210012d0 ffffc90011e93da8 ffff88008c2fe000 ffff8801210012d0
[ 4282.487853]  ffff880121001200 ffff880121be3788 ffffffffa0fe18ba ffff880121000430
[ 4282.487858]  0000000000000000 ffff880036ca2b00 ffffffffa0ff8da0 ffffffffa0ff8dd0
[ 4282.487862] Call Trace:
[ 4282.487877]  [<ffffffffa0fe18ba>] ? NdisAllocateMemoryWithTag+0x1a/0x40 [ndiswrapper]
[ 4282.487895]  [<ffffffffa0ff8da0>] ? USBD_InterfaceReference+0x0/0x30 [ndiswrapper]
[ 4282.487913]  [<ffffffffa0ff8dd0>] ? USBD_InterfaceDereference+0x0/0x30 [ndiswrapper]
[ 4282.487930]  [<ffffffffa0ff8d40>] ? USBD_InterfaceGetUSBDIVersion+0x0/0x40 [ndiswrapper]
[ 4282.487948]  [<ffffffffa0ff8e00>] ? USBD_InterfaceQueryBusTime+0x0/0x30 [ndiswrapper]
[ 4282.487965]  [<ffffffffa0ff8e30>] ? USBD_InterfaceSubmitIsoOutUrb+0x0/0x30 [ndiswrapper]
[ 4282.487982]  [<ffffffffa0ff8e60>] ? USBD_InterfaceQueryBusInformation+0x0/0x30 [ndiswrapper]
[ 4282.488000]  [<ffffffffa0ff8d80>] ? USBD_InterfaceIsDeviceHighSpeed+0x0/0x20 [ndiswrapper]
[ 4282.488017]  [<ffffffffa0fe887c>] ? ExAllocatePoolWithTag+0x3c/0x80 [ndiswrapper]
[ 4282.488034]  [<ffffffffa0ff8fcb>] ? win2lin3+0x11/0x14 [ndiswrapper]
[ 4282.488051]  [<ffffffffa0ff46d2>] ? mp_init+0x72/0x210 [ndiswrapper]
[ 4282.488068]  [<ffffffffa0fec760>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[ 4282.488084]  [<ffffffffa0fecab6>] ? IoSyncForwardIrp+0x96/0xe0 [ndiswrapper]
[ 4282.488090]  [<ffffffff8104dde6>] ? enqueue_task+0x66/0x80
[ 4282.488108]  [<ffffffffa0ff676b>] ? NdisDispatchPnp+0xcb/0xc30 [ndiswrapper]
[ 4282.488124]  [<ffffffffa0fec0d4>] ? IoAllocateIrp+0x54/0x80 [ndiswrapper]
[ 4282.488141]  [<ffffffffa0febff7>] ? IoInitializeIrp+0x37/0x70 [ndiswrapper]
[ 4282.488157]  [<ffffffffa0fec0ea>] ? IoAllocateIrp+0x6a/0x80 [ndiswrapper]
[ 4282.488174]  [<ffffffffa0ff8fb7>] ? win2lin2+0xe/0x11 [ndiswrapper]
[ 4282.488191]  [<ffffffffa0fec760>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[ 4282.488207]  [<ffffffffa0fec78c>] ? IofCallDriver+0x6c/0xc0 [ndiswrapper]
[ 4282.488212]  [<ffffffff815c2bd9>] ? _raw_spin_unlock_bh+0x19/0x20
[ 4282.488228]  [<ffffffffa0fec760>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[ 4282.488244]  [<ffffffffa0fee517>] ? IoSendIrpTopDev+0xd7/0x120 [ndiswrapper]
[ 4282.488248]  [<ffffffff815c2bd9>] ? _raw_spin_unlock_bh+0x19/0x20
[ 4282.488252]  [<ffffffff815c2bd9>] ? _raw_spin_unlock_bh+0x19/0x20
[ 4282.488268]  [<ffffffffa0feed3c>] ? pnp_start_device+0x4c/0x90 [ndiswrapper]
[ 4282.488286]  [<ffffffffa0fef16f>] ? wrap_pnp_start_device+0x1af/0x270 [ndiswrapper]
[ 4282.488302]  [<ffffffffa0fef401>] ? wrap_pnp_start_usb_device+0xf1/0x120 [ndiswrapper]
[ 4282.488307]  [<ffffffff813c36a1>] ? __pm_runtime_set_status+0x141/0x210
[ 4282.488311]  [<ffffffff813c3c1d>] ? __pm_runtime_resume+0x5d/0x80
[ 4282.488316]  [<ffffffff8143e439>] ? usb_probe_interface+0x109/0x200
[ 4282.488320]  [<ffffffff813ba858>] ? really_probe+0x68/0x190
[ 4282.488323]  [<ffffffff813bab65>] ? driver_probe_device+0x45/0x70
[ 4282.488327]  [<ffffffff813bac3b>] ? __driver_attach+0xab/0xb0
[ 4282.488330]  [<ffffffff813bab90>] ? __driver_attach+0x0/0xb0
[ 4282.488333]  [<ffffffff813b99de>] ? bus_for_each_dev+0x5e/0x90
[ 4282.488336]  [<ffffffff813ba6ae>] ? driver_attach+0x1e/0x20
[ 4282.488339]  [<ffffffff813ba215>] ? bus_add_driver+0xc5/0x280
[ 4282.488343]  [<ffffffff813baed6>] ? driver_register+0x76/0x140
[ 4282.488347]  [<ffffffff811d4891>] ? sysfs_add_file+0x11/0x20
[ 4282.488351]  [<ffffffff8143d008>] ? usb_register_driver+0xb8/0x170
[ 4282.488362]  [<ffffffffa0d2f000>] ? wrapper_init+0x0/0x1000 [ndiswrapper]
[ 4282.488375]  [<ffffffffa0fe11ac>] ? loader_init+0xcc/0x160 [ndiswrapper]
[ 4282.488386]  [<ffffffffa0d2f07b>] ? wrapper_init+0x7b/0x1000 [ndiswrapper]
[ 4282.488391]  [<ffffffff81002175>] ? do_one_initcall+0x45/0x190
[ 4282.488395]  [<ffffffff810a4feb>] ? sys_init_module+0xfb/0x250
[ 4282.488399]  [<ffffffff8100c002>] ? system_call_fastpath+0x16/0x1b
[ 4282.488401] Code: 00 00 83 79 1c 03 b9 10 01 00 00 0f 45 c1 89 46 04 c7 02 01 00 00 00 c9 c3 66 0f 1f 84 00 00 00 00 00 55 48 89 e5 0f 1f 44 00 00 <48> 8b 87 98 00 00 00 83 78 1c 03 c9 0f 94 c0 c3 0f 1f 80 00 00 
[ 4282.488435] RIP  [<ffffffffa0ff8d89>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[ 4282.488454]  RSP <ffff880121be3740>
[ 4282.488455] CR2: 00000000ffffffd0
[ 4282.488458] ---[ end trace 5f93b64c6a1ee9e4 ]---
 $ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper is in use
```

---

### Post by wetzeldc on 2011-07-04
I almost have it working.  Almost.  At startup I am prompted "Authentication Required by Wireless Network".  The wireless network icon in the upper right corner is running, and yet Firefox cannot find the connection.

Does the following provide any clues?

david@No2:~$ dmesg | grep -e ndis -e wlan
[    4.564523] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[    5.492705] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[    5.492815] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[    6.086263] wlan0: ethernet device e0:91:f5:59:86:cc using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[    6.090385] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[    6.091711] usbcore: registered new interface driver ndiswrapper
[   13.107864] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  118.291340] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  128.953138] wlan0: no IPv6 routers present
david@No2:~$

---

### Post by robert.erickson on 2011-08-23
p { margin-bottom: 0.08in; }  [SIZE=3][COLOR=#000000][FONT=Times New Roman, serif]Okay, so I followed these steps below.

[/FONT][/COLOR][/SIZE][INDENT][SIZE=3][COLOR=#000000][FONT=Times New Roman, serif]Locate [/FONT][FONT=Times New Roman, serif]*ntoskernal_io.c*[/FONT][FONT=Times New Roman, serif] in the ndiswrapper & add the following lines at the end of the file[/FONT][/COLOR][/SIZE]
```

wstdcall NTSTATUS WIN_FUNC(IoUnregisterPlugPlayNotification,1)[INDENT](void *tag) /* Don't ever use this pointer */
[/INDENT]{[INDENT]TRACE2("%p", tag);
[/INDENT][INDENT]TODO(); /* Probably Not, legacy function abandoned in Windows 7 */
[/INDENT][INDENT]IOEXIT(return STATUS_SUCCESS); /* Linux doesn't use it either */
[/INDENT]}
```[SIZE=3][COLOR=#000000][FONT=Times New Roman, serif]**cd**[/FONT][FONT=Times New Roman, serif] to the ndiswrapper folder[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman, serif]**sudo make**[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman, serif]**sudo make install**[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman, serif]Download bcmwlhigh5.inf & bcmwlhigh5.sys[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman, serif]After extracting the above files, [/FONT][FONT=Times New Roman, serif]**cd**[/FONT][FONT=Times New Roman, serif] to the folder.[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman, serif]Then type in a terminal [/FONT][FONT=Times New Roman, serif]**sudo ndiswrapper -i bcmwlhigh5.inf**[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman, serif]Now turn off your computer & remove the WNA3100 USB stick from it's cradle[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman, serif]Turn your computer back on & log in[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Times New Roman, serif]Wait until you're at the Ubuntu Desktop & insert the WNA3100 USB stick in it's cradle

[/FONT][/COLOR][/SIZE][/INDENT]After following these steps, my computer still wasn't recognizing the wireless connection. I then used terminal to execute this code

sudo insmod /home/name/ndiswrapper-1.56/driver/ndiswrapper.ko

As soon as I do do that, the connection is found.  I am using the wirelss connection to write and post this, the only catch is. If I try to download or load pages that are large, the connection stops and the only remedy is to restart the computer and re-execute 
sudo insmod /home/name/ndiswrapper-1.56/driver/ndiswrapper.ko

Most webpages work just fine, but youtube always ends the connection, downloading torrents ends the connection, pretty much downloading anything over 30 MB ends the connection. I did try to download a 700 MB file and the progress made it to 98 MB before ending the connection, however, I have also tried to download a 25 MB files and it only made it to 10 MB.

Does anyone have any idea why it might be doing this? Any bit of info helps. Here's a printout of a few commands in terminal.

```
name@name-desktop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.31-21-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.31-21-generic SMP mod_unload modversions 586
``````
name@name-desktop:~$ sudo ifconfig
[sudo] password for name: 
eth0      Link encap:Ethernet  HWaddr 00:13:20:53:6e:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10012 (10.0 KB)  TX bytes:10012 (10.0 KB)

wlan0     Link encap:Ethernet  HWaddr e0:46:9a:01:c3:26  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e246:9aff:fe01:c326/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:140917 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151640290 (151.6 MB)  TX bytes:22122415 (22.1 MB)
``````
name@name-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ANONYMOUS"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: A6:21:B7:A4:60:D0   
          Bit Rate=104 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by shortt86 on 2011-08-30
Hi there, I've got the same WNA3100, got Ubuntu Lucid, 32 bit installed yesterday and it's typical that as a total newbie I'm stuck with such a troublesome wireless adaptor. I've tried following the steps here but just can't get any sign of wlan0. I have no idea whether there's something I should have installed and haven't, but here is the current situation, I hope someone can help... (be patient if I forget some info, there's a whole load of unfamiliar commands spinning around my head at the moment).

ndiswrapper -v
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-33-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.32-33-generic SMP mod_unload modversions 586 
```ndiswrapper -l
```
bcmwlhigh5 : driver installed
    device (0846:9020) present

```lsusb
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 003: ID 03f0:3407 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```modprobe ndiswrapper gives no output.

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:00:13:e3:7f:fd  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:13ff:fee3:7ffd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:829 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:806128 (806.1 KB)  TX bytes:176615 (176.6 KB)
          Interrupt:19 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```I've changed the usb socket a couple of times to no avail. dmesg ends with this:

```
[  107.349048] serial8250: too much work for irq19
[  696.310193] Disabling lock debugging due to kernel taint
[  696.319547] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  696.436023] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[  696.603133] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[  696.603401] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh5'
[  696.604485] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[  696.604616] usbcore: registered new interface driver ndiswrapper
```There's a whole stream of these 'serial8250: too much work for irq19' and I don't know what it means. The WNA3100 worked fine in these usb sockets on Windows XP. I really hope someone can help, I'm so frustrated right now because I switched to Linux in the hope of it offering more freedom and ease of use, which I am convinced it still will once I get this d--- wireless sorted...:(

---

### Post by milnersmithj on 2011-10-25
Hey, I'm very very new to this Ubuntu. I love it and want to get my WNA3100 Wireless Adapter working. I have done all the steps to get it to search and try and connect to my home network. It gets to the point where it asks for the password to get onto the network, but then it is just forever loading and wont connect until eventually it will ask for the pass again. I am 100% sure it's the right password and I have done all the steps up until this point. I have restarted, still the same problem. 

Thanks in advance for your help.

---

### Post by Dennuzzz on 2011-10-31
> **milnersmithj said:**
> Hey, I'm very very new to this Ubuntu. I love it and want to get my WNA3100 Wireless Adapter working. I have done all the steps to get it to search and try and connect to my home network. It gets to the point where it asks for the password to get onto the network, but then it is just forever loading and wont connect until eventually it will ask for the pass again. I am 100% sure it's the right password and I have done all the steps up until this point. I have restarted, still the same problem. 

Thanks in advance for your help.

I have exactly the same problem!
I can establish a connection to a NOT ENCRYPTED wireless network, but of course is my connection encrypted using WPA2... But than it doesn't connect and it sais invalid password. But I am 100% sure it is the right one, because it is working on my iPod and on Windows so...
Anyone has any ideas or recommandations?
I really like to see them, because now I am stuck to Windows... again

---

### Post by SenLin on 2011-11-15
I know this is getting to be an old thread, but for the sake of others who are still searching and stumbling through here, I wanted to quickly tell what worked for me.

Thanks, guys, for all your work...I was about to follow your instructions for modding ndiswrapper (1.56), but decided first to try compiling the latest "beta" (ndiswrapper-1.57rc1) without any changes...and...VOILA! It worked!

So, for those still searching:
[LIST=1]
[*]Grab the latest (at least 1.57) source code at [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)
[*]extract, 'cd' into the folder, 'make uninstall', 'make', 'make install, (as per the simple instructions in the extracted INSTALL file ;o)
[*]Use your shiny NEW ndiswrapper to install your .inf driver:
```
sudo ndiswrapper -i /LOCATION/OF/bcmwlhigh5.inf
```
[/LIST]

Hopefully, it won't be long till this works its way into all of our systems anyway!

---

### Post by parsim on 2011-11-15
Is the above 32-bit or 64-bit?

---

### Post by SenLin on 2011-11-18
> **parsim said:**
> Is the above 32-bit or 64-bit?

I didn't even think about that before, but surprisingly enough, it seems to work for both. I tried it first on a 32-bit BT5 (Ubuntu10.4) USB system, then later on my 64-bit Fedora 16 Thinkpad. Worked like a charm on both!

I haven't worked much with it on the 64bit system, though, since I have an internal adapter there, so...will need some more testing to be sure.

---

### Post by m.foster on 2011-11-26
Does anybody know a way to make this Netgear WNA3100 driver work without ndiswrapper or atleast to make it support monitor mode. thank you for any suggestions.

---

### Post by kurt18947 on 2011-11-27
> **m.foster said:**
> Does anybody know a way to make this Netgear WNA3100 driver work without ndiswrapper or atleast to make it support monitor mode. thank you for any suggestions.

Native support doesn't seem real likely in the near future.
[http://www.wikidevi.com/wiki/Netgear_WNA3100](http://www.wikidevi.com/wiki/Netgear_WNA3100)

---

### Post by parsim on 2011-11-27
> **SenLin said:**
> I didn't even think about that before, but surprisingly enough, it seems to work for both. I tried it first on a 32-bit BT5 (Ubuntu10.4) USB system, then later on my 64-bit Fedora 16 Thinkpad. Worked like a charm on both!

I haven't worked much with it on the 64bit system, though, since I have an internal adapter there, so...will need some more testing to be sure.

Still no good on 11.10 64-bit here, unfortunately. After following your steps and plugging in the device, I got:
```
[  321.892018] usb 1-5: new high speed USB device number 7 using ehci_hcd
[  323.216111] usb 1-5: usbfs: USBDEVFS_CONTROL failed cmd mtp-probe rqt 128 rq 6 len 1024 ret -110
```
I removed libmtp-runtime [as recommended here](http://us.generation-nt.com/answer/bug-630202-libmtp-runtime-mtp-probe-prevents-virtualbox-guest-access-scanner-usb-port-help-203717242.html#203717252) and that got rid of the error, but still the system wasn't loading the driver.

So then I forced it with:
```
sudo ndiswrapper -a 0846:9020 bcmwlhigh5
```
and got this:
```
[  665.924025] usb 1-5: new high speed USB device number 9 using ehci_hcd
[  666.176035] usb 1-5: reset high speed USB device number 9 using ehci_hcd
[  666.368920] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
[  666.370382] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[  666.372530] BUG: unable to handle kernel paging request at 00000000ffffffd0
[  666.372536] IP: [<ffffffffa0e8ce39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[  666.372560] PGD b188e067 PUD 0 
[  666.372563] Oops: 0000 [#1] SMP 
[  666.372567] CPU 0 
[  666.372568] Modules linked in: pci_stub vboxpci vboxnetadp vboxnetflt vboxdrv parport_pc ppdev vesafb ndiswrapper binfmt_misc snd_hda_codec_hdmi joydev snd_seq_midi snd_hda_codec_realtek nvidia(P) snd_rawmidi snd_hda_intel snd_hda_codec snd_hwdep snd_pcm dm_multipath snd_seq_midi_event snd_seq snd_timer snd_seq_device serio_raw snd asus_atk0110 soundcore snd_page_alloc firewire_sbp2 firewire_core crc_itu_t lp parport hid_microsoft usbhid hid raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov pata_marvell ahci libahci atl1 natsemi raid6_pq async_tx raid1 raid0 multipath linear
[  666.372610] 
[  666.372613] Pid: 20, comm: khubd Tainted: P            3.0.0-13-generic #22-Ubuntu System manufacturer P5K SE/EPU/P5K SE/EPU
[  666.372622] RIP: 0010:[<ffffffffa0e8ce39>]  [<ffffffffa0e8ce39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[  666.372634] RSP: 0018:ffff8801281e3358  EFLAGS: 00010286
[  666.372635] RAX: ffffffffa0e8ce30 RBX: ffff880104bb8000 RCX: ffff8800b5b31900
[  666.372637] RDX: 000000000000000a RSI: ffff8800ad51c600 RDI: 00000000ffffff38
[  666.372638] RBP: ffff8801281e3358 R08: 0000000000000000 R09: 0000000000000000
[  666.372640] R10: ffffffffa0e7de30 R11: ffff8800ad51c718 R12: ffff88009249f000
[  666.372642] R13: 0000000000000000 R14: ffff8800bb09e430 R15: 0000000000000000
[  666.372644] FS:  0000000000000000(0000) GS:ffff88012fc00000(0000) knlGS:0000000000000000
[  666.372646] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  666.372647] CR2: 00000000ffffffd0 CR3: 00000000b5bb5000 CR4: 00000000000006f0
[  666.372649] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  666.372650] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  666.372652] Process khubd (pid: 20, threadinfo ffff8801281e2000, task ffff880128ff4560)
[  666.372654] Stack:
[  666.372655]  ffff8800ad51c6d0 ffffc900158c1da8 ffff880104bb8000 ffff8800ad51c6d0
[  666.372658]  ffff8800ad51c600 ffff8801281e33a0 ffffffffa0e75c7a ffff8801281e33a0
[  666.372661]  0000000000000000 ffff8800b5b31900 ffffffffa0e8ce50 ffffffffa0e8ce80
[  666.372664] Call Trace:
[  666.372672]  [<ffffffffa0e75c7a>] ? NdisAllocateMemoryWithTag+0x1a/0x40 [ndiswrapper]
[  666.372683]  [<ffffffffa0e8ce50>] ? USBD_InterfaceIsDeviceHighSpeed+0x20/0x20 [ndiswrapper]
[  666.372693]  [<ffffffffa0e8ce80>] ? USBD_InterfaceReference+0x30/0x30 [ndiswrapper]
[  666.372703]  [<ffffffffa0e8cdf0>] ? USBD_GetUSBDIVersion+0x20/0x20 [ndiswrapper]
[  666.372714]  [<ffffffffa0e8ceb0>] ? USBD_InterfaceDereference+0x30/0x30 [ndiswrapper]
[  666.372724]  [<ffffffffa0e8cee0>] ? USBD_InterfaceQueryBusTime+0x30/0x30 [ndiswrapper]
[  666.372734]  [<ffffffffa0e8cf10>] ? USBD_InterfaceSubmitIsoOutUrb+0x30/0x30 [ndiswrapper]
[  666.372744]  [<ffffffffa0e8ce30>] ? USBD_InterfaceGetUSBDIVersion+0x40/0x40 [ndiswrapper]
[  666.372753]  [<ffffffffa0e7aef0>] ? ExAllocatePoolWithTag.part.9+0x30/0x40 [ndiswrapper]
[  666.372762]  [<ffffffffa0e7cbfa>] ? ExAllocatePoolWithTag+0x1a/0x60 [ndiswrapper]
[  666.372772]  [<ffffffffa0e8d07b>] ? win2lin3+0x11/0x14 [ndiswrapper]
[  666.372777]  [<ffffffff8106fab3>] ? mod_timer+0x143/0x2f0
[  666.372787]  [<ffffffffa0e88e02>] ? mp_init+0x72/0x210 [ndiswrapper]
[  666.372797]  [<ffffffffa0e82eca>] ? pdoDispatchPnp+0x5a/0x190 [ndiswrapper]
[  666.372806]  [<ffffffffa0e80bb0>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[  666.372816]  [<ffffffffa0e89fbb>] ? ndis_start_device+0x2b/0x870 [ndiswrapper]
[  666.372821]  [<ffffffff815ea4e9>] ? _raw_spin_unlock_bh+0x19/0x20
[  666.372830]  [<ffffffffa0e80bb0>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[  666.372839]  [<ffffffffa0e80f26>] ? IoSyncForwardIrp+0x96/0xe0 [ndiswrapper]
[  666.372850]  [<ffffffffa0e8b073>] ? NdisDispatchPnp+0xa3/0x150 [ndiswrapper]
[  666.372860]  [<ffffffffa0e8d067>] ? win2lin2+0xe/0x11 [ndiswrapper]
[  666.372869]  [<ffffffffa0e80bb0>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[  666.372878]  [<ffffffffa0e80bdc>] ? IofCallDriver+0x6c/0xc0 [ndiswrapper]
[  666.372881]  [<ffffffff815ea4e9>] ? _raw_spin_unlock_bh+0x19/0x20
[  666.372890]  [<ffffffffa0e80bb0>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[  666.372899]  [<ffffffffa0e828d7>] ? IoSendIrpTopDev+0xd7/0x120 [ndiswrapper]
[  666.372902]  [<ffffffff815ea4e9>] ? _raw_spin_unlock_bh+0x19/0x20
[  666.372912]  [<ffffffffa0e831dc>] ? pnp_start_device+0x4c/0x90 [ndiswrapper]
[  666.372921]  [<ffffffffa0e83531>] ? wrap_pnp_start_device+0xd1/0x180 [ndiswrapper]
[  666.372931]  [<ffffffffa0e837bf>] ? wrap_pnp_start_usb_device+0xef/0x120 [ndiswrapper]
[  666.372935]  [<ffffffff813d87fb>] ? __pm_runtime_set_status+0x11b/0x1d0
[  666.372937]  [<ffffffff813d829a>] ? __pm_runtime_resume+0x5a/0x70
[  666.372941]  [<ffffffff81450b63>] ? usb_probe_interface+0xd3/0x1e0
[  666.372944]  [<ffffffff813ce948>] ? really_probe+0x68/0x190
[  666.372946]  [<ffffffff813cebd5>] ? driver_probe_device+0x45/0x70
[  666.372949]  [<ffffffff813ced03>] ? __device_attach+0x53/0x60
[  666.372951]  [<ffffffff813cecb0>] ? __driver_attach+0xb0/0xb0
[  666.372953]  [<ffffffff813cd6bc>] ? bus_for_each_drv+0x5c/0x90
[  666.372955]  [<ffffffff813ceb47>] ? device_attach+0xa7/0xc0
[  666.372957]  [<ffffffff813ce0ed>] ? bus_probe_device+0x2d/0x50
[  666.372959]  [<ffffffff813cc1cf>] ? device_add+0x2df/0x3e0
[  666.372962]  [<ffffffff8144eff1>] ? usb_set_configuration+0x5d1/0x6d0
[  666.372966]  [<ffffffff811d860b>] ? sysfs_addrm_finish+0x1b/0x70
[  666.372969]  [<ffffffff81458323>] ? generic_probe+0x43/0xa0
[  666.372971]  [<ffffffff81450c9f>] ? usb_probe_device+0x2f/0x60
[  666.372973]  [<ffffffff813ce948>] ? really_probe+0x68/0x190
[  666.372975]  [<ffffffff813cebd5>] ? driver_probe_device+0x45/0x70
[  666.372977]  [<ffffffff813ced03>] ? __device_attach+0x53/0x60
[  666.372979]  [<ffffffff813cecb0>] ? __driver_attach+0xb0/0xb0
[  666.372981]  [<ffffffff813cd6bc>] ? bus_for_each_drv+0x5c/0x90
[  666.372984]  [<ffffffff813ceb47>] ? device_attach+0xa7/0xc0
[  666.372986]  [<ffffffff813ce0ed>] ? bus_probe_device+0x2d/0x50
[  666.372988]  [<ffffffff813cc1cf>] ? device_add+0x2df/0x3e0
[  666.372990]  [<ffffffff81447791>] ? usb_new_device+0x101/0x140
[  666.372992]  [<ffffffff814482e8>] ? hub_port_connect_change+0x478/0x6e0
[  666.372994]  [<ffffffff81448a04>] ? hub_events+0x4b4/0x610
[  666.372997]  [<ffffffff815e7f04>] ? __schedule+0x3d4/0x700
[  666.372999]  [<ffffffff81448b95>] ? hub_thread+0x35/0x180
[  666.373003]  [<ffffffff81081d40>] ? add_wait_queue+0x60/0x60
[  666.373005]  [<ffffffff81448b60>] ? hub_events+0x610/0x610
[  666.373007]  [<ffffffff8108129c>] ? kthread+0x8c/0xa0
[  666.373010]  [<ffffffff815f38e4>] ? kernel_thread_helper+0x4/0x10
[  666.373012]  [<ffffffff81081210>] ? flush_kthread_worker+0xa0/0xa0
[  666.373014]  [<ffffffff815f38e0>] ? gs_change+0x13/0x13
[  666.373015] Code: 00 00 83 79 1c 03 b9 10 01 00 00 0f 45 c1 89 46 04 c7 02 01 00 00 00 5d c3 66 0f 1f 84 00 00 00 00 00 55 48 89 e5 66 66 66 66 90 
[  666.373031]  8b 87 98 00 00 00 5d 83 78 1c 03 0f 94 c0 c3 0f 1f 80 00 00 
[  666.373039] RIP  [<ffffffffa0e8ce39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[  666.373050]  RSP <ffff8801281e3358>
[  666.373051] CR2: 00000000ffffffd0
[  666.373053] ---[ end trace 541ac9b655266cc8 ]---
```
This is with:
```
$ lsusb
...
Bus 001 Device 009: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
```

---

### Post by riko540 on 2011-12-04
Yeah I am having trouble getting it to work for the 64bit version too.  I can't get the driver to install I keep getting this error:

> josh@josh-AY138AA-ABA-CQ5320Y:~/bcmwlhigh6$ sudo ndiswrapper -i bcmwlhigh6.inf
[sudo] password for josh: 
installing bcmwlhigh6 ...
couldn't find "bcmwlhigh664.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incompleteI apperently need the bcmwlhigh664.sys file.  The sys. file that I got from here is  bcmwlhigh6.sys and I have tried renaming it to get rid of the error but the adapter still doesn't work.

Oh and btw I get the same error with the bcmwlhigh5.inf file

---

### Post by parsim on 2011-12-11
> **SenLin said:**
> I was about to follow your instructions for modding ndiswrapper (1.56), but decided first to try compiling the latest "beta" (ndiswrapper-1.57rc1) without any changes...and...VOILA! It worked!

Well, ndiswrapper 1.57rc1 certainly has the patched ntoskernel_io.c. So this should indeed now work on 32-bit without any need for custom modification.

However, I'm getting nothing on my 32-bit system either.

```
$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.35-30-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.57rc1
vermagic:       2.6.35-30-generic SMP mod_unload modversions 686 
$ ndiswrapper -l
bcmwlhigh5 : driver installed
$ lsusb
Bus 002 Device 003: ID 0fe9:9010 DVICO 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
No errors, but the module isn't picking up the device.

---

### Post by parsim on 2011-12-11
Whoa! I take it back. One 'sudo rmmod ndiswrapper; sudo modprobe ndiswrapper' later, and I have a 'wlan2'.

---

### Post by Dennuzzz on 2011-12-18
> **parsim said:**
> Whoa! I take it back. One 'sudo rmmod ndiswrapper; sudo modprobe ndiswrapper' later, and I have a 'wlan2'.
Does the connection work with encryption and do you use bcwlhigh5 of 6?

---

### Post by parsim on 2011-12-18
> **Dennuzzz said:**
> Does the connection work with encryption and do you use bcwlhigh5 of 6?

It does **not** work with encryption, sadly, although I haven't investigated much yet. This is using bcwlhigh5.inf on a 32-bit machine.

---

### Post by ferhatelmas on 2012-01-16
Hi, yesterday I bought this usb adapter and got it worked with your posts in this thread and wrote my experience at [Netgear_WNA3100 page of ndiswrapper wiki.]("https://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100") I hope it helps.

Btw, while writing this, I saw your comment, parsim but bcmwlhigh5 works under 64 bit Lucid with WPA2.

---

### Post by Green_Bean on 2012-01-21
This works for me, thank you so much, I haven't been able to get this to work since I upgraded to Ubuntu 11.10. Yay Yay the crowd goes wild!

---

### Post by Green_Bean on 2012-01-21
> **SenLin said:**
> I know this is getting to be an old thread, but for the sake of others who are still searching and stumbling through here, I wanted to quickly tell what worked for me.

Thanks, guys, for all your work...I was about to follow your instructions for modding ndiswrapper (1.56), but decided first to try compiling the latest "beta" (ndiswrapper-1.57rc1) without any changes...and...VOILA! It worked!

So, for those still searching:
[LIST=1]
[*]Grab the latest (at least 1.57) source code at [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)
[*]extract, 'cd' into the folder, 'make uninstall', 'make', 'make install, (as per the simple instructions in the extracted INSTALL file ;o)
[*]Use your shiny NEW ndiswrapper to install your .inf driver:
```
sudo ndiswrapper -i /LOCATION/OF/bcmwlhigh5.inf
```
[/LIST]

Hopefully, it won't be long till this works its way into all of our systems anyway! 

This works for me, thank you so much, I haven't been able to get this to  work since I upgraded to Ubuntu 11.10. Yay Yay the crowd goes wild!

---

### Post by soft0613 on 2012-01-23
> **Green_Bean said:**
> This works for me, thank you so much, I haven't been able to get this to  work since I upgraded to Ubuntu 11.10. Yay Yay the crowd goes wild!

Could you tell me what version of Ubuntu you are running? I just set up a 11.10 64 bits and I can't get the wireless adapter to work...

---

### Post by zmanfarlee on 2012-01-29
[http://askubuntu.com/questions/48563/could-anyone-help-me-get-my-netgear-wna3100-broadcom-bcm43231-wireless-adapter](http://askubuntu.com/questions/48563/could-anyone-help-me-get-my-netgear-wna3100-broadcom-bcm43231-wireless-adapter)

ZOMG SIMPLE SOLUTION WITH NO LINE CODE!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Also use 
bcmwlhigh5.inf
bcmwlhigh5.sys

Dont know if it matters but the following was in the file also:

0846:9020.F.conf

I am using Pinguy OS and have the WNA3100 USB adapter working.  It's how I'm posting now!

---

### Post by MerKzRx on 2012-02-22
^that didn't work for me. I'm getting nowhere with this and this is the deal breaker for me for linux. 
why can't things just work lol.

---

### Post by seifertd on 2012-02-27
Adding my experiences with the WNA3100(v2) adapter.  First, my hardware is 64-bit.  I have dual boot Windows 7 and Ubuntu 11.10 system.  I have installed the Netgear drivers in the Windows 7 system and the driver files I get are in C:\Program Files (x86)\NETGEAR\WNDA3100v2\Driver\WIN764\

bcmwlhigh6.inf
bcmwlhigh6.sys
bcmwlhigh664.sys

I copied those to /usr/local/share/ndiswrapper_drivers (a directory I created myself) on the Ubuntu system.  I also compiled stock ndiswrapper-1.57 from source and installed it (make && make install -- the usual as root install).

I can then use ndiswrapper to install the driver (again, all this as root):

  cd /usr/local/share/ndiswrapper_drivers
  ndiswrapper -i bcmwlhigh6.inf
  ndiswrapper -l
bcmwlhigh6 : driver installed
	device (0846:9011) present
  modprobe ndiswrapper

This results in the following dmesg output (truncated):

[ 9525.439534] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[ 9525.596052] usb 1-8: reset high speed USB device number 4 using ehci_hcd
[ 9525.730007] usb 1-8: device firmware changed
[ 9525.730021] ndiswrapper (wrap_pnp_start_usb_device:647): reset failed: -19
[ 9525.730056] usb 1-8: USB disconnect, device number 4
[ 9525.735458] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 9525.735469] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 9525.735476] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 9525.735487] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[ 9525.735494] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[ 9525.735501] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 9525.735508] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 9525.735515] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'

So version 6 of these drivers do not work with ndiswrapper (assuming the 6 in bcmlhigh6.inf refers to some kind of version number). I found version 5 of the drivers on a thread somewhere (ndis_bcmwl.zip):

bcmwlhigh5.inf
bcmwlhigh5.sys
bcmwlhigh564.sys

Redoing all the ndiswrapper config results in a working wireless adapter that "works" with WPA2.  I put works in quotes because if you stress it (for example, upgrade a stock 11.10 using Update Manager, downloading 100's of megabytes of files), it will stop working and any attempt to reset it (by doing a rmmod ndiswrapper; modprobe ndiswrapper) results in a kernel panic.  The only recovery once it wedges is a reboot.

Not ideal, but ok ...

-Doug

---

### Post by marios85 on 2012-04-27
Hi guys,

I've just installed Ububtu 12.04 x64 (i'm brand new to this operating system and had to swim in the deep waters from the beginning) and had the same problem as you (but now i'm writing from the ubuntu platform :-))!!

But i managed to come along with it by googling almost 3 hours!!

Just to know i'm also running windows 7 x64 on the same machine but i don't think that matters.

The solution comes from a linux mint Forum!!Following this link [http://forums.linuxmint.com/viewtopic.php?f=42&t=97610]("http://forums.linuxmint.com/viewtopic.php?f=42&t=97610") will guide you to the specific subject. At the bottom you will see  a download link.[http://outpox.free.fr/Downloads/Netgear ... int.tar.gz]("http://outpox.free.fr/Downloads/Netgear ... int.tar.gz").
After downloading, you will find in the folder a HowTo.txt file. Follow the instructions carefully.!!
When done there is one more thing to do:

You have to go to your router's settings and deactivate the authentication type or the security mode that you have. Unfortunatelly, you have to leave the access tottaly free. However you can use MAC Address filtering in your router and thus you 'll be able to control the access in the network.
Save your changes and enjoy!!

P.S My router settings were: wpa2-psk authentication type and TKIP/AES encryption for the wireless password. Having these settings, the adapter was able to "see" my home network but when i tried to enter the password it just wouldn't do anything prompting the window for setting the wireless password over and over again. I did different combinations of router settings but only with the totally free access got it work!!!

I hope this was helpfull!!

Greetings from Greece!!!!!!!!!

---

