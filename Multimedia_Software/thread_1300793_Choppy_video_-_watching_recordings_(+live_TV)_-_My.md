---
title: "Choppy video - watching recordings (+live TV) - MythTV and others"
date: 2009-10-25
forum: Multimedia Software
---

### Post by javine on 2009-10-25
I am trying to get MythTV up and running and am having problems with choppy video, both in live TV and in playback. I am hoping it is just a settings issue, as I think the system should be up to it (details below). I've tried to provide lots of information about my system and what I've tried so far, but I'm very happy try anything else that you can recommend and to provide outputs of any tests. (I'm new to the whole Linux thing, but quite good at following instructions!)

I don't think the issue is specific to MythTV - playback is better in other software, but still not fully smooth. Setting up watching live TV directly through another piece of software is quite smooth. My understanding is that watching live TV through MythTV actually records it to and plays it back immediately, so it would be expected to behave at least as badly as watching a recording.

Thanks in advance for any help.
 

**System information:**

CPU - Dual Pentium 4 3GHz (output from CPUinfo below)
Memory - 2GB PC3200 Kingston
Hard drive - SATA. Approx 250GB, most of it free space
Tuner card - Nova DVB-T 500
Graphics - onboard (but the system is a Scaleo E, which is a Media Centre PC, so I would've thought they were up to the job). Intel 915 chip with a Chrontel CH7021A as a TV encoder. At the moment I'm using the VGA output and trying to get it running on a monitor before trying to get it hooked up to my TV.
Operating System - Ubuntu 9.04
MythTV - version 0.21.0. Frontend and Backend running on same machine.
Video type - standard definition DVB-T (UK)

**Drivers:**

System > Administration > Hardware Drivers shows "No proprietary drivers are in use on this system." The space where a list would be is blank, so it is not just a case of enabling them if they're needed. (Main, universe, multiverse, restricted and medibuntu repositories are all enabled.)


**Tests and symptoms**

I have been searching for information that might help track down the problem and these are some of the things I have tried so far. I'll include as much information as possible, both to help with the diagnosis of my problem, but also in case it's helpful for the next person suffering with these problems to be able to try out some of the tests I've done.

**** Playing back a recording on other software***

```
cd /var/lib/mythtv/recordings
xine 6230_20091025010000.mpg
```

(I have also tried "mplayer" and "vlc" instead of "xine" and a few different .mpg recordings.)

Xine and VLC both play the recording more smoothly than the MythTV playback, but not perfectly. (Mplayer doesn't seem to be able to pick up the video stream and just plays the audio.)

I am pretty sure that the recording is OK, because the screen where you pick recordings to play back shows a small version playing which runs smoothly.

**** Checking the hard drive is using DMA***

One page I found suggested that a likely cause of this symptom is the HDD not using DMA. Using the hdparm command as below it looks like I'm using udma6. A quick search suggests that "UDMA" means "Ultra DMA", which I presume is at least as good as DMA.

```
sudo hdparm -i /dev/sda1

/dev/sda1:

 Model=WDC WD2500AAKS-00VSA0                   , FwRev=01.01B01, SerialNo=     WD-WMART1591067
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=488397168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode
```

**** Checking the system load***

Using the GUI (Gnome) System Monitor (System > Administration > System Monitor, "Resources" tab) shows that while playing a video in Xine CPU usage is about 60% (showing as CPU1 and CPU2 both at around that level). Memory usage is pretty constant at around 18% (0 bytes of a 5.8GiB swap being used).

Watching the same recording in MythTV the usage is a bit higher - CPU usage around 70% and memory at around 24%.

Using htop (which I admit to not being very clear about the use of) it looks like the bulk of the CPU usage is being allocated to X (around 40-50%), with a smaller amount (20-30%) actually due to the player (either xine or mythfrontend.real, depending on which I'm testing at the time), but these do fluctuate a lot in htop, and I'm not entirely what it indicates. The figures for the process usage in the System Monitor are a lot more stable, but that doesn't seem to show X.

These figures are high-ish, but they're not burying the needle, so my guess would have been that this isn't the problem, but I don't know.

**** Trying different video profiles***

In MythTV (Utilities / setup > Setup > TV settings > Playback) I have tried all of the profiles that come as default (Normal, Slim, CPU--, CPU++, CPU+, High Quality). I couldn't tell much difference - perhaps High Quality was even choppier than the rest, but there wasn't much obvious difference between the others.

**** Setting the video output plugin***

This was something I tried just following some instructions I found - I don't actually know what it's supposed to do.

```
gstreamer-properties
```

This opens the Multimedia Systems Selector. Under the Video tab I changed Default Output Plugin from "Autodetect" to "X Window System (No Xv)". Clicking Test made some test bars appear, which seemed to be the expecte behaviour, but it didn't seem to make any difference to the playback. I also tried the other option ("X Window System (X11/XShm/Xv)") - that failed on the test.

**** Examining the processor***

One page suggested checking the processor using the command below.

```
cat /proc/cpuinfo
```

The output seems to indicate that they are being recognised correctly, and are running a bit slower than their full 3GHz rating. I don't know if that's a problem, or if there's something in the rest of the information that is useful.

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 3
cpu MHz		: 2800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr
bogomips	: 5985.12
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 3
cpu MHz		: 2800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr
bogomips	: 5985.34
clflush size	: 64
power management:

```

That's about as far as I've got so far. Thanks in advance to anyone who can help point me in the right direction!

Thanks,
javine

---

### Post by Linuxgood on 2009-10-25
What is the setting for System -> Preferences -> Appearance -> Visual effects ? I had to turn the effecs off to get smooth playback in smplayer and vlc on my desktop computer.

---

### Post by javine on 2009-10-25
Visual effects are set to "None", which seems to be the simplest state already.

Thanks for the suggestion.

Thanks,
javine

---

