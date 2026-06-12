---
title: "Sound comes out of speakers even with headphones in"
date: 2010-08-03
forum: Multimedia Software
---

### Post by timinator94 on 2010-08-03
Hey all I have a msi vr630 with an alc888 soundcard. It has 4 slots see here "http://multimedia.agito.pl/image/700x700/0/notebooki/msi-vr630-213pl.185626.2.jpg". when i have my headphones plugged into any slots sound still comes out of my speakers... i found a fix once.. but that fix also disabled my 2nd headphone jack. I think it involved something like editing alsa-base or something... please help thanks!

Timinator94

---

### Post by timinator94 on 2010-08-03
Bump. Please Help!!

---

### Post by darkstarbyte on 2010-08-03
Its the crappy sound manager in kde I had the same problem I just reinstalled it and it worked fine.

---

### Post by timinator94 on 2010-08-04
Sorry I should have stated that im running ubuntu 10.04 x64 not kde my bad

---

### Post by justin43384 on 2010-08-04
same problem here please help because im goin on a plane trip soon

by the way im using 10.04

---

### Post by timinator94 on 2010-08-04
Bump. I really need to fix this:(

---

### Post by lidex on 2010-08-05
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=targa-2ch-dig 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

If that doesn't work try changing 
```
targa-2ch-dig
```
to
```
targa-dig
```

---

### Post by Donalt2010 on 2010-08-05
Thanks this helped me:)

---

### Post by timinator94 on 2010-08-07
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=targa-2ch-dig 
```Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

If that doesn't work try changing 
```
targa-2ch-dig
```to
```
targa-dig
```


HAHA thanks but now my built in mic doesnt work:p any ideas?

---

### Post by timinator94 on 2010-08-11
anybody know why???

---

### Post by Yellow Pasque on 2010-08-11
Well, here's the list of models for your codec. You may have to search or experiment to see which one works best for your laptop (try targa and targa-dig):
```
ALC882/883/885/888/889
======================
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  macmini3	Macmini 3,1
  mba21		Macbook Air 2,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  imac91	iMac 9,1
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m540r	Clevo M540R (6ch + digital)
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)
```

---

### Post by lidex on 2010-08-11
If everything works but the mic, make sure your options in 'Sound Preferences' and alsamixer are configured properly.
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab. Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by imfreak130 on 2010-08-12
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=targa-2ch-dig 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

If that doesn't work try changing 
```
targa-2ch-dig
```
to
```
targa-dig
```




THANK YOU.
I've been looking for a fix NONSTOP for 3 days.
I've tried over 10 different things, and this one simple line fixed it!
I'm running an HP G60-119-OM.

---

### Post by timinator94 on 2010-08-12
Ok thanks Ill try all of that today and let you know:)

---

### Post by evenrelation on 2010-08-12
Not working for me.

My processor is AMD not Intel. Does it matter?

---

### Post by imfreak130 on 2010-08-12
> **evenrelation said:**
> Not working for me.

My processor is AMD not Intel. Does it matter?



Shouldn't matter.
I have an AMD.

---

### Post by lidex on 2010-08-13
> **evenrelation said:**
> Not working for me.

My processor is AMD not Intel. Does it matter?
No. What matters is your sound controller and codec, both of which relate to your motherboard layout. You need to know your codec:
```
head -n 1 /proc/asound/card*/codec#*
```
as well as PC make and model and sometimes need the number of audio jacks (stacks), both analog and digital and number of audio channels supported.

---

### Post by timinator94 on 2010-08-18
output 0f 
head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC888

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040
 only one headphone jack works and mic still dosent work after enabling it in gnome-alsamixer
also tried changing to targa-2ch-dig and then nothing worked
PLEASE HELP!!:confused:

---

### Post by lidex on 2010-08-19
> **timinator94 said:**
> output 0f 
head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC888

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040
 only one headphone jack works and mic still dosent work after enabling it in gnome-alsamixer
also tried changing to targa-2ch-dig and then nothing worked
PLEASE HELP!!:confused:

How about:
```
3stack-dig
or
targa
```

---

### Post by timinator94 on 2010-08-20
> **lidex said:**
> How about:
```
3stack-dig
or
targa
```

tried that too... this is really annoying...

---

### Post by lidex on 2010-08-20
Using a Terminal="Applications->Accessories->Terminal"
Enter this command:
```
ubuntu-bug audio
```

---

### Post by timinator94 on 2010-08-20
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Enter this command:
```
ubuntu-bug audio
```
Alright I did that... now i just wait?

---

### Post by lidex on 2010-08-20
> **timinator94 said:**
> Alright I did that... now i just wait?

Can you post the link to the bug report please?

---

### Post by timinator94 on 2010-08-20
```
** Attachment added: "AlsaDevices.txt"
   [https://bugs.launchpad.net/bugs/620927/+attachment/1502714/+files/AlsaDevices.txt](https://bugs.launchpad.net/bugs/620927/+attachment/1502714/+files/AlsaDevices.txt)
 
** Attachment added: "BootDmesg.txt"
   [https://bugs.launchpad.net/bugs/620927/+attachment/1502715/+files/BootDmesg.txt](https://bugs.launchpad.net/bugs/620927/+attachment/1502715/+files/BootDmesg.txt)
 
** Attachment added: "Card0.Amixer.info.txt"
   [https://bugs.launchpad.net/bugs/620927/+attachment/1502716/+files/Card0.Amixer.info.txt](https://bugs.launchpad.net/bugs/620927/+attachment/1502716/+files/Card0.Amixer.info.txt)
 
** Attachment added: "Card0.Amixer.values.txt"
   [https://bugs.launchpad.net/bugs/620927/+attachment/1502717/+files/Card0.Amixer.values.txt](https://bugs.launchpad.net/bugs/620927/+attachment/1502717/+files/Card0.Amixer.values.txt)
 
** Attachment added: "Card0.Codecs.codec.0.txt"
   [https://bugs.launchpad.net/bugs/620927/+attachment/1502718/+files/Card0.Codecs.codec.0.txt](https://bugs.launchpad.net/bugs/620927/+attachment/1502718/+files/Card0.Codecs.codec.0.txt)
 
** Attachment added: "Card0.Codecs.codec.1.txt"
   [https://bugs.launchpad.net/bugs/620927/+attachment/1502719/+files/Card0.Codecs.codec.1.txt](https://bugs.launchpad.net/bugs/620927/+attachment/1502719/+files/Card0.Codecs.codec.1.txt)
 
** Attachment added: "CurrentDmesg.txt"
   [https://bugs.launchpad.net/bugs/620927/+attachment/1502720/+files/CurrentDmesg.txt](https://bugs.launchpad.net/bugs/620927/+attachment/1502720/+files/CurrentDmesg.txt)
 
** Attachment added: "Dependencies.txt"
   [https://bugs.launchpad.net/bugs/620927/+attachment/1502721/+files/Dependencies.txt](https://bugs.launchpad.net/bugs/620927/+attachment/1502721/+files/Dependencies.txt)
 
** Attachment added: "PactlStat.txt"
   [https://bugs.launchpad.net/bugs/620927/+attachment/1502722/+files/PactlStat.txt](https://bugs.launchpad.net/bugs/620927/+attachment/1502722/+files/PactlStat.txt)
 
** Attachment added: "PciMultimedia.txt"
   [https://bugs.launchpad.net/bugs/620927/+attachment/1502723/+files/PciMultimedia.txt](https://bugs.launchpad.net/bugs/620927/+attachment/1502723/+files/PciMultimedia.txt)
 
** Attachment added: "ProcCpuinfo.txt"
   [https://bugs.launchpad.net/bugs/620927/+attachment/1502724/+files/ProcCpuinfo.txt](https://bugs.launchpad.net/bugs/620927/+attachment/1502724/+files/ProcCpuinfo.txt)
 
-- 
[Realtek ALC888] only one jack works and built in mic doesnt work
[https://bugs.launchpad.net/bugs/620927](https://bugs.launchpad.net/bugs/620927)
You received this bug notification because you are a direct subscriber
of the bug.
 
Status in &#8220;pulseaudio&#8221; package in Ubuntu: New
 
Bug description:
Binary package hint: pulseaudio
 
Ubuntu 10.04 x68
 output of apt-cache policy pulseaudio
pulseaudio:
  Installed: 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14
  Candidate: 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14
  Version table:
 *** 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
Built in microphone is non op-4 jacks 2in 2out only one out works cannot test input
 
all steps taken here-[http://ubuntuforums.org/showthread.php?t=1545245](http://ubuntuforums.org/showthread.php?t=1545245)
 
ProblemType: Bug
DistroRelease: Ubuntu 10.04
Package: pulseaudio 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14
ProcVersionSignature: Ubuntu 2.6.32-24.41-generic 2.6.32.15+drm33.5
Uname: Linux 2.6.32-24-generic i686
NonfreeKernelModules: nvidia wl
AlsaVersion: Advanced Linux Sound Architecture Driver Version 1.0.21.
AplayDevices: aplay: device_list:223: no soundcards found...
Architecture: i386
ArecordDevices: arecord: device_list:223: no soundcards found...
AudioDevicesInUse: Error: command ['fuser', '-v', '/dev/dsp', '/dev/snd/by-path', '/dev/snd/controlC0', '/dev/snd/hwC0D0', '/dev/snd/hwC0D1', '/dev/snd/pcmC0D0c', '/dev/snd/pcmC0D0p', '/dev/snd/pcmC0D1p', '/dev/snd/seq', '/dev/snd/timer', '/dev/sequencer2', '/dev/sequencer'] failed with exit code 1:
Date: Thu Aug 19 23:33:13 2010
InstallationMedia: Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
ProcEnviron:
 LANG=en_US.UTF-8
 SHELL=/bin/bash
SelectedCard: 0 NVidia HDA-Intel - HDA NVidia
SourcePackage: pulseaudio
Symptom: audio
Title: [Realtek ALC888] pactl stat failed to find default card
dmi.bios.date: 04/10/2009
dmi.bios.vendor: American Megatrends Inc.
dmi.bios.version: A1672NMS V1.0J
dmi.board.asset.tag: To Be Filled By O.E.M.
dmi.board.name: MS-1672
dmi.board.vendor: MSI
dmi.board.version: Ver 1.000
dmi.chassis.asset.tag: To Be Filled By O.E.M.
dmi.chassis.type: 3
dmi.chassis.vendor: To Be Filled By O.E.M.
dmi.chassis.version: To Be Filled By O.E.M.
dmi.modalias: dmi:bvnAmericanMegatrendsInc.:bvrA1672NMSV1.0J:bd04/10/2009:svnMicro-StarInternational:pnMSINOTEBOOKVR630:pvrVer1.000:rvnMSI:rnMS-1672:rvrVer1.000:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:
dmi.product.name: MSI NOTEBOOK VR630
dmi.product.version: Ver 1.000
dmi.sys.vendor: Micro-Star International
 
To unsubscribe from this bug, go to:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/620927/+subscribe](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/620927/+subscribe)
```

Thats the email i got..

---

### Post by lidex on 2010-08-20
> AplayDevices: aplay: device_list:223: no soundcards found...
Not cool. I think you should try upgrading your alsa install. Use the link in my sig.

---

### Post by timinator94 on 2010-08-24
> **lidex said:**
> Not cool. I think you should try upgrading your alsa install. Use the link in my sig.
Did the upgrade. still no luck. Heres the new bug report.


```
ProblemType: Bug
DistroRelease: Ubuntu 10.04
Package: alsa-base 1.0.22.1+dfsg-0ubuntu3
ProcVersionSignature: Ubuntu 2.6.32-24.41-generic 2.6.32.15+drm33.5
Uname: Linux 2.6.32-24-generic i686
NonfreeKernelModules: nvidia wl
AlsaVersion:
 Advanced Linux Sound Architecture Driver Version 1.0.23.
 Compiled on Aug 21 2010 for kernel 2.6.32-24-generic (SMP).
Architecture: i386
ArecordDevices:
 **** List of CAPTURE Hardware Devices ****
 card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
   Subdevices: 1/1
   Subdevice #0: subdevice #0
AudioDevicesInUse:
 USER        PID ACCESS COMMAND
 /dev/snd/controlC0:  timinator94   2405 F.... pulseaudio
Card0.Amixer.info:
 Card hw:0 'NVidia'/'HDA NVidia at 0xfbf78000 irq 21'
   Mixer name    : 'Realtek ALC888'
   Components    : 'HDA:10ec0888,14626721,00100001 HDA:11c11040,11c10001,00100200'
   Controls      : 24
   Simple ctrls  : 15
Date: Tue Aug 24 12:43:52 2010
InstallationMedia: Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
PackageArchitecture: all
ProcEnviron:
 LANG=en_US.UTF-8
 SHELL=/bin/bash
SelectedCard: 0 NVidia HDA-Intel - HDA NVidia
SourcePackage: alsa-driver
Symptom: audio
Title: [Realtek ALC888] Recording problem
dmi.bios.date: 04/10/2009
dmi.bios.vendor: American Megatrends Inc.
dmi.bios.version: A1672NMS V1.0J
dmi.board.asset.tag: To Be Filled By O.E.M.
dmi.board.name: MS-1672
dmi.board.vendor: MSI
dmi.board.version: Ver 1.000
dmi.chassis.asset.tag: To Be Filled By O.E.M.
dmi.chassis.type: 3
dmi.chassis.vendor: To Be Filled By O.E.M.
dmi.chassis.version: To Be Filled By O.E.M.
dmi.modalias: dmi:bvnAmericanMegatrendsInc.:bvrA1672NMSV1.0J:bd04/10/2009:svnMicro-StarInternational:pnMSINOTEBOOKVR630:pvrVer1.000:rvnMSI:rnMS-1672:rvrVer1.000:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:
dmi.product.name: MSI NOTEBOOK VR630
dmi.product.version: Ver 1.000
dmi.sys.vendor: Micro-Star International
```

---

### Post by timinator94 on 2010-08-24
Any more ideas?:confused:

---

### Post by Yellow Pasque on 2010-08-24
Please use [ code ][ /code ] tags (without the spaces in between the brackets) when posting output. Also, bumping your thread faster than 1day/24hours after the last post is frowned upon in these forums.

This thread is a bit hard to follow. What is your current audio status, and can you run the alsa-info script again?

---

### Post by lidex on 2010-08-24
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack-6ch-dig  
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by timinator94 on 2010-08-27
[@Temüjin- Im sorry didnt know about the code thing and no im still having problems]("http://ubuntuforums.org/member.php?u=327594")
@lidex-first of all thank you for all the help. If i can get my mic working i will be totaly ditching windows. I have already gotten all of my games working in wine and i will probably buy crossover. did what you said still no dice OK well i changed the levels(screenshot-2.png&screenshot-1.png) i want to make sure their right and also which hardware do i select(screenshot.png)?
thanks again for all the help
tim

---

### Post by timinator94 on 2010-08-27
also tried targa-dig still no mic please help!

---

### Post by timinator94 on 2010-08-28
Bump Please Help!!!!!!:confused:

---

### Post by lidex on 2010-08-28
Do you have the link to launchpad for the bug report?
Are you sure you're using the HP jack and not a line output?
Check for bios update also.

---

### Post by timinator94 on 2010-09-12
I fixed it solution

Buy a new laptop:p got me an asus g50vt-x1 new for 590 usd so ill be using that from now on! thnx anyways

---

### Post by lidex on 2010-09-14
OK then. I guess that works also.

---

