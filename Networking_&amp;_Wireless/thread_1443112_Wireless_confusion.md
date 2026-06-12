---
title: "Wireless confusion"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by Tomween1 on 2010-03-30
OK I have installed and un-installed 3 different versions of Ubuntu. My forth is a re-install of v9.10. During all these installs I have had difficulty getting my wifi to work.
 
During my last install I left the ISO in the drive by mistake so when the system rebooted it loaded from the disc in demo.... This was interesting because in the demo the program manager showed 2 drives for wireless, 1 Broadcom STA and 2 Broadcom b43xx. I tried loading the STA AND IT WORKED! (sorry it could have been the b43xx, for the time being it's insignificant) Upon my excitement I restarted the computer and removed the disk went to my Ubuntu set up and ...what the Broadcom choices weren't there:confused: Why?
 
Now I am running Win 7 Home 32bit on my main drive and have Ubuntu loaded on its own drive. I have a Netgear WN311b wireless N card installed. Again my confusion is why it worked in demo (off the cd) but doesn't from full install.
 
I read on the web to try inserting my supplied disc from Netgear and then search program manager. It now showed the two for-mentioned Broadcom programs, but this time wouldn't install them. On the b43 I got an error message and on the STA it searched extracting and loading this continued for a 1/2 hour with no progression. I couldn't close the PM or the extracting and loading box, so I had to restart the computer.
 
I still don't have wireless and after three weeks of trying I'm about ready to throw in the towel:frown:
 
Any assistance would be appreciated,
 
Tom

---

### Post by 2hot6ft2 on 2010-03-30
Instead of reinstalling again try fixing it.
Connect to a wired connection so you can get drivers and updates.
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get update
```
Then go to
System > Administration > Hardware Drivers
and see if there's a driver available

Since you mentioned Broadcom STA and Broadcom b43xx you may find your solution here:
[The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

If all that fails then
Open a terminal
Applications > Accessories > Terminal
and run

If internal PCI
```
lspci
```
That's LSPCI in lower case, and post the results.

If it's a USB adapter
```
lsusb
```
That's LSUSB in lower case, and post the results.

---

### Post by Tomween1 on 2010-03-31
Your steps are appreciated, however, my dilemma is a wired connection. 1 I'm handicapped, 2 my system is on ground floor and all inter-net connections are on third floor. I haven't the ability to move computer to this level. Do I have the ability to download drivers to accomplish what you've suggested?
 
I am still confused as to why I was able to get the Demo to hook to the net but can't do the same w/ full version. Can the drivers that make the Demo work, be transferred from Demo to full, on the ISO disc?
 
Thank you, Tom

---

### Post by bkratz on 2010-03-31
> **Tomween1 said:**
> Your steps are appreciated, however, my dilemma is a wired connection. 1 I'm handicapped, 2 my system is on ground floor and all inter-net connections are on third floor. I haven't the ability to move computer to this level. Do I have the ability to download drivers to accomplish what you've suggested?
 
I am still confused as to why I was able to get the Demo to hook to the net but can't do the same w/ full version. Can the drivers that make the Demo work, be transferred from Demo to full, on the ISO disc?
 
Thank you, Tom

The link provided previously tells you how to install those drivers without wired access  directly from the Live CD.

Here is the link again

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Tomween1 on 2010-03-31
My greatest apologies, I will try these steps.

---

### Post by bkratz on 2010-03-31
> **Tomween1 said:**
> My greatest apologies, I will try these steps.

Believe me there is nothing to apologize about! Good Luck, hopefully we will soon hear good news.

---

### Post by Tomween1 on 2010-03-31
Unfortunately no luck. The steps given, I had already tried, I know, I know your response to this... I re installed Ubuntu. I did this because the previous time I tried this step, I had tried installing both b43 and STA both not working and wouldn't let me uninstall. So I re loaded 9.10. I tried the steps again, this time when it came time to search the cd it asked me to install cd in cd drive.... It was already there and showing on on the desktop. I let it search for 20 min or so and nothing happened. When I canceled out, of course I got the error of non installation.
 
So here is the info requested
 
[FONT=Times New Roman][SIZE=2]familypc@ubuntu:~$ lspci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:01.0 ISA bridge: nVidia Corporation nForce 750a LPC Bridge (rev a2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]01:06.0 Network controller: Broadcom Corporation BCM43XG (rev 01)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]03:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]03:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]04:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GTX] (rev a2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]07:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]07:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]08:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]09:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]familypc@ubuntu:~$ [/SIZE][/FONT]

---

### Post by bkratz on 2010-03-31
Not really sure if it will be of any help, but

[http://www.backports.ubuntuforums.org/showthread.php?t=1347545](http://www.backports.ubuntuforums.org/showthread.php?t=1347545)

they kept saying they got it working here.  Still googling.

---

### Post by Tomween1 on 2010-03-31
Well it looks like I have a tough road ahead of me:mad:. I'm still curious as to why the demo found and offered the correct drivers to make the inter net work! It makes no sense that the demo works but the full does not! Any thoughts as to why this happens?

---

### Post by bkratz on 2010-03-31
> **Tomween1 said:**
> Well it looks like I have a tough road ahead of me:mad:. I'm still curious as to why the demo found and offered the correct drivers to make the inter net work! It makes no sense that the demo works but the full does not! Any thoughts as to why this happens?

From what I understand ( and I am often wrong!) the driver is made available, but is actually proprietary and can't be directly included. ( I'm sure i will be corrected soon! ) Anyway, further searching seems to indicate that the correct driver was the STA version. It is available here

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

read the readme first. It is well explained, but may be more that you want to try.
Anyway, how about going to the terminal Applications>>Accessories>>Terminal and copy/paste the outputs of the following back here.

```
sudo lshw -C network
sudo iwlist scan
iwconfig
lsmod
```

Those a lowercase L not 1's.  Please post these with the use of the code tags (#) for readability.


Forgot you don't have ethernet, however you are communicating you can simply use a usb key and do something like this

You can convert your terminal output to a text document easily:

sudo lshw -C network > lshw.txt

Then you will find a text document in your /home/user directory, in this case lshw.txt, which you can drag-n-drop onto a flash drive and see it in Windows with, IIRC, wordpad repeat with different names for each of those above.

---

### Post by chili555 on 2010-03-31
If we knew the pci.id, we would be able to confirm that the device works with the STA driver module, *wl*. Please let us see:```
lspci -nn | grep Network
```The STA driver is on the install CD.

---

### Post by bkratz on 2010-03-31
> **chili555 said:**
> If we knew the pci.id, we would be able to confirm that the device works with the STA driver module, *wl*. Please let us see:```
lspci -nn | grep Network
```The STA driver is on the install CD.

It is this one

01:06.0 Network controller: Broadcom Corporation BCM43XG (rev 01)

---

### Post by chili555 on 2010-03-31
If the pci.id is 14e4:4329, it works with *wl*, which can be installed from the CD.```
$ modinfo wl | grep 4329
alias:          pci:v0000[COLOR="Blue"]14E4[/COLOR]d0000[COLOR="Blue"]4329[/COLOR]sv*sd*bc*sc*i*
```

---

### Post by bkratz on 2010-03-31
> **chili555 said:**
> If the pci.id is 14e4:4329, it works with *wl*, which can be installed from the CD.```
$ modinfo wl | grep 4329
alias:          pci:v0000[COLOR="Blue"]14E4[/COLOR]d0000[COLOR="Blue"]4329[/COLOR]sv*sd*bc*sc*i*
```

Sorry to trouble you Dr. chili, but he already tried that(earlier)
Quote

Unfortunately no luck. The steps given, I had already tried, I know, I know your response to this... I re installed Ubuntu. I did this because the previous time I tried this step, I had tried installing both b43 and STA both not working and wouldn't let me uninstall. So I re loaded 9.10. I tried the steps again, this time when it came time to search the cd it asked me to install cd in cd drive.... It was already there and showing on on the desktop. I let it search for 20 min or so and nothing happened. When I canceled out, of course I got the error of non installation.


Do you know what would be the likely cause of this?


@Tomween1
Did you go to system>>Administration>>Software sources and put a check mark in install from CD?

---

### Post by Tomween1 on 2010-03-31
Well that's all good stuff, a lot to digest.
 
1st- Yes I have inter-net connection on this computer. I keep switching between Win 7 and Ubuntu. Gotta do what I gotta do!
 
2- In the forum link forwarded to me by bkratz I noticed a similar problem I too am having, The hardware download screen it shows the STA version in the box, I highlight it to apply it and the system freezes, the same thing happened to the person in the link.... There wasn't a resolve to this.
 
3- I will be back at this tomorrow and attempt to forward the info requested.
 
4- Would it be a good idea to, yet burn another ISO in case of corruption? Or let it go and continue from where we are now?
 
5- How do I get the STA drive out of the Hardware Update (I think that's what it's called) so my new attempts aren't stopped do to overlap.

---

### Post by bkratz on 2010-03-31
> **Tomween1 said:**
> Well that's all good stuff, a lot to digest.
 
1st- Yes I have inter-net connection on this computer. I keep switching between Win 7 and Ubuntu. Gotta do what I gotta do!
 
2- In the forum link forwarded to me by bkratz I noticed a similar problem I too am having, The hardware download screen it shows the STA version in the box, I highlight it to apply it and the system freezes, the same thing happened to the person in the link.... There wasn't a resolve to this.
 
3- I will be back at this tomorrow and attempt to forward the info requested.
 
4- Would it be a good idea to, yet burn another ISO in case of corruption? Or let it go and continue from where we are now?
 
5- How do I get the STA drive out of the Hardware Update (I think that's what it's called) so my new attempts aren't stopped do to overlap.

Sorry to be taking so long, but I don't think you need to burn a new disk yet. Can you answer my last question before retiring?

---

### Post by Tomween1 on 2010-03-31
@Tomween1
Did you go to system>>Administration>>Software sources and put a check mark in install from CD?[/QUOTE]
 
As a matter of fact, no I didn't! Never saw that step. Well check into that tomorrow! It would be to sweet if that were it\\:D/\\:D/

---

### Post by bkratz on 2010-03-31
> **Tomween1 said:**
> @Tomween1
Did you go to system>>Administration>>Software sources and put a check mark in install from CD?
 
As a matter of fact, no I didn't! Never saw that step. Well check into that tomorrow! It would be to sweet if that were it\\:D/\\:D/[/QUOTE]

I think that is all it is! Post with good news tomorrow.

---

### Post by Tomween1 on 2010-04-01
bkratz, after I left my message last night I thought about your question (I was extremely tired at that point) and yes I do check that box! That's one of those annoyances I have found. Even though the disc shows on the desktop, when you click on Apply (on the selected river) the system asks you to insert the cd into the cd drive! I'll be getting back to the desktop soon and I'll start going over the questions poised yesterday.

---

### Post by Tomween1 on 2010-04-01
:popcorn:
OK all went swimmingly, however I have been left with more questions. Here's the low down on my standings.
 
I reformatted the drive I had Ubuntu installed on and rebooted the computer, booting directly from the Ubuntu CD. I preformed a full install from the disc and not through Windows. This proved to be the solution. I now have all facilities, except sound, working.
 
Here's the dilemma. Now on start up of computer, I don't get a dual boot choice I get a Ubunto/Linux menu that includes 2 Window 7 choice's. I much prefer the dual boot Window priority boot.
 
Why did the system change itself like this and can I change back to the standard Dual boot set up?
 
Sorry I realize this is no longer a wireless issue, and if need be I will relocate this post.
 
Thanks, Tom

---

### Post by bkratz on 2010-04-01
> **Tomween1 said:**
> :popcorn:
OK all went swimmingly, however I have been left with more questions. Here's the low down on my standings.
 
I reformatted the drive I had Ubuntu installed on and rebooted the computer, booting directly from the Ubuntu CD. I preformed a full install from the disc and not through Windows. This proved to be the solution. I now have all facilities, except sound, working.
 
Here's the dilemma. Now on start up of computer, I don't get a dual boot choice I get a Ubunto/Linux menu that includes 2 Window 7 choice's. I much prefer the dual boot Window priority boot.
 
Why did the system change itself like this and can I change back to the standard Dual boot set up?
 
Sorry I realize this is no longer a wireless issue, and if need be I will relocate this post.
 
Thanks, Tom


Sorry you had to re-install, but it sounds like it was worth it. Anyway, I know little about the new grub, but I am curious did you also reinstall Windows? Since you reformatted it should have been gone unless you were very careful about partitioning correctly. If you did reinstall Windows, which did you install first? I know that Windows 7 is really picky about sharing any credit, not like XP, and if you did it second it probably destroyed grub.

For the sound issue I would post it in the Multimedia forum

[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

For the grub issue, you might check the installation forum

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

I just looked there and it seems a lot of people have virtually the same type of problem.

Anyway, I am glad you got your wireless issues worked out relatively painlessly and trust you will have the same luck with the other forums.


Oh, you might want to go to the thread tools and select [solved] in case it helps someone else.


Just found this in the installation forum--kinda interesting

[http://ubuntuforums.org/showthread.php?t=1444436](http://ubuntuforums.org/showthread.php?t=1444436)

---

### Post by Tomween1 on 2010-04-01
bkratz thanks for your help. I now have much bigger problems to solve. I removed Ubuntu now my Disk is haywire. Upon booting I now get GRUB loading error unknown filesystem.
 
As they say, when it rains it pours.
 
To answer your last query, I did partition the disk and it was only the partition I formatted. I had Windows up until I removed Ubuntu:-k

---

