---
title: "[SOLVED] Help needed...  Can't update Linux Driver for Hauppauge PVR-150"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by armin00as on 2007-08-05
Since I'm a newb, I've been reading up a lot on installing tarballs to update my drivers, and I finally got the procedure down... - or so I thought.

After downloading the latest Linux driver from [http://ivtvdriver.org/index.php/Main_Page](http://ivtvdriver.org/index.php/Main_Page), and tried to install the tarball. [[http://dl.ivtvdriver.org/ivtv/archive/1.0.x/ivtv-1.0.1.tar.gz]](http://dl.ivtvdriver.org/ivtv/archive/1.0.x/ivtv-1.0.1.tar.gz])

After messing around with this for almost 4 hours now (I guess you have to be a frickin' programmer to understand UNIX/Linux..) I am frustrated as hell and would very much appreciate some Forum Help, please

Here's what I did:
1.) **extracted** the tarball to my /home/user folder using **tar zxf file.tar.gz**
2.) **cd**'ed to the directory where I extracted the file to
3.) skipped **./configure** as it doesn't apply for this file (only got errors)
4.) opened the .txt help file and find instructions that you have to use **make -C driver** to 'make' it (whatever that means...).

When I tried that, I get a bunch of errors... I have no clue what to make of it:

```

armin@E6400-UBUNTU:~/PVR-150/ivtv-1.0.1$ make -C driver
make: Entering directory `/home/armin/PVR-150/ivtv-1.0.1/driver'
make -C /lib/modules/2.6.20-16-generic/build M=/home/armin/PVR-150/ivtv-1.0.1/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/armin/PVR-150/ivtv-1.0.1/driver/ivtv-fb.o
In file included from /home/armin/PVR-150/ivtv-1.0.1/driver/ivtv-fb.c:59:
/home/armin/PVR-150/ivtv-1.0.1/driver/ivtv-driver.h:755: error: array type has incomplete element type
make[2]: *** [/home/armin/PVR-150/ivtv-1.0.1/driver/ivtv-fb.o] Error 1
make[1]: *** [_module_/home/armin/PVR-150/ivtv-1.0.1/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2
make: Leaving directory `/home/armin/PVR-150/ivtv-1.0.1/driver'

```

Anyone got an idea what this actually means?
 
I'm so frustrated with Ubuntu Linux right now, I feel like working with XP has been a walk in the park (sad, isn't it). Would hate to give up on Ubuntu though, as I really liked Feisty a lot - until now. 
FYI: What I eventually want is to get from this is to have **MythTV** installed (...big surprise). Unfortunately, I don't seem to be able to see a picture (-> Black Screen) and can't capture a test mpg either (using 'cat /dev/video0 > test.mpg'). Hence, I figured my drivers for the Hauppauge card may not be working with Linux.

If anyone has any ideas, please let me know! Maybe I don't even need the drivers - but I don't know that for sure? Here's the 'dmesg' output on the subject - maybe you can tell?

```

armin@E6400-UBUNTU:~$ dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac
[   14.703115] ivtv:  ==================== START INIT IVTV ====================
[   14.703118] ivtv:  version 0.10.1 (tagged release) loading
[   14.703119] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   14.703120] ivtv:  In case of problems please include the debug info between
[   14.703121] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   14.703122] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   14.703166] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   14.703735] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 21
[   14.703741] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   15.377546] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   15.405802] NET: Registered protocol family 17
[   15.595128] ivtv0: Encoder revision: 0x02050032
[   15.595130] ivtv0: Recommended firmware version is 0x02060039.
[   15.660189] tveeprom 0-0050: Hauppauge model 26552, rev F1A3, serial# 9933251
[   15.660191] tveeprom 0-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[   15.660192] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   15.660193] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   15.660194] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   15.660196] tveeprom 0-0050: has radio, has no IR receiver, has no IR transmitter
[   15.660197] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   15.680178] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   15.680196] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   15.684692] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   15.712416] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   15.816542] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   20.717163] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   20.843858] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   20.911541] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   20.911628] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   20.911734] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   20.911775] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   20.911888] ivtv0: Registered device radio0 for encoder radio
[   20.911898] tuner 0-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   21.315833] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   21.315842] ivtv:  ====================  END INIT IVTV  ====================

```

Just in case you're wondering: YES, I've read tons of posts and websites before posting here, but I don't seem to be able to get it done without help from someone who can walk me though...
**-- Thanks.**

---

### Post by armin00as on 2007-08-05
???

---

### Post by tgm4883 on 2007-08-05
If your final destination is have mythtv installed and working with your PVR-150 on Feisty, and the PVR-150 works out of the box in mythtv and feisty, perhaps we should look elsewhere than trying to install ivtv.

So my question is, what have you done for testing your PVR-150 and MythTV?  Have you followed any MythTV guides?

---

### Post by wolfen69 on 2007-08-05
was an update necessary? if it aint broke, don't fix it. at least wait until system update recommends it.

---

### Post by armin00as on 2007-08-05
Hi... Thanks for your response!

I followed this installation guide  step by step
[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop)

..and then switched over to...
[http://mythtv.org/docs/mythtv-HOWTO-1.html](http://mythtv.org/docs/mythtv-HOWTO-1.html)
 as it seemed to be the better one.. I don't really know.

I've started reading on the 2nd How-To guide today, and I "got stuck" at checking the Hardware requirements - that's why I thought I may have to update the drivers.

What else did I do:
- I posted in the newb forum, and got some helpful advice (which solved a few other problems);
- I made sure that Frontend/Backend are communicating;
- I made sure that the '../mythtv/recodings' folder can be accessed by mythtv -> checked the permissions;
- I tried to check if I can capture some text mpg ('cat /dev/video0 > test.mpg')... which didn't work;
- I made sure to comment out ("#") out the server address 127.0.0.1 in the mysql.txt file;
- I made sure that the information in that particular file is correct, including addresses and passwords...

...and basically everything else -and more- that's suggested by the first Community Doc installation guide on a bunch of troubleshooting websites (don't recall 'em all).

Fact is, I don't get a picture when clicking the "Live TV" button in Frontend... it's just black for 20 sec and then the menu comes up again.
Well... What can I do next? :confused:

Very much appreciate your suggestions, tgm4883....(and whoever else may be able to help :) )

SYSTEM Details... just in case it's of help:
**Custom Full-Tower with Windoze XP SP2 & Ubuntu Feisty x86 (2.6.20-16 generic) in Dual-Boot (on separate HDDs), Intel E6400 Proc OC'ed to 3.2GHz, NVIDIA 8800GTS (with 100.14.11 driver), 2 GB DDR2-800, Hauppauge PVR-150 w/ MPEG-2 Dec, M Audio Revolution-7.1**

---

### Post by tgm4883 on 2007-08-05
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV) is the better guide

How far did you make it in this guide

---

### Post by armin00as on 2007-08-05
That's the guide I used... and I made it all the way through.

However, and after clicking the link again now, I realized that I started right away with the [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)  guide.

Maybe, I should have used... [https://help.ubuntu.com/community/MythTV_Feisty_Frontend_Desktop_O](https://help.ubuntu.com/community/MythTV_Feisty_Frontend_Desktop_O)  instead??


??? :confused: :confused: :confused:

---

### Post by tgm4883 on 2007-08-05
What kind of system do you want?  Frontend backend desktop?  Frontend only?  Etc?

---

### Post by armin00as on 2007-08-05
I think I want the Frontend/Backend [Desktop?] combination. Seems to be the most common one... right? I don't need any remote access or multiple Backends (yet)...

---

### Post by tgm4883 on 2007-08-05
do you want to use it as a regular desktop too?

---

### Post by armin00as on 2007-08-05
If that means sitting in front of it (for TV) and schedule recordings (by making the necessary entries on Desktop level directly, for starters..)... then the answer is - YES!

Just browsed through the Backend/Frontend Desktop Guide: I've been taking care of all the suggestions inside already before, and I've checked multiple times after that. 
I don't think it's something with the BE/FE setup. I can't help it, but it must be something else. For example: why can't I capture an mpg test file?? [check this out, pls:  [http://ubuntuforums.org/showthread.php?t=518337](http://ubuntuforums.org/showthread.php?t=518337) ]... Any ideas?

Or: do I have to install my NVIDIA drivers again..?

---

### Post by tgm4883 on 2007-08-06
> **armin00as said:**
> If that means sitting in front of it (for TV) and schedule recordings (by making the necessary entries on Desktop level directly, for starters..)... then the answer is - YES!

Just browsed through the Backend/Frontend Desktop Guide: I've been taking care of all the suggestions inside already before, and I've checked multiple times after that. 
I don't think it's something with the BE/FE setup. I can't help it, but it must be something else. For example: why can't I capture an mpg test file?? [check this out, pls:  [http://ubuntuforums.org/showthread.php?t=518337](http://ubuntuforums.org/showthread.php?t=518337) ]... Any ideas?

Or: do I have to install my NVIDIA drivers again..?

Do you have more than one computer?

If so, you could schedule recording via the other computer or by using a remote.

If scheduling recording is the only reason you want a desktop environment there are other options.

Now let me look at your other problem.

---

### Post by tgm4883 on 2007-08-06
also try these
cat /dev/video1 > test.mpg
cat /dev/video2 > test.mpg

---

### Post by armin00as on 2007-08-06
Here's what I get on the cat /dev/video'x' test:

> armin@E6400-UBUNTU:~$ cat /dev/video1 > test.mpg
cat: /dev/video1: No such file or directory

armin@E6400-UBUNTU:~$ cat /dev/video2 > test.mpg
cat: /dev/video2: No such file or directory


armin@E6400-UBUNTU:~$ cat /dev/video0 > test.mpg
-- This one runs w/o error.... 
HOWEVER, that particular output file (test.mpg) is not an .mpg; it's just a 'plain text document'...

Message:
> **Cannot open test.mpg**.  The filename "test.mpg" indicates that this file is of type "MPEG video". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

I believe I have the needed .mpg drivers installed - so why is it not capturing .mpg correctly? Any ideas? 
In the meantime, I searched my HD for other .mpg and found a couple of files which must stem from the Ubuntu installation (..showing Tux in front of some sort of menu :) 
Guess what... - those run OK !   :confused: :confused:

EDIT: Interestingly enough, the 'video0' test.mpg file was stored in my '/home/armin' directory - and not in my '/var/lib/mythtv/recordings' folder, as it's supposed to be for recordings... (I guess?).

---

### Post by armin00as on 2007-08-06
Just found something else -rather strange(?)- when trying some commands given in the [http://www.mythtv.org.wiki](http://www.mythtv.org.wiki) documentation :

When starting my backend via Terminal, I got his output:

```

armin@E6400-UBUNTU:~$ sudo /usr/bin/mythbackend
Password: ******
2007-08-06 00:00:34.482 Using runtime prefix = /usr
2007-08-06 00:00:34.499 New DB connection, total: 1
2007-08-06 00:00:34.501 Connected to database 'mythconverg' at host: localhost
2007-08-06 00:00:34.502 [B]Current Schema Version: 1160
Running as a slave backend.[/B]
2007-08-06 00:00:34.504 New DB connection, total: 2
2007-08-06 00:00:34.504 Connected to database 'mythconverg' at host: localhost
2007-08-06 00:00:34.504 EITHelper: localtime offset -5:00:00 
2007-08-06 00:00:34.506 New DB connection, total: 3
2007-08-06 00:00:34.506 Connected to database 'mythconverg' at host: localhost
2007-08-06 00:00:34.697 [B]Main::Starting HttpServer
QServerSocket: failed to bind or listen to the socket[/B]
2007-08-06 00:00:34.698 Main::HttpServer Create Error
2007-08-06 00:00:34.698 Main::Registering HttpStatus Extension
2007-08-06 00:00:34.698 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-08-06 00:00:34.698 Enabled verbose msgs:  important general
2007-08-06 00:00:34.698 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2007-08-06 00:00:34.698 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
**QServerSocket: failed to bind or listen to the socket**
2007-08-06 00:00:34.699 Failed to bind port 6543. Exiting.

```

A few things struck me right away.. as marked above.
1.) " running as as slave backend" --> that OK??
2.) "Main::Starting HttpServer QServerSocket: failed to bind or listen to the socket"
3.) "2007-08-06 00:00:34.698 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
QServerSocket: failed to bind or listen to the socket
2007-08-06 00:00:34.699 Failed to bind port 6543."   

 :confused: :confused:

---

### Post by tgm4883 on 2007-08-06
> **armin00as said:**
> Just found something else -rather strange(?)- when trying some commands given in the [http://www.mythtv.org.wiki](http://www.mythtv.org.wiki) documentation :

When starting my backend via Terminal, I got his output:

```

armin@E6400-UBUNTU:~$ sudo /usr/bin/mythbackend
Password: ******
2007-08-06 00:00:34.482 Using runtime prefix = /usr
2007-08-06 00:00:34.499 New DB connection, total: 1
2007-08-06 00:00:34.501 Connected to database 'mythconverg' at host: localhost
2007-08-06 00:00:34.502 [B]Current Schema Version: 1160
Running as a slave backend.[/B]
2007-08-06 00:00:34.504 New DB connection, total: 2
2007-08-06 00:00:34.504 Connected to database 'mythconverg' at host: localhost
2007-08-06 00:00:34.504 EITHelper: localtime offset -5:00:00 
2007-08-06 00:00:34.506 New DB connection, total: 3
2007-08-06 00:00:34.506 Connected to database 'mythconverg' at host: localhost
2007-08-06 00:00:34.697 [B]Main::Starting HttpServer
QServerSocket: failed to bind or listen to the socket[/B]
2007-08-06 00:00:34.698 Main::HttpServer Create Error
2007-08-06 00:00:34.698 Main::Registering HttpStatus Extension
2007-08-06 00:00:34.698 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-08-06 00:00:34.698 Enabled verbose msgs:  important general
2007-08-06 00:00:34.698 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2007-08-06 00:00:34.698 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
**QServerSocket: failed to bind or listen to the socket**
2007-08-06 00:00:34.699 Failed to bind port 6543. Exiting.

```

A few things struck me right away.. as marked above.
1.) " running as as slave backend" --> that OK??
2.) "Main::Starting HttpServer QServerSocket: failed to bind or listen to the socket"
3.) "2007-08-06 00:00:34.698 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
QServerSocket: failed to bind or listen to the socket
2007-08-06 00:00:34.699 Failed to bind port 6543."   

 :confused: :confused:

Well thats all related to mythtv.  If you can't capture any video with your card lets not worry about mythtv yet.

First, lets make sure mythtv isn't conflicting with our test.  Turn off the backend 
sudo /etc/init.d/mythtv-backend stop

then lets make sure the tuner is on a valid channel.  Change it to a known working channel with 

ivtv-ctl -C number

now lets try recording some video again with
cat /dev/video0 > test.mpg


The reason this file is in your home directory and not the mythtv directory is because your not using mythtv to record it.

---

### Post by tgm4883 on 2007-08-06
also can you post the output of 

lspci -vv

---

### Post by armin00as on 2007-08-06
Hi tgm4883 -

Seems like we're getting closer...

Output of ivtv-ctl -C [number]:
> armin@E6400-UBUNTU:~$ ivtv-ctl -C 5
bash: **ivtv-ctl: command not found**

Note: doesn't work with other numbers (e.g. 12) either, even though I know that Fox is on 12 around here...


The next one, output of **lspci -vv**:

```
armin@E6400-UBUNTU:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5000
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: e8000000-ebffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 4: I/O ports at d000 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 18
        Region 4: I/O ports at c000 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5006
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 20
        Region 0: Memory at ee200000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: ee100000-ee1fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: ec000000-edffffff
        Prefetchable memory behind bridge: 0000000080000000-00000000800fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 19
        Region 4: I/O ports at c400 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 17
        Region 4: I/O ports at c800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 20
        Region 4: I/O ports at cc00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5006
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at ee201000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: ee000000-ee0fffff
        Prefetchable memory behind bridge: 00000000e4000000-00000000e7ffffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5001
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology Unknown device b002
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 17
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at f000 [size=16]
        Region 5: I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device 5001
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 3
        Region 0: Memory at ee202000 (32-bit, non-prefetchable) [size=256]
        Region 4: I/O ports at 0500 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Unknown device b002
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 17
        Region 0: I/O ports at d800 [size=8]
        Region 1: I/O ports at dc00 [size=4]
        Region 2: I/O ports at e000 [size=8]
        Region 3: I/O ports at e400 [size=4]
        Region 4: I/O ports at e800 [size=16]
        Region 5: I/O ports at ec00 [size=16]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp. Unknown device c815
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at ea000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at e8000000 (64-bit, non-prefetchable) [size=32M]
        Region 5: I/O ports at 7000 [size=128]
        [virtual] Expansion ROM at eb000000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Giga-byte Technology Unknown device b000
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 17
        Region 5: Memory at ee100000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Unknown device b000
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 16
        Region 0: I/O ports at 8000 [size=8]
        Region 1: I/O ports at 8400 [size=4]
        Region 2: I/O ports at 8800 [size=8]
        Region 3: I/O ports at 8c00 [size=4]
        Region 4: I/O ports at 9000 [size=16]
        Capabilities: <access denied>

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
        Subsystem: Giga-byte Technology Marvell 88E8053 Gigabit Ethernet Controller (Gigabyte)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at ed000000 (64-bit, non-prefetchable) [size=16K]
        Region 2: I/O ports at a000 [size=256]
        [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
        Capabilities: <access denied>

05:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR 150
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (32000ns min, 2000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

05:01.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
        Subsystem: VIA Technologies Inc. M-Audio Revolution 7.1
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 17
        Region 0: I/O ports at b000 [size=32]
        Region 1: I/O ports at b400 [size=128]
        Capabilities: <access denied>

05:02.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: NEC Corporation Hama USB 2.0 CardBus
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (250ns min, 10500ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at ee000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

05:02.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: NEC Corporation Hama USB 2.0 CardBus
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (250ns min, 10500ns max), Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 16
        Region 0: Memory at ee001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

05:02.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20 [EHCI])
        Subsystem: HaSoTec GmbH Unknown device 2928
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (4000ns min, 8500ns max), Cache Line Size: 32 bytes
        Interrupt: pin C routed to IRQ 21
        Region 0: Memory at ee002000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
```

... ??? ...

My rig runs nicely under XP - including capturing Live TV (using BeyondTV).

Anyways, 
many thanks for your help tgm4883, just in case I haven't mentioned that yet.. :)

(Gotta go to work now...)

---

### Post by armin00as on 2007-08-06
Just checked in Synaptic:

I have "**ivtv utils**" and "**libvideo-ivtv-perl**" installed... *but not* **ivtv-source**..

Is that it? Where did I miss that in the installation guide??
I'll install now and give it another try.

---

### Post by armin00as on 2007-08-06
Well... I installed **ivtv-source** via Synaptic, and I hate to say it: nothing has changed.
I also tried to capture some TV again using 'cat', but the results are the same as before. No .mpg file...

---

### Post by tgm4883 on 2007-08-06
My bad, just looked it up and I gave you the wrong command.  Run these command instead

sudo /etc/init.d/mythtv-backend stop

ivtv-tune -tus-cable -c12 -d/dev/video0

cat /dev/video0 > test.mpg

---

### Post by armin00as on 2007-08-06
No problem.. thanks for correcting!

I'll head home around lunchtime and will give it a try then.
- THANKS!

---

### Post by armin00as on 2007-08-06
OK, here we go:

> armin@E6400-UBUNTU:~$ sudo /etc/init.d/mythtv-backend stop
Password: *****
Stopping MythTV server: mythbackend .

..and..

> armin@E6400-UBUNTU:~$ ivtv-tune -tus-cable -c12 -d/dev/video0
/dev/video0: 205.250 MHz  (Signal Detected)


I guess it's not a lack of signal... What else could it be? 

- Thanks!!

---

### Post by tgm4883 on 2007-08-06
> **armin00as said:**
> OK, here we go:



..and..



I guess it's not a lack of signal... What else could it be? 

- Thanks!!

Did you try recording the channel after doing that?

cat /dev/video0 > test.mpg

BTW, leave the backend stopped

---

### Post by armin00as on 2007-08-06
Yep... same thing... :(

:confused::confused::confused:


Thanks for trying... I gotta get back to work now, sorry.
I'll keep trying to find other hints on other website - maybe I get lucky. Your input, however, is still much, much appreciated!!! You seem to have a good idea of what to check and to look for... I'm sure we'll get to it soon, and then I may be able to return the favor to someone else next time. Seems to me like this problem is not that uncommon - however, I couldn't find anyone actually posting a working solution for it...

THANKS!!

---

### Post by tgm4883 on 2007-08-06
can you list 

 ls /dev/video*

---

### Post by armin00as on 2007-08-06
> can you list

ls /dev/video*

OK, here you are, tgm4883:

```
armin@E6400-UBUNTU:~$ ls /dev/video*
/dev/video0  /dev/video24  /dev/video32

```

...OK?

---

### Post by armin00as on 2007-08-07
-- THAT'S IT, I'M THROWING IN THE TOWEL...!! :mad:

---

