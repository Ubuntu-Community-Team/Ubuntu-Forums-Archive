---
title: "Wine WoW Wrath of the Lich king with ATI open source graphic driver"
date: 2010-02-18
forum: Multimedia Software
---

### Post by Shadyboy on 2010-02-18
Just wondering if this is possible?
Total n00b with linux, this is my *thinking* 3rd week using Ubuntu 9.10

And I am using my system for surfing the web, listen to music, video`s and chatting.
And I got the "funny" tough`t of trying to maybe play World of Warcraft again on this computer. Yes I have run it before when I had XP and W7 on it.
The w7 experience on this computer was a bad mistake.

So yeah, the thing I am really wondering on is this:
Wine, WoW with WoTLK ( Wrath of the Lich King ), with the newest Open Source ATI graphic driver?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421")
According to that page (you have to Ctrl-F and "Open source ATI drivers" to find the what I mean ) it is possible, but I am wondering on how to do it?

Pastebin of my lspci:
[http://pastebin.com/f1a75c08c](http://pastebin.com/f1a75c08c)

and been reading on different sites that you can play games with wine in a new X. Curious on how that can be done, and if that MAYBE is the best thing to do with my Wow game...
Havent installed it YET, thinking of downloading the web installer after this post.

------------------------------------------------------------------------------------

If the moderators should find this is the wrong place for this to be asked, please move it to the "Wine" section, if its better placed there....

---

### Post by dajames4 on 2010-02-18
Hopefully this is useful.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Shadyboy on 2010-02-19
So now I have the game downloaded and installed, but my graphics are BAD >.<

The attachment shows how my "login screen" for wow is looking.
Now I have finaly mannaged to "log in" on my account, ( even tough its not active yet, just for the updater to start downloading ) beacuse the shortcut on the Desktop won't work. It just closes when I press the Play button, and I get a gray screen when I try to go into the "settings" from the Launcher

And also I have managed to "not" own the World of Warcraft folder.
I have to each time trying to run wow, go to the ./wine/ folder and setting persmission to the World of Warcraft folder. But each time after I have exited wine running wow, I have to do it again. Its like the permissions for that folder just vanishes. Any clues?

---

### Post by lacktorium on 2010-02-19
its a glitch with the launcher program. 
it can some times be fixed by running the launcher and while its still on edit the file permissions.
or you can simply change the file permissions back and run wow.exe directly

---

### Post by Shadyboy on 2010-02-21
well I figured it out that it was just best to run the wow.exe file, and not the launcher.exe file.
But am still wondering on the graphics. If I can do something about it?

I have read on the web that I need to change something in my config.wtf file, but since I have just installed it, I have no config.wtf file :(
Am updating the game now, beacuse I have read that the config.wtf is made after you log in and selects at character.

---

### Post by Shadowkath on 2010-05-30
cris@flavour-ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
09:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

-----------------------------------------

my details - 

When I load up WoW - I get a serious issue with the graphics. I can't seem to figure it out. Anything I do, doesn't seem to figure it out, or fix it.

----------------------------------------

Here is a screenshot of what I'm seeing.
[IMG]http://www.kath.us/images/Screenshot.png[/IMG]

---

### Post by Whiterin on 2010-07-04
It's happening because it's opening the game in DirectX instead of OpenGL.

Find the file wtf/Config.wtf in your main WoW directory. By default it is found in /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/, where <username> is you computer login name. Note that since .wine begins with a period, you will not be able to see it, but you may still access it in a terminal. In the Nautilus file manager, you can press Ctrl + h to see hidden files. If config.wtf does not exist, run the game and log into a character, then exit WoW. The game should then have created the file. Open it using a text editor, and add the following line to it:

SET gxApi "opengl"

---

### Post by daz1uk on 2010-07-18
Hi, 

I'm having real issues with the graphics on wotlk, I have tried adding SET gxApi "opengl" to my config.wtf but this just causes the game to crash and generate an error report. Does anyone know how to get this game to work?

Intel Core 2
X1250 ATI Graphics On-board

---

