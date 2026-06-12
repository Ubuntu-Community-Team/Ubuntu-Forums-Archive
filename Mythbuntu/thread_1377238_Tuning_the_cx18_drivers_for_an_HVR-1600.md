---
title: "Tuning the cx18 drivers for an HVR-1600"
date: 2010-01-10
forum: Mythbuntu
---

### Post by johnlatz on 2010-01-10
I have nearly given up attempting to use the digital half of my card, as  the resulting files are so corrupted with artifacts (temporarily hung  frames, blocky compression artifacts, audio skipping and dropouts, tearing). 

I get plenty of dropouts in the dmesg file, seem to be a lot of  interupts in /proc/interupts: 
```
$ dmesg | grep cx18 
[1083852.869439] cx18-0: Skipped encoder MPEG, buffer 45, 62 times - it  must have dropped out of rotation 
[1084342.826947] cx18-0: Skipped encoder MPEG, buffer 58, 61 times - it  must have dropped out of rotation 
[1084861.748387] cx18-0: Skipped encoder MPEG, buffer 27, 62 times - it  must have dropped out of rotation 
[1086389.267179] cx18-0: Skipped encoder MPEG, buffer 31, 62 times - it  must have dropped out of rotation 
[1088695.275839] cx18-0: Could not find buf 71 for stream TS 
[1088695.277418] cx18-0: Skipped TS, buffer 75, 16 times - it must have  dropped out of rotation 
[1091896.370754] cx18-0: Skipped encoder MPEG, buffer 30, 62 times - it  must have dropped out of rotation 
[1107387.381003] cx18-0: Skipped encoder MPEG, buffer 25, 62 times - it  must have dropped out of rotation 
[1107651.839600] cx18-0: Skipped encoder MPEG, buffer 3, 62 times - it  must have dropped out of rotation 
[1109352.777731] cx18-0: Skipped encoder MPEG, buffer 1, 62 times - it  must have dropped out of rotation 
[1109451.274455] cx18-0: Skipped encoder MPEG, buffer 46, 62 times - it  must have dropped out of rotation 
[1109624.811614] cx18-0: Skipped encoder MPEG, buffer 12, 62 times - it  must have dropped out of rotation 
[1162908.934027] cx18-0: Skipped encoder MPEG, buffer 9, 62 times - it  must have dropped out of rotation 
[1165354.241609] cx18-0: Skipped TS, buffer 92, 31 times - it must have  dropped out of rotation 
[1165814.275797] cx18-0: Skipped encoder MPEG, buffer 28, 61 times - it  must have dropped out of rotation 
[1165832.087816] cx18-0: Could not find buf 46 for stream encoder MPEG 
[1165833.547558] cx18-0: Skipped encoder MPEG, buffer 53, 62 times - it  must have dropped out of rotation 
[1165836.370859] cx18-0: Could not find buf 92 for stream TS 
[1166092.520151] cx18-0: Could not find buf 19 for stream encoder MPEG 
[1166092.520877] cx18-0: Skipped encoder MPEG, buffer 45, 12 times - it  must have dropped out of rotation 
[1166480.766293] cx18-0: Could not find buf 13 for stream encoder MPEG 
[1166482.073408] cx18-0: Skipped encoder MPEG, buffer 43, 62 times - it  must have dropped out of rotation 
[1166941.693512] cx18-0: Could not find buf 86 for stream TS 
[1166943.101497] cx18-0: Skipped encoder MPEG, buffer 5, 62 times - it  must have dropped out of rotation 
[1167822.880947] cx18-0: Skipped encoder MPEG, buffer 49, 62 times - it  must have dropped out of rotation 
[1169928.649813] cx18-0: Skipped encoder MPEG, buffer 36, 62 times - it  must have dropped out of rotation 
[1170047.032633] cx18-0: Skipped encoder MPEG, buffer 54, 62 times - it  must have dropped out of rotation 
[1173351.617178] cx18-0: Skipped encoder MPEG, buffer 0, 61 times - it  must have dropped out of rotation 
[1174388.090390] cx18-0: Could not find buf 66 for stream encoder MPEG 
[1174389.527638] cx18-0: Skipped encoder MPEG, buffer 8, 62 times - it  must have dropped out of rotation 
[1174909.105658] cx18-0: Skipped encoder MPEG, buffer 37, 62 times - it  must have dropped out of rotation 
[1175627.758500] cx18-0: Skipped encoder MPEG, buffer 36, 62 times - it  must have dropped out of rotation 
[1175710.138838] cx18-0: Skipped encoder MPEG, buffer 17, 62 times - it  must have dropped out of rotation 
[1176506.006066] cx18-0: Skipped encoder MPEG, buffer 2, 62 times - it  must have dropped out of rotation 
[1177024.357829] cx18-0: Skipped encoder MPEG, buffer 40, 62 times - it  must have dropped out of rotation 
[1181721.031104] cx18-0: Skipped encoder MPEG, buffer 15, 62 times - it  must have dropped out of rotation 
[1182411.178933] cx18-0: Skipped encoder MPEG, buffer 40, 60 times - it  must have dropped out of rotation 
[1183827.059070] cx18-0: Skipped encoder MPEG, buffer 61, 62 times - it  must have dropped out of rotation 
[1186713.338763] cx18-0: Skipped encoder MPEG, buffer 61, 62 times - it  must have dropped out of rotation 
[1186816.938672] cx18-0: Skipped encoder MPEG, buffer 18, 61 times - it  must have dropped out of rotation 
[1195254.908566] cx18-0: Skipped encoder MPEG, buffer 58, 62 times - it  must have dropped out of rotation 
[1195303.856851] cx18-0: Skipped encoder MPEG, buffer 11, 62 times - it  must have dropped out of rotation 
[1196372.366987] cx18-0: Skipped encoder MPEG, buffer 25, 62 times - it  must have dropped out of rotation 
[1196641.532111] cx18-0: Skipped encoder MPEG, buffer 30, 62 times - it  must have dropped out of rotation 
[1251611.545998] cx18-0: Skipped encoder MPEG, buffer 31, 62 times - it  must have dropped out of rotation 
[1253886.222692] cx18-0: Skipped encoder MPEG, buffer 36, 62 times - it  must have dropped out of rotation 
[1257223.221794] cx18-0: Could not find buf 86 for stream TS 
[1257224.653934] cx18-0: Skipped encoder MPEG, buffer 20, 62 times - it  must have dropped out of rotation 
[1257393.485154] cx18-0: Skipped encoder MPEG, buffer 59, 62 times - it  must have dropped out of rotation 
[1258595.379322] cx18-0: Skipped encoder MPEG, buffer 5, 62 times - it  must have dropped out of rotation 
[1259106.391892] cx18-0: Skipped encoder MPEG, buffer 47, 62 times - it  must have dropped out of rotation 
[1259175.023492] cx18-0: Skipped encoder MPEG, buffer 13, 62 times - it  must have dropped out of rotation 
[1259561.943918] cx18-0: Skipped encoder MPEG, buffer 12, 62 times - it  must have dropped out of rotation 
[1260000.948109] cx18-0: Skipped encoder MPEG, buffer 52, 62 times - it  must have dropped out of rotation 
[1260375.258830] cx18-0: Fell behind! Ignoring stale mailbox with   inconsistent data. Lost buffer for mailbox seq no 26574599 
[1260376.665371] cx18-0: Skipped encoder MPEG, buffer 50, 62 times - it  must have dropped out of rotation 
[1261324.673928] cx18-0: Skipped encoder MPEG, buffer 51, 62 times - it  must have dropped out of rotation 
[1262597.882338] cx18-0: Skipped encoder MPEG, buffer 28, 62 times - it  must have dropped out of rotation 
[1262883.238706] cx18-0: Skipped encoder MPEG, buffer 28, 62 times - it  must have dropped out of rotation 
[1263114.471936] cx18-0: Skipped encoder MPEG, buffer 7, 62 times - it  must have dropped out of rotation 
[1263429.680607] cx18-0: Skipped encoder MPEG, buffer 36, 62 times - it  must have dropped out of rotation 
[1282684.103627] cx18-0: Skipped encoder MPEG, buffer 18, 62 times - it  must have dropped out of rotation 
[1282986.844672] cx18-0: Skipped encoder MPEG, buffer 23, 62 times - it  must have dropped out of rotation 
[1300715.020705] cx18-0: Skipped TS, buffer 70, 31 times - it must have  dropped out of rotation 
[1301091.990354] cx18-0: Could not find buf 70 for stream TS 

``````
~$ cat /proc/interrupts 
          CPU0       CPU1 
 0:         24          0   IO-APIC-edge      timer 
 1:        169      41936   IO-APIC-edge      i8042 
 3:          0          1   IO-APIC-edge 
 4:          0          2   IO-APIC-edge 
 6:          0          4   IO-APIC-edge      floppy 
 7:          1          0   IO-APIC-edge      parport0 
 8:          0          0   IO-APIC-edge      rtc0 
 9:          0          0   IO-APIC-fasteoi   acpi 
12:         13      12157   IO-APIC-edge      i8042 
14:     134111   51936820   IO-APIC-edge      pata_amd 
15:          0          0   IO-APIC-edge      pata_amd 
18:     139374   68667065   IO-APIC-fasteoi   ohci1394, cx18-0 
19:      90086   51915174   IO-APIC-fasteoi   ath 
20:      67122    8088594   IO-APIC-fasteoi   ohci_hcd:usb3, HDA Intel 
21:     144539   45360088   IO-APIC-fasteoi   ehci_hcd:usb2, nvidia 
22:          0          0   IO-APIC-fasteoi   ehci_hcd:usb1 
23:          0          0   IO-APIC-fasteoi   ohci_hcd:usb4 
28:      77424   14033077   PCI-MSI-edge      ahci 
29:      39083    7297307   PCI-MSI-edge      eth0 
NMI:          0          0   Non-maskable interrupts 
LOC:  319377794  274871019   Local timer interrupts 
SPU:          0          0   Spurious interrupts 
CNT:          0          0   Performance counter interrupts 
PND:          0          0   Performance pending work 
RES:   46144351   27829975   Rescheduling interrupts 
CAL:    1436063     329818   Function call interrupts 
TLB:    1117907    1100388   TLB shootdowns 
TRM:          0          0   Thermal event interrupts 
THR:          0          0   Threshold APIC interrupts 
MCE:          0          0   Machine check exceptions 
MCP:       5229       5229   Machine check polls 
ERR:          1 
MIS:          0 

```
Can someone help me troubleshoot this? I have a sample video file I can provide to show the effects.  I ONLY use the Myth system to record, I never watch live video on it.

Lastly, I'm using Mythbuntu 9.10.  Used to be on Knoppix R5.5, but I  couldn't get R6(0.22) to install on my system, and I wanted to try 0.22.  Have  had problems with this card under both distros...

---

### Post by klc5555 on 2010-01-10
> **johnlatz said:**
> I have nearly given up attempting to use the digital half of my card, as  the resulting files are so corrupted with artifacts (temporarily hung  frames, blocky compression artifacts, audio skipping and dropouts, tearing). 
...

Can someone help me troubleshoot this? I have a sample video file I can provide to show the effects.  I ONLY use the Myth system to record, I never watch live video on it.

Lastly, I'm using Mythbuntu 9.10.  Used to be on Knoppix R5.5, but I  couldn't get R6(0.22) to install on my system, and I wanted to try 0.22.  Have  had problems with this card under both distros...

The 1600 has signal strength issues in QAM, compounded by the state of the standard cx18 driver.

There have been recentish developments in this driver (at linuxtv.org) that haven't made it yet into the standard kernel tree. And, moreover, Devin Heitmuller has developed a tweaked cx18 driver, the source for which is available at [http://www.kernellabs.com/hg/~dheitmueller/hvr-1600-perf-2](http://www.kernellabs.com/hg/~dheitmueller/hvr-1600-perf-2)

Compiling and using this QAM-optimized cx18 driver may not solve all the issues with QAM and the 1600, but through using the tweaked driver, QAM on the 1600 should suck less.

---

### Post by johnlatz on 2010-01-10
> **klc5555 said:**
> QAM on the 1600 should suck less.

Less than a glaring endorsement of the hardware...

Is there a consensus of opinion as to which the better hybrid cards are?  I had such good luck with my PVR-350 (until I physically broke the coax connector - long story), I loved the hardware MPEG-2 encoder, I just assumed Hauppauge is a quality supplier.

Is that not the case for digital?  I would have thought that digital was simply a simple pipe - take the input signal and save to disk...

The HVR-2250 looks like good hardware from the specs, but no analog driver AFAIK.  The pcHDTV-5500 seems to have similar complaints about QAM signal strength attenuation.  So who's got a good hybrid card on the market today?

---

### Post by johnlatz on 2010-01-11
To get Devin's drivers to compile, I had to edit v4l/.config to change
```
CONFIG_DVB_FIREDTV=m
```to
```
CONFIG_DVB_FIREDTV=n
```On reboot, strange thing - my data disk disappeared.  df didn't show it, mount resulted in:
mount: /dev/sdb3 already mounted or /myth busy

Eventually cleaned up with a fsck command - dunno if the issue was related or simply coincidental, I suspect the latter.

Anyway, I'll see how this works tomorrow,gotta put the kids to bed...

---

### Post by klc5555 on 2010-01-11
> **johnlatz said:**
> Less than a glaring endorsement of the hardware...

Is there a consensus of opinion as to which the better hybrid cards are?  I had such good luck with my PVR-350 (until I physically broke the coax connector - long story), I loved the hardware MPEG-2 encoder, I just assumed Hauppauge is a quality supplier.

Is that not the case for digital?  I would have thought that digital was simply a simple pipe - take the input signal and save to disk...

The HVR-2250 looks like good hardware from the specs, but no analog driver AFAIK.  The pcHDTV-5500 seems to have similar complaints about QAM signal strength attenuation.  So who's got a good hybrid card on the market today?

I don't know about a consensus. However, I have 2 1600s which I relegate to catching the the converted analog output from Comcast DTAs/STBs, at which activity they excel. They are too unreliable for my purposes on QAM, even when hooked to a good line-drop amp, and I eventually gave up on them for that. 

I also use a motley assembly of 3 pchdtv5500s, 1 new-style AverMedia A180 and 1 old-style AverMedia A180. I have found them all to be excellent for QAM. The only issue I've ever encountered with the 5500, once the analog driver finally became reliable with kernel 2.6.26, is that on QAM it is sufficiently sensitive that sometimes very strong QAM signals may overload it a bit. The 5500s are about as close to "just works out of the box" as I've ever encountered in Linux.

The AverMedias are also great on QAM. But the new-style has no analog at all, while the analog on the old-style is fairly useless. Plus a tad tricky to set up. But overall good and perfectly useful digital tuners, and I'm glad I purchased them.

---

### Post by the_pod on 2010-01-11
> **klc5555 said:**
> The 1600 has signal strength issues in QAM, compounded by the state of the standard cx18 driver.

There have been recentish developments in this driver (at linuxtv.org) that haven't made it yet into the standard kernel tree. And, moreover, Devin Heitmuller has developed a tweaked cx18 driver, the source for which is available at [http://www.kernellabs.com/hg/~dheitmueller/hvr-1600-perf-2](http://www.kernellabs.com/hg/~dheitmueller/hvr-1600-perf-2)

Compiling and using this QAM-optimized cx18 driver may not solve all the issues with QAM and the 1600, but through using the tweaked driver, QAM on the 1600 should suck less.

I'll vouch for these drivers.  I too was at wits end.  Devin's drivers pretty much removed any problems I have w/ the digital side of my 1600.  (I don't use the analog). Someone should buy this guy a nice steak at the Sizzler or something.

---

### Post by johnlatz on 2010-01-12
So I tried to pay attention when I played Caillou for the kids tonight - the situation has improved markedly: went from "this is barely tolerable" to only one noticeable dropout.  Thanks for pointing me in the right direction.

On a side note, I'm currently watching an analog channel straight off the coax (splitter upstream of the Mythbox), and I just caught a flash of compression artifacts - so some of the problems I'm having are farther upstream TW's pipe than just my card.

But I'm paying $19/month for analog and clear QAM, and I really don't want to jump to $1000/year for satellite....

---

### Post by klc5555 on 2010-01-12
Depending on how you've got the line split and the quality of your coax cabling, the usual next step would be to slip a reasonable quality $30-$40-ish line-drop amp upstream of your splitter(s). Motorola 484095-001-00 or similar.

If you happen to have say a 4, 6, or 8-way split, useful amplified splitters are also to be had in the $40 range.

Cheers!

---

### Post by Nausser on 2010-02-12
I've recently built a Mybuntu 9.10 box front/backend system. No other front-ends, not yet anyway. For some reason my research at the time led me to purchase the HVR-1600(the one without the remote). First thing I tried to get things working is follow the steps on the mythtv.org/wiki page which made the card completely useless.

I did a complete reinstall due to a bad hard drive and tried the backend setup without any pre-config of any drivers or modules. The analog works wonderfully; however, the QAM cable does not. I want to get the 5.1, 12.1, etc channels that I can tune directly with my TV's built in tuner. (It looks great on the TV)

I ran the install according to the readme in the driver download.

make
make install

Afterwards, I rebooted and still no channels found under digital. I also wanted to note that the Mythtv wiki page instructions for the HVR-1600 indicate there is a setting spec just before channel scanning for "." or "-" I think. I do not have this option at all on my Mythbuntu backend setup.

After noting that nothing has changed I ran:

lspci -v | grep -A8 cx18

and returned,

Kernel driver in use: cx18
	Kernel modules: cx18

which is no different than before I ran Devin's new driver.

Any other users out there have any luck with Mythbuntu 9.10 and the HVR-1600? I've been at this for three days non-stop.(A little sleep now and then)

Thanks!

**UPDATE**

I've run Devin's drivers/firmware as root instead of sudo and seemed to have luck with the installation until I restarted. My card now seems to be missing altogether in the backend setup as no "Probed" info is acquired. When I run the "lspci -v | grep -A8 cx18" command, I get nothing at all which is right where I was the last time I did a full reinstall after implementing the drivers/firmware indicated on the mythtv.or/wiki HVR-1600 page.

So... my problem is getting worse, not better.

Please advise...

---

### Post by dazer26 on 2010-02-12
I'v only tried to use the digital half of the 1600 once, and didn't have much luck, mostly cause of a cheap antenna and no digital towers close to where I live.  In the 9.x version of ubuntu the analogue half works out of the box with mythtv.

As a side note, ha anyone found another tv program that works with the 1600?  I love mythtv, but most of the time I just wanna watch tv, so I don't use 99% of the features.

---

### Post by johnlatz on 2010-02-14
[klc5555]("http://ohioloco.ubuntuforums.org/member.php?u=533176")
I took your advice, bought a Motorola BDA-S2 amp/splitter, and installed it today.  Unfortunately, didn't help my HVR-1600 performance - when I attempted to watch the Olympics this afternoon live, I'm still getting audio "zaps" and blocky compression artifacts and ghosting.

The good thing is, I now know how to wire up a power outlet, I didn't overload my cable modem, and my VOIP did seem just a little bit clearer when I called my grandmother today.

The bad things are that my programming skills are skewed exclusively toward scientific computing (FORTRAN and Matlab coding; though I can deconstruct and adapt the occasional Perl and Python script if need be), and I know nothing about driver programming.  So there's not much that I think I could add to Devin's efforts to improve the HVR-1600 drivers.  Personally, pretty frustrating...

johnlatz

---

### Post by johnlatz on 2010-02-14
Nausser,

I'm still having issues in troubleshooting my HVR-1600, but it sounds like I'm at least further along than you - so maybe I can help.

Two things burned me early on when I was trying to configure my card - the first is that when I went into the Config screen, I couldn't find the PVR-150/ivtv config option in the screen.  I eventually hand typed in the presumed card, and then things went smoothly.  But that is for the analog half of the card, not the digital half.  Doesn't sound as if this is your issue, but still <http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Backend_Setup>

As far as finding the digital channels, I had originally tried to deal with this card under Knoppmyth R5.5 (myth 0.21-fixes).  Under that distro, it was suggested to do a manual scan for channels  At the time, I was pointed to this:  <http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_%28For_ATSC/QAM_Tuner_Cards_--_USA/Canada%29#Scanning_for_channels>.

My recollection is that I found a slightly newer and slightly different guide on how to scan for channels, something that accessed the files found in /usr/share/dvb/atsc/, but for the life of me I'm not finding it on google right now (see <http://www.gossamer-threads.com/lists/mythtv/users/328828>?).  The thing is - once I found my digital channels, I ported my channels.conf file over to my Mythbuntu install and used it direct.  I hit SiliconDust every so often <http://www.silicondust.com/hdhomerun/channels_us>, and there aren't any new clear QAM channels popping up that I care about., so I've not had to do this exercise in a year or so.

So, I hope this at least gives you a direction to head down.

---

### Post by kpl388 on 2010-02-15
I think I may be having a similar problem to you. Devin Heitmueller and Andy Walls over on the ivtv-users mailing list were able to provide me with tons of valuable information and things to try. Unfortunately, I am still getting the occasional video glitches accompanied by an audio buzz. Still, some of the tests we've been through might help you troubleshoot your problem as well. Keep us updated if you figure anything out.

Best, 
Kyle

ps. here's the link to that thread [http://www.gossamer-threads.com/lists/ivtv/users/40784](http://www.gossamer-threads.com/lists/ivtv/users/40784)

---

### Post by johnlatz on 2010-03-28
What drivers are in 2.6.31-20-generic?  I think I read on one of the links that [klc5555]("http://ubuntuforums.org/member.php?u=533176") provided that Devin Heitmuller basically said his changes were merged, and there is no longer a need to specifically compile and install his betas.  Does anyone know if that is true?

I ask because under -19 & the beta drivers, I still got artifacts, and under -20 and stock drivers, same issue:
```
$ grep cx18 syslog
Mar 28 08:19:59 localhost kernel: [652464.576282] cx18-0: Skipped encoder MPEG, buffer 56, 62 times - it must have dropped out of rotation
Mar 28 08:54:50 localhost kernel: [654556.245515] cx18-0: Skipped encoder MPEG, buffer 18, 62 times - it must have dropped out of rotation
Mar 28 10:30:28 localhost kernel: [660293.786962] cx18-0: Skipped encoder MPEG, buffer 5, 62 times - it must have dropped out of rotation
Mar 28 10:43:04 localhost kernel: [661050.315319] cx18-0: Skipped encoder MPEG, buffer 51, 62 times - it must have dropped out of rotation
Mar 28 10:44:16 localhost kernel: [661121.388111] cx18-0: Skipped encoder MPEG, buffer 58, 62 times - it must have dropped out of rotation
```I know I'm peeing into the wind on this one and I should just bite the bullet and buy a card with better Linux support - but I thought I'd bump anyway...

---

### Post by Lepy on 2010-03-30
I'd like the know the answer to this too. I update the drivers every few days, but I'm not sure if I should stick with devin's or the mainline v4l. I read through the link kpl388 posted, and I have basically the exact same problem and symptoms. 

I wrestled with it, attenuated my signal, watched ber and unc, bypassed house lines by hooking the HVR directly at the box. I had a cable tech come out and said I had about the best signal one could get. I tried multiple outlets and unplugged appliances thinking it might be electromagnetic interference. I finally gave up and will live with it until things get better (crosses fingers).

The digital side of the card is working ok now, but still has artifacts and pops on a few channels. There doesn't seem to be any rhyme or reason to when these pop up though as some shows recorded at the same time everyday may be almost perfect or full of artifacting/popping. I'm going to see if changing the qam_gain will help.

The analog side is much better though. I had a horrible static cross (see here: [http://i37.tinypic.com/14kbog2.jpg](http://i37.tinypic.com/14kbog2.jpg)) for a while, but mainly fixed it by running the coax through a few splitters. Now, only a few mid-number channels showcase this cross at a much more acceptable level. I'd still like to completely get rid of it though. Anyone seen similar behavior?

---

### Post by Lepy on 2010-03-31
Following kpl388, I set qam_gain (in v4l-dvb/v4l/cx18-dvb.c, line 64) to 0x01 (from 0x02) before compiling. This has resulted in exceptional results! 

Every channel used to squeak and pop (though some channels were pretty good from time to time), now almost every channel plays perfectly. I was able to record a digital program without some sort of error (e.g. [mpeg2video @ 0x7f836b2f7820]Missing picture start code) for the first time.

Doing a quick channel scan, I found that out of 29 channels I receive on the digital side, 2 had corrupt frames every few seconds, 2 resulted in completely non-functioning, god awful screeching squeaking green screens, and the remainder of the channels came through perfectly as far as I could tell. The tuner also never dropped failed and kicked me back to the menu (except when tuning to the two green screen channels).

So, going from all channels dropping frames as well as sometimes failing to tune, to 25 out of 29 working perfectly, I'm quite pleased.

---

### Post by scorptig on 2010-04-06
I have spent nearly 7 hours trying to get my HVR-1600 card to work, I find the instructions confusing, one page to another section, nothing seems concise as information.

Anyway LSMOD shows I have my CX18 installed, I still don't know what to do next, I am using Ubuntu 9.10 64 bit.

IF someone could start from the first step and go through every exact step, that would really help.

I use command line, that's not an issue, the compiling part,. I got errors, then I simply don't know what to do, it says supported by Kernel 2.6 & on, I really was hoping for an easier install.

So I am requesting UBUNTU list Every step to get this card going..

Thank you.

By the way I am right now Going to format my Ubuntu installation and start over from scratch !

---

### Post by Lepy on 2010-04-06
The HVR-1600 page of the mythwiki has been updated recently. It contains everything you need to know about the card and is much more straightforward than the previous revisions. It doesn't get any more step by step than this.

Find it here: [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

Your compilation errors most likely have to do with the firedtv module: 
"note: While in menuconfig, unless you have downloaded the entire kernel source, you will need to disable Multimedia support-->DVB/ATSC adapters --->FireDTV and FloppyDTV or build will fail"
Follow the menuconfig directions or edit "v4l-dvb/v4l/.config" and change CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n

---

