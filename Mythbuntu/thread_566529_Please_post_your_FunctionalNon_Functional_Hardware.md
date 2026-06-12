---
title: "Please post your Functional/Non Functional Hardware"
date: 2007-10-03
forum: Mythbuntu
---

### Post by superm1 on 2007-10-03
Hi folks,
With the release of the beta, the amount of changes that can be made are likely limited to bug fixes.

In an effort to produce accurate documentation of what people will need hardware wise for setting up a box, we'd like if you can post what hardware you've got (particularly tuners) and how things work with it.

Please don't hijack the thread with trying to diagnose problems you are encountering, make a separate thread for that.  Just a simple works/doesn't work followed by a short description will suffice.  Hopefully a lot of the problems people encounter will be simple solutions (such as manually adding a remote configuration), but still a separate thread is much preferred to using this thread again.  If you have a piece of hardware that you got to work though the help of the forums or other online source, a link to that would be great.

A sample post can look something like this:

_**Hardware**_
**CPU:** Intel pentium4 2.8 Ghz
**RAM:** 1.0 gb ram
**Video Card: **NVIDIA 7600gt, 256 mb
**Remote****: **mceusb2
**HD:** 60 gb hard drive
**Tuners:**
Hauppauge PVR-350
Silicon Dust HDHomerun

[U][B]Performance
[/B][/U]All hardware properly detected and functional.
Had to install nvidia proprietary drivers before able to use HD playback.

**_A blank template for your convenience_** 

_**Hardware**_
[B]Motherboard:
CPU:[/B]
**RAM:**
**Video Card: **
**Sound Card:**
**HD:** 
**Remote:**
**Tuners:**
**Country: E.g. the Netherlands:**
**TV provider: E.g. canal digital:**
**TV signal type: E.g. DVB-S (satellite):**
**Mythbuntu Version: E.g. 8.10**

_**Performance**_

---

### Post by tgm4883 on 2007-10-03
_**Hardware (myrtle)**_
**Setup:**  Primary Backend/Frontend
**CPU:** AMD Athlon X2 3800+
**RAM:** 1.0 gb ram
**Video Card:** NVIDIA 6100 (onboard)
**Sound Card:**IDK, whatever is onboard a Gigabyte GA-M61VME-S2
**HD:** 500 GB SATA hard drive
**Remote:**  MCEUSB2
**Tuners:**
Hauppauge PVR-150
pvHDTV 5500

**_Performance_**
All hardware properly detected and functional.
Had to install nvidia proprietary drivers before able to use HD playback.

_**Hardware(zeus)**_
**Setup:**  Slave Backend (and fileserver)
**CPU:** AMD Athlon XP 2000+
**RAM:** 768 gb ram
**Video Card:**  Some old video card
**Sound Card:**  IDK, don't matter on backend only
**HD:** 160 GB hard drive
**HD2:**  Various Hard Drives for file storage (Files, Videos, Music, Pictures)
**Remote:** None
**Tuners:**
Motorola 6200 STB streaming over firewire

**_Performance_**
All hardware properly detected and functional.
Firewire works OK.  Some channels are flaky because of they way they are broadcast (poorly) from the cable company.  I haven't bothered to talk to the cable company about it hasn't become a problem for me yet.

---

### Post by pdragon04 on 2007-10-04
**_Hardware_**
**CPU:** 2.8Ghz Celeron
**RAM:** 512MB
**Video Card:** GeForce 5500 using S-Video out to TV
**HD:** 250GB (50gb ext3 base install; 200gb xfs for recordings)
**HD2:** 750gb (xfs; extra storage for dvd-rips, etc)
**Tuners:** Hauppauge PVR-150

_**Performance**_
Had to boot into Safe Graphics Mode to install.
After install, everything working perfect.

---

### Post by mndbndr on 2007-10-04
**_Hardware_**
**CPU:** AMD64 AM2 3800
**RAM:** 2 GB Crucial Balisitc 
**Video Card:** EVGA 7600GT 512MB
**HD:** 3 500 GB SATA3 
**Tuners**: Twinahn 102G, Avermedia A180 HD
**Sound Card:** X-Fi Elite Pro, onboard sound


**_Performance_**
Had to boot into Safe Graphics Mode to install.
Installed X-Fi beta driver after install.

---

### Post by crmullins on 2007-10-05
**_Hardware_**
**CPU:** AMD64 Socket 754 Newcastle 2.4 Ghz
**RAM:** 1 GB RAM
**Video Card:** NVIDIA GeForce 5200 FX 128 MB using DVI -> HDMI cable
**HDD1:** 200 GB SATA (10 GB ext3 base install; remainder for future expansion)
**HDD2:** 200 GB SATA (200 GB xfs for recordings)
**Tuners:** Hauppauge PVR-500
**Remote:** Windows MCE usbmce2

**_Performance_**
All hardware properly detected and functional.
Had to use lcd monitor for install before hooking up to my plasma tv.
Had to disable screensaver to watch anything over 10 mins long.
Remote worked from the get-go.
Easiest installation I've encountered so far and I've tried them all!

---

### Post by drven1005 on 2007-10-06
This is an Intel Mac Mini.

Hardware
CPU:Genuine Intel(R) CPU           T2300  @ 1.66GHz
RAM: 512MB
Video Card: Intel i810
Sound Card: Intel Corporation 82801G (ICH7 Family)
Remote: Stream Zap



I've ran in to a few small issues.  First, by default the mac mini while connected to an hdtv via dvi is stuck at 640x480.  This is true during the install.  I had to alt+drag to move the menus around so I could see the forward button.  

That wasn't a big deal.  The main problem is with the video drivers.  Mythbuntu decided to use the "intel" driver.  While it did get me X on my tv and I could go through mythtv-setup and the frontend, when I tried to watch a recorded program, it looked awful.  Very red, colors seemed to bleed etc..

To fix this, I had to change to the i810 driver by modifying the /etc/X11/xorg.conf file manually. 

The other problem I found while installing on a different machine with an nvidia card is that the installer likes to use the open source "nv" driver, which does not support TV out.  So to install this on my backend, which doesn't have a monitor, I had to drop to a virtual terminal and modify the xorg.conf to use vesa and then restart gdm.  Same problem again where I couldn't see the forward buttons.

Other than that, so far so good.

> **drven1005 said:**
> Other than that, so far so good.

Well I spoke too soon.  When you use the i810 driver, all you get is a blue screen when you try to watch HD content.  

To get around this, I had to add:

Option          "LinearAlloc"   "16384"

to my xorg.conf file.  Notes from:  [http://mythtv.org/wiki/index.php/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu#Viewing_HD_Material](http://mythtv.org/wiki/index.php/Installing_MythTV_on_an_Intel_Mac_Mini_using_Ubuntu#Viewing_HD_Material)

Using the i810 driver also breaks the display resolution utility.

---

### Post by superm1 on 2007-10-06
> **drven1005 said:**
> This is an Intel Mac Mini.

Hardware
CPU:Genuine Intel(R) CPU           T2300  @ 1.66GHz
RAM: 512MB
Video Card: Intel i810
Sound Card: Intel Corporation 82801G (ICH7 Family)
Remote: Stream Zap



I've ran in to a few small issues.  First, by default the mac mini while connected to an hdtv via dvi is stuck at 640x480.  This is true during the install.  I had to alt+drag to move the menus around so I could see the forward button.  

That wasn't a big deal.  The main problem is with the video drivers.  Mythbuntu decided to use the "intel" driver.  While it did get me X on my tv and I could go through mythtv-setup and the frontend, when I tried to watch a recorded program, it looked awful.  Very red, colors seemed to bleed etc..

To fix this, I had to change to the i810 driver by modifying the /etc/X11/xorg.conf file manually. 

The other problem I found while installing on a different machine with an nvidia card is that the installer likes to use the open source "nv" driver, which does not support TV out.  So to install this on my backend, which doesn't have a monitor, I had to drop to a virtual terminal and modify the xorg.conf to use vesa and then restart gdm.  Same problem again where I couldn't see the forward buttons.

Other than that, so far so good.
Please start another thread regarding this issue if you can.  Detail everything you've already mentioned here.  (Don't want to clutter this one).  I've got some points to bring up from a discussion with the xorg maintainer tonight.

---

### Post by spoky99 on 2007-10-07
Setup: Primary Backend/Frontend
Hardware
Motherboard: Mini-ITX Motherboard LV-671
CPU: Pentium Intel(R) Pentium(R) M processor 1.70GHz
RAM: 512 (work well also with only 256 Mb)
Video Card: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
Sound Card: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
HD: now only 40 Gb
Remote: grey hauppauge and M$ mce remote via USB
Tuners: 1 hauppauge PVR150 MCE and 1 hauppauge PVR150 (i tryed also one PVR350 but.. the tuner is less sensitive than the PVR150 I don't know is the hardware is damaged ;) I buy it used)

Performance
All hardware properly detected and functional.
I had some problem for the tvout, lcd (crystalfontz 634) and acpi autoboot
the tv out was only a problem of configuration (I will post the xorg.conf)
the lcd was solved (thanks to superM and maxnuv)
I'm working o the ACPI (is not true.. we are working :) )

I also installed the mythbuntu into other computer... I will post the hardware list and the problem soon

---

### Post by p$y on 2007-10-07
Setup: Primary Backend/Frontend
**Hardware**
CPU: Pentium 4 / 2,6 Ghz
RAM: 1024 DDR
Video Card: Nvidia GeForce 8400GS
Sound Card: Via OnBoard / Soundblaster Live 5.1
HD: 80 GB mythbuntu installed
      160 GB with a mountpoint at /var/lib/mythtv
Remote: X10 Medion Remote
Tuners: DVB-T Siemens Mobile
             DVB-T MSI Megasky 580
             Hauppauge DVB-S


**Performance**
The OnBoard sound sometimes doesnt work / Soundblaster not recognized (known Ubuntu problem)
Had to download the firmware for the MSI Megasky
the 160GB aren't recognized (Mythweb says there is only the 80GB) mybe my faul (first time set such a mount point)
Had to install in safe graphical mode (installed with tvout/s-video)
Only few functions for the remote (no rewind etc...) 
(lircd.conf from [http://www.vdr-wiki.de/wiki/index.php/Fernbedienung_-_USB_X10](http://www.vdr-wiki.de/wiki/index.php/Fernbedienung_-_USB_X10))

---

### Post by gareththered on 2007-10-07
Hardware
**CPU:** Intel Pentium 4 @ 2.6GHz
**RAM: **1Gb
**Video Card:** Geforce 6200
**Sound Card:** Soundblaster Live! 5.1
**HD:** 40Gb PATA & 80 Gb PATA
**Remote:** Hauppauge Remote ( Does NOT Work :-( )
**Tuners:** Hauppauge Nova T-500 (Dual DVB-T)

Works very well apart from the IR Remote.
Video card and Sound card detected first time, although I had to use 'asoundconf' to set my SoundBlaster Live! to be the default one instead of the onboard chip.

---

### Post by stevetv on 2007-10-08
hi there... first time poster.  i wasnt sure if i was suposed to reply to this post or start a new one.  

regardless.. maybe this is a new forum? .. so i wanted to post my experiences.  it was positive.  

Hardware
Mobo:  gigabyte GA-7N400 (its fine.. but it doesnt have sata connectors)
CPU: athlon XP 3200+ underclocked to around 2000mhz socket a
RAM: 1 gig (2 x 512) corsair value select DDR
Video Card: winfast leadtek GF7300GT.  connected via component cables to a SD CRT tv.
Sound Card:nvidia onboard.
HD:samsung 400g pata
Remote: streamzap - im not thrilled with the default mapping so ill change it
Tuners:  Technisat AirStar 2 DVB-T .. required me to update vlc.


i needed to update VLC before the tuner card would be detected.
the video card was detected fine.. which was nice.

i live in australia.  i believe that i asked for xmltv to be installed, but it didn't do it for me.  i had to install xmltv via apt-get.  I then needed to create tv_grab_au and modify that to suit.  I used a piece of code written by manicmike from the knoppmyth forums.  his code sets up tv_grab_au.  i needed to modify the code to fit the mythbuntu file structure.. but it worked perfectly.

i enjoyed this setup.  thanks to those that worked on it.

---

### Post by jmbarra78 on 2007-10-08
Hardware
Barebome MSI MEGA PC 651
CPU: Pentium 4 2,6 Mhz
RAM: 1 GB DDR 400
Video Card: nVidia FX 5500
Sound Card: Realtek ALC 650
HD: Maxtor 250 GB ATA 133
Remote: Nova-T 500 Remote control
Tuners: Hauppauge NOVA-T 500 

All hardware works fine except remote control... I Worked with Ubuntu 7.04 but in 7.10 doesn't work...

---

### Post by dmf86 on 2007-10-08
ATI Radeon 9200 (Only works in VESA mode) - Worked fine in 7.04

---

### Post by tgm4883 on 2007-10-08
> **dmf86 said:**
> ATI Radeon 9200 (Only works in VESA mode) - Worked fine in 7.04

Was there anything else about your hardware that you wanted to tell us?

---

### Post by jpwilson on 2007-10-08
Backend (running)
Hardware
CPU: Athlon 4400 X2 (low power)
RAM: 1 gig
Video Card: NVidia 7600
Sound Card: Onboard (Via)
HD: 320 Gb Seagate Sata
Remote: NA
Tuners: 1 x Haup Nova-T 500

Frontend 1 (work in progress)
Hardware
CPU: VIA C3 1000MHz
RAM: 512Mb
Video Card: Unichrome Pro
Sound Card: On board
HD: 4 gig USB Drive
Remote: MCE Remote
Tuners: NA

---

### Post by gtr33m on 2007-10-08
Hardware
CPU: AMD Athlon 3000+
RAM: 2.0 gb ram
Video Card: NVIDIA 7300gt, 256 mb
HD: 80 gb ext3 for O/S and recording, 500 gb NTFS for data storage
Tuners:
Ultraview (DVico) DVB-T Plus

Performance
All hardware properly detected and functional.
Made changes to /etc/modprobe.d/aliases and created /etc/modprobe.d/dvico.  May not have been necessary but always had to before to get MythTV working.
No problems with HD, runs smoothly

---

### Post by bowmanr@mailcity.com on 2007-10-09
**_[SIZE="6"]Combined Backend/Frontend[/SIZE]_**

**_Hardware_**
**CPU:** Pentium IV 1.8
**RAM: **512Mb
**Video Card:** nVidia FX5200
**Sound Card:** Onboard
**HD:** 1 x 80Gb, 1 x 500Gb
**Remote:** Hauppauge
**Tuners:** 2 x Hauppauge PVR-350

**_Performance_**
All SD, works abolutely fine even when recording on both tuners whilst watching liveTV from one of the tuners and streaming recordings to remote frontend.
Also used as home file server via samba, no negative impact on performance.

**_[SIZE="6"]Remote Frontend #1 -- wired mini desktop[/SIZE]_**

**_Hardware_**
**CPU:** AMD Sempron 2600
**RAM: **512Mb
**Video Card:** Onboard
**Sound Card:** Onboard
**HD:** 1 x 160Gb
**Remote:** Serial (Igor)
**Tuners:** n/a

**_Performance_**
Perfectly acceptable performance watching SD streams from the backend and watching DVDs from local player.

**_[SIZE="6"]Remote Frontend #2 -- wireless laptop[/SIZE]_**

**_Hardware_**
**Model:** IBM R50e 1834
**CPU:** Pentium M
**RAM: **768Mb
**Video Card:** Onboard
**Sound Card:** Onboard
**HD:** 1 x 40Gb
**Remote:** none
**Tuners:** n/a

**_Performance_**
Reasonable performance watching SD streams from the backend, occasional prebuffering pauses (once or twice an hour). Prebuffering maybe network related as DVD playback absolutely fine.

~~~~~~~ 
*Note : not mythbuntu boxes, 7.04 install following community install docs*

---

### Post by rusty0101 on 2007-10-09
[B]Master back end - Beast

Hardware[/B]
**CPU:** AMD Athlon(tm) XP 2400+
**RAM:** 1 gig ram 2 gig swap
**Video Card**: nVidia GeForce FX 5200
**Sound Card**: nForce2 AC97
**HD:** 3 400 gig 7200 rpm Segate Barracuda pata drives, 1 dvd+/-rw. hda configured with 92 gig root, 2 gig swap, remaining added to lvm group. hdb and hdc dedicated entirely to lvm group. total in lvm comes out to 1 Tbyte
**Remote:** Hauppauge Grey
**Tuners:** 3 Hauppauge pvr-250 tuners in case, 2 silicon graphics hdhomerun receivers outside. The three 250s are capturing analog cable, oen hdhomerun is capturing unencrypted digital cable, 1 is capturing off the air hdtv content.


**Performance** This box currently has a front end running on it, however I am likely to be removing that functionality in the reasonably near future. I have succesfully captured 2 hdtv (not just digital tv) channals and 2 analog channels simultaniously. That is possible because all of the tuners are streaming mpeg2 content already compressed and the system itself is primarily just keeping track of what files are open and where it should be dumping the data. It is serving up content to the front end described below (Beauty) and is making content available to other systems in my home running the mythtv front end software. Those systems are running a combination of gutsy and feisty and have accessed with no problem. One of the reasons that this is not running as a front end is that the HDTV content is not displayed in an acceptable fassion. This box has run Knopmyth for over a year with half the memory and a slower processor. I had hoped that the 2400 processor I had pulled form a motherboard that would not have functioned well (VIA chipset bios, exhibits known DMA crashinb behaviour) would have helped with that, no luck.

[B]Front end - Beauty
Hardware
CPU:[/B] Intel(R) Pentium(R) 4 CPU 2.66GHz
**RAM:** 512 Meg ram, 1.5 Gig swap
**Video Card:** nVidia GeForoce 6200
**Sound Card:** embeded Intel ICH4/ICM4-L/ICM4-M AC'97 controler
**HD:** Seagate baracuda 160 gig drive (smallest I could find when the 30 gig that came with the system died), cd-rw/dvd-ram
**Remote:** Streamzap pc remote
**Tuners:** none


**Performance** This started as an IBM netvista that came with the described Intel processor, memory audio and a cd-rw/dvd-ram drive. The embeded intel video could only be configured in bios to accept 8 meg of stolen memory, and no matter what I tried I was never able to get HDTV to succesfully play through that video interface. The hard drive (30 gig) that came with it, died slaming it's heads against the wall, so I picked up the smallest new hard drive I could find. (generally happy with Segate drives up to this point, but was not specifically looking for that) With the GeForce 6200, the propriatary 3D enhanced-new drivers and the Preferred MPEG2 Decoder set to "Standard XvMC" HDTV content plays acceptably. The card also has 256 meg of ddr2 memory, though I'm not sure how much that helps. The card is 8x agp capable, but is only runing at 4x agp. Not sure if this is a limitation of the nVidia drivers or the motherboard.

You may note elsewhere that the minimum recomended specs for hdtv content are 3 gig. In general I support that recommendation. My front end is capable of hdtv content playback at an acceptable rate for me, but it is not doing hdtv recording at the same time. That is happening (if at all) on the back end system. The front end box that I have assembled totals about $35 in parts. I was not looking for 5.1 surround sound or digital audio out. This specific box uses a low profile format, and while the video card is a low profile card, it did not come with the low profile bracket. I consider this to be a flaw that I will be correcting at some point. But ti's why I am not advertising the manufacturer of this specific card.

Video output frm the front end is going through a 50 foot VGA cable to a DLP projector. The resolution is outside the native resolution for the projector which may be an issue for some users, however the projector ahs a native resolution of 1024x768. 1280x960 with the projector set to 16:9 and the format set to 16:9 works acceptably for me. For now the 'screen' is a wall painted white, which probably suggests to some people that I don't care about the quality as much as they do. That's ok too.

Configuring the Hauppauge remote on the front end still needs a few tweeks. Originally this system had been configured with the StreamZap remote, and the software to change remotes does not seem to know how to update the ~/.mythtv/lircrc file with the new profile. It involved a manual run of mythbuntu-lircrc-generator which gathered from the /etc/lircrc file that I was using a hauppauge receiver and generated a .lircrc file for me, with multiple hauppauge remotes defined. Minor chor editing out the Hauppauge_WinTV_Nexus-S, Hauppauge-350 and Hauppauge (non _pvr) lines. Some tweeking remains to make the channel up/down, blank, audio up/down, and color buttons usable, but it's not a priority at this time.

---

### Post by jmbarra78 on 2007-10-09
My Nova-T 500 control remote works fine!! 

I follow this wiki:

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

---

### Post by mr_bungalow on 2007-10-10
Combined frontend and backend

Hardware
CPU: P4 2.8 (Prescott) - Machspeed Motherboard
RAM: 1 Gig 
Video Card:  nVidia GeForce 5600
Sound Card: Onboard Sound (VIA 8533 - I think)
HD: 250 + 160 IDE Hard Drive
Remote: Zapway.de homebrew serial receiver (not working) w/ harmony remote
Tuners: Hauppauge PVR-150

Performance: Forced to upgrade when I lost support on my FC4 machine this fall.  I only use standard definition at this point in time and everything worked out of the box EXCEPT for the serial IR receiver.  Thanks for the slick installer!

---

### Post by superm1 on 2007-10-10
> **mr_bungalow said:**
> Combined frontend and backend

Hardware
CPU: P4 2.8 (Prescott) - Machspeed Motherboard
RAM: 1 Gig 
Video Card:  nVidia GeForce 5600
Sound Card: Onboard Sound (VIA 8533 - I think)
HD: 250 + 160 IDE Hard Drive
Remote: Zapway.de homebrew serial receiver (not working) w/ harmony remote
Tuners: Hauppauge PVR-150

Performance: Forced to upgrade when I lost support on my FC4 machine this fall.  I only use standard definition at this point in time and everything worked out of the box EXCEPT for the serial IR receiver.  Thanks for the slick installer!

Can you start another thread on this issue?  I have a feeling it should be a pretty simple fix.

---

### Post by gumperoncini on 2007-10-11
**Hardware**
Dell GX260
CPU: P4 - 2.4GHz
RAM: 512mb
Video Card: Nvidia GeForce4 MX440
Sound Card: Onboard
HD: PATA 160GB 
Remote: Black Hauppage "Vista" MCE Remote (1069)
Tuners: Hauppage PVR-150


**Performance**
I installed mythbuntu (mythbuntu-7.10~071002-i386) in less than an hour and everything worked perfectly straight away. Incredible! Especially since I have spent 100+ hours trying to get this to work on 2 versions of fedora, mythdora and 2 versions of Ubuntu 6.10, 7.04.

---

### Post by propagandhi on 2007-10-11
I have two MythBoxes - the first one is here:

[B]Hardware:
CPU:[/B] Intel Core 2 Quad Q6600 LGA775 2.40Ghz 8MB L2 Cache 1066Mhz FSB 
**RAM:** 2GB DDR2 800Mhz
**DVD Drive:** LG GSA-H62N  SATA DVD Multi Drive
**Video Card:** Nvidia 8600GT 256MB PCI-Express
**Sound Card:** On Board HD audio ALC880 7.1 Ch
**Motherboard Chipset: **Intel G965+ICH8
**HDD:** Seagate Barracuda 750GB SATA HDD
**Remote: **DVICO USB MCE REMOTE
**Tuners: **DVICO Fusion HDTV5 Dual Express [/B]


**Performance**

* Need to add **irqpoll** to kernel boot parameters for normal boot, otherwise you experience either very slow boot or sometimes impossible to boot, just hangs. (tested this on 4 units i have deployed). This is something to do with the SATA setup)

* Currently have only one tuner of the dual tuners working. You have to check out the v4l-dvb latest source using mercurial, and then make and install it, then add to **/etc/modprobe.d/options** the line:

 [B]cx23885 card=4
[/B]

This gets one of the dual tuners working at present.

Other than this everything works great!

---

### Post by propagandhi on 2007-10-12
My second mythbox is here:

[B]Hardware:
CPU:[/B] Intel Core 2 Duo 2.16Ghz 
**RAM:** 2GB DDR2 800Mhz
**Video Card:** Nvidia 8600GT 256MB PCI-Express
**Sound Card:** On Board HD audio ALC880 7.1 Ch
**HDD:** Seagate Barracuda 750GB SATA HDD
**Remote: **DVICO USB MCE REMOTE
**Tuners: **DVICO Fusion HDTV Dual Digital 4 [/B]

**Performance**

* I had to follow these instructions to get the tuner card working:

[http://fremnet.net/article/228/dvico-fusionhdtv-dual-digital-4-under-linux](http://fremnet.net/article/228/dvico-fusionhdtv-dual-digital-4-under-linux)

Other than that, everything is just peachy!

---

### Post by ryanVickers on 2007-10-12
see "Gutsy install thread" in signature ;)

> **CPU:** [I]AMD Athlon 64 X2 (2.01Ghz) 3800+
[/I]**GPU: **[I]NVIDIA GeForce 7600GT
[/I]**HD(s): ***Seagate 300GB (main), and Wester Digital 8GB (secondary), and Toshiba 20GB Laptop (external)*
**Motherboard: **[I]Asus A8V-E SE
[/I]**RAM: **[I]Kingston 512MB (x2) (1GB total)
[/I]**Monitor: ***Samsung SyncMaster 940BF*
**Mouse/Keyboard:*** Microsoft Digital Media Keyboard and 'generic' mouse :wink:*

---

### Post by Tteddo on 2007-10-12
Hardware
**CPU:** Athlon XP 2800+
**RAM:** 1 Gig
**Video Card:** Radeon 9550
**Sound Card:** NVidia nForce2 with ALC650F
**HD:** 40Gig Primary 200Gig Video
**Remote:** Ati Remote Wonder RF
**Tuners:** Hauppage PVR 500


**Performance**
All working in initial install except remote (still working on it)
Initial install for one desktop, now have digital out to 1080p TV at 1920x1080, and vga out to complete 2nd desktop to another monitor to use as computer.
1 regular PS2 KBD and Mouse, and 1 MS wireless USB KBD and mouse

---

### Post by mjezell on 2007-10-13
Mythtv 2.02 Running on ubuntu 7.04 server
 
Hardware
_CPU_: AMD Athlon 64 3400+ Venice 2.2GHz 
_RAM_: Kingston ValueRam DDR SDRAM 400 (PC 3200) 4@512MB
_Video Card_: Foxconn FV-N76SM3DT GeForce 7600GS 512MG 128-bit GDDR2 PCI Epress x16 
_Sound Card_:Foxconn 761GXK8MB-RS On board Realtek ALC655 6 channel
_HD_: 1- Samsung IDE 20 Gig
               2- Western Digital SATA 500 Gig
_Remote_: Hauppauge
_Tuners_:  Hauppauge WinTV-PVR-150 PCI Interface 1045 Tuner Card

_Performance_: Had to stick with 7.04 server when I updated to .20.2 myth because of issues with using the restricted Nvidia drivers which caused myth to not see my tuner card.  Other than that it was a pretty clean upgrade.

---

### Post by budge31 on 2007-10-15
Hi all.

Heres my working setup 

Backend:

Mythbuntu 8.04
Winfast NF4UK8AA Motherboard.
Dualcore AMD 4200+
2.5 gig generic ram
7300LE Nvidia Graphics Card
640gb sata2 + 320gb sata2 +300gb sata2 +320gb PATA +320gb PATA for recordings
640gb sata2 + 500gb sata2 for Videos
1 200gb for OS and Music
2 DNTV Live! Tiny USB  Devices (2 Tuners)
1 DNTV Live! Pro Tuner
2 Fusion HDTV Tuners

Frontend 1

MSI K8 Platinum Motherboard
AMD 3200+
1 GB Ram
100GB SATA 2 Samsung 2.5 inch Drive for OS.
Onboard NIC
Nvidia  8500 GT
Sony Bravia W-Series 46"
Onboard SPDif  Out to Surround Sound Amp
Logitech Universal Remote

Frontend 2

Gigabyte 7n400L (Or something like it)
AMD Athlon 2800+
768 mb RAM
LG DVD Read/Writer
Gigabyte 7600GS Video Card Component Out to CRT TV
Onboard Soundcars SPDIF Fibre

Frontend 3
Dualboot Vista and Ubuntu (Testbox)
Intel Q6600 Quad core
4 GB Ram
Asus P5K/EPU Motherboard
8600gt Video card


Apart from my LVM becoming corrupt  due to (I think) a faulty PSU, all working, and improving with every update.

Update: I ended up taking out the 8500gt as I didn't realise that the  underscan/overscan feature was not available with the 8 series NVIDIA cards. I am outputting to a 32 inch WS CRT at the moment and the overscan makes it unwatchable.  I am now running a second-hand 7600gt I swapped for the 8500gt with a mate. Not happy, but what can you do...? Getting a 42inch LCD sometime in the near future. That should cheer me up.
Update 2: Now have my Sony Bravia 46". The 8500gt problem mentioned above is no longer an issue.
Update 3: Since Mythtv 0.21  I have dumped the LVM and moved to storage directories. I now sleep much better instead of worrying about losing all my recordings to a faulty HD.
Update 4 : Upgraded the processor on the backend from a X2 3800+ to a X2 4200+ because I had one lying around. Also upgraded from 1 gb ram to 2.5gb of ram on the backend as the backend was running out of memory under certain circumstances (not anymore).

---

### Post by pavon on 2007-10-15
_Backend:_
 CPU: Intel Core 2 Duo 6320
 RAM: 1 GB
 Video: Onboard Intel 965G
 Sound:Onboard Intel.
 Ethernet:Onboard Intel.
 HD: 250GB WD SATA 
 Tuners: Hauppauge PVR-250
 Remote:Hauppauge remote
 OS: Ubuntu 7.04
 
 Performance: Great. Wish it had TV-out so I could use it as a front end as well.

_FrontEnd:_
 CPU: VIA Samuel 2 600MHz
 RAM: 512 MB
 Video: Onboard VIA CLE266
 Sound:Onboard VIA
 Ethernet: 3c905
 HD: 2GB Flash 
 Tuners: N/A
 Remote:Windows Media Center
 OS: Mythbuntu 7.10 Beta

Performance:
Had to tweak xorg.conf file to get correct DPI, work around OSD hack.
Had to modify lircrc to get Back button working on remote.
Playback stutters on complex scenes, even after enabling (VIA) XvMC.
There is sometimes a very long (15 sec) delay in processing button presses on remote.
Performace seemed better with iMedia MythTV (had to stop using it when my onboard ethernet died, as it didn't have any other NIC drivers)

---

### Post by mynis on 2007-10-15
CPU: am2 3800+ duo core
RAM: 2 gb patriot 800mhz ddr 5-5-5-12 (pdc22g6400elk)
Video: evga 8800+ gts factory over clock (320-P2-N815-AR)
Sound:m-audio delta 1010lt
Motherboard:Gigabyte ga-m55+ s3g rev 1.0
HD: 250GB + 320 GB Seagate SATA

sound card completely nonfunctional since kernel update, no known fix. everything else works perfect!

---

### Post by Crashedfiesta on 2007-10-17
Hardware:
**CPU:** AMD XP1500 (really...)
**RAM:** 1Gb 
**DVD Drive:** Pioneer DVR-105 DVD-R Re-writer
**Video Card:** Nvidia Geforce 2 MX/MX400 32Mb
**Sound Card:** On Board AC97 thingy
**Motherboard Chipset:** Errr...not too sure
**HDD: **Hitachi 160Gb IDE
**Remote:** Hauppage Grey one
**Tuners:** Hauppage PVR-150

Performance:

Failed.  When booting from the CD my floppy drive goes into meltdown and then the installer drops back to the command prompt.  The command /sbin/modprobe failed apparently...

It's supposed to be a combined front and backend and has worked successfully(ish) with Mythdora but I've always preferred Ubuntu.

---

### Post by am_pcguy on 2007-10-20
Hardware:
ASUS P1-AH2 Barebones kit
CPU:AMD Athlon 64 4200+ X2
RAM: 2GB Mushkin DDRII 800 Dual Channel Kit
DVD Drive:  LITE-ON LH-20A1L-05 20X DVD-RW SATA
Video Card: Nvidia 6150 (onboard video)
Sound Card: On Board Azalia ALC86-DTS
Motherboard Chipset:  whatever comes with the P1-AH2
HDD: Western Digital 500GB SATA
Remote: Kworld 
Tuners: Kworld 115
Display: Panasonic AE-700 Front Projector

This is my first MythTV install.  I built the box and installed  MythTV last night.  The install was very smooth even though there don't appear to be instructions on how to install for Gutsy.  I just used the Feisty instructions as a guide.

I followed these instructions for the Kworld 115 card: [[COLOR="Blue"]LINK[/COLOR]]("http://mythtv.org/wiki/index.php/Kworld_ATSC_110")
I set up 3 programs to record and went to bed.  They were all there this morning when I got up.  This setup is playing ATSC HD very well, over the air or recorded.  I've yet to test the optical audio out, or remote.

EDIT:  The Kworld 115 doesn't provide audio on the NTSC SD Tuner.  I've followed several guides and I'm still working on the issue.  I may start a new thread requesting help on this issue.  On the ATSC side of the tuner everything is working great, recording and playback with now issues.  Also I ended up with one bad stick of ram so I'm running with 1GB until I get that replaced.

---

### Post by york2600 on 2007-10-21
**Hardware**
**CPU**: AMD Athlon 64 3200
**RAM**: 1Gb
**Video Card**: Geforce 5200FX
**Sound Card**: Soundblaster Live! Audigy
**HD**: 250GB PATA and 750GB SATA in LVM
**Remote**: Windows Media Center Remote (MCEUSB2) ( Does NOT Work  )  / iMon Pad Remote (Did not attempt to configure as I don't use it, but this probably is interfering with the MS remote)
**Tuners**: None installed (2 sitting on a shelf)
**Extra**: LCD.  iMON VFD.  No options to setup the LCD

---

### Post by besmith2@hotmail.com on 2007-10-22
Dedicated BE
Hardware : Sony Viao RS ( BEER-TAP)
CPU: 2.4 Ghz HT
RAM: 1.0 Gb
Video Card: NVidia FX-5200
Sound Card: On-board
HD: None
Remote: None
Tuners: Hauppauge PVR-150
             Hauppauge PVR-350

Dedicated FE
Hardware : Mini-itx Epia 800 (COORS-LITE)
CPU: 800Mhz
RAM: 512MB
Video Card: On-Board
Sound Card: On-Board
HD: None
Remote: None
Tuners: None

Performance:
Backend works great, frontend works good.

---

### Post by JB2007 on 2007-10-22
**Backend/Frontend**
**CPU:** Sempron 2800+
**M/B:** Basic Gigabyte
**RAM:** 512Mb RAM
**HDD:** 200Gb PATA
**Sound:** onboard
**Video:** Leadtek FX 5700 128Mb - TV out (to TV ;) )
**Tuner 1:** Happauge Nova-T DVB-T (Phillips)
**Tuner 2&3:** Dvico FusionHDTV Dual Digital 4 (new PCI version)
**Remote: **MCE Remote original Microsoft
**Software:** Mythbuntu 7.10 RC + Shepherd for Guide Data

Sydney Australia

Nova-T worked out of the box - well you need to download firmware but was too easy.
Dvico was a little more troublesome - although once the latest V4L was setup and firmware loaded - it just worked. Followed howto that everyone points to..
CPU barely hits 40% with all three cards recording... (20% is frontend process) tempted to try another Dual Digital 4 to take it to 5 tuners... and seperate the frontend from the backend + add a couple of more frontends. Have tried the Live CD frontend and it worked seamlessly. Plan to offload post processing to my Vmware machine as commercial flagging alone can chew 40% CPU...

Planned upgrade: another 1Gig of RAM + 500GB SATA drive + another dual tuner.

Mythbuntu Rocks... cheers! :guitar:

---

### Post by napsilan on 2007-10-22
Hardware
CPU: p4 3ghz
RAM: 512mb
Video Card: ATI x800xl, fglrx 42.3  (tv-out)
Sound Card: onboard ac97 
HD: 320gb sata seagate, xfs
Remote: Gyration media center remote
Tuners: PCHDTV 5500
OS: Feisty Kubuntu + mythtv backend and frontend, dist-upgraded to gutsy (still uses openbox)


Performance

TV card worked right away after picking the right driver, and it actually shows up as 4 capture cards in "input connections" because it does both analog and digital using different drivers.  Because the tv card doesn't have an onboard encoder, my cpu has to do it all.  Using the kerneldeint and denoise3d playback filters and mpeg4 encoding and xvideo, watching an analog tv file while it is still recording is smooth now.  Sound in recordings is pretty quiet, and I usually run the playback volume at max (external cord from capture card to onboard mic input, and I haven't messed with alsamixer).  Digital SD plays back fine live.  HD live playback does work when I turn off the deint and denoise filters.  The remote was instantly recognized as a keyboard and mouse, but needed keymapping, and still has 4 buttons that aren't recognized at all (stuff like the dvd menu button).  I needed to install fglrx to get TV-out working (did not try gatos).  There's a small blank space at the bottom of my TV screen, probably due to video card driver issues.

---

### Post by Meph1st0 on 2007-10-23
Just installed last night.  Hardware config is as follows:

Dell Dimension 4600
CPU: Intell P4 2.4ghz
Mobo: standard mobo for a dimension 4600
RAM: 1GB PC2700 DDR333
Video Card: Nvidia GeForce 6200
Hard drives: 2x 320 GB  (Haven't setup LVM yet but plan to thanks to the recent sticky)
Optical: DVD-RW DL Memorex and DVD+RW NEC
Tuner: pcHDTV HD-5500
Remote: Snapstream Firefly

All hardware installed without any problems.  I had to use the lircrc and lircd.conf files from mythtv.org for the firefly. After that the remote worked fine.

I also had to setup ndiswrapper for my netgear wireless card.  That was no problem either.

Mythbuntu is awesome.

---

### Post by RabidWolf on 2007-10-24
Hardware-Backend/Frontend
__________________________

CPU: P4 2.6  HT  @ 3.13
Mobo: Asus  P4C800-E Deluxe
RAM: 2048 Kingston HyperX (PC3200 DDR)
Video Card: BFGTech 7800GS OC (256) AGP
Sound Card: SB Audigy 2 Platinum
HD: 500 GB Seagate
Remote: Hauppauge
Tuners: Hauppauge-WinTV-PVR-150
Monitor: VS VX922 19" LCD @ 1280x1024


Performance
____________

I just wanted to say how smooth the install went, everything went fine, including setting up grub, thanx to the advanced option during the bootloader setup, I read through your install manual and step by step everything went perfect, taking notes on the kernel and root entries for grub before rebooting I was able to add it to my existing grub and Mythbuntu booted up fine without making me chroot in to fix my existing grub, leaving my multiboot setup intact. 

Recording works great, love the commercial skipping, still need to figure out transferring stuff from an external ntfs removable hdd into the myth install as user, will search the forums.

So far everything is performing fine, but I only watched a little TV so far. The entire install was pleasant,  polished, professional. Thanx again

---

### Post by djhedges on 2007-10-26
Hardware
CPU: AMD Athlon 2ghz
RAM: 512mb ram
Video Card: NVIDIA 440mx
Remote: pvr-150 black & gray
HD: 2 Harddrives in LVM fashion about 450gb
Tuners:
Hauppauge PVR-150

Performance
Tuner worked right out the gate.
Had to install the nvidia legacy drivers for my card to work
Used a different .lircrc file which worked much better

---

### Post by axelsvag on 2007-10-26
Hardware
CPU: AMD Athlon 64 X2 4800+ (2,4GHz) Socket AM2 65W Box
RAM: Corsair Value S. PC5300 DDR2 2048MB 
Video Card: Nvidia 7600GS Silent 512 MB
Sound Card:Onboard
HD: Samsung SpinPoint T166 500GB SATA2 16MB 7200RPM
Remote: Windows MCE Phillips new model
Tuners: Hauppage 500 MCE
Motherboard: Asus M2A-VM HDMI
Chassi: Antec Fusion V2?

Performance
Installation worked perfect if you don´t use an old CRT television. Everything works besides... Remote is recognized sometimes and sometimes not. After install of xubuntu desktop videofiles can´t be played in  xine, mplayer, vlc or totem. Audio OK but video just gives many shades of green colours. Same picture in all players. I have still not found a way to make my LCD/VFD on the chassi work. Old Feisty manuals don´t seems to work.

---

### Post by Zafrusteria on 2007-10-27
Hardware
CPU: AMD X2 +6000 (64bit)
RAM:  4 Gb
Video Card: Nvidia 8600GTS 265mb
Motherboard: Azus Crosshair
Sound Card: on the MB
HD: 3 x SATA 256 Gb Matrox
Remote: none
Tuners: none

Hardware
CPU: Athlon 32 bit 3200
RAM: 2Gb
Video Card: Geforce 68000 128Mb
Sound Card:  mother board
HD:  2 x IDE 160Gb Matrox and Seagate
Remote: none
Tuners: none

All working no problems.

---

### Post by alleycat69 on 2007-10-28
Hardware
CPU: XP2200 
RAM: 1 Gb
Video Card: Nvidia 8500GTS 265mb
Motherboard: Gigabyte
Sound Card: AC97
HD: 20GIG , 80GIG, 40GIG IDE
Remote: Hauppage 
Tuners: Nova T500, PVR 150
DVD rom - Gigabyte 


All hardware is working.

---

### Post by CaptainPatent on 2007-10-28
**_Hardware_**
_**Setup**_: Primary Backend/Frontend
**_CPU_**: AMD Athlon XP 1800+
**_RAM_**: 512 MB SDRAM
**_Video Card_**: ATI 9200
**_Sound Card_**:AC'97 Onboard
**_HD_**: 200GB Western Digital
**_Remote_**: ATI Remote Wonder
**_Tuner_**: ATI TV Wonder 200

Performance
All hardware properly detected and functional.
TV has artifacts and will skip just a couple frames. TV is still watchable but I recommend against getting a TV Wonder 200 for a MythTV box

---

### Post by evongugg on 2007-10-30
Hardware
CPU: Athlon XP 3000+ 
RAM: 1 Gb Kingston DDR-400
Video Card: Nvidia 5950
**[COLOR="Red"]Motherboard:[/COLOR]** Asus A7N8X-E Deluxe
Sound Card: Soundblaster
HD: 120GIG IDE
DVD Rom: Sony
CD-R: Lite-On

No problems. Everything works.

---

### Post by freak1 on 2007-10-31
**Hardware**
CPU: Intel Core2 Duo T7300
RAM: 2 Gb Kingston DDR-400
Video Card: Intel GM965
Motherboard: AOpen MP965-DR
Sound Card: Intel 82801H
HD: 80GB SATA
DVD-R: Sony
IR: Fintek
Network: Intel 3945ABG

**Problems:**
1) IR doesn't work. Fix is located here but unable to commit changes: [http://www.nabble.com/lirc_mceusb2.c-fintek-productid-typo-t4626593.htm]("http://www.nabble.com/lirc_mceusb2.c-fintek-productid-typo-t4626593.html")l
2) Network asks for keyring password on bootup to allow wireless to work
3) Alsa does not detect the SPDIF (tested with mythvantage using OSS and works great)
4) Had to manually install libgl1-mesa-dri to get GL to work

Great start though!

---

### Post by superm1 on 2007-10-31
> **freak1 said:**
> **Hardware**
CPU: Intel Core2 Duo T7300
RAM: 2 Gb Kingston DDR-400
Video Card: Intel GM965
Motherboard: AOpen MP965-DR
Sound Card: Intel 82801H
HD: 80GB SATA
DVD-R: Sony
IR: Fintek
Network: Intel 3945ABG

**Problems:**
1) IR doesn't work. Fix is located here but unable to commit changes: [http://www.nabble.com/lirc_mceusb2.c-fintek-productid-typo-t4626593.htm]("http://www.nabble.com/lirc_mceusb2.c-fintek-productid-typo-t4626593.html")l
2) Network asks for keyring password on bootup to allow wireless to work
3) Alsa does not detect the SPDIF (tested with mythvantage using OSS and works great)
4) Had to manually install libgl1-mesa-dri to get GL to work

Great start though!

Can you please start another thread for your issues and try installing libpam-gnome-keyring for (2)?  Also, why did you need (4)?

---

### Post by freak1 on 2007-10-31
Moved to [http://ubuntuforums.org/showthread.php?p=3677980#post3677980]("http://ubuntuforums.org/showthread.php?p=3677980#post3677980")

---

### Post by JustInterested on 2007-11-05
Using Mythbuntu Gutsy 7.10 AMD64

_Hardware_
CPU: AM2 4200+
RAM: 2G
Video Card: Onboard GeForce 6150
Sound Card: OnBoard
HD: SAMSUNG 320G
Remote: MCE USB2
Tuners: 2 x WinFast DTV 1000
Motherboard: ASUS M2NPV-VM

_Performance_
All h/w recognised and working - attached to PC LCD monitor at the moment... Need to do more reading/research to attach to LCD TV for best viewing experience (Panasonic TX-32LXD700A).

---

### Post by CCB0x45 on 2007-11-06
Just got mine completely working, everything runs perfect:

Running Mythbuntu Gutsy 7.10 i386
Dual Core Athlon 64 2.3ghz
Biostar NV770 Based HDMI Board MicroATX 
2 Gigs of Ram
Hauppage PVR-150 (Both remote and blaster works!)
Mitsubishi WD 63628 63" HDTV running HDMI Port 1 720p(after a lot of config)
Antec Fusion Silver case(VFD works, I havnt gotten the volume knob to work yet but I think it will eventually)
Encore PCI Wireless-G card(Based on RTL 8185 chipset, only works with ndiswrapper)
Also runs torrentflux and mythweb perfectly, im working on getting mythstreamtv working.

---

### Post by Balki on 2007-11-06
**_Hardware_**
Motherboard/CPU: VIA Epia SP13000 (1.3Ghz)
RAM: 512mb
Video Card: integrated on motherboard (CN400 chipset)
Sound Card:integrated on motherboard 
HD:320gb
Remote:Hauppauge
Tuners:Hauppauge PVR250


**_Performance_**
Everything auto-detected fine.  Performance is fine with auto-installed openchrome drivers.

---

### Post by e00 on 2007-11-07
_Hardware_
CPU: AMD X2 4800
RAM: 2Gb
Video Card: Nvidia 6100 integrated on mobo (Asus M2N-MX SE)
Sound Card: integrated hi-def
HD: 320Gb
Remote: Sunwave MCE USB
Tuners: Leadtek Winfast DTV1000

_Performance_
Works well. Only problems are:
[LIST=1]
[*]Setting up a video resolution appropriate for a hi-def plasma connected via VGA
[*]Getting the remote to work sufficiently that I won't need a keyboard (some functions work, some don't)
[*]Finding EPG source for Australia
[/LIST]

---

### Post by linuxlibrarian on 2007-11-12
Hardware
Athlon 64 Socket Am2 2.4 ghz Orleans 
Biostar TForce 7050pv M2 motherboard
1 gig Corsair DDR2 RAM
250 gb Western Digital SATA Hd
Hauppauge PVR150 MCE Vista Edition (the usb blaster/xmitter with the Black MCE remote. PVR 150 PCI card)
Nvidia (integrated on motherboard) 7050 graphics using nvidia-new drivers  (proprietary)
Zonet wireless card
DVD drive
Antec case/380 psu


Performance:

Everything works great (finally).

Using with a DirecTV Philips DSX5250 STB and an RCA CRT Television. Channel changes, scheduled recording, everything works. Even remote.

Main issues that may or may not bother someone with this set up: Prebuffering pauses on the Hauppauge card causes a few fits and starts and jitters. Not bad, and not too annoying, mainly because our television isn't terribly good either. I suspect altering pci latency, increasing buffers, and possibly changing the channel frequencies might help this a bit. (I seem to do better with "us-cable" than "us-bcast" when using DirecTV, even though it technically *is* an antenna.)

A good, low budget set up though... esp. recommend if you don't have a top of the line TV and no plans to upgrade the TV in the near future.

---

### Post by old_salt on 2007-11-13
Hardware - HP Dv9000z 
CPU:AMD Turion64 x2
RAM:2Gb
Video Card:nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
Sound Card:nVidia Corporation MCP51 High Definition Audio (rev a2)
HD:
NIC: nVidia Corporation MCP51 Ethernet Controller (rev a3)
Remote:
Tuners:

Other: 
- Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
- FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
- Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
- Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
- Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
- Ricoh Co Ltd xD-Picture Card Controller (rev 05)
- PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
- nVidia Corporation MCP51 USB Controller (rev a3)
- Matsushita Lightscribe DVD/RW-DL



Performance
Fair to midland. 

Top Output on Gutsy install using 64bit Install--------------

Tasks: 128 total,   2 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.0%sy,  0.0%ni, 77.0%id,  0.0%wa, 62.8%hi,  0.0%si,  0.0%st
Mem:   1998036k total,  1008836k used,   989200k free,    82048k buffers
Swap:  4208988k total,        0k used,  4208988k free,   526892k cached

The Hardware interrupts are unusually high and USB 2.0 is inoperable and must remove the uhci in order to get USB ports operable at all.

---

### Post by stinger30au on 2007-11-13
Hardware
CPU: Intel pentium4 3 Ghz Prescott
RAM: 1.0 gb ram
Video Card: NVIDIA Geforce 2 64megram
HD: 2 x 40 gig ide and 1x80gig sata
Audio:Onboard


Performance
All hardware properly detected and functional.
This includes my HP Deskjet 1120C colour printer and my Canon Lide20USB Scanner.

Had to install nvidia proprietary drivers by clicking on the "restrited drivers"tab when 7.10 started.it restarted and all is ok

Performance
Runs very sweet and silky smooth. Did a format and fresh install after backing up my data

---

### Post by billionmonkeys on 2007-11-15
Hardware
CPU: amd64 3500
RAM: 1gb
Video Card: nvidia geforce 7100 GS, connected to NTSC tv via s-video, using nvidia binary driver
Sound Card: onboard nvidia audio
HD: sata
Remote: hauppauge
Tuners: hauppauge 350 and 250

Problems:
1. Cannot run install while system is connected to a TV.  The resolution used by the installer is not tv-out compatible.
2. using the default mythbuntu theme, it is almost impossible to tell if a checkbox in the setup menu is selected or not on my tv.
3. commercial skip doesn't seem to work.  I haven't investigated this problem yet.
4. picture quality issues when watching hockey games on this system.  (noticible jumpiness when the camera pans across the ice).  not sure if this is a playback issue or an issue with capturing.  Tried messing with the quality settings to no avail so far.
5. hauppauge remote settings not good
6. overscan-related issue - if you narrow down the screen resolution on the config page (so all the menus fit on the screen) you will have problems with the underlying window manager putting the menu bar on top of the myth screen.
7. would be nice if the driver for the lcd device was installed/configured by default.
8. have both the hauppauge remote and a (useless) imon remote.  i chose the hauppauge in the install screen but it automatically seems to support them both out of the box, I had to manually update the lirc config in /etc since /dev/lirc0 seemed to be allocated to the imon.

---

### Post by Limulf on 2007-11-15
_**Hardware**_
**CPU: **Intel Core 2 Duo T7250 2x2GHz
**RAM: **2 Gb DDRII SDRAM
**Video Card: **NVIDIA GeForce 8600M GT 
**Sound Card: **integrated
**HD:** Toshiba MK2035GSS ([link]("http://sdd.toshiba.com/main.aspx?Path=HardDrivesOpticalDrives/2.5-inchHardDiskDrives/MK2035GSS/MK2035GSSSpecifications"))
**Remote: **RC115V([link]("http://www.edio21.com/prod_rc115v.asp#"))
**Tuner: **[FONT=Arial][SIZE=2]PRO-NETS DM100A ([link]("http://www.pro-nets.com/eng/product.php?mode=show&cid=109&pid=143"))
**Webcam**: Bison 1.3 MegaPixel Digital Camera
[/SIZE][/FONT] 

_**Performance**_
Ubuntu 7.10 64bit. Installed without problems, and works quite well, except the following issues:
 1) The famous [load/unload cycles issue]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/"): after some testing, I found that ```
$ sudo hdparm -B 192 /dev/sda
``` solves it.
 2) Webcam is not detected
 3) Remote is not detected.
 4) Tuner is not automatically detected. As in WindowsXP the drivers the vendor gave me configure this card as if it were an "AF9015" I have tried installing the kernel modules from _[here]("http://linuxtv.org/wiki/index.php/Afatech_AF9015")_. Problem is that, when I scan for stations, I find no one.
 5) Suspend / hibernate do not work, computer shuts down instead.
 6) Screen's brightness control performs weirdly, if I set brightness below 15% it goes back to full intensity instead.
 7) Screen is blank during startup, until login box appears. This can be inconvenient for new Ubuntu users, who don't know that once in a while there will be a hard disk scan. As they don't see a thing, they could try to reboot the computer before it finishes it.


Thanks for your kind work.

---

### Post by budge31 on 2007-11-16
> **e00 said:**
> _Hardware_
CPU: AMD X2 4800
RAM: 2Gb
Video Card: Nvidia 6100 integrated on mobo (Asus M2N-MX SE)
Sound Card: integrated hi-def
HD: 320Gb
Remote: Sunwave MCE USB
Tuners: Leadtek Winfast DTV1000

_Performance_
Works well. Only problems are:
[LIST=1]
[*]Setting up a video resolution appropriate for a hi-def plasma connected via VGA
[*]Getting the remote to work sufficiently that I won't need a keyboard (some functions work, some don't)
[*]Finding EPG source for Australia
[/LIST]

Did you get your epg working?

I use Shepherd, and it hasn't missed a beat since I set it up.

[http://svn.whuffy.com/index.fcgi/wiki](http://svn.whuffy.com/index.fcgi/wiki)

---

### Post by twkisner on 2007-11-18
Hardware
CPU: AMD Athlon 64 3000+
RAM: 1gb
Video Card: AGP nvidia 6200 component out
Sound Card: built in (I forget)
HD: Sanyo Vizon HDTV (4:3)
Remote: Firefly mini 
Tuners: 3 Air2PC PCI ATSC cards (2 first rev., 1 Second rev.)


Performance

I have to manually install the drivers for my tuner cards (even though they are on the supported list on the install document).  I had to go to Fiesty hardware install directions to get them working (-should someone move those over?)

I'm changing remotes to the Firefly mini.  I'm going to have to manually key-map it, but when I do I intend on posing a guide.  The one on the mythtv wiki for Fedora sounds silly to me.

*Update* I used Xmodmap to remap the keys.  Right now use the "run on startup" feature to run a script that does it when the GUI loads, but does anyone know the proper way?

---

### Post by mdkendall on 2007-11-20
Hardware
CPU: Intel Celeron D 430 (1.8GHz)
RAM: 1GB DDR2
HD: 500GB Seagate Barracuda SATA
Motherboard: Shuttle SG31G2
Video Card: NVIDIA 7200GS, 256MB
Video Capture: Hauppauge PVR-150 MCE
IR Transceiver: SMK RXX6000 USB-attached transceiver (supplied with PVR-150), mceusb2
IR Remote: MCE remote, 1069-type (black) (supplied with PVR-150)

Performance
All hardware properly detected and functional.

I am using the NVIDIA proprietary drivers. I installed the software and set the system up using an LCD monitor, then changed to a (standard definition, NTSC) TV attached to the S-video out of the video card. TV-out works fine regardless of the screen resolution, but it seems to me that things look best with the resolution set to 800x600.

Using mceusb2 the IR transceiver received the associated remote and controlled Myth with no further setup. After I added the definitions for my set-top box remote to lircd.conf and added a channel changer script I was also able to use the transmitter functions without problem.

Shuttle SG31G2 fans (PSU and CPU) are very quiet; I am very pleased.

Hard drive noise is distracting; it is actually fairly quiet but the constant ticking of the heads during recording is distracting. I am going to try some rubber isolation mounts.

Using the default Mythbuntu theme I bumped the font sizes up about 4pt each (from 12pt, 16pt and 25pt to 16pt, 20pt, 30pt IIRC) and the configuration screens are now much more readable on my SD TV. I agree with a previous comment that the 'checkbox' widget in this theme is terrible. The checked and unchecked state are an embossed or debossed square respectively (and its is not clear which way round that would be even if you could see it) which are distinguished by dark blue and slightly-darker blue shading. It is practically unusable on a SD TV.

I thought the Celeron might be underpowered and was prepared to have to change it, but actually it is doing fairly well. I see no recording or playback issues. Load average during recording is less than 0.1 (as would be expected given the hardware MPEG encoder) and during concurrent recording and playback it runs around 0.4.

---

### Post by roseway on 2007-11-20
**Hardware**
CPU: Athlon 64 X2 4000
RAM: 2 GB Kingston
Video Card: Onboard nVidia 6150
Sound Card: Onboard ADI 1986A
HD: Western Digital 5000AAKS SATA
Remote: Hauppauge Nova-T
Tuner: Hauppauge Nova-T PCI (conexant version)

**Performance**
Everything worked correctly out of the box except the remote control. I set up the RC using the guide at [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Remote_control](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Remote_control) plus extra information at [http://ubuntuforums.org/showthread.php?t=183545&highlight=nova](http://ubuntuforums.org/showthread.php?t=183545&highlight=nova)

---

### Post by superm1 on 2007-11-20
> **roseway said:**
> **Hardware**
CPU: Athlon 64 X2 4000
RAM: 2 GB Kingston
Video Card: Onboard nVidia 6150
Sound Card: Onboard ADI 1986A
HD: Western Digital 5000AAKS SATA
Remote: Hauppauge Nova-T
Tuner: Hauppauge Nova-T PCI (conexant version)

**Performance**
Everything worked correctly out of the box except the remote control. I set up the RC using the guide at [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Remote_control](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Remote_control) plus extra information at [http://ubuntuforums.org/showthread.php?t=183545&highlight=nova](http://ubuntuforums.org/showthread.php?t=183545&highlight=nova)
Can you please file a bug against mythbuntu with any specific changes that you had to make.  We can attempt to address them and have out of the box support for Hardy.  Thanks!

---

### Post by roseway on 2007-11-20
Will do (when I've found out how to :) )

---

### Post by superm1 on 2007-11-20
> **roseway said:**
> Will do (when I've found out how to :) )
[https://bugs.launchpad.net/mythbuntu/+filebug](https://bugs.launchpad.net/mythbuntu/+filebug)

---

### Post by roseway on 2007-11-20
Thanks. I see that there's already a bug report dealing with this, so I've simply subscribed to it and added a comment.

---

### Post by Nikas on 2007-11-21
_**Hardware**_
**CPU:** AMD64 3200+, 2200 Ghz
**RAM:** 1.0 gb ram
**Video Card: ** cheap NVIDIA-card.
**Remote****: **None
**HD:** 40 gb sys disk. 250 gb for recordings and live tv.
**Tuners:**
2 x Hauppauge WinTV Nova T-500 = 4 dvb-t tuners total.
[U][B]Performance
[/B][/U]All hardware properly detected and functional.
Added latest firmware and updated the v4l-dvb-drivers.
Got "I2C read error" with IR-cable connected but I'm using the computer as server only so i dont need to have the ir-cable connected.

---

### Post by spinlock99 on 2007-11-23
_**Hardware**_
**CPU:**
**RAM:**
**Video Card: **
**Sound Card:**
**HD:** 
**Remote:**
**Tuners:** Hauppauge WinTV (using bt878, bttv, and tuner linux modules)

**Performance:**Using a standard Mythbuntu install I have been able to watch tv using xawtv with **_no_** recompiling of kernel modules.  It just worked out of the box!!!  I have gotten MythTV to play TV using the V4L Capture Card and _not_ the MPEG2 as it says in the manual.

---

### Post by The Odometer on 2007-11-24
Hardware
CPU:AMD Athon XP 2200+
RAM:512 MB DDR
Video Card: Chaintech Geforce FX 5200 128 MB
Sound Card:Onboard Nforce2
HD:250 GB
Remote:MCE Remote
Tuners:Hauppauge Win-TV PVR 150 MCE


Performance:
Worked right out of the box. Had a few problems with TV Out-but they were fixed easily. Thanks for a great distro!

---

### Post by kameleon25 on 2007-11-24
Hardware
CPU: AMD 64 4600+ x2 65W
RAM: 1.0 GB (512x2) A-data ADQVE1908K PC6400 Ram
Video Card: Onboard ATI Xpress 1250 connected via HDMI
Remote: Streamzap pc remote
HD: 160GB SATA
Tuners: Firewire to Scientific Atlanta 8300HD DVR Comcast box
Motherboard: Gigabyte GA-MA69GM-S2H
Performance: Mostly worked out of the box. Much easier to deal with than the manual mythtv install I had previously.

Had to install Ubuntu 7.10 from cd first then install the mythbuntu control center. My hardware had issues with booting into the graphical interface using the mythbuntu 7.10 disk. Got it all installed and then had issues with the ATI Xpress1250 chipset to display 1080p properly on my Sharp Aquos 42" LCD. Had to remove the restricted fglrx driver and then reboot the pc with the sharp turned on and tuned into the HDMI port. Worked like a charm. I previously had this running on ubuntu 7.04 but something happened and it all crashed. Found mythbuntu and decided to install that. 
The only issues that remain is my streamzap remote and the firewire to the comcast box. The streamzap actually "works" as far as selecting and navigating the menus. But it does not work for manipulating the video stream. The firewire is an issue in itself. I have not really delved into that fully yet but if anyone has any pointers they are appreciated.

---

### Post by pasta514 on 2007-11-25
BACKEND
Hardware
CPU: AMD BE-2300 45W
Motherboard: Abit AN52
RAM: 2x2GB Crucial
Video Card: ATI Radeon X600
Sound Card: n/a
HD: 1x160GB Maxtor & 1x500GB Maxtor
Remote: n/a
Tuners: ATI HDTV Wonder

Performance
Had to download the DVB firmware for the HDTV card.
Want to use this as a samba server as well, so was hoping to mirror the 160GB disk with 160GB partition on the other disk with RAID/LVM, then use the remaining disk space in non-RAID. So far no luck.  Maybe the samba server will sit on another machine.

FRONTEND
Hardware
CPU: AMD AthlonX2 6000+
Motherboard:  Abit AN-M2HD nForce 630a
RAM: 2x2GB Crucial
Video Card: GeForce 7050PV
Sound Card: Realtek?   MPC67/ALC883  7.1 HD Audio
HD: 160GB Maxtor
Remote: WinMCE USB
Tuners: n/a


Performance
connected to Sharp Aquous through HDMI.  No Audio through HDMI; known nvidia driver issue.  Have not had time to check out other audio options yet.
Significant overscan on the screen.  Also a driver issue.  Overscan should be OK for media, but problematic for running a linux desktop.  Have tried to debug without success.

---

### Post by e00 on 2007-11-27
> **budge31 said:**
> Did you get your epg working?

I use Shepherd, and it hasn't missed a beat since I set it up.

[http://svn.whuffy.com/index.fcgi/wiki](http://svn.whuffy.com/index.fcgi/wiki)

Tried to set up Shepherd. Seemed to set up ok, except for waiting 20 minutes or so for it to download data (over cable!). But it didn't properly update the guide database so recording via EPG didn't work at all.

Don't really have time to debug it, so disabled it. Recording works fine using manual record or the station's transmitted guide.

---

### Post by williammanda on 2007-11-27
Hardware
CPU: Intel Core 2 Duo 6400
RAM: 2 GB
Video Card: Nvidia 7300 le 512 MB ram PCIe
Sound Card:: Onboard sound  - ADI AD1986A
HD: 250 GB
Remote: Snapstream Firefly RF
Tuners: pcHDTV HD-5500 & Dvico FusionHDTV5 Gold **Updated 1/5/08**
Monitor: Westinghouse W4207 42"

Performance
Everything worked correctly out of the box except the Nvidia restricted drivers had to be updated to ver 169.04. I use Xine outside of mythtv. **Update 1/5/08** Using the Nvidia driver 169.07.

Hardware
CPU: AMD Dual Core 4200
RAM: 2 GB
Video Card: Nvidia 7300 gt 512 MB ram PCIe
Sound Card: Onboard sound  - ADI AD1986A
HD: 250 GB
Remote: Snapstream Firefly RF
Tuners: Dvico FusionHDTV5 Express (PCIE version)** Updated 1/5/08** I had to get the latest linuxtv drivers to use the pcie card since kernel 2.6.22.14 doesn't support it.
Monitor: LG 42LC7D 42"

Performance
Everything worked correctly out of the box except the Nvidia restricted drivers had to be updated to ver 169.04. I use Xine outside of mythtv. **Update 1/5/08** Using the Nvidia driver 169.07.


Hardware
CPU: Intel P4 HT 3 Ghz
RAM: 1 GB
Video Card: ATI X1650t 512 MB ram AGP
Sound Card: Onboard sound  - AC 97
HD: 160 GB
Remote: none
Tuners: Hauppauge PVR-150
Monitor: Viewsonic VA520 Analog 15"

Performance
Enable restricted drivers for the ATI video card. Mythtv playback for SDTV is ok.  Digital tv is choppy. Xine media playback of SDTV is ok but digital playback gives a message " the amount of dropped frames is to high". I am using the xshm driver since xv will not work with the ATI card. Any ideas?
**Update 12/23/07**
I've since removed the ATI card and used the onboard video Intel 82865G and all video works fine even HD. Anyone want an ATI card

---

### Post by umggc on 2007-11-29
Combined Front/Back End:

CPU: AMD Turion ML-30 (socket 754)
MB: MSI K8MM3-V (VIA K8M800 VT8237R)
RAM: 1 GB DDR 400
GPU: GeForce 6200 128 MB

Tried 2 tuners: 

Leadtek Winfast TV2000/XP Expert: works. Set as software v4l card, using mpeg4 in recording profile, adjusted ALSA setting to use aux audio; 

ADS PTV 305 (same as KWorld MCE-TV 200): not working. Had to manually type in device name in hardware encoder card setup to recognize, channel scan worked, live TV went black screen than nothing. Probably because IVTV driver does not support blackbird cards.

---

### Post by gnickm on 2007-11-29
CPU: VIA C3/EDEN
MB: VIA EPIA-M10000 Fanless
RAM: 512MB DDR
GPU: Integrated VIA CastleRock AGP w/TV out

Used as a video playing front-end, so no tuners. Absolutely no problems installing or running, Mythbuntu 7.10 "just worked" right off CD.

---

### Post by spalVl on 2007-12-09
CPU: Athlon XP1800
MB: SOLTEK SL-75DRV5 Socket A (Socket 462) VIA KT333 ATX AMD 
RAM: Kingston ValueRAM 512MB 184-Pin DDR SDRAM DDR 266 (PC 2100)
HDD: Maxtor DiamondMax Plus 9 6Y080L0 80GB 7200 RPM IDE Ultra ATA133 Hard Drive
GPU: nVidia GeForce4 MX 440 AGP (S-Video out)
Sound 1: Integraded VIA Technologies, AC97 Audio Controller (Disabled)
Sound 2: Chaintech AV-710 (Optical out)
PS: Generic 300w PS
CD: CDRW 24X10X40|SONY CRX175
Tuner: Leadtek Winfast TV2000XP Deluxe tuner NTSC

Had to connect it to a VGA monitor to get  installed.  After that setup restricted Nvidia driver and hooked to TV.  
Used custom modeline migrated from Knoppmyth with video settings for TV.

Ran into the VNC CD needs to be inserted to enable problem.

Ran into the MythWeb password problem resolved with post from this forum.

Audio: Had to change to /dev/adsp in Setup>General and enable AC3/DTS to SPDIF.
Mplayer needed /etc/mplayer/mplayer.conf audio section modified with audio options.

[COLOR="Blue"]ac=hwac3,hwdts,
ao=oss:/dev/adsp[/COLOR]

Been unable to get the remote working appended to this post.
[http://ubuntuforums.org/showthread.php?t=610426](http://ubuntuforums.org/showthread.php?t=610426)

Great distro, REALLY like Mythbuntu Control Centre and the lightness of XFCE, plus is easy to switch to Mythbuntu SVN repository.

---

### Post by Brando569 on 2007-12-10
**_Hardware_**
CPU:AMD Athlon 64 x2 4200
RAM: 2x512mb Kingston HyperX DDR400
Video Card:Nvidia 7600GT and/or 8600GTS OC
Sound Card:onboard nvidia (realtek?)
HD:WD 5000KS 500GB Sata II 16mb cache

**_Performance_**
kubuntu runs great on my system, well with the exception of compiz-fusion screwing up randomly (no borders, freezing). the only problem that i have is when i have my 8600GTS in it doesnt display the kubuntu splash screen.

---

### Post by milhouse on 2007-12-17
**_Hardware_**

CPU: Athlon 64 3000+
MB: ASUS K8V-SE Deluxe
RAM: Kingston HyperX 512MB 184-Pin DDR SDRAM
HDD: Seagate 120GB 7200 RPM IDE Ultra ATA133 Hard Drive
GPU: nVidia GeForceFX 6600 AGP (S-Video out)
Sound: Integraded VIA Technologies, AC97 Audio Controller
Tuner: DViCO Fusion HDTV 5 RT Gold

**_Performance_**

Installed 7.1 w/o issue.  Tuner card recognized and configured both analog and digital tuners easily.  Installed nVidia restricted drivers using the restricted drivers manager.  Display on both my 20" LCD monitor during setup and 4:3 CRT TV via s-video for use was flawless.

Setup suffers from the "pink screen of death" and will upgrade nVidia drivers to solve this.

Digital tuner works fine.

The analog tuner on the FusionHDTV 5 has audio problems.  There is some very loud static for 2 or 3 seconds then an audio bitrate mismatch when you switch from a digital to analog station.  Changing again to another analog station usually fixes the issue.  Not a workable solution for unattended recording.  Fixes may be out there, I just didn't need the analog tuner so stopped trying.

---

### Post by voctikal on 2007-12-22
Hardware

Case  	 nMEDIAPC HTPC 300BA
Mobo  	 BIOSTAR TForce TF7050-M2 AM2 NVIDIA GeForce 7050PV HDMI Micro ATX AMD Motherboard
CPU  	 AMD Athlon 64 LE-1600 2.2GHz Socket AM2 45W Single-Core
PSU  	 COOLER MASTER eXtreme RP-500-PCAR ATX
RAM  	 A-DATA 1GB (2 x 512MB) 240-Pin DDR2 SDRAM DDR2 800
Game Controller  	 Logitech 963326-0403 Cordless RumblePad 2 USB
Remote      Streamzap Remote
HDD      Seagate Barracuda 7200.10 320GB 7200 RPM SATA 
Optical    Sony NEC Black 20X DVD+R 8X DVD+RW

Almost forgot the 52 inch big screen

---

### Post by dougsnell on 2007-12-23
**Hardware** - Wal-Mart Everex TC2502 (with new HD)

CPU: 1.5 GHz VIA C7-D
RAM: 512 Mb DDR2
Video Card: (not used) on-board VIA UniChrome Pro
Sound Card: (not used) on-board
HD: 250 Gb (WD, I think)
Remote: Hauppage 350 (4 color buttons on bottom)
Tuners: Hauppage 500 and Hauppage 350

**Performance**

Runs Mythbuntu.  Virtually no overhead on processor, very low-watt consumption.  Had problems getting everything working with the 350 TV-out, but the new Gutsy howto was perfect.

... and it works a lot better than it did under Windows with BeyondTV :)

---

### Post by JeepFreak on 2007-12-24
[SIZE="4"]**Hardware**[/SIZE]
**CPU:** Intel Pentium D 925 3 GHz Dual Core
**Motherboard: **Intel DG965WH Media Series
**RAM: **1GB Kingston PC2-6400 DDR2 DIMM 240-pin 800MHz Non-ECC
**Video Card: **ASUS EN7300LE/HTD/128M GeForce 7300LE Supporting to 512MB(128MB on BoarD) 64-bit GDDR2 PCI Express x16 
**Sound Card:** On Board
**HD:** Western Digital Caviar SE16 250GB 7200 RPM SATA 3.0Gb/s
**Remote:** Soundgraph iMon Pad
**Tuners:** Hauppauge WinTV-PVR-500
**Case:** Silverstone GD01MX

[SIZE="4"][B]
Performance[/B][/SIZE]
I just installed Mythbuntu 7.10 and the system works remarkably well right out of the box.  The remote is flakey and needs configuring.  The card readers on the front of the case do not work (actually... I only know that they do not autodetect media).  And, of course, the iMon LCD does not work.

Overall... I am very impressed with Mythbuntu!! I can't believe I've been putting this project off for almost a year!  

Thanks,
Billy

---

### Post by ozybushwalker on 2007-12-28
**[SIZE="4"]Hardware[/SIZE]**
**CPU:** Via C3 1GHz on GA-PCV2 Mini ITX mother board
**RAM:** 256MB
**Video Card:** On board in VIA CLE-266 Chipset
**Sound Card:** AC97 On board in VIA CLE-266 Chipset 
**HD:** Seagate 80GB PATA
**Remote:** included with Tuner
**Tuners:** Leadtek Winfast DTV1000 T 


**[SIZE="4"]Performance[/SIZE]**
The tuner has DVB (Digital) facilities with composite video input. I haven't tried the remote or the composite video input yet. The digital tuner works well but it took me a while to figure out how to configure it correctly. Perhaps if I had read the installation manual it might have been a bit clearer.

I tried to get a suitable EPG but there was no option for Australia in the setup script. I found the shepherd EPG but ran into trouble getting it going because there were insufficient perl modules. I tried to follow the shepherd installation procedure at [http://svn.whuffy.com/index.fcgi/wiki/Installation]("http://svn.whuffy.com/index.fcgi/wiki/Installation")
but it reported a missing perl module and I haven't yet tried to rectify that.

Overall, I'm very pleased with what I have seen so far. Thanks Mythbuntu team.

My initial euphoria has soured with experience. Because I saw some swapping and jerky video I upgraded the memory to 512MB but that didn't fix the jerky video problem. After investigation (described in my bug report at
[https://bugs.launchpad.net/mythbuntu/+bug/179634]("https://bugs.launchpad.net/mythbuntu/+bug/179634")
I got better performance by editing /etc/X11/xorg.conf and adding the line **VideoRam 16384** to the device section.

---

### Post by AlecJ on 2008-01-11
Hardware MSI K9N6GM
CPU: Amd 64 x2 4400
RAM: 1Gb
Video Card: Nvidia FX 7300 GS
Sound Card: on board Nvidia ALC883 7.1  (not working as 7.1 yet)
HD:Maxtor 160Gb
Remote: Nova-T 500 grey snow board type
Tuners: Kworld expert (works from the box (crap remote))
Nova-T500 (have to follow [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)
for Mythbuntu to find it.


Performance
Works Great!
Still trying to get 7.1 working

---

### Post by ian dobson on 2008-01-17
Backend:-

Intel Q6600
2Gb ram
RAID 5 array (4x500Gb SATA)
1Gbit network
PVR 150 analog tuner
Running 7.10

Frontend
Intel C2D 2140 
Gigabyte G945 motherboard
512Mb ram
40Gb 21/2 harddisk
Nvidia G7300 graphic card
SABA TV (Now this feels strange in a PC spec)
PVR 150 remote control + homebrew IR input (see 5)
TV running off S-VIDEO port as PAL-B at 1024/768 (Need to change this sometime).
Running 7.10/Mythbuntu

Problems:-
1) The backend doesn't have an X server so getting myth-setup working took abit of work.
2) The AL1 network card has a problem with > 4Gb ram so I only have 2Gb at the moment
3) The PVR 150 recordings where far too quiet until I increased the recording volume in MythTV 
4) The TV out isn't 100% OK. Bright colours are abit "smudgy". I think that the luminance signal is abit too high. I'll try making a new cable sometime.
5) Mythbuntu doesn't support "home brew" adapters from the setup screen, I had to say I had a PVR 150 remote then manually reconfigure LIRC to use the Serial driver and disable the serial port in the Kernel using setserial.

The WAF (Women acceptance Factor) is quite good. My wife has started using MythTV even though I'm still fixing afew hardware bugs and the system isn't really "on-line". Mythweb makes everything much easier. I have a normal harddisk recorder and it's a pig to work with (User interface is slow /unresponsive, EPG doesn't always work)

Regards
Ian Dobson

---

### Post by Mrbbad on 2008-01-20
[SIZE=5]**Hardware**[/SIZE]
**Motherboard**: BIOSTAR TForce TF7050-M2 AM2 NVIDIA GeForce 7050PV HDMI Micro ATX AMD Motherboard
**RAM: **1Gig (4 sticks of 256MB RAM)
**CPU: **AMD Athlon 64 X2 4000+ Brisbane 2.1GHz Socket AM2 65W Dual-Core Processor
**Network: **GIGABYTE GN-WP01GS PCI Wireless Adapter 
**TV Tuner: **SABRENT TV Tuner / Video Capture / MPEG Recording PCI Card with Remote Control TV-PCIRC PCI Interface
**HD: **40Gig Barracuda 
**Remote: **TSHA IR01 (Example [here]("http://www.directron.com/hair01sv.html"); didn't buy it from them, that is just a view of the remote.) 

[SIZE=5]**Comments**[/SIZE]
Sound & video are on the motherboard.  Ran sound out of TV Tuner to Motherboard and then to the TV.  Hard-coded (how annoying) the system so Mythbuntu would stop asking me for the wireless password on boot to access the Internet.

[SIZE=5]**Problems**[/SIZE]
Had to use 'low graphics mode' during install because the on-board video was not supported.  Downloaded, installed, compiled (didn't do this part myself, worked on this with a friend) appropriate NVIDIA drivers (annoying).

I **[COLOR=Red]*do not*[/COLOR]** recommend the motherboard I got currently (though it is AWESOME!) for those building their own systems -- not until the on board video card is supported by the installer for sure.

The remote that came with the TV Tuner did not work, bought the above listed one instead and it worked perfectly. 

Some stations have this green fuzzy line at the bottom -- it's easy to ignore since the line is quite small; but we couldn't find a way to remove it.

40GIGs of space is no fun, will have to add another HD in the future.

[B][SIZE=5]Current Status[/SIZE]
[/B]After a 24 hour marathon, somehow, someway, we got it working, it is now recording and playing standard definition cable TV very well.

If for some reason anyone has a question about any of that, please PM me.

---

### Post by Chuckels550 on 2008-01-30
**Hardware**
CPU - Slot 939, AMD Athlon64 3500+
RAM - Corsair 4x512 GB DDR, 400 MHz FSB, CAS 2.5, TWINX Value
Mobo - MSI K8N Neo2 Platinum (MS-7025)
Hard drives - ATA 133 Maxtor 250 GB 16 MB Buffer and SATA II Western Digital 750 GB 16 MB Buffer
DVD Burner - LG GSA-H10A 16x Super Multi DVDRW/CDRW
Soundcard - Creative Labs Soundblaster Audigy X-Gamer - used for TV-Out
Graphics - Asus Nvidia N7600GS, TV-Out DVI, 256 MB DDR, AGP 8x Silent (fanless) - I use the graphics card TV-Out
Wireless NIC - Dlink DWL-G520 High Speed 2.4GHz (802.11g) Wireless PCI Adapter, Rev B
TV Tuners - Hauppauge WinTV PVR 350, model 990 (NTSC tuner) and Hauppauge WinTV PVR 150, model 1045 (NTSC tuner) - both used only for capture, but I use the WinTV PVR 350 remote with LIRC.
Keyboard/Mouse - Microsoft Wireless Laser Desktop 6000
Display - Sharp 32" LCD TV set to Digital A/V (no monitor)

**Cabling the TV Tuner, Sound Card and TV**
**Additional cables required:**
[LIST]
[*]Coaxial Cable Splitter and coaxial cable for connections to LCD TV, WinPVR 350 TV Tuner, WinPVR 150 TV Tuner
[*]Audio patch cable, short as possible, (for connection between the TV tuner card and sound card)
[*]DVI cable (for connection between the LCD TV and the Graphics Card
[*]Audio cable with small headphone jack (for connection between the soundcard and the LCD TV
[/LIST]
**Note: ** The WinPVR 150 does not need to be connected to anything other than the cable TV input.
[LIST=1]
[*]Connect one cable TV coaxial cable to the Hauppauge WinPVR 350 connector and one to the Hauppauge WinPVR 150 connector on the back panel.  The top coaxial connection on both TV tuners is for cable FM, which I don’t use.
[*]Connect the Hauppauge IR receiver to the WinTV PVR 350 back panel IR receiver connection.
[*]Using a audio cable with the small headphone jacks, connect the Audio Line Out on the sound card to the LCD TV audio input for the DVI connection.
[/LIST]

**Comments:  **
Everything listed works and works well for me at 720p
I configure storage using LVM2.  
I had problems with Network Manager, with getting the cabling to the correct audio out jack on the soundcard and with configuring alsamixer.  
[LIST]
[*]Network Manager has never worked well for me and I would love to see it disappear from Ubuntu releases.  When it broke this time, I uninstalled it and installed/configured Wicd instead.  Wicd has no problems with maintaining static IPs, which is a requirement for MythTV and has proven very reliable as well as easy to set up.  
[*]I found it confusing to decide where the correct line-out jack was for my soundcard, but once I realized that the Analog/Digital line out was used for the subwoofer in a 5.1 set-up I was able to find the correct line-out to use.  
[*]Setting up alsamixer was by guess and by gosh.  For my soundcard, if the Analog/Digital line out Jack is on, nothing works.  The settings in MythTV were ALSA: default and default.
[/LIST]

---

### Post by stdPikachu on 2008-01-31
> **Chuckels550 said:**
> 
For my soundcard, if the Analog/Digital line out Jack is on, nothing works.  The settings in MythTV were ALSA: default and default.

IIRC this is the same for every Audigy. In addition, if they're anything like mine you won't be able to mute the master or PCM channels either. I filed a bug report with ALSA about this ages ago but still don't think it's been incorporated upstream.

---

### Post by kreegor on 2008-02-07
**Hardware**
**Motherboard:** Gigabyte P31-S3G
**CPU:** C2D E2160 (stock)
**RAM:** 1 Gig DDR2 667 (generic)
**Video Card:** POV 256MB nVidia 8400GS
**Sound Card:** Onboard
**HD:** 160Gig Western Digital
**Remote:** Dvico FusionRemote MCE
**Tuners:** DVICO (Ultraview) Fusion HDTV DVB-T Plus

**Problems**
[LIST]
[*]Some remote buttons were not configured properly. Simple change in the lircrc file.
[*]Sound was very quite. Had to install Alsamixergui to boost the sound
[*]Accessing a Samba share crashes my Windows machine. No idea why just yet :)
[/LIST]

**Performance**
Installation was simple, tuner card worked out of the box and remote worked from install. This machine has no trouble displaying high quality video. Recording quality is great and playback is really smooth.

Overall, I am more than happy with it!

---

### Post by solitaire on 2008-02-07
[B]Hardware
Motherboard:[/B] Dell Inspiron 8200 Laptop
**CPU**: P4m 2Ghz (stock)
**RAM**: 512Mb (generic)
**Video Card**: nVidia GeForce4 440 m
**Sound Card**: Onboard
**HD**: 27Gb Western Digital
**OS**: Ubuntu 7.10 Gutsy Gibbon

**Performance**
Generaly Good. Issues with faulty Heatsink on Graphics overheating the unit (Not an OS Issue).

---

### Post by Mythstory on 2008-02-08
Hardware
CPU: Intel 6550
RAM: 2.0 gb ram
Video Card: on mb Gigabyte G33 intel Graphics
Remote: Winfast DTV 1000 T bundle
HD: 500 gb SATA Seagate hard drive
Tuners:
2 X Winfast DTV 1000 T bundle
Performance
All hardware properly detected and functional.
But HD Recording of 2 chanels at once works
But HD live and playback does not work on Myth

Winfast PVR2 Software on WinXP does work for watching,Playing 
and recoding of HD TV on same box..But is less stable..Is faster
changing channels. Will check on HD Threads

---

### Post by DuncanG on 2008-02-08
**Hardware**
Motherboard: Gigabyte GA-MA69GM-S2H
CPU: AMD BE-2350, Scythe Mini Ninja cooler, 1 GB RAM
Video Card: Onboard ATI X1250
Sound Card: Onboard Realtec
HDD: Samsung 1TB HD103UJ 
Tuner: AVerMedia AVerTV Hybrid+FM PCI A16D
Case: Antec NSK2480B

**Performance**
Not working yet. Mythbuntu and graphic install of Ubuntu fail due to onboard graphics, so text install and manual MythTV install required. Playback via MythTV jerky, so working on drivers next.

**Specific problems**
Gigabyte GA-MA69GM-S2H: SATA connectors are off the edge of the board, so does not fit in MicroATX case without cutting metalwork. Problems with onboard graphics not yet resolved, but enough to prevent straightforward install.
Samsung 1TB HD103UJ: Slow on cold start and not recognised by BIOS, so reboot always required.
AVerMedia AVerTV Hybrid+FM PCI A16D: Not supported out of the box (Linux), but install instructions [http://mcentral.de/wiki/index.php5/AVerMedia_AverTV_Hybrid_FM_PCI_A16D]("http://mcentral.de/wiki/index.php5/AVerMedia_AverTV_Hybrid_FM_PCI_A16D") may be working, cannot tell until playback resolved.
Antec NSK2480B: Power connector for two close SATA devices - so cannot power both HDD and DVD without extra lead, as they are several inches apart. Otherwise an excellent case.

---

### Post by rmoore2112 on 2008-02-10
**[SIZE="3"]Hardware[/SIZE]**

This hardware is a great value for a quiet frontend and a powerful backend.  Please pay attention to the installation notes, especially the NVIDIA drivers section (it will save you from re-installing the whole shebang!).
The tuners were supported out of the box !!

**Role** MythTV Frontend and Backend
**Motherboard** EVGA e-7150/630i Motherboard - NVIDIA nForce 630i, Socket 775, MicroATX
**Case** Antec NSK 2480
**CPU:**Intel Core 2 Duo E4500
**CPU FAN** ZEROtherm CPU Cooler CF900 775
**RAM: **2 GB Corsair TWINX 2048MB PC6400 DDR2 800MHz (2x1024)
**Video Card:** Integrated nVIDIA e-7150
**Sound Card:** Integrated 
**HD**: WD Caviar 500GB Serial ATA HD 7200/16MB/SATA-3G
**CVD/CD** LITE-ON 20x DVDRW SATA 
**Remote: **Microsoft MCE Remote with IR reciever / blaster (version2)
**Tuners: **HDHomeRun, Hauppage WinTV PVR-150

**[SIZE="3"]Installation Notes[/SIZE]**

Install Mythbuntu 7.10 in SAFE Mode - [COLOR="Red"]DO NOT[/COLOR] use the restricted drivers for the NVIDIA card - use generic VESA driver during the install.
Install the complete system before performing the configuration steps below.


**[SIZE="2"]e-7150 Configuration[/SIZE]**

Download the [169.04 beta video drivers]("http://www.nvidia.com/object/linux_display_ia32_169.04.html") from NVIDIA.

When you install the driver, the installer will compile a version for your Kernel.  To do this, you will need to install the kenrnel source & headers, gcc and build-essentials.

After the NVIDIA drivers are installed run
```
nvidia-xconfig
```


**[SIZE="2"]Onboard Sound Configuration[/SIZE]**


install linux-backport-modules which includes the hda_intel module.
You will have to add the backports repository through synaptic-package-manager

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse Deb-src-http://it.archive.ubuntu.com/ubuntu/ gutsy backports main restricted universe multiverse

```
sudo apt-get install linux-backport-modules
```

If you are going to use the digital output on the back of the motherboard, you will have to enable it through the ALSA mixer.


**Performance**
The system performs great!!.  I was able to rip a dvd, and watch recorded HD content on two different front ends while capturing from the two HDHomeRun tuners.

---

### Post by david.birch on 2008-02-11
Setup: Frontend/Backend  7.10

CPU: Core Duo E6600 - dual 2.4GHz
RAM: 2GB
MB: Asus P5B-VM
Video: XFX nVidia 7300GS
Sound: onboard Intel HD (ICH8)

Tuner 1: Hauppauge Nova-T-500
Tuner 2: Leadtek DTV1000T

Functions well (great playback on 1080i signals in Aus with low cpu usage - < 5%) aside from a current problem with 0.20.2 frontend pausing between program changes on the same channel.
Remote on Hauppauge works, haven't testing on the leadtek but it's input is detected so i assume it should work.  AC3 Pass thru wouldn't work for me in myth but would in mplayer & vlc, not sure what the prob is - assume it is configuration error.
Only other issue is tuners getting picked up in random order by kernel at boot - there is no way to differentiate between the hauppauge tuners to write a udev rule, so i had to write a script to grep dmesg & update the cardinput table...

---

### Post by incubi on 2008-02-12
_**Hardware**_
**Mother board:** Asus A7N8x-x 
**Chipset: **Nvidia nforce 2
**CPU:** AMD Athlon XP 2400+
**RAM:** 1G Kingston
**Video Card:** Nvidia 5200 FX
**Display:** Syntax Olevia 542i 42" LCD HDTV using VGA input
**Sound Card:** SB Live
**HD: **50G WD IDE, and  2 WD 250G IDE
**Remote:** Newer pvr-350 /w colored buttons at bottom
**Tuners:** PVR-350


**_Performance_**
My first try was with mythdora and it installed but had choppy video. My system worked well on first install with mythbuntu 7.10! All hardware was detected and remote worked default. PVR-350 TV Out worked with a mod but not worth the work because the video was not much better then VGA. Needed to format and mount the two 205G drives then point myth to them. 

Overall good performance!
__________________

---

### Post by txcrackers on 2008-02-17
Setup: Backend/Frontend

_Hardware_
CPU: AMD XP 2100
RAM: 1Gb
Video Card: PNY NVidia GeForce 6200 256mb
Sound Card: SoundBlaster Live!
HD: Seagate Barracuda 7200.10 ST3250820A 250GB
Remote: eDATA DEC-200B (Toshiba IR01)
Tuners: Hauppauge WinTV-PVR 150 MCE 274

_Performance_
Worked out-of-the-box. The only issue I had was figuring out the correct frequency table to use.

---

### Post by r_endymion on 2008-02-18
Hardware 
CPU: Pentium D 3.2
RAM: 2 gigs
Video Card: GeForce 6600
Sound Card: Onboard Intel HDA (Realtek ALC880) using SPDIF
HD:200GB Seagate SATA
Remote:
Tuners: Leadtek Winfast TV Expert 2000 XP


Performance
Card detected fine, audio was a PITA to get configured. ALSA will not load  on boot, will not load until I first play an audio file. I'm sure its a config problem, only my first week using Linux.

---

### Post by Caps18 on 2008-02-20
**Hardware Working With No Problems:**
PNY GeForce 6200 AGP (8x running on  4x AGP motherboard)- Mythbuntu detected it and downloaded the nvidia drivers much better than Fedora


**Hardware With Some Problems, but now setup 100%**

**Hardware With Some Problems, but still needs fixed**

**Hardware that doesn't work**
Rosewill PCMCIA To PCI adapter 

(Doesn't work in Fedora either, or at least I wasn't able to get it to work and it caused problems during boot-up when installed)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815166013](http://www.newegg.com/Product/Product.aspx?Item=N82E16815166013)


I'll come back and update this again later.

---

### Post by lytke on 2008-02-21
**Hardware**
CPU: C7 on VIA EX10000EG
RAM: 1GB
Video Card: onboard cx700m2
Sound Card: onboard VIA VT1708A
HD: 80GB PATA
Remote: Hauppauge 
Tuners: Hauppauge nova-t 500


**Performance**
Install okay, tuner discovered and working
video driver (vesa) only allows 768x1024, not able to customize
- does show a TV picture -very slow - unusable
- is it possible to include driver from VIA ? (available on viaarena for 7.10 and other older versions)

---

### Post by rddone on 2008-02-25
Hardware
CPU: AMD XP 2400+ in old MB (running at 2000, since MB cant detect 2400)
RAM: 1 GB RAM
Video Card: NVIDIA GeForce 6200 256 MB using composite video out -> Channel modulator
HDD1: 30 GB PATA using a bit over 1GB.
Recordings played from file server over NFS mount.
Tuners: None (recording is done on other machine)
Remote: Tira-2 USB using Satellite 1142 on JP1 universal remote

Performance:
CPU time of less than 20% while playing 640x480 mpgs. 
Video quality is awesome even on 52" LCD through modulator->demodulator combo fed from composite video output.
Had to force video mode for install even with monitor capable of 1280x1024.
All hardware properly detected.
Disabled all Power saving features of monitor in xorg.conf since TV out not properly restored after blanking
Tira USB remote was a huge learning curve, even after having to manually setup PVR-150 remote on Mythbuntu 7.04.

Everything works perfectly now, and could replicate setup from scratch in a couple hours.

---

### Post by tr333 on 2008-02-29
**Hardware**
Case:  Antec NSK2480
Mobo: Gigabyte GA-G31M-S2L
HDD:  120GB IDE
GPU:  nVidia 8600GT
WiFi:  D-Link DWL-G510 (rt61 chipset)
CPU:  Intel E2160 1.8GHz C2D
RAM:  2GB
Audio:  Onboard Intel HDA
Optical Drive:  ASUS Lightscribe 20x DVD-R.

**Performance**
Case looks good sitting next to a TV, and is nice and quiet.
Ethernet and WiFi not working out of the box on Mythbuntu 7.10.  Ethernet now working after removing r8169 driver and compiling and installing r8168 driver (using instructions found on ubuntuforums).  WiFi still not connecting to WPA2-AES network even after compiling rt61 legacy driver from serialmonkey.  This should hopefully improve in 8.04 with the rt2x00 driver in the 2.6.24 kernel.  Haven't yet tested the 8600GT on S-VIDEO output.

---

### Post by jakev383 on 2008-03-08
**Hardware**

**CPU:** Intel P4 2.4Ghs Celeron
**RAM**: 1G
**Video Card**: Onboard Intel based
**Sound Card**: Onboard
**HD**: Seagate 250G
**Remote**: N/A
**Tuners**: PVR 150 and a PVR-500


**Performance**
Works great. I can use all 3 cards at the same time. Do date I've recorded on 2, and watched liveTV on the last. The PVR150 does get a "sharper" image than the PVR500, so I have it +1 in priority for recordings. This is my backend, and is currently running MythDora4.  Only time I've ever noticed a hiccup was while recording a show, comm-flagging another show, the wife was watching a show on one of the front ends, and I was re-encoding some shows to burn to DVD at the same time. It would cause the front end to stutter every once in a while. 



**CPU**: Intel P4 2.4G
**RAM**: 2G of DDR2
**Video Card**: NVIDIA GeForce 6800 (restricted drivers)
**Sound Card**: On board
**HD**: 500G Seagate
**Remote**: N/A
**Tuners**: N/A


**Performance**
Works great, except for the NVIDIA pink screen bug. I use this machine to edit my shows before exporting to DVD on the backend. This is a Ubuntu 7.10 machine with the Myth components installed.


**CPU**: Via MII 10000 (1Ghz)
**RAM**: 512M
**Video Card**: OpenChrome (onboard)
**Sound Card**: (onboard)
**HD**: 10G Toshiba (laptop drive)
**Remote**: PVR150 remote using a home-built serial adapter
**Tuners**: N/A

[B]
Performance[/B]
Works great as well. I have not tried PIP since it's connected to a 20" TV in my bedroom, but we watch our shows and movies on this machine without problems. I do turn it off at night since the CPU fan is loud. Slim DVD drive also works great, and I use it to rip DVDs to the NFS share. This machine runs MythBuntu 7.10. I have another frontend with exactly the same specs, except for the HD which is a 20G Seagate 2.5" drive.

---

### Post by miket3115 on 2008-03-09
Hardware:

CPU - Intel Dual Core @ 2.66Ghz
Mother Board - Intel D945GTP
Ram - 3 gig's 
Video card - ATI Radeon Sapphire HD 2400 Pro
sound - Onboard
HD - 250 gig Western Dig.
Cams - Microsoft life cam 3000 and a Logitec Quick Cam
Lan - Onboard 
Wireless - DLink DWL510 
Printer - Lexmark X1195

Performance:
System works well running Gusty 7.1, took me a little while to get my printer to work.  It prints fine now, although, the built in scanner and photo copier functions are a no go as of yet. 

I had Gusty installed on this system for about two weeks when I installed the Graphics card and to my dismay when I booted for the first time the system crashed.  It did boot on the second try but only to a command prompt which asked me to login. No GUI at all.  

I reinstalled Gusty and it seemed to work, however, on further inspection I discovered the system was using a Generic VESA Driver and not the Radeon driver.  The driver works well and I've not taken the time to fiddle with it to find a compatible ATI drive.

I down graded my web cam from the Microsoft to a Logitech as i couldn't get the  Microsoft webcam to function.

To date I haven't been able to get a Mic to work on this system, I believe it has something to do with the Intel chipset but not sure on that.

That being said I am still very impressed with Ubuntu.

MIke
Just say no to Microsoft!;-)

---

### Post by myth-karl on 2008-03-09
Hardware

CPU: Athlon x2 4800 (dual core)
RAM: 2G (ebuyer value)
Video Card: Onboard ATI X1250 (690g chipset)
Sound Card: Onboard
HD: WD 500gb IDE
Remote: N/A
Tuners:
Others: Antec Fusion Black v2


Performance
All works fine expect lcd, volume knob and IR reciever. Some progress on this from codeka. Graphics work ok out of box through HDMI. Also had to install GUI mixer so I could enable SPDIF output. Some graphical glitches occasionally during video playback. HD playback has diagonal lines.

---

### Post by rickyble on 2008-03-10
**Backend**

Hardware
CPU: dual 550s Pentium II
Ram: 1GIG
Video: 3D Oxygen
Remote: None
Hard drives: 30 GIG system 
                     250 GIG /Home
Tuner: None 
Capture Card: None

Performance: Excellent

**Frontend**

Hardware
CPU: 700 Pentium III
RAM: 320 GIG
Video Card: Nvidia FX 5500(both DVI and S-Video work)
Sound Card: Digital SPDIF
HD: 6 GIG
Remote: None
Tuners:None

Performance: Good

All videos are captured using hacked Directv and transcoding on the fly using TysuiteJ and saved to the Mythtv video directory.  DVDs ripped are saved to the videos directory.  Downloaded music saves to the Mythmusic directory.  These are shared out though Samba and NFS mounts.  Saved videos are both SD and HD.  HD will not play smooth.  Jerky.  I suspect the CPU is not fast enough for HD.  CD import will not work right now.  I will add a tuner card and capture card eventually.

---

### Post by haggus on 2008-03-25
Hardware 

Asus M2NPV-VM
CPU AMD X2 5000 Brisbane Blackbox 65Nm
Northbridge Nvidia geforce 6150 GPU
Southbridge Nvidia nforce 430 MCP
2Gb Mushkin DDR2 800 Mhz Ram
250Gb Seagate SATA2 HD
Logitech wireless keyboard and mouse model YRK56-A
Soundmax 5.1 channel codec
twinahan 1020A red DVB-S
Hauppauge pvr 150 MCE
LG 42" plasma
5.1 surround through jvc home theatre

Everything was detected right out of the box with mythbuntu 7.10 x 64 however I did oringinally try 1Gb of kingston DDR2 667Mhz ram but had video problems with pxelation and mythfrontend regular crashes puuting more ram in seemed to fix this although it goes against everything I read because myth is not supposed to eat up ram. Running version 0.21 compiled from svn using debuild -us -uc I had tried the mce 150 remote which I had working twice but I couldn't get it to work well but with wireless mouse and keyboard don't really need this

---

### Post by jakev383 on 2008-03-26
> **jakev383 said:**
> **Hardware**

**CPU:** Intel P4 2.4Ghs Celeron
**RAM**: 1G
**Video Card**: Onboard Intel based
**Sound Card**: Onboard
**HD**: Seagate 250G
**Remote**: N/A
**Tuners**: PVR 150 and a PVR-500


**Performance**
Works great. I can use all 3 cards at the same time. Do date I've recorded on 2, and watched liveTV on the last. The PVR150 does get a "sharper" image than the PVR500, so I have it +1 in priority for recordings. This is my backend, and is currently running MythDora4.  Only time I've ever noticed a hiccup was while recording a show, comm-flagging another show, the wife was watching a show on one of the front ends, and I was re-encoding some shows to burn to DVD at the same time. It would cause the front end to stutter every once in a while. 



**CPU**: Intel P4 2.4G
**RAM**: 2G of DDR2
**Video Card**: NVIDIA GeForce 6800 (restricted drivers)
**Sound Card**: On board
**HD**: 500G Seagate
**Remote**: N/A
**Tuners**: N/A


**Performance**
Works great, except for the NVIDIA pink screen bug. I use this machine to edit my shows before exporting to DVD on the backend. This is a Ubuntu 7.10 machine with the Myth components installed.


**CPU**: Via MII 10000 (1Ghz)
**RAM**: 512M
**Video Card**: OpenChrome (onboard)
**Sound Card**: (onboard)
**HD**: 10G Toshiba (laptop drive)
**Remote**: PVR150 remote using a home-built serial adapter
**Tuners**: N/A

[B]
Performance[/B]
Works great as well. I have not tried PIP since it's connected to a 20" TV in my bedroom, but we watch our shows and movies on this machine without problems. I do turn it off at night since the CPU fan is loud. Slim DVD drive also works great, and I use it to rip DVDs to the NFS share. This machine runs MythBuntu 7.10. I have another frontend with exactly the same specs, except for the HD which is a 20G Seagate 2.5" drive.


Just wanted to update that I recently added a new front end to my setup:



**CPU**: MSI Fuzzy945GM1 (2.4G Celeron Intel CPU, has DVI out on board)
**RAM**: 512M of 667Mhz DDR2
**Video Card**: Intel 945 (onboard)
**Sound Card**: (onboard)
**HD**: 60G Seagate SATA
**Remote**: generic serial receiver, with a universal remote
**Tuners**: N/A

**Performance**
Worked out of the box once I used the Intel graphics drivers. I do not have true HD resolution set up yet on my Westinghouse 42" 1080P, but the 1280x1024 screen looks nice enough. I only have SD content and tuners, so I can't comment on HD performance at this time. Everything else worked great with minimal fuss.

---

### Post by imric on 2008-03-29
**Hardware**
**CPU:**AMD2800
**RAM:**2gb
**Video Card:**nvidia fx5900
**Sound Card:**generic 16bsb
**HD:** 40gb, 250gb
**Remote:**winMCE usb
**Tuners:**
wintv-pvr-usb2
MSI PC@anywhere

**Performance**
The wintv tuner works fine.
The MSI card fails to initialize /dev/dsp1 (though it showed on the livecd), and so will not play through my sound card.

---

### Post by dafreak on 2008-03-30
Hardware
CPU: P4 1.4Ghz
RAM: 768 MB
Video Card: Matrox G450MAX
Sound Card: Hercules Fortissimo
HD: Western Digital 40 GB
HD: Seagate 320 GB
Remote: MCE USB2 remote (really a Harmony 670 setup that way)
Tuners: ATi TV Wonder (pair of them)

Performance:

Video works fine out of the box although not at the resolution that I want to run it at. Sound continues to be an issue as I cannot get audio out of the SPDIF connector yet. Remote works great however which makes me happy. Lots of stuttering out of the ATi TV wonder cards though.

---

### Post by grytpype on 2008-03-30
The following mobo did NOT work for me and is being replaced:

Asus M2V-MX SE Socket AM2 VIA K8M890 DDR2-800 PCI.e Motherboard

Everything was working except video capture.  After about 2 sec of capture of either Firewire video or PVR-250 video with ivtv, the capture would freeze.  The ivtv driver was throwing a DMA TIMEOUT error in syslog.  I never determined the problem with the Firewire capture, but I figure it was probably a DMA problem as well.

Details here:
[http://ubuntuforums.org/showthread.php?t=738387](http://ubuntuforums.org/showthread.php?t=738387)

I think the VIA chipset is very problematic with respect to DMA and should be avoided.  I am replacing with an NForce-based mobo.

---

### Post by lilmagnus on 2008-03-31
Hardware
CPU: P4 2.8GHz
RAM: 768 MB
Video Card: GeForce MX 440, 128 MB
Sound Card: On-board CMX?
HD: 160 GB
Remote: MCEUSB2
Tuners: Hauppauge PVR-500MCE
Wireless: D-Link WDA-2320 (restricted MadWifi drivers)

It all worked flawlessly after an hour of install, tweak, test. Windows XP with GB-PVR on same hardware was absolute CRAP!

---

### Post by NightwishFan on 2008-03-31
CPU:AMD Athlon 64 X2 Dual Core Processor 3800+ @ 2.0ghz
RAM: 2X 512 DDR2 (898 usable)
Display Adapter:Nvidia Geforce 6100/6150 nForce 430 Integrated (128mb)
Hard Disk: 200gb ATA WDC
Sound Card: Realtek (Unknown Model)
Internet: Unknown Ethernet

All works flawlessly except my display adapter which is almost always detected as 640x480 resolution max. Gutsy sees 1280x800(?) With the restricted drivers all works well (1440x900) although some programs assume I do not have Open GL acceleration when I presume I do.

---

### Post by jjohns63 on 2008-04-04
CPU: Intel E6750 Core 2 Duo 2.66  GHz
Tuners: PVR-350, AverMEDIA A180
Mobo: Gigabyte GA-G31M-S2L
Antec Fusion V2 Silver case

Well I had a couple issues, the tuner cards work great, just had to add the nxt2004 firmware for the A180. The mobo had one major problem, the NIC didn't work out of the box, the driver provided with Gutsy is incorrect. There's an updated driver on Realtek's website but it's hard to compile when you can't download any compilers. The case works great, the VFD works wonderfully, I'm very happy with that. But the built-in IR receiver apparently only works with MCE remotes. Oh well, I just used my homebrew seiral receiver.

Edit:
I'm using the onboard Intel G31 graphics and the onboard audio, only stereo, no SPDIF

---

### Post by johnnybirdman on 2008-04-05
Hardware
**CPU:** P3 866 (Dell L866r guts in a different case)
**RAM:** 512
**Video Card**: evga mx4000 (nvidia)
**Sound Card**: generic - came from my parts box
**HD**: 1 - 40GB Maxtor; 1- 250GB Seagate
**Remote**: PVR-350 remote
**Tuners**: PVR-350
**Mythbuntu Version**: currently 8.04

**Performance:**
Tried an install with 7.10 first and it would not even boot into the live CD.  8.04 Live CD worked fine, then installed fine as well.
All hardware works out of the box.  I don't use for recording TV but for .avi's/vids, DVD, music, weather, streaming, etc. and it all works.  A few software beta bugs fixed and all is running well.
Hard to believe how easy it was to install and setup... and the remote was just plug in ir trans/rec, check the box and it worked.  Awesome.  Now just need to get a better looking HTPC case and get the PC of the floor and make the other half happy.

Only remaining issue is volume up/down does not actually control volume when playing music, but does for DVD and vid playback.  Odd.
Thanks to the project leaders.
J.

---

### Post by Valentin_X on 2008-04-11
**Hardware **
Setup: Primary Backend/Frontend (hardy fully patched)
CPU: E6600
RAM: 4.0 gb ram
Board: MSI P6N SLI
Video Card: NVIDIA 8800 GT 512MB Gainward 
Sound Card: TerraTec aureon 5.1
HD1: 250 GB SATA hard drive
HD2: 250 GB SATA hard drive
HD3: 750 GB SATA hard drive
HD4: 500 GB USB hard drive
Tuners: LeadTek PVR 3200 H

**Performance**
graphic card not spontaneous working.. take some time to get it running. now xserver does not work proper after first login, if ctrl+alt+backspace and relogin it works more or less (gnome upper panel switch between the length of both screens and one screen, drive icons not shown and background is black and do not accept any input (eg. right click) ). TV tuner does not work until now. dvd playback does not work (css, read installed). sometimes shutdown is not working because xserver does not shut down (i have to make ctrl alt backspace ) then it shuts down with some network_manager errors. and last but not least only one (IDE) dvd device is recognized and i can not burn anything. most of the other stuff is working i think :lolflag:.  hopefully i found the time to get the rest running. **pm me if u have some tips. **

cheers

---

### Post by techniciantf on 2008-04-20
Have been trying and finally.........

Thanks for 8.x beta.
Although I could not get the grub loader to work.....

Have a-lot of different hardware and have been trying to find a system that works. It's not perfect but....

System 1 : Main Backend
  P23G motherboard, Celeron 3ghz, 1 g mem. 500g sata, mce 150 w/remote.
All is working Well.

System 2 : Secondary Backend
  M7VIG Pro mother, AMD something or other, 1g mem, 250g ide, 
  150 Happ Tuner.
All is Well

Looking to add three frontends, two more backends, and possible network boot.Definetly booting from usb or compact flash IDE adapters.

I have won a few tuners on Ebay and am going to expand the recording system soon.

Hardware Problems
Have a ADS usb instant tv, can't get to work.
Have V.Everything Geoforce2 Twin with tuner, no go.
Have Happ 1600 HD, getting working with newer system. but why can't I use the normal tuner?

Questions: Can i set up network cameras as channels to watch?
also, I'm not shure just how to use the video in (composite).

All in all, thanks for the great work on this project.

---

### Post by gstrock on 2008-04-26
Sanyo M1 cell phone, can not attach as a usb mass storage device.
I'm fed up.

about 2 releases ago or so, it worked.
I upgraded to Hardy in early March and it worked.
Then by the final release of Hardy it didn't work.
Why do they taunt me like that???

---

### Post by voctikal on 2008-04-26
Combined Frontend/Backend

Case - Nmedia HTPC Case
CPU - AMD 64 - LE 1600 2.2 GHz
Mobo - TForce TF7050-M2 AM2 NVIDIA GeForce 7050PV HDMI Micro ATX
Graphics - NVIDIA GeForce 7050PV
Sound - Onboard Audio
HDD - 2 750 GB Seagate 7200 RPM SATA 3.0 Drives
Optical - Lite-on DVD Burner
PSU - COOLER MASTER eXtreme 500W Power Supply
RAM - A-DATA 1GB (2 x 512MB) DDR2 800 (PC2 6400)
Remote - Streamzap Remote
Gamepads - 2 x Logitech  Cordless RumblePad  

Performance - Just did the upgrade to 8.04 and everything went smooth. All types of video play very well, both SD and HD, even though this is only a single core cpu.  Video is surprisingly well for onboard.

No complaints thus far as far as performance goes.:guitar:

---

### Post by amphibem on 2008-04-26
**Hardware**
CPU: Athlon 64 3800 (2.4GHz)
RAM: 1GB
Video Card: Nvida 6100
Sound Card: Realtek ALC662 
HD: Seagate 320GB
Remote: Microsoft MCE USB2
Tuners: Hauppauge PVR150


**Performance**
Installed fine except for GRUB failing to install, used LILO instead.

Records and plays back analog TV fine, adding a Nova-T 500 soon so will update.

Analog 5.1 doesn't work (working on this, see [http://ubuntuforums.org/showthread.php?t=760091](http://ubuntuforums.org/showthread.php?t=760091)), 2 channel sound works fine.

System status shows full memory usage which I find suprising, however this doesn't appear to affect usability.

---

### Post by thafemann on 2008-04-26
How did you get the PVR-500 MCE remote to work?

Also, how did you get the card to work?  Everything was detected but the video card doesn't give any video.  :(

---

### Post by mtbdrew on 2008-05-08
Hardware
CPU: AthlonXP 2000+ 
RAM: 1GB
Video Card: Nvida 5500
Sound Card: Onboard SIS
HD: Seagate 300GB
K7S5A Pro (SiS 735 chipset)
Tuners: AverTVHD MCE A180

Performance
Installed fine but had to jump through hoops to get the firmware for the tuner loaded.
No LiveTV and no record functionality even though I can scan the channels and use program guide (EIT) to setup record time. Harware works out of the box with MythDora 5 installed.

---

### Post by repaco on 2008-05-08
Hardware
 CPU: Amd sempron +2000 32 bit
 RAM: 1 gb
 Video Card: Ati Radeon 9550
 Sound Card: don`t know
 HD: 2 * 80 = 160GB Hard Disks (Matrox)

Performance 
Black Screen after boot and previous Login Box. System doesn`t work.
Maybe Ati Drivers Bugs.

---

### Post by falcon15500 on 2008-05-21
**_[SIZE="5"]Hardware:[/SIZE]_**
**CPU:** AMD X2 5200+
**Mobo:** GA-MA69GM-S2H
**RAM:** 2Gb 800Mhz
**Video:** Nvidia 6200TC 256Mb (passive)
**Audio:** Onboard
**HD:** Seagate 500Gb SATA
**Tuners:** 2 x WinFast DTV1000T
**Remote:** New style MCE

**_[SIZE="5"]Problems:[/SIZE]_**
Have been trying to get onboard video (ATI 1250 from 690G) working but everything I have tried so far has failed.  It's either choppy as hell or I get two squashed images, on above the other?  Hoping that this will be sorted soon as I want to use the onboard HDMI someday.  **If anyone can help me with this, let me know!!!**

Remotes for the Tuners are POS.  I think a hardware limitation means that the generic kernel needs to be recompiled using a 1000Hz timer, for the remote to be reliable.  This is a pain in the **** each time a new kernel version pops out, so I replaced with the MCE remote that worked out of the box.

**_[SIZE="5"]Performance:[/SIZE]_**
With the Nvidia card in, performance is flawless for both SD & HD.  I have the system hooked up to a 22" LCD and pretty much only ever watch HD transmissions.  From everything I read, the system should have tonnes of grunt left for other frontend, should the need arise.

I am using the Shepherd EPG grabber, which is an absolute godsend!  More power to these people IMO.

---

### Post by DutchLoki on 2008-06-27
Though it would be nice to have a thread about the hardware setups everyone uses with MythBuntu.

Is your hardware working well with MythBuntu? Then let others know about your choice of hardware and how you got it to work.

---

### Post by DutchLoki on 2008-06-27
My setup:

Country: the Netherlands
TV provider: Kanaal digitaal (satellite)

livingroom setup:

* Mainboard: Gigabyte matx 780G (Gigabyte GA-MA78GM-S2H);
* CPU: AMD Athlon X2 4850e;
* Cpu-cooler: Scythe Ninja Mini (using it passive)
* Video-card: onboard
* sound-card: onboard
* networkcontroller: onboard
* hardisk: Samsung SpinPoint F1 1TB
* Memory: 2 gig ram
* Tunercard: 2 * technotrend S-1500, technotrend CI + alfacrypt classic + smartcard from kanaal digitaal.
* Webcam: Logitech QuickCam Pro 9000 for videocalls (looks good on a flatscreen and works even better!)
* case: an old miditower case hiden behind the furniture.
* remote control: ms mce remote (cheap and works great, but will be replaced by a RF type)


Previous setup (currently active as a frontend in the bedroom):

* P4 1800;
* Medion mainboard (not sure about the type)
* medion videocard (a rebranded nvidea card)
* 512 mb
* 450 gig HD
* 2* hauppauge pvr 350
This setup will soon be moved to my sister in law (alway good to keep her on the good side ;) ). 


Future plans: 

looking around for a frontend in the bedroom. I'm considering to buy a secondhand laptop with defect screen for about 75 euro or building a low budget ITX system.

Also going to build a mythbox for my parents which need to work for cable tv (Ziggo). This system will be the same as my current system except for the tunercards. These will probably be replaced by two technotrend c-1501 budget cards, great price and capable of full hd in mpeg 2 and 4 (only the drivers are in experimental status so need to sit on my hands for a while). Also throwing in a quickcam pro 9000 so we can have videocalls with each other (This cam is the best you can get at the moment and has a nice pricetag).

---

### Post by freymann on 2008-06-27
My Main backend/frontend in the basement:

    * Diablo X-Man Silver Gamer Case, Coolmax 400W V2.01 Power Supply
    * EVGA nForce 650i Ultra Socket 775 Motherboard
    * EVGA GeForce 8400 GS, 512MB RAM, PCIe w/DVI-TV-OUT
    * Samsung 18x DVD RW SH-S183L SATA LS OEM
    * Seagate 250GB Serial ATA w/NCQ 7200/8MB/SATA-3G
    * Crucial 1024MB PC5400 DDR2 667 MHZ (2 pieces, for 2GB RAM)
    * Intel Pentium D 925 3Ghz DT 800FSB Socket 775
    * Hauppauge WINTV-PVR-150 MCE BNDL MPEG2 w/REMOTE 
    * WD Caviar 500GB Serial ATA HD 7200/16MB/SATA-3G 
    * Sony DRU190A 20X DVD Burner EIDE
    * Logitech Cordless Desktop LX310 (keyboard/mouse)
    * Linksys Etherfast 10/100 5-port Switch 
Connects to a no-name 26" LCD HD TV via HDMI

My Frontend/Secondary Backend in the living-room:

* AMD Athlon 64 X2 Dual Core 4200+ Socket AM2
* AMD Original AM2 CPU Fan
* ECS nVidia GeForce6100-SM-M Motherboard
* 1GB DDR II 667 Memory 240 Pin (Kingston)
* nVidia GeForce 6100 2D/3D Graphic Engine, up to 256MB Memory (disabled in favour on PCIe Video card)
* Realtek ALC660 6-channel HD Audio
* Onboard 10/100 Network Card 
* 6 USB 2.0 Port, 1 Parallel, 1 Serial
* 1285 Deluxe Black Tower Case
* 450 Watt Power Supply
* Hauppauge WINTV-PVR-150 MCE BNDL MPEG2 w/REMOTE
* Logitech Cordless Desktop EX110 (keyboard/mouse)
* EVGA GeForce 72000 GS 256MB (will take up to 512MB) PCIe
* Sony DRU190A 20X DVD Burner, IDE
* X10 CM11A controller is on this box. It reaches every light from this location. 
* Some 500GB IDE HD
Connects to a 32" CRT Toshiba TV via SVideo

 Master-Bedroom Frontend:

* Model Name • VIA EPIA SP13000G
* VIA EPIA SP8000EG
* Processor • VIA C3™/ VIA Eden™ EBGA processor 
* Chipset • VIA CN400 North Bridge 
* VIA VT8237R-Series South Bridge
* MCE remote
* System Memory • 1 DDR266/333/400 DIMM socket 
* VGA • Integrated VIA UniChrome™ Pro AGP graphics with MPEG-2 decoder /MPEG-4 Accelerator 
* Onboard LAN • VIA VT6103 10/100 Base-T Ethernet PHY
* Onboard Audio • VIA VT1617A 6channel AC'97 codec
* Onboard TV Out • VIA VT1623M TV Encoder
* Onboard 1394 • VIA VT6307S IEEE 1394 Firewire
* Form Factor • Mini-ITX (6 layers)
* 17 cm x 17 cm 
Connects to a 21" Hitachi CRT TV via RCA A/V cables

 I have made some changes in June...

 Like replacing the main frontend/backend with:

* AMD Athlon 64 X2 Dual Core 4600+ Socket AM2
* 1 x AMD Original AM2 CPU Fan (a little noisy, not too bad)
* 1 x ECS nVidia GeForce6100SM-M Motherboard
* 2GB DDR II 667 Memory 240 Pin (Kingston?)
* 1 x LG 20X IDE DVD RW + Dual Layer optical drive
* disabled on-board nVidia GeForce 6100 as I couldn't use VGA output
* Realtek ALC660 6-channel HD Audio
* Onboard 10/100 Network Card 
* 6 x USB 2.0 Port, 1 Parallel, 1 Serial
* 1285 Deluxe Black Tower Case
* 450 Watt Power Supply
* Hitachi 500GB Serial ATA HD, 7200/16MB/SATA-3G (Main OS and initial installation on here)
* WD Caviar 500GB Serial ATA HD 7200/16MB/SATA-3G (Media drive in LMCE file structure)
* D-Link DGE-530T 10/100/1000 Mbps PCI Network Adapter (for the inside Network)
* EVGA GeForce 7200 GS 256MB (will take up to 512MB) PCIe Video card
* Hauppauge WINTV-PVR-150 MCE BNDL MPEG2 w/REMOTE
* TP-Link TL-SG1008D 8-Port Gigabit Ethernet Switch (connected to internal nic in Core, rest of the internal LAN connects here)
* Logitech Cordless Desktop LX310 (keyboard/mouse)
* USB-UIRT
* Gyration Motion Sensing Remote Control (GYR3101US) 

My main box is now LinuxMCE 7.10RC2, in the basement.

The Living-Room now network boots into LinuxMCE and I replaced the MCE USB transceiver with a USB-UIRT and added another GYR3101US gyro remote.

The master-bedroom has gone back to MythBuntu 7.10 and talks to the LMCE core, with some NFS mapped shares accessing my media collection on the second 500GB HD in the core.

This link:

[http://wiki.linuxmce.org/index.php/User:Freymann](http://wiki.linuxmce.org/index.php/User:Freymann)

has pictures and full specs, including costs!!

---

### Post by tgm4883 on 2008-06-27
Merged Threads

---

### Post by DutchLoki on 2008-06-28
-Oops- 
(needed a quote for a PM and clicked save)

---

### Post by El_Matthews on 2008-07-12
Hardware
CPU: Intel Pentium 3G
RAM:1.0 gb ram
Video Card: NVIDIA 7600gt, 256 mb
Sound Card: onboard Asus P4-P800-e Deluxe
HD: 500GB
Remote: Delivered with OrigenAe Case
Tuners: WinTV-GO (BT878)
Country: BELGIUM
TV provider: Havi-TV
TV signal type: Normal Cable

Performance:
Everything works except sound of TV-Card. I can watch TV but not hear it and I didn't found a solution yet.

---

### Post by rts on 2008-07-13
_**Hardware**_
(This is a combined frontend/backend).
[LIST]
[*][Asus M3N78-EMH HDMI]("http://www.asus.com/products.aspx?l1=3&l2=149&l3=643&l4=0&model=2082&modelmenu=2") motherboard, using the onboard:
[LIST]
[*]NVidia GeForce 8200 graphics
[*]Realtek ALC883 audio
[*]NVIDIA nForce built-in Gigabit MAC
[/LIST]
[*]AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
[*][Hauppage WinTV Nova-T-500]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI") (with supplied remote)
[*]1 TB Samsung Spinpoint HDD
[*]2 GB RAM
[*]Pioneer BD-ROM/DVD-RW
[*][Antec NSK2480]("http://www.antec.com/us/productDetails.php?ProdID=92480") case
[/LIST]

**_Country_**
[LIST]
[*]United Kingdom using Freeview
[/LIST]

**_Software_**

[LIST]
[*] Fully up-to-date Mythbuntu 8.04, plus some additions (below)
[/LIST]

Due to the unsupported nature of my hardware, I've had to upgrade a few components from the current 8.04 release:

[LIST]
[*]Kernel  2.6.25.9
[*]NVidia drivers 173.14.09
[*]v4l-dvb drivers from mercurial to solve the problems mentioned [here with the remote]("http://ubuntuforums.org/showthread.php?t=828934").
[*]Alsa drivers 1.0.17rc3
[/LIST]

Mythbuntu did not work out of the box on this set up.  [This blog post]("http://coyotesg.blogspot.com/2008/06/cracking-ubuntu-804-to-work-with-nvidia.html") helped me get the motherboard working.

**_Performance_**

Everything works except:

[LIST]
[*]HDMI audio out (apparently a future NVidia driver update will fix that) so for now I'm using the VGA-out with stereo out.
[*][Crackly audio]("http://ubuntuforums.org/showthread.php?t=857508") **SOLVED - Downgrade to 0404 bios**
[*]CPU is a little underpowered for 1080p playback
[*]Suspend to RAM
[/LIST]

To playback 1080p I created the following script:

```

#!/bin/bash
mplayer -vfm ffmpeg -fs -lavdopts skiploopfilter=all:threads=2:fast "${1}"

```

to lower the quality.  Playback is fine now, except mplayer doesn't respond to the remote for some reason.


The case has two 120mm fans circulating air which is a bit noisy, but you can remove one and replace it with a plastic insert that comes with the case.  The AMD-supplied CPU cooler is a bit noisy as well, so I'm going to replace it.

---

### Post by jasondean on 2008-07-13
---

---

### Post by macbookpro2 on 2008-07-29
**Master Backend (mythmaster - Ubuntu 8.04) - Server Rack(Basement):**
CASE: 4U Rack Mount Chassis ATX Case [http://www.plinkusa.net/web4038.htm](http://www.plinkusa.net/web4038.htm)
CPU: Intel Pentium D 930 Presler 3.0GHz
MOTHERBOARD: Intel BOXDG965OTMKR LGA 775 Intel G965 Express Micro ATX Intel Motherboard
RAM: 2GB DDR2 667
Sound Card: Onboard - SigmaTel STAC9271D 
HD: 160GB SATA
Tuners: PVR-500 (2) DirecTv D11-100's Sat boxes
Country:USA
TV provider: DirecTV
TV signal type: Satellite
Display: 15" 1U RackMount LCD monitor KVM

**Frontend/Secondary Backend (mythsony - mythbuntu 8.04) - Living Room:**
CASE: Antec Solution Series NSK2400 Black/Silver Steel MicroATX Desktop Computer Case with Thermaltake A2331 Media LAB
CPU: Intel Pentium E2180 Allendale 2.0GHz
MOTHERBOARD: Intel BOXDG965OTMKR LGA 775 Intel G965 Express Micro ATX Intel Motherboard
RAM: 3GB DDR2 800
Video Card: Nvidia GeForce 7300 GT
Sound Card: Onboard - SigmaTel STAC9271D
HD: 120GB SATA
Remote:  Logitech Harmony 890 / ACK-581 wireless(IR) keyboard/mouse
Tuners: (2) DVICO FusionHDTV
Country:USA
TV signal type: OTA HDTV
Display: Sony 55" LCD HDTV

**Frontend/Secondary Backend (master - mythbuntu 8.04) - Master Bedroom:**
CASE: COOLER MASTER Elite 330
CPU:  Intel Pentium E2160 Allendale 1.8GHz
MOTHERBOARD: Intel BOXDG965OTMKR LGA 775 Intel G965 Express Micro ATX Intel Motherboard
RAM: 2GB DDR2 800
Video Card: Nvidia GeForce 7300 GT
Sound Card: Onboard - SigmaTel STAC9271D
HD: 120GB SATA
Remote: Logitech Harmony 550 / ACK-581 wireless(IR) keyboard/mouseTuners: (1) DVICO FusionHDTV
Country:USA
TV signal type: OTA HDTV
Display: Samsung 27" CRT HDTV

**Mac Frontends:**
Mac Mini
MacBook
MacBook Pro

**File Server (nasbuntu - ubuntu 8.04 64bit) - Server Rack(Basement):**
CASE: 4U Rack Mount Chassis ATX Case [http://www.plinkusa.net/web4038.htm](http://www.plinkusa.net/web4038.htm)
CPU: Intel Pentium D 930 Presler 3.0GHz
MOTHERBOARD: Intel BOXDG965OTMKR LGA 775 Intel G965 Express Micro ATX Intel Motherboard
RAM: 6GB DDR2 667
Sound Card: Onboard - SigmaTel STAC9271D 
HD: 160GB SATA
RAID: LSI 1506064 PCI SATA MegaRAID 150-6 (6x 250GB SATA RAID5)
Display: 15" 1U RackMount LCD monitor KVM

---

### Post by newlinux on 2008-07-29
All systems running mythtv .24 from autobuilds.


[B]1. Firestorm - Ubuntu 11.10 64 bit custom build secondary backend/ HD frontend
[/B]
[ASRock Z68 Pro3 LGA 1155 Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157251")
Intel Core i7-2600 3.4Ghz CPU
[Kingston Hyper X 16GB PC12800]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820104173")
[180GB Corsair Force Series SATA III Solid State Drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820233211")
250Gb SATA (legacy ext3)
2TB USB 3.0 External Hard Drive (JFS - Fantom GForce)

**2. Manhunter - Ubuntu 10.04.1 with myth installed - Custom build garage machine HD Frontend/slave backend**
Prescott P4 3.0 Ghz (socket 775LGA)
[Asus ASUS P5GDC-V mobo (915G)]("http://www.motherboards.org/reviews/motherboards/1474_1.html")
[ECS NSG210C-512QS-H GeForce 210 512MB 64-bit DDR2 PCI Express 2.0 x16 HDCP Ready Low Profile Ready Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814134085")
2GB PC3200
harmony 720 MCE remote with MCE usb IR receiver
[USB TV translater]("http://www.patersontech.com/products/usbtvtranslator.aspx") and [USB->Serial Adapter]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812186105") connected to DirecTv H21 receiver to control channel changing
250GB Western digital IDE (10GB OS partition-EXT3, rest recording storage group partition - XFS)
[Hauppage HD-PVR]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116030&Tpk=HD-PVR") connected to H21-200 DirecTV Receiver via Component and TOSLINK SPDIF In
Connected via DECA cloud (MOCA) from direcTV. nice!


**3. Amazo - Kubuntu 11.10 64 bit custom build HD Frontend/slave backend **
[Abit AN-M2]("http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AN-M2&fMTYPE=Socket%20AM2") AMD (7025-630a)
NVidia Geforce 7025 (onboard)
1 Kworld ATSC 110 (QAM)
1 PVR-150 (not used in myth)
X2 4600 (socket AM2)
2GB PC5400
250GB WD SATA HD (20GB OS - EXT4, 42GB /home- EXT4, rest for recordings - JFS)

**4. Deathstroke - Ubuntu Fileserver 10.04.1 - Master Backend/HD Frontend**
Dell 530N 
[FOXCONN G33M02]("http://www.foxconnchannel.com/product/motherboards/detail_overview.aspx?ID=en-us0000319") (G33 + ICH9) 
E2180 Dual Core 2.0Ghz (socket 775) 
Intel GMA3100[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16816132020"]
Rosewill RC-219 Silicon Image PCI Express eSata x2 NCQ non-RAID SATA II Controller Card[/URL]
[Intel Pro 1000 PCIe gigabit nic]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833106033")
2 7200RPM Hitachi eSATA 2TB Hard drive for backups (JFS)
2 1TB SATA Hard drives (Samsung and Western Digital) - File storage - EXT3
1 250GB Hard drive SATA 40GB (OS 10GB - EXT3, rest recordings - XFS)
1 250GB External USB Hard drive (EXT3)
2GB PC5400
Dvico Fusion 5 Lite (QAM - not currently in use in myth)


[B] 5. Newmyth - Ubuntu 10.04.1 Custom Build
Slave backend/HD Frontend[/B]
X2 3800 (socket 939)
2GB pc3200
[Asus A8N-E]("http://www.newegg.com/product/product.aspx?Item=N82E16813131530")
[ASUS EN8400GS SILENT/HTP/512M/V2 using VDPAU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814121344")
250GB Western Digital 7200RPM (10 GB root partition EXT4, rest is recording partition - XFS)
1TB eSATA 7200RPM drive (recordings - JFS) 
2 Kworld ATSC 110s (QAM)
1 Avermedia A180 (QAM)
Harmony 680 remote, MCE receiver

** 6. Julian - Ubuntu 10.04.1 remote HD frontend/laptop [Acer 5520-5155]("http://computers.toptenreviews.com/gaming-laptops/acer/acer-lxaja0x233-details-23758.htm") **
AMD Turion 64 X2 TL-56 1.8Ghz
15.4 in TFT active matrix WXGA (1280X800)
120GB - Serial ATA-150 - 5400rpm (Linux partition is all EXT3)
2GB DDR2 SDRAM - 667.0 MHz
NVIDIA GeForce 7000M / nForce 610M
Dual boot with Vista

** 7. Ubuntu-laptop - Ubuntu 10.04.1 remote frontend/laptop (SD only) **
Celeron M 380 1.6 GHz 1MB 400FSB
12.1&#8221; Widescreen WXGA (1280X800)
60 GB 5400 RPM
1GB DDR RAM
Intel Graphics
[System76]("http://system76.com") Gazelle

** 8. Blackadam - [ Zotac Mag HD-ND01 NVIDIA ION]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856173001&Tpk=zotac%20mag") Ubuntu 10.04.1 remote HD frontend **
Intel Atom 330
SPDIF optical to receiver
160 GB 5400 RPM
2GB DDR2-800 RAM
Harmony 680 remote, MCE receiver

** 9. Dark-Knight - Ubuntu 10.04.3 remote HD frontend/Convertible Tablet/notebook [Fujitsu T730]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834110433&cm_re=t730-_-34-110-433-_-Product") **
Intel(R) Core(TM) i5 CPU       M 450  @ 2.40GHz
12.1 in Dual digitizer touchscreen (1280X800)
160GB - Serial ATA 7200rpm (Linux partition is all EXT4)
4GB DDR3 1066 RAM
Intel GMA 4800MHD
Dual boot with Win7 Pro 64 bit
[B]
Keyboard Mouse Combos:[/B]

I have 2 BTC-9039URF-3's and 1 ADESSO WKB-3000UB. They both have nice integrated mice and work out of the box (may need to configure a multimedia key or two, but I don't use those).

**Performance:**

All Systems designated HD can playback 720p/1080i mpeg-2 encoded content and most 720p h.264 encoded content that I've thrown at them. Some struggle with some 1080p h.264 content - but I don't watch much of that.The ones with VDPAU supported cards can playback 1080p h.264. All playback is working great, except that VDPAU seems to deal worse with imperfections in m mpeg-2 streams from QAM recordings than software decoding, so for mpeg-2 I usually switch off VDPAU (my cable signal is poor). My Intel HD system do well with playback as well. Acer laptop needed ndiswrapper to get wireless working, and I have the web cam working, but not the internal mic. Everything but wireless and internal mic worked out of the box with Intrepid, and kept working with the upgrade to Jaunty, Karmic, and now Lucid. Fujitsu Tablet took a little fiddling to get tablet features and touchscreen to work properly. Wireless and camera worked out of the box.

HD-PVR is wonderful for recording HD quality off of my directv box, and the USB TV Translator works perfectly.

---

### Post by pjennings on 2008-07-31
Hardware
CPU: Athlon 64 X2 5000+ BE
RAM: 2x512MB DDR2 800
Motherboard: Abit AN-M2
Video Card: GeForce 7025 (onboard, using DVI output @ 1280x720)
Sound Card: ALC888 (onboard, using optical output)
HD: 120GB and 500GB PATA
Remote: ATI Remote Wonder II
Tuners: HDHomeRun
Country: USA
TV provider: OTA
TV signal type: NTSC/ATSC

Performance:
I upgraded from a Sempron 2600+ in order to record/play HD content.  I had some trouble with the system locking when starting X, which I fixed by updating to the latest NVIDIA proprietary drivers.  I also had some problems with the onboard network that was apparently caused by the HDHomeRun, since the problem went away when I unplugged the HDHomeRun for a while.  I am still toying with the audio settings since I have never used digital output before.  It is working as long as I don't enable AC3 passthru.

---

### Post by jnorth on 2008-08-04
_**Hardware**_(mc01)
**CPU:** Intel Core Duo 1300 @ 1.66GHz
**RAM:** 2GB
**Video Card: **Integrated Intel GMA950 GPU (DVI->HDMI converter->LCD)
**Sound Card:** Integrated (Digital available but using analog->amp)
**HD:** 3 (830G total) on-board 80G SATA, 250G firewire, 500G USB.  LVM setup  (RAID0 basically- backups are on another server)
**Remote:** Harmony 520 transmitter.  Built-in macmini receiver.  Custom program using the incrementing Apple remote ID ability to generate over 40 commands available to the Harmony.  PITA but sweet once it gets set up.
**Tuners:** Plextor ConvertX TV402U USB tuner
**Country: E.g. the Netherlands:** USA
**TV provider: E.g. canal digital:** Comcast
**TV signal type: E.g. DVB-S (satellite):** Cable

[U][B]Performance
[/B][/U]Sweet- but this is my first ever MythTV box.  I have been running it for around 6 months so far with no issues.
It was a pain to get the remote working, but once I figured out that by using Apple's ability to "lock" a specific remote to a specific Mac Mini, it was actually generating unique sets of codes.  I was able to save 6 codes to both the mini and the remote, reset the unique ID button by holding play and pauses, and get 6 more codes, and so on.
The other thing I had a problem with was the Plextor.  Since I'm using a mini I have to have  USB or firewire based solution, and cheap also - this works great now but was a pain to setup because of an ALSA/kernel issue.  Downgrading a couple of minor kernel revisions works great.  So I'm running on 8.04 now and loving it!

---

### Post by managementboy on 2008-08-06
_**Hardware**_(mc01)
**CPU:** Intel(R) Core(TM)2 Duo E8200  @ 2.66GHz
**RAM:** 8GB
**Video Card: ** nVidia Corporation GeForce 8600 GT (rev a1) (DVI connected to 1600x1050 LCD and VGA to Sanyo Z1 native res)
**Sound Card:** Intel Corporation 82801I (ICH9 Family) HD Audio Controller (only Stereo for now)
**HD:** 2 (694G SATA2 + 370G IDE) 
**Remote:** Logitech Harmony 525 and Serial Donlge and Logitech dinovo Edge via bluetooth dongle
**Tuners:** Technisat SkyStar2 DVB card (rev 02)
**Country: E.g. the Netherlands:** Germany
**TV provider: E.g. canal digital:** Astra 19
**TV signal type: E.g. DVB-S (satellite):** DVB-S

[U][B]Performance
[/B][/U]Very fast. OpenGL OSD and Video only with patches (check [this]("http://www.nvnews.net/vbulletin/showthread.php?t=111308") site). Native Sanyo Z1 via nvidia-settings at 50Hz. 64bit system.

---

### Post by Nate B. on 2008-08-06
_**Hardware**_
**CPU:** 3.0 GHz P4 HT (two penguins in KNOPPIx!)
**RAM:** 1 GB
**Video Card: ** GeForce FX 5200
**Sound Card:** SoundBlaster Live!
**HD:** EIDE 40 GB (soon to be upgraded to SATA 500 GB or 1 TB)
**Remote:** Hauppage 350
**Tuners:** Hauppage PVR-150
**Country:** USA
**TV provider:** DirecTV
**TV signal type:** S-Video in, VGA to composite via an Averkey Micro (planned as it should arrive in a few days) because my old TV doesn't like a simple S-Video to composite cable conversion.  :confused:

_**Performance**_
So far, so good.  I began this project with installation of the tuner into a second hand IBM ThinkCentre M50 tower along with the video and sound card ten days ago.  Setup has been both easy and a bit of a challenge, but that's to be expected of a complex piece of software with an associated learning curve (not only the software but arcane video trivia).  My thanks to the Mythbuntu crew for making this work so well "out of the box".

I guess that now that it's working, it's time to break it by exploring some of the more obscure corners of Myth.  :)

_**Update**_

Last night I added the final pieces to my Myth box, a 1 TiB drive and DVD+r/RW drive.  In the process of trying to eliminate a series of rolling lines (caused by having the NEC monitor and TV hooked to the Averkey iMicro at the same time) I tried the onboard Intel i865G video adapter with stellar results after a bit of playback brightness/contrast tweaking and recording picture level adjustment.

Right now I'm watching live TV from my satellite receiver and the picture rivals the direct composite video from the receiver.  The improvement in picture quality of the i865G over the FX5200 (both through the iMicro) with the proprietary NVIDIA driver amazed me.  I notice that my load average is about half of before even now sampling at 6 Mib/S and having playback at the high quality setting.  Part of that may be due to now having an SATA drive to store the video.  At the very least the NVIDIA card is out and I'm sure my case will run several degrees cooler since it was a fanless unit and the heatsinks were quite hot.

So, if anyone can use VGA output with SD video, the i865G may be a good bet.

---

### Post by The Pinny Parlour on 2008-08-09
Hardware
CPU:P4 3.0Ghz
RAM:1.5
Video Card:Sis Onboard
Sound Card: Onboard
HD:Seagate 40Gb
Remote: none
Tuners:Asus My Cinema U3000 Mini (USB)
Country: Australia
TV provider: ?
TV signal type: ?

Asus My Cinema U3000 Mini (USB) doesn't work. Tried many tutorials/help files...nothing works.

---

### Post by schmidtbag on 2008-08-17
I have the integrated nVidia (but Intel based) audio AD1986A.  It is classified as ad198x in ALSA.  It works, but anything I run that is processor intensive will have delayed and usually a low quality playback.

I've been searching a lot to see how to fix this but I'm getting very little luck.  I'll post again to mention whether this works OK or not.

---

### Post by mediaimpactman on 2008-08-22
Here is what we use to make the world go round.

Hardware
CPU:AMD Socket AM2 5000+
RAM:2GB GSkill DDR2 800
Video Card:ASUS nVidia 6200LE
Mobo:Gigabyte GA-MA74GM-S2
HD:WD SATA II 7200RPM 320GB or 500GB or 750GB or 1TB
Remote:Hauppauge 1039
Tuners:Hauppauge HVR 1600 & PcHDTV 5500
Country:USA
TV provider:Cable or Satellite

Mike
__________________________________________________________
"More Cowbell!"

---

### Post by JB2007 on 2008-08-23
**Master Backend/Frontend**
**Running:** Mythbuntu 8.04.1 AMD64
**CPU:** AMD Athlon 64 4800+
**Motherboard:** Asrock  ALiveNF7G-FullHD Motherboard (GeForce 7050, DVI & VGA dual output, PCI-E x16, SATA II, RAID, LAN, 6Ch audio) 
**RAM:** 2GB
**Video Card:** Integrated (using DVI > HDMI cable)
**Sound Card:** Integrated 
**HDD:** 2 x Samsung 500GB SATAII
**Remote:** Microsoft MCE old
**Tuner1:** Nova-T single HD DVB-T
**Tuner 2 & 3:** Nova-T 500 MCE dual HD DVB-T
**Country:** Australia (Sydney)

**Slave Backend/Frontend**
**Running:** Mythbuntu 8.04.1 AMD64
**CPU:** AMD Athlon 64 4800+
**Motherboard:** Asrock  ALiveNF7G-FullHD Motherboard (GeForce 7050, DVI & VGA dual output, PCI-E x16, SATA II, RAID, LAN, 6Ch audio) 
**RAM:** 2GB
**Video Card:** Integrated (using DVI > HDMI cable)
**Sound Card:** Integrated 
**HDD:** 1 x Samsung 250GB SATAII
**Remote:** Microsoft MCE old
**Tuner4&5:** Nova-T 500 MCE dual HD DVB-T
**Country:** Australia (Sydney)

**Network** Gigabit(1000baseT)
**EPG Guide Data:** Shepherd

**Performance**
Love it! The old Nova-t needs a firmware file - however the get_DVB_firmware script gets that for you. The new Nova-T 500 MCE's work out of the box - although there are a couple of tweeks to stop the IR polling and turn on the onboard LNA (low noise amp). System was built for HD Free-to-air and purforms very well I can record whatever i want here in Australia with the 5 tuners and multirec that is now part of MythTV I have never had a conflict. There is no issues recording 2 HD channels and watching another on the Master while recording and watching another on the Slave. Purchased both machines for just under A$800 had the old Nova-T already and purchased 2 x Nova-T 500 MCE's for A$185 each so for around $1200 I have almost unlimited recording capabilities on Australian FTA and two frontends. About 1hr setup for each machine and a couple of days tweaking settings. Been stable now - no restarts for 2 weeks, hasn't missed a beat.

---

### Post by uncle pennybags on 2008-08-26
I've got this - 

Motherboard   -- Gigabyte m61pme-s2
CPU           -- AMD Athlon 64 x2 brisbane 2300
RAM           -- 1GB kington ddr2 800
HDD           -- Some crappy Maxtor 250gb on ide
Capture card  -- Happuage hvr-1600 (see note later)
Audio & Video -- Intergrated nVida graphics & audio
Mythbuntu     -- 8.04.1

all hooked up and running. Only one major hurdle, schedules direct doesn't seem to like me

----------note------
HVR-1600 seems to work fine with the beta software installed. See google for further info

---

### Post by jimgrill on 2008-08-29
**_Primary BE/FE Hardware_**
Motherboard: ASUS P5K LGA 775 Intel P35 ATX Intel Motherboard
CPU: Intel Core 2 Duo E8400 Wolfdale 3.0GHz LGA 775 65W Dual-Core Processor Model BX80570E8400
RAM: G.SKILL 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) 
Video Card: ASUS EN8400GS SILENT/HTP/512M GeForce 8400 GS 512MB 64-bit GDDR2 PCI Express x16
Sound Card: integrated w/ S/PDIF digital out
HD: Western Digital Caviar SE16 WD6400AAKS 640GB 7200 RPM SATA 3.0Gb/s
Remote:  (mceusb) Microsoft A9O-00007 WinXP Media Center Infrared Remote
Tuners: PVR-500, firewire
Country: USA
TV provider: Comcast Cable - HD
TV signal type: US-Cable
version: MythBuntu 8.04.1

_**Performance**_
Excellent.  Can record on two inputs, including one in HD, while also watching HD recordings.  I'm using the video card's DVI output via DVI-HDMI adapter to a Sharp Aquos 42" LCD.  Installation was a snap.  I had to tweak nothing.  Got 1080p output with proprietary nvidia driver without any hassle.  Firewire is able to change channels perfectly and obtain a lock in seconds.  HD recording via firewire is also working perfectly.  Setup was quick and painless!

**_Secondary FE Hardware_**
Motherboard: Gigabyte GA-SINXP1394(GA-8SQ800 Ultra2)
CPU: Intel P4 2.6 Ghz
RAM: 4X 512MB
Video Card: nvidia geforce 7600GS 512MB
Sound Card: integrated
HD: Old used 20 G
Remote:  (mceusb) Microsoft A9O-00007 WinXP Media Center Infrared Remote
Tuners: None

_**Performance**_
Good.  This system was a primary BE for a while with a pvr-500 and firewire.  It could record and play HD, but not too well with simultaneous playback of other recordings.  It could, however, record SD and play back other recordings with ease.  As a dedicated FE it is probably overkill.  I may add a SD tuner and a bigger hdd and make it a secondary BE as well.

---

### Post by waspbloke on 2008-09-07
Hardware
Motherboard: ASUS A7N8X v2.0
CPU: AMD Athlon XP2600
RAM: 512MB DDR
Video Card: Geforce4 Ti 4600 (using twinview TVout)
Sound Card: Creative SB Live
HD: Maxtor 40GB ATA
Remote: -
Tuners: Hauppauge WinTV HVR900
Country: UK
TV signal type: DVB-T
Version: Mythbuntu 8.04.1

Performance
Hardware all working from install except USB WinTV HVR900 which needed patching using Markus Rechberger's driver: [https://bugs.launchpad.net/ubuntu/+bug/204578/comments/58](https://bugs.launchpad.net/ubuntu/+bug/204578/comments/58).

Took a while to figure out MythTV setup to get the DVB input working correctly.

Still not got my PCI raid controller being used, it has (striped) 2x 80GB Maxtor ATA drives.

Mobo was initially a problem, PC would just die without warning at random times until I disabled all the unused integrated on-board stuff (3COM & Nvidia ethernet, Nvidia sound, firewire) not a problem as I was already using PCI Realtek eth and PCI SB live.

---

### Post by apollyonis on 2008-09-12
Hardware
Motherboard: ASUS unknown - whatever bundles with the ASUS V3-M2NC61S
CPU: AMD Athlon 64 X2 3800+ Windsor 2.0GHz Socket AM2 65W Dual-Core
RAM: 4GB  Transcend JETRAM 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel
Video Card: MSI N9400GT-MD512 GeForce 9400 GT 512MB 128-bit GDDR2 PCI Express 2.0 x16 Using TwinView TVout to a Panasonic via HDMI
Sound Card: Realtek ALC888
HD: Western Digital Caviar SE16 WD5000AAKS 500GB 7200 RPM SATA 3.0Gb/s for the /mythtv storage and unknown 100GB for O/S and dual boot
Remote: -
Tuners: pcHDTV 5500
Country: US
TV signal type: NTSC (IIRC, edit after confirming)
Version: Mythbuntu 8.04.1

Performance
All hardware working save for a very fine line of static at the top of the screen. I believe this to be caused by the voltage from the provided power supply but I will have to get my hands on another 250Watt power supply to confirm. All recording profiles are set to highest setting and connected through S-Video to DirecTV. Resolutions of 720x480 recording and MP3 for audio @ 44800kbps on all recording profiles. I will eventually connect an HD antenna as an alternate input. The sound is coming in through a Y connector from the composite audio and video is S-Video for the highest possible SD recording. The PCI-E nVidia card has an active fan but this is quiet enough to leave running in the bedroom.

Additionally, since this is connected to the DirecTV I will be looking into a serial-> usb connector to automatically change channels on the D11-500 with the [Patersontech USB TV Translator.]("http://www.patersontech.com/products/UsbTvTranslator.aspx") and adding a serial port via PCI to the computer.

---

### Post by MarkAtNeerim on 2008-09-13
Hardware
Motherboard:  Gigabyte EP35-DS4
CPU: Intel    E6600 Core 2 Duo 2400MHz
RAM:          4GB Kingston 6400
Video Card:   ASUS EN8500GT-Silent
Sound Card:   Realtek ALC889A
HDD:          WD 150GB WD1500ADFD-00NLR5 
              WD 500GB ST3500320NS x2
DVD:          Pioneer DVR-112D 
Remote:       MCE compatible (new version Philips et al)
Tuners:       Hauppauge WinTV-HVR1300
              Hauppauge Nova-T-500MCE dual DVB-T
Country:      Australia
TV signal type: PAL
Version: Mythbuntu 8.04.1

System works well, wouldn't recomend the HVR-1300 as we haven't been able to tune analog TV - which is why we bought it, driver development appears to have stalled.  The Nova-T-500 works well with XVMC setup and installed and driver development is current.

Don't get caught trying to install the default Hauppauge remote that MythTV shows as the default for this Nova-T-500MCE tuner,  the MCE version of this card comes with an MCE compatible remote.

if using a NVidia 8500GT card see Envy installation guide - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A) and see 
[http://www.avsforum.com/avs-vb/showthread.php?t=1027557](http://www.avsforum.com/avs-vb/showthread.php?t=1027557) for help on editing xorg.conf.

---

### Post by Dumdideldum on 2008-09-16
Hardware
Motherboard: Epox 8rda+
CPU: AMD Athlon XP2400
RAM: 512MB DDR
Video Card: Geforce FX5200 (using twinview TVout)
Sound Card: Onboard nforce2
HD: several discs, 2 combined within lvm
Remote: SupportPlus SP-URC-89C-0373
Tuners: Hauppauge WinTV PVR150
Country: AT
TV signal type: analog
Version: Mythbuntu 8.04.1 + fixes

Performance
Using proprietary drivers for nvidia and some manual tweaking allowed me to display on TV (CRT) via SCART in a resolution of 800x600.

The mainboard worked without any special work, as far as I remember correctly.
I configured lirc manually within /etc.
Besides that, everything worked like a charm - except acpi wakeup and mythwelcome. It took me several months and several started and stopped tries till I found it working.

I have written a small (and sloppy) howto for Epox 8rda+ users who might find this information helpful:
[Howto](http://justanotherwebblog.wordpress.com/2008/09/09/howto-mythtv-with-acpi-wakeup-and-mythwelcome/)

---

### Post by zapree on 2008-09-16
A bad sound card for linux in general because alsa doesnt have any of their drivers is the Diamond: Xtreme sound 5.1 and 7.1 series, i got it before i had linux and now its giving me ALOT of problems because of the driver :P

---

### Post by db260179 on 2008-09-19
Just to let people know that the Haupuagge Wintv HVR-1110 has the following working/not working:

Working:- DVB-T, Analog TV with sound, S-Video and Composite Video

Not Working:- Analog S-Video and Composite sound (driver issue)

---

### Post by Will May on 2008-09-19
Hardware
Motherboard: Gigabyte GA-73PVM-S2H
CPU: Intel Core&#8482; 2 Quad Q9300
RAM: 4GB DDR2
Video Card: On-board nVidia GeForce 7100 (comes with HDMI connector)
Sound Card: On-board Realtek ALC889A
HD: 400GB & 640GB (both SATA)
Remote: Remote that comes with Hauppauge NOVA-T
Tuners: Hauppauge NOVA-T
Country: UK
TV provider: Freeview
TV signal type: E.g. DVB-S (satellite): DVB-T
Wireless: Edimax 54 Mbps from linuxemporium.co.uk
Case: Antec Fusion 430 (includes small LCD)

Everything works out of the box apart from a few things:

* The LCD required compiling lcdproc ([http://ubuntuforums.org/showthread.php?t=779674](http://ubuntuforums.org/showthread.php?t=779674))
* Sound over the HDMI cable doesn't work but apparently is fixed in the latest version of nVidia's binary drivers, but haven't had a chance to check it out.
* The remote had a few issues such as Mythbuntu not using all of the buttons on the remote and also the remote had a tendency to change its event number which I had to fix using a custom udev rule.

Performance
Takes everything that can be thrown at it.

---

### Post by fiepel on 2008-09-21
**_Hardware_**
CPU: VIA Nehemia C3 (EPIA M10000)
RAM: 512 MB
Video Card: CLE 266
HD: 60 gb hard drive
Tuners:

_**Performance**_
*DOES NOT WORK*
Mythbuntu 8.04 boots and runs desktop. mythfrontend crashes with "illegal instruction". Probably due to "optimized" code. Cannot find a way to properly recompile packages.

---

### Post by lokimon on 2008-09-22
Hardware
Motherboard: biostar TF7050-M2 board
CPU: AMD Athlon 64 x2 4000+
RAM: Corsair Twin2x2048-5400C4 2GB kit
Video Card: built in - HDMI out
Sound Card: built in
HD: WD 500GB SATA2 16mb 7200rpm
Remote: Hauppague
Tuners: Hauppague PVR-350, PVR-150, Firewire connection to DCT2200 cable box.
Country: US
TV signal type: us-cable
Cable Provider: RCN-Digital Cable
Version: Mythbuntu 8.04.1

Performance

works well, captures HD content, and is able to record both HD and standard def content at the same time (have not tried recording 3 shows at once yet.)

had to set the firewire box to broadcast rather then p2p and had to power off both the cable box and the myth box and restart both to get it to work in the end.

---

### Post by GuiGuy on 2008-09-26
Hardware

Motherboard: ASUS M3A
CPU: AMD Athlon AM2 64 x2 4800+
RAM: Corsair 2 x 1024 DDR2
Video Card: ASUS (NVIDIA) 7200GS HDMI out to
DISPLAY: LG 42" LCD High Definition (1080) at 50hz
Sound Card: built in
HDD: 4 X 500G Seagate SATA (unable to sort RAID out)
Remote: MICROSOFT MCE remote
Tuners: 1 X Ultraview PLUS, 1 X DVICO Dual 4, 1 X Hauppage NOVA t-500.
Country: AUSTRALIA
TV signal type: AUSTRALIA - Terrestial
Version: Mythbuntu 8.04.1

The Dvico Dual 4 was a PITA to set up. Everything else worked straight out of the box, more or less.

---

### Post by vixmusic01 on 2008-09-28
Dual Boot Vista + Ubuntu Hardy 8.04
Kernel Linux 2.6.24-19 rt

Hardware:  ASUS notebook computer A8M
Motherboard: Asus 
CPU: AMD Turion 64 x2 Mobile Technology TL-52
RAM: 1.9 Gig
Video Card:NVIDIA GeoForce 
Sound Card: 
HD: 120 G
Remote:
Tuners: no
Country: Canada - notebook originally from Korea
TV provider: E.g. canal digital:
TV signal type: E.g. DVB-S (satellite):

Performance: Built-in webcam and microphone worked fine in Gutsy -- since upgrading to Hardy they don't work. I did post about this, but no one responded.

I have not found any webcam to work yet.

I am now working on ffado drivers and jackd-progress on my blog:

[http://livemorelightly.com/2008/09/21/ubuntu-hardy-free-firewire-drivers-jackd/](http://livemorelightly.com/2008/09/21/ubuntu-hardy-free-firewire-drivers-jackd/)

I do not use the computer for television, but video works fine.

I don't know how to find the hardware list in Ubuntu, so I can't answer every item.

Hope this helps.

Victoria

---

### Post by novellahub on 2008-09-30
** System has now been retired **

**Hardware**
Motherboard: Intel Desktop Board D845GERG2L (mATX)
CPU: Pentium 4 1.7 Ghz [socket 478] 
RAM: 1 GB DDR 400 (512 + 512 running at 266 speed)
Video Card: ATI 9200 (Not used since running machine headless)
Sound Card: On-Board
HD: Two 300 GB Hard drives
Remote: None (Slave ony recording box)
Tuners: Hauppauge PVR-500
Country: United States (Minneapolis / St. Paul Metro area)
TV provider: Comcast
TV signal type: Analog Cable

**Performance**
Fresh install of Mythbuntu 9.10 (Upgraded to 10.04.2) as a slave backend. Both tuners were recognized right out of box.  I did a customized install where the first 300 GB HD has the root partition (/) that uses 10 GB.  The rest of the space on the first  hd was formatted as /myth2 using XFS.  I then formatted the second hard drive using all the 300 GB space as /myth using XFS as well.  Both /myth and /myth2 store recordings in a tv directory.

---

### Post by 0x29a on 2008-10-01
Current distro: Kubuntu 8.04.1 x86_64
Motherboard: HP Pavilion zv5000 (DP523AV CTO) NForce 3 chipset
CPU: AMD Athlon(tm) 64 Processor 3700+
RAM: 1024 MB
Video Card: GeForce4 440 Go 64M 
Sound Card: NForce 3 audio (rev a2)
HD: WD Scorpio 80 GB
Remote: N/A
Tuners: N/A
Country: U.S.
TV provider: N/A
TV signal type: N/A

Edited lspci output:
FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) Functionality unknown. Never tried it.
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Wireless controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
PCMCIA Slot: (CardBus bridge): Texas Instruments PCI1620 PC Card Controller (rev 01) Functional under SuSE
Card Reader: (CardBus bridge): Texas Instruments PCI1620 PC Card Controller (rev 01) Non-functional under Linux (any distro)

Fail Summary: Card reader has never worked under any distro of Linux. Broadcom 4306 requires windows driver using either ndiswrapper or fwcutter. Proprietary Nvidia driver works perfectly under SuSE. Under Kubuntu, not so much. Have yet to get it to load under Kubuntu.

---

### Post by Baka no Kami on 2008-10-02
Distro: Mythbuntu 8.04.1 x86
Motherboard: Shuttle st62k (Shuttle Zen)
CPU: 3.0Ghz Pentium 4
RAM: 512 MB
Video Card: Integrated ATI Radeon 9200
Sound Card: Integrated Realtek ALC650
HD: Lexmark Firefly 4GB thumbdrive
Remote: Snapstream Firefly
Tuners: Hauppauge WinTV-PVR-150
Country: U.S.
TV provider: N/A
TV signal type: Would be NTSC.

Performance
Chose standard install. Could not complete backend setup at end of install because mythtv user was denied access to mysql. 
Attempted to change password and found that mythtv user was never added. Ran 'dpkg-reconfigure mythtv-database' which added the user (didn't check if mythtv database had been created before), but I still had to manually set the password before MythTV could start.

Chose Snapstream remote during setup, but the config files installed didn't work. Remote worked fine after downloading new config files.

---

### Post by sekeunzer on 2008-10-06
Machine 1 (Master Backend+Frontend):
Hardware 
Motherboard: VIA J7F4
CPU: VIA C7 1200MHz
RAM: 1024 MB
Video Card: onboard
Sound Card: onboard
HD: Samsung HJ501
Remote:
Tuners: Hauppauge WinTV HVR 1300 (RC not tested yet)
Country: Germany
TV signal type: DVB-T

Machine 2 (Diskless Frontend):
Hardware 
Motherboard: (Laptop FS Amilo)
CPU: Centrino (Dothan) 1700MHz
RAM: 1024 MB
Video Card: ATI mobile
Sound Card: onboard
HD: local not used, uses nfs-install (see [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto))

Performance

-had problems with HVR 1300 and onboard grafics on early 8.04(-kernel)-versions, 2.6.24-19 works perfect now

-watching TV/Video on Machine 1 ok, no problems (70-90% CPU-Load)

-streaming TV/Video to Machine 2 ok, no problems
(Machine 1: 15-30% Load, Machine 2: ca. 30% Load)

-watching TV/Video on Machine 1 and streaming to 2 ok, no problems, even when watching different TV multiplexes
(Machine 1: >80% Load, Machine 2: ca. 30% Load)

-activated ATI proprietary Driver on Machine 2: NOT GOOD!
(CPU-Load on Machine 2 nearly 100%, TV/Video freezes)

-hardware-knob for volume on Machine 2 doesn't work

-tested Live-CD-Frontend on Machine 2 via wlan b/g and that was working ok (throughput with iperf: 6-20 MBit/s)

-Fast Ethernet vs Gigabit Ethernet: no differences

---

### Post by mark467 on 2008-10-11
Hardware
Motherboard: Intel DG31PR
CPU: Intel® Celeron® Dual-Core processor E1200
RAM: 1 GB 667mhz DDR2
Video Card: PNY GeForce 8400gs PCIe
Sound Card: Intel® High Definition Audio 5.1 Realtek* ALC888 audio codec

HD: WD 500 GB SATA 2
DVD: Sony DRU-V200S/BR DVD/CD Rewritable Drive
Remote: ATI Remote Wonder
Tuners: ATI TV Wonder
Country: USA
TV provider: Comcast
TV signal type: Analog Cable

Performance:
Works Great. Ripping DVD's While recording tv no problems. The onboard LAN and audio auto detected and work great. The remote is so-so not all buttons work. This is my 2nd attempt for this backend. Had hardware issues with first one (will post as non working setup)

---

### Post by mark467 on 2008-10-11
Hardware
Motherboard: Asus P5GC MX
CPU: Intel® Celeron® Dual-Core processor E1200
RAM: 1 GB 533mhz DDR2
Video Card: PNY GeForce 8400gs PCIe
Sound Card: Onboard Realtek ALC883 audio codec

HD: WD 500 GB SATA 2
Remote: Pinnacle MCE Remmote
Tuners: ATI TV Wonder
Country: USA
TV provider: Comcast
TV signal type: Analog Cable

Performance:
Lots of issues. The onboard Atheros chipset LAN would reset a lot and the onboard audio never worked right. Bad choice for a MB I guess. I could never get the pinnacle remote to work. Replaced the MB and remote.

---

### Post by rusty0101 on 2008-10-12
Have had a couple of revisions to the platform setup here.

Beas has been updated a couple of times, and a couple of months ago the video card ignited. I was able to pull the hard drives and one of the video capture card. I ended up replacing the case, motherboard, and processor. From /proc/cpuinfo:
model name	: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz

For storage I have 2 1 terrabyte Western Digital green SATA drives, running in quiet mode Also 2 500 gig drives in external sata housings. Booting off of a 400 gig PATA drive where the home directory is.

Audio is currently through a sound blaster usb interface, feeding into a Yamaha sound system via a fiber optic link.

Video is through an ATI 3200 hdmi enabled card. The motherboard has a nVidia 5100 card on board, which should be sufficient, (has a DVI port even) however for some reason it's comming up in lower resolution modes only. (Vesa 800x600 max) The ATI is outputting 1920x1080x60 into a projector. Native resolution on the projector is 1024x768, so the 1920x1080 is an illusion, but it still looks good.

Currently 1 internal capture card, a pvr-250. 2 external HDHomeRuns, 1 with an antenna for local TV, the other on the cable capturing a few channels there. Trying to get a couple of other video capture devices going. Would rather have a second (preferably third as well) analog capture device. I have a Pinnical usb hdtv/analog tv capture device, (I forget the model) and a hvr-950, both of which should work, but I have to work on them yet, they are not being recognized properly yet.

Note on the audio situation. I ran into the problem where I wasn't sure which card would be which after a boot. However if you type 'cat /proc/asound/cards' I get the following:
```

rusty@beast:/proc$ cat asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe9f8000 irq 11
 1 [External       ]: USB-Audio - SB Live! 24-bit External
                      Creative Technology SB Live! 24-bit External at usb-0000:00:04.0-4, full speed
 2 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfeaec000 irq 7

```

Where "External" always refers to that SB interface. In setup general on the third page (the one for 'Audio') I set 'Audio output device:' to "ALSA:hw:External" to specify which interface to use. (Note that this interface does not have any volume control built into it. Mute does not work, I do all audio level adjustment on the Yamaha Tuner.) For video playback I have added "-ao alsa:device=hw=External,0" to the mplayer commands.

Still using the StreamZap PC Remote, as well as a usb keyboard (primarily for editing video, it's faster.)

Occasionally I'm using my PS3 as a front end. It's primary purpose in life is as my Blue Ray disk player. (Contemplating adding a Blue Ray drive to beast, but I have no idea how long it will be before BR playback will be available.) The built in software for the PS3 does recognize the Mythbuntu box as a media server, and can play most of the content. It doesn't recognize .nuv files, and occasionally has issues with audio in mpeg files though, so .avi files tends to be what I'll use it for most as a front end.

I've brushed the dust out of George, and replaced the motherboard in him. He's now my video re-encoder box. I'll transfer a movie that I've edited the comercials out of and re-encode to avi the movie on him. Currently running headless.

Laptops and desktops around the house have Mythtv Front End installed on them, and once the 8.10 release happens, I'll migrate all of them. Too many to itemize though.

Added 2 entries to the mythtv portion of the streamzap lircrc file. The Yellow button doubles as the 'w' key, and the Blue button doubles as the '_' key. The former allows me to cycle through the fill sizes, and the latter allows me to select digital tv station sub channels. I'm thinking about setting the Green button to be a double for an '#' key for digital cable channels, and the Red button to 'd' to delete recordings.

For the most part everything is working. Things I would consider changing though include moving storage into an external box. Possibly George. The issue is that as well as I do have things woring, I occasionally encounter issues, that require a reload of the box. Checkdisk on a 1T drive takes a while.

---

### Post by johnsoak on 2008-10-14
_Hardware_

Backend - Only Configuration – Front ends standalone
(Server runs headless in storage space SSH & VNC installed)

Motherboard: 	Asus A8V Deluxe (5 PCI Slots)
CPU: 		AMD Athlon64 X2 3800
RAM:		2Gb DDR400
Video Card: 	Matrox Millenium G400 AGP (only used for set up)
Sound Card: 	On Board Realtek ALC 850 8 Channel CODEC
LAN             Marvell Gigabit (connected to 100Mb Switch)
HD1: 		Seagate ST3160021A 160Gb - System (ext3) - Covers, LiveTV, Music (xfs)
HD2:		Samsung SP2514N 250Gb - Videos, Recordings (xfs)
Remote:		Not Required
Tuners: 	3 x Nova-T-500 & 2 x Nova-S
Country: 	UK
TV provider: 	Freeview & Sky
TV signal type: DVB-T & DVB-S
Software Ver:   0.21.0+fixes18207-0ubuntu4~hardy1


_Performance_

Everything was detected and installed “out of the box” with the exception of the LNA activation for the Nova-T-500s
The Nova-T-500s require a very good aerial / antenna signal to give good performance – with a mediocre signal blocking and dropped frames are very evident.

They also require a clean signal, so if you need to use a booster, make sure that this is as close to the aerial / antenna end as possible otherwise you amplify the noise too!

Not yet seen any issues using all of the tuner cards and am running with 2 streams per card option enabled.

Watching 3 LiveTV streams simultaneously whilst recording two DVB-T streams does not seem to strain the CPU

One of the easiest installations I have carried out – required some fiddling with shares to get the frontends to talk to it, but this is well documented elsewhere – lots of tweaks to Fes to match my requirements but am still working on these!

Will upload FE details once tested!

---

### Post by Slate8 on 2008-10-14
**Hardware**
Motherboard: Asus K8VSE Deluxe
CPU: AMD Athlon 64 3200
RAM: Corsair 512MB DDR X 2 (1Gb)
Video Card: nVidia 7600Gs
Sound Card: Onboard ADI AD1980 (Analogue Stereo output)
HD: Western Digital Raptor 74GB 10,000RPM SATA 8MB Cache
Remote: MCE V2
Tuners: Hauppauge Nova T-500 PCI
Country: United Kingdom
TV signal type: Freeview

**Performance**
Mythbuntu 64-bit works without issue. All hardware detected and working upon install when connected to monitor. Change over to Domino 20 DLP projector but correct resolution not detected on reboot (640x480 was the only choice). Had to manually enter refresh and resolution in Xorg.conf. Setup cloned output to tv (s-video) and projector (vga) with nvidia-settings. Everything working great now.

---

### Post by codered867 on 2008-10-20
Hardware
Motherboard: ASUS M3A78-EM AM2+/AM2 AMD 780G HDMI Micro ATX AMD 
CPU: AMD Athlon 64 X2 5000+ Brisbane 2.6GHz Socket AM2 65W Dual-Core Processor
RAM: G.SKILL 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel
Video Card: Built-In ATI 3200HD
Sound Card: On-Board
HD: Western Digital Caviar SE16 WD6400AAKS 640GB 7200 RPM SATA 3.0Gb/s
Remote: Anyware GP-IR02BK
Tuners: SiliconDust HDHomeRun, Motorola DCH3200 FireWire
Country: US
TV signal type: us-cable
Cable Provider: RCN-Digital Cable
Version: Mythbuntu 8.10 beta

Problems:
After enabling the restricted AMD driver mythtv-frontend would start up completely distorted. I found that a few other people had this problem and was able to fix it by running it 1919x1200 instead of 1920x1200. In order to get the Motorola DCH3200 working I followed this guide [https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire) and was able to get everything working including switching channels through the firewire port. The last problem I encountered and still have is when I switch to a SD channel after watching a HD channel the frontend either crashes out or channel is completely distorted, this seems to just be a front-end problem.

Working:
Everything else worked pretty much out of the box. The HDHomeRun tuner was simple to set up and had no problems picking up unencrypted QAM. Also thank you RCN for not having any 5C encrypted channels I'm loving recording all my premium channels at full 720p :).

---

### Post by fryed_1 on 2008-10-24
Motherboard: [forthcoming]
CPU:  P4 2.4Ghz
RAM:  2Gb Crucial DDR
Video Card:  Nvidea Gforce 6200
Sound:  On-Board
HD:  4x500Gb WD Sata 7200rpm
Remote:  PVR-150 MCE Remote (labeled RC6 Gateway Remote)
Tuners:  (2) PVR-150 MCE, (1) Kworld BT878
Country:  US
TV signal type: us-cable
Cable Provider:  Comcast
Version:  Mythbuntu 8.04

Problems:
Everything works great.  Recording two shows and watching a third tends to introduce a little skipping on the live show, but doesn't effect recordings.  IR blaster still doesn't work.  Occasionally the sound will take on a veyr thin and distorted sound (1/20 times of changing the channel maybe), but changing to a different channel and back again usually fixes this

Working:
Everything else.

---

### Post by Something Other on 2008-10-30
Hello everyone, thanks for all this awesome information.  I have a question.  I want to set up mythbuntu on my current machine.  I am going to be using only over the air signal and the majority of the stations I get are in HD.  My goal is to be able to record one channel and still be able to watch another.  If price is not a worry, what tv tuner cards would you recommend?  I take it I would need 2 in order to accomplish my goal.  Any and all help is much appreciated!  Thanks.

---

### Post by thepizzaman on 2008-10-30
Hardware
CPU: AMD Athlon X2 5000+ 2.6ghz
RAM: 2gbs ddr2 dual channel PC6400
Video Card: ATI Radeon HD3450 and ATI Radeon 2100
Sound Card: Relteak HD onboard sound
HD: 320 Western Digital SATA2 and 500 Seagate SATA2 
Tuners:AVerMedia MCE1500 (not working, yet....)
Country: US
TV provider: Time Warner Cable
TV signal type: Cable

---

### Post by mark467 on 2008-11-04
*** Update at end of post****
I just bought a cheap Trendnet TEG-PCITXR GB NIC and Dlink DGS-2208 GB 8 port switch. The trendnet worked out of the box with Myth and I have a big jump in speed for little money.\
Trendnet card $15 and Dlink switch $55 from compusa (tigerdirect)
My main muthbox has intel onboard gb nic. Here are the iperf results from gb nic and switch and then my onboard 10/100...

Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.25 port 5001 connected with 192.168.1.169 port 34429
[  4]  0.0-10.0 sec    694 MBytes    580 Mbits/sec
[  5] local 192.168.1.25 port 5001 connected with 192.168.1.26 port 51543
[  5]  0.0-10.2 sec    114 MBytes  94.1 Mbits/sec


**************Update
spoke to soon. i am having a problem with videos (dvd ripped to iso) stuttering slighly, also transfering the same file between 2 intel onboard gb nics took 1m 80s and between trendnet and intel took 10 min (which is longer than it took between to 100mb intel nics

---

### Post by volaer on 2008-11-11
**Laptop Specs**
Processor Type: Intel Celeron M 575 (2.0GHz, 1MB, 667FSB)
	
Chipset: Mobile Intel® GL40 Express Chipset
Memory: 1GB DDR2 RAM

Video Type: Intel® Graphics Media Accelerator 4500M with up to 1759 MB of Intel DVMT 5.0 (64 MB of Dedicated Memory, up to 1695 MB of Shared Memory )
	
56K Modem and Gigabit LAN
Wireless LAN Built in Wireless LAN (802.11a/b/g/Draft-N) Wireless (Atheros AR5B91 Wireless Network Adapter)

Card Reader:   Built in 5 in 1 Card Reader
Built-in Camera: Acer CrystalEye Webcam

**Performance:**
My laptop freezes, whenever I play video files including mp3 and sounds that will use visualization. Everything in my desktop freezes except my mouse cursor. Even the cntrl-alt-delete function freezes. so i don't have any choice in rebooting my laptop except to take off the battery....

My wireless connection (the Atheros) also doesn't work. How am I going to enable it???

please help...

---

### Post by laffinet on 2008-11-17
Motherboard: Asus M2N68-VM
Processor: AMD AM2 x2 5000+
Graphics: Nvidia Geforce 7Series (onboard)
Hard drive: 320G SATA Western Digital
Memory: 2G 667MHz
TV card: Leadtek DTV2000H Rev. J
Network: D-Link DWA-510 wireless
Remote: Rock MCE Remote
DVD: some Samsung 20x DVD-RW SATA
Case: Antec NSK2480B
Power supply: incl.

Issues: 
- got tired trying to get the Leadtek remote to work so bought the ["Rock" MCE remote]("http://www.pcworld.idg.com.au/index.php/taxid;2136212606;pid;4896;pt;1"), worked out of the box
- ensure that HDMI is connected while installing Mythbuntu, hard to get working otherwise
- newest NVIDIA driver causes live TV to freeze, one version down (forgot number) works without problems
- had to modify xorg.conf to make sure correct resolution is selected

Other: thinking about buying a Scythe Mini Ninja CPU cooler to reduce noise, not sure if it fits on the motherboard though.

---

### Post by gdir on 2008-11-22
This is my combined back- and frontend running Mythbuntu 8.10:

_**Hardware**_
Model: Asus EEE Box B202
Motherboard: Intel 945 GSE
CPU: Intel Atom N270 1.6 GHz, running at 1.75 GHz
RAM: 2 GB 
Video Card: Onboard Intel GMA950
Sound Card: Onboard Intel
HD: 160 GB 2,5" 5400 RPM (Seagate ST9160310AS)
External HD: 2 x 1 TB WD MyBook, configured as RAID1 (mdadm)
Remote: iPod Touch running MyMote
Tuners: WinTV Nova-TD-Stick (USB stick with dual DVB-T tuner), IR receiver not recognized
Country: Germany
TV provider: German DVB-T 
TV signal type: E.g. DVB-S (satellite): DVB-T, 1024x576/720x576
TV: Panasonic Viera 32" LCD (TX-32LE7F/S)

**_Performance:_**
Backend role:
The EEE Box B202 performs very well as MythTV backend. With the Nova-TD-Stick it is able to record two (even up to four) streams of DVB-T simultaneously without getting much load. Of course, that's not in HD resolution, but just 1024x576 or 720x576. Commercial flagging takes about half the time of the original recording. 
The Nova-TD-Stick has two individual tuners. If have MythTV configured to record up to 2 channels (on the same multiplex) on each tuner. So far I have used up to three streams at the same time (1x LiveTV, 2 x recording)

Frontend role:
If have connected the EEE Box to the TV with a DVI->HDMI cable. It was very difficult to get a useful signal to the TV. The native resolution of the TV is 1366x768, but I was only able to send 1280x720 to it. There is still about 5 mm  underscan on the top right and even more overscan in the lower left corner. MythTV uses about 1220x680 pixel.

In the first days I wasn't satisfied with the image quality in LiveTV (I'm comparing it to the analog cable tuner of my TV). Some channels were good (better than the analog tuner), others showed MPEG artefacts. After several tests I found out that it's not the fault of the slow EEE Box, but caused by heavily compressed DVB-T-MPEG streams. Some channels use MPEG streams with very low bandwith. These shows the MPEG artefacts.

I have spend some time to get XvMC working on the GMA950, but finally decided against hardware accelareted XvMC and Bob deinterlacing. The image quality of ffmpeg and Yadif or GreedyH is better. During the playback Mythfrontend.real uses about 40-50% CPU, the load is about 1.0 - 1.5.

General information about the EEE Box:
The EEE Box sits near the TV in the living room. It is extremly silent. Although the CPU is overclocked to 1.75 GHz, the fan stays very calm. The box doesn't get warm even under heavy load. The hard disk is silent, too. 

**_Problems/To do:_**
- The IR receiver of my Nova-TD-Stick is not recognized. There seem to be two different revisions of this stick. On one revision the IR receiver works, on mine not.
- After a reboot mdadm fails to assemble the RAID1 automatically. At the moment I have to assemble it manually after a reboot. If seen similar bug reports on launchpad.
- I am working on a problem with DPMS: As far as I can see DPMS is disabled by MythFrontend while watchting TV or a recording. After stopping the playback, when the frontend menu is displayed, DPMS is enabled again. When I'm in the menu, the power saving starts after some idle time. I can wake up the display by pressing the space bar on the keyboard. But I am unable to wake up the display with MyMote. MyMote communicates with the frontend through the telnet interface. When the display is in power save mode and I try to switch to live TV with MyMote, the communication between the front an backend fails. I will try to work out the details in the next days.
- If anyone has an idea how to improve image quality with Intel GMA950 XvMC or on the other hand reduce CPU load while using ffmpeg, I would be very thankful.
- I'm thinking about switching from DVB-T to DVB-C (german provider Kabel Deutschland). I hope to get MPEG streams with better quality there. But so far I haven't found out which external DVB-C tuner would work with Mythbuntu 8.10. It needs to be connected with USB. For all non public channels I would need a CI, too. Anyway, it would like to test any USB DVB-C tuner with or without CI, as long as the linux driver works.

So far,

Guenther

2008/11/25 Update:
I'm still working on the image quality of the frontend. I'm testing several playback profiles. The EEE Box is possibly too slow for certain deinterlacing operations.

---

### Post by ak2534 on 2008-11-24
**Hardware**
Motherboard: Asus A7N8X-E WiFi
CPU: AMD Athlon XP 3200+
RAM: 3x512M DDR400 (1,5G)
Video Card: Ati Radeon X1950Pro 512Mb AGP
Sound Card: On-board sound
HD: Hitachi 120GB
Remote: Technisat
Tuners: Technisat Cablestar 2 PCI (does not work)
Country: Finland
TV provider: Welho
TV signal type: DVB-C

**Software**
Mythbuntu 8.10

**Performance**
Tuner does not work.

"b2c2-flexcop: no frontend driver found for this B2C2/FlexCop adapter"
lspci lists the tuner card as Airstar 2 PCI, not Cablestar 2 PCI

**Previous working distribution**
The card seems to get detected correctly in MythBuntu 8.04.1.
So it seems that the support for the specific card was dropped out in 8.10. The question remains, why?

---

### Post by d_morgan on 2008-11-25
Hardware
Motherboard: Shuttle SG33G5
CPU: Intel Core2 Duo E6750 (2.66 GHz)
RAM: 2x 1GB DDR2-800 (total of 2GB memory)
Video Card: On board (intel g33 chipset / intel gma 3100) 
Sound Card: On-board sound (intel g33 chipset / intel hd audio controller) 
HD: 1 TB
Remote: Technisat
Tuners: Haupauge HVR-1600
Country: US West Coast
TV provider: Broadcast over-the-air ATSC
TV signal type: ATSC (NTSC selected in myth)

Software
Ubuntu 8.10 but using mythbuntu control centre
Myth 0.21.0+fixes18722-0ubuntu1

Performance
Great.

Working on
ACPI shutdown and wakeup timers
irc control of my surround amplifier
wine or virtual machine of winxp for netflix instant watch

---

### Post by jeff45 on 2008-11-27
[SIZE="3"]All systems are still in experimental/tweak stage[/SIZE]
*currently, all my programming is OTA NTSC(a little side note for clarification)*


**_Backend:  _**Dell Poweredge 2450 server 2U(no I'm not kidding)

**CPU:  **2 - PIII, 1 Mhz, 256K cache
**MB:  ** Dell 35XYT, Dell PERC 3/Di: SCSI-3 Raid controller, 3-64/32bit PCI riser, onbaord VGA 8MB/2x USB/LAN/2x PS2/2x serial/1 par.
**Memory:  **1GB, ECC (2 x 512MB), 133 Mhz
**HD:  **4 x 9.1GB SCSI-UW2 in raid0=36GB(sys), 1 x 250GB IDE (seagate), 1 x 320GB  ext USB (seagate) 
**Tuner Card:  **1 x Happauge PVR 150 PCI, 1 x Kworld HD Plus 120 PCI(doesn't work, yet)

**_Performance:  _**All hardware functioning except the Kworld card.
Once I got Ubuntu/Myth installed and setup backend(a couple of hurdles, although nothing linux/ubuntu related.)everything works great on OTA NTSC programming using the PVR 150.  However, I'm still working on getting the HD plus 120 working - would like go "HD" w/ myth.  Obviously, I'll have to upgrade my frontends to support "HD", but was hoping my current backend could handle it.  I'm confident that I could run 2 more NTSC encoding tuners without problems.  I did try an external USB drive set up as my default recording folder and the recordings turned out choppy w/ dropped frames - now its backups only.

**_Frontend:  _**Salvaged Sony VAIO

**CPU:  **PIII, 933 Mhz, 256k L2.
**MB:  **ASUS(sony branded) CUSL-LV w/ snd, lan,2x USB
**Memory:  **512MB (2x 256B)
**HD:  **40 GB IDE, 80 GB IDE (windows XP)
**Video:  **nVidia MX400, 64MB
**Tuner Card:  **none

**_Performance:  _**All hardware works except an ATI TV wonder USB wireless remote.
Playback/liveTV is fine till I open another window like firefox browser, then it will drop a few frames here and there.  I use this interface more for managing recordings than viewing, so its really not an issue.  The ATI remote wasn't a priority - I just had it lying around and thought why not.  I think it'll work eventually.

**_Frontend 2:  _**Softmodded Xbox

**Info:  **Other than dashboard/software, everthing else is original Xbox

**_Performance:  _**XBMC works great, but...........
Softmodded and installed XBMC no problems.  Unable to install myth or get the mythtv python script to work on XBMC (tried many methods many times).  However, Video playback is exceptional - Hardware MPEG2 decoder?
One other small glitch I've noticed is when exiting a video, sometimes it takes about 30-45 sec to return to the folder and it appears empty.  I then have to go back one folder and return to see my recordings - not sure if this is backend storage issue or xbox config.

---

### Post by drifting on 2008-11-30
Backend Hardware 
Motherboard:Asus M2NSLI
CPU:AMD 3800 X2
RAM:8GB
Video Card: Nvidia 7800
Sound Card:Nvidia (not used)
HD:4TB total,4 x 1TB Seagate Sata disks
Remote:none
Tuners:Nova-T500,2 x Nova-S
Country:UK
TV provider:Freeview, Freesat
TV signal DVB-T.DVB-S

Performance
Works very well, although random stopping of Myth backend, even plays back h264 well (BBC-HD)

Hardware Frontends
Motherboard:Asrock AliveNF6P-vsta
CPU:AMD X2 3800
RAM:2048
Video Card:inbuilt nvidia 
Sound Card:inbuilt (unknown as yet)
HD:Sata 80GB
Remote:MS MCE USM
Country:UK

Performance
SD TV perfection, sound, good, works very well, very high GF acceptance, HD pauses BBC-HD(wished I knew why?) Mythstream does not work (no urls)

Other than the over which I consider minor irritations, I love my Mythbuntu to bits.

Paul.

---

### Post by ACGarib on 2008-12-03
Both the backend and frontend are installed on a laptop running Ubuntu Intrepid Ibex.

Hardware
Dell Vostro 1500
CPU: core2duo T7300 2GHz
RAM: 2 GB
Video Card: Nvidia 8400m GS
HD: Just using Laptop screen at 1440x900
Remote: came with the tuner
Tuners: Hauppauge HVR-1950
Country: US
TV provider: University of Delaware
TV signal type: NTSC cable, QAM256 digital cable

Performance
NTSC and QAM work. Audio is out of sync every now and then, but it's usually fine. Video is usually smooth, but sometimes it will momentarily stutter, both SD and HD. I don't get any ATSC signals so I can't try that. Have not tried the Svideo input yet either. The remote works, but it's laggy and sometimes I have to push the button twice for it to register. Since I'm only a foot away from the screen, I just use the keyboard anyway.

---

### Post by richard.e.morton on 2008-12-17
Hardware
Via Mini-ITX SP13000
CPU: Via Nahelem 1.3Ghz - soldered on board
RAM: 512MB
Video Card: onboard
HD: 1200 x 800 resolution screen - no HD playback attempted

Tuners: None
Country: UK
TV signal type: Freeview Terrestrial DVB 

Performance
A bit of a bizarre one, when using SP13000 to watch TV from remote MasterBackend, the playback is jittery, as it is with DVD VOB video playback. After considerable investigation and trial and (lots of) error (still not working) there was comments that an Myth .20 on FC7 worked with this board. I have installed MythDora5 (based on FC8) and rather than the CPU maxing out during playback it now works with about 70% utilisation.

This is connection to a Mythbuntu master backend currently. But I want only have to learn and use a single distro.

Hope that helps someone - and I look forward to Mythbuntu working with this board.

---

### Post by rokrbo on 2009-01-02
Hardware
Motherboard: Gigabyte GA-EG43M-S2H
CPU: Intel E5200
RAM: 2 Gb
Video Card: onboard
Sound Card: onboard
HD: WD 640Gb
Remote: Technisat
Tuners: Technisat Skystar 2 Rev. 2.8
Country: Germany
TV provider: Astra 19.2E
TV signal type: DVB-S (satellite)

Performance
Installed Jaunty Alpha, patched and compiled custom kernel for the open-source driver for the Skystar 2 Rev. 2.8 driver. Works smoothly.
Configuration of remote still makes trouble.

---

### Post by user11 on 2009-01-02
Xubuntu (8.04.1/8.10) in a Compaq Presario 5030

Specs on my PC:

Intel Pentium II processor - 300 MHz

256MB pc100 ram

12 GB hard drive

44X Max CD-ROM drive

Integrated ATI 3D Rage LT Pro (64-bit Hardware Accelerated 3D Graphics)
2 MB 100 MHz SyncGraphics video memory (upgradable to 4 MB)

"Aureal A3D Interactive 360 Positional Sound"
According to Compaq driver download section, the integrated sound card is the ESS 1869, 1887, or 1888 Audio chipset.

Sound card complete MIA, video card can not be optimized with ATI driver but functional. All options and resources exhausted for the sound card.:confused:

---

### Post by tad1073 on 2009-01-02
[My Computer]("http://support.gateway.com/s/PC/DX/1015694R/1015694Rsp3.shtml")


_**Hardware**_
**Motherboard: **Yes
** CPU:** Intell Core 2 Quad Q6700
**RAM:** 6 gb
**Video Card: Nvidia Geforce 9500 GT**
**Sound Card: Dynex 5.1 Surround w/ Optical Audio Out**
**HD:** WD 640 gb
**Remote: none**
**Tuners: none**
**Country: United States**
**TV provider: Comcast**
**TV signal type: DTV**

_**Performance**_

No problems thus far.

---------------- Now playing: [Incubus - Nice to Know You]("http://www.foxytunes.com/artist/incubus/track/nice+to+know+you") via [FoxyTunes]("http://www.foxytunes.com/signatunes/")

---

### Post by grif.ghatak on 2009-01-03
[B]Hardware
Motherboard[/B]: Intel i810 M6TWG
**CPU**: Intel Celeron Coppermine 850 MHz
**RAM**: 128x2 SD RAM
**Video Card**: Integrated 3d Accelerator
**Sound Card**: Intgrated
HD: Samsung SV200 something.. 20GB
**Country**: India

This is a very old system (6 years old) and I had only 1 problem that my Serial mouse was not detected and since my P/S2 mouse port is faulty therefore I could not replace that with a new P/S2 mouse.

Although I found a way to get it work by tweaking the xorg.conf file but I think that it should have had provisions to detect it automatically.

I've used Puppy Linux, Mandriva, Knoppix etc. and it was easily detected in all of them.

---

### Post by stollefsen on 2009-01-05
Hardware
Motherboard:ASUS P5LD2-VM
CPU:	Intel(R) Core(TM)2 CPU 4300 @ 1.80GHz
RAM: 2 Gig SDRAM
Video Card: 82945G/GZ Integrated Graphics Controller
Sound Card: 82801G (ICH7 Family) High Definition Audio Controller
HD: ST3320620AS
Remote: HAUPPAUGE PVR-350 , USB-UIRT
Tuners:HAUPPAUGE PVR-350
Country: Canada
TV provider: TELUS TV
TV signal type: NTSC-A From SA IPN330 set top box

Performance:

Installed Mythbuntu 8.10.  Cannot use PVR-350 with  tv out and x-out nor USB-UIRT on initial GUI installation. 

I can get the PVR-350 out on the tv to work by manually configuring  my xorg.conf. 

But, I have been unsuccessful in configuring remotes and LIRC using myth-control and in determining root cause for LIRC configure to cause PVR-350 remote from receiving properly and for USB-UIRT to transmit properly.

---

### Post by earlycj5 on 2009-01-10
**_Hardware_**
Case: [Silverstone LC-19](http://www.silverstonetek.com/products/p_contents.php?pno=lc19)
Motherboard: ASUS M3**_N_**78-EM AM2+/AM2 NVIDIA GeForce 8300 HDMI Micro ATX AMD
Processor: AMD Athlon X2 4850e 2.5GHz Socket AM2 45W Dual-Core
RAM: 2GB
Tuner: Hauppauge WinTV-HVR 1800 MCE
Hard Drive: 1TB SATA.
Country: USA
TV Signal: OTA digital

**_Performance_**
Everything seems to work well.  Initially I had the ASUS M3A78-EM motherboard, the ATI drivers were just headaches so I bought the M3N78-EM and use the on-board NVIDIA GEForce 8300 graphics. The case only allows for one card so I selected a motherboard that had HDMI out.  Sound off the motherboard is fine as well.  

I use this as a combined front/back end.  I set the tuner up with the help of the howto from theduke88 here: [http://ubuntuforums.org/showpost.php?p=6129026&postcount=132](http://ubuntuforums.org/showpost.php?p=6129026&postcount=132).

After that it was pretty easy but I've been using Linux for several years already.  I use this for OTA digital, no cable or satellite.

Oh, I've not checked for sound over HDMI, I've plugged directly into the MOBO for sound.

Update, it is capable of recording HD and playing HD recordings at the same time.

---

### Post by oldpgmr on 2009-01-11
Hardware
Motherboard: Machspeed P4M800
CPU: Intel Celeron 2.4Ghz 
RAM: 1 gb
Video Card: NVIDIA GeForce 7600GS 256 mb
Sound Card: VIA Chipset
HD: 
Remote: N/A
Tuners: Hauppauge PVR-150
               Firewire to DCH3200
Country: US
TV provider: Comcast Digital:
Performance under 8.10
All hardware properly detected and functional.
Had to install nvidia proprietary drivers to prevent general choppyness
HD content recorded from Firewire (when it worked) could not be played back through the TV properly but could be viewed as a stream.

---

### Post by ikke2808 on 2009-01-14
**_Hardware_**
**Motherboard:** Gigabyte GA-M78SM-S2H
**CPU:** AMD Phenom 8650 Triple-Core 2,3 GHz
**RAM:** 4 GB, Corsair TWIN2X 6400 DDR2
**Video Card:** Onboard GeForce 8200
**Sound Card:** Onboard
**HD:** 1 TB Samsung SpinPoint F1
**Remote:** TechnoTrend on card (not fully working yet)
**Tuners:** Technotrend C-1501-CI
**Country:** The Netherlands
**TV provider:** Ziggo
**TV signal type:** DVB-C

_**Performance:**_
Basic functionality is working, after some initial problems on locking certain frequencies. The remote is less configurable then expected, but still working on that. Bluetooth keyboard is not connected automatically on boot.

---

### Post by AHanff on 2009-01-14
**Hardware** (Backend Only)
HP T5700 Thin Client modded as follows:

PCI Extender Module (Addon for the Case to allow a PCI card to be fitted)
250GB IDE 2.5" HDD
512MB PC2700 RAM
Hauppauge PVR-150
Dusky Control (for controlling Sky STB)

**Performance**
During Recording the system load creeps up to about 0.18, when not recording system load is 0.00 (GDM has been stopped and the system is running headless with SSHD and MythWeb Plugin for management).

All encoding is handled by the PVR-150 so no CPU overhead other than I/O for the HDD.

System runs at 12 Watts during recording and less when idle.

I originally set this up as an experiment to see if it would work and now that it does it will remain as my HTPC for some time to come (until I can afford the NVidia Ion platform) - for a low power energy efficient system I think this is hard to beat.

It should be noted that this system will only work with SD and would not be suitable for HD.

The other advantage is all the hardware is cheaply available on eBay.

I needed to make a few modifications to get this to work.  The HP T5700 ships with a Flash DOM with Windows XP SP2 Embedded and only 256MB RAM.  Obviously I needed to remove the Flash DOM (which is connected to a 44 Pin IDE connector - Laptop size) and replace it with a HDD for this you need to get a 44pin to 44pin IDE cable - I picked one up for $5 on eBay (2.5" long which was more than enough).

I made some changes to the chasis too to make connecting the IDE Drive easier by cutting an access "whole" with my dremel.  I currently have the HDD mounted on the inside of the chasis and it sits about 5mm above the PVR-150 but with a long IDE cable the drive could be mounted on the outside of the chasis however this would require modifying the case with a dremel by cutting out a square piece the size of the HDD where the cooling grill is and replacing it with a mesh grill which can be pushed out slightly (embossed) to allow the HDD to sit nicely.  Although this really is not needed as heat is not an issue.

Another thing to note is the BIOS in this machine will only support upto 512MB RAM, so don't make the mistake I made and buy a 1GB Stick as the system will not boot.

I used Unetbootin to put the MythBuntu ISO onto a bootable USB pen drive for installing.

Alexander Hanff

---

### Post by GuiGuy on 2009-01-17
I'm approaching a year since I scrubbed all trace of Vista from the home entertainment center and replaced it with MythBuntu. I thought it's time to report back:

BACKEND 

LOCATION: AUSTRALIA 

MOBO: ASUS MA3
CPU:  AMD AM2 4500+
RAM:  KINGSTON 2 X 1G
HDD:  4 X 500G Seagate SATA
VIDEO: NVIDIA 7100GS 
NETWORK:  Onboard Ethernet adapter
TUNERS:   2 X ULTRAVIEWS PLUS DTV (Dvicos in disguise)
          1 X DVICO FUSION 4 DUAL DIGITAL 
          1 X HAUPPAGE NOVA T-500 DUAL TUNER

Backend runs headless via a NETGEAR  RANGEMAX router

Main frontend  
MOBO:   ASUS M2N-VM
CPU:    AMD AM2 3500+
RAM:    2 X 1G generic  
SOUND:  Onboard SPDIF out
HDD:    1 X MAXTOR 80G
VIDEO:  NVIDIA 7300GT (Onboard 6100 not good enough)
NETWORK: Wired ([over power cabling]("http://www.netcomm.com.au/products/ethernetoverpower/np285")) using onboard controller.    
REMOTE:  Microsoft MCE Remote
DISPLAY: 42" LG LCD 1080p at 50hz (PAL)

Others around the house have frontends installed on their PCs. They use wireless to access the backend. 

The only reason I have 2G in the frontend is because I can :P

I had the usual learning curve, although I mostly used a trial and error approach to fine tune.

SPDIF sound is still a problem, but I think it is MythTV or Linux, not the hardware. Every now and then when switching source the sound will corrupt. It sounds like loud white noise. Stopping and restarting the source once or twice usually fixes it. It's annoying, but I've learnt to live with it. 

Other than the intermittent sound PITA, the system is remarkably robust, although I have re-installed a backup image onto the backend once or twice when I screwed it up :) - 

Picture quality on the main front end is OK. De-interlacing also leaves a lot to be desired. I cannot find a setting combination that gives quality images when watching fast action sports like basketball, in which case I switch over to the LG LCD's internal digital tuner. It is much more capable than anything I have seen on a media center box, be it WinXP MCE, Vista MC or MythTV. 
  

BTW, the EPG is [shepherd]("http://svn.whuffy.com/"). Install, configure and forget. 

Cheers

---

### Post by beachdaze on 2009-01-18
Hardware
Motherboard: Asus A8N-SLI Deluxe (NForce 4)
CPU: AMD x2 64 3800+
RAM: 4GB DDR400
Video Card: NVida GeForce 6600GT 256MB
Sound Card: Creative X-Fi Platinum
HD: 2x300GB Sata, 1TB Sata
Remote: None
Tuners: PVR150
Country: USA (Florida)
TV provider: Brigthhouse (Time Warner) Digital cable
TV signal type: Digital Cable - no set top box

Performance
Setup was rather easy, although I missed a few steps due to my own impatience!

I still get some green artifacts when viewing the signal (the don't show when booted into the Windows partition using the included WinTV app). 
But otherwise very enjoyable.

---

### Post by DrJohn999 on 2009-01-18
_Hardware_
Motherboard: ASUS M3N78-EM, BIOS 418
CPU: AMD Phenom 9600 (Quad core) w/ stock CPU fan
RAM: OCZ Platinum 2GB (2 x 1GB) SDRAM DDR2 1066
Video Card: Onboard NVIDIA GeForce 8300 (driver 177)
Sound Card: Onboard Realtek ALC1200
HD: Western Digital Caviar Black WD1001FALS 1TB 7200 RPM SATA 3.0Gb/s
Remote: eDATA DEC-200B Vista Certified Infrared Remote Control W/ Receiver & Blaster
Tuners: HDHomeRun
DVD-RW: SAMSUNG Black SATA Model SH-S223Q 
Case: Antec Silver/ Black Veris Fusion 430
Wireless KB/Mouse Pad: ADESSO WKB-4000US USB RF Wireless Mini Keyboard 
Country: US
TV provider: OTA / SchedulesDirect
TV signal type: ATSC

[B]_Performance_
Hardware[/B]
Assembly went well. One problem w/ PSU jumper cable & connector to VFD supply: one pin had been overheated at Antec and was pushed out on first assembling. Removed pins and pushed directly into socket.

The VFD display can be made to work by fiddling with LCDd, but OOB it does not. LIRC doesn't see either the IR receiver or the volume control. Others have had limited success here; I gave up and am waiting for the right drivers to show up. Meantime I'm using the USB IR receiver included with the eDATA DEC-200B which "just works."

Case is very quiet w/ fans on low (2200 rpm) setting. CPU temperature (lm-sensors) hovers at 35C, %usage around 35-44% while recording one channel and viewing another simultaneously, both in hidef. Haven't loaded up additional clients yet. I plan to build a diskless PXE booted client next, perhaps using this same MOBO but with a less capable CPU and half the memory.

The Adesso works very well as long as your cell phone is nowhere nearby. They're both 2.4 GHz devices.

**Software**
ESSENTIAL to apt-get update / upgrade all Ubuntu packages and then get latest MythTV weekly 0.21 fixes builds. Some problems with NetMan and Nvidia control were fixed since the Mythbuntu 8.10 CD image was released.

Initially couldn't play LiveTV after bootup w/o restarting backend. MUST set LAN to a fixed IP address using updated NetManager. A DHCP reservation alone on your server or router won't solve this problem. Also MUST change priority of loading for MythTV backend in /etc/rc2.d from S20mythtv-backend to S40mythtv-backend. Then all is well.

You can find out how to do all this in this forum, just search.

No audio over HDMI yet (need newer ALSA driver). Haven't tried SPDIF.

Overall this is an excellent combination for a MythTV frontend/backend combo system!

---

### Post by captainskyhawk on 2009-01-19
Old Dell Dimension
Celeron 1.4 GHz
384 MB PC100
40GB HD
IXMICRO (IXTV) ( BT848 ) Tuner
USA
Mythbuntu 8.10

Works, but no sound from tuner card as of yet.  Had to manually configure card using [instructions on this page]("http://www.mythtv.org/wiki/Bttv") (card=9 and tuner=6).  Surprising performance considering old hardware, just need to get the sound output from the card working!

---

### Post by john roll on 2009-01-19
I upgraded from 7.10 to 8.10 and then when that didn't work I tried
9 alpha 3.

my pvr-150 would not work with 8.10 and the 9a3 install would not
boot into X11 graphics.

I ran 7.10 very happily for over a year.

I'm not sure what to include here.  I have a 1.2Ghz athlon is a shuttle sytle case with 1 Gig memory.

here is lspci:

root@tv:/var/log/mythtv# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

---

### Post by sforces on 2009-01-23
How'd you get it to work? I'm running Ibex with same tuner and can't get mine working. :(

> **ACGarib said:**
> Both the backend and frontend are installed on a laptop running Ubuntu Intrepid Ibex.

Hardware
Dell Vostro 1500
CPU: core2duo T7300 2GHz
RAM: 2 GB
Video Card: Nvidia 8400m GS
HD: Just using Laptop screen at 1440x900
Remote: came with the tuner
Tuners: Hauppauge HVR-1950
Country: US
TV provider: University of Delaware
TV signal type: NTSC cable, QAM256 digital cable

Performance
NTSC and QAM work. Audio is out of sync every now and then, but it's usually fine. Video is usually smooth, but sometimes it will momentarily stutter, both SD and HD. I don't get any ATSC signals so I can't try that. Have not tried the Svideo input yet either. The remote works, but it's laggy and sometimes I have to push the button twice for it to register. Since I'm only a foot away from the screen, I just use the keyboard anyway.

---

### Post by ttolstead on 2009-01-25
Hardware
Motherboard:Asus A8M2N-LA (Nodus)
CPU:Athlon 64 X2 5200+
RAM:4gb DDR2 PC5300 dual channel
Video Card: MSI GeForce 7100GS 256m ram PCI Express x16
Sound Card:Integrated
HD: 400gb
Remote:Vista Media Center Remote
Tuners: PVR-150
Country: United Stares of America
TV provider: Dish Network
TV signal type:satellite (NTSC)

Performance
All hardware except the PVR-150 properly detected and functional.  On previous installs of Gutsy and Hardy, the PVR-150 worked properly with VLC.  The card appears to be recognized but will not tune, only snow. 
 ubuntu 8.10 2.6.27-7-generic AMD 64

---

### Post by movieman on 2009-01-27
Hardware:

Motherboard: Intel D945GCLF2
CPU: Atom 330
RAM: 2GB
Video Card: Integrated Intel
Sound Card:Integrated
HD: Caviar Green 1TB
Tuners: PVR-150
Country: Canada
TV provider: OTA
TV signal type: OTA NTSC

Performance:

Pretty good for SD, though I get occasional stuttering in DVD playback or Mythweb streaming; I don't think that's CPU-related because the CPU load is low at the time. Can't reliably play HD with a single-threaded codec, but should be OK with multithreading as that's what the CPU is designed for. Can record one channel to disk while transcoding two more to MPEG-4 (~25fps), commercial flagging another (approx 100fps) and streaming a fourth to my laptop through Mythweb.

Uses 50W at idle and 57W maxed out (e.g. transcoding and commercial scanning while playing a video). A significant part of that is probably down to the cheap PSU that came with the case.

Issues:

TV-out doesn't work with current drivers, BIOS upgrade required to install Linux, haven't figured out how to enable 5.1 sound.

For HD playback it's probably worth waiting for the Nvidia Ion platform with integrated Nvidia GPU; I suspect I'll build a separate front-end when that's available.

Updates:

Managed to get 5.1 audio output working with suggestions from this thread: [http://ubuntuforums.org/showthread.php?t=760091&highlight=alc662](http://ubuntuforums.org/showthread.php?t=760091&highlight=alc662)

---

### Post by bigtreacle on 2009-01-28
**Hardware**
Motherboard: MSI Mega 865 (small form factor)
CPU: Intel P4 2.8Ghz
RAM: 510Mb
Video Card: On board intel
Sound Card: On board
HD: 250GB Maxtor SATA
Remote: mceusb2
Tuners: Hauppauge PVR-500
Country: UK
TV provider: Analog Terrestrial
TV signal type: Analog

**Performance**
Ok so far, but only tested at 2am this morning!

**Issues:**
Had to roll back the ivtv firmware for the PVR-500 back to a 2007 one to get the tuner to work.

---

### Post by jr_herman on 2009-01-28
**Working Hardware**
**Motherboard:**GIGABYTE GA-G31M-ES2L LGA 775 Micro ATX
**CPU:**3.0GHz Intel Core 2 Duo E8400 Wolfdale
**RAM:**Kingston 2GB
**Video Card:**EVGA GeForce 9500GT 512MB 128-bit
**Sound Card:**Turtle Beach RIVIERA 5.1
**HD:** SAMSUNG Spinpoint 500GB 7200 RPM
**Remote:** N/A
**Tuners:** Skystar 2 DVB-S
**Country:** USA (Texas)
**TV provider:** Still working
**TV signal type:** Still working

**Performance**
All hardware was recognized. Had to set soundcard as default. Also install gnome-alsamixer to get SPDIF, IEC958 working to Yamaha sound receiver.  Matter of making all the peices work as planned. (READING)

---

### Post by techno-dug on 2009-02-03
[B]Hardware
Motherboard: Gigabyte
CPU: P4 2.8ghz
RAM: 1gb
Video Card: Nvidia 6600LE
Sound Card: OnBoard
HD: 80gb & 250gb
Remote: Remote From Twinham TV Card
Tuners: Leadtek DTV1000 & VStream PCI
Country: Australia
TV signal type: DVB-T

Performance[/B]
All worked out of the box. Had to fiddle with the tuner cards to get them both working together.
Struggles a little with High Definition channels. Faster CPU & more RAM would help..........but hey for stuff that was laying around, who's complaining!

---

### Post by dontpntpool on 2009-02-05
[B]_Hardware_
Motherboard: [/B]Intel OEM E210882 [D845GLLY]("http://support.intel.com/support/motherboards/desktop/d845glly/")[B]
CPU: [/B]P4 2.2ghz[B]
RAM: [/B]512meg[B]
Video Card: [/B]onboard[B]
Sound Card: [/B]onboard[B]
HD: [/B]40GIG Western Digital[B]
Remote: 
Tuners: [/B]Dual haupauge PVR 350[B]
Country: [/B]USA[B]
TV provider: [/B]Huxcom[B]
TV signal type: [/B]Cable[B]

_Tuner card Info:_
[/B]**Card 1:**
480000-07A
61381 Rev D 423
**Card 2:**
610000-08
48132 Rev D 323
[B]
My LSPCI output:
[/B]```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
01:01.0 Ethernet controller: Intel Corporation 82544EI Gigabit Ethernet Controller (Copper) (rev 02)
01:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:03.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
```

_**PROBLEMS: **_
**VIDEO: **My video would not work at all without putting in a PCI video card then I could get to x windows.  I tested by trying to booth the live cd in live mode and in install mode, there was no text mode afaict. When gettting to the graphics mode the live cd would have numerous graphic glitches and then would just lock up. Caps lock would work, ctrl-alt-bs or ctrl-alt-f1 would not work. After installing the nvidia card I was able to install the os. After install I tried booting from the HD without the PCI video card using the onboard video outbout but the x server still locked up.
[B]
INSTALL: [/B]I told it to only install backend without frontend and it still installed everything. I specified the mysql root password to be "none" and after the install it was a random password.

**UPDATE: **First run only a partial update could be ran. After update no plugins were checked and they could not be installed.

**USE: **Tried booting a 2nd computer with the live cd to configure the backend server but none of the passwords I set are working. Could not SSH in I was able to use a web browser after I guessed that I was supposed to add /mythweb.  My tuners were not setup on the webpage, still trying to figure that out. Was able to use VNC to manage the server but its EXTREMELY SLOW.


[U][B]IDEAL OPERATIONAL STATUS:
[/B][/U]PC1 - MythTV backend Tuner box
PC2 - iSCSI backend storage server for MythTV recorded content
PC3 - HD XBMC frontend playing content from PC2 and streaming live from PC1
xbox - XBMC frontend for 720p and below content and live content from PC1
Laptop - control and playing via web

_**STATUS:**_
LONG LONG WAY AWAY

---

### Post by ederopaa on 2009-02-06
**_Hardware_**

**Motherboard:** Asus M2N-SLI Deluxe AM2 motherboard
**CPU:** AMD Athlon 64 X2 5200+
**RAM:** 4 x Kingston 1024MB 667MHZ DDR2 NON-ECC DIMM-memory
**Video Card:** Asus  GeForce 7600 GS, 512MB
**Sound Card:** Onboard
**HD:** 2 x Western Digital Caviar GP 1TB
**Remote:**Microsoft Media Center Remote with usb receiver
**Tuners**: 3 x Terratec 1200 dvb-t
**Country:** Finland
**TV provider:** YLE
**TV signal type:** DVB-T
**Other stuff:** SilverStone LaScala SST-LC20B HTPC ATX case
2 x Nexus Silent 80x80mm fans (back)
Enermax Modu82+ 625W ATX power supply
Samsung SH-S182M/RSMN Super-WriteMaster dvd
Scythe SCMNJ-1000 Ninja Mini 6
Nexus PWM Series Silent Fan 80mm on the side of the Ninja
Sony Bravia 32" S-series 

**_Performance_**

This setup is really silent and it runs cool! I've had no big problems with this. 

I've recently put together 2 almost identical setups for my brother and mother. The only difference being the motherboard (Asus M2N32-SLI DELUXE/WIFI), the tuners (Satelco EasyWatch PCI DVB-T) and a slightly updated CPU (AMD Athlon 64 X2 5600+). With the M2N32-SLI DELUXE/WIFI mobo I could not get the serial port ir-receiver to work after updating the Kernel from the initial install kernel??

---

### Post by chiark on 2009-02-09
**_Back end server_** 

_**Hardware**_
**Motherboard:**Dell optiplex GX150
**CPU:** Pentium III 1.0GHz
**RAM:** 512MB
**Video Card: ** Internal
**Sound Card:** Internal
**HD:** 120GB WD RAID edition IDE
**Remote:** n/a
**Tuners:** Leadtek Winfast USB DVB-T (on USB2.0 PCI card), Hauppauge Nova-T PCI
**Country: ** UK
**TV provider: ** DVB-T in UK
**TV signal type:** DVB-T

_**Performance**_[/QUOTE]
Very good for the back end.


**_Back end server_** 

_**Hardware**_
**Motherboard:**Via EPIA SP-13000
**CPU:** 1.3GHz C7
**RAM:** 512MB
**Video Card: ** Internal
**Sound Card:** Internal (SP/DIF)
**HD:** 80GB Seagate Momentus
**Remote:** ATI Remote Wonder (v1)
**Tuners:** n/a (yet!)
**Country: ** UK
**TV provider: ** Backend
**TV signal type:** DVB-T

_**Performance**_[/QUOTE]
Needs to have acpi=noirq as a kernel option otherwise wired network does not work!  Video profile needs to be CPU--

---

### Post by dadie11 on 2009-02-11
..... hope this is not too late. I've been building this little swine for a year or so. Nearly there. Small graphics problem nearly sorted (slow and blocky) ~ remote is more problematical; especially as the config. is supposed to be the correct one. No apparent cooling problems, I have fitted a second fan on the northbridge, though. David Crawford.

---

### Post by elroldan on 2009-02-11
Hello, im new in this forum, but i dont know too much english so 
i hope all the people in this forum understand me.
i dont know if are another forum in spanish. If are another please give me the link
Hardware
CPU: Intel Core 2 Duo 2.3 Ghz
RAM: 4.0 gb ram
Video Card: NVIDIA 8400GS, 512 mb with turbocaché
Remote: i dont know what is this 
HD: 230 gb hard drive
Tuners:
i dont know what is this

Performance
i dont know where i can found the driver of my motherboard
GA-G31M-S2L and the driver of my video card i need the driver of lan of my motherboard. in this momment i have windows vista ultimate but i want to change my OS to ubuntu 8.10 i have the CD but without thats driver i cant use my computer to play and work. thanks for you help

---

### Post by Dartr on 2009-02-13
**_Hardware_**

**Motherboard:** ASUS M3N78-EM
**CPU:** AMD Athlon X2 5050e 2.6GHz 45w
**RAM:** Corsair 4GB (2x2GB) 800MHZ DDR2
**Video Card:** Onboard Nvidia 8300 512MB shared from system RAM
**Sound Card:** Onboard Realtek
**HDD:** Western Digital Raptor 150GB system/data
**HDD:** Western Digital Caviar 250GB recordings
**DVD:** NEC 3500 w/ bitsetting firmware
**Remote:** Streamzap
**Tuners:** Silicondust HD Homerun
**Country:** US
**TV provider:** Antenna
**TV signal type:** 8-VSB ATSC
**Playback quality:** High
**Case:** Nexus Clodius
**PSU:** Nexus 430w Compact PSU (16db!)
**Case Fans:** 2 x Nexus Silent 120mm fans
**CPU Cooler:** Nexus AXM-8200 CPU cooler
**Monitor:** HP LP2275w
**OS:** Intrepid 64 w/ Gnome desktop + MythTV


**_Performance_**

This is a very quiet and cool-running build.  The internal case temperature never requires additional fan speed.  I'm planning to disconnect the CPU fan as the heatsink never even feels warm.

Load averages range between .2 and .4, with 2 users logged into Gnome desktop and one user logged in remotely with NX client.  Never skips a beat with 1080i recordings.  Can easily record two 1080i MPEG-TS streams while watching one with pause/rewind, etc. On-the-fly automatic comm flagging works well too.

MythWeb streams nicely from original 1080i recordings.  Currently using 480x360 @ 256kbps.  Haven't tested higher bitrates yet.  Music streaming does not work, however.  Just can't seem to get the right combination of permissions/symlinks right.

Everything pretty much works out of the box, except having to relocate the recordings directory, and MythArchive fails while using ffmpeg to transcode for DVD [now patched/fixed].  Haven't taken time to solve yet.  Would like to configure Streamzap buttons better as some buttons aren't functional yet...haven't figured this out yet [now configured in lircrc].

Very, very pleased overall. :)

---

### Post by dch3200_hell on 2009-02-15
Vista 64 bit (This seems to be the biggest problem)
NO 64 BIT Driver for Firewire copnnection to the DCH3200...

all this for HD... I dont want to lose the WMC ... so no HD for ME...

DCH3200 is the worst.

Motorola sucks for not creating drivers for it.

and a 46" LCD Flat with an HP m9150f 8500 GTX card.

HD movies work fine -

---

### Post by kappe on 2009-03-04
**_Hardware_**
**Motherboard:** Intel Atom D945GCLF2
**CPU:** Atom 1.6 Ghz 2 core
**RAM:** 1024 ddr2 800
**Video Card:** Intel GMA 950 integrated
**Sound Card:** ac97 integrated
**HD:** 500 Gb sata
**Remote:** Windows media center remote
**Tuners:** n.a
**Country:** Italy
**TV provider:** n.a
**TV signal type:** n.a (next step DVB-T)
[B]
Performance:[/B]
S-video output don't work, (bug fixed, wait mythbunt update: [http://bugs.freedesktop.org/show_bug.cgi?id=17776](http://bugs.freedesktop.org/show_bug.cgi?id=17776) )
good performance for media center use.

---

### Post by orlande on 2009-03-15
DVB-S2 card Technotrend budget-pci-320 with chip SAA7146
does NOT work (mythbuntu 8.10).
snd_aw2 is loaded, although it is blacklisted.

# lspci -vnn
03:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7146 [1131:7146] (rev 01)
Subsystem: Technotrend Systemtechnik GmbH Device [13c2:1019]
Flags: bus master, medium devsel, latency 32, IRQ 3
Memory at fdcfe000 (32-bit, non-prefetchable) [size=512]
Kernel modules: snd-aw2

/etc/modprobe.d/blacklist
and
blacklist-oss -> /lib/linux-sound-base/noOSS.modprobe.conf
contain a line: blacklist snd_aw2

What else can I do to permanently remove the module snd_aw2?

---

### Post by mric5180 on 2009-03-16
**_Hardware_**
**Motherboard:** Gigabyte GA-MA78GM-US2H 
**CPU:** AMD AM2 Athlon Dual Core 5200+
**RAM:** 2Gb RAM DDR2 800MHz Kingston 
**Video Card:** On board motherboard
**Sound Card:** On board motherboard
**HD:** 1x 40Gb IDE Seagate for OS (master) AND 1x 400Gb IDE Seagate for recordings (slave)
**Remote:** Came with tuner
**Tuners:** Leadtek Winfast DTV 1000T 
**Country:** Australia
**TV provider:** Free to air (channel 7, 9, 10 etc...)
**TV signal type:** DVB-T

**Operating System:** Ubuntu 8.10 (Intrepid Ibex)

**Performance:**
Works great. No dramas at all. Had a few setup issues but once solved the system is fantastic. CPU load is small, remote works well. Turns off when not in use and back on when about to record. Why buy a tivo when you can use MythTV? More details can be found at [http://sites.google.com/site/mricci43/](http://sites.google.com/site/mricci43/)

---

### Post by xfred on 2009-03-21
dual DTV2000H Rev J with Y04G0044 remote:

Working:

- digital working including high-def after adding card=51 option
- remote working after some serious messing around

Not working:

- can't get any analogue reception (V4L).
- having some trouble setting up video capture (admittedly I'm not really sure where to start with this one, so may just be my incompetence showing).

---

### Post by phroman on 2009-05-10
Hardware
Motherboard: ASUS P5Q
CPU: Intel Core 2 Duo E8400 3GHz
RAM: 2gig Corsair model TWIN2x4096-8500C5
Video Card: GeForce 7300 SE/7200 GS PCI Express  (forgot manufacturer)
Sound Card: On board audio * (see note below)
HD: WD 320 gig SATA
Remote: Snapstrem Firefly * (see note below)
Tuners: Hauppauge WinTV PVR 250
Country: USA
TV provider: Direct TV
TV signal type: DVB-S (satellite)
Mythbuntu Version: 9.04


Onboard Audio:  Had to add the following line to the end of /etc/modprobe.d/asla-base.conf   
```
snd-hda-intel model=6stack-dig
```Had to run from the terminal:  ```
alsamixer
```
Had to un-mute iec958 as this is the SPDIF out on my mobo.  Audio fine after this.


Snapstream Firefly Remote:   If you enable the Snapstream X10 Remote in MCC, the file generated in /usr/share/lirc/remotes/atiusb/lircd.conf.atiusb, will have the incorrect name entry for "remote name", as compared the /etc/lirc/hardware.conf.   It will say "Snapstream Firefly", this is wrong, it must be changed to match the name of the remote that is named in /etc/lirc/hardware.conf, which will be "Snapstream X10 RF.

Have had *no luck at all* with controlling my Direct TV HR21-100 STB.  Have tried multiple setups of serial-usb and ir, but I just can't get it worked out.

---

### Post by pcooley on 2009-05-13
Hardware

**Motherboard:** Asus M3N78-EM 
**CPU**: AMD Athlon 64 X2 Dual Core Processor 5200+ Brisbane 2.7GHz
**Heatsink/Fan:** Thermaltake TR2-R1
**RAM:** 4GB RAM DDR2 800MHz Patriot
**Video Card:** On board video Geforce 8300
**Sound Card:** On board motherboard Realtek ALC1200 8 -Channel HD audio
**HD:** 2 x SATA 1TB WD Caviar Green WD10EADS-00L
**Optical:** Lite-On iHAS120 DVD-RAM
**Remote:** Harmony One Advanced Universal Remote 
**Tuner:** HDHomeRun Home Networked Digital TV Tuner
**Receiver:** ONKYO TX-DS696
**Case:** Antec Fusion Remote Black
**TV:** Panasonic 42" plasma TH-42PX60U
**Country:** USA
**TV provider:** Comcast

**Operating System:** Mythbuntu 9.04

Performance

Installs and detects all hardware.  Plenty of power to record 2 HD streams, flag commercials, and watch a recording.  CPU stays < 40 C.

Very impressed with both Ubuntu and the MythTV projects.  Kudos to all involved.

Note: Majority of the configuration was spent on mapping/documenting the Comcast channels to scheduledirect.org and secondly mapping the remote control buttons to the appropriate keybindings.

Additional Configuration needed
* Using SPDIF sound needs "options snd-hda-intel model=6stack-dig" added to  /etc/modprobe.d/alsa-base.conf and then alsamixer needs to be run to unmute the digital out (IEC958).  Discussed on many threads. 
* Configuring the Soundgraph LCD/IR in the Antec Fusion case requires the latest csv code and some additional configuration documented here: [http://ubuntuforums.org/showthread.php?t=1103474](http://ubuntuforums.org/showthread.php?t=1103474).
* HDHomerun connection is attempted before the network is up.  Requires having the mythbackend in rc2.d to be started last a mv to S99zmythtv-backend.

Paul Cooley - [http://linuxlore.blogspot.com/](http://linuxlore.blogspot.com/)

---

### Post by iQuizzle on 2009-05-25
CPU - AMD 5050e
Motherboard - Biostar 790GX 128M
Ram - 2gb Kingston HyperX 1066
Hard Drive - Western Digital Green Power 750gb
Case - Auzentech R-2 Toast
Tuner - Hauppauge PVR-150
PSU - PC P&C Silencer 370W
Optical - Lite-On DVD
Remote - Anyware GP-IR02BK Vista 2 channel IR Remote Control

Comments:

 The 790GX chipset has full 1080p HD playback capability (I've read) and it has an HDMI output. Not too shabby for onboard graphics. This is the reason I chose the AMD route (that and a low power 45W TDP rated CPU), in spite of the fact that they still need to play catch-up on their linux drivers. Couldn't get the catalyst drivers working for the 790GX chipset in mythbuntu 9.04. Also, the Realtek 8111 ethernet was not working, and the Realtek rtl8185L wireless chip worked poorly. I reverted to mythbuntu 8.04 and the catalyst drivers and ethernet drivers worked effortlessly. The only thing required for the catalyst drivers was a few lines added to the xorg.conf file to better its performance in myth. These can be found on the mythtv wiki. Still no wireless, but I'll attempt to fix it later. The remote was plug and play for both versions of mythbuntu! I was very happy with the ease of use and would recommend it to anyone. Plenty of buttons, inexpensive ($25) and available on newegg. I'd recommend it to anyone. It uses the standard MCE/phillips key mappings provided with mythbuntu, so no complaints there. The picture isn't perfect with the hauppauge card, but it's not to bad either. What can you expect for a regular NTSC tuner. It seems to work reliably though, so I'm happy. I also recommend the WD green power hard drives for HTPC. It uses less power (about 5W) than regular hard drives, but they are extremely quiet..which is nice for home theater builds.

In case anyone is interested, the auzentech case looks nice, but mountings are a little weird. The optical drive has to be mounted vertical and my old dvd drive (which has trouble opening in a horizontal mounting as it is) refuses to push the tray up vertically.

---

### Post by mookie60 on 2009-05-31
Hardware
Motherboard: not sure, Dell Optiplex 260 (a $70 salvage yard pc)
CPU:  2.26gHz
RAM:  512mb
Video Card:  nvidia geforce 6200
Sound Card:  integrated with MB
HD:  Segate 80gb IDE
Remote:  mce remote (phillips) supplied with Hauppauge tuner
Tuners:  Hauppauge 1600 (analog & digital tuners)
Country: US
TV provider: Bright House networks
TV signal type: basic cable, no set top box
Mythbuntu Version: 9.04

Performance

Analog performance mostly very good.  It does need the startup script  to avoid the first record glitch (see wiki page for this card).  

Under 8.10 it did have a problem where the analog (mpeg) tuner would sometimes lose it's settings during a reboot; requiring an annoying process to reset it.  This has not yet happened with 9.04

Initially the digital (qam) tuner would work only intermittently.  After identifying and partially correcting a ground loop problem (caused by the addition of the pc to the home theater), it's now working pretty well, though channel signal strength always shows 0%.  

The box will not do HD without some stutter; probably due to the older CPU.

Overall, I'm very happy as this is my first Mythbox.

---

### Post by exredhat on 2009-06-08
Distro: Xubuntu 9.04 (with mythubuntu-control-center added)
Mobo: Gigabye GA-73PVM-S2H
CPU: Core 2 duo 2.5GHz (E7200)
Graphics: Onboard Nvidia 7100
Audio: Onboard
Tuner: WinTV-NOVA-TD-500 PCI
Network: USB Wireless N Edimax EW-7711UAN
Periperals: Keysonic Wireless Keyboard 2.4GHz USB with Touchpad
Disk: Seagate 400GB SATA2
RAM: 2GB DDR2 800MHz

Everything works, bar the remote, with minimal playing arround. Install the NVidia driver for OpenGL and Xbox Media Centre. MythTV works fine and is good. SMPlayer is good too. Tuners work fine.

I don't know why the remote doesn't work. It does work in Windows XP though. The PCI WinTV is recognised, but not the remote (not found at all - in dmesg or lsof). I think I'm going to have to buy another USB remote, but have not found one which I know will work with Linux :(

If any company sells remote controls which work for Linux then they could make some money :)

---

### Post by Caps18 on 2009-06-11
> **exredhat said:**
> 
I don't know why the remote doesn't work. It does work in Windows XP though. The PCI WinTV is recognised, but not the remote (not found at all - in dmesg or lsof). I think I'm going to have to buy another USB remote, but have not found one which I know will work with Linux :(

If any company sells remote controls which work for Linux then they could make some money :)

The Microsoft MCE ones do.  I use two of these around the house.  I'm not saying it's perfect and all the buttons work, just the main buttons that do what I want it to in order to control MythTV.

[http://www.amazon.com/Windows-Certified-Infrared-Receiver-Ultimate/dp/B000ST7QPA/ref=sr_1_1?ie=UTF8&s=electronics&qid=1244735070&sr=8-1](http://www.amazon.com/Windows-Certified-Infrared-Receiver-Ultimate/dp/B000ST7QPA/ref=sr_1_1?ie=UTF8&s=electronics&qid=1244735070&sr=8-1)

It would be nice if there was a list that showed what the best hardware was to buy that would work.  Like an awards show type thing, a few choices get nominated that we know work, and then we all vote on which one is best.

---

### Post by richard.e.morton on 2009-06-11
> **exredhat said:**
> Distro: Xubuntu 9.04 (with mythubuntu-control-center added)
Mobo: Gigabye GA-73PVM-S2H
CPU: Core 2 duo 2.5GHz (E7200)
Graphics: Onboard Nvidia 7100
Audio: Onboard
Tuner: WinTV-NOVA-TD-500 PCI
Network: USB Wireless N Edimax EW-7711UAN
Periperals: Keysonic Wireless Keyboard 2.4GHz USB with Touchpad
Disk: Seagate 400GB SATA2
RAM: 2GB DDR2 800MHz

Everything works, bar the remote, with minimal playing arround. Install the NVidia driver for OpenGL and Xbox Media Centre. MythTV works fine and is good. SMPlayer is good too. Tuners work fine.

I don't know why the remote doesn't work. It does work in Windows XP though. The PCI WinTV is recognised, but not the remote (not found at all - in dmesg or lsof). I think I'm going to have to buy another USB remote, but have not found one which I know will work with Linux :(

If any company sells remote controls which work for Linux then they could make some money :)

Look on the Mythbuntu and MythTV sites there are lots of posts about how to get various remotes to work. You should be able to use the information to get your remote to work with the app of your choice

Richard

---

### Post by newbdriver8 on 2009-06-16
sorry if this doent belong, please help, cant find in forums.

hitachi deskstar 160gb ata133 hd new\broken in.
replacement for maxtor drives of 80+60gb old drives out of a bin that worked.
fresh install gets (error 5) disk geometry error?

 k7, an19mb, 3gb pc2700, LG multidrive.sbaudigy2, nvidia 5200 agp,

---

### Post by sdutta1980 on 2009-07-02
Hardware
Motherboard: Intel DG31PR
CPU: Intel® Celeron® Core 2 Duo Processor
RAM: 2 GB 667mhz DDR2
Video Card: Inbuild
Sound Card: Inbuild
HD: Seagate 250 GB SATA 2
DVD: ASUS DVD/CD Rewritable Drive
Country: INDIA

Performance:
Works Great without sound. Ripping DVD's no problems. The onboard LAN card detected and work great but the audio card had not been detected. No sound at all. Donno how to configure my 5:1 channel creative speaker system in this. Please advise.

---

### Post by philcamlin on 2009-07-02
**_Hardware_**
**CPU:** intel celeron D 2.53 ghz
**RAM:** 1.5GB DDR2
**Video Card:** RADEON X300SE
**HD:** 40 GB SATA HDD
**Sound Card:** no idea :P it works nie though 

**_Performance_**
everything works lovely :)

---

### Post by larsolav on 2009-07-06
**Hardware**
**Motherboard:** ZOTAC GF9300-D-E LGA 775 NVIDIA GeForce 9300 HDMI WiFi Mini ITX Intel Motherboard
**CPU:** Intel Pentium E5200 Wolfdale 2.5GHz LGA 775 65W Dual-Core Processor Model BX80571E5200
**RAM: **A-DATA 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model ADQVE1A16K 
**Video Card:** NVIDIA GeForce 9300 (Onboard)
**Sound Card:** Onboard 8 channel, SPDIF, HDMI
**HD:** Seagate Barracuda 7200.10 ST380815AS 80GB 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive
**Remote:** Anyware HA-IR01SV Infrared Certified MCE VISTA Remote Control
**Tuners:** No tuners Frontend only
**Country: **USA
**TV provider:** OTA
**TV signal type:** ATSC
**Mythbuntu Version:** 9.04
**Extras:** SILVERSTONE NT07-775 90mm CPU Cooler, Scythe S-FLEX SFF21D 120mm Case Fan, SAMSUNG DVD Burner Black SATA Model SH-S223L, APEX MI-008 Black Steel Mini-ITX Tower Computer Case 250W Power Supply. This is based on an AVS Forum recommended build. 

**Performance**

Dual boot Windows 7 RC and Mythbuntu 9.04 frontend only.

In Windows 7, HDMI sound worked until I installed NVIDIA drivers. Then it stopped working. For hdmi audio to work in Windows 7 I had to install the HD audio driver found under beta drivers for nforce730/geforce 9300 for Windows 7 64 bit.  [http://www.nvidia.com/object/nforce_win7_64bit_15.37.html](http://www.nvidia.com/object/nforce_win7_64bit_15.37.html) 

In Mythbuntu HDMI audio works great. Just had to unmute in Alsamixer. However, the attached WIFI for the board does not work in Mythbuntu. I do not know if there are drivers for this WIFI card for Ubuntu. I will try using ndiswrapper.

With my 32” Vizio I have lots of overscan in Mythbuntu. In Windows 7 there were sliders in the NVIDIA settings for removing overscan. Can not find such sliders in the NVIDIA settings for Mythbuntu.

Works great as a frontend for the bedroom. Quiet and keeps relatively cool.

---

### Post by molder on 2009-07-06
[COLOR=Red]_**Hardware**_[/COLOR]
**Motherboard: **Biostar P4-M900-M4[B]
CPU:[/B] Pentium 4 2.80 Ghz
**RAM:** 2.0 GB
**Video Card:  **MSI nVidia 9500 GT 512 MB with HDMI output
**Sound Card:** onboard Realtek ALC861VD
**HD:** Maxtor 40 GB and Seagate 120 GB
**Remote:** iPhone MyMote Had to install IRC option to get remote to function
**Tuners:** ATI HDTV Wonder
**Country: **Austin, Texas USA
**TV provider: **none OTA
**TV signal type:  **DVB-T
**Mythbuntu Version: **9.04
**NIC:** Had Linksys [SIZE=1]WMP11 functional with fwcutter, upgraded to D-Link WDA-1320 and system crashes.  Have not solved issue yet.  Wireless works marvelously with the tuner card installed.

[B]Preformance:

[/B]Have not got the HDMI sound functinoal yet either.  I also use the Averard VDPAU fixes.  Occasionally jitter but not exactly a problem.  I use a 50 inch 720p Panasonic plasma TV.  Some overscan is present and last time I tried to fix it I ended up with a new installation to correct my tinkering ;) [/SIZE]

---

### Post by muranternet on 2009-07-07
**_Hardware_**
**Motherboard:** Intel D915GAV
**CPU:** Intel Pentium 4 3.4GHz (Prescott model 550, SL7KM), Rocketfish cooler (clone of Coolermaster Vortex 752), Arctic Silver Ceramique compound
**RAM:** 3GB DDR (some random stuff I had lying about, 2x1GB 2x512MB, probably a mix of mushkin/corsair value)
**Video Card: **ATI Radeon HD 4550 512MB
**Sound Card:** Onboard
**HD:** 3x 120GB WD SATA I, 1x 120GB Seagate SATA I, 1x 750GB USB WD MyBook (external)
**Remote:** Insignia something something, built the lircrc by hand using Tivo codeset
**Tuners:** Silicon Dust HDHomerun, Hauppauge WinTV PVRUSB2
**Country: **US
**TV provider: **Comcast
**TV signal type: E.g. DVB-S (satellite):** NTSC, QAM256
**Mythbuntu Version: E.g. 8.10** 9.04
**PSU:** Soly Tech 600W (had it lying around)
**Case:** Some generic midtower
 
_**Performance**_
 
This was a new build using hardware I could scrounge for free or lying around to replace my proof of concept box built in a totally inadequate HP Pavilion P4 1.8GHz.
 
Good performance on playback, output VGA to a 720P HDTV.
 
Still having some problems getting the external drive to auto-enumerate on a rare reboot from fstab. Box will lock during POST if user,noauto is omitted from the options line in fstab.  Fortunately I don't reboot the box at all generally so when I do I just mount it.  Still annoying; I had it working in the last box.
 
Used an inelegant method of getting the ATI to work. First installed using the DMA900 onboard graphics driver (which tears at 720P), then plugged in the HD 4550. Worked without changing drivers. Because I have heard about nightmares with ATI cards under 9.04, and because an earlier try using this same card on a motherboard with no integrated video resulted in auto-HDMI out for everything (including sound) with no recourse to return to onboard analog ALSA sound, I just left it alone. As far as I know the system thinks it's using a generic video card.
 
Had to set volume controls in 3 spots to get sufficient analog output: in ALSA mixer, in Mythtv, and via the ALSA mixer in the console.
 
Using remote control via HDHomerun. No issues as long as hardware.conf is configured properly to allow udp and the correct port.  I built the relevant lirc files using irrecord and some hand editing.
 
For some reason mplayer will not accept any remote inputs. Very strange. I worked around this by just switching to internal for all playback, and haven't had a problem. 
 
There is some choppiness when playing back 720P MKV files from an external ext3 mount, but I can live with that since most of my mythvideo stuff is SD.
 
Transcodes are pretty slow as expected. For standard definition and analog I transcode to MPEG4, 2200kbps, 720x400 resizing, and it usually clicks at about 41fps. For HDTV I transcode to MPEG4, 2200kbps, 1360x768 and it plods at 11fps. With these transcoding levels I generally save about 50% space on recordings with no degradation.
 
No crashes yet, with constant uptime at about one week. My old box would crash, and I suspect either heat (stupid small tight HP case) or lousy power supply.
 
Originally tried using the stock HSF, but anytime max clocks were being used (transcode or HD playback) the stupid stock fan would whine through the whole house.
 
Partitions as follows: 20GB / ext3, 20GB /home ext3, 3GB swap, 20GB /var/lib/mythtv XFS, 60GB /var/lib/mythtv/recordings XFS, then 3 drives all XFS for /var/lib/mythtv/recordings1 (...2 ...3), then external 750GB ext3 for a video share. Videos moved in and out over the network generally from a WindowsXP desktop via samba.
 
Occasional packet loss on HD feeds from the HDHR if there is a file transfer happening at the same time. I can fix this by either upgrading my LAN to gigabit or else trying to subnet the HDHR off a second NIC.

---

### Post by pumkinut on 2009-07-13
> **larsolav said:**
> **Hardware**
**Motherboard:** ZOTAC GF9300-D-E LGA 775 NVIDIA GeForce 9300 HDMI WiFi Mini ITX Intel Motherboard
**CPU:** Intel Pentium E5200 Wolfdale 2.5GHz LGA 775 65W Dual-Core Processor Model BX80571E5200
**RAM: **A-DATA 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model ADQVE1A16K 
**Video Card:** NVIDIA GeForce 9300 (Onboard)
**Sound Card:** Onboard 8 channel, SPDIF, HDMI
**HD:** Seagate Barracuda 7200.10 ST380815AS 80GB 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive
**Remote:** Anyware HA-IR01SV Infrared Certified MCE VISTA Remote Control
**Tuners:** No tuners Frontend only
**Country: **USA
**TV provider:** OTA
**TV signal type:** ATSC
**Mythbuntu Version:** 9.04
**Extras:** SILVERSTONE NT07-775 90mm CPU Cooler, Scythe S-FLEX SFF21D 120mm Case Fan, SAMSUNG DVD Burner Black SATA Model SH-S223L, APEX MI-008 Black Steel Mini-ITX Tower Computer Case 250W Power Supply. This is based on an AVS Forum recommended build. 

**Performance**

Dual boot Windows 7 RC and Mythbuntu 9.04 frontend only.

In Windows 7, HDMI sound worked until I installed NVIDIA drivers. Then it stopped working. For hdmi audio to work in Windows 7 I had to install the HD audio driver found under beta drivers for nforce730/geforce 9300 for Windows 7 64 bit.  [http://www.nvidia.com/object/nforce_win7_64bit_15.37.html](http://www.nvidia.com/object/nforce_win7_64bit_15.37.html) 

In Mythbuntu HDMI audio works great. Just had to unmute in Alsamixer. However, the attached WIFI for the board does not work in Mythbuntu. I do not know if there are drivers for this WIFI card for Ubuntu. I will try using ndiswrapper.

With my 32” Vizio I have lots of overscan in Mythbuntu. In Windows 7 there were sliders in the NVIDIA settings for removing overscan. Can not find such sliders in the NVIDIA settings for Mythbuntu.

Works great as a frontend for the bedroom. Quiet and keeps relatively cool.
Could you please post your sound configs if possible.  I have the same setup Zotac GF9300 + e5200.  I got sound through HDMI working in Windows7, but I'm having a bit of trouble with sound in Ubuntu.  I kind of have it working through HDMI, but not all the way.

Any help would be appreciated, thanks.

---

### Post by ds_pablo on 2009-07-14
Hardware:

Backend (Appliance)
CPU: 550 MHz PIII
RAM: 768 MB
HD: 20 GB for system, 500GB for recordings
Video: nVidia GeForce 4 MX 64 MB hooked up to nothing
Audio: Onboard hooked up to nothing
Tuners: PVR-150 and HVR-1600
TV Provider: Local Cable provider/OTA
TV Signal: Analog Cable/8-VSB
Mythbuntu Version: 9.04

Frontend
MoB0: Zotac nf630i-d-e
CPU: Pentium Dual Core E5200 2.5 GHz overclocked to 3.0 I think
RAM: 256 shared with onboard vid, 1.24ish dedicated system RAM
HD: 4GB compact flash card (3.7 gigs filled with boxee installed)
Video: Onboard nForce630i/geForce7100
Audio: Onboard nForce630i/geForce7100 (ALC 662 I think)


Performance:

Well, the backend sure can be sluggish (the old PIII is not too quick) and I actually have another frontend as well as run a frontend on my mac.  Once videos and recordings are cached up and streaming over the network, performance is phenomenal: I can easily watch HD and record two analog streams or any combo thereof.  I have the zotac box hooked up over HDMI and in windows it can do audio over the HDMI but I haven't managed to make this work in linux yet (any help there would be appreciated!).  Anyway, I am in the process of migrating the backend to an old but newer box with a 1.6 GHz P4 and when that is complete, the whole setup should be a little (okay maybe a lot) snappier.  Wish me luck!

---

### Post by bumperaxe on 2009-07-16
**_Hardware_**
Motherboard:Asus P5QL-SE
CPU: Core 2 Duo E7400
RAM:Kingmax DDR800 2GB
Video Card: Palit 9500GT 1GB
Sound Card: On board
HD: Samsung SATA2 1TB
Remote: Sony PS3
Tuners: Leadtek 1000S
Country: Australia
Network: Tenda 11N wireless PCI card
Mythbuntu Version: 9.04

**_Performance_**
Most hardware detected and functional with exception of -
Sony PS3 remote, not yet working
Tenda wireless card, detects network but won't connect (now using wired LAN via wireless access point)
New driver requred fo TV tuner, worked after following info on this forum 
HD record and playback works great
Shepherd guide grabber also great

---

### Post by chipppy on 2009-07-19
**Hardware**
**MainBoad:** ASUS P5Q SE/R
**CPU:** Intel E8500 3.15GHz Dual core
**RAM:** 4 GB 1066
**Video Card:** Gigabyte 8400GS 512MB (for composite out) + 9400GT 1024MB (for HDMI)
**HDD:** 1 X 500 GB + 1 X 1000GBSATA3
**Tuners: **Divco Fusion HDTV DVB-T Digital 4 (remote no used, Wii remote used)
**Sound Card:** onboard


**Performance**
Running Mythbuntu 9.04
All hardware automagic which was great
Had to boot into Safe Graphics Mode after install, due to needing to update graphic driver to Navida.  Activated new driver and rebooted and all perfect from a hardware point of view.

---

### Post by brianko on 2009-07-20
**Hardware**
**MainBoad:**  Asus M2N-E
**CPU:** AMD Athlon 64 X2 4200+ dual core
**RAM:** 2 GB
**Video Card:** nVidia nForce 570 Ultra
**HDD:** WD 500MB PATA
**Tuners: **Hauppauge PVR-350
**Sound Card:** onboard


**Performance**
Running Mythbuntu 9.04

*[FF during playback will lock up the front end on this setup!]("http://ubuntuforums.org/showthread.php?p=7605134#post7605134") *Otherwise, all other functionality appears normal.

---

### Post by sawbuck on 2009-08-01
[SIZE=2][FONT=Arial]I have had to rebuild a MythTV system[/FONT] after functional issues with a Fedora 8 based system cropped up in late Spring '09. I thought this time around I would try to simplify effort and do a package combo of linux/MythTV. I selected Mythbuntu since I had seen a lot of references to Ubuntu. Much of my hardware is the same except for more system memory (2 Gb) and a different graphics card (was ATI Radeon 8500 LE 128Mb). This go around I thought more system memory and a bit higher end graphics card would eliminate choppy Live TV. More notes on progress below - so much for simple.[/SIZE]
 
_**Hardware**_
**Motherboard: ****ASUS P4B533**
**CPU: Intel 2.4 Ghz**
**RAM: 2 Gb**
**Video Card: EVGA 6200 AGP 8x 512 Mb (NVIDIA GeForce chip) **
**Sound Card: integrated onboard** - C-Media Electronics Inc CM8738 (rev 10) (added edit 9/23/09)
**HD: 250Gb** 
**Remote: none**
**Tuners: Haupauge HVR 1600 (using ATSC)**
**Country: US**
**TV provider: US Broadcast**
**TV signal type: Digital (HD & DTV)**
**Mythbuntu Version: 9.04**
     Frontend/Backend & Backend for networked Frontend - (added edit 9/23/09)
 
_**Performance**_
 
_**8/1/09**_
 
[SIZE=2]As of a week or so of use, after initial setup with Windows 7 RC (worked fine including TV in the Media Center), my huge problem is trying to find working drivers for the new video card. So far nothing works and I'm forced to use the low end standard graphics supplied with Mythbuntu. I may be close to exhausting possibilities without success and need to resort to another ***!@@!#*!!!** graphics card purchase[/SIZE], [SIZE=2]Or as I did with my old card, record, clip commercials, and transcode to a basic viewing format.[/SIZE]
 
[SIZE=2]**_8/24/09_**[/SIZE]
 
[SIZE=2]With the kind assistance of a poster who answered my plea to point me to somewhere that would give me some hints on using the EVGA 6200 Graphics card I was able to actually use the card's dense graphics ability and get into the NVDIA config utility.  In other words it now works. The HVR 1600's chipset apparently has issues with ATI and NVDIA but tweaking vmalloc (I set it to 256 Mb) and XVMC I am back in business.  Aside from HD Live TV or any raw recording of HD being choppy it is performing well with any transcoded recordings.  I continue to learn and tweak.


[/SIZE]

---

### Post by jamestrowbridge on 2009-08-09
> **dadie11 said:**
> ..... hope this is not too late. I've been building this little swine for a year or so. Nearly there. Small graphics problem nearly sorted (slow and blocky) ~ remote is more problematical; especially as the config. is supposed to be the correct one. No apparent cooling problems, I have fitted a second fan on the northbridge, though. David Crawford.

This guy used an ODT upload, in order to make it easier, here is what is in that file:
Hardware
Motherboard:  Jetway J7F2WE2G
CPU:  VIA C7 2Ghz Processor  (CN700)
RAM: 1gb 533 Corsair DDR2 
Video Card: Via IGP
Sound Card: Onboard 6-Channel CODEC Compliant to AC 97
HD: 500gb Samsung 'Spinpoint' SATA2
Remote: Hauppauge 
Tuners:  Hauppauge Nova-T_500 PCI (2xDVB)
Country: England
TV provider: Terrestial DVB
TV signal type: E.g. DVB-T                                                                Additional 1) Jetway DVI add~on daughter board                                              2) Cubit 3 Case (White, if you're interested!)

---

### Post by blkmeth on 2009-09-05
_**Hardware**_ :D:D:D
**Motherboard:** Gigabyte S-Series GA-G41M-ES2H
**Chassis:** Chenbro PC405
** CPU:** Intel 930 Pentium D Dual Core 3 GHz 800Mhz FSB
**RAM:** 2GB Patriot PC2-6400 800MHz
**Video Card:** onboard video via m/b HDMI port
**Sound Card:** Realtec ALC888 HD onboard Audio
**HD:** Seagate 200GB (Single) 
**Remote:** Hauppauge TV remote (came with tuner card)
**Tuners:** Hauppauge WinTV-HVR 1600 Model 1178
**Country: E.g. the Netherlands:** North America (USA)
**TV provider: E.g. canal digital:** Comcast Cable
**TV signal type: E.g. DVB-S (satellite):** ATSC cable only (digital frontend hangs and drops)
**Mythbuntu Version:** Mythbuntu 9.04

_**Performance**_         

All hardware detected and fuctional except for digital tuner due to ivtv driver issues. Have to manually install mfg version audio HD driver ( Realtek ALC888 ) to get alsa sound mixer to work with onboard audio. Video card HDMI out does work in low graphics mode.

---

### Post by vixmusic01 on 2009-09-06
Hardware
Motherboard: Intel
CPU: Intel Pentium 4 2.00Ghz
RAM: 623.2 MB
Video Card:
Sound Card: Delta 44
HD: available 61.7GB
Remote:N\A
Tuners:N\A
Country:  Canada
TV provider:  none
TV signal type: N\A
Mythbuntu Version: N\A

Release Jaunty 9.04
-------------------------------------------
Ubuntu Studio Controls

Enable memlock checked 90%
Enable raw 1394 access checked

--------------------------------------------

NO SOUND

Delta 44 sound cards worked very well in Gutsy.
Now they don't work except with Audacity.

Preferences> Sound shows the cards, but when I try to play the test sound 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Everything else seems to work OK.

Can you help?

Victoria

---

### Post by Monteblanco on 2009-09-07
this is what i get..ive been trying to get compiz to work on my machine its a k8v-mx motherboard with a amd sempron 2800 (1.6ghz)processor and a VIA k8m800 512mb RAM and 80GB harddrive

 can someone help 
david@david-desktop:~$ chmod +x compiz-check
david@david-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
 Driver in use:         openchrome
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: openchrome driver in use

---

### Post by gunbladeiv on 2009-09-16
All my hardware detect flawlessly except for my microphone which doesnt work at all. I'm recoding a wind sound which means that my microphone do not work normally.  Anyone know how to solve this issue? 

I'm using karmic.  But so far that i know, jaunty also have the same problem. :(

---

### Post by TheStroj on 2009-09-16
Hardware
**Motherboard**: Asus P5Q PRO
**CPU**: Intel Core 2 Quad Q9400 @ 2,66 GHz
**RAM**: A-Data - 2x2GB 800 MHz DDR2 
**Video Card**: Gigabyte 9800 GT 1GB GDDR3
**Sound Card**: Integrated
**HD:** 500 GB
Remote:
Tuners:
**Country**: Slovenia
**Mythbuntu Version**: 

**Performance**
Everything works great!

---

### Post by Nathan.Flow on 2009-09-16
**Hardware**
**Motherboard:** ASUS M3A79-T Deluxe AM2+/AM2 AMD 790FX ATX AMD
**CPU:** Phenom II X4 940 Deneb 3.0GHz Black Edition 
**RAM:** OCZ Reaper HPC (2 x 2GB) DDR2 1066 (PC2 8500) 
**Video Card:** SAPPHIRE Radeon HD 4870 1GB 256-bit GDDR5 PCI Express 2.0 x16 HDCP Ready CrossFire Supported 
**Sound Card:** Onboard Audio-ADI AD2000B-8 Channels
**HD:**
**Remote:** N/A
**Tuners:** N/A
**Country:** N/A
**TV provider:** N/A
**TV signal type:** N/A
**Mythbuntu Version:** N/A

**Performance** Honestly, not sure, the biggest problems I have are with my mutable monitor setup, getting it work as I want is not quite as intuitive as I would like. Every thing seems to work as it should.:confused:

---

### Post by badger_fruit on 2009-09-16
_**Hardware**_
**Motherboard:   **Intel Pentium 4/Pentium D socket 775
** CPU:  Intel** 3.0GHz, 800MHz Front Side Bus, 2x1 MB cache
**RAM: 1GB**
**Video Card:  **On-board Volari Z7 16mb
**Sound Card: None**
**HD: 40GB** 
**Remote: None**
**Tuners: Hauppauge TD500**
**Country: UK**
**TV provider: Freeview**
**TV signal type: **DVB-T
**Mythbuntu Version: 9.04**

[U][B]Performance

[/B][/U]This is the server/backend setup, works perfectly well![U][B]

The clients that connect to it are 
[/B][/U]
IBM Thinkcentre S50
1GB RAM
3GHZ P4HT
NV6200 Gfx card
Ubuntu 9.04 on one, Suse 11.0 on the others (2)
Runs sweeeeeeeet

---

### Post by prupert on 2009-10-05
Hardware
Motherboard: Intel D945GCLF2
CPU: Intel Atom 330
RAM: 2 GB
Video Card: Intel Graphics Media Accelerator 950
Sound Card: Realtek ALC662 audio codec
HD: 500GB SATA WD
Remote: Hauppage MCE Remote w/ USB IR Reciever
Tuners: Hauppage WinTV NovaT USB DVB-T
Country: The UK
TV provider: Freeview
TV signal type: DVB-T
Mythbuntu Version: 9.04

Everything worked out of the box. All I needed to do was follow this: [http://ubuntuforums.org/showpost.php?p=7054850&postcount=38](http://ubuntuforums.org/showpost.php?p=7054850&postcount=38) to get the svideo out to work.

---

### Post by chipppy on 2009-10-09
Good Evening 
9.10beta works in the box as per hardware in signature all worked straight up including the standard install of the 2nd HDD.

Cheers
chipppy

---

### Post by belly917 on 2009-10-09
_**Backend Hardware:_**
[SIZE="1"]Motherboard:[/SIZE] IBM 8185-W2D
[SIZE="1"]CPU:[/SIZE] Intel Pentium 4 3.2Ghz
[SIZE="1"]RAM:[/SIZE] 1Gb
[SIZE="1"]Video Card:[/SIZE] Nvidia
[SIZE="1"]Sound Card:[/SIZE] Onboard
[SIZE="1"]HD:[/SIZE] Western Digital Caviar 300Gb
[SIZE="1"]Remote:[/SIZE] Included with DViCO FusionHDTV7
[SIZE="1"]Tuners:[/SIZE] DViCO FusionHDTV7 Gold (x1) & pcHDTV HD5500 (x2)
[SIZE="1"]Country:[/SIZE] USA
[SIZE="1"]TV provider:[/SIZE] Over-the-Air & Time Warner Cable
[SIZE="1"]TV signal type:[/SIZE] ATSC -> FusionHDTV7 & QAM256 (TWC) -> HD5500
[SIZE="1"]Mythbuntu Version:[/SIZE] 9.04

_**Frontend Hardware:_**
[SIZE="1"]Motherboard:[/SIZE] Asus
[SIZE="1"]CPU:[/SIZE] AMD X2
[SIZE="1"]RAM:[/SIZE] 2Gb
[SIZE="1"]Video Card:[/SIZE] XFX Nvidia GeForce 6200 *(AGP) (DVI->HDMI)*
[SIZE="1"]Sound Card:[/SIZE] Turtle Beach Audio Advantage Micro Virtual 5.1 Surround Channels USB Interface Sound Card *(optical to receiver)*
[SIZE="1"]HD:[/SIZE] Western Digital Caviar 40 Gb
[SIZE="1"]Remote:[/SIZE] Anyware HA-IR01SV (MCEUSB2)  *I use the USB receiver only with my Logitech Harmony 550*
[SIZE="1"]Mythbuntu Version:[/SIZE] 9.04

---

### Post by dhughes on 2009-10-11
**Functional Hardware**
**Motherboard:** Epox 8k5a2+
**CPU:** AMD Athlon XP2200+
**RAM:** 1GB DDR
**Video Card:** ATI Radeon All-in-wonder 9600XT 128MB
**Sound Card:** Realtek AC '97 (integrated/on-board)
**HD:** 80GB
**Remote:** none ******(see below)*
**Tuners:** Hauppauge PVR-150 (2004 on tuner sticker) *******(see below)*
**Country:** Canada (south eastern)
**TV provider:** Eastlink
**TV signal type:** Plain old regular cable
**Mythbuntu Version:** Mythbuntu 9.10 Beta

**Additional:**

***Remote** Some sort of IR type remote came with the PVR-150, I chose the driver lirc (?) during set-up of Mythbuntu i.e. I checked the box that yes I was using a remote, I think I picked just generic Hauppauge remote" or something like that. It didn't work.

****Tuner** During set-up I accidentally installed an older Hauppauge card (1998 is the year on the tuner body sticker) and it worked! I'm not sure what model it is, V4L was the driver that worked for it. Although the new one worked better, it uses the ivtv driver.

 Brand new install, my first ever so I'm still getting the bugs out but I'd say it's going pretty well, a bit jittery, but for a new install on such old hardware I'd say it's good.

**Non-Functional Hardware**

 **Output**This set-up is only being output to a computer monitor not a TV, I don't seem to be able to get it to show on my TV using S-Video and I don't have a VGA, DVI on my TV only RCA (red/white/yellow connectors) but I don't have an RCA cable.

edit: correction, the remote is working!

---

### Post by novellahub on 2009-10-19
**System has been retired **

_**Hardware**_
**Motherboard:** ECS GF8200a
**CPU:** AMD Phenom II X6 1055T AM3 (Hex Core)
**RAM:** Kingston HyperX 4GB (4 x 1GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500)
**Video Card:** eVGA Nvidia GT240
**Sound Card:** N/A (Audio via HDMI)
**HD:** Samsung 830 Series 64GB SSD,Western Digital GP 1 TB drive, 2 X SAMSUNG 2TB 5400 RPM SATA, Hitachi 1TB 7200 SATA drive
**Remote:** Microsoft MCE
**Tuners:** 3 X ATI HDTV WONDER VE, HDHR Prime
**Country:** United States (Minneapolis / St. Paul Metro area)
**TV provider:** Comcast QAM
**TV signal type:** HDTV (Panasonic VIERA TC-P42X1)

_**Performance**_
Fresh install of Mythbuntu 12.04 LTS as a master backend/frontend. Migrated recordings from backup of older 10.04 LTS install.  I had to download the tuner firmware and force the tuner types:

[http://www.linuxtv.org/wiki/index.php/ATI/AMD_HDTV_Wonder](http://www.linuxtv.org/wiki/index.php/ATI/AMD_HDTV_Wonder)

Machine boots in 10 seconds with the SSD.  I enabled noatime and discard options for the mounting of the SSD.

---

### Post by tnat on 2009-10-20
My hardware:
Motherboard: Gigabyte GA-G41M-ES2H
CPU: Intel Core 2 Duo E7400
RAM: 2GB DDR2
Video Card: onboard Intel GMA X4500
Sound Card: Realtek ALC887
HD: WDC 2,5" 160GB
Remote: Toshiba MCE PX1246E-1ETC
Tuners: 2x Hauppauge WinTV Nova-SE 2 PCI
Country: Austria (Europe)
TV provider: DVB-S Astra 19,2°
TV signal type: DVB-S
Mythbuntu Version: Mythbuntu 9.10 Beta

All hardware is working out of the box with updated Mythbuntu 9.10. 4 parallel recordings over the 2 dvb-s-cards while watching live-tv are no problem.
Greedy High-Motion x2 causes only 15% CPU usage. TV is connected to the DVI-port and gets 1920x1080@50 signal.

---

### Post by kenaveli on 2009-11-02
_**Hardware**_
**Motherboard: ASUS P4C800 DELUXE**
**CPU: P4 3.2GHz overclocked to 3.5GHz**
**RAM: 2GB **
**Video Card: BFG nVidia GeForce 7800GS OC 256MB DVI/TV-Out AGP**
**Sound Card: Soundblaster 5.1**
**HD:** 2 Western Digital 80 GB, 1 500 GB Ext US Seagate Freeagent
**Remote: KWORLD standard issue, currently no known solution to get this working. Using Microsoft wireless keyboard and mouse on my sectional couch.**
**Tuners: KWORLD 120 ATSC/NTSC connected to [Winegard SS-3000 Amplified [B]Indoor** UHF/VHF Antenna]("http://www.google.com/product_url?q=http://www.amazon.com/gp/product/B001DFZ5II&fr=AI0rofcuMchEpa8p6ArqMKDHh2o6_LTlxqgMgSGDvu-L8OLJkY7nsNOomg3_mAkJeq4Vxp_Yliy35JMkiGgmIynp4Gd6ysu3GZjKBtTCIgb04SHPq_y7xpsAAAAAAAAAAA&gl=us&hl=en&sa=title") [/B]
**Country: Colorado, USA**
**Display: Westinghouse 37 Inch 1080p Monitor using DVI cables**
**TV signal type: Digital Terrestrial Television **
**Mythbuntu Version: 9.10 downloaded on 10/29/09**
 
**All parts bought on Ebay. [B][COLOR=black][FONT=Verdana]All parts bought on Ebay. I have had this computer since 2002 and have made upgrades to it ever since.[/FONT][/COLOR]**[/B]
 
 
9.10 livetv is a lot smoother than 9.04 no V-sync issues anymore. VLC is way better than Xine.
130 processes running when watching live TV. 10% process usage too.
KWORLD 120 does not display signal strength, but does show S/N ratio, so it may be a little more difficult to tune to local terrestrial channels.
If you need help with the KWORLD 120, let me know. I used the steps listed in [http://www.mythtv.org/wiki/Kworld_ATSC_120](http://www.mythtv.org/wiki/Kworld_ATSC_120) and can verify it still works with mythbuntu 9.04 but much better in 9.10. 
I had to add the line sudo /etc/init.d/mythtv-backend restart to /etc/rc.local before the exit0 line, so that when I reboot the workstation the backend will launch otherwise you would have to restart the backend each time after reboot.

---

### Post by superm1 on 2009-11-02
> **kenaveli said:**
> _**Hardware**_
[B]Motherboard: ASUS P4C800 DELUXE
CPU: P4 3.2GHz overclocked to 3.5GHz[/B]
**RAM: 2GB **
[B]Video Card: BFG nVidia GeForce 7800GS OC 256MB DVI/TV-Out AGP
[/B]**Sound Card: Soundblaster 5.1**
**HD:** 2 Western Digital 80 GB, 1 500 GB Ext US Seagate Freeagent
**Remote: KWORLD standard issue, currently no known solution to get this working. Using Microsoft wireless keyboard and mouse on my sectional couch.**
**Tuners: KWORLD 120 ATSC/NTSC connected to [Winegard SS-3000 Amplified [B]Indoor** UHF/VHF Antenna]("http://www.google.com/product_url?q=http://www.amazon.com/gp/product/B001DFZ5II&fr=AI0rofcuMchEpa8p6ArqMKDHh2o6_LTlxqgMgSGDvu-L8OLJkY7nsNOomg3_mAkJeq4Vxp_Yliy35JMkiGgmIynp4Gd6ysu3GZjKBtTCIgb04SHPq_y7xpsAAAAAAAAAAA&gl=us&hl=en&sa=title") [/B]
**Country: Colorado, USA**
**Display: Westinghouse 37 Inch 1080p Monitor using DVI cables**
**TV signal type: Digital Terrestrial Television **
**Mythbuntu Version: 9.10 downloaded on 10/29/09**
 
**All parts bought on Ebay.  [B][COLOR=black][FONT=Verdana]All parts bought on Ebay.  I have had this computer since 2002 and have made upgrades to it ever since.[/FONT][/COLOR]**
[/B]

9.10 livetv is a lot smoother than 9.04 no V-sync issues anymore. VLC is way better than Xine.
130 processes running when watching live TV. 10% process usage too.
KWORLD 120 does not display signal strength, but does show S/N ratio, so it may be a little more difficult to tune to local terrestrial channels.
If you need help with the KWORLD 120, let me know.  I used the steps listed in [http://www.mythtv.org/wiki/Kworld_ATSC_120](http://www.mythtv.org/wiki/Kworld_ATSC_120) and can verify it still works with mythbuntu 9.04 but much better in 9.10.  
I had to add the line /usr/bin/mythbackend to /etc/rc.local before the exit0 line, so that when I reboot the workstation the backend will launch otherwise you would have to restart the backend each time after reboot.
You have another bug at play here.  I'd recommend temporarily commenting out your invokation of mythbackend in /etc/rc.local, removing /var/log/mythtv/mythbackend.log and rebooting.

Check the /var/log/mythtv/mythbackend.log after the reboot to see where things failed.  Common problems are usually permissions, not running as the "mythtv" user.

---

### Post by blue_z on 2009-11-02
_Hardware_
Motherboard: Intel D945GCLF2
CPU: Intel Atom 330
RAM: 2 GB DDR2 PC6400
Video Card: integrated Intel GMA 950
Sound Card: integrated audio
HD: WD 750 GB SATA
Remote: none
Tuners: EVGA inDtube USB NTSC/ATSC
Country: USA
TV provider: OTA
TV signal type: ATSC
Mythbuntu Version: 9.10

Functional backend+frontend.
The inDtube tuner needs the xc3028L-v27.fw file found on the web.  
720p and 480i broadcasts display smoothly on a 1024x768 VGA monitor, but 1080i channels would glitch every few seconds.  Changing the TV settings, video playback profile from the default "CPU+" to "high quality" resolved this.  Deinterlacing appears okay.
S-video output works w/o any extra tweaking.

---

### Post by superm1 on 2009-11-02
> **blue_z said:**
> _Hardware_
Motherboard: Intel D945GCLF2
CPU: Intel Atom 330
RAM: 2 GB DDR2 PC6400
Video Card: integrated Intel GMA 950
Sound Card: integrated audio
HD: WD 750 GB SATA
Remote: none
Tuners: EVGA inDtube USB NTSC/ATSC
Country: USA
TV provider: OTA
TV signal type: ATSC
Mythbuntu Version: 9.10

The inDtube tuner needs the xc3028L-v27.fw file found on the web.  
720p and 480i broadcasts display smoothly on a 1024x768 VGA monitor, but 1080i channels would glitch every few seconds.  Changing the TV settings, video playback profile from the default "CPU+" to "high quality" resolved this.  Deinterlacing appears okay.
S-video output works w/o any extra tweaking.
Can you check if that firmware is in linux-firmware-nonfree?  If it's not, please file a bug on launchpad.net/ubuntu/+source/linux-firmware-nonfree to get it included for Lucid.

---

### Post by hibit on 2009-11-09
Hi There,

Here is my spec, its a combined front and backend:

**Hardware**
Motherboard: Asus M3A78-EM
CPU: AMD Phenom(tm) II X4 920
RAM: Corsair XMS2 4GB (2x2GB) DDR2 PC2-8500C5 TwinX Dual Channel
Video Card: Onboard video, ATI Radeon  HD3200
Sound Card: Onboard audio, stereo outputs to TV inputs (red/white)
HD 1: WDC WD360GD-00FL
HD 2: ST3320620AS
Remote: Standard remotes from each tuner card / remote with case
Case: Antec Fusion Remote
Tuner 1: KWorld/VStream XPert DVB-T
Tuner 2: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2
Country: UK
TV provider: Freeview DVB-T, Freesat DVB-S
TV signal type: Aerial and Satellite
Mythbuntu Version: 9.10 Karmic

What works:

VGA output to the PC input of a Sony 32" flatscreen.
Freeview DVB-T works great.
I got the LCD panel on the Antec case working to a point with a lot of trial and error.

What doesn't work:

Needed to download firmware (dvb-fe-cx24116.fw) for the Hauppauge DVB-S card and install it
The Hauppauge DVB-S card no longer works after the upgrade to Karmic
Any of the three remotes (either of the two remotes with the tuners, or the one with the case)
Had trouble with HDMI output on Jaunty but haven't tried yet with Karmic

Hope this helps

---

### Post by fromgi on 2009-11-09
Floppy drive does not mount via Nautilus.  You can however mount from terminal.  Also, even though the Gnome Desktop Utilities from the Software Center say that "gfloppy" is installed, it is not.  Also, Synaptic say the gfloopy is install with gnome-utils, it too is not.

---

### Post by pootle1 on 2009-11-10
I've just finished upgrading a split frontend / backend system to work with freesat to get BBC HD.

It's now working well (digital audio out was a real hassle) using VDPAU.  Picture quality is mostly good on BBC HD, although not as smooth as a Humax Foxsat HD.  Occasionally gets very confused and pxellated for 5 - 10 seonds.  Doesn't work so well on LUX HD - something in there is tripping it up.

On a 22" screen looks fine, its only a really big screen that shows up lack of smoothness in playback.

Ubuntu 9.10 with MythTV 0.22 and Nvidia drivers 190.42

GPU core temperature goes up to 36 C and max speed when VDPAU running (from 26 C

**Hardware**
Motherboard: ASUS M2N PV delux
CPU: AMD Athlon(tm) 64 Processor 3500+
RAM: 2Gb el cheapo
Video Card: gigabyte GeForce GT 220 DDR3
Sound Card: motherboard
HD 1: WD 250GB SATA
Remote: none
Case: Antec of some sort
Tuner 1: Hauppauge NOVA-T 500 dual (on separate front end
Tuner 2: Hauppauge WinTV- DVB-S/S2 (on separate front end
Country: UK
TV provider: Freeview DVB-T, Freesat DVB-S
TV signal type: Aerial (WinterHill) and Satellite (Astra 28.2E)
output via HDMI switcher to Viewsonic 22" and front projector

Mythbuntu Version: 9.10 Karmic

---

### Post by proyectomx on 2009-11-10
My system is a Dell Studio 1535 laptop.

It actually has ubuntu 904 installed, and everything works like a charm... I mean, unless I want to use my bluetooth mouse.

I have a Microsoft Bluetooth Laser Mouse 5000. When I try to pair via the bluetooth device manager, it shows the device as paired, but it does not connect to the computer.... in fact, it stops connecting in my other OS (windows vista). Only with a firmware and driver reinstall (replace) it works again under windows, but it never works under ubuntu.

My problem is.... that I have posted THREE times this problems in these forums, with not even one person telling me something or asking me for any more details, so I hope this thread is for this case.

Please, do not send me to the store to buy another mouse, that is a big deal for me.... besides, would you tell that to a new ubuntu user?

by the way, I googled the answer, with no luck. Hope somebody here has an idea of what's going on with my bluetooth mouse.

---

### Post by pootle1 on 2009-11-10
given your problem has nothing to do with Myth, I'm not surprised you didn't get an answer if you posted in this forum.

try this [link]("http://www.google.co.uk/url?sa=t&source=web&ct=res&cd=1&ved=0CAkQFjAA&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D227057&ei=bX75SrCQEYWw4QbprtzACw&usg=AFQjCNGwtJxs7mamY0HaU7x7gwK9PgttWQ&sig2=mIdLEEVm_aUPMYL5tY8FFA"), which was first hit on a search in google for bluetooth mouse ubuntu

---

### Post by proyectomx on 2009-11-10
Thank you very much.
I will give it a try tonight, when I get home.

by the way, I posted in this forum to see if somebody would really answer, when I first posted, I entererd ubuntuforums.org and posted under a cathegory, I don't remember which one.

Thanks very much, will try that, see if it works.

---

### Post by novellahub on 2009-11-11
*** Hardware has been retired ***

**_Hardware**_
**Motherboard:** EPoX 8RDA6+ Pro 
**CPU:** AMD Athlon XP 3200+
**RAM:** OCZ 1GB (2 x 512) DDR SDRAM (DDR 400)
**Video Card:** EVGA nVidia e-GeForce 8400 GS 512 MB DDR2 PCI
**Sound Card:** Sound Blaster Audigy PCI
**HD:** 40 GB Maxtor EIDE, 160 GB Western Digital IDE, 80 GB Samsung IDE
**Remote:** Streamzap
**Tuners:** 4 X Kworld 115
**Country:** United States (Minneapolis / St. Paul Metro area)
**TV provider:** Local Broadcast
**TV signal type:** SD (Sanyo 31 inch CRT TV)

**_Performance**_
Fresh install of Mythbuntu 9.10 (Later updated to 10.04.3 LTS) as a slave backend/frontend. I had to download the tuner firmware:

[http://www.mythtv.org/wiki/Kworld_ATSC_110](http://www.mythtv.org/wiki/Kworld_ATSC_110)

I did a customized install where the root partition (/) uses 10 GB (ext3). The rest of the space on the hard drive was formatted as /myth using XFS. The 160 GB is formated to XFS and mounted as /myth2.  The 80 GB drive is formatted as well with XFS and mounted as /myth3.

---

### Post by MountainX on 2009-11-12
****_**Hardware**_
**Motherboard:** Asus P4P800[B]
CPU:[/B] Intel(R) Pentium(R) 4 CPU 2.40GHz
**RAM:** 2012MiB
**Video Card: **ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
**Sound Card:** Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
**HD:** N/A
**Remote:** None
**Tuners:** Hauppauge PVR-150
**Country: E.g. **USA
**TV provider: **Comcast Digital Cable
**TV signal type: **Cable
**Mythbuntu Version: **9.10 32 bit

[U][B]Performance
[/B][/U]I am happy to say I just got MythTV working on this hardware! :) I'm new to MythTV. But it works!

---

### Post by blkmeth on 2009-11-14
> **blkmeth said:**
> _**Hardware**_ :D:D:D
**Motherboard:** Gigabyte S-Series GA-G41M-ES2H
**Chassis:** Chenbro PC405
** CPU:** Intel 930 Pentium D Dual Core 3 GHz 800Mhz FSB
**RAM:** 2GB Patriot PC2-6400 800MHz
**Video Card:** onboard video via m/b HDMI port
**Sound Card:** Realtec ALC888 HD onboard Audio
**HD:** Seagate 200GB (Single) 
**Remote:** Hauppauge TV remote (came with tuner card)
**Tuners:** Hauppauge WinTV-HVR 1600 Model 1178
**Country: E.g. the Netherlands:** North America (USA)
**TV provider: E.g. canal digital:** Comcast Cable
**TV signal type: E.g. DVB-S (satellite):** ATSC cable only (digital frontend hangs and drops)
**Mythbuntu Version:** Mythbuntu 9.04

_**Performance**_         

All hardware detected and fuctional except for digital tuner due to ivtv driver issues. Have to manually install mfg version audio HD driver ( Realtek ALC888 ) to get alsa sound mixer to work with onboard audio. Video card HDMI out does work in low graphics mode.

**UPDATE**

Attempted to load 9.10 on new harddrive on my existing i386 system config in the event of any 9.10 upgrade issues to preserve current working system setup.

Just as I suspected, 9.10 will not even install/load on my current 9.04 i386 h/w setup.

I tried loading the livecd = no load; the install on new hdd = no load; new hdd install in safe graphics mode = no load.

I have an AMD 64bit system built and 9.10 loaded without a hitch. Even the onboard sound works right out the box. The only thing is my Hauppauge WinHVR 1600 card. The analog tuner using IVTV hangs @ 5% while scanning channels (never completes a channel scan). The digital tuner works like a dream. Also, my Hauppauge remote doesn't work with 9.10. I tried all variants of the Mythtv Hauppauge lirc remote settings. All tuner functions and remote does work with 9.04.

Will stick with 9.04 for now.

---

### Post by port443 on 2009-11-25
_**Hardware**_
**Motherboard: **ZOTAC GF9300-D-E LGA 775 NVIDIA GeForce 9300 HDMI WiFi Mini ITX Intel Motherboard
** CPU: **Intel Pentium E5200 Wolfdale 2.5GHz LGA 775 65W Dual-Core Processor
**RAM: **2Gb (2x1Gb) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Desktop Memory Model KVR800D2N6/1G
**Video Card: **onboard (HDMI)
**Sound Card: **onboard (via HDMI)
**HD: **4Gb Sandisk Contour USB Flash Drive 
**Remote: **Mediagate GP-IR01BK Vista MCE Remote Control
**Tuners: **none
**Country: **Canada
**TV provider: **none
**TV signal type: **none
**Mythbuntu Version: **9.04

**Additional:** case (temporary) APEX MI-100; Pico-PSU 120; Cooljag fanless heatsink; single 120mm noiseblocker XL1 fan = no noise :)

[U][B]Performance
[/B][/U]One issue so far: big DVDRip (or BlurayRip), 8.2Gb, ~15Mbit/sec, MKV plays with some hiccups.  Network or CPU seem not to be an issue.

---

### Post by wackston on 2009-12-01
_Hardware_
Motherboard: ASUS M2NPV-VM Graphics Nvidia nForce430 chipsey
CPU: AMD Athlon X2 6000
RAM: 2Gb  SDRAM DDR2 800 (PC2 6400) Desktop Memory Model KVR800D2N6/1G
Video Card: Onboard NVIDIA 6150  (HDMI)
Sound Card: onboard (via SPDIF)
HD: Myth-TV backend via Gbit Ethernet (onboard)
Remote: none
Tuners: 3 x Hauppauge Nova-S2 1xHauppauge WinTV Nexus-S 1x Hauppauge WinTV Nova S-plus (on dedicated mythtv backend)
Country: Germany
TV provider: Astra 19.2E and 28E 
TV signal type: DVB-S and DVB-S2 
Mythbuntu Version: 9.10

_Performance_
SDTV - perfect
720p and 1080i - rare tearing high on frame but stable jitter-free playback (BIG exception H.264 streams whose profile is affected by known ffmpeg bug).
Needed to adjust CPU throttling threshold for HDTV.
Heavy CPU load during HDTV playback needing excessive fan activity on PSU.  (Gonna move to VDPAU and a single-core CPU).
Rare crashes of front-end - not easily reproducible.
Hanging/crashing of front-end when backend attempts to tune DVB-S2 channels with DVB-S tuner.

---

### Post by matt06 on 2009-12-06
**_Hardware_**
**Setup:** Primary Backend/Frontend (currently headless)
**MB:** Abit IS7-V2
**CPU:** P4 3.0GHz
**RAM:** 2.0GB DDR [S]1.0GB DDR[/S]
**Video:** NVidia GeForce 5500 128MB AGP
**Audio:** Onboard, ICH5
**LAN: ** Realtek-8169 PCI 1Gbps
**HD:** 160GB (various IDE) + 1TB Hitachi ST6OA31B (SATA)
**Tuners:** (2) Hauppauge HVR-1600 PCI
**Signal:** Analog Cable x 2 + OTA Digital x 2
**OS/Software:** Mythbuntu 9.10

**_Performance_**
Compiled and installed latest [v4l-dvb drivers]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Drivers") (info might be out of date).  Both analog and digital works, but MythTV scanner missed a few digital channels until antenna positioning was tweaked.  Cable company only offers few digital clear-QAM channels so I use strictly OTA digital.

I also tweaked /etc/X11/xorg.conf for video performance and other issues with my GeForce 5500.  I've been running this as a backend since 11-2008 and upgraded 8.10 -> 9.04 -> 9.10 without any major issues.  I also periodically compile and install the newest v4l-dvb drivers.  This is also my file/music/picture/video server for my Windows network using CIFS shared folders.

***Edit***:  added an additional GB of RAM, no perceived performance difference.  Frontend reports that backend is using up to 1.9GB used after watching a show, but normally 400-1800MB [S]400-600MB[/S] when idle.

**_Hardware_**
**Setup:** Frontend Only
**MB:** P4M900-M4
**CPU:** Celeron 2.0GHz
**RAM:** 1GB DDR2
**Video:** ASUS GeForce 8400GS 512MB[G98] (SVideo out)
**Audio:** Ensoniq ES1371 PCI
**LAN: ** Onboard VIA VT6102 [Rhine-II]
**HD:** RiDATA 4GB RDCF4G-233X-LIG CF IDE + SYBA SD-CF-IDE-A Adapter
**Remote:** [MCEUSB2]("http://www.mythtv.org/wiki/File:MCE-Remote-2-v1069.jpg") (comes with Hauppauge HVR-1600)
**OS/Software:** Mythbuntu 9.10 + fixes

**_Performance_**
I tweaked /etc/X11/xorg.conf for video performance and other issues with my [S]GeForce 4 MX 4000[/S] GeForce 8400.  I mount CIFS shares over the network in /etc/fstab which gives me access to my music, pictures and videos in MythTV.  I also changed "[swappiness]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")" to 10 since I'm using a CF card, but I still have about 120MB [S]330MB[/S] swap that is almost never used.

[S]Still[/S] [working on getting suspend/resume working]("http://ubuntuforums.org/showthread.php?p=8448447&highlight=nvagp#post8448447") on the frontend with NVidia drivers set to NvAGP 1 and acceptable HD playback.  Other than that, I'm a happy camper. ***Edit***: this no longer applies to my current frontend, but left for reference since I had [fixed it]("http://ubuntuforums.org/showthread.php?p=8487456&highlight=nvagp#post8487456").

***Edit***:  built a new frontend to replace my old one.  ATSC HD playback is fine with the Celeron 2.0 and 8400GS using VDPAU.  Had trouble with onboard audio on the new board as well so I used the same PCI sound card.  Removed MythGame and the MS Gamepad since I have no time.

**_Hardware_**
**Setup:** Spare Frontend
**MB:** Abit IS7-V2
**CPU:** P4 3.0GHz
**RAM:** 512MB DDR
**Video:** NVidia GeForce4 MX 4000 128MB AGP (SVideo out)
**Audio:** (onboard)
**LAN: ** Onboard Realtek-8139 100Mbps
**HD:** RiDATA 8GB CF IDE + SYBA SD-CF-IDE-A Adapter
**Gamepad:** [S]Microsoft Sidewinder Gamepad (Gameport)[/S]
**Remote:** n/a
**OS/Software:** Xubuntu 9.10 + Mythbuntu Control Center + MythTV fixes

**_Performance_**
See above.

Many Thanks to Linux, Ubuntu, v4l, cx18, lirc, MythTV, MythBuntu and all other developers!!

---

### Post by voyteckst on 2009-12-16
**Hardware**
Setup: Frontend and Backend
MB: Asus P5Q-EM
CPU: C2D E8400
RAM: 4GB DDR
Video: Radeon HD5770
Audio: Integrated
LAN: Onboard Realtek
HD: WD 320GB
Tuners: AverTV Trinity A707 (Analog, DVB-T, DVB-S)
Remote: Logitech Dinovo Mini
OS/Software: Mythbuntu 9.10

**Problems:**
- [COLOR="Red"]TV Tuner completely doesn't work...[/COLOR]
- had to install PulseAudio to change audio output to HDMI
- had to install some apps to change default (very very small) QT apps fonts
- had to upgrade fgrlx, because default did not support my graphic card

---

### Post by myth_cougar on 2010-01-03
_**Hardware**_
[B]Motherboard: Gigabyte GA-MA78GM-S2H
CPU: AMD 4850e[/B]
**RAM: 2Gb DDR2 800 **
[B]Video Card: HD3200 (Integrated)
                    Tried NVidia GT220
[/B] **Sound Card: Integrated**
**HD: 1x1Tb Seagate SATA 1x500Gb Seagate SATA** 
**Remote: Hauppage via PVR-350**
[B]Tuners: Hauppage PVR-350 (connected to Sky+ s-video)
             Hauppage Nova T-500
[/B] **Country: UK**
**TV provider: Freeview**
**TV signal type: DVB-T**
**Mythbuntu Version: 9.10**

_**Performance**_
The above works quite well, currently used for standard def, as I haven't any hi def stuff.  Originally tried an NVidia GT220, but this had poor performance from the open source driver and the nvidia drivers need to be at least version 190 (karmic has 185).  I did manage to install the 190 drivers from avenard along with the updated mythtv (a trial in itself), but I found stability to be an issue along with an annoying freeze for several seconds at a time and a loss of sound.  Tried various suggested fixes but without success.

My original reason for aquiring an nvidia card was due to image tearing in video playback on the HD3200 which I couldn't find a fix for (this was using mythdora btw).  Buying the gt220 was the opportunity to update to mythbuntu, but I was dissapointed with the gt220, I guess I have to wait for the software to catch up.  I found a thread regarding the video tearing on the hd3200 suggesting the radeonhd driver, so I removed the gt220 and reinstalled mythbuntu on a separate partition, intalling the radeon driver and then updating to the radeonhd driver in edgers repo.  After configuring xorg.conf, including the hdmi audio options,  video is tear free, audio is via hdmi and no problems with freezing.  Minor glitches have been seen in playback which have coincided with autoexpire messages appearing in the logs, so I am looking into what is going on there.  Otherwise playback is smooth.

One thing I still have to sort out is the remote.  I selected the hauppage remote (several different options here), but none appear to be working.  Shouldn't be to big a problem to sort out, currently using a wireless keyboard/mouse so no rush.

---

### Post by User X on 2010-01-04
**Hardware**
**Motherboard:** ASUS ? (nforce 4 chipset)
**CPU:** AMD Athalon 64 X2 3800+
**RAM:** 4Gb DDR 400
**Video Card:** BFG Tech Nvidia 9600 GT
**Sound Card:** SB Audigy X-Fi
**HD:** 1x 40Gb for OS, and 1x 200Gb for recordings
**Remote:** iPhone, running Hippo remote (highly recomended)
**Tuners:** Hauppauge HVR-1250
**Country:** USA
**TV provider:** OTA DTV
**TV signal type:** ATSC
**Mythbuntu Version:** 9.10 frontend/backend

**Performance**
     Performance is good.  Live TV is excelent, I am having a problem with recording image quality, but I expect I will be able to solve the issue. Everything worked without any tweaking so far.  I have also added the Hulu Desktop application and launch it from the MythTV frontend.  Video from hulu is good - not the best.

edit: The recording playback problem was resolved by enabling VDPAU playback profiles, and now the performance is excelent.  I will be adding a remote and possibly another tuner to the system shortly.  Viewing ATSC in HD, recording in HD, and playback in HD all work very well.  Schedules direct was added for programing information and integration was seamless.  This seems to be a very stable configuration so far.

edit: Added remote reference, added Boxee and launch it through MythTV.  The Hippo Remote is a VNC app for the iPhone that has native support for Ubuntu and profiles for boxee and hulu built in.  Also works as a remote trackpad and keyboard in Ubuntu for doing all sorts of computer tasks that would otherwise require me to have a wireless keyboard and mouse in my living room. Quite happy with the current set up!

---

### Post by brianko on 2010-01-04
Update:

[I]Hardware 
MainBoad:  Asus M2N-E 
CPU: AMD Athlon 64 X2 4200+ dual core 
RAM: 2 GB 
Video Card: nVidia nForce 570 Ultra 
HDD: WD 500MB PATA 
Tuners: Hauppauge PVR-350 
Sound Card: onboard

[/I] I now consider this setup **non-functional.**  After freezing on fast-forward during playback, the sound dropped from all recorded tracks.  No one seems to be able to resolve the issue. I do not recommend this hardware setup.  (In addition, it appears that PVR-350 support is deprecated in the latest version of Mythbuntu (9.10); indeed, an upgrade to 9.10 was unsuccessful).

Some additional research indicates problems with AMD dual-core processors.  Might be something to be wary of as well.  Good luck, as I've given up on Mythbuntu.

---

### Post by jquintana on 2010-01-05
Hello, all. I'm new to MythTV and Ubuntu all together. I'm looking to re-use some existing hardware (CPUs) but I do realize I will need a new motherboard. I would like a motherboard with on-board HDMI output to use with my TV.

The main purpuse of my system is to store HD content from my Comcast cable box, HD movies, music, and picture slideshows. I would like to use MythBuntu 9.10 as I have already tested it out on a Virtual Machine and am happy with it.

I would like to use either a P4 or AMD Sempron 3200+ that I have laying around. 

RAM, HDD, and case are not issues. I just need a good motherboard with HDMI output.

Thanks for the help.

---

### Post by liquidonline on 2010-01-09
Hi guys,

Just installed mythbuntu 9.10, I've been a long time ubuntu user and finally got "with the program" and got an LCDTV.  First order of business was an HTPC of course!  There is (what appears to be) an unresolvable showstopper problem right now which is pushing me to buy Win 7 home to run xbmc on...

**Hardware**
**Motherboard:** Abit IL-90MV intel VIIV technology **w/onboard HDMI**
**CPU:** Intel Core 2 Duo T7200 (2.0ghz)
**RAM:** 4Gb DDR2 667 (3.5 visible)
**Video Card:** onboard intel GMA 950
**Sound Card:** integrated Realtek 7.1 HD audio w/spdif in/out
**HD:** 500GB seagate
**Remote:** ebay mini wireless kb/trackball
**Tuners:** none yet
**Country:** Canada
**TV provider:** Will be going with FTA to onboard DVB/DVA HD tuner to complement my expressvu subscription :)

**TV signal type:** N/A
**Mythbuntu Version:** 9.10 frontend/backend

**What doesn't work:**  Audio over HDMI.  I've tried everything I can find so far and this IS a show stopper for me because the audio out of the 3.5mm audio cable sucks

Given how the intel video driver works with the windows driver (according to the manual) I'm open, reluctantly, to the possibility it's related to the intel driver - but I'm doubtful.

---

### Post by pnauta on 2010-01-09
Hi,

I've been using Mythtv since 7.10, had a lot of trouble but it's getting there now.

**Hardware**
**Motherboard:** Asus M3N78-EM
**CPU:** AMD 5050e
**RAM:** 2GB
**Video Card:** NVidia 8300 on board
**Sound Card:** Realtek ALC1200 7.1 HD audio w/SPDIF out
**HD:** 1,5TB Samsung Spinpoint Green 5400RPM
**Remote:** Logitech Harmony One
**Tuners: **Digital Everywhere FloppyDTV DVB-T with Conax CAM and subscription card
**Country:** Netherlands
**TV provider: **Digitenne (DVB-T)
**TV signal type: **DVB-T
**Mythbuntu Version:** 9.10 frontend/backend
**Receiver:** Sony STR-DB 930 5.1 with SPDIF in
**TV:** Samsung LE40B530 (1080p) 3 X HDMI, SPDIF out

**What doesn't work:** Struggled with audio/video at first, but finally have everything working.  I can record any channel from Digitenne (also encrypted commercial channels)  Sometimes recording multiple channels fails.  Sometimes ISO's of DVD's I ripped don't work, these same ISO's work when I play them using VLC on Windows.  Also, the EDID data for my TV is wrong so VLC has enormous fonts which make it impossible to use.

---

### Post by baldydonald on 2010-01-13
_**Hardware**_
**Acer Revo 3600**[B]
CPU: dual core intel atom N330[/B]
 **RAM: 1G**
 **Video Card: nvidia ION**
 **Sound Card: on-board**
 **HD: not using it, so don't know if the CPU can cope** 
 **Remote:** Hauppauge WinTV 35 key &quot;wafer-thin&quot; DSR-0112
 **Tuners:** Hauppauge WinTV Nova-T USB Dual Tuner
 **Country: UK**
 **TV provider: UK Freeview**
 **TV signal type: DVB-T**
 **Mythbuntu Version: 9.10**
 
 [U][B]Performance
[/B][/U]In short: very good:
When idle or recording, gnome system-monitor indicates a total CPU load of <10%
When playing non-HD video, total CPU load around 10-15%
About 50% of memory used by file cache, 20% or so by programs (
Using nvidia 185 drivers, and &quot;VDPAU Normal&quot; playback profile.
Remote works, but is not the best device in the world (will post config files etc) - I use a wireless keyboard/trackball, which works out of the tin - [http://www.gizoo.co.uk/Products/PCGaming/Wireless/WirelessKeyboard.htm](http://www.gizoo.co.uk/Products/PCGaming/Wireless/WirelessKeyboard.htm) and is conveniently small
Not using HDMI: using VGA output through a GRANDTEC HAND VIEW III VGA TO TV adaptor (one of the many cables it comes with has a scart plug connected to a VGA plug & 3.5mm audio socket) - some screen tearing, and frame loss leading to jerky images, but still very watchable. Screen tear and frame loss appears to be a function of the VGA adaptor, because plugging in a Samsung SyncMaster 913v VGA LCD monitor in instead does not exhibit either symptom.
Some issues with tuning the USB stick, occasionally has lots of corruption, switch channels (retune to different mux), switch back and everything is ok - not sure if this is a card/driver problem, or reception (signal strengths are between 79% and 95%, so seems unlikely?)

---

### Post by aovermy on 2010-01-21
hardware: nforce 2 motherboard with AMD XP 2400 CPU
6 SATA drives, 1 PATA drive
1 FusionHDTV USB ATSC tuner
1 nxt2004 ATI HDWonder ATSC tuner
1 nxt2002 Air2PC v 2 ATSC tuner (flexcop variant, not broadcom)
1 Plextor M402U USB NTSC device (SVIDEO + LR audio from dish receiver)
1 NVIDIA 6200 video card

The hardest part I had was getting past booting! The grub 2 (and even legacy grub) is not happy when drives shift (that is, linux sees /dev/hdg as 7th drive, but bios sees it as first drive because it's PATA). I finally had to boot with alternate install CD from ubuntu, install lilo bootloader, then install the mythbuntu-control-desktop to convert the ubuntu to mythbuntu.

The Fusion HDTV game me no trouble, it was set up out of the box.

The ATI HDWonder had to get nxt2004 firmware using the get_dvb_firmware.pl script from the linuxtv.org site.  I knew from past experience the Fusion tuner used bluebird, so I just did a locate for that file and put the nxt2004 file in the same place.

The plextor device uses the go7007 driver, which I found at go7007.imploder.org. All I had to do was install the tools needed to build a kernel plus libncurses5-dev, then run make and make install. Then I needed to copy the file in the driver source at udev/go7007_firmware_load to /usr/sbin because the make install puts the wrong file there.

The air2pc v 2 was a nightmare! The get_dvb_firmware.pl file no longer works to retrieve the nxt2002 firmware because the web site it's using has changed the file, so the offsets and hashes don't match anymore. Fortunately I had an old copy from an old mythtv install lying around, so I was able to use it.

It's all working now. I'm able to record and watch on another machine. I've tested all the tuners and they all work appropriately. 

The intent is that this hardware will only be used for backend purposes, while a couple of different machines with VDPAU capable video cards will be the frontends.

---

### Post by caravanman on 2010-01-22
Hardware
AMD64
1gb ram
Graphics Nvidia GeForce 6600LE

[B]Performance
About 30 seconds after the desktop has loaded Computer Freezes
[/B]

---

### Post by jmagee on 2010-01-24
_**Hardware**_
**Motherboard: **Gigabyte M85M-US2H (rev 1.2)[B]
CPU: [/B]AMD Sempron 2.7Ghz (AM3)
**RAM: **4GB Kingston
**Video Card: **On MB
 **Sound Card: **On MB
**HD: ** 1TB WD Caviar Green
**Remote:** Hauppauge
**Tuners:** Hauppauge WinTV Nova-T (PCI)
**Country: E.g. the Netherlands:** UK
**TV provider: E.g. canal digital: **Freeview
**TV signal type: E.g. DVB-S (satellite): **DVB-T
**Mythbuntu Version: E.g. 8.10** 9.10

_**Performance**_

Everything smooth apart from the remote, which didn't work out of the box. Followed the guidance @ [http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php) and was sent appropriate config files by a friend, tho I suspect good google-fu would produce the files too. 

Big thanks to the Mythbuntu people for a very nice product, very nice to see FOSS with a strong emphasis on usability.

EDIT: Forgot to say, installed from flash disk, using UNetBootIn. Previously, had put Ubuntu on a netbook via this method and had to manually edit grub files, but for this install, no trouble at all.

---

### Post by dougsnell on 2010-01-26
I don't believe I've ever posted my hardware.  I've had it running for a few years now.  The main system is an Everex gPC.  Low power, but it has very few problems for standard def.

_**Hardware**_
**CPU:** VIA C7-D 1.5 Ghz
**RAM:** 512 gb VIA UniChrome Pro Shared video memory (UMA) (64 Mb reserved)
**Remote****: ** Logitech Harmony One (configured as a PVR 350)
**HD:** Upgraded over time to a 2 Tb WD "green" drive (again, low power ... low noise)
**Tuners:**
Hauppauge PVR-350
Hauppauge PVR 500 (dual tuner)

[U][B]Performance
[/B][/U]All hardware properly detected and functional.
Required to use PVR 350 HowTo's; current is 9.04.

**Sound Card:** on-board
**Country: **US
**TV provider: **Comcast
**TV signal type: **Standard Cable
**Mythbuntu Version: **9.04

_**Performance**_
Probably sad that I spent more on the tuners than the system.  I also spent nearly as much on simply the HD upgrade.

---

### Post by ViktorB on 2010-01-29
[B][U]Hardware
[/U]Motherboard: [/B]Asus P5QPL-VM EPU
**CPU:** Intel Pentium E6300 Dual Core
**RAM:** Kingston 4GB 1333Mhz DDR3
**Video Card:** Intel on board GMA5400
**Sound Card:** Realtec on board 887
**HD:** Western Digital 160GB for the system and Samsung HD321KJ for the media
**Remote:** So far Mouse and Keyboard
**Tuners:**Hauppauge Nova 500 HD (Dual DVB-T) and Hauppauge HVR-4000 (DVB-T)
**Country:** Sweden
**TV provider:** Free channels
**TV signal type:** DVB-T
**Mythbuntu Version:** 9.10

_**Performance:**_
New to Linux it took me a while to get it up and running. Spent some time over Christmas puting it together with both Backend and Frontend on the same system. It's been working fine over a month. Records nicely five channels simultaniously, where one is HD quality. Not that I expect to need that level of performance, but it works.
 
Next is to get a Remote working. Would be nice to control from an Andriod, or iPad.

---

### Post by philaphonic on 2010-01-30
_**Hardware**_
**Motherboard**: MSI 785GM-E65
**CPU**: Athlon II X2 250 3 GHz
**RAM**: 2 GB Kingston DDR3 1333 MHz
**Video Card**: onboard ATI 4200 GPU
**Sound Card**: onboard Realtek ALC888S/ALC889
**HD1**: Western Digital WD1600BEKT 160 GB
**HD2**: Western Digital WD10EADS 1 TB
**Case**: Antec Fusion black
**Remote**: included with case
**Tuners**: Hauppauge PVR-500
**Country**: USA
**TV provider**: Comcast
**TV signal type**: analog cable
**Mythbuntu Version**: 9.10

_**Performance**_
Live TV and recording/playback are functional, have not tested most other features.  Graphics are buggered (video tearing; resolution and vertical hold issues) due, I assume, to my using the onboard ATI graphics.  Also, using an outboard VGA-to-TV converter for my basic analog TV which accepts S-video.  Have several nagging problems with the case's LCD display.

---

### Post by wirepuller134 on 2010-01-31
Hardware
Motherboard: don't know, would have to open it.
CPU: 	Intel(R) Pentium(R) 4 CPU 2.80GHz, 2 cores
RAM: 3 GB DDR 400
Video Card: Nvidia 7300 gt
Sound Card: onboard Realtek
HD1: Seagate 80 gb
HD2-4: Toshiba 1 TB
Case: Bosch 5u (retired DESA server that was traded into us)
Remote: PVR-150 remote
Tuners: Hauppauge PVR-500 x 3/ PVR-150 x 1
Country: USA
TV provider: Directv
TV signal type: analog cable coming from a media combiner so we have all of our satellite tuners sitting in one spot.
Mythbuntu Version: 9.10 upgraded from 9.04 through update manager

Performance:
We use this for the primary backend/front end.  We also have 2 Acer Revos with Firefly remotes as remote front ends.  Nice quality play back on the local and remote front ends. Had a bit of trouble with video permissions using multiple hard drives and NAS storage.  
  Doesn't like to have the DVD drive opened using the button on it, prefers to use the icon in Myth-frontend. I haven't looked into this much, as it is just as easy to use the remote and have it open as it is to push the button to open the tray.

---

### Post by TheMiz on 2010-02-01
_**Hardware**_
**Motherboard: **Zotac IONTIX-G-E
** CPU: **Intel Atom 330 1.6 GHz
**RAM: **1 GB
**Video Card:** integrated GeForce 9400
**Sound Card: **integrated (I am using HDMI)
**HD: **250 GB Western Digital 
**Remote:** FusionRemote (bundled with my tuner)
**Tuners: **DViCO FusionHDTV7
**Power Source: **200W
**Country: **United States
**TV provider: **Mediacom
**TV signal type: **QAM digital cable
**Mythbuntu Version: **Mythbuntu 9.10 (64-bit)

[U][B]Performance
[/B][/U]I have never ever played with Linux before.  The closest I have come has been DOS back in the 80's and early 90's (when I was just a kid).  I read everything I could about setting things up for High Definition recording and HDMI audio output, tuner card setup, scanning for channels.  This box took me 2 weeks to get setup perfectly, and really it was working after 2 days, but it took me the extra time to figure out how to use the remote, how to do SSH and VNC to make editing easier.  The most painful part of setup (besides the remote) was getting the scanned channels to match SchedulesDirect (I did this all manually and it took me about 2.5 hours).  It is Wife-friendly (she's still a little scared of it, but she's getting it), and I am amazed everyday about what it can do and how I can customize it.

I only have a little bit of video hiccups when I am watching live HD content , I don't think it is that noticeable, and I may not have it optimized as well as I should (I'm pretty sure I have VDPAU configured correctly maybe I need to upgrade my memory to 2 GB).  Recorded HD content is perfect.  I get a jump error if I switch channels really fast.  I'm going to try to integrate Hulu tonight, and then I really can't think of anything else I want to do to get it set up.

Thank you to everyone who has put time into this project!

---

### Post by pnauta on 2010-02-01
> **port443 said:**
> _**Hardware**_
**Motherboard: **ZOTAC GF9300-D-E LGA 775 NVIDIA GeForce 9300 HDMI WiFi Mini ITX Intel Motherboard
** CPU: **Intel Pentium E5200 Wolfdale 2.5GHz LGA 775 65W Dual-Core Processor
**RAM: **2Gb (2x1Gb) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Desktop Memory Model KVR800D2N6/1G
**Video Card: **onboard (HDMI)
**Sound Card: **onboard (via HDMI)
**HD: **4Gb Sandisk Contour USB Flash Drive 
**Remote: **Mediagate GP-IR01BK Vista MCE Remote Control
**Tuners: **none
**Country: **Canada
**TV provider: **none
**TV signal type: **none
**Mythbuntu Version: **9.04

**Additional:** case (temporary) APEX MI-100; Pico-PSU 120; Cooljag fanless heatsink; single 120mm noiseblocker XL1 fan = no noise :)

[U][B]Performance
[/B][/U]One issue so far: big DVDRip (or BlurayRip), 8.2Gb, ~15Mbit/sec, MKV plays with some hiccups.  Network or CPU seem not to be an issue.

You need to change your TV Playback profile, bet you have CPU-- or the like.  Had that last week.

---

### Post by blkmeth on 2010-02-02
[COLOR=Red]***[SIZE=4]NEW RIG[/SIZE]***[/COLOR]

**Motherboard:** Gigabyte GA-MA770-UD3
**Chassis:** Apevia X-Master
** CPU:** AMD Phenom II Black Edition X2 3.1 GHz
**RAM:** 2GB Patriot PC2-6400 800MHz
**Video Card:** Asus EN210 (GeForce 210) 512M via HDMI
**Sound Card:** Realtek ALC888 HD onboard Audio
**HD:** 40GB Seagate + 250GB WD
**Remote:** Hauppauge TV remote (came with tuner card)
**Tuners:** Hauppauge WinTV-HVR 1600 Model 1178
**Country: E.g. the Netherlands:** North America (USA)
**TV provider: E.g. canal digital:** Comcast Cable
**TV signal type: E.g. DVB-S (satellite):** ATSC cable and OTA Digital (digital frontend mostly drops and/or playback very glitchy)
**Mythbuntu Version:** Mythbuntu 9.04

_**Performance**_         

All hardware detected out-the-box.
System has intermittent hesitation during any form of playback and digital tuner drops frontend. Issue is under R and D. Could be a ram voltage issue.
Grfx card HDMI works wonderfully, no need for tweaking using generic nvidia drivers.

Will attempt to load 9.10 on this hardware and report findings at a later date.

> **blkmeth said:**
> _**Hardware**_ :D:D:D
**Motherboard:** Gigabyte S-Series GA-G41M-ES2H
**Chassis:** Chenbro PC405
** CPU:** Intel 930 Pentium D Dual Core 3 GHz 800Mhz FSB
**RAM:** 2GB Patriot PC2-6400 800MHz
**Video Card:** onboard video via m/b HDMI port
**Sound Card:** Realtec ALC888 HD onboard Audio
**HD:** Seagate 200GB (Single) 
**Remote:** Hauppauge TV remote (came with tuner card)
**Tuners:** Hauppauge WinTV-HVR 1600 Model 1178
**Country: E.g. the Netherlands:** North America (USA)
**TV provider: E.g. canal digital:** Comcast Cable
**TV signal type: E.g. DVB-S (satellite):** ATSC cable only (digital frontend hangs and drops)
**Mythbuntu Version:** Mythbuntu 9.04

_**Performance**_         

All hardware detected and fuctional except for digital tuner due to ivtv driver issues. Have to manually install mfg version audio HD driver ( Realtek ALC888 ) to get alsa sound mixer to work with onboard audio. Video card HDMI out does work in low graphics mode.

---

### Post by cedyathome on 2010-02-11
_**Hardware**_
[B]Motherboard: ASUS M3N78-VM
CPU_:_ AMD Athlon 64 X2 5200 Brisbane 2.7GHz.[/B][]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103210")**RAM:** Crucial 2 x 1GB
**Video Card:  **On board nVidia 8200
**Sound Card: on board**
**HD: WD Caviar Green 1TB** 
**Remote: (not yet implemented) Streamzap ordered**
**Tuners: Hauppague WinTV-HVR-2250**
**Country: USA**
**TV provider: Comcast**
**TV signal type:  Digital QAM/256**
**Mythbuntu Version: 9.10** w/auto updates.
**Enclosure :  Antec Minuet 350 Slim Mini Desktop case**

[U][B]Performance
[/B][/U]Overall good. Using VDPAU & find de-interlacing on non-HD channels is not as good as I would like. A few unresolved issues remain like I cannot use mythtv to control volume. Need to manually boost AMD processor speed to 2.4GHz to get vdpau to work. I like the case. Quiet and small.

---

### Post by JohnReid on 2010-02-18
_**Hardware**_
**Motherboard: **Intel TOM COVE DH55TC
** CPU:** intel Core i3 530
**RAM:** Crucial 4GB
**Video Card: **Integrated
**Sound Card: **Integrated
**HD: **Western Digital 1.5TB Hard Drive SATAII 5400rpm 
**Remote:** none yet
**Tuners: **Hauppage 2200
**Country: **UK
**TV provider: **Freeview
**TV signal type: **DVB-T
**Mythbuntu Version: **9.10

Mythbuntu seems to work fine. Still trying to iron out problems with EIT. Card required setting modprobe options card=4. Some screen flickering and screen does not always update until mouse moved or a key is pressed. Will raise separate threads for these problems ([http://ubuntuforums.org/showthread.php?t=1410407](http://ubuntuforums.org/showthread.php?t=1410407)).

---

### Post by myth01 on 2010-02-18
**Hardware**
**Motherboard:** Asus something or other (in purchased PC)
**CPU:** Intel Core 2 Duo 6300 (1.86GHz)
**RAM:** 2GB
**Video Card:** MSI nVidia 9400GT
**Sound Card:** Integrated
**HD:** Samsung Spinpoint F1 1TB, Seagate 320GB
**Remote:** Windows (ergh) MCEUSB
**Tuners:** 2x Hauppauge WinTV NOVA DVB-S2
**Country:** UK
**TV provider:** Freesat
**TV signal type:** DVB-S/2
**Ubuntu 9.10 with MythTV 0.22-fixes**

A few kinks at the start, but test rig is now mostly up and running.

Graphics:
All the graphics tweaks (disabling composite, "UseEvents", "TripleBuffer" etc) made the world of difference.  VDPAU Normal playback profile has the playback at about 90% of what I think it should be, even BBC HD is almost flawless.  Will likely be putting nVidia GT220 in production setup.
HDMI worked out of the box.

Sound:
Using digital out until I can figure out which pins on motherboard SPDIF should be connected to the graphics card for HDMI audio.  Works perfectly although had to create .asoundrc to specify iec958 as default as the one of the tuners was being listed as the only device for sound.

Tuners:
Worked pretty much out of the box although had to download and copy firmware to /lib/firmware

CPU:
Top reports no more than about 10% even during HD playback.  (I don't compress/transcode anything).

For a test setup I'm pretty happy, looking forward to deploying the final thing!

---

### Post by blkmeth on 2010-03-02
[COLOR=Red]***[SIZE=4]NEW RIG [/SIZE]***[/COLOR][COLOR=Red]**Back to Intel**[/COLOR]
**Motherboard:** \\:D/\\:D/**Gigabyte GA-P43-ES3G**\\:D/\\:D/
**Chassis:** Apevia X-Master
** CPU:** Intel Pentium D 930 3.0 GHz
**RAM:** 2x1GB Patriot PC2-6400 800MHz
**Video Card:** Asus EN210 (GeForce 210) 512M via HDMI
**Sound Card:** Realtek ALC888 HD onboard Audio
**HD:** 40GB Seagate + 500GB WD
**Remote:** Hauppauge TV remote (came with tuner card)
**Tuners:** 2 x Hauppauge WinTV-HVR 1600 Model 1178
**Country: E.g. the Netherlands:** North America (USA)
**TV provider: E.g. canal digital:** Comcast Cable
**TV signal type: E.g. DVB-S (satellite):** 2 x NTSC cable and ATSC cable
**Mythbuntu Version:** Mythbuntu 9.04

_**Performance**_         

*** RECOMMEND any Intel Based Board w/out onboard video supporting Realtek audio chipset ***

All hardware detected out-the-box.
System is running very stable during any form of playback with no noticeable hesitation.
Grfx card HDMI works wonderfully, no need for tweaking using generic nvidia drivers.

TODO: Test Digital tunners


[/QUOTE]
> **blkmeth said:**
> 

**Motherboard:** Gigabyte GA-MA770-UD3
**Chassis:** Apevia X-Master
** CPU:** AMD Phenom II Black Edition X2 3.1 GHz
**RAM:** 2GB Patriot PC2-6400 800MHz
**Video Card:** Asus EN210 (GeForce 210) 512M via HDMI
**Sound Card:** Realtek ALC888 HD onboard Audio
**HD:** 40GB Seagate + 250GB WD
**Remote:** Hauppauge TV remote (came with tuner card)
**Tuners:** Hauppauge WinTV-HVR 1600 Model 1178
**Country: E.g. the Netherlands:** North America (USA)
**TV provider: E.g. canal digital:** Comcast Cable
**TV signal type: E.g. DVB-S (satellite):** ATSC cable and OTA Digital (digital frontend mostly drops and/or playback very glitchy)
**Mythbuntu Version:** Mythbuntu 9.04

_**Performance**_         

All hardware detected out-the-box.
System has intermittent hesitation during any form of playback and digital tuner drops frontend. Issue is under R and D. Could be a ram voltage issue.
Grfx card HDMI works wonderfully, no need for tweaking using generic nvidia drivers.

Will attempt to load 9.10 on this hardware and report findings at a later date.

---

### Post by Trinity33 on 2010-03-14
hi,

_**Hardware**_       MSI GT725
[B]Motherboard: dont really know 
CPU:[/B]              q9000 2Ghhz quad core
**RAM:**             ddr2 4gb                                     UBUNTU 9.10X86X32 SEE 3GB OF MY RAM AFTER CHANGING TO KERNEL 2.6.31.14 OR 31.20 PAE MOUSSE CURSOR DISAPPEAR 
**Video Card:   **Ati HD 4850 500mb             PROBLEMS IN 9.10 AFTER SYSTEM UPDATE UPGRADE 
**Sound Card:**  intel acl1200 + Ati hd48x0 HDMI ATI HDMI NOT SUPPORTED SO I USE INTEL SOUND CARD
**HD:**                500 Gb
**Remote:**
**Tuners:**         Hauppauge Nova-s usb2  NOT SUPPORTED

_**Performance**_

ubuntu 9.10 as long as u dont upgrade anything after fresh OS installation everything is working fine Cpu usage around 1 to max 5%. after system upgrade update the cpu usage is around 50% the same problem i experienced trying to use lucid lynx. dont know why maybe Xorg it doesnt matter. after kernel upgrade currently i use 2.6.31.14 mousse cursor disappear.  Hauppauge Nova-s usb2 in not supported. shame cos thats the reason i need every time i want to watch tv boot up windows:(.

---

### Post by russell5 on 2010-03-14
Hardware
Motherboard:asrocks 4coredual-vsta
CPU:pentium d
RAM:1gb ddr
Video Card: geforce fx 5200
Sound Card: onboard
HD:segeate 400gb sata
Remote: rosewill usb
Tuners: 2x pvr 150s
Country: USA
TV provider: comcast:
TV signal type: coaxial cable ?:
Mythbuntu Version: 9.10

Performance
Setting up the remote was a pain. Had to edit lirc source files but had found great guide.

Some reason i cant get it to sleep/resume. I think its something to do with the remote receiver because when its unplugged it works.  Still working on.

---

### Post by trevmar on 2010-03-15
.
Tiny ACER Revo AR1600-U910H refurbished ($159)with ATOM 230 CPU
1GB Ram (64M for Nividia Ion), 160GB 5400 RPM drive
HDHomeRun twin QAM tuner
Hanns 32inch 1920x1080p television, HDMI connection to Revo
Front and Back ends configured with Mythbuntu 9.10

Enough CPU / Peripheral power to watch live 1920x1080 TV and record two live 1920x1080 channels in the background (as long as two of the three sources are on the same transponder)

Problems with setup? Extreme frustration trying to understand what the menus were asking for. Didn't reach for the Manuals and FAQs until I was just about to give up. A typical geek problem..
.
.

Thanks to the Mythbuntu team...

---

### Post by joejoe148 on 2010-03-31
Hardware
Motherboard: asus a7n8x
CPU:amd athlon xp 3000+
RAM: 2048 MB PC2700
Video Card: Geforce 6200le 512 MB DDR2
Sound Card: onboard
HD: WD1200
Remote: came with tuner
Tuners:HVR-1600 hauppage
Country: US
TV provider:broadcast
TV signal type: broadcast
Mythbuntu Version: 9.04

Performance
After much thrashing I mangaged to resolve the conflict between the tuner and the video card but I was never able to get gnome to install or flash to operate. MythTV appears to be operating fine and record and playback are functional in 720p. I wanted to use this as a desktop/frontend/backend but I must need an ideal set of hardware or more linux chi.  I will try again loading ubuntu first(instead of mythbuntu first), then myth and see where I get.

Loading ubuntu first and then putting myth-desktop after seemed to work.  I have myth, gnome, flash and all seem to be coexisting at the moment.

---

### Post by Trinity33 on 2010-04-01
_**Hardware**_
 [B]Motherboard: American megatrend 
CPU:[/B] q9000 2ghz quad core 
 **RAM:** ddr2 4gb
 **Video Card: ati hd4850**
 **Sound Card: intel acl 1200+ati hd48x0 hdmi**
 **HD: 500** gb
 **Remote:**
 **Tuners:**hauppauge nova-s usb2 model 47000 
 **Country: UK**
 **TV provider: E.g. canal digital:** sky digital
 **TV signal type: E.g. DVB-S (satellite):** dvb-s
 **Mythbuntu Version: E.g. 8.10**
 
 _**Performance**_

i tested alpha 2 then alpha3 and last test i did with beta1. TV card is not supported my laptop is MSI gt725 and the lucid doesnt work on it. first time i booted i tried to update everything from synaptic but i got bus error so i needed to reinstall lucid. after fresh instalation synaptic was working fine but i got high cpu usage i tried ati catalyst 10.2 then 10.3 didnt worked out maybe cos catalyst still doesnt support xorg 7.5. i tried open source driver i intsalled it but i still had high cpu usage im talkin about around 30 to 50%. i tried to upgrade or disable different things but it didnt helped much sometimes xorg cpu usage went to 20% from nothing then udevd used 30% of cpu from nothing then other application normally in karmic the cpu usage is around 2%. so thats all lucid still doesnt work on msi gt725 or advent gx7555 or advent gx8555.

---

### Post by pbawesome on 2010-04-06
_**Hardware**_
**CPU:** core 2 duo @ 2.2 Ghz
**RAM:** 2.0 gb ram
**Video Card: **ATI Radeon HD 3850, 512mb
**HD:** 250 gb hard drive
**Tuners:**
ATI TV Wonder 600 USB (DOESNT WORK)

[U][B]Performance
[/B][/U]installed proprietary drivers for video card, installed firwmare and everything for tuner, and NOTHING showed up
****

---

### Post by Nausser on 2010-04-07
_**Hardware**_
**Motherboard:** ASUS P5Q PRO TURBO 775 RT 
**CPU:** INTEL|C2Q Q9550 2.83 775 12M
**RAM:** 2Gx2|OCZ OCZ2RPR10664GK
**Video Card:** EVGA|512-P3-N987-TR 9800GT
**Sound Card:** Onboard
**HD:** 160G Seagate for OS/Music 1.5T Seagate for TV/Movies
**Remote:** Logitech Harmony 700
**IR Receiver:** Microsoft MCE Receiver/Blaster
**Tuners:** HAUPPAUGE|1101WB and Firewire Capture via Comcast Cisco RNG-150HD 
**Country:** US
**TV provider:** E.g. canal digital: Comcast
**TV signal type:** E.g. DVB-S (satellite): us-cable
**Mythbuntu Version:** 9.10

**_Install/Performance_**

Install went rather well. The backend setup was a little confusing on the digital side of the installed tuner. I installed only one tuner at a time. It didn't like me multitasking with this. I installed the cable box first.
After the restart, I had to go into recovery mode and install the nvidia drivers via **apt-get install envyng-core** and then **envyng -t** even though I selected proprietary nvidia drivers in the initial setup. After that I would then boot back to recovery mode to get to the command line to edit the grub boot to keep it from going to low graphics mode or a blank screen during bootup. To do this I would edit the **/boot/grub/grub.cfg** file. There I would add **vmalloc=256MB** after the word splash. This file has to be re edited each time a major update is applied to restart.
The last thing I would have to do from the command line before starting the full blown OS is to make sure mysql would start before mythbackend. This was done by editing **/etc/init/mythtv-backend.conf** and adding
[B]pre-start script
   /etc/init.d/mysql start
end script[/B]

From there I finished installing my tuners one at a time.
I then opened the control centre and installed all the extras such as mythweb etc with password support enabled. Everything worked like a charm. Not a single glitch with HD recording/playback. I've done PIP with two HD sources and recording another HD program simultaneously. Couldn't ask for more television freedom! My last feature I enabled was the streaming capabilities via flash. I haven't tested it over the internet yet but it works flawlessly over my LAN on a wireless G laptop. It even works with shows I've cut the commercials out of and transcoded. Those are all the details I can think of. If you have any additional questions, feel free to ask!

---

### Post by movieman on 2010-04-09
_**Hardware**_
**CPU:** Atom-330
**Motherboard:** Zotac Ionitx F-E
**RAM:** 4GB DDR2 (only sees about 3.3GB)
**Video Card: ** Ion
**HD:** Intel X25-V SSD
**Tuners:** Frontend only.

_**Performance**_

Everything basically works, I have video and audio out over HDMI and it plays HD files fine with GPU acceleration. However, I'm running xbmc rather than MythTV frontend because I've had so many problems with the Myth frontend recently and xbmc seems far more reliable; that said, it does reliably crash if I configure it to generate thumbnail files.

Boots in 15-20 seconds, I was hoping it would be a bit faster than that with the SSD, but it still boots faster than my Blu-Ray player.

---

### Post by joarctic on 2010-04-12
Aopen i855 GME Mobo
750Mb RAM
1.6Ghz Pentium M
Hauppauge Nova TD-500 with Hauppauge remote
750Gb WD Green HDD
NVIDIA 6200 AGP 64Mb
No DVD player after install
cheap steel case drilled with holes & sprayed black
good airflow means temp controlled fans never spin up so totally silent
Mythbuntu 10.04
UK Freeview
MP3 converter plugin to transcode radio shows to MP3 from here;
    [http://ubuntuforums.org/showpost.php?p=8345112&postcount=636](http://ubuntuforums.org/showpost.php?p=8345112&postcount=636)


Issues with regular system freezes (in 9.0.4) finally fixed by only having 1 tuner scan for channel info & messing around with the timeouts. 

Recent upgrade to 10.0.4 totally painless apart from volume muting every time I rebooted. Removed any line with the word "mute" in it from the alsa-utils file in etc/init.d & seems to have worked. Also though I'd locked the remote to event 6 the upgrade threw that out too so had to redo hardware.conf to make it work. Oh and I still can't make it boot straight to Myth Frontend but since I only reboot rarely this is no big deal. 
For the upgrade I basically just allowed the system to update itself, first Ubuntu then Myth. Took ages but all worked seamlessly. CPU useage also went down substantially with Xorg dropping from 30% under 9.0.4 to around 1% (at idle).

---

### Post by c1ru on 2010-04-20
Sveon STV22
Dont work, only get Afatech from lsusb.
Its a dvb-t dual and supports HDChannels.
Usb pen.

---

### Post by mechanizedmedic on 2010-04-20
_**Hardware**_
**Motherboard: **Biostar A770E3 v6.0
**CPU:** AMD Athlon II X3 435 2.9GHz (OC'd to 3.2)
**RAM:** Patriot DDR3 1333MHz
**Video Card: **BFG GeForce 210 1GB
**Storage: **Patriot PS-100 32GB SSD
**Add-ons: **Sony 3.5" Multi-Card Reader w/ USB Port
Airlink PCI Wireless Card
**OS:** Ubuntu 9.10
 
 
_**Performance**_
Very fast system for under 300 bucks! The SSD made all the difference in performance. I have yet to update the BIOS to unlock the fourth core. The only problems so far have been from user error. ](*,)

---

### Post by rramesh on 2010-04-23
Hardware
--------------
HDHomerun OTA
Biostart TForce6100 + Athlon 64 2G (socket 939)
2G RAM + 1TB WD black HD
9400 GT with VDPAU normal
Sound from MB audio
Vista remote (mce_usb2  - I think) from newegg.

Works mostly. Occasional stutter with HD recordings. Could because I have OS+DB+Myth
on one disk.

---

### Post by Ryazanov on 2010-05-01
_**Hardware**_
[B]Laptop: HP6735s
CPU:[/B] AMD Turion x2 64
**RAM:** 3GB
**Video Card: **Ati Radeon HD3200
**HD:**  320 GB
[B]Tuners:
-Acorp DS120: Works perfectly
-LightWave LW-EXPTVAV: Does not work at all. Searched internet: nothing usable
[/B]

---

### Post by dewmanstl on 2010-05-03
_**Hardware**_
**Motherboard: **Dell PowerEdge SC420
** CPU:** Pentium 4 3.00GHz
**RAM:** 4x1g DDR Synchronous 533 MHz 
**Video Card: **IntelE7221 Integrated Graphics Controller
**Sound Card:**  Ensoniq ES1370 
**HD:**  /40GB-OS/ 160GB-Live TV-Mythgame/ /250GB-Music/ /1TB-Recordings/
**Remote:** Xbox DVD IRKit  [http://nikosapi.org/wiki/index.php/Xbox_DVD_Playback_Kit_Pinout](http://nikosapi.org/wiki/index.php/Xbox_DVD_Playback_Kit_Pinout)
**Tuners:** Pinnacle PCTV HD_Card (800i)
**Country: E.g. the Netherlands:** USA
**TV provider: E.g. canal digital:** TVC 
**TV signal type: E.g. DVB-S (satellite):** ATSC / NTSC
**Mythbuntu Version: **Mythbuntu 9.10 .23 Trunk

[U][B]Performance
[/B][/U]Overall performance is pretty good. Some slight stuttering with HD playback but waf is pretty high. Remote was hardest part of entire project due to soldering of wires to IR receiver. Minor glitches here and there, but I blame those on me.

---

### Post by russell5 on 2010-05-09
Hardware
Motherboard: ASrocks 4CoreDual-VSTA
CPU: Pentium D 2.8 GHZ
RAM: 2x1GB DDR2 
Video Card: Gefore fx 5200 128MB
Sound Card: Built in 
HD: 400 sata  1tb sata
Remote: Rosewill rrc-127 pain to get working but found awesome guide
Tuners: 2x pvr 150
Country: USA
TV provider: Comcast
TV signal type: NTSC
Mythbuntu Version: Mythbuntu 10.04 .23 Trunk

Performance
Pretty good boot up is much faster with 10.04. No complaints about system. Haven't seen a slowdown yet. Even when recording two programs and watching a movie.

---

### Post by juanfernandes on 2010-06-10
**Hardware**: Acer Aspire Revo R3610

**CPU:** Intel Atom 330
**RAM:** 4GB DDR2 800MHz
**Video Card: **NVIDIA Ion Chipset
**Sound Card: **Onboard
**HD: **500GB SATA
**Remote:** Wireless keyboard
**Tuners:** None
**Country:** United Kingdom
**Mythbuntu Version:** 10.4

**Performance**:
Very good. Had few issues to start off with, no dvd playback, no sound, no video playback, videos not showing up in library, shutdown or restart didnt work from mythtv menu, couldnt not bind F keys from my multimedia keyboard. 

After I fixed all the above issues, the system was working perfectly. Sound output was via HDMI.

---

### Post by rulet on 2010-06-12
> **juanfernandes said:**
> **Hardware**: Acer Aspire Revo R3610

**CPU:** Intel Atom 330
**RAM:** 4GB DDR2 800MHz
**Video Card: **NVIDIA Ion Chipset
**Sound Card: **Onboard
**HD: **500GB SATA
**Remote:** Wireless keyboard
**Tuners:** None
**Country:** United Kingdom
**Mythbuntu Version:** 10.4

**Performance**:
Very good. Had few issues to start off with, no dvd playback, no sound, no video playback, videos not showing up in library, shutdown or restart didnt work from mythtv menu, couldnt not bind F keys from my multimedia keyboard. 

After I fixed all the above issues, the system was working perfectly. Sound output was via HDMI.

 And how did you do that, can you describe?

---

### Post by tomaton on 2010-06-15
_**Hardware**_
**Motherboard: **ZOTAC IONITX-A-E
** CPU:** Intel ATOM 330
**RAM:** 2 GB RAM DDR
**Video Card: **NVIDIA ION
**HD: **SAMSUNG 2.5" Spinpoint M7 HM500JI 500GB, SATA 
**Tuners: **
USB LifeView LV52T (doesn't work, no drivers for Linux)
USB Aver TV Hybrid Volar HX Windows 7 Starter Kit (works, driver from vendor's web)
 **Remote: **USB tuners contains IR receivers which doesn't work
**Country: **Czech Republic
**TV signal type: **DVB-T, FM radio (not checked), Analog TV (not checked)
**Mythbuntu Version: **10.04

_**Performance**_
Almost all hardware properly detected. Need to select NVIDIA proprietary driver during install. Then need to install Linux driver for Aver TV Hybrid Volar HX from [http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=293&tab=APDriver](http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=293&tab=APDriver)
Remote receivers in USB DVB-T cards seems not be detected. I connected HTPC to FullHD TV via HDMI, for audio over hdmi I needed to manually execute [FONT=Courier New]alsamixer [/FONT] and unmute the third SPDIF labeled as **SPDIF 1**. In the mythtv-frontend selected  [FONT=Courier New]Setup -> General -> Audio System -> Audio Output device[/FONT] **alsa:hdmi**.[FONT=Courier New]
[/FONT]To view HD channels, it needs to select[COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000] [/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR] **VDPAU Slim **[COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000][COLOR=#ffffff][COLOR=#000000]in Setup->TV  Settings->Playback 3/8 -> [/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]Current Video Playback Profile. The other options VDPAU Normal and VDPAU High Quality produce choppy video playback. I also disabled the MPEG signal noise reduction on my TV, which also produced a little choppy video playback.
Didn't checked yet FM Radio as it needs quite more effort to configure/set/integrate into mythtv frontend.

---

### Post by Slate8 on 2010-06-15
**Hardware**
**Motherboard:** Acer Aspire Revo R3610
**CPU:** Intel Atom N330 (Dual Core)
**RAM:** 2GB
**Video Card:** NVIDIA GeForce 9400 (NVIDIA Ion)
**Sound Card:** Onboard
**HD:** 250GB SATA
**Remote:** Microsoft MCE Remote Model 1039 with IR sensor
**Tuners:** Hauppauge WinTV-NOVA-T USB
**Country:** United Kingdom
**TV signal type:** Freeview DVB-T
**Mythbuntu Version:** 10.04

**Performance**
Very good, all hardware detected and working out the box. Selected nVidia proprietary driver during install. Had to enable HDMI audio via the alsa mixer. Experienced tearing of video until I set the "Composite" "Disabled" option in xorg.conf. Otherwise fantastic bit of kit. UI is fast with the Arclight theme. VDPAU working out the box and plays high bitrate 1080p without issue. An ideal quiet, low power, small Mythbuntu box!

---

### Post by percula on 2010-07-16
Well after living 4+ years my old Myth box finally, slowly gave up the ghost and it was time to build a new MBE/FE box.

**The Build**
Mythbuntu 10.04 LTS
Asus M4A77D
Athlon X2 245 (2.9Ghz)
2GB of RAM
500G WD HDD
Zotac GeForce GT 240 (fanless model!)
PVR-150 with remote
PVR-500
SA4250HDC STB connected via firewall
Generic CDROM drive
Intel 10/100/1000 NIC

**The network/design**

I have a SAN built on a 1Gbps jumbo frame network. This is where I store my movies and other media content. The second (Intel) NIC in this build is dedicated for the SAN network. I use NFS to mount the SAN to provide Myth with a videos, etc directory structure.

The MBE/FE serves only myself at this point, even thought it maybe expanded in the future.

**Issues **

The first issue I was confronted with was the built-in sound card the MB. I connected my 5.1 surround speaker system and expected to have fiddle with things to get more than 2 channels, nope, no sound what so ever. After much searching/researching I found out that the version of ALSA that ships with the Mythbuntu 10.04 ISO does not correctly identify the sound system.

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810) This thread worked well, but I had to run the process twice as I had a package manager open, and there was no warning that these scripts need to have package manager access and report no errors if they are blocked from exclusive access... Oh well.

I am still not 100% on sound. I am not getting enough volume out the setup despite having everything cranked to the max. Something I need to dig into a bit more. The system is workable but fails if I get a media source with low volume to begin with.

The next issue is my SA4250HDC... I have it hooked up, setup, changing channels, everything except being able to fully lock up and get video to record. This likely has more to do with Cox in PHX than anything I can do... Oh well, HDPVR in the future anyway, no worries.

**Summary/thoughts**

I am a died in the wool CentOS user, converted our entire company to CentOS (8 locations worldwide, 2500+ employees, hundreds of servers). I am big fanboy. However in the desktop world, especially for a HTPC Ubuntu rules!

It was great timing that the old hardware decided to die when there was a fresh LTS version out! The old hardware had me really down on Mythbuntu, but that was all hardware related and nothing to do with Mythbuntu, despite the looks of the situation at the time. Now with fresh working hardware, things are working every well.

Some of the things I seen during the death of the old hardware...

[LIST]
[*]PVR-150 remote just stopped working. Nothing wrong, just slowly went from working to barely registering key presses to nothing. I went out and got a MCE remote, and it too had some serious lag, sluggishness issues.

[*]Xorg was eating 100% of the CPU.

[*]Recording was hit and miss on the 150 and 500 inputs.
[/LIST]

Overall I am very happy with the build and Mythbuntu.

---

### Post by drivingdynamics on 2010-07-18
_**Hardware**_
**Motherboard: **Asrock M3A785GXH/128[B]
CPU:[/B] AMD Athlon 5050e 2x2,8 Ghz
**RAM:** 4GB Geil
**Video Card: **Gainward NVIDIA 9500 GT (fanless)
**Sound Card:** Internal ATI
**HD:**  Samsung 1TB 
**case:** Antec Fusion remote max (antec versis) with LCD and remote.
**Remote:** Antec-Version RM200 
**Tuners:** Technisat SkyStar 2
**Country: Germany**
**Wireless network:** TP-Link TL-WN350G
**TV signal type: DVB-S**
**Mythbuntu Version: 10.04** , 9.10

[U][B]Performance
[/B][/U]
Internal Graphic (ATI 4200) card was too slow, performance with NVIDIA 9500GT is much better, picture with VDPAU is very good.
Sound over HDMI works with internal connection from
mainboard SPdif --> graphiccard.

I had a lot of problem with system freezes (prebuffering pauses and write audio errors) caused by the wireless network card. I had to deactivate the network card.ACPI wakeup doesn't work with this mainboad from standby,
only from suspend mode.

---

### Post by linuxyogi on 2010-07-23
HP Scanner --- Scanjet 2400

             &

Lexmark X75 Printer

Simply not supported.:-x

---

### Post by Drenriza on 2010-07-23
_**Hardware**_
**CPU:** Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz
**RAM:** 4.0 gb ram
**Video Card: **nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
**Wireless network: **Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express
**HD:** 190 gb hard drive
**Tuners:**
**Country:** Denmark
**Ubuntu:** 10.04
**Sound** Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
**Laptop** Zepto Znote 6224W (no longer produced)

[U][B]Performance
[/B][/U]All hardware properly detected and functional.
0 problems

---

### Post by mycatsnameisbernie on 2010-07-25
_**Hardware**_
**Motherboard: **Intel DG43GT uATX
**Case: **In-Win IW-BK623 plus Scythe SY124010L 40mm Chipset Fan for very hot ICH10 Southbridge chip
**CPU:** Intel Wolfdale E6300 2.8 GHz 1066FSB
**RAM:** Kingston KVR800D2N6K2/2G (2 x 1GB)
**Video Card: **None, using motherboard's integrated G43/X4500 graphics
**Sound: **Onboard ICH10 Intel HD Audio via on-board optical S/PDIF.
**Wireless adapter:** Rosewill RNX-G1W USB
**HD:** Western Digital AV-GP WD5000AVDS 500GB
**Tuners: **Hauppauge HVR-1600 model 1199 w/IR receiver/blaster/remote, plus Hauppauge HVR-1250 model 1187
**TV inputs**: 2 x clear QAM-256 from Comcast cable plus analog input from Motorola DHC70 cable box controlled by the Hauppauge IR blaster.
**TV:** Panasonic 50" Viera Plasma circa 2008, connected via HDMI
**Country:** US
**Ubuntu:** 10.04
 
_**Performance**_
This is a combined FE/BE.
 
The biggest challenge was getting the HVR-1600 IR receiver and blaster to work on Ubuntu 10.04. You can find my recepie to make both the IR receiver and blaster work here:
[http://ubuntuforums.org/showpost.php?p=9548142&postcount=9](http://ubuntuforums.org/showpost.php?p=9548142&postcount=9)
 
I had to force each DVB input (on the HVR 1600 and 1250) to work separately (by removing the other from input connections) before MythTV would switch between them automatically.
 
The next problem was running out of kernel memory when using all 3 tuners at the same time. This was fixed as described here: [http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small](http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small). The default vmalloc set during the Lucid install was 128MB. I added the boot option vmalloc=512MB, which is way more than I will ever need, but with 2GB total RAM there is plenty of room for the extra kernel memory.
 
The next problem was lots of prebuffering pauses. I solved these by changing the TV Playback profile from CPU+ (the initial default set during Mythbuntu installation) to CPU++. I think the prebuffering pauses were caused by XvMC failing to work on my G43 graphics at 1080P and falling back to libmpeg2. With CPU++ it uses ffmpeg which looks and performs great. CPU usage is about 30% when recording 3 simultaneous MPEG streams plus playing back a 1080i recording with deinterlacing to 1080P TV.
 
I had minor problems with audio via HDMI. Outputs of ALSA:default and ALSA:hdmi did not work (no audio). Using ALSA: plughw:0,3 which is my HDMI audio card/device, worked fine. Later I changed to S/PDIF optical output, which works fine for 5.1 audio using ALSA:iec958.
 
Then I was getting lots of WriteAudio buffer underruns. I solved these by unchecking "Use Internal Volume Controls" in front end setup General/Audio Mixer (I couldn't get the mixer to work with HDMI audio in any case). Controlling volume with my TV or stereo is fine.
 
I have one remaining problem:
 
I am unable to get frontend setup Appearance/Screen Settings x/y offset and "use GUI size for playback" (unchecked) to work to correct my TV's overscan. I need to do more research on this issue.
 
**_Other thoughts:_**
I originally was planning to get an Atom 330/ION board. Then Comcast started encrypting most basic cable channels, so I needed a 2nd PCI slot for an analog card to hook up to my cable box (I was afraid to try an analog USB TV Tuner). I realized I could get a cheap uATX board with 4 expansion slots, plus a more powerful CPU, for less money than an Atom/ION board. I think this was a good decision. MythTV deinterlacing runs great using about 30% of CPU. The biggest CPU hog I could find was Adobe Flash playback of 1080P full-screen, which uses about 60% of CPU. 
 
I knew I was taking a chance with the Intel onboard graphics, but it is working fine for me except for the overscan issue mentioned above. I can always add an Nvidia graphics card that supports VDPAU if I ever feel the need for it.
 
The main advantage of an Atom-based system would be less power and heat. My system draws about 48 watts when idle, and 78 watts when in use, as measured with a Kill-A-Watt.

---

### Post by linuxilis on 2010-08-04
**_Hardware_**
**HTPC: [ASRock ION330HT-BD HTPC]("http://www.ocinside.de/html/results/asrock_ion330ht_blu_ray.html") :popcorn:**
**Motherboard: **ASRock AMCP7AION-HT
**CPU:** Intel ATOM 330 Dual Core
**RAM:** 2 GB RAM DDR
**Video Card: **NVIDIA ION
**HD: **Seagate Momentus 320GB 
**Remote: **[USB Ultra infrared receiver v2.0]("http://www.ocinside.de/html/modding/usb_ultra_ir_receiver/usb_ultra_ir_receiver.html")
**Mythbuntu Version: **10.04 LTS 64 Bit
 
_**Performance**_
good, also with HD content.
Installed with [**[SIZE=2]this[/SIZE]**]("http://www.ocinside.de/html/modding/linux_ir_anleitung_d.html") German LIRC guide.

---

### Post by jms-ubuntu-en on 2010-08-08
[SIZE="5"]**Backend server**[/SIZE]
**_Hardware_**
**Motherboard:** Asus M3N78-VM
**CPU:** AMD Phenom(tm) II X4 920 Processor
**RAM:** 4GB
**Video Card: ** nVidia Geforce 8200 (integrated)
**Sound Card:** nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (integrated)
**HD system:** Seagate Barracuda 500GB (ST3500320AS) 
**HD storage:** Seagate Barracuda 1TB (ST31000340AS)
**Remote:**
**Tuners:** 2 x Terratec Cinergy 1200 (Philips Semiconductors SAA7146)
**Country: ** Finland
**TV provider: ** Elisa (free, non-free and HD content)
**TV signal type: ** DVB-C
**Mythbuntu Version: ** 10.04.1

_**Performance**_
Zero problems so far. I have subscribed also some non-free channels (crypted) so I have also a Phoenix card reader, an oscam cardserver and vdr-sasc-ng (release 551) as a software emulated CAM.

[SIZE="5"]**Frontend primary**[/SIZE]
**_Hardware_**
**Motherboard:** Zotac 330 ION mini-itx
**CPU:** Intel(R) Atom(TM) CPU  330   @ 1.60GHz
**RAM:** 2GB
**Video Card: ** nVidia Corporation ION VGA (integrated)
**Sound Card:** nVidia Corporation MCP79 High Definition Audio (integrated)
**HD:** Kingston 8GB usb stick
**Remote:** HTPC-Keyboard Ione Scorpius-P20
**Mythbuntu Version: ** 10.04.1

_**Performance**_
Reasonable performance in scope of video/audio output, also with HD material (both DVB-C broadcasts and blueray disks). All logging is disabled or minimized due to usage of usb stick as hard disk.

[SIZE="5"]**Frontend secondary**[/SIZE]
**_Hardware_**
**Motherboard:** Dell Precision M4300 (laptop)
**CPU:** Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz
**RAM:** 2GB
**Video Card: ** nVidia Corporation Quadro FX 360M
**Sound Card:** Intel Corporation 82801H (ICH8 Family) HD Audio Controller
**HD:** Seagate 120GB (ST9120823AS)
**Mythbuntu Version: ** 10.04.1

_**Performance**_
Problems with HD content when using wireless (11g), otherwise ok.

---

### Post by Addanc on 2010-09-07
Hardware
Motherboard: Gigabyte GA-H55M-S2H uATX
CPU: Intel Core i5-650
RAM: 4GB
Video Card: Core i5-650 GPU
Sound Card: Realtek ALC888B/892 (Motherboard)
HD: Western Digital 500GB SATA II 7200RPM 16MB cache.
DVD: Sony AD7241S 24x SATA.
Tuners: Hauppauge Nova-T-500 dual DVB tuner.
Enclosure: Antec NSK 1380 MATX cube case with 350W PSU.
Country: UK.
TV provider: Freeview digital terrestrial.
TV signal type: DVB-T.
Mythbuntu Version: 64bit 10.04

Mythbuntu installed without any problems; TV play and recording excellent. Very impressed with how quiet the set-up is.

The only problem encountered is DVD playback from within the Mythbuntu framework; DVD playback freezes on completion of the DVD opening title play-back (can escape out to Mythbuntu menus, so not a total lock-up); don't believe its the hardware since VLC and SMPlayer playback DVD OK; probably more a function of DVD navigation?

After testing with multiple DVD, the freeze-up appears to be a function on the DVD and not the hardware; as suggested previously probably the DVD navigation.

---

### Post by LowSky on 2010-09-07
**Hardware**
**Motherboard:** MSI 790GX-GD70
**Case:** Lancool K-62
**CPU:** AMD Phenom II 550 x2 (unlocked to 4 cores at 3.5 GHz)
**RAM:** G-Skill 2x2GB DDR3 1600
**Video Card:** Gigabyte Nvidia 460GTX
**Sound:** Onboard
**HD:** 4 different sized and branded hard drives, totaling 1.6TB of recordable space
**Tuners:** Hauppauge HVR-2250 w/ USB IR receiver/blaster/remote, Hauppauge HD PVR 1212 connected to SA4250HD cable box using Firewire to change channels.
**TV:** Vizio 37" 720p/1080i connected via VGA, Hanns-G 19" Monitor connected via DVI.
**Ubuntu:** 10.04, MythTV 0.23.1

**Performance**
System is a backend/frontend using a monitor and TV as separate X sessions. The Nvidia 460GTX handles this beautifully.
Moving the mouse between screens switches which X session is being used. Sound is still prioritized by MythTV frontend when it is being utilized. VDPAU really helps keep loads down as the machine is constantly multitasking.

Mythchanger was a great help in changing channels for my HD PVR without it I would need to use a blaster which seems like a messy solution to me.

Still working on analog support for the HVR-2250, digital works great and can record 4 shows at once as long as they share QAM frequencies. HD PVR isn't too bad recoding form cable box. sometimes it will not record due to errors of the cable box, or  mess up if someone changes the channel by hand.

One odd issue is Firefox locking up when running it and mythtv at the same time on separate X sessions... I'm guessing flash is the real culprit but I need to look into it further.

---

### Post by jskiller on 2010-09-07
Hardware
Dell Latitude E6510
CPU: Intel Core i5-540m
RAM: 4GB
Video Card: Core i5-540m GPU

Ubuntu 9.04 - video issues, screen freezes after gnome boots up.  Later, built kernel 2.6.35 and gnome still freezes.

Ubuntu 9.10, 10.04, 10.04TLS, 10.10 (beta) installation screen goes black.  Cannot install.

---

### Post by gvvsss on 2010-09-16
**_Hardware_**
Motherboard:ASUS M3N78-VM
CPU:AMD Phenom II X4 955
RAM:4 GB DDR2 800 MHz
Video Card: NVIDIA GeForce 8200 (Onboard)(512 MB Shared)
Sound Card:VT1708B Analog Audio (Onboard)

Installation went well, had to install NVIDIA proprietary drivers after installation for Desktop Effects, only NVIDIA HD Audio option showing up in alsamixer, and **_no sound through speakers_** and my **_analog sound device is not functioning._**.

Observed lately that although the analog devise is not shown up in audio mixer or alsamixer, it is actually working, only sound from rare audio ports is working and front audio is missing (I figured it very lately since I mostly use my front audio ports for playback). Could not still figure a way to work around this.

---

### Post by forkd on 2010-09-19
I am using a 
Mythbuntu 10.4
CPU Socket 775 C2D
motherboard Zotac GF9300
Onboard Sound
Onboard Nvidia Video with VDPAU 
Onboard NIC
Hard Drive WD EARS 2TB (advanced format so I formatted it in Windows 7 first so the partitions started on the right cylinders and then installed with "take over all partitions" option...worked fine)
Snapstream RF Remote
HD-PVR connected to a DirectTV box
Hauppauge 950Q for digital OTA signal
USB>Serial>USB assembly to control the DirectTV box

All worked well out of the box but I fleshed out my own lirc config files because I was unhappy with the default one...If anyone is interested I'd be happy to post my files.

---

### Post by JoaoRoberto on 2010-09-25
_**Hardware**_
**CPU:** atlhon 4200 x2
**RAM:** 1.0 gb ram
**Video Card: ati x1550 sapphire** 256/64
**HD:**80 gb hard drive


[U][B]Performance
[/B][/U]All hardware properly detected are functional, except my  LG GSA-H50N dvd rom...
Please, help me! im freakin' out...i need backup my pc to format
Help

_**Hardware**_
[B]Motherboard: m2n-x asus
[/B][B]ubuntu 10.04, updated today...
[/B]

---

### Post by lviperz on 2010-09-29
This is for the newbies and people that want to build a standard def system on old hardware. Like me.

I've been using mythtv on fedora since about 2003 or 2004. Think it was like version .17 or something. Ran it on fedora core 5. Then I merged to a better system with FC7 and mythtv .20.

Figured it was time to upgrade and found mythbuntu, wonderful and so damn simple to setup. Anyway, here is what I'm using for a simple sdtv system.

**System:** Dell Dimension 8300 with a P4 2.6 hyper-threading
**Ram:** 2.5 Gig pc2700
**Video:** nVidia MX series with 64 meg ram
**Hard Drive:** 80 Gig seagate for the os - mythbuntu 10.04
iOmega NAS for recording storage - 1TB
**Network:** Gigabit network
**Tuners:** Hauppauge pvr-150, pvr-250 and pvr-350

System connected to Samsung DLP via vga. This is a single backend/frontend system and all is working right out of the box. Once I configured my tuners correctly. Forgot to select ivtv for the type.

I have great video and did a test by recording 3 shows at once, set another old recording for commercial flagging and transcode, watched a recording and monitored the system with TOP. CPU averaged 15% wth an occasional spike to 30%. Everything was still using ram and never toughed swap. Playback of the recording remained steady and never any stutters.

When the three recording were finished, I viewed them and no stutter in them either. I doubt I will even try to do HD with this system, so my next project is to build a system just for hi-def stuff and use the old system as a master backend.

---

### Post by image_editor on 2010-10-18
Hi all,
My newly reserrected systems hardware includes:

P4P800S Asus Motherboard
P4 1.7Ghz Processsor
1.256 Gig Ram
160Gig Sata Hard DRive
Nvidea Geforce 128mb Video Card AGP
DNTV Live PCI Video Card
Mythbuntu 10.04
--

**PROBLEM**
------------
My problem is the computer (acting as a frontend and backend) keeps freezing.
When its up and running it plays back recordings beautifully but if i leave it alone for an hour or more and i come back it has crashed.


**ACTIONS SO FAR**
------------------
I have tried wiping the drive and installing mythbuntu 10.10 with no difference in effectiveness


What can i do , does anyone have any suggestions?

---

### Post by torrent99 on 2010-10-20
> **lviperz said:**
> This is for the newbies and people that want to build a standard def system on old hardware. Like me.
 
Intel P4 pah! When I wer lad, we used to sleep in paper box. and imagine eating potatoes...  ;-)
 
Anyway here's my SD system. 
**System:** Pentium 3 1Ghz on an Intel D815EEA MB
**Ram:** 512MB PC133
**Video:** nVidia FX5200 using XvMC+bob 2x connected via SCART RGB
**Hard Drive:** 40 Gig seagate for the os - ubuntu 10.04
2x 160GB IDE + 1x 500GB SATA for recordings
**Network:** 100Mb/s network
**Tuners:** Hauppauge pvr-150, 1x DVB-T on PCI, 1x DVB-T USB
 
 
System ran Myth 0.21 really well, could record up to 4 shows at once & playback at same time.
Running 0.23 it's not so good.. Myth backend has got a bit fat. Can still record 2x & playback 1x though...
 
 How low can you go?

---

### Post by darkdrow on 2010-10-21
_**Hardware**_
**CPU:**amd 64 athalon
**RAM:**4 gb ddr 2 800
**Video Card: **ati radeon 4650 hd ( HDMI conection )
**Country:canada**

OS works fine the only issue im having is getting the ati control center to work, i just get a error saying cant locate graphic drivers, or hardware. i need it tho cause im running a 42" LCD high def tv for a minitor and ubuntu thinks its a 46 so all my sides are cut off.

---

### Post by avacado on 2010-10-26
[B]

Hardware
CPU Intel Atom N450
RAM 2gb upgraded from 1 gb
multi card reader device number [/B]0cf2:6250 ENE Technology Does **NOT** work
[B] DESPITE BEING CANONICAL CERTIFIED HARDWARE
see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277)
Country Australia
[/B]

---

### Post by mr_luksom on 2010-11-21
Hardware - Backend
Motherboard: Gigabyte GA-M61-PM-S2
CPU: AMD Athlon 64 x2 3800+
RAM: 1GB
Video Card: None
Sound Card: None
HD: yes
Remote: None
Tuners: 2 x Haupaugge HVR-1100
Country: Australia
TV provider: Free to Air
TV signal type: DVB-T
Mythbuntu Version: 10.10

Performance
Perfect - no issues.

Hardware - Frontend
Motherboard: Laptop - Toshiba A80
CPU: Centrino M 1.6Ghz
RAM: 512MB
Video Card: None
Sound Card:??
HD: yes
Remote: Generic PS2 controller
Tuners:
Country: Australia
TV provider: Free to air
TV signal type: DVB-T
Mythbuntu Version: 10.10

Performance
Doesnt handle PIP very well.

---

### Post by Richard_T on 2010-11-21
GIGABYTE GA-MA770
AMD PHENOM 9650
RAM 4 GB DDR
ZOTAC 9800 1GB DDR3 
on board 5.1 sound.  
Hitachi 250 GB Drive
Maxtor 250 GB Drive 
segate 500 GB Drive

Microsoft Keyboard
Gigabyte Mouse.  GM - M6880
HYUNDAI 22" Blue H monitor.  

No Problems Installed like a charm.

Also
Asus A8N-SLI
AMD ATHLON 
2 GB RAM
250 GB DRIVE
XFX 8600gt 256 Mb

Failed to install the partition manager couldn't partition the drive (partition manager wouldn't give any options) I had suse 11.3 on but now have 7 on there.  

Country:  Cymru Great Britain

---

### Post by Xrcam on 2010-11-26
Xrcam setup.
 
[SIZE=3][FONT=Times New Roman]Four machines. One linux backend server, one linux frontend server and two windows frontend.[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
**[SIZE=3][FONT=Times New Roman]Backend server:[/FONT][/SIZE]**
_[SIZE=3][FONT=Times New Roman]**Hardware**[/FONT][/SIZE]_
[FONT=Times New Roman][SIZE=3]**Mobo :**                      Asus M2N-MX SE PLUS[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]**CPU :**                        Amd Athlon 64 X2 Dual Core Processor 5000+[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**RAM :**                      2 GB[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**Video Card :**             GeForce 6150E nforce 430 (on mobo)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**Sound Card :**            Nvidia corporation MCP61 High Definition Audio (Rev 22) (on mobo)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**Remote:                  ** None[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**HD :**                         Western Digital 2TB – WDC WD20EAR5-00[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**Tuners :**                   Hauppauge HD-PVR 1212[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**TV Box :**                  Scientific Atlanta 4250HD[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**TV Provider :**          Videotron[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**Country:**                  Canada[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
_[SIZE=3][FONT=Times New Roman]**Software**[/FONT][/SIZE]_
[SIZE=3][FONT=Times New Roman]**OS:**                           Mythbuntu 10.10[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**MythRelease:**         0.24[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**FireWire Channel Changer:**  /usr/bin/mythchanger[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
**[SIZE=3][FONT=Times New Roman]Frontend 1:[/FONT][/SIZE]**
_[SIZE=3][FONT=Times New Roman]**Hardware**[/FONT][/SIZE]_
[SIZE=3][FONT=Times New Roman]**Mobo : **                    Shuttle XS35gt[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**CPU :**                       Intel Atom 510 Dual core (Pineview-D)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**RAM :**                     2 GB DDR2[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**Video Card :**           Nvidia Ion 512MB DDR3, HDMI[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**Sound Card :**           Nvidia Ion[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**Remote control :**    Wireless Rii Mini PC Keyboard        [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**HD :**                        SSD 30GB OCZ – OCZSSD2, 1VTX30G RTL[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
_[SIZE=3][FONT=Times New Roman]**Software**[/FONT][/SIZE]_
[SIZE=3][FONT=Times New Roman]**OS:**                            Mythbuntu 10.10[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**MythRelease:**         0.24[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
**[SIZE=3][FONT=Times New Roman]Frontend 2 and 3:[/FONT][/SIZE]**
[SIZE=3][FONT=Times New Roman]Windows PC – Kids room (using Myth 0.24 compiled for Windows)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]So far everything works as expected. Got 4 problems :[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]1-[/SIZE]      [SIZE=3]No sound thru HDMI with Frontend 1. Fixed : Alsa-conf files  and MythFrontEnd audio settings.[/SIZE][/FONT]
[FONT=Times New Roman][/FONT][FONT=Times New Roman][SIZE=3]2-[/SIZE]      [SIZE=3]Streamzap (lirc) does not work with (10.10). Replaced Streamzap by Rii Mini PC Keyboard[/SIZE][/FONT]
[FONT=Times New Roman][/FONT][FONT=Times New Roman][SIZE=3]3-[/SIZE]      [SIZE=3]Did not succeeded using IR Blaster as a channel changer for the TV Box. I hooked my backend to the SA4250HD with a FireWire Link and used (Mythchanger) program instead.[/SIZE][/FONT]
[FONT=Times New Roman][/FONT][FONT=Times New Roman][SIZE=3]4-[/SIZE]      [SIZE=3]This is unsolved: Cannot use High Def VDPAU on the master frontend. This setup cause display lag on the TV. Ended using VDPAU Standard definition.[/SIZE][/FONT]
 
Thanks folks for this great package !  :popcorn:

---

### Post by vanbob on 2010-12-07
**_Hardware_**
**Motherboard**: MSI H57M-ED65 LGA 1156 Intel H57 HDMI Micro ATX
**CPU**: Intel Core i3-560 Clarkdale 3.33GHz 4 x 256KB L2 Cache 4MB L3 Cache LGA 1156 73W Dual-Core
**RAM**: G.SKILL Ripjaws Series 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800)
**Video Card**: [I3 processor]
**Sound Card**: HDMI [motherboard]
**HD**: Western Digital Caviar Green WD10EADS 1TB 32MB Cache SATA 3.0Gb/s
**Remote**: mceusb
**Tuners**: Hauppauge WinTV-HVR-2250
**Country**: US
**TV provider**: OTA
**Mythbuntu Version**: 10.10 (64 bit) & Ubuntu 10.10 desktop

***Performance***
Used LowSky's tutorial ([http://ubuntuforums.org/showthread.php?t=566529]("http://ubuntuforums.org/showthread.php?t=566529")) to get HVR-2250 running.  I used 10:10 HVR2250 driver and audio.
Still encountering "Video Buffer Errors" but suspect this is a antenna reception problem.  I'll post if it's something different.

---

### Post by MarkAtNeerim on 2011-01-06
Motherboard:    Gigabyte EP45-DS4 
CPU:            Intel E8500 Core 2 Duo 3.16 3.16 GHz, 1333 MHz FSB
RAM:            8GB DDR2
Video Card:     nVidia EN8500GT-Silent
Sound:          RealTek on M/B
HDD:            OCZ Agility 60 GB SSD
                WD Velic1raptor 300MB (x2)
Tuners:         Hauppauge Nova-T500 PCI Dual tuner
                Leadtech DTV1000S Single tuner
Location        West Gippsland, Victoria, Australia
TV format:      Free to air Digital

Mythbuntu:      Mythbuntu 10.10  x64 xfce desktop

Works great, no problems with with any of above hardware.

[COLOR="black"]**Note:**[/COLOR]  Hauppauge WinTV-HVR-T1300 fails to tune  or lock stations, tried backported V4L-DVB with fix at:
      [https://bugs.launchpad.net/mythtv/+bug/439163/comments/147](https://bugs.launchpad.net/mythtv/+bug/439163/comments/147)
which solves tuning/lock problem but interferes with IR remote,  so will wait for fix in kernel before deciding to replace DTV1000s with it.

Thanks for great package

---

### Post by nhtrader on 2011-01-22
AverTVHD Duet - Non Functional


Hardware
Motherboard: Gigabyte GA-MA785GM-US2H
CPU: AMD X2 245 (2.9Ghz)
RAM: 4 Gb
Video Card: Onboard AMD/ATI 
Sound Card: Onboard
HD: 750Gb Seagate SATA 3.0
Remote: none
Tuners: AverTVHD Duet
Country: US
TV provider: Comcast/OTA
Mythbuntu Version: 10.10 (32 bit) & tried both open-source video driver and AMD/ATI proprietary drivers

Performance
AverMedia's AverTVHD Duet not supported. MythTV Error message = 'No UPnP'
No playback; No recording possible.

---

### Post by Slate8 on 2011-01-23
_**Hardware: **_
**Motherboard: **Acer Aspire Revo R3700 Desktop
**CPU:** Intel Atom D525 1.8GHz
**RAM: **2Gb
**Video Card:** NVIDIA ION 2 
**Sound Card:** onboard
**HD:** 160Gb SATA
**Remote:** Windows Media Center
**Tuners:** WinTV Nova-TD Diversity USB
**Country:** UK
**TV provider:** Freeview
**TV signal type:** DVB-T
**Mythbuntu Version:** 10.10

**_Performance_**
All hardware detected and functional except driver for wireless adapter which causes a hang on shutdown / restart. 

Fix for wireless driver
Credit to Dan Wood from the comments page on [http://www.ebuyer.com/product/236579](http://www.ebuyer.com/product/236579)
[I]Open a terminal and type:
sudo pico /etc/modprobe.d/blacklist.conf

Now add this to the bottom of the file:
```
blacklist rt2800pci
```

Save the file (Ctrl+o)

Now reboot (you'll still need to hold power button in this time!).

You should now find your system restarts with a different wifi driver that behaves better on shutdown.
[/I]
There was slight tearing when viewing video so I disabled compositing
edit /etc/X11/xorg.conf and add the following to the bottom

```
Section "Extensions"
  Option "Composite" "Disabled"
EndSection
```

Then reboot

Fantastic little machine. Cheap, silent, plays high bitrate 1080p h264 video through VDPAU with ease. Highly recommend this little box as a myth frontend / backend.

---

### Post by Chunk of Earth on 2011-01-26
> **superm1 said:**
> Hi folks,
With the release of the beta, the amount of changes that can be made are likely limited to bug fixes.

In an effort to produce accurate documentation of what people will need hardware wise for setting up a box, we'd like if you can post what hardware you've got (particularly tuners) and how things work with it.

_**Hardware**_
[B]Motherboard: Dell 400sc
CPU: Pentium 4 2.8GHz Hyperthreaded[/B]
**RAM: 2.5GB**
**Video Card: nVidia GeForce FX 5200 **
**Sound Card: SoundBlaster Live! 5.1 Platinum**
**HD: Samscum SpinPoint 500GB x2 in LVM and RAID 1 config**
**Remote: mceusb IR6**
**Tuners: Hauppauge HVR-1600 (x2), pcHDTV HD5500**
**Country: 'tis of thee**
**TV provider: Suddenstink Cable**
**TV signal type: QAM 256**
**Mythbuntu Version: 10.10**
**MythTV Version: .24-fixes**

_**Performance**_
The SoundBlaster Live **does not work** with the .24-fixes branch. I (and at least one other user) get constant [ALSA buffer underruns and jumpy video]("http://ubuntuforums.org/showthread.php?t=1632963"). I can make it work with the on-board audio (Intel ICH5) as long as I settle for 2-channel analog sound output.
XvMC would be nice with the 5200 video but the package maintainers have dropped support for it in the nightly builds. Xv and openGL scaling work but with a little extra CPU utilization (mythfrontend.real uses about 17% CPU while playing SD video)

---

### Post by crbnrod on 2011-02-21
_**Hardware**_
**Motherboard: **Asus Pundit P1-AH2
** CPU: **Athlon 64 X2 3800+
**RAM: **1 Gb Kingston DDR2
**Video Card: **onboard, Nvidia 6150
**Sound Card: **onboard, Azalia ALC86-DTS
**HD: **Seagate Barracuda 500 Gb SATA 
**Remote: **MCE, came w/tuner card
**Tuners: **Hauppauge PVR-500 
**Country: **USA
**TV provider: **Comcast 
**TV signal type: **analog cable tv
**Mythbuntu Version: **10.04. Machine has been running since April 2008, so I don't really remember what the original version was.

[U][B]Performance
[/B][/U]Machine is solo FE/BE. Add'l hardware is a D-Link WDA-1320 wireless adapter. Everything pretty much works out of the box with a clean install of 10.04. I think the only tweak I made was to add a delay to the backend startup in /etc/init/mythtv-backend.conf so the tuner cards are initialized before the backend starts.
Will soon be canceling cable and switching to digital OTA. Have (v. briefly) tested Hauppauge 950Q with this machine and seems to handle HD just fine.
This is probably moot because machine is almost 3 years old, but the PVR-500 is a really big card and required some retrofitting (read: bending the chassis a little) to fit inside the Pundit.


_**Hardware**_
 **Motherboard: **Asus M2N68-AM Plus
** CPU: **Athlon II X2 250
 **RAM: **1 Gb Kingston DDR2
 **Video Card: **MSI n8400GS-TD256 GeForce 8400
 **Sound Card: **onboard Realtek ALC662
 **HD: **Seagate Barracuda 500 Gb SATA 
 **Remote: **MCE, came w/tuner card, but see comments below
 **Tuners: ** Hauppauge HVR-2250
 **Country: **USA
 **TV provider: **OTA
 **TV signal type: **Whatever comes through the antenna - ATSC I think
 **Mythbuntu Version: **10.04
 
 [U][B]Performance
[/B][/U]Machine is solo FE/BE. Using ASUS USB N-13 for wireless internet to the machine. Motherboard does not have tv-out, "minor" oversight on my part, hence the videocard (duuuh).  I ended up with the "new" version of the HVR-2250 with the IR receiver the plugs into the tuner card. Bought USB MCE receiver on ebay & works fine. Same change to backend config as above to make sure tuner cards are initialized. 
Using Terk HDTV-a indoor antenna, if anyone cares.

Will soon be adding second antenna to OTA array in order to pick up Chicago and Milwaukee stations and will then put 950q in the old machine and convert to secondary backend (need to wire house for ethernet as well, so).

Two other pieces of hardware I wish I'd had when setting up the first mythbox:
1. A wireless usb keyboard & mouse. It's a lot easier to tweak a machine in your living room when you're not on the floor.
2. Sewell PC to TV converter. Since I for now have tube TV's, this thing makes it a lot easier to do the initial setup/install (before the tv-out gets turned on).

---

### Post by floh-511 on 2011-02-22
Hardware
Case: Lian-Li PC-Q7B
Motherboard: Asus IONT-5
CPU: Intel Atom 2x 1.8 GHz
RAM: 4 GB Kingston ValueRAM (SO-DIMM !!)
Video Card: onboard, NVIDIA ION w. 512MB dedicated video RAM
Sound Card: onboard, don´t know what chip
HD: Kingston SSDNow 2.5" SSD
Remote: MCE, Hama
Tuners: digital devices cineS2
Country: Germany
TV provider: -
TV signal type: digital satellite TV (Astra)
Mythbuntu Version: 10.10.

Performance:
Machine is solo FE/BE.
Additional hardware: A LiteOn ihos104 Blu-Ray drive and that´s it. Everything pretty much works out of the box.
The tuner card requires some work with the drivers and firmware but is easy to do even for noobs like me with support from [www.linuxtv.org](www.linuxtv.org).

HD playback (transcoded Blu-Ray rips, mp4 or mkv) runs beautifully, better than on my old Athlon X2 machine w. ATI GFX card (and this machine is FANLESS and has a 26W TDP rating!)
Raw blu-ray files (m2ts) tax my network capacity and since I only have 64 gigs of hard drive space storing locally is not an option.

Digital Audio (SPDIF) did not work right away. Solution: ALSA mixer has this muted by default. run the mixer from a terminal window, unmute it and there you go.

Live TV is currently not working, I have some issues because I botched the initial install and config of the backend. Not the capture card´s fault though, I specifically chose it because it has great Linux support.

---

### Post by newlinux on 2011-02-22
I've updated my hardware and software a number of times since my original post, so I thought I'd post a link back to it here.

[http://ubuntuforums.org/showthread.php?p=5485661#post5485661](http://ubuntuforums.org/showthread.php?p=5485661#post5485661)

---

### Post by el_Paraguayo on 2011-02-23
**_Hardware_**
**Motherboard:** Gigabyte GA870A-UD3
**CPU:** [COLOR=black]AMD Athlon II X2 245e[/COLOR]
**RAM:** [COLOR=black]4GB (&#65279;&#65279;&#65279;4GB kit (2GBx2), 240-pin DIMM, DDR3 PC3-10600) [/COLOR]
**Video Card:** [COLOR=black]MSI M210-ND512H [/COLOR]
**Sound Card:** Onboard
**HD:** 160Gb primary, 2Tb for media
**Remote: **Creative SB0540 receiver with RM1500 remote
**Tuners:** Haupaugge Nova-T PCI
**Country:** UK
**TV provider: **Aerial
**TV signal type:** DVB-T
**Mythbuntu Version:** 10.10
 
All ok _except_ Mythbuntu [does not powerdown]("http://ubuntuforums.org/showthread.php?t=1692877") successfully.
 
 
EDIT: looks like the Nova-T is giving me an irq conflict. It records fine, just won't let the machine powerdown.

---

### Post by Catiline on 2011-03-27
Hardware
Motherboard:Gigabyte [GA-G31M-ES2L]("http://www.gigabyte.com/products/product-page.aspx?pid=3485#ov")
CPU:Intel [Pentium E5400]("http://ark.intel.com/Product.aspx?id=40478") dual core 2.7GHz
RAM:[Corsair XMS2]("http://www.corsair.com/memory/xms-classic/xms2-ddr2-memory/cm2x2048-6400c5.html") 2GB
Video Card: [ASUS GeForce EN210]("http://commercial.asus.com/product/detail/99") Silent 512MB
Sound Card:On board - using analogue through HiFi amp.
HD: Samsung 1TB
Remote:Hauppauge A415-HPG-UE
Tuners:Hauppauge Nova S-Plus
Country: UK
TV provider: Freesat
TV signal type: DVB-S
Mythbuntu Version: MythTV 0.23-fixes 24158 on a standard Ubuntu 10.04 desktop install.

All hardware worked out of the box.  The remote works but has limited functionality.  I'm still trying to work the issue out with lirc.  Other than that very pleased (and relieved!) that the install has been pretty painless.  The only real issue being the bewildering array of setup options in MythTV.

The only reason I installed MythTV on top of an Ubuntu desktop was that I hated the XFCE desktop that came with Mythbuntu.

To install I followed the guide at: [http://parker1.co.uk/mythtv_about.php](http://parker1.co.uk/mythtv_about.php) . Very easy to follow.

---

### Post by KevinJaeger on 2011-07-24
I have a combined Myth Frontend/backend dedicated to Myth service.  It sits in the TV cabinet with no keyboard, mouse or monitor and gets administered over the wireless network interface.

Software: MythBuntu 11.04

Hardware:
Silverstone G4 HTPC case
Gigabyte GA-880GM-D2H motherboard
CPU: AMD Phenom II X4 840
Integrated ATI 4250 Graphics
Hauppauge PVR-350 TV Capture card with Grey Remote
IR Blaster from irblaster.info with a Scientific Atlanta set top box
Realtek 8190 Wireless network with WPA2 encryption (needed to use ndiswrapper)

Most things installed and worked as expected with two exceptions:
1. I have still been unable to get HDMI audio out of the ATI 4250 (analog audio works fine).  Would love to hear from someone who has managed to get that to work.

2. The PVR-350 remote did not work with LIRC.  I was unable to resolve constant double events, among other issues.  I eventually stopped using LIRC and just mapped the keys directly to Myth Frontend keyboard shortcuts in /etc/rc_keymaps, with X using it directly as a keyboard.  This works fine but makes it difficult to use the remote with other applications, such as VLC.

Overall, performance is excellent.  Still fiddling with the myriad playback settings and filters to optimize the playback quality.

---

### Post by Nausser on 2011-08-11
Perfect integration of an old 1970s Zenith Console stereo system(still works) and Mythbuntu 11.04. Summed up all the basics in a youtube video.
[http://www.youtube.com/watch?v=lm6cz08v14k]("http://www.youtube.com/watch?v=lm6cz08v14k")
Enjoy!

---

### Post by Slate8 on 2011-08-11
> **Nausser said:**
> Perfect integration of an old 1970s Zenith Console stereo system(still works) and Mythbuntu 11.04. Summed up all the basics in a youtube video.
[http://www.youtube.com/watch?v=lm6cz08v14k]("http://www.youtube.com/watch?v=lm6cz08v14k")
Enjoy!

Haha - that is nuts, but awesome!

---

### Post by jerg on 2011-08-22
```

**Motherboard:** MSI X58 PRO-E
**CPU:** Intel Core i7 930 (1366)
**RAM:** 10GB (1x2GB) Patriot Sector5 (PC3-10666, 1333MHz),(2x4GB) Kingston
**Video Card:** XFX ATI Radeon HD 5770 1 GB GDDR5 (XXX Edition)
**Sound Card:** RealTek
**HD:** Segate 250GB 7200RPM
**Remote:** Yes
**Tuners:** Hauppauge 1600 model 1199
**Country:** Belize
**TV provider:** CBC
**TV signal type:** NTSC/ClearQAM
**kubuntu:** 11.04

```

Can't get TV tuner to work. I read maybe that it has to do with the fact that ATI cards can't do over-lacing or something to that effect. I don't understand i figured it can work in my Windows 7 then it can sure as hell work in Ubuntu.

I had a pervious Avantek TV Tuner (don't even remember the model but I know its only Analog NTSC) that worked in this same Ubuntu using TVTime. 

When I tried to run TVTime with my new Hauppauge card the program crash ...so I try to execute TVTime through the terminal in hopes of getting back some error message and voila:

```

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/j3rg/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

```


Well thats where I am at at ....hope that some Ubuntu mad scientist can help me ...thanks in advance I will keep trying to get my card to work

1 love

---

### Post by vidtek on 2011-09-10
_**Hardware**_
[B]Motherboard: Gigabyte Z68 UD4B3
CPU:[/B] i7
**RAM:** 16gb
**Video Card: **Nvidia GTS250 
**Sound Card:** onboard ALC889 (using coax SPDIF)
**HD:**  assorted 4tb
**Remote:** Topseed
**Tuners:** Compro E900F  Hauppauge 2200 Divico PCI Fusion HDTV Compro USB U300
**Country: E.g. the Netherlands:**  Western Australia
**TV provider: E.g. canal digital:**  ABC 7, 9 10 SBS WTV
**TV signal type: E.g. DVB-S (satellite):** Terrestrial digital
**Mythbuntu Version: E.g. 8.10** 11.04 Natty

[U][B]Performance

[/B][/U]:sad:** Compro E900F** - no drivers-no linux function at all although hardware is tantalizingly close to the 

:smile:** Hauppauge HR2200** which works after some serious driver install issues with Natty[U][B].

[/B][/U]:KS Both the **Compro USB U300** and the **Divico PCI Fusion HDTV** cards have inbuilt support from Ubuntu kernel, enabling them is the same a enabling Nvidia drivers from Mythbuntu Control Centre.

Tony.

Update- 17-10-2011 see new post

---

### Post by badger_fruit on 2011-09-11
Hello forums! Here is my configuration and results ...[U][B]

Hardware[/B][/U]
**Motherboard: **Unsure, it's the 'default' one provided with the machine (Dell Poweredge SC430)[B]
CPU:[/B] P4 630,  3.0GHZ/2MB
**RAM:** 1GB SINGLE RANK 533MHZ ECC MEMORY (2X512)
**Video Card: **N/A
**Sound Card: **N/A
**HD: **80GB SATA for OS and 1TB SATA for recordings 
**Remote:** N/A
**Tuners: **TD500 (single tuner)
**Country:** UK
**TV provider: **FREEVIEW
**TV signal type:** DVB-T
**Mythbuntu Version: **10.04

[U][B]Performance

[/B][/U]Works flawlessly as a back-end machine, my front-ends are windows XP SP3 with the MythTV player software (which is flawed but does a good enough job in all fairness).

---

### Post by bbruenfl on 2011-10-16
_**Hardware**_
**Motherboard: **[ASRock A75M-ITX FM1 AMD A75 (Hudson D3)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157273")
** CPU:** [AMD A4-3400 Llano 2.7GHz Socket FM1]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103955")
**RAM:**[G.SKILL 4GB (2 x 2GB) 240-Pin]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231253")
**Video Card: **APU...
**Sound Card:** Realtek ALC892 Onboard SPDIF Optical
**HD:**  160GB HD...old don't recall brand etc.
**Remote: None**
**Tuners: None**
**Country: USA**
**TV provider: Brighthouse**
**TV signal type: **
**Mythbuntu Version: 11.10 w/Ubuntu 11.10 desktop and 11.9 amd proprietary driver**

[U][B]Performance

[/B][/U]Overall performance is good.
Audio works out of the box.
A few problems (familiar to AMD users): Cannot use OpenGL for menus or video playback without issues when switching between watching video, menus, and desktop.  Disabling all desktop effects solves some problems.
Tearing (minor) when using ffmpeg and xv-blit.
Occasional "pink screen" when starting HD content.
MythTV Frontend appears below top menu bar (compiz workaround does not solve).  Switched to 2D desktop to solve problem.

Sorry if I went overboard here but I thought I would share all the issues that I've found.

Cheers.

---

### Post by vidtek on 2011-10-16
17-10-2011 Update- 

_**Hardware**_
[B]F/E + Secondary B/E
Motherboard: Gigabyte Z68 UD4B3
CPU:[/B] i7
**RAM:** 16gb
**Video Card: **Nvidia GTS450 
**Sound Card:** onboard ALC889 (using coax SPDIF)
**HD:**  assorted 4tb
**Remote:** Topseed
**Tuners:** Compro E900F  Hauppauge 2200 
**Country: E.g. the Netherlands:**  Western Australia
**TV provider: E.g. canal digital:**  ABC, 7, 9 10 SBS WTV
**TV signal type: E.g. DVB-S (satellite):** Terrestrial digital
**Mythbuntu Version: E.g. 8.10** 11.04 Natty ******will update soon**** to Ocelot.


_**Hardware**_
 Primary B/E (very occasional frontend if I'm working in garage and want music)[B]
Motherboard: [/B]Asus mobo P5G41T-m LX 
** CPU:** Core2 Duo Socket 775
 **RAM:** 8gb
 **Video Card: **Nvidia GTS250 
 **Sound Card:** onboard ALC889 (using coax SPDIF)
 **HD:**  assorted 1.5tb
 **Remote:** None
 **Tuners:**  Divico PCI Fusion HDTV Compro USB U300
 **Country: E.g. the Netherlands:**  Western Australia
 **TV provider: E.g. canal digital:**  ABC, 7, 9 10 SBS WTV
 **TV signal type: E.g. DVB-S (satellite):** Terrestrial digital
 **Mythbuntu Version: E.g. 8.10** 11.10 Ocelot

[U][B]Performance

[/B][/U]:sad:** Compro E900F** - no drivers-no linux function at all although hardware is tantalizingly close to the 

:smile:** Hauppauge HR2200** which works after some serious driver install issues with Natty[U][B].

[/B][/U]:KS Both the **Compro USB U300** and the **Divico PCI Fusion HDTV**  cards have inbuilt support from Ubuntu kernel, enabling them is the  same a enabling Nvidia drivers from Mythbuntu Control Centre.


Installed 11.10 Mythbuntu Ocelot no hitches on the new B/E.  This surprised and delighted me as I changed everything, hardware platform AMD to an Intel based mobo and new O/S.
It looks as though Mythbuntu is coming of age, a hearty well done to all who contributed to this O/S.
Will attempt update on F/E to same, but am taking ghost of machine first.  Will report back with results soon.  I hope the HR2200 install will be easier with Ocelot.
Anyone heard anything about Compro E900 Linux Drivers yet?

Tony

---

### Post by trippy21 on 2011-10-30
_**Hardware**_
[B]Motherboard: Gigabyte M85M-US2H
CPU:[/B] AMD Ahtlon X2 5050e
**RAM:** 4GB
**Video Card: **On board NVIDIA 8200 chipset
**Sound Card:** On board NVDIA
**HD:**  60GB and a QNAP turbo NAS 1.5TB for DVD and CD library
**Remote:** Hauppauge & iPhone
**Tuners:** Hauppauge HVR4000
**Country: ** UK
**TV provider:** Freeview and Freesat
**TV signal type: **DVB-T, DVB-S, DVB-S2
**Mythbuntu Version: **11.10

[U][B]Performance
[/B][/U]All working ok after a weekend of setting up. Firmware for HVR4000 had to be installed manually, used the details on linuxtv.org and installed v1.26.90.0 currently working on combing Freeview and Freesat channel lists and need to sort out a sound problem with the WebTV, i.e. BBC iPlayer and youtube.
Looking forward to ditching SKY, just need to run some more feeds from my LNB so i can run a parrallel system, to test the wife out on its use!
upgrade plans include obviously a bigger hard drive once i've proven it all works, with Xmas coming i'm thinking a SSD drive for the OS and a TB6981 card to give more Freesat streams.
Remote needs reviewing, maybe i can persuade the wife an iPad is the way forward!

---

### Post by bobwdn on 2011-11-03
Hello everyone, this is a work in progress.

**Hardware**
**Motherboard:** ASUS P4P800
**CPU:** Pentium4 3.0Ghz/512/800
**RAM:** 2Gb PC3200 (400mHz)
**Video Card:** Nvidia 6200
**Sound Card:** Onboard MB
**HD:** Primary 20.4Gb (ide) Secondary 2Tb (sata)
**Remote:** Hauppauge (gray)
**Tuners:** Hauppauge DVR-1600
**Country:** USA
**TV provider:** Directv
**TV signal type:** ?
**Mythbuntu Version:** v11.10 (Oneiric Ocelot)

**Performance:**
Still configuring, however, this is my first box. If all goes well (so far, so good) I'll build a much bigger and faster secondary backend and this one will act as the primary backend.

---

### Post by jamoody on 2011-11-21
[U][B]
Hardware[/B][/U]
**Motherboard: ****I[B]ntel BOXDP35DPM**[/B][B]
CPU:[/B] Intel Core 2 Duo E8400, 3.0 GHz
**RAM:** 4x1G DDR2 800 MHz (PC2 6400)
**Video Card: **Galaxy GeForce 9500GT 95TFE8HUFEXN
**Sound Card: **on board
**HD: **Samsung Spinpoint F3 HD103SJ
**Remote:** StreamZap
**Tuners: **pcHDTC HD5500, Silicondust HDHomeRun Prime
**Country:** USA
**TV provider: **Comcast
**TV signal type:** ATSC
**Mythbuntu Version: **10.04

[U][B]Performance

[/B][/U]Works great, processor is a bit overkill (playback of HD only uses 30% of one processor), but makes commercial flagging (CPU intensive) much faster. 		                   		  		  		 		 			 				__________________

---

### Post by vidtek on 2011-11-22
> **vidtek said:**
> 17-10-2011 Update- 

_**Hardware**_
[B]F/E + Secondary B/E
Motherboard: Gigabyte Z68 UD4B3
CPU:[/B] i7
**RAM:** 16gb
**Video Card: **Nvidia GTS450 
**Sound Card:** onboard ALC889 (using coax SPDIF)
**HD:**  assorted 4tb
**Remote:** Topseed
**Tuners:** Compro E900F  Hauppauge 2200 
**Country: E.g. the Netherlands:**  Western Australia
**TV provider: E.g. canal digital:**  ABC, 7, 9 10 SBS WTV
**TV signal type: E.g. DVB-S (satellite):** Terrestrial digital
**Mythbuntu Version: E.g. 8.10** 11.04 Natty ******will update soon**** to Ocelot.


_**Hardware**_
 Primary B/E (very occasional frontend if I'm working in garage and want music)[B]
Motherboard: [/B]Asus mobo P5G41T-m LX 
** CPU:** Core2 Duo Socket 775
 **RAM:** 8gb
 **Video Card: **Nvidia GTS250 
 **Sound Card:** onboard ALC889 (using coax SPDIF)
 **HD:**  assorted 1.5tb
 **Remote:** None
 **Tuners:**  Divico PCI Fusion HDTV Compro USB U300
 **Country: E.g. the Netherlands:**  Western Australia
 **TV provider: E.g. canal digital:**  ABC, 7, 9 10 SBS WTV
 **TV signal type: E.g. DVB-S (satellite):** Terrestrial digital
 **Mythbuntu Version: E.g. 8.10** 11.10 Ocelot

[U][B]Performance

[/B][/U]:sad:** Compro E900F** - no drivers-no linux function at all although hardware is tantalizingly close to the 

:smile:** Hauppauge HR2200** which works after some serious driver install issues with Natty[U][B].

[/B][/U]:KS Both the **Compro USB U300** and the **Divico PCI Fusion HDTV**  cards have inbuilt support from Ubuntu kernel, enabling them is the  same a enabling Nvidia drivers from Mythbuntu Control Centre.


Installed 11.10 Mythbuntu Ocelot no hitches on the new B/E.  This surprised and delighted me as I changed everything, hardware platform AMD to an Intel based mobo and new O/S.
It looks as though Mythbuntu is coming of age, a hearty well done to all who contributed to this O/S.
Will attempt update on F/E to same, but am taking ghost of machine first.  Will report back with results soon.  I hope the HR2200 install will be easier with Ocelot.
Anyone heard anything about Compro E900 Linux Drivers yet?

Tony


Tried installing 11.10 Ocelot on main Gigabyte Z68 machine but failed dismally.  Unable to get the Hvr2200 to work at all. 

Reverted back to Natty 11.04 kernel 2.6.38-12-generic on ghosted image.
Maybe the next incarnation in April will have proper support for the Hvr2200/2250 cards. 

 If anyone has managed to get the Hvr2200/2250 to work can they please post a how-to?

Tony

---

### Post by kenyee on 2011-12-04
Motherboard: Gigabyte Z68MX-UD2H-B3
CPU: 2500K
RAM: 16GB
Video/Sound: no separate cards needed
MythBuntu version: 11.10 with Myth 0.25 and libva
Tuner: HDHomerun

---

### Post by newlinux on 2011-12-05
Thought I'd post a link now to my 3 year old post that I just keep updated with my hardware:

[http://ubuntuforums.org/showthread.php?p=5485661#post5485661](http://ubuntuforums.org/showthread.php?p=5485661#post5485661)

---

### Post by langner on 2011-12-15
Hi,

I can't post much about the PC, will nothing really, it is old. The only new thing on it is the Digital satellite tv card that works fine. 

Hardware
TBS 8920 [I]Digital satellite TV card DVB S2 (PCI)

running Myth 0.24.1, ubuntu 11.10
[/I]

---

### Post by homewood on 2011-12-17
_**Hardware**_ EMachines T1742
[B]Motherboard:
CPU:[/B] 1.7Ghz
**RAM:**2Gb
**Video Card: **onboard
**Sound Card:** onboard
**HD:**  2-500Gb
**Remote:**
**Tuners:** Hauppauge WinTV-HVR-1600
**Country:  USA:**
**TV provider:  Charter Cable**
**TV signal type: Analog**
**Mythbuntu Version: 11.10**

[U][B]Performance

[/B][/U]Couldn't get the tuner working with .iso distro.  I built/installed the latest drivers from linuxtv and got things working

---

### Post by dangerous_d on 2012-01-07
Hardware
Motherboard: Gigabyte GA-Z68MA-D2H-B3 LGA 1155 Z68 mATX 
CPU: Intel Core i5 2500K 3.3GHz
RAM: 8G DDR3 1333MHz
Video Card: PNY GT440 1G DDR5
Sound Card: Motherboard SPDIF
HD: WD blue 250GB 6GB/s (moving to 2TB very soon!)
Remote: Hauppauge HD-PVR IR blaster
Tuners: Hauppauge HD-PVR
Country: USA
TV provider: Comcast Xfinity
TV signal type: Cable
Mythbuntu Version: 11.10/0.24.x

Performance
It's my primary front/back device and it basically worked out-of-the-box.  I use high-quality VDPAU for playback and high-quality recording with real time commercial detection.  The system has plenty of extra resources.

The graphics card cooling fan was too loud so I unplugged it and it occasionally overheats.  The channel changer is imperfect and it occasionally ends up on the wrong channel for a recording.  Otherwise I'm very pleased.

---

### Post by novellahub on 2012-01-13
Updating my last hardware posts.  Just upgraded my Master Backend/Frontend with a new Hex Core AMD processor. Also added a HDHR Prime and retired a old Slave SD Recording system.

Master Backend / Frontend:
[http://ubuntuforums.org/showpost.php?p=8129716&postcount=236](http://ubuntuforums.org/showpost.php?p=8129716&postcount=236)

Slave Frontend:
[http://ubuntuforums.org/showpost.php?p=8294065&postcount=248](http://ubuntuforums.org/showpost.php?p=8294065&postcount=248)

Retired:
[http://ubuntuforums.org/showpost.php?p=5882582&postcount=152](http://ubuntuforums.org/showpost.php?p=5882582&postcount=152)

---

### Post by ecwanet on 2012-01-27
Hardware Primary BE/FE
Motherboard:ASRock M3A785GM-LE/128M
CPU:AMD Phenom II X2 555
RAM:4GB DDR3 1600
Video Card: onboard Radeon HD4200 dual VGA/DVI-D
Sound Card: onboard ALC662 HD
HD: Samsung 2.5in 250GB, 2 x Samsung 3.5in 2TB eco green 
Remote: Ortek vrc-1100
Tuners: BlackGold BGT3650 quad DVB-T2
Country: UK
TV provider: Freeview
TV signal type: DVB-T2 
Mythbuntu Version: 11.10
Triple boot Mythbuntu//Slackware 13.37/ Windows 7

Performance
Records at least four channels simultaneously. Not got to grips with profiles yet for best playback. Don't like AMD video drivers. ALSA driver settings need some work.

Sometimes after changing channel, reception (video and audio) is completely garbled and does not recover itself. Changing to another channel and back again immediately usually corrects the problem. I should probably start a thread for it.

---

### Post by blackadam on 2012-03-12
Processor
Type Intel Extreme Edition 840 3.2 GHz
Mainboard
Chipset type Intel 955X
Data bus speed 800.0 MHz
RAM
Installed Size 6.0 GB DDR2
Storage
Hard Drive 750.0 GB - Standard - Serial ATA
Hard Drive Storage 1TB
Optical Storage
Type DVD-ROM
Read Speed 16x
Optical Storage (2nd)
Read Speed 16x
Monitor
Monitor Type LCD display
Diagonal Size 20.1 in
Viewable Size 20.1 in
Graphics Controller
Video Memory 256.0 MB / 256.0 MB (max)
Audio Output
Type Sound card - Integrated
Audio Adapter Creative Sound Blaster Audigy 2 ZS
Operating System / Software
Linux Oneric Ocelot

My Storage Drive is set somehow to read only and i don't know how to edit it so that i can use it like normal if anyone can help me out with that

---

### Post by vidtek on 2012-03-12
> **blackadam said:**
> Processor
Type Intel Extreme Edition 840 3.2 GHz
Mainboard
Chipset type Intel 955X
Data bus speed 800.0 MHz
RAM
Installed Size 6.0 GB DDR2
Storage
Hard Drive 750.0 GB - Standard - Serial ATA
Hard Drive Storage 1TB
Optical Storage
Type DVD-ROM
Read Speed 16x
Optical Storage (2nd)
Read Speed 16x
Monitor
Monitor Type LCD display
Diagonal Size 20.1 in
Viewable Size 20.1 in
Graphics Controller
Video Memory 256.0 MB / 256.0 MB (max)
Audio Output
Type Sound card - Integrated
Audio Adapter Creative Sound Blaster Audigy 2 ZS
Operating System / Software
Linux Oneric Ocelot

My Storage Drive is set somehow to read only and i don't know how to edit it so that i can use it like normal if anyone can help me out with that

Blackdam-

You don't list your tuner card or interface. 
How is the storage drive formatted?
When you mount it you need to ensure you have read/write permissions 
both for your normal user and for mythtv.
Tony.

---

### Post by Henk Poley on 2012-03-30
Terratec C1500 CI, a DVB-C tuner with CI slot daughtercard, "new" hardware revision, with coax plugs ("tulip" plugs). 

Works but does not support QAM256 properly. Might be possible to get to work by figuring out better sweeprate (etc.) values for the stv0297 tuner driver.


```
02:09.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
	Subsystem: Technotrend Systemtechnik GmbH Device 1010
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at fdefe000 (32-bit, non-prefetchable) [size=512]
	Kernel driver in use: budget_ci dvb
	Kernel modules: budget-ci

Class:     0x048000
Vendor:    0x1131
Device:    0x7146
SubVendor: 0x13c2
SubDevice: 0x1010
```

---

### Post by GiggsyR on 2012-05-02
_**Hardware**_
**CPU:** AMD64 Dual Core 2.6 Ghz
**RAM:** 1.0 gb ram
**Video Card: **NVIDIA Geforce 8600gt, 256 mb
**Remote****: **none yet
**HD:** 80 gb hard drive
**Tuners:**
Hauppauge HVR-1300
Medion Creatix Hybrid

[U][B]Performance
[/B][/U]All hardware properly detected and functional except for Analog.

---

### Post by mcfiddish on 2012-06-09
```
Motherboard:       ASRock H67M-ITX mini ITX
Case:              SilverStone SG07
CPU:               Intel i3-2100
Cooler:            SilverStone NT06-E
RAM:               G.SKILL Ripjaws Series 4GB DDR 1333
Video Card:        Use Intel HD 2000 graphics on chip
Sound Card:        Use motherboard audio
HD:                Boot: Crucial 64GB SSD, Storage: 1 TB SATA
Remote:            Microsoft MCE
Tuners:            HDHomeRun Prime, HDHomeRun
Country:           USA
TV provider:       Verizon
TV signal type:    FIOS
Mythbuntu Version: 12.04
```

This system worked great right from the start.  The case is rather small, but I did not install an optical drive or dedicated video card so it's roomy enough.  The system is extremely quiet.

The only trouble I had was getting the analog audio to work.  I'm sure it's doable; I just didn't spend the time.  HDMI audio/video works perfectly.  I use the OpenGL playback profile.

---

### Post by anonymousdog on 2012-06-13
[VisionTek Products Candyboard Mini Keyboard with Touchpad - Wing Design (900508)]("http://www.amazon.com/VisionTek-Products-Candyboard-Keyboard-Touchpad/dp/tech-data/B007VMCBN4")
This little thing straight rocks, just plain kicking the snot out of all other remote control solutions I've tried.
[LIST]
[*]Rechargeable with mini-usb cable/charger
[*]Backlit keys with auto-off
[*]Backlight button easy to find in the dark (top-right corner)
[*]Auto-off function for whole unit (not just backlight)...any keystroke wakes unit
[*]Small, unobtrusive status lights
[*]Full Keyboard with no missing keys: F1-F12, Fn, some media keys
[*]Adequate RF range (at least 5meters with obstructions)
[*]Tiny USB dongle
[*]Zero config: kernel drivers support this as keyboard and mouse
[*]Small form factor similar to typical candy bar remote controls
[*]Switchable touchpad "sensitivity" changes how quickly it moves the pointer
[*]Touchpad Scrolling function (like a mouse scroll wheel)
[*]D-pad supports up/down/left/right and PageUp/PageDn/Home/End
[*]Layout feels better than units with touchpad in lower right-hand corner
[/LIST]
Don't spend the money for a DiNovo mini or Sony RF mini-keyboard.  This unit is "the one".
Love. It.

---

### Post by navingoradara on 2012-07-10
Just a simple works/doesn't work followed by a short description will  suffice.  Hopefully a lot of the problems people encounter will be  simple solutions (such as manually adding a remote configuration), but  still a separate thread is much preferred to using this thread again.   If you have a piece of hardware that you got to work though the help of  the forums or other online source,

---

### Post by anonymousdog on 2012-07-10
> **navingoradara said:**
> Just a simple works/doesn't work followed by a short description will  suffice.  Hopefully a lot of the problems people encounter will be  simple solutions (such as manually adding a remote configuration), but  still a separate thread is much preferred to using this thread again.   If you have a piece of hardware that you got to work though the help of  the forums or other online source,
Do you have a point?  Is this objection related to a particular post?  "Using this thread again?": It's a sticky to which users are expected to post new, working hardware.  What's the problem?  Are you sure you should be "flexing" your opinion on forum structure and use while so new to this forum? :confused:

Forget my confusion over your unquoted quote of the OP's instructions, I figured out...no, don't forget it...your post is still confusing because you have posted no context or anything other than an unreferenced, unquoted quote.  If you're objecting to my post, suck it!  My entry wasn't a hardware list package, but it takes up very little room, does not disrupt the thread with off topic garbage, and adds meaningful content.

---

### Post by vidtek on 2012-07-11
> **anonymousdog said:**
> Do you have a point?  Is this objection related to a particular post?  "Using this thread again?": It's a sticky to which users are expected to post new, working hardware.  What's the problem?  Are you sure you should be "flexing" your opinion on forum structure and use while so new to this forum? :confused:

Forget my confusion over your unquoted quote of the OP's instructions, I figured out...no, don't forget it...your post is still confusing because you have posted no context or anything other than an unreferenced, unquoted quote.  If you're objecting to my post, suck it!  My entry wasn't a hardware list package, but it takes up very little room, does not disrupt the thread with off topic garbage, and adds meaningful content.

Angrydog-  I personally welcomed your original post as it sent me in a different direction and I bought the Noontec mini as a result of your post.  Perhaps the newbie nav...is confused with the forum structure and didn't mean to put the post up that we see, but was just trying to quote from the sticky and got it wrong.  Let's give him the benefit of the doubt.  Anyway, my hardware/software has changed so I thought I'd update my list.

Hardware
F/E + Primary B/E
Motherboard: Gigabyte Z68 UD4B3
CPU: i7
RAM: 16gb
Video Card: Nvidia GTS450 
Sound Card: onboard ALC889 (using coax SPDIF)
HD: assorted 4tb
Remote: Topseed
Tuners: Compro E900F, Afatec Magica dual USB, Compro U300 USB Divico PCI Fusion HDTV 
Country:  Western Australia
TV provider:  ABC, 7, 9 10 SBS WTV
TV signal type: E.g. DVB-S (satellite): Terrestrial digital
Mythbuntu Version: Mint Maya 
Noontec M100 mini keyboard, Harmony i1000 remote

Hardware
Secondary B/E (very occasional frontend if I'm working in garage and want music)
Motherboard: Asrock mobo G41C-S 
CPU: Core2 Quad Socket 775
RAM: 8gb
Video Card: Nvidia GTS250 
Sound Card: onboard ALC889 (using analogue)
HD: assorted 1.5tb
Remote: None
Tuners:  Hauppauge HR2200
Country: Western Australia
TV provider: ABC, 7, 9 10 SBS WTV
TV signal type:  Terrestrial digital
Mythbuntu Version: Ubuntu Lucid

Performance: Both these machines perform beautifully as home theatre machines.  They are both housed in my garage with an internal wall separating them from my theatre.  I have hard-wired  the boxes to my projector and LCD tv using HDMI, DVI and to my sound system using coax digital and stereo analogue.  I extended the usb connections on both machines and have a pair of 7-port powered usb hubs so I have connectivity with the machines from the theatre.  I am now able to record up to 11 different channels simultaneously while enjoying a film at the same time, I have never been able to stress these machines to any noticeable degree.

Works/Doesn't work:

Installed Linux Mint Maya no hitches on the new BE/FE. 
Because later kernels insist on using the RTL8169 driver for almost every chipset, I needed a distribution with all the fruit installable from DVD, otherwise cannot install network drivers and therefore no internet, no drivers, no internet....etc...  

Hauppauge HR2200 will not work in any iteration since Lucid, my card only works with the earlier SAA drivers, it won't work with the NXP driver.
Compro E900F I finally got this to sort of half work with Linux.
Requires card=5 in driver file and only works with one tuner on big signal strength.

Both the Compro USB U300, the Afatek Magica USB and the Divico PCI Fusion HDTV cards have inbuilt support from Ubuntu kernel, enabling them is the same a enabling Nvidia drivers from Mythbuntu Control Centre.  There was an issue with the old Afatek af9015 drivers, they were flaky, the newer drivers work like a charm, get them here- [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/)

Tony.

---

### Post by hovrashko on 2012-07-12
I used Dell optiplex 280 for my MythUbuntu project and it worked very well.
Hardware
CPU: Intel pentium 3 Ghz
RAM: 1.0 gb ram
Video Card: NVIDIA 64 mgb integrated 
HD: 60 gb hard drive
Tuners:
Hauppauge PVR-350

:)

---

### Post by Nath4n on 2012-07-22
Acer AspireOne AOD-255 

Intel Atom N550 - 1.5 GHz
RAM 2gig - upgraded from 1
Graphics chip - Intel GMA 3150
Broadcom 802.11n wireless (requires Wl driver must install in 'additional drivers')
OS - Lubuntu 12.04
Webcam/internal mic
120 gig hard drive
SD Drive WORKS (will not work on any other *buntu distro, developers please look into this)

EVERYTHING works with Lubuntu 12.04 and I mean EVERYTHING.

This is not the case with Ubuntu, or any other distro FWIW.

---

### Post by ahood on 2012-07-24
Long time mythtv/mythbuntu user. I rebuilt my BE/FE system because it was low powered (AMD Athlon XP, GeForce 6200, 2 GB RAM, and analog tuners only). Because my tv provider (Comcast) stopped broadcasting analog signal, we could no longer record tv.

The new BE/FE system was built to for recording digital tv, capturing vhs movies, storing/playing videos, and storing/playing music.

BE/FE Hardware Specifications

[INDENT]Motherboard: ASUS P8 Z68-V/Gen 3 (LGA115 CPU socket)
CPU: Intel Core i3-2120 (3.3 Ghz, 3Mb Cache) 
RAM: 8 Gb (GSkill, DDR3-1600)
Videocard: Integrated into i3 CPU
TV Tuner: pcHDTV 5500 (digital/analog), Hauppauge PVR 500 (analog only)
Soundcard: Integrated into motherboard
Powersupply: Dynex 520 Watt
DVD Drive (optical): LG GH24 Super Multi DVD Rewriter
Hard Disks: OCR 120 Gb Solid State SATA III (OS), 750 Gb WD SATA, 2Tb Samsung SATA
Remotes: MediaGate MCE USB GP-IR02BK, Cideko Air Keyboard  AVK-02
OS: Mythbuntu 12.04 (Precise)
TV: Panasonic Viera 50"[/INDENT]

What Works Flawlessly:
All hardware worked out of the box. I am using the pcHDTV to record digital (DBS) broadcasts only, while the PVR 500 is connected to a VCR to record VHS videos. The system has plenty of power to play high definition videos smoothly.

Resolvable Issues:
Initially the pcHDTV card was unable to pick up all of the tv channels and there was some pixelation with recordings. The fault was not the pcHDTV card, but rather a weak signal (<80%) due to splitting the coaxial cable between MythTV and the TV. I also had the other splits left over from the previous BE/FE system. Removing all of the coaxial cable splitters (1-three way and 1-two way) and a single coaxial cable from the wall to the pcHDTV increased the signal to >90%. The pcHDTV was then able to pick up all of the tv channels and pixelation in the recordings was eliminated.

What's Not Resolved:
Screen resolution 1280x720 does not fit in the tv screen (top task bar cannot be seen except for a few pixels). I have been unable to adjust the screen to fit the tv using tv zoom feature or MythTV utilities. This is more annoying than a significant problem. The fact that xfce allows right-clicking on the desktop for access to programs is really appreciated.

Mythweather doesn't work very well for me. Current conditions works, but none of the other screens in Mythweather even though the source is configured.

Other than the above, Mythbuntu software works very well. 

Thank you Mythbuntu team and MythTV developers.

---

### Post by topcat5 on 2012-08-02
Frontend for MythTV & Flashvideos.  Works like a charm no issues at all.  

[LIST]
[*]Antec ISK 310-150 Black Mini-ITX Desktop Computer Case
[*]PNY GeForce GT 430 1024MB DDR3 PCI-Express 2.0 DVI+VGA+HDMI Low Profile Graphics Card
[*]Intel Core I3-2120T processor
[*]Crucial 64 GB m4 2.5-Inch Solid State Drive SATA 6Gb/s CT064M4SSD2
[*]ASRock H67M-ITX Socket 1155/ Intel H67/ SATA3&USB3.0/ A&V&GbE/ Mini-ITX Motherboard
[*]Corsair XMS3 4 GB 1333MHz PC3-10666 240-pin DDR3 Memory
[*]Windows 7 Vista XP Media Center MCE PC Remote Control and Infrared Receiver
[*]ARCTIC 80mm F8 case fan
[/LIST]

Some Notes:  

Plays MythTV with advanced 2x vdpau interlacing flawlessly. Resolution is 1920x1080@60  Fullscreen youtube or other flash vids work without issue as does 1080p video streamed from server. 

This setup allows for a GT 430 Nvidia graphics card. If you go with a different card, pay attention to the heatsink. It's very tight. Some GT 430 heatsinks simply won't fit. 

This system is connected to widescreen Samsung TV via HDMI connection on GT 430. (Video & Sound)  Sound on MythTV worked fine via this method.   Sound on Ubuntu was more difficult.  Took a bit of research to find settings that worked for alsa. Soundcard on Mobo is turned off.  

This was a tight fit, but I wanted a small case for the kitchen counter with the power to play anything and this system does it really well. I added an additional fan and set both to lowest setting result is that I can just barely hear it and only if the TV is turned off.   Heat is no issue at all as even playing a high rez video with advanced interlacing, there is no heat rise at all and the stock intel cooling fan never needs to shift to higher speed. 

I did not install an optical drive.  It would work with this case, but honestly I don't really see how it would fit with the internal PS and cabling. 

Now issues at all with available power from the included internal supply. (no brick needed)  The 2120T is low power and is barely used while Myth is playing.   

This system boots up from power button to MythTV menu in less 10 seconds. This is mostly due to the SSD.   There is room for a 2nd SSD in this case but I did not use it.  

The case has USB 3.0 headers on the front but my Mobo does not support it.  You may want to use a different Mobo if USB 3.0 is important.  

The remote I'm using identifies itself as a keyboard & mouse, so LIRC is not needed.   The mouse part is handy.  I had to use Xmodmap to configure some of the keys as MythTV does not recognize "shift".   It's very responsive once setup.

---

### Post by mtbdrew on 2012-09-10
Walmart online is selling the Hauppauge WinTV-HVR-850

lsusb -v will show the manufacturer:device code of 2040:b140

dmesg will show:

[   22.752176] dvb_init: looking for tuner / demod on i2c bus: 2
[   22.809556] tda18271 2-0060: attaching existing instance
[   22.809562] DVB: registering new adapter (cx231xx #0)
[   22.809567] DVB: registering adapter 2 frontend 0 (LG Electronics LGDT3305 VSB/QAM Frontend)...
[   22.812176] Successfully loaded cx231xx-dvb
[   22.812424] cx231xx: Cx231xx dvb Extension initialized
[   24.354035] HDMI hot plug event: Codec=3 Pin=5 

In backend add new DVD DTV card type LGDT3305.

After power cycling the card scanned channels fine. 
This is using 12.04

Update - Tuner showed issues of not working after reset or power cycle requiring it to be unplugged and reseated. This has been reported on several sights with no fix listed. Took card and installed it in a Win7 machine afterwards re-installed in Mythbuntu box and power cycled. Tuner card came up with no problem. Will continue to monitor to see if this was a fluke and will update accordingly.

---

### Post by sparx66 on 2012-12-14
DTV2000DS Plus DVB card.

In the backend I selected DVB DTV Capture Card but no card options show up in the next line.

Should MythTv have identified the card at this point or should it have a list of cards to select? I cant see either.

Any help on where to get the driver?

lsusb -v gives:


Bus 003 Device 003: ID 0413:6f12 Leadtek Research, Inc. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0413 Leadtek Research, Inc.
  idProduct          0x6f12 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0

---

### Post by nickrout on 2012-12-14
> **sparx66 said:**
> DTV2000DS Plus DVB card.

In the backend I selected DVB DTV Capture Card but no card options show up in the next line.

Should MythTv have identified the card at this point or should it have a list of cards to select? I cant see either.

Any help on where to get the driver?

lsusb -v gives:


Bus 003 Device 003: ID 0413:6f12 Leadtek Research, Inc. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0413 Leadtek Research, Inc.
  idProduct          0x6f12 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0

I believe there is no linux driver for this card, see [www.linuxtv.org](www.linuxtv.org) - the wiki has details of what has support.

---

### Post by daone on 2013-02-16
Current Bedroom Mythtv Front-End

CPU = AMD Athalon 64 3000+ Socket 754
Motherboard = Asus K8V
Video Card = Asus ATI 9800XT
Memory = 2 sticks of 1GB DDR 3200
Power Supply = Nspire 400 watt 
Hard Drive = Seagate 250 GB SATA II
Sound Card = Onboard
Operating System = Mythbuntu 12.04 64 bit
Keyboard and Mouse = Wireless PS/2 Logitech keyboard and mouse

Television for viewing = Sansui 32" 720p lcd using VGA connection.

Had to write a custom xorg.conf file to configure ATI card to boot at 720p resolution. 

Far from the best front-end, but built with all old hard ware I had laying around. Will eventually upgrade to something more power efficient and quiet.

---

### Post by antoniodesmet on 2013-02-24
[B]Hardware
Motherboard:?
CPU:AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57
RAM:3gb
Video Card:NVIDIA GeForce 7000M / nForce 610M     
Sound Card:Conexant High Definition Audio
HD:ST9250827AS ATA Device 250gb
Remote:
Tuners:
Country: E.g. the Netherlands:
TV provider: E.g. canal digital:
TV signal type: E.g. DVB-S (satellite):
Mythbuntu Version: E.g. 8.10[/B]

Hello,my machine is packard bell amd64, 3gb ram, 250gb hdd and windows vista. i am working on baktrack 5 r2, os : linux 3.2.6 xorg server 2: 1.7.6-2ubuntu7.11. And i have this issue i can´t install geforce 7000m / nforce 600m driver, i try and try diferents drives but the result is all ways the same backtrack (os linux bt 3,2,6) can´t start the startx because they don´t found drivers.So i thing what going wrong and at the cmd prompt try the "lspci" comd,and it his what hapen the operating system don´t recognize the gpu.

[IMG]https://lh6.googleusercontent.com/-
PzOAMlOn4_U/USgKfnPbyVI/AAAAAAAAAGM/HFbuxT4C9ak/w932-h266-o-k/geforce.JPG[/IMG]
on the firts picture on widows vista is (my) gpu working fine, on the secund photo is under linux, they only recognize that vga compatible. until i can´t find the way to the operating system recognize the gpu im done , help me please.
and by the way congratulations for your being i am already thanks for your know how!

---

### Post by nickrout on 2013-02-24
> **antoniodesmet said:**
> [B]Hardware
Motherboard:?
CPU:AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57
RAM:3gb
Video Card:NVIDIA GeForce 7000M / nForce 610M     
Sound Card:Conexant High Definition Audio
HD:ST9250827AS ATA Device 250gb
Remote:
Tuners:
Country: E.g. the Netherlands:
TV provider: E.g. canal digital:
TV signal type: E.g. DVB-S (satellite):
Mythbuntu Version: E.g. 8.10[/B]

Hello,my machine is packard bell amd64, 3gb ram, 250gb hdd and windows vista. i am working on baktrack 5 r2, os : linux 3.2.6 xorg server 2: 1.7.6-2ubuntu7.11. And i have this issue i can´t install geforce 7000m / nforce 600m driver, i try and try diferents drives but the result is all ways the same backtrack (os linux bt 3,2,6) can´t start the startx because they don´t found drivers.So i thing what going wrong and at the cmd prompt try the "lspci" comd,and it his what hapen the operating system don´t recognize the gpu.

[IMG]https://lh6.googleusercontent.com/-
PzOAMlOn4_U/USgKfnPbyVI/AAAAAAAAAGM/HFbuxT4C9ak/w932-h266-o-k/geforce.JPG[/IMG]
on the firts picture on widows vista is (my) gpu working fine, on the secund photo is under linux, they only recognize that vga compatible. until i can´t find the way to the operating system recognize the gpu im done , help me please.
and by the way congratulations for your being i am already thanks for your know how!1. Install a newer version of mythbuntu (8.10 - are you serious??)

2. ```
sudo apt-get install nvidia-current

```

---

### Post by tom2460 on 2013-03-04
[B]_Hardware_
[B]Motherboard: Lenovo Z580 Laptop
CPU: i5
RAM: 4gb
Video Card:  Intel HD-4000 Integrated Graphics
Sound Card: Built into laptop
HD:  Internal plus a Toshiba external over USB 2.0
Remote: Iphone and Android Apps
Tuners: HDHomeRun dual
Country: USA
TV provider: Over the air
TV signal type: ATSC
Mythbuntu Version: 0.26
TV: Vizio connected by laptop HDMI connector

[/B][/B]I considered building a small computer for this but could not beat the price of just using a laptop.  I was concerned about the integrated graphics but it works fine for my tastes and have never noticed an issue.  This Lenovo laptop works great except that it has a bug that makes it slow to boot - not really a problem since it never gets rebooted it is on all the time.  The external hard drive is USB 3, but when I hook it to a USB 3 port it will not wake up on a reboot.  I connected it to USB 2.0 port and it works all the time.  I have not seen any problem when using the HD to record while watching another or while recording two.  I can't say that I've ever been in the worse case situation of recording two and watching another, but overall there is no sign of having any performance issue. The laptop is in an enclosed cabinet and does not overheat.

The latest phone apps are great.  When my better half got Torc (?) on her iphone, all resistance melted.  I have an Android phone and use mythmote and sometimes myth TV android for streaming.

---

### Post by grunge09 on 2013-03-06
My Setup:

Backed w/ Frontend in 1 PC:

Hardware
Motherboard: MSI 
CPU: AMD 965  Quad Core 3.4GHz
RAM: 4gb DDR2
Video Card: Geforce 210 PCI-E
Sound Card:onboard
HD: 1tb Samsung 7200 RPM
Remote: Rc6 Came with HVR-2250
Tuners: 1x HVR-2250, and 2x PVR-500
Country: USA
TV provider: Bright House
TV signal type: Cable (only using analog side of tuners)
Mythtv Version: Running Ubuntu 10.10 with Myth TV installed. 

**Note** When I installed the 2nd pvr-500 card my system freaked out and I wound up having to delete all tuners in backend and re-entering them, and had to for some reason change the IP address in the backend, then change back and it all works fine.  All 6 tuners record fine even all at once.   

Performance: It stutters at the end of a recording a little, especially when recording 6 streams at once.  but its only for a few moments.

I recently moved all my /var/lib/mythtv data to my new Ubuntu Server running Samba, it saves all data across the Gigabit networked Server PC with no noticable difference in speed.

Ubuntu Server Hardware
Motherboard: Asus 
CPU: AMD 6000+  CPU
RAM: 2gb DDR2
Video Card: Geforce 210
Sound Card:onboard
HD: 4x2TB WD Green Drives (RAID5) using 8gb usb flash drive to boot off of.

Only issue now is I need another 2TB Drive and a PCI-E 8 port Raid controller with passthru support.  I am using onboard sata II controllers for MDADM software raid.

---

### Post by flecki on 2013-03-30
Board: Asus P8Z77-V LX
CPU: Core i3 3225 3,3 Ghz
Power: be quiet straight power E9
Fan: Noctua NH-L9i
Case: Silverstone La Scala
Cable Card: SATELCO EasyWatch PCI DVB-C "Basic Edition" with CI-daughtercard (on LIWEST cable provider in linz/austria)
Harddisk: 2 x WD red 2TB (4 slots left for more storage if needed)

I use only CPU and power supply fan as the whole setup uses a maximum of 38 Watts when playing full HD - Case fans are unnecessary and louder than the rest - now i am below 20 dba which means SILENT

Core i3 integrated graphics plus CPU is enough to play full hd 1920x1080 without any issues - no additional graphic hardware needed(setting OpenGL high quality) - sound out via integrated fiberoptic SPDIF to receiver

---

### Post by newlinux on 2013-04-04
All systems running mythtv 29


**1. Firestorm - Kubuntu 14.04.5 64 bit custom build secondary backend/ HD frontend. Main desktop PC and server for various purposes (Main Office) **
[ASRock Z68 Pro3 LGA 1155 Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157251")
[Intel Core i7-2600 3.4Ghz CPU]("http://ark.intel.com/products/52213")
[Kingston Hyper X 16GB PC12800]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820104173")
[180GB Corsair Force Series SATA III Solid State Drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820233211") with ext4 partition for root and jfs for the rest.
[250Gb WD Caviar SE SATA (ext4)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822144417")
[4TB Internal Seagate ST4000VX000 (for video surveillance)]("https://www.amazon.com/gp/product/B00JW53C5Y/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1")

[**2 X Seagate** Expansion 5TB Desktop External Hard Drive USB 3.0 (STEB5000100) - formatted JFS ]("http://www.amazon.com/gp/product/B00TKFEEBW?psc=1&redirect=true&ref_=oh_aui_detailpage_o05_s00")
[HD Homerun Prime 1 Tuner allocated]("http://www.silicondust.com/products/hdhomerun/prime/")


** 2. Powergirl - Kubuntu 14.04.5 with myth installed  HD Frontend/secondary backend** - [Zotac ZBOX-ID84-U]("http://www.newegg.com/Product/Product.aspx?Item=9SIA24G28M7398&cm_re=zotac_id84-_-56-173-049-_-Product") NVIDIA GT520M (512MB) Kubuntu 14.04.1 remote frontend (bedroom)
[Intel Atom D2550 1.86Ghz]("http://ark.intel.com/products/65470/Intel-Atom-Processor-D2550-1M-Cache-1_86-GHz")
HDMI Audio/Video
[32GB SATA III SSD]("http://www.amazon.com/gp/product/B009SKB5HA?psc=1&redirect=true&ref_=oh_aui_detailpage_o02_s03")
[4GB DDR3-1066 (PC3 8500) SO-DIMM RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231213")
[Harmony 680 MCE remote]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880099001") with [MCE usb IR receiver]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880100851")
[MCE receiver]("http://www.amazon.com/gp/product/B00123UGWQ/ref=oh_details_o05_s01_i01?ie=UTF8&psc=1")
[2TB Hitachi GST Deskstar (inside USB 3.0 External Fantom GForce shell) - formatted jfs ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822145298")
[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16822136771"]250GB Western digital SATA Hard drive (ext4)
[/URL][Hauppage HD-PVR]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116030") connected to H21-200 DirecTV Receiver via Component and TOSLINK SPDIF In


**3. Amazo - Kubuntu 12.04.1 64 bit custom build HD Frontend/slave backend (commercial flagging only), daily use desktop (Secondary Office)**
[Abit AN-M2]("http://www.hardwaresecrets.com/article/Abit-AN-M2-Motherboard-Review/470") AMD (7025-630a)
NVidia Geforce 7025 (onboard)
[X2 4600 (socket AM2)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103751")
2GB PC5400
[250GB WD SATA HD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822144701") (20GB OS - EXT4, 42GB /home- EXT4, rest for recordings - JFS)


**4. Deathstroke - Kubuntu Fileserver 14.04.5 - Master Backend/HD Frontend (Main Office)**
Dell 530N 
[FOXCONN G33M02 (G33 + ICH9) ]("http://www.foxconnchannel.com/ProductDetail.aspx?T=motherboard&U=en-us0000319")
[E2180 Dual Core 2.0Ghz (socket 775) ]("http://ark.intel.com/products/31733/Intel-Pentium-Processor-E2180-1M-Cache-2_00-GHz-800-MHz-FSB")
Intel GMA3100
[Rosewill RC-219 Silicon Image PCI Express eSata x2 NCQ non-RAID SATA II Controller Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816132020")
[Intel Pro 1000 PCIe gigabit nic]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833106033")
[2TB Hitachi GST Deskstar (inside USB 3.0/esata External Fantom GForce shell) -  ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822145298") (JFS and EXT4 for data and backup)
[1TB SATA Hard drive (Samsung)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152102") legacy ext3 drive
[1TB SATA  Hard Drive (Western Digital)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136151") jfs drive
[1 Seagate Barracude 250GB Hard drive SATA (ext4)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148261")
[**2 X Seagate** Expansion 5TB Desktop External Hard Drive USB 3.0 (STEB5000100) - formatted JFS ]("http://www.amazon.com/gp/product/B00TKFEEBW?psc=1&redirect=true&ref_=oh_aui_detailpage_o05_s00")
2GB PC5400


**5. Newmyth - Kubuntu 14.04.5 Custom Build Slave backend/HD Frontend (primary recording backend in gym)**
[X2 3800 (socket 939)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103562")
2GB pc3200
[Asus A8N-E]("http://www.newegg.com/product/product.aspx?Item=N82E16813131530")
[ASUS EN8400GS SILENT/HTP/512M/V2]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814121344")
[500GB Western Digital 7200RPM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136769") EX4 for OS
[1TB eSATA 7200RPM drive (recordings - JFS)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822145304") 
[Harmony 650 remote]("http://www.logitech.com/en-us/product/harmony-remote-650")
[MCE usb IR receiver]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880100851")
[HD Homerun 2 tuners]("http://www.silicondust.com/products/hdhomerun/atsc/")
[HD Homerun Prime 2 Tuners]("http://www.silicondust.com/products/hdhomerun/prime/")


**6. Julian - Ubuntu 12.04.1 remote HD frontend/laptop [Acer 5520-5155]("http://www.cnet.com/laptops/acer-aspire-5520-5155/4505-3121_7-33089593.html") (Roams) **
AMD Turion 64 X2 TL-56 1.8Ghz
15.4 in TFT active matrix WXGA (1280X800)
120GB - Serial ATA-150 - 5400rpm (Linux partition is all EXT3)
2GB DDR2 SDRAM - 667.0 MHz
NVIDIA GeForce 7000M / nForce 610M
Dual boot with Vista


**7. Manhunter - Kubuntu 14.04.5 [Zotax ZBOX-ID41-PLUS-U]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856173028") Front End Only (Family Room)**
[Intel Atom D525 (1.8Ghz Dual Core)]("http://ark.intel.com/products/49490/Intel-Atom-processor-D525-1M-Cache-1_80-GHz")
Nvidia ION2
2GB DDR3 RAM
250GB Hard Drive
[Harmony One Remote]("http://www.logitech.com/en-us/support/harmony-one-advanced-universal-remote?osid=14&bit=64")
[MCE usb IR receiver]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880100851")


**8. Mr-Terrific - Kubuntu 14.04.5 [Zotax ZBOX-ID41-PLUS-U]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856173028") Front End Only (Theater Room)**
[Intel Atom D525 (1.8Ghz Dual Core)]("http://ark.intel.com/products/49490/Intel-Atom-processor-D525-1M-Cache-1_80-GHz")
Nvidia ION2
2GB DDR3 RAM
250GB Hard Drive
[Harmony One Remote]("http://www.logitech.com/en-us/support/harmony-one-advanced-universal-remote?osid=14&bit=64")
[MCE usb IR receiver]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880100851")


[B]9. Blackadam - [Zotac Mag HD-ND01]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856173001&Tpk=zotac%20mag") NVIDIA ION Kubuntu 14.04.1 remote frontend (roams)
[/B][Intel Atom 330 1.6Ghz]("http://ark.intel.com/products/35641/Intel-Atom-Processor-330-1M-Cache-1_60-GHz-533-MHz-FSB")
HDMI Audio/Video
160 GB 5400 RPM
2GB DDR2-800 RAM



**10. Dark-Knight - Ubuntu 12.04.1 remote  frontend/Convertible Tablet/notebook[ Fujitsu T730 ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834110433&cm_re=t730-_-34-110-433-_-Product")**
[Intel(R) Core(TM) i5 CPU M 450 @ 2.40GHz]("http://ark.intel.com/products/49022/Intel-Core-i5-450M-Processor-3M-cache-2_40-GHz")
12.1 in Dual digitizer touchscreen (1280X800)
160GB - Serial ATA 7200rpm (Linux partition is all EXT4)
4GB DDR3 1066 RAM
Intel GMA 4800MHD
Dual boot with Win7 Pro 64 bit

[B]11. WonderWoman - [Zotac ZBOX-ID84-U]("http://www.newegg.com/Product/Product.aspx?Item=9SIA24G28M7398&cm_re=zotac_id84-_-56-173-049-_-Product") NVIDIA GT520M (512MB) Kubuntu 14.04.5 remote frontend (bedroom)
[/B][Intel Atom D2550 1.86Ghz]("http://ark.intel.com/products/65470/Intel-Atom-Processor-D2550-1M-Cache-1_86-GHz")
HDMI Audio/Video
[54GB SATA III SSD]("http://www.amazon.com/gp/product/B009SX8WEQ/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1")
[4GB DDR3-1066 (PC3 8500) SO-DIMM RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231213")
[URL="http://www.logitech.com/en-us/support/370?osid=14&bit=64"]Harmony 720 remote
[/URL][MCE receiver]("http://www.amazon.com/gp/product/B00123UGWQ/ref=oh_details_o05_s01_i01?ie=UTF8&psc=1")

**Currently on the shelf OLD Powergirl - Kubuntu 12.04.2 with myth installed - Custom build Rec Room machine HD Frontend/secondary backend**
[Asus A8N-VM CSM Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131570")
[ECS NSG210C-512QS-H GeForce 210 512MB 64-bit DDR2 PCI Express 2.0 x16 HDCP Ready Low Profile Ready Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814134085")
[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16819103547"]AMD Athlon 64 X2 4200+ (socket 939)
[/URL]2.5GB PC3200
[Harmony 680 MCE remote]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880099001") with [MCE usb IR receiver]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880100851")


**Keyboard Mouse Combos:**

I have 1 [BTC-9039URF-3]("http://www.newegg.com/Product/Product.aspx?Item=N82E16823110021"),  1 [ADESSO WKB-3000UB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16823166128&Tpk=WKB-3000UB&IsVirtualParent=1"), 1 [Logitech Mini PC dinovo]("http://www.amazon.com/gp/product/B008JGU3YA/ref=oh_details_o02_s00_i02?ie=UTF8&psc=1"), and 2 [IOGEAR GKM561Rs]("http://www.amazon.com/gp/product/B002H0BOBA/ref=oh_details_o03_s00_i01?ie=UTF8&psc=1"). They all work fine out of the box. Might need to configure multimedia keys.

**Performance**:

All systems can playback 720p/1080i mpeg-2 encoded content and all 720p/1080p h.264 encoded content that I've thrown at them.  My Intel GPU systems do well with playback as well. Acer laptop needed ndiswrapper to get wireless working, and I have the web cam working, but not the internal mic. The Fujitsu Tablet took a little fiddling to get tablet features and touchscreen to work properly. Wireless and camera worked out of the box.

HD-PVR is wonderful for recording HD quality off of my directv box. I connect to the HR21 box via it's network (web) interface to change channels, so no direct serial or USB connection is needed for channel changing.

HDHomerun Prime and HDHomerun work well. All in all this system completely serves my family's needs and then some in every room with a TV/Monitor.

---

### Post by bpmod on 2013-05-07
First machine:
_**Hardware**_
[B]Motherboard: Asus P8Z68-V LX
CPU: Intel i3-2120[/B]
**RAM: 8GB Corsair DDR3 1600MHz**
**Video Card: on-board HDMI/DVI**
**Sound Card: on-board**
**HD: booting from CF recording to NAS** 
**Remote: none**
**Tuners: 2x HDHR dual + Hauppauge HVR 1800**
**Country: Canada**
**TV provider: OTA ATSC**
**Mythbuntu Version: 11.10**

[U][B]Performance
[/B][/U]For the past year and a half or so, I have been using this as a dedicated backend and have had very little trouble. Every once in a while, I would try to watch something that had been recorded, but it would not play any HD content clearly. I assumed that it was because I was feeding the DVI output through a KVM and to my monitor.

I have just moved this box from my office to my TV (to be used as a combined frontend/backend until I find the funds for a new dedicated frontend) and the only changes made were the addition of a wireless keyboard/mouse combo, the (temporary) disconnection of the coax from the internal Hauppauge tuner and an HDMI connection to my TV. I have found that I can still not output any HD content. I have tried increasing the video memory in the BIOS (see below) but that has not worked. I think I will start a new thread on this subject to see if anybody can help.

Second machine:
_**Hardware**_
[B]Motherboard: Asus P8B75-M/CSM
CPU: Intel Pentium G630[/B]
**RAM: 8GB Corsair DDR3 1600MHz**
**Video Card: on-board HDMI**
**Sound Card: on-board**
**HD: Seagate 2TB** 
**Remote: Logitech wireless keyboard/mouse combo**
**Tuners: Hauppauge HVR 1250**
**Country: Canada**
**TV provider: OTA ATSC**
**Mythbuntu Version: 12.04**

_**Performance**_
I have just installed this in my mother's house. It is not connected to the previous machine, although I had originally planned it to be my own (diskless) frontend. It is working as a combined frontend/backend with very few issues. I had some installation issues which I [posted about]("http://ubuntuforums.org/showthread.php?t=2129481"). Also, at the time that I first installed Mythbuntu on that machine, I had no luck with HD playback, so I installed the GPU mentioned in that thread. I then discovered that simply increasing the memory of the on-board video gave me eveything I needed (so I removed the add-on GPU). However, that has not been a solution to the same problem with the other machine.

Brian

---

### Post by paulsum2 on 2013-09-25
[U][B]Hardware
[/B][/U]**Motherboard: asus p8hh77-i**
[B]CPU: Intel pentium g2120 3.1 Ghz
[B]RAM: 8.0 GB ram 
[B]Video Card: NVIDIA GT630(gk208), 1GB[B][B]
[B]HD: 2 TB seagate, 3TB WD AV-GP, 2TB WD RED
Remote: Wireless keyboard
LAN: TU2-ETG trendnet usb to gigabit ethernet ... because i burned-out the ethernet on the motherboard. 
**Tuners: **[/B][/B][/B][/B][/B][/B][B][B][B][B][B][B][B]3x Silicon Dust HDHomerun
[/B][/B][/B][/B][/B][/B][/B][B]Country: Canada, Toronto
[B]TV provider :OTA HDTA
**TV signal type: ATSC  MPEG2**[/B][/B][B][B][B][B][B][B][B]
Mythbuntu Version: 12.04,([/B][/B][/B][/B][/B][/B][/B]**[B][B][B][B][B][B]effectively 12.04.3)**[/B][/B][/B][/B][/B][/B][B][B][B][B][B][B][B] but upgraded kernal to 3.8 so to get audio over HDMI using the gt630(gk208)

using mythtv 0.27

[U][B]Performance
[/B][/U]All hardware properly detected and functional. (not sure if the sdpif port works on the h77... have not tried it)
Had to install nvidia proprietary drivers before able to use HD playback. (vdpau high quality)
the TU2-ETG was recognized automatically.

all in a fractal designs node304 case, with a seasonic x-400... arctic cooling freezer pro rev 2(no fan)... using only the back case fan on the node 304 on low.
thus, is quieter than the bell satellite box beneath it.


the gt630(gk208) is the gt630 with the 64bit bus... it is perfect for mythtv. (25 watts max, idles at 5-6 watts) the whole system idles at 43 watts.
the gt640(gk208) is peppier than the gt630v2, but uses more power because of the power states when watching TV.


i found that the gt610, while you can use VDPAU high quality has a disappointing picture, some sort of "black fuzz" ; 
IMO the gt630(gk630) "the replacement" "blows it out of the water" 5- 6 watts idle power use, whereas the gt610 is 8watts idle.

the gt640 is good, but uses 12 watts idle, the gtx650 is better 12-14 Watts idle power and uses less power playing HDTV because it has 3 power states... the gt640 has 2.
 the gtx650 is a pain because in uses a mini-hdmi port.
 With the advent of the gt630(gk208), the gt640,gtx650 and higher are overkill for mythtv.



 

[/B][/B][/B][/B][/B][/B][/B]

---

### Post by z7APXKm on 2013-10-29
**Case      **- Chieftec Hi-Fi HM03B (hard to get hold of but good looking case)
**Board     **- Asus P8H77-M PRO Intel H77 Socket 1155 Motherboard
**CPU       **- Intel Core i3 3220 Ivy Bridge Dual Core Processor - Retail
**CPU FAN** - Zalman CNPS8000B Ultra Quiet Low Profile CPU Cooler
**Tuner     **- TBS PCI-E DVB-T2 Dual TV Tuner Card
**Disk       **- Western Digital WD20EARX 2TB Caviar Green Quiet SATA 6Gb/s IntelliPower 64Mb Cache 8ms HDD
**PSU       **- be quiet! BN104 Pure Power L7 350W Power Supply
**RAM       **- Corsair Memory XMS3 Classic 4GB DDR3 2000 MHz CAS 9-10-9-27 Dual Channel Desktop
**DVD       **- BDC-207DBK Blu Ray Rom / DVDRW writer from Pioneer
**KB/MSE   **- Cideko AVK08 Air Conqueror Gaming Joypad & Media Centre Keyboard Combo Wireless
**WEBCAM  **- Logitech C270 HD Webcam

Started  out with Mythbuntu but accidentally upgraded to full Ubuntu 12.04 whilst trying to fix something  so  I've now manually uninstalled as much bloat as possible back to the original look  and feel of Mythbuntu using XFCE + Compton (to prevent screen tear).  Took a while, but very happy.

---

### Post by novellahub on 2013-11-04
_**Hardware**_
**Motherboard:** ZOTAC GF6100-E-E AM3
**CPU:** AMD Phenom X4 9150e
**RAM:** ADATA Extreme Edition 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)
**Video Card:** Onboard NVIDIA GeForce 6100
**Sound Card:** Onboard Audio
**HD:** Samsung 830 Series 64GB SSD
**Remote:** None (Use RII Mini Keyboard)
**Tuners:** None (Frontend only)
**Country:** United States (Minneapolis / St. Paul Metro area)
**TV provider:** Comcast QAM
**TV signal type:** Sceptre 32" Class LED 720p 60Hz HDTV E325BV-HD

_**Performance**_
Fresh install of Mythbuntu 14.04 LTS as a frontend. Machine boots in 10 seconds with the SSD.  I enabled noatime and discard options for the mounting of the SSD.  Performance is excellent with little to no lag in bringing up recordings in menu.  File system on SSD is EXT4.

Master Backend:

[http://ubuntuforums.org/showthread.php?t=566529&page=38&p=13213042&viewfull=1#post13213042](http://ubuntuforums.org/showthread.php?t=566529&page=38&p=13213042&viewfull=1#post13213042)

---

### Post by Bushcraft Bill on 2013-11-04
HP envy-17-jo83ca  and all I get is a blank screen I have turned off secure boot and intelsmart response technology could it be that its just the nvidea card that it is not happy with?
I get to the install screen and then when I try a test drive all I get is a blank screen...

---

### Post by JP_Rockagetty_III on 2013-12-22
[U][B]Hardware
[/B][/U][B]
Motherboard[/B]: Intel DH77EB
**CPU:** i3-3245, stepping level 9h
**RAM:** 2.0 gb RAM (I might add more soon)
**HD:** 3 TB Seagate, default partitioning I think.[B]
Video Card:[/B] handled by i3 CPU
**Sound:** onboard sound
**Power supply: **OCZ Fatal1ty 550 (the 2010 version, not the 2013/2014 version)
**Networking chips:** works with motherboard's wired 82579v chip (10/100/1000).
At present, I am using the Asus PCE-N15 (wireless PCI-Express x1, "N" capable).
[B]
[U]Other hardware and information:
[/U]
Router:[/B] WRT-54GL with DD-WRT firmware (NOT "N" capable).
**Tuner: **Silicon Dust HDHomerun Dual
**Antenna:** home-built Grey-Hoverman
Combining signal with 29.8 inch "T" shape copper wire (half-wave?) for RF channel 11
**Broadcasts:** USA Free "Over-the-Air" (ABC/NBC/CBS/FOX/PBS)
**City:** Louisville, KY USA
**Mythbuntu Version:** 12.04.3 LTS
This machine is both a front end and a back end, and there are no other "ends".

_**Installation Notes:**_

Hardware "in the box" detected first time, including wireless card -- very nice!

Back end was not detected.  In MythTV backend setup --> General, in the first screen of the "Host Address Backend Setup", for both "Local Backend" and "Master Backend" I had to type in the IP Address 192.168.1.133.  That's the address the WRT-54GL (or the DD-WRT firmware) gives this machine every bootup.  On the next screen, ("TV format"), choose NTSC even though US television broadcasters use ATSC.  This dialog needs to be updated in the backend setup.  Setting up SchedulesDirect was pretty easy.

Here are two entries from my hosts file:

127.0.0.1 localhost
127.0.1.1 mikes-htpc

I'm not sure if Mythbuntu or I made that second entry, but mikes-htpc is the host name for my mythbuntu machine.  Maybe the second line is only required if your host name is not "localhost".  I don't know.  I set the WRT-54GL to hand out addresses starting at 127.0.1.1, not 127.0.0.1.

At first, "Watch TV" could not be done a second time without rebooting the machine  or shutting down and restarting the Mythbuntu back end.  This cleared up without a reinstall -- I'm not sure what happened.

An "N" capable router does not seem to be a requirement, but I am only running one tuner at a time.

It looks like using both tuners at once is not possible out-of-the-box.  Either in Mythbuntu or Mythbuntu + Windows MCE (watching two different channels on two PCs with a KVM switch) causes crashes and "tuner broken or not available" messages.

Also, if you add joe, ncftp, Krusader file manager, and maybe a few other things  (from my long experience with Mandrake/Mandriva) you will have a fine  home/office machine as well.  The "root" user is different, but  it works just fine !


[U][B]Performance
[/B][/U]
In good weather, signal is very strong (basically 100%).  In cloudy weather, signal strength and quality varies widely and frequently drops out.  Am I too close to local transmitters? (they are on Knob Creek Hill, 4 to 4.2 miles LOS to house).  My antennae are in the attic, 12 feet above ground.

HD Homerun Dual DOES require more signal than my 40-inch Toshiba (40L-5200U) to get a perfect picture.  This is a disadvantage of the Homerun.

As mentioned above, using both tuners at once is not possible yet.

But recording 1920 by 1080 is just fabulous.  It is way better than the set-top box that died on me (Toshiba D-R550).  That would only record OTA at regular DVD resolution.  I have not tried Mythbuntu commercial-detection yet, or SAMBA (sharing my files over the network).

I am not sure if the video playback is the same quality as it is with my Windows 7 box (it has a PCI-E Radeon 6770 with good drivers).  I am using a 27-inch monitor.  I have not burned any 1920x1080 MPEGs to disc and tried them on the 40-inch TV yet.

---

### Post by Clockmender on 2014-04-20
The most significant bit of my system is that I have a **_FULLY_** functional E-MU 0404 PCIe sound card.

That means Audio In/Out and Midi In/Out at a latency level appropriate to "Live" playing. This includes driving Reason on My Mac, with the _Midi_ piped from my Ubuntu box and the returning _Audio_ also piped through the Ubuntu box. This took me a looooong time to achieve BTW and I came so close to adding this card to the "Non-Functional" list.

---

### Post by mattlach on 2014-07-05
Alright here is mine:

This is for a Frontend only.  My backend is running asa a guest on my VMWare server in the basement.

This system is for a bedroom machine.  My main  HTPC in the livingroom is running Windows 8.1 with XBMC and the MythTV PVR plugin (working on converting it to a Mythbuntu machine at some point, but it is tricky as I want to retain Netflix compatibility.   I am not including system specs for the main rig, as it is running Windows and I have not tested it with Mythbuntu yet.

As can be seen below, I raided my spare parts closet and built a rig with whatever I had laying around, hoping it would work, and I wouldn't have to spend any extra money.

_**Hardware**_
**Motherboard:**  ASUS E35M1-M PRO
**CPU:** Integrated into motherboard, AMD E350, low power 1.6GHz dual core bobcat.  18W TDP
**RAM:**  2x4GB DDR3-1600 (running at 1333, as that is the most the motherboard/CPU supports)
**Video Card: **  Integrated in APU.  AMD calls it the Radeon HD 6310
**Sound Card:**  Integrated Realtek ALC 887-VD2
**HD:** OCZ Onyx 32GB SSD.   (all real storage is on the backend, which utilizes a 28TB ZFS RAIDz2 array on another guest running FreeNAS linked internally to the backend using a virtual 10gig ethernet connection)
**Remote:**  Mythmote on Android phone (for now)
**Tuners:**   This is a frontend only system.  Tuners on backend are Ceton InfiniTV 6 ETH.
**Country:**  USA
**TV provider:**  Verizon FiOS
**TV signal type:**  Umm, not sure.  Whatever FiOS uses.
**Mythbuntu Version:**  14.04

_**Performance**_

I'm very impressed with this 3 year old low power system.  Based on what some are saying it shouldn't be powerful enough, but it is a little trooper and handles the mpeg2 based 1080p TV streams just fine.  It struggles with H264 / mpeg4 HD streams in my media library though.  They play, but can become jumpy in high detail scenes with lots of movement.  I expected this though (after all it's a 3 year old low power Atom competitor), and this machine is really mostly used for TV anyway.

_**Notes**_

In order for this to work smoothly, I needed to enable VDPAU which some say is troublesome on Radeon chips.   The trick appears to be to avoid the firegl closed source drivers and rely on the open source Mesa drivers.  The VDPAU enabled MESA drivers are not included with ubuntu due to them adding an additional 8MB to the ISO, but IMHO, they really should be added, at least to the Mythbuntu release.

In order to get this working I added the Oibaf PPA (read [this Launchpad link](https://launchpad.net/~oibaf/%2Barchive/graphics-drivers/), and follow instructions)

I did have a weird problem upon a fresh install, in which [MythFrontend would not load](http://ubuntuforums.org/showthread.php?t=2232740) even after retrying the install a couple of times, which solved itself when I (on a whim) deleted the .MythTV folder in my home folder in order to reset all settings.

I would probably recommend against buying an E-350 specially for MythTV based on it being marginal in power, especially for H264/Mpeg4, but if you are aware of it's limitations and have one in your closet (like I did) then it will do the job surprisingly well!

Based on my experiences, I'd say maybe it is time we stop dissuading users from using Radeon hardware.

---

### Post by vidtek on 2014-08-17
mobo and processor etc as per signature

Worked out the box-

1 x Hauppauge 2210
1 x Hauppauge 2200
GTS450 Nvidia
MCE remote translated to Logitech i1000
Logitech K800 wireless kb
" M810 wireless mouse
HDMI output inc. audio to Samsung E8000 tv.

Doesn't work/problematic

Mythtv freezes on video playback when using replay (sometimes)
Brother MFC885CW printer - there seems to be no interface for connecting printers in Mythbuntu I'll do separate post on this.

Cheers, Tony.

---

### Post by Mike_Brown on 2014-11-20
My MythTV DVR build was a project to build a DVR from spare components and parts I already have and my attempt to have only &#8216;sweat equity&#8217; in it &#8211; ie: no money investment. (I actually converted the Dell &#8216;slim&#8217; desktop case by inserting spacers in the 4 sides to make the case tall enough for the Hauppauge full height cards.) So far total cost = $0.00!!!

I have built the box with these components:
**Hardware**
**Motherboard:** Dell Optiplex 755  
**CPU: **Core2 Duo 7500 (2.93gHz)
**RAM:** 4GB DDR2 
**Video card:** GigaByte GV-R435OC-512I -- Radeon HD 4350 with 512Mb ram (HDMI out)
**Sound Card: **HDMI out through Video card
**Hard Drive:** 1Tb Western Digital Hard Drive
**TV Tuner Cards:** 2 Hauppauge HVR 1600s
**Lan:** 100Mb on motherboard Static IP to network via Linksys WRT120n router (hard wired)*
**Location:** Florida, USA
**TV Provider:** OTA &#8211; ATSC via small outside antenna (distance to xmitters = 10 ~ 40 miles @ 280&#8304; ~ 20&#8304;)
**Mythbuntu Version:** 14.04 LTS (set up as Backend/Frontend and backend server for XBMC-KODI)
**Internet Provider: **Comcast Xfinity 3Mb service
**Audio/Video output:** HDMI to Yamaha Aventage RX-A800 receiver --> Sony KDL60EX500 TV (all of my Home Entertainment Components go through the Yamaha receiver)
[B]
Other Home Theater Components:[/B] Phillips DVDR 3455H PVR, Insignia Blueray player, Dell Inspiron-3847 Home Theater Computer running Windows 8.1 with XBMC- KODI frontend (used for Amazon Prime and Netflix viewing and music server), and a Sony VHS recorder for the occasional video tape playing.
*The MythTV computer, the HTPC and the Blueray player along with my office computer are all hard wired connected to the router with static IP addresses. Laptops, tablets and phones connect wirelessly.
 
**Performance**
After several attempts (re-installs) to get the system running, I have finally gotten it to do most of my design requirements. I had problems with the HDMI not outputting after the receiver changing to another input, with Ubuntu not recognizing both of my Hauppauge cards every boot and problems with remote control with MythMote for my Android and also the IR receiver not working. 

A settings change corrected the HDMI trouble. I am working on the TV card issue trying to make changes in Grub to correct the problem. For now, I am recording one show at a time. The IR and MythMote problems are not a big worry as I am using a keyboard to navigate MythTV.

The biggest challenge is going from being a Windows pro to a Linux newbe &#8211; trying to keep from using all of my Windows methods to quickly fix problems to learning how to do things in Linux. Once the Linux methods become natural to me, things will be much smoother. The support that Ubunbtu veterans have given me with trouble-shooting the problems has been great. Thanks muchly.

---

### Post by MoebusNet on 2014-12-21
This is my first attempt at a dedicated combined front-end/back-end Mythbuntu setup. This Zotac ZBox ID 45 Plus is working well for OTA recording with the Silicondust HD Homerun Plus using the current Mythbuntu 14.04 version. I bought this used on Amazon for ~ $360 USD. I had 8Gb RAM available from my notebook upgrade, so that is what I used. If you'll be buying new, I recommend buying the bare-bones version and getting a larger HDD and 2 RAM cards to total 4GB or more memory. Use both RAM slots = faster RAM access.

**Hardware**
Product Name 	ZBOX ID45 Plus

**Motherboard:**
Chipset - Intel NM77 Express

**CPU** 	Intel Core i3 3227U (dual-core, 1.9 GHz)
Socket 	N/A (integrated CPU)

**RAM:**
Memory Type 	DDR3
Memory Speed 	1600 MHz
Slots 	2 x 204-pin SO-DIMM
Capacity 	4GB (up to 16GB)
Expansions
Expansion Slots 	N/A

**Video Card:**
GPU 	NVIDIA GeForce GT 640 w/2GB DDR3
3D API
DirectX 	DirectX 11.2 (feature level 11_0)
OpenGL 	OpenGL 4.4

**Sound Card:**
onboard Audio
Analog 	Stereo Output
Digital 	8-ch via HDMI

**HD:**
Storage
mSATA Solid State Drive (OS)      60GB
SATA Hard Drive (Files)	500GB 5400RPM HDD

**Remote:** Logitech wireless keyboard k400

**Tuners:** Silicondust HD Homerun Plus

**Other Information:**
Networking
Ethernet 	2 x 10/100/1000Mbps
WiFi 	802.11ac + Bluetooth 4.0 - Intel Dual-Band 3160 802.11ac 1x1

Optical Drive 	external USB generic DVD R/W
Memory Card Reader 	4-in-1 (MMC/SD/SDHC/SDXC)
Ports
DVI 	1 (dual-link)
HDMI 	1
DisplayPort 	N/A
SATA 	2 (1 SATA 6.0 Gb/s, 1 mSATA 3.0 Gb/s)
eSATA 	N/A
IDE 	N/A
PS2 	N/A
Serial Port 	N/A
USB Ports 	4 USB 3.0 (1 on top, 1 front, 2 on back panel)
Firewire 	N/A
Cooler
Cooler 	Smartfan
Form Factor
Form Factor 	mini-PC
OS Compatibility
Windows 	User installed (Windows 7 and 8 ready) *and Ubuntu/Mythbuntu*
General
SLI Supported 	N/A
Maximum Resolution 	N/A
Other
Graphics Output 	1 DVI / 1 HDMI supporting up to 4k resolution
Packaging
Content 	1 x ZOTAC ZBOX ID45 Plus 2 x WiFi antenna 1 x VESA mount 4 x Mounting screws 1 x Stand 1 x DVI-to-VGA adapter 1 x AC adapter 1 x Power cord 1 x Warranty card 1 x User manual 1 x Quick Install Guide 1 x Driver disc

**Country:** USA
**TV provider:** OTA
**TV signal type:** us-bcast
**Mythbuntu Version:** 0.27+

**Performance**
Picture quality is good using the Nvidia GeForce GT640 video card (UPDATE: Picture-in-picture with 2 simultaneous 1080p live-tv stations seems to cause stutter. Lesser resolutions not so much).
This seems to make a good HTPC for me.

Mythbuntu 14.04 version 0.27 setup notes for Zbox ID45

Installation
	Boot - use *noapic* boot option:
			*F6* at boot menu (not needed for 14.04.2)
	Partition    60 GB SSD ext4 as root
                        500 Gb HDD &#8211;  JFS as /var/lib/mythtv &#8211; using JFS instead of ext4 eliminated playback judder.

Setup
	Disable tap-to-click on Logitech wireless keyboard 400k:
		*Fn+left-click* (keyboard not OS dependent)	

	Fix DVD error message: &#8220;failed to open device /dev/dvd&#8221;  (bug #1323777)
		Frontend Menu: Setup>Media Settings>Video Settings>DVD Drive
			change: */dev/dvd* to */dev/sr0*
	Note: bug fixed in systemd (208-7ubuntu4) utopic

	Fix missing network icon in taskbar
		In Terminal ```
 sudo gedit /etc/xdg/autostart/nm-applet.desktop 
```
			Go down to Exec line and change the entry from:
				*nm-applet* to *dbus-launch nm-applet*
		Save the file and reboot.
		(This made it trivially easy to manage the wireless card;  i.e. change WiFi networks)

---

### Post by novellahub on 2015-01-22
Low power Mythtv frontend / backend combo.  Processor has a TDP of 10 watts.  I used the Cooler Master HAF 912 case and used two Thermaltake 200mm fans to cool. I installed two PCI-Express SIL3132 SATA II Raid controler cards (2 port) since motherboard only comes with 2 SATA ports. The SSD has the OS installed (EXT4 file system) and the recordings are on 4 separate mechanical hard drives (XFS file systems). The power supply used is a Corsair CX430.

_**Hardware**_
**Motherboard:** Asrock Q1900M
**CPU:** Intel Celeron J1900 Quad Core
**RAM:** G.Skill 4GB (2 x 2GB) 240-Pin SDRAM DDR3 1333 (PC3 10600)
**Video Card:** Onboard Intel
**Sound Card:** N/A (Audio via HDMI)
**HD:** Silicon Power Slim S60 120GB Sata III SSD,Seagate 2TB drive, 2 X SAMSUNG 2TB 5400 RPM SATA, WD Green WD40EZRX 4TB SATA drive
**Remote:** Microsoft MCE
**Tuners:** HDHR Prime X 2
**Country:** United States (Minneapolis / St. Paul Metro area)
**TV provider:** Comcast QAM
**TV signal type:** HDTV (Panasonic VIERA TC-P42X1)

_**Performance**_
Fresh install of Mythbuntu 14.04 LTS as a master backend/frontend. Migrated recordings from backup of older Mythbuntu 12.04 LTS machine. 

Machine boots in 10 seconds with the SSD.  CPU load of mythfrontend playback is about 10 to 14% with VAAPI enabled.  Load of Mythbackend is about 20 to 29% when all tuners are active.  I had to unmute the SPDIF output in alsamixer to enable sound for HDMI.

---

### Post by novellahub on 2015-02-11
Low power Mythtv frontend.  I set it up using a bootable 1 GB USB drive imaged with Mythbuntu 14.04.1 (Pendrive Linux Universal installer) and let the Mythbuntu do the default partitioning of the 32gb eMMC drive.

_**Hardware**_
**Motherboard**: ECS Liva 32GB 
**CPU**: Intel Bay Trail-M Celeron N2807
**RAM**: 2GB onboard RAM
**Video Card**: Onboard Intel
**Sound Card**: N/A (Audio via HDMI)
**HD**: On Board 32GB eMMC drive
**Remote**: Rii Mini Keyboard / Mouse Combo
**Tuners**: None
**Country**: United States (Minneapolis / St. Paul Metro area)
**TV provider**: Comcast QAM
**TV signal type**: HDTV 

Performance

Machine boots in 15 - 20  seconds with the on board 32GB eMMC drive. CPU load of mythfrontend playback is about 10 to 25% with VAAPI enabled. I had to unmute the SPDIF output in alsamixer to enable sound for HDMI.  

Did software upgrade / tweeks as noted here:

[http://samiux.blogspot.com/2014/07/howto-ecs-liva-mini-pc-kit-on-ubuntu.html](http://samiux.blogspot.com/2014/07/howto-ecs-liva-mini-pc-kit-on-ubuntu.html)

---

### Post by Dartr on 2015-02-12
**Combined FE/BE**

**Hardware**

**System:** ZOTAC SYSTEM ZBOX-ID86-U 
**CPU:** INTEL ATOM D25 (integrated in ZBOX)
**RAM:** G.SKILL 4GB (2 x 2GB) 204-Pin DDR3 SO-DIMM DDR3
**Video Card:** Onboard NVIDIA GeForce GT 610
**Sound Card:** Onboard 8 channel via HDMI
**OS HDD:** OCZ ARC 100 ARC100-25SAT3-120G 2.5" 120GB SATA III
**Recorder HDD: **Western Digital USB 1TB external
**Remote:** Logitech Harmony 700 + Flirc USB adapter
**Network:** Onboard LAN (WiFi also works fine)
**Tuners:** Silicondust HD Homerun on LAN
**Country:** US
**TV provider:** Antenna
**TV signal type: **8-VSB ATSC
**Playback quality:** VDPAU High
**TV/Monitor:** Panasonic 55GT50 Plasma TV
**TV connection: **HDMI
**OS: **Xubuntu 14.04 x64 base install + MythTV


**Performance**

This is a nearly silent and but somewhat warm-running box.

Load averages are very low. Never skips a beat with 2 1080i simultaneous recordings. I don't know that I've tried watching one while recording two, but have watched one while recording one. On-the-fly automatic comm flagging works well too.

Basic functions work pretty much out of the box. Had to add Nvidia drivers, program FLIRC to work with Harmony remote, and relocate the recordings directory to the external drive.

Great build, all in all.

---

### Post by wpcprez on 2015-12-10
[COLOR=#000000][INDENT]**Combined FE/BE**

**Hardware**

**System:** Custom
**CPU:** i3-2100
**RAM:** 8GB DDR3
**Video Card:** EVGA NVIDIA GeForce GTX 950 SC
**Sound Card:** Onboard
**OS HDD:** OCZ 120GB SATA III SSD
**Recorder HDD: **Toshiba 4TB USB 3.0 External
**Remote:** Generic Radioshack Gamer remote + MCE IR Receiver
**Network:** Onboard Gigabit
**Tuners:** Ceton PCIe InfiniTV4
**Country:** US
**TV provider:** Verizon Fios 
**TV signal type: **Cable Card
**Playback quality:** VDPAU High
**TV/Monitor:** RCA 65" 4K
**TV connection: **HDMI
**OS: **Mythbuntu 14.04


**Performance**
4K@60fps via VDPAU is nice. Everything runs smoothly.

[/INDENT]
[/COLOR]

---

### Post by bswarm2 on 2016-03-03
Hardware: Lenovo M53 Tiny
Motherboard: Aptio CRB
CPU: Intel Pentium J2900
RAM: 8Gb
Video Card: Integrated Intel Bay Trail 
Sound Card: Integrated HDA Intel PCH
HD: WD10J31X
Country: USA
Ubuntu Version: Ubuntu Gnome 14.04.4 64bit (Dual boots with Windows 10)
Kernel 4.2.0-32

Performance: System was freezing up (multiple times per day) in Ubuntu using either kernel v3 or v4, but not in Windows. After setting the bios CPU Max C-state to C1 it has been stable, no freeze ups at all.

Edit: Just noticed this was a Mythbuntu thread, oops.

---

### Post by 4ps4all on 2016-04-03
I have used RTL2832u DVB-USB-sticks with mythbuntu 140401, 140402, 140403 (always latest mythtv from mythbuntu ppa repository). These DVB-Usb-sticks work well with kernel 3.19, well detected with Mythtv-backend setup.

With mythbuntu 14.04.04 instead there's a driver regression(or what else). With kernel 4.2 and kernel 4.4 is not possible to find any channels in "INPUT CONNECTION" of mythtv-backend setup. Scannin channels do not give any channels found.

Only installing kernel 3.19 in mythbuntu 14.04.04 the "RTL2832u DVB-USB-sticks" works again(always latest mythtv from mythbuntu ppa repository).

I have found some info:
[https://bugzilla.kernel.org/show_bug.cgi?id=103391](https://bugzilla.kernel.org/show_bug.cgi?id=103391)
I think the bug in the kernel is yet present

---

### Post by vidtek on 2016-04-09
Using latest Xenial 16.04
tony@linuxmint:~$ more /etc/*-release
::::::::::::::
/etc/lsb-release
::::::::::::::
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu Xenial Xerus (development branch)"
::::::::::::::
/etc/os-release
::::::::::::::
NAME="Ubuntu"
VERSION="16.04 (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"                                                                                     
SUPPORT_URL="http://help.ubuntu.com/"                                                                                 
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"                                                                    
UBUNTU_CODENAME=xenial 

TBS 6205 quad tuner works 
Hauppauge 2210 dual tuner works
Using efi on old Gigabyte z68 UDB4 16gbram i7:
Mythtv .28 works
Brother MFC-885CW multifunction works well over wireless, printing worked well after Brother script
was run, but xsane had to have the directory /usr/lib64/sane   copied to  /usr/lib
before it would wirelessly scan.

KDE connect works well with my Pipo T9S tablet and ZTE Axon Elite phablet.

Having problems with mythweb though, just blank page.

Tony

---

### Post by gottabefoss on 2016-04-17
AMD 5350
MSI motherboard
WD Blue HD
8 gigs ram
HD Homerun Connect

Running 14.04.04 w/LTS enablement stack, mythtv 0.28, and Kodi Jarvis.

Everything works well. Video through VGA, audio through HDMI.

There's enough horsepower to record several HD shows at once w/realtime commercial detection.

Running Kodi in standalone mode, because if running in desktop mode, there's a bug in XFCE desktop that if you turn the tv & receiver off, it forgets about the HDMI connection when you turn them back on.

---

### Post by mtbdrew on 2016-06-18
Remote FE running on Ubuntu 16.04 desktop with following hardware:

ASRock N3150B-ITX Intel Quad-Core
4GB Crucial 
Asus GT630 supports 7.1 over HDMI 
Kingston 60GB SSD 

Both MB and Video card are fanless installed in Antec Fusion Remote Black case. Controlled with Lenovo N5902.

---

