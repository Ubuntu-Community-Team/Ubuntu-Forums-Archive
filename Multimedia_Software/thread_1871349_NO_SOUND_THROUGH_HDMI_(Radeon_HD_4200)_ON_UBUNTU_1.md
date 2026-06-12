---
title: "NO SOUND THROUGH HDMI (Radeon HD 4200) ON UBUNTU 11.10"
date: 2011-10-28
forum: Multimedia Software
---

### Post by klevstul on 2011-10-28
NO SOUND THROUGH HDMI (Radeon HD 4200) ON UBUNTU 11.10
--

After I updated to Ubuntu 11.10 no audio is played through HDMI. I've searched the Net and this forum,
seen that several people are having problems with sound through HDMI on 11.10, but have found no solution.

If anyone has got any ideas please let me know.

Please note that before I updated to 11.10 audio played perfectly through HDMI.
I have double checked the sound settings, and made sure the correct hardware and output
(HDMI) is chosen.


I've got the following setup:
---
Hardware: RS880 Audio Device [Radeon HD 4200]

```
klevstul@Inspiron570:~$ cat /etc/issue
Ubuntu 11.10 \n \l
```


```
klevstul@Inspiron570:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
```


```
klevstul@Inspiron570:~$ uname -a
Linux Inspiron570 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 athlon i386 GNU/Linux
```
---

I've done the "Comprehensive Sound Problem Solutions Guide"
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

The output from that is
---
(1)
```
klevstul@Inspiron570:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 3: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


(2)
```
klevstul@Inspiron570:~$ lspci -v
...
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200] (prog-if 00 [VGA controller])
	Subsystem: Dell Device 043b
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at e000 [size=256]
	Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fe900000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
	Subsystem: Dell Device 043b
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at feae8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
...
```


(3)
Found nowhere to search on given page. But I can run the speaker test (no sound to be heard through):
```
klevstul@Inspiron570:~$ speaker-test -Dplug:surround51 -c6 -twav

speaker-test 1.0.24.2

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 349504
Period size range from 32 to 174752
Using max buffer size 349504
Periods = 4
was set period_size = 174752
was set buffer_size = 349504
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 21.975189
...
```

It might be this though (snd-hda-intel):
[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)



(4)
```
klevstul@Inspiron570:~$ sudo modprobe snd-hda-intel 
[sudo] password for klevstul:
``` 

still no sound...
#sudo nano /etc/modules


(2-1)
Getting the ALSA drivers from a *fresh* kernel

```
klevstul@Inspiron570:~$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libbluray0 phonon libdvbpsi6 libjs-mootools liblzo2-2 phonon-backend-gstreamer libphonon4 libquicktime1 libmatroska3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  alsa-base* alsa-utils* linux-sound-base* ubuntu-desktop*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 2,802 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 232209 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing alsa-base ...
Purging configuration files for alsa-base ...
Removing alsa-utils ...
Purging configuration files for alsa-utils ...
Removing linux-sound-base ...
Purging configuration files for linux-sound-base ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
```


(2-2)
```
klevstul@Inspiron570:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils
```
...


(2-3)

```
klevstul@Inspiron570:~$ sudo apt-get install gdm ubuntu-desktop
```
...


```
klevstul@Inspiron570:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 3: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


ALSA driver Compilation
Skipped this step as the driver seems to work, except for not outputting sound.
---


I also read that an option can be to get drivers manually, however I have not tried that:
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually)

---

### Post by BicyclerBoy on 2011-10-28
speaker-test -c 2 -r 48000 -D hw:1,3

surround5.1 is a default alias..likely pointing to hw:0,0.
aplay -L 
shows you the aliases..

---

### Post by klevstul on 2011-10-29
Executes without problems but my speakers are all silent... (no, it's not the sound system that is the problem, works for everything else, all other HDMI inputs plays fine)

```
klevstul@Inspiron570:~$ speaker-test -c 2 -r 48000 -D hw:1,3

speaker-test 1.0.24.2

Playback device is hw:1,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 1048576
Period size range from 32 to 524288
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 7.088080

```

---

### Post by BicyclerBoy on 2011-10-29
I don't follow any AMD news/releases except stuff about fusion/zacate..

For HDA HDMI audio to work over video card you have to have the correct video driver.
For AMD cards this means proprietary catalyst driver..

Is this HD4200 an mobo/onboard chipset graphics adaptor ?
This chipset only supports stereo & AC3 5.1 over HDMI, no HDA formats..really just S/PDIF.
It may not matter which driver is used in this case..

[http://lists.freedesktop.org/archives/dri-devel/2010-May/000510.html](http://lists.freedesktop.org/archives/dri-devel/2010-May/000510.html)

How exactly are your speakers connected ?
HT amp AVR with HDMI ?
Speakers attached to TV receiver (HDMI) ?

What do you mean by works with everything else ?
Do you mean other output devices (DVD/CD player) connected to AVR or TV ?

---

### Post by klevstul on 2011-10-30
> **BicyclerBoy said:**
> Is this HD4200 an mobo/onboard chipset graphics adaptor ?
This chipset only supports stereo & AC3 5.1 over HDMI, no HDA formats..really just S/PDIF.
It may not matter which driver is used in this case..

[http://lists.freedesktop.org/archives/dri-devel/2010-May/000510.html](http://lists.freedesktop.org/archives/dri-devel/2010-May/000510.html)

How exactly are your speakers connected ?

What do you mean by works with everything else ?
Do you mean other output devices (DVD/CD player) connected to AVR or TV ?

- Yes, the card is integrated / onboard.
- I have a Yamaha YSP sound system, HDMI directly from the PC to this.
- Yes, I do mean that other input devices, like PS3 and WDTV works fine.

Please note that the sound worked without problems when I ran 11.04. It was after the upgrade to 11.10 that the sound did disappear. Maybe a new sound driver was installed then, that doesn't support my card?

---

### Post by BicyclerBoy on 2011-10-30
The words (posted previous) "Inspiron" suggests troublesome laptop h/w ?

Cast you mind back to your 10.10 install; did you have to use a snd-hda-intel module options ?
(in the file /etc/modprobe.d/alsa-base.conf)

If you are lucky, the 11.10 installer will have just commented out the old settings..

I suspect you were previously using the AMD/ATI catalyst video driver & now you are using radeon which I think is the open source project.
I don't know if the radeon driver can support HDMI audio or ELD reporting.

---

### Post by klevstul on 2011-10-30
Having spent too much time on this issue I gave up and installed Mint Linux in stead of plain Ubuntu. So easy and everything works like a charm now. The sound is finally back!

---

### Post by BicyclerBoy on 2011-10-30
Can't blame you for that..

I only have 11.10 setup on a 2nd disk just to see if it works or not as the case maybe.
The real work-horse is still 10.04.

---

### Post by jmate24 on 2011-10-30
The 4200 series is a motherboard videocard/soundcard i would suggest upgrading to a 5670 Radeon HD

---

### Post by klevstul on 2011-10-30
Anyway. Thanks a lot for your input on this one. Very much appreciated!

---

### Post by alex2399 on 2011-10-30
Also had a problem with digital output (SP/DIF), no sound...The solution was to unmute. Not from the GUI but from the terminal with

```
alsamixer
```

Hope it helps, you may need to play with the settings.

---

### Post by pearce_jj on 2011-10-31
Just found this too, also ATI chipset ([Zotac ZBox HD-AD01]("http://pdpt.zotac.com/index.php?page=shop.product_details&flypage=flypage_images.tpl&product_id=260&category_id=118&option=com_virtuemart&Itemid=1")).  Sound was a pain under 10, video performance was very poor under 11.04 (but sound worked) and sound doesn't seem to work with 11.10 (although it's all detected okay).

---

### Post by Samos123 on 2011-11-05
I am having the same problem with ATI Radeon 4250 HD.. in 11.04 my sound worked perfectly but now I can not get sound from my laptop speakers, headset works fine though..

any suggestions?

---

### Post by sarin_cv on 2011-11-06
I'm also facing this issue with 11.10 and Radeon 3450...there is no sound and video playback is too fast....Didn't have this issue with 11.04..

---

### Post by sarin_cv on 2011-11-07
This solved my issue...

[http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound](http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound)

---

### Post by Samos123 on 2011-11-07
> **sarin_cv said:**
> This solved my issue...

[http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound](http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound)

Didn't solve the problem of my laptop speakers sound not working, in 11.04 it worked perfectly. My headset is working though.

---

### Post by sarin_cv on 2011-11-09
I had this issue with opensuse once...installed alsamixer and played with the settings....some control was in mute...

---

### Post by Samos123 on 2011-11-09
> **sarin_cv said:**
> I had this issue with opensuse once...installed alsamixer and played with the settings....some control was in mute...

Yea I also checked it with alsamixer, but its not on MM so seems fine to me. Thanks for tip

---

### Post by jae18708 on 2011-11-18
Had this issue in Mint Debian. 

In a terminal try: gksudo gedit /etc/default/grub

Add radeon.audio=1 to the line that starts with GRUB_CMDLINE_LINUX_DEFAULT  

Mine looks like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

---

### Post by Ubsat on 2011-11-20
After installing ATI proprietary FGLRX drivers (shown in the list of additional drivers app), HDMI sound is working in 11.10!!

---

### Post by kaizo2560 on 2011-12-22
Hi I did the editing and update of grub (both 1 and 2) but no luck so far.

I did get audio using the fglrx drivers but this time the screen was over-scanned (had about an inch of black boarders).

I use HD6970 and 11.10 any idea?

---

### Post by tbrminsanity on 2011-12-24
Good day everyone,

I was having a similar problem with my new box.  I checked my proprietary drivers (due to some of the things that were said on this thread) and noticed my graphic drivers were not enabled.  I downloaded, enabled and reset my machine and now my sound works.  I also noticed that video is not speed up any more.  Hope this helps anyone else that are having these issues, and thank you for the help of everyone on this thread.

TBRMInsanity

---

### Post by kaizo2560 on 2012-01-01
bump

---

### Post by Jmgf on 2012-01-20
Just go to Aditional Drivers and update the available drivers. I had the exact same problem with the hd 4200 and worked for me.

---

### Post by Axess_Denied on 2012-01-25
> **sarin_cv said:**
> This solved my issue...

[http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound](http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound)

This also solved my issues. This thread should be marked SOLVED

---

### Post by Johnny English on 2012-03-04
Sorry to bring this back up, but I'm having this same problem. Forgive me if what I'm about to say shows me up as the technical dunce I know I am, but here's my issue and what I've done:

- New build PC with Gigabyte 880GM mobo and Radeon HD 4200 graphics running Oneiric

- Sound > Sound Settings > Hardware and > Output both set to Digital Stereo (HDMI), but speaker test produces nothing

- Additional Drivers shows me ATI/AMD proprietary FGLRX graphics driver and ATI/AMD proprietary FGLRX graphics driver (post-release updates) as options. I installed and activated the first with no problem, but when I then selected and attempted to activate the post-release updates version I got the following error message:

```
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```

Unfortunately I don't know how to read that log file (told you I was a dunce!). I found [this](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/827120) relating to that error message but I don't know if that's actually my issue, and I don't want to start fixing things that don't need fixing.

- I've been into the grub file and made the radeon.audio=1 amendment, but that makes no difference.

Can anyone advise the village idiot on this, please?

Edit: by removing the fglrx driver and reverting to the open source drivers (using [this process](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch), I now have sound and proper playback speed via HDMI. However, that introduces a slightly different problem, which is that I can't get the desktop to display in widescreen on my Phillips TV which is serving as the monitor without it disappearing off the sides - I have to run in 4:3 which isn't the end of the world, but is a pain. Any suggestions?

---

### Post by onebutters on 2012-05-24
Running AMD x64 CPU with nForce 430 Chipset and Radeon HD5770. Managed to get HDMI audio working on my TV on 12.04 by installing proprietary AMD drivers. I followed the instructions found here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I followed the instructions found under Manually Installing Catalyst 12.4 and finally got an output for the command fglrxinfo.

---

### Post by chbrules on 2012-11-27
> **sarin_cv said:**
> This solved my issue...

[http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound](http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound)

This solved my issue. Radeon 4200HD, Ubuntu 12.10, HDMI

---

