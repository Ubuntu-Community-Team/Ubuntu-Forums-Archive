---
title: "Random Freezing of Mythbuntu"
date: 2007-12-26
forum: Mythbuntu
---

### Post by browndog289 on 2007-12-26
Hello

I have installed Mythbuntu on an old system I had lying around, the specs are:

AMD Athlon XP 1600+ Processor
768Mb DDR-RAM
20Gb IDE Hard Disk (Install Drive)
250Gb SATA Hard Disk (Media Drive)
MSI NVidia FX5200 AGP 8x
SATA PCI Controller Card
DVD+/-Rewriter
WinTV PCI Card (For Analogue)
Win TV Nova-T 500 PCI Card (For DVB)
Netgear Wireless PCI Card
Infra-Red Wireless Keyboard
TrendSonic Media Centre Case

The system installed without problems and I have been using it for a week or so, however it has started freezing up.

Normally when I go to use it I press an arrow on the Nova-T remote and the mythfrontend displays, however when it freezes nothing happens and I cannot ping the box either so a hard reset is required.

I have run a memory test using MemTest86+ and it passed, I also checked the IDE drive and that passed both the short and long tests.

Previously it froze after 8-10 hours but it has just frozen after running for over 30 hours.

After I rebooted a couple of days ago I installed sensorsd to log the temperatures and they seem normal around 53-63C. At the last freezing the CPU was at 57C so I don't think overheating is the problem.

It seems to have crashed around 18:40 today in the logs.

Here is the syslog during the last freeze (Not sure if I have the voltage calculations configured right):

--------------------------------------------------------------------------------

Dec 26 18:39:01 mythtv /USR/SBIN/CRON[18117]: (root) CMD (  [ -d /var/lib/php5 $
Dec 26 18:40:35 mythtv sensord: Chip: it87-isa-0290
Dec 26 18:40:35 mythtv sensord: Adapter: ISA adapter
Dec 26 18:40:35 mythtv sensord:   VCore 1: +1.70 V (min = +0.00 V, max = +4.08 $
Dec 26 18:40:35 mythtv sensord:   VCore 2: +2.53 V (min = +0.00 V, max = +4.08 $
Dec 26 18:40:35 mythtv sensord:   +3.3V: +2.16 V (min = +0.00 V, max = +4.08 V)
Dec 26 18:40:35 mythtv sensord:   +5V: +3.76 V (min = +0.00 V, max = +6.85 V)
Dec 26 18:40:35 mythtv sensord:   +12V: +7.23 V (min = +0.00 V, max = +16.32 V)
Dec 26 18:40:35 mythtv sensord:   -12V: -19.26 V (min = -27.36 V, max = +3.93 V)
Dec 26 18:40:35 mythtv sensord:   -5V: -9.28 V (min = -13.64 V, max = +4.03 V)
Dec 26 18:40:35 mythtv sensord:   Stdby: +2.74 V (min = +0.00 V, max = +6.85 V)
Dec 26 18:40:35 mythtv sensord:   fan1: 4687 RPM (min = 0 RPM, div = 7)
Dec 26 18:40:35 mythtv sensord:   CPU Temp: 57 C (min = -1 C, max = 75 C)
Dec 26 18:40:35 mythtv sensord:   Unknown Temp: 66 C (min = -1 C, max = 127 C)
Dec 26 23:08:50 mythtv syslogd 1.4.1#21ubuntu3: restart.
Dec 26 23:08:51 mythtv kernel: Inspecting /boot/System.map-2.6.22-14-generic
Dec 26 23:08:51 mythtv kernel: Loaded 25445 symbols from /boot/System.map-2.6.2$
Dec 26 23:08:51 mythtv kernel: Symbols match kernel version 2.6.22.
Dec 26 23:08:51 mythtv kernel: No module symbols loaded - kernel modules not en$

--------------------------------------------------------------------------------

mythbackend log during the crash

--------------------------------------------------------------------------------

2007-12-26 18:16:06.075 Scheduled 74 items in 0.2 = 0.09 match + 0.16 place
2007-12-26 18:21:28.739 EITScanner: Added 2 EIT Events
2007-12-26 18:21:28.744 Reschedule requested for id -1.
2007-12-26 18:21:28.991 Scheduled 74 items in 0.2 = 0.09 match + 0.16 place
2007-12-26 18:24:49.581 EITScanner: Added 1 EIT Events
2007-12-26 18:24:49.586 Reschedule requested for id -1.
2007-12-26 18:24:49.846 Scheduled 74 items in 0.3 = 0.09 match + 0.17 place
2007-12-26 18:28:26.836 EITScanner: Added 1 EIT Events
2007-12-26 18:28:26.851 Reschedule requested for id -1.
2007-12-26 18:28:27.100 Scheduled 74 items in 0.2 = 0.09 match + 0.16 place
2007-12-26 18:31:07.093 EITScanner: Added 11 EIT Events
2007-12-26 18:31:07.098 Reschedule requested for id -1.
2007-12-26 18:31:07.348 Scheduled 74 items in 0.2 = 0.09 match + 0.16 place
2007-12-26 18:33:17.972 EITScanner: Added 1 EIT Events
2007-12-26 23:09:12.967 Using runtime prefix = /usr
2007-12-26 23:09:13.616 New DB connection, total: 1
2007-12-26 23:09:13.918 Connected to database 'mythconverg' at host: localhost
2007-12-26 23:09:14.558 Current Schema Version: 1160
Starting up as the master server.

--------------------------------------------------------------------------------

mythfrontend log during the crash

--------------------------------------------------------------------------------

stream: start_time: 62073.287 duration: 1916.938 bitrate=6076 kb/s
2007-12-26 18:38:24.637 AFD: Opened codec 0x99a9740, id(MPEG2VIDEO) type(Video)
2007-12-26 18:38:24.637 AFD: Opened codec 0x96b2de0, id(MP3) type(Audio)
2007-12-26 18:38:24.637 AFD: Opened codec 0x8b5b6c0, id(MP3) type(Audio)
2007-12-26 18:38:24.638 AFD: Opened codec 0x8a76920, id(DVB_SUBTITLE) type(Subt$
[mpegts @ 0x4e8598b0]Parser not found for Codec Id: 94212 !
[mpegts @ 0x4e8598b0]Parser not found for Codec Id: 94212 !
[mpeg2video @ 0x4ec84dc8]ac-tex damaged at 30 26
[mpeg2video @ 0x4ec84dc8]Warning MVs not available
[mpeg2video @ 0x4ec84dc8]ac-tex damaged at 22 0
[mpeg2video @ 0x4ec84dc8]Warning MVs not available
Starting mythfrontend.real..
2007-12-26 23:09:42.728 Current Schema Version: 1160
2007-12-26 23:09:42.730 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-12-26 23:09:42.730 Enabled verbose msgs:  important general
2007-12-26 23:09:46.994 Total desktop dim: 800x600, with 1 screen[s].
2007-12-26 23:09:46.997 Using screen 0, 800x600 at 0,0
2007-12-26 23:09:47.017 Switching to wide mode (MythCenter-wide)
2007-12-26 23:09:47.125 Using the OpenGL painter

---------------------------------------------------------------------------------

Can anyone offer any help as to why it is freezing or what I can try to solve it as it seems completely random at the moment.

Any help would be greatly appreciated.

Regards

James

---

### Post by browndog289 on 2007-12-28
I have been reading on the web about freezing of Ubuntu / Mythbuntu and several posts refer to the proprietary nvidia driver crashing the system. I installed Envy and updated to the latest nvidia driver, but this morning I tried to wake the box but it did not respond again so I am back to square one!

I will try booting Windows from UBCD for Windows (Bart-PE Edition) and leave it on to see if the problem happens there which should tell me if it is a hardware or software problem.

In the meantime if anyone has any ideas please help!

---

### Post by ian dobson on 2007-12-29
Hi,

Try booting froma LiveCD and run a memory check. I had problems with my Myth system until I found one of the memory modules was "bad".

I also built a test box out of junk that I had laying around.

Regards
Ian Dobson

---

### Post by browndog289 on 2007-12-31
Hi

Thanks for your reply. I already ran MemTest86+ for 7 hours without problems.

I have also tried passing acpi=off on the command line of grub as I have read that it can help. With that option it ran for 2 days without crashing but this morning the frontend displayed but is not responsive and I cannot ping the system either so I did a manual restart. The temps seem ok and the last log in mythbackend is:

----------------------------------------------------------------------------------
5: start_time: 8216.311 duration: 172.550
6: start_time: 8216.311 duration: 172.550
7: start_time: 8216.311 duration: 172.550
8: start_time: 8216.311 duration: 172.550
9: start_time: 8216.311 duration: 172.550
stream: start_time: 91292.344 duration: 1917.226 bitrate=6075 kb/s
2007-12-30 23:31:58.510 AFD: Opened codec 0x835cb10, id(MPEG2VIDEO) type(Video)
2007-12-30 23:31:58.511 AFD: Opened codec 0x9643530, id(MP3) type(Audio)
2007-12-30 23:31:58.511 AFD: Opened codec 0x8b84350, id(MP3) type(Audio)
2007-12-30 23:31:58.511 AFD: Opened codec 0x8fc1fa0, id(DVB_SUBTITLE) type(Subt$
[mpegts @ 0x4e8598b0]Parser not found for Codec Id: 94212 !
[mpeg2video @ 0x4ec84dc8]invalid cbp at 16 24
[mpeg2video @ 0x4ec84dc8]Warning MVs not available
----------------------------------------------------------------------------------

Now I am wondering if it is the old IR wireless keyboard (Model: SK-7100) that's causing problems so I have disconnected it and I'll let you know how I get on.

---

### Post by browndog289 on 2007-12-31
No good! It just froze up again - black screen and unresponsive will not reply to pings either.

I'm running out of ideas!

Can anyone help?

---

### Post by browndog289 on 2008-01-02
UPDATE:

Ok I have had the system on MemTest86+ for 45 hours and it passed all 58 tests without problems so the system is nice and stable.

I rebooted and removed and reinstalled the latest nvidia driver with Envy but it froze again after 2 hours!!

So I have changed to the open source nv driver instead - no TV-Out so no good for mythbuntu but it will narrow down the cause to a video driver issue or kernel issue, but I'm suspecting a driver issue at the moment.

Anyway I'll see what happens with the nv driver and let you know.

---

### Post by browndog289 on 2008-01-03
Well it froze again last night using the nv open source driver so I am going to try it with the VESA driver to see what happens.

---

### Post by browndog289 on 2008-01-04
It froze again last night on the VESA driver so I think I can rule out a video driver issue.

I have installed Boot Up Manager and disabled all but X and system logging to see if it is a software or Kernel issue.

---

### Post by sygin on 2008-01-05
Hi,

It sounds like you have an unstable rig, but it could still be a software issue. Are you using analog capture when the box freeze occurs? This process is cpu/memory intensive.

I would suggest that you install a package called "cpuburn" and run the it to test if it is a CPU overheating problem.

Try running:
burnK7

It works from the command line, so does not require X11 or Graphic card drivers. This should rule out CPU overheating. Sometimes old PC's have dried out heat sink compound on the CPU, or the heat sink is clogged, or the fan is not working.  

Best of luck,
Sygin

PS: Turn off overclocking if switched on.
PPS: For the Nova-T 500 PCI Card are you using firmware 1.10?

---

### Post by browndog289 on 2008-01-07
Hi,

Thanks for your response.
It froze again even when I wasn't running anything other than X and the logging services - mythbackend and mythfrontend were not running.

I have installed cpuburn and set it running under 'burnK7' yesterday from the recovery mode prompt and the system is still alive this morning some 21 hours later - I will leave it running for at least 48 hours (as thats the most it ran for before freezing before). I checked the voltages on the PSU using a meter and +5V was exactly 5V, 12V was 12.66V, however I have a new PSU, new IDE hard disk drive and a PSU tester on order.

The system was overclocked but I lowered it back to stock speeds after the freezing started.

I'll check the firmware on the Nova-T card after the 48 hours has finished.

Regards

James

---

### Post by sygin on 2008-01-08
Hi browndog,

If it was an overheating problem then I would have expected cpuburn to cause a freeze after 20 to 30 minutes. So I think that overheating is ruled out. I like the idea of getting a new PSU as this would have been my next guess.

While you wait for  your PSU etc.
I recently fought with a similar problem, it turned out to be a stick RAM that did not like the speed I was running at. I would suggest that you set your RAM BIOS timings to manual mode and set everything to the safest setting. i.e. Set the timings to thier slowest (highest). Just something to try while you wait.

All the best,
Sygin

---

### Post by theorganloft on 2008-01-09
I am having that freezing problem too.  I suspected the Nvidia drivers and did the same type of troubleshooting you did.  

I am suspicious of the Hard Drive caching and MYSQL.  Since this is running on a MySql engine, I suspect that the database is not keeping up with the cache built into the hard drive and there is some type of lag as it records.  

I am looking for a way to bypass the physical cache for testing.  I have a Maxtor 160 gb drive with 8 mb cache.  One other way to help this is to install a separate controller and drive for the MYSQL. 

I think we should take a look at the MYSQL performance as well.  :guitar:

---

### Post by sygin on 2008-01-09
Hi,

I doubt that the problem is related to MySQL, it is not used to directly store the recorded video. The recorded video is written directly to disk. MySQL is used to store info on the recording and a seek table for each recording (it does do a lot more), this not very much info compared to the actual video files. 

This does not rule out a faulty Hard Disk though. 

I have Ubuntu 7.10 and MythTV installed on two systems and have not had any stability problems except for a faulty CPU fan. If you are experiencing a "hard lockup", i.e. No disk activity, keyboard does not work, and you can not ping the box, I would bet on a hardware related issue.

I must say that I hate dealing with unstability problems, and wish you the best of luck,
Sygin

---

### Post by theorganloft on 2008-01-09
> **sygin said:**
> Hi,

I doubt that the problem is related to MySQL, it is not used to directly store the recorded video. The recorded video is written directly to disk. MySQL is used to store info on the recording and a seek table for each recording (it does do a lot more), this not very much info compared to the actual video files. 

This does not rule out a faulty Hard Disk though. 

I have Ubuntu 7.10 and MythTV installed on two systems and have not had any stability problems except for a faulty CPU fan. If you are experiencing a "hard lockup", i.e. No disk activity, keyboard does not work, and you can not ping the box, I would bet on a hardware related issue.

I must say that I hate dealing with unstability problems, and wish you the best of luck,
Sygin

You are correct about the MYSQL but I want to be sure about the scheduling systems and MYSQL. I notice that when I fool around with the schedules, it locks up.  That is why I looked at MYSQL.    

I agree with you that there may be another reason and where my system is concerned, I installed MythTV on top of my Ubuntu Studio install to see what would happen.  

I suspect that I messed with the resolution settings too much. This may be the main problem.   

Thanks!  
:guitar:

---

### Post by browndog289 on 2008-01-09
Hello!

Ok I finally stopped burnK7 after 3 days solid without any freezes and the cpu was running at 55C so that rules out overheating.

I am now trying your suggestion of relaxing the memory timings, although the board I have will only let me change a few settings.

The old settings were: 

Bus Speed: 133MHz (266 DDR)
Timing: Normal
CAS: Set by SPD
MemTest86+ Memory throughput: 701Mb/s

The current ones for testing are: 

Bus Speed: 110MHz (220 DDR) - Manually lowered in the BIOS
Timing: Safe
CAS: 3T
MemTest86+ Memory throughput: 621Mb/s

Its been running for nearly 10 hours so far but it'll need to run for around 2-3 days without freezing for success.

As regards the MySQL problem, I don't think this is affecting my system although I may try killing the MySQL daemon and mythbackend in the next test to rule that out.

I'll post back the results of the current test if it freezes or after 2 or 3 days if it doesn't!

Thanks

browndog289

---

### Post by browndog289 on 2008-01-10
I checked it this morning by pressing the CAPS LOCK key and the light didn't come on so I pressed the NUM LOCK key and the light came on but then it wouldn't do anything else, the screen was blank and it stopped responding to the keyboard.

The new PSU and Hard disk are here now so I may have to give them a try later.

---

### Post by browndog289 on 2008-01-10
Looks like the last syslog entry was around 06:25am so it froze 3 hours before I checked it.

I've removed one of the memory modules and rebooted it to test if there is an incompatibility problem between the 2 (1 x 512Mb, 1 x 256Mb).

---

### Post by theorganloft on 2008-01-10
I think that I solved my freezing problem.  

When I installed MythTV, I installed it over Ubuntu Studio Gutsy Gibbon 7.10.  It would freeze randomly.  Then I discovered that the screen saver and Power management features were causing problems.  I turned them off and the freezing subsided.  I thought that I was in the clear until it froze when I tried to make scheduling changes.  

I decided to reload the machine with a brand new download of Mythbuntu.  This seems to be the answer.  It is more responsive, recognizes my Nvidia PCI Express (with the special drivers) and I could go in an out of menus.  

The only problem is that you have to change channels slowly.  According to the forums, this is a bug that they are working on.  

My system recordied for 4 hours straight and was still running when I left the house this morning.  We will see when I get back home if it crashes.  I need to set up a remote connection but I did not have time to configure the router last night. :guitar:

---

### Post by browndog289 on 2008-01-10
I'm glad you managed to sort your one out, wish mine was as easy!

It froze up again this afternoon with only the 512Mb module in (that one was detected by the SPD as 200MB/s - DDR400). I've replaced it with the other one - the 256Mb (133Mb/s - DDR266). To see how it goes with that one - otherwise I will start removing hardware - network cards etc one at a time to isolate the problem.

---

### Post by rhpot1991 on 2008-01-13
I have a very similar issue.  Though mine doesn't happen nearly as frequently as yours does.  Once every month or two I notice (normally from work where I can't do anything about it) that my master backend is no longer responding.  The system completely locks up, no video output, keyboard is dead.  I have tried a few of the sysreq magic keys in attempt to unlock the system and see if I can find any clues as to the problems, but none of them seem to do anything at that point.

A few things I have noticed:
1.  The system seems to lock up while a recording is happening or finishing.  I always have a 1B recording laying around after the lock.  The last time I had 2 1B recordings, one which should have just been ending while the other one was starting.
2.  Everyone seems to say this is a hardware issue (which makes sense because my 2ndary backend doesn't do this), but then why does the box run perfectly fine for 1-2 months (constantly recording and everything) and then this happens?

At this point I can try to replace parts, but nothing stands out as a good choice.  I have tested the ram with memtest, goes through at least 5 iterations of tests.  I have been removing random things like my bluetooth adapter, which gets my hopes up that I have fixed the problem, only to see it crash at some later point.  It is so hard to debug when it happens so infrequently and so far apart.

---

### Post by browndog289 on 2008-01-14
Sounds like your problem may be down to somethink like scheduling updates for the TV guide - maybe they are performed once a month or so? Someone else on here would know better than me!

Anyway I am still trying to troubleshoot mine, I am down to it being either the 512Mb RAM stick or ndiswrapper for my Netgear WG311 wifi card.

I removed the 512Mb RAM and disabled the wifi card and the system ran without problems for 3 days. I put the 512Mb RAM in alongside the 256Mb last night and it had frozen this morning - I've removed it again and am waiting to see what happens.

There is a similar problem described here: [http://discussions.virtualdr.com/archive/index.php/t-142761.html](http://discussions.virtualdr.com/archive/index.php/t-142761.html)

I have one double sided (The 256Mb) and one single sided (the 512Mb) memory module so my problem is similar to the link.

Also the system was not on a surge protector which I'm sure didn't help.

---

### Post by browndog289 on 2008-01-17
Well its frozen again this morning so I have now removed the Netgear WG311 wireless card and rebooted to see if its that causing a problem.

So far thats the most it has run without a freeze for - 36 hours.

I have also read that disabling apic in the kernel options in GRUB can solve freezing problems - does anyone know if this is true or worth a try?

---

### Post by anaconda on 2008-01-18
I think it is acpi not apic..

Try the "acpi=off" boot option..
There have been freezing problems that have been solved with that..

[http://ubuntuforums.org/showthread.php?t=587905&highlight=randomly+freezing&page=52](http://ubuntuforums.org/showthread.php?t=587905&highlight=randomly+freezing&page=52)

---

### Post by theorganloft on 2008-01-18
> **browndog289 said:**
> Well its frozen again this morning so I have now removed the Netgear WG311 wireless card and rebooted to see if its that causing a problem.

So far thats the most it has run without a freeze for - 36 hours.

I have also read that disabling apic in the kernel options in GRUB can solve freezing problems - does anyone know if this is true or worth a try?

You definitely have a issue in the hardware. 

I built a brand new Myth TV system based on a biostar MOBO, Maxtor 160Gb X2, a 256 MB Nvidia Video Card, and a happuage tuner card.  It works flawlessly. I use the 7.10 Mythbuntu distribution. 

This week I will get to test the Clear-QAM on Comcast cable.

I did not have to turn off the power saver in the bios or the application.  I tested t by leaving it running 24/7 for 1 week and setting scheduled recordings.   It ran flawlessly.  

I think your MOBO or CPU is bad.

---

### Post by browndog289 on 2008-01-18
Thanks, I already tried it with acpi=off, the option I mean is noapic as in this link:

[http://ubuntuforums.org/showthread.php?t=667489](http://ubuntuforums.org/showthread.php?t=667489)

Yes it is looking like a hardware issue although with the wifi card removed it has now been up for 38 hours (2 hours more than before) so fingers crossed! I'll check it again in the morning.

---

### Post by browndog289 on 2008-01-21
With the wifi card removed the system is still up and running after 4 days, so I'm declaring this one solved!

Now is there any reason why ndiswrapper and a Netgear WG311 would freeze the system every 2 days or so?

browndog

---

### Post by Meph1st0 on 2008-06-30
Browndog,

I believe I'm experiencing the same problem as you were.  My PC has been crashing every night for the last week or so.  This didn't happen before I upgraded to Hardy Heron AND installed the GUI Ndiswrapper tool.  When I initially installed my network card back in the day I only installed ndiswrapper without the gui tool.  I too have a netgear wg311 wireless network card that I'm using.  I'm going to remove the card tonight and see how long my machine stays up and I'll let you know.  But from what I've read in this thread and comparing with my own PC freezing experience, I think you've found the problem.  I wonder if it's more specific to the Ndiswrapper GUI tool though.  Are you using the ndiswrapper gui tool as well?

---

### Post by Lindsay.Mathieson on 2008-07-01
Joining in .... :(

I have a fresh two week old Mythbuntu 8.04 install as well, all weekly updates etc.

I did have some issues with a faulty power supply that caused it to randomly shut down, new power supply seems to have fixed that.

I have had lock ups as well, always after a recording *ends* it seems. I have suspicions that it may be related to commercial detection, which is set to start when the recording starts. I'm going to disable commercial detection jobs to see if that makes a difference.

---

### Post by Lindsay.Mathieson on 2008-07-01
Gaah - should have read to the end of the thread before posting.

I too have a Netgear WG311v3 card, using ndis wrapper. I think the evidence is getting overwhelming here.

Unfortunately I *really* need a network connection. Can anyone recomend a cheap/easy PCI/PCIe/USB wireless adaptor?

---

### Post by Meph1st0 on 2008-07-01
Last night was the first night my box has gone without freezing.  I removed my netgear wg311 card (I think it too was a v3).

Lindsay,

I've constantly had problems with my wg311 network card and wireless and ndiswrapper.  What I've ended up doing is getting a spare (from a friend for practically nothing) linksys wrt54g router and loading the dd-wrt firmware.  I then set it up as a wireless bridge and connected my mythbox to it with just a network cable.  This way it's still "wireless" but as far as my mythbox can tell it's actually wired.  

I did this only a week ago and haven't had a problem with it since.  The only thing is, it's not too attractive having a bright blue wireless router sitting in my entertainment center.

---

### Post by ozybushwalker on 2008-07-01
> **Lindsay.Mathieson said:**
> 
Unfortunately I *really* need a network connection. Can anyone recomend a cheap/easy PCI/PCIe/USB wireless adaptor?

I've written a few device drivers. It can be hard enough to get them right when interfacing directly to the operating system. Adding an emulation layer like ndiswrapper makes things more complex. I suggest you look for something thats supported by native drivers. However that is not as easy as it may sound. The big 3 consumer network gear suppliers (DLink, Linksys and Netgear) have all adopted the practice of changing chipsets without changing the model id, thus a particular model may use any one of four different chipsets, only one or two of which have native Linux drivers. 

Atheros based cards have a good reputation in the open source community, both Linux and xBSD. Most (but not all) of the Atheros PCI chipsets are supported by the madwifi driver. See [http://ath5k.org/wiki/Compatibility]("http://ath5k.org/wiki/Compatibility")
for a list of suppliers of Atheros cards supported by the madwifi driver. Note the warning about USB devices. 

I've been using a TP-LINK TL-WN651G which is based on the Atheros AR5212 for over 6 months in a Linux based firewall (Smoothwall). Its been on constantly providing Access Point service and its worked very reliably. It wasn't the cheapest card available at the time but it wasn't expensive either.

Ralink has a range of chipsets which are supported by open source drivers. See [http://ralink.rapla.net/]("http://ralink.rapla.net/") for lists of devices based on the Ralink chipsets. I have used a Gigabyte GN-WB01GS (USB device, rt73 driver) intermittently. It was instantly recognised by Mythbuntu 7.10. I have not used it over extended periods but have no reason to believe it would give trouble.

You can also consult [http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/")
for more information about what chipsets are in what wireless devices.

I suggest you get a card based on the Atheros chipset and work through the list of suppliers referred to earlier and with a shopbot style service locate an outlet selling Atheros based PCI cards.

---

### Post by buntunub on 2008-07-01
For those of you remotely accessing mythtv on a remote backend, I believe th issue is with NFS. For me, it seems to be getting worse with each kernel update. Several bugs on launchpad reference the issue as well. Check your /var/log/messages, /var/log/syslog, /var/log/daemon. You should see a common set of messages referencing nfs server timeouts. I experience no issue whatever when accessing the backend via Windows clients, or when using Mythweb streaming that way. This has been driving me completely up the wall lately trying to figure this thing out and get it fixed lol!.. Still working the issue.. Will get back when I get something figured out.

---

### Post by bigdawgte on 2008-07-02
I would bet $50 that it is your motherboard, and specifically your chipset that is really causing your problems.  You don't mention what you have, but dollars to donuts, it is an nForce chipset; and if that is correct, then is likely to be the most troublesome of all nForces, the nf3.  I have this chipset in my DFI Lanparty UT nF3 250Gb, which works fine in Windows, but Linux hates it, and despite documentation everywhere, across numerous distributions, about problems with Video, Sound, Audio, ACPI, bugginess and other instability related, as best I can tell, as a noob, to the peculiar way Nvidia handled the AGPGart in these mobos (or not, since newer PCI-E nForce boards appear to have similar issues).  The thing is, there are reports of problems with these chipets on SUSE, Fedora, Kernel Tracker, etc. endlessly, but no sort of centralized effort or shared recognition of the problem.  Again, as a noob, it is difficult to understand how the board could run windows so smoothly, but give every Linux distro I have tried fits.

I could not ever rely upon Linux exclusively because I have had similar issues with several hardware I have owned over the years.  Likewise, the approach to problem solving in the Linux world makes it nearly impossible for a new hand to approach problem solving in an efficient way - when you post to or simply read a board about an issue, although the people thereon are certainly well intentioned, they often know very little about your specific issue, and so you waste time trying solutions that many others have tried across the Linux universe, to no good end, or pursuing the wrong rabbits down (very deep) rabbit holes.  

I thought my 3-day troubleshooting sessions were painful enough with Windows; which is why I switched to Macs.  In Linux, trouble shooting has averaged 1.5 weeks in most cases, and my success rate is low.  While I love the freedom of the Open Source world, I could never really be productive at this pace.  Macs are a non-tinkerer's best friend - more freedom (and more logical) than Windows(MS's built in fixes and stupid proofing are quite often the CAUSE of most problems).  Sorry about the rant, I just had to get if off my chest.

---

### Post by mark467 on 2008-07-11
I experience the same type of lockups. Blank screen and no response from keyboard or remote access (or ping) I dont think it is a faulty hardware issue however. This same box ran OpenSuse 10 stable and never locked up once for 5 months. I have run memtest and cpuburn and another one that does mem cpu and hd testing with no problems. It might be an issue with the wireless though. I have reloaded this machine with clean installs of mythbuntu hardy package. I dont get any lockups until I move it downstairs and add the wireless. I have tried netgear ma11, linksys wusb54gc, and trendnet tew-423pi so I dont think it is specific to chipset or brand. Also, I tried mythdora 5 with no lockups til adding wireless. I did not use ndiswrapper for it. The wusb54gc was detected and I just added firmware/drivers for it. Would love some help with this as I dont want to run 200ft of cat5 downstairs. I might try a wireless hub next that I can plug into my 10/100 nic.

---

