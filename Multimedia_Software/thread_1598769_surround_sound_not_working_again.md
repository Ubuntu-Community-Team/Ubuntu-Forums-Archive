---
title: "surround sound not working again"
date: 2010-10-16
forum: Multimedia Software
---

### Post by Lucky75 on 2010-10-16
Hi!

I recently upgraded to 10.10, but I can't get surround sound working. I had it working in 10.04, but now the option under System->preferences->sound doesn't give me anything for 5.1, only stereo analog.

I've tried changing daemon.conf to default-sample-channels = 6, but nothings showing in alsamixer or system/pref/sound.

Any suggestions? 

Thanks!

---

### Post by Lucky75 on 2010-10-17
up

---

### Post by Lucky75 on 2010-10-18
up

---

### Post by ozzman2 on 2010-10-19
I'm struggling with the same problem in 10.04.

Only difference is that I have no "Digital Surround" options in pulseaudio (just the onboard analog surround appears).

My "Digital Stereo Duplex (IEC958 )" works fine, but I'd like to watch movies in 5.1.

I've read through a lot of stuff trying to get it to work, but I haven't had any luck so far.  Any help would be appreciated.  :)

---

### Post by Lucky75 on 2010-10-20
up

---

### Post by Lucky75 on 2010-10-25
bump

---

### Post by lidex on 2010-10-25
> **Lucky75 said:**
> bump

Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by ozzman2 on 2010-10-26
Thanks for that reply bud!
It hasn't solved my problem (yet), but at least it's a start in another direction.

I'm reply#7 here;
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/236372?comments=all](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/236372?comments=all)

I don't anticipate a response from them anytime soon, but would you mind reading my comment?  Is there something I may have missed?
Thanks.

---

### Post by lidex on 2010-10-26
> **ozzman2 said:**
> Thanks for that reply bud!
It hasn't solved my problem (yet), but at least it's a start in another direction.

I'm reply#7 here;
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/236372?comments=all](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/236372?comments=all)

I don't anticipate a response from them anytime soon, but would you mind reading my comment?  Is there something I may have missed?
Thanks.

Run the alsa-info script and post it there as an attachment as well as a link here. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by ozzman2 on 2010-10-26
lidex, thank you so much for helping me with this!  (I was about to give up before you came along).  :grin:

Here's the link:
[http://www.alsa-project.org/db/?f=fd4b7df396328aa982f02e7f7dd6e504f1823c9d](http://www.alsa-project.org/db/?f=fd4b7df396328aa982f02e7f7dd6e504f1823c9d)

---

### Post by lidex on 2010-10-26
> **ozzman2 said:**
> lidex, thank you so much for helping me with this!  (I was about to give up before you came along).  :grin:

Here's the link:
[http://www.alsa-project.org/db/?f=fd4b7df396328aa982f02e7f7dd6e504f1823c9d](http://www.alsa-project.org/db/?f=fd4b7df396328aa982f02e7f7dd6e504f1823c9d)

You have the via 1708b codec. I have not seen that and 1708 codecs in general have been problematic. For best support I recommend upgrading alsa to the latest version via the link in my sig.

---

### Post by ozzman2 on 2010-10-27
I've upgraded to ALSA version 1.0.23 (with your script).  Immediately following, I lost sound.  So I went into "/etc/modprobe.d/alsa-base.conf"

I did not see "snd-hda-intel  index=-2" in the file at all, so I added it in.  After a save and reboot, my sound came back.  However, I still don't have any 5.1 from my fiber cable.

Reading through your "HD-Audio-Models.txt", I couldn't find VIA VT1708B.  Does this mean I'm I'm out of luck, or is there something else I could try?

---

### Post by lidex on 2010-10-27
> **ozzman2 said:**
> I've upgraded to ALSA version 1.0.23 (with your script).  Immediately following, I lost sound.  So I went into "/etc/modprobe.d/alsa-base.conf"

I did not see "snd-hda-intel  index=-2" in the file at all, so I added it in.  After a save and reboot, my sound came back.  However, I still don't have any 5.1 from my fiber cable.

Reading through your "HD-Audio-Models.txt", I couldn't find VIA VT1708B.  Does this mean I'm I'm out of luck, or is there something else I could try?

I don't see how that addition to alsa-base.conf could benefit you. Remove it for me please, reboot and run the alsa-info script again so we can see where you are. Also please provide the make/model of the pc in question.

---

### Post by ozzman2 on 2010-10-27
lidex, I removed "snd-hda-intel index=-2", from alsa-base.conf, saved and restarted like you said.

Initially, I would get the Ubuntu startup sound, but no sound after that.  Going into SYSTEM>PREFERENCES>SOUND, there wasn't anything listed in the HARDWARE tab.  Here is the output from the alsa-info script at this stage:
[http://www.alsa-project.org/db/?f=ec58e2e26bcadb5f2ed16f3cf9e3eb5c8e1a86ba](http://www.alsa-project.org/db/?f=ec58e2e26bcadb5f2ed16f3cf9e3eb5c8e1a86ba)

This is where it gets interesting...
Just for fun, I installed VLC media player (through Ubuntu Software Center).  From there I opened a movie that had DTS.  Going into TOOLS and PREFERENCES, I selected the AUDIO tab.  Checked off USE S/PDIF WHEN AVAILABLE, and changed the output type to ALSA AUDIO OUTPUT.  For the first time, I had real 5.1 surround in Ubuntu!

When I exit VLC and go back into SYSTEM>PREFERENCES>SOUND>HARDWARE TAB, my sound card shows up!  The weird thing is that under PROFILE, the only options I have are "analog" (previous to this, I had several digital stereo options). - The default at this point is "Analog Surround 5.1 Output + Analog Stereo Input".  Here is another "alsa-info" output:
[http://www.alsa-project.org/db/?f=68c95a001360162faba016b791d71edbdbdb1032](http://www.alsa-project.org/db/?f=68c95a001360162faba016b791d71edbdbdb1032)
(No other sound at this point works.)

Now, if I change "Analog Surround 5.1 Output + Analog Stereo Input" to "Analog Stereo Duplex", I start getting sound from Rhythmbox.  (Please note that my only sound connection on this machine is a digital fiber optic S/PDIF cable running to a reciever - there is no analog connection).
Script output:
[http://www.alsa-project.org/db/?f=a5a35bc4378df24be2c47b5646a4e1e66572b828](http://www.alsa-project.org/db/?f=a5a35bc4378df24be2c47b5646a4e1e66572b828)

If I do a quick reboot, everything behaves just the same as I previously described.  However, after I perform the "VLC workaround" and go into SYSTEM>PREFERENCES>SOUND a message pops up saying "Waiting for Sound System to Respond!"  A second later, the Sound Preferences window is up.  This time however (in the HARDWARE tab), the "digital" options return in PROFILE.  The sound continues to work if I change "Analog Stereo Duplex" to the newly reappeared "Digital Stereo Duplex (IEC958 )".  Script output:
[http://www.alsa-project.org/db/?f=05347e836d0c96e79c3eb9bc06286a9c4cbc89d0](http://www.alsa-project.org/db/?f=05347e836d0c96e79c3eb9bc06286a9c4cbc89d0)

Sorry if all this was complete overkill - but I have performed these actions several times with the same results.  I've tried to be as concise as I can with all this.  A factor seems to be the difference between a "warm boot" vs "cold boot".

My motherboard is an ASUS M3N78-VM.  I bought it for it's NVIDIA chipset (which I was told works better with Linux).

Please tell me it can work better than this...
:confused:

---

### Post by lidex on 2010-10-28
That's insane. Wow.

Remove your pulse config files. ```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.** 

A bios update may help. What do you get here:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

There are two options for alsa-base.conf that may help as well:
```
options snd-hda-intel model=auto
options snd-hda-intel model=6stack-digout 
```
Only try one at a time and reboot to initialize.

Some references:
[http://ubuntuforums.org/showthread.php?t=1058464](http://ubuntuforums.org/showthread.php?t=1058464)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4330](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4330)

---

### Post by ozzman2 on 2010-10-28
Removed what files there were to remove.

sudo dmidecode -t bios:
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 1602   
    Release Date: 04/13/2010
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 8.14

Handle 0x003B, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

sudo dmidecode -t baseboard:
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: M3N78-VM
    Version: Rev X.0x
    Serial Number: MF709BG01700515
    Asset Tag: To Be Filled By O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To Be Filled By O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0039, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description:   To Be Filled By O.E.M.

Tried both changes to the alsa-base.conf (separately).  Neither one resolved the issue on cold boot (in fact, the second option made the video sound "jitter" occasionally).

I am familiar with the first reference link.  It assisted me in finding out I had to purchase an "SPDIF bracket" to get toslink to work on my M3N78-VM.  I don't have a login for the alsa bug tracking site.  Is it worthwhile signing up?

Are there any changes I should/shouldn't make to /etc/pulse/daemon.conf?

I'm thinking about formatting this machine and starting over with a fresh install.  I've been installing/uninstalling/reinstalling pulseaudio and alsa modules for several weeks trying to get this to work.  I'm wondering if something could have just got messed up?

---

### Post by lidex on 2010-10-28
Looks like you have a recent bios.
The alsa site has a link just below the login to view as a guest (read only).
Here is the link for launchpad bugs matching VT1708B:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver?field.searchtext=vt1708b&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+source/alsa-driver?field.searchtext=vt1708b&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by Lucky75 on 2010-10-28
In terms of the "ubuntu-bug audio" I see the following error:

```

2219
symptom script /usr/share/apport/symptoms/audio.py crashed:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 54, in thread_collect_info
    package = symb['run'](report, ui)
  File "/usr/share/apport/symptoms/audio.py", line 33, in run
    package, channelcount = check_pulseaudio_profile(report, ui, card, problem)
  File "/usr/share/apport/symptoms/audio.py", line 194, in check_pulseaudio_profile
    cc = int(cc)/10 + int(cc) % 10
ValueError: invalid literal for int() with base 10: 'stereo'

```


Script output:
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Fri Oct 29 03:22:57 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


!!Kernel Information
!!------------------

Kernel release:    2.6.35-22-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_usb_audio


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd8000000 irq 23
 1 [Camera         ]: USB-Audio - DVC FINE PC Camera
                      Vimicro Co.,ltd DVC FINE PC Camera at usb-0000:00:0b.1-3, high speed


!!PCI Soundcards installed in the system
!!--------------------------------------

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:10.1 0403: 10de:026c (rev a2)
	Subsystem: 1043:818f


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_usb_audio
	async_unlink : Y
	device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	ignore_ctl_error : N
	index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	nrpacks : 8
	pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Analog Devices AD1986A
Address: 0
Function Id: 0x1
Vendor Id: 0x11d41986
Subsystem Id: 0x1043818f
Revision Id: 0x100500
No Modem Function Group found
Default PCM:
    rates [0x7f]: 8000 11025 16000 22050 32000 44100 48000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
GPIO: io=0, o=1, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x30311: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="AD198x Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x60]: 44100 48000
    bits [0x2]: 16
    formats [0x5]: PCM AC3
  Delay: 3 samples
  Connection: 2
     0x01* 0x06
Node 0x03 [Audio Output] wcaps 0x44d: Stereo Amp-Out
  Control: name="PCM Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="PCM Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="AD198x Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x17 0x17]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Processing caps: benign=1, ncoeff=70
Node 0x04 [Audio Output] wcaps 0x40d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x40d: Stereo Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=0, channel=8
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x06 [Audio Input] wcaps 0x100511: Stereo
  Device: name="AD198x Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x7f]: 8000 11025 16000 22050 32000 44100 48000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x07 [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 8
     0x03 0x09 0x13 0x14 0x15 0x16 0x17 0x18
Node 0x08 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x07
Node 0x09 [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80] [0x80]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Connection: 2
     0x04 0x05
Node 0x0a [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x07* 0x04 0x05
Node 0x0b [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x07* 0x04
Node 0x0c [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x04* 0x07
Node 0x0d [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x05* 0x08
Node 0x0e [Audio Selector] wcaps 0x300100: Mono
  Connection: 2
     0x08* 0x11
Node 0x0f [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 8
     0x1f* 0x20 0x1d 0x1d 0x27 0x28 0x29 0x2a
Node 0x10 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x20* 0x1c 0x1f
Node 0x11 [Audio Selector] wcaps 0x300941: Stereo R/L
  Connection: 2
     0x0f* 0x2b
  Processing caps: benign=1, ncoeff=0
Node 0x12 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Capture Source", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 0
Node 0x13 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x96 0x96]
  Connection: 1
     0x11
Node 0x14 [Audio Selector] wcaps 0x30010c: Mono Amp-Out
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80]
  Connection: 1
     0x23
Node 0x15 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="CD Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="CD Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x19 0x19]
  Connection: 1
     0x22
Node 0x16 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Aux Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Aux Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x21
Node 0x17 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x10
Node 0x18 [Audio Selector] wcaps 0x30010c: Mono Amp-Out
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x8f]
  Connection: 2
     0x19* 0x24
Node 0x19 [Beep Generator Widget] wcaps 0x700000: Mono
Node 0x1a [Pin Complex] wcaps 0x400185: Stereo Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1f 0x1f]
  Pincap 0x0000001f: OUT HP Detect Trigger ImpSense
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0a
Node 0x1b [Pin Complex] wcaps 0x400185: Stereo Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1f 0x1f]
  Pincap 0x0001001f: OUT HP EAPD Detect Trigger ImpSense
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0b
Node 0x1c [Pin Complex] wcaps 0x400185: Stereo Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000037: IN OUT Detect Trigger ImpSense
  Pin Default 0x01a19020: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c
Node 0x1d [Pin Complex] wcaps 0x400985: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001737: IN OUT Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01813021: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x2, Sequence = 0x1
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0d
Node 0x1e [Pin Complex] wcaps 0x400104: Mono Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x511711f0: [N/A] Speaker at Int Rear
    Conn = Analog, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0e
Node 0x1f [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001727: IN Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a19022: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x2
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
Node 0x20 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001727: IN Detect Trigger ImpSense
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01813023: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x2, Sequence = 0x3
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
Node 0x21 [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00000027: IN Detect Trigger ImpSense
  Pin Default 0x9997e1f0: [Fixed] Aux at Int ATAPI
    Conn = Analog, Color = White
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x22 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x9933112e: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Black
    DefAssociation = 0x2, Sequence = 0xe
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x23 [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x59b771f0: [N/A] Telephony at Int ATAPI
    Conn = Analog, Color = Yellow
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x24 [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x51f711f0: [N/A] Other at Int Rear
    Conn = Analog, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x25 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x0145f1f0: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Other
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x02
Node 0x26 [Power Widget] wcaps 0x500500: Mono
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 8
     0x07 0x08 0x13 0x14 0x15 0x16 0x17 0x18
Node 0x27 [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 2
     0x1f 0x1d
Node 0x28 [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 2
     0x1f 0x20
Node 0x29 [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 2
     0x1d 0x20
Node 0x2a [Audio Mixer] wcaps 0x200101: Stereo
  Connection: 3
     0x1f 0x1d 0x20
Node 0x2b [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x0f
--endcollapse--


!!USB Mixer information
!!---------------------------
--startcollapse--

USB Mixer: usb_id=0x0ac8332d, ctrlif=2, ctlerr=0
Card: Vimicro Co.,ltd DVC FINE PC Camera at usb-0000:00:0b.1-3, high speed
  Unit: 2
    Control: name="Auto Gain Control", index=0
    Info: id=2, control=7, cmask=0x1, channels=1, type="BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 2
    Control: name="Mic Capture Volume", index=0
    Info: id=2, control=2, cmask=0x1, channels=1, type="S16"
    Volume: min=-6912, max=5376, dBmin=-2700, dBmax=2100
  Unit: 2
    Control: name="Mic Capture Switch", index=0
    Info: id=2, control=1, cmask=0x1, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 10 Oct 27 22:57 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  5 Oct 27 22:57 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  9 Oct 27 22:57 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  8 Oct 27 22:58 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  7 Oct 28 23:20 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  6 Oct 27 22:58 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  4 Oct 28 23:19 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  3 Oct 27 22:57 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Oct 27 22:57 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  60 Oct 27 22:57 .
drwxr-xr-x 4 root root 260 Oct 27 22:57 ..
lrwxrwxrwx 1 root root  12 Oct 27 22:57 usb-Vimicro_Co._ltd_DVC_FINE_PC_Camera-02 -> ../controlC1

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Oct 27 22:57 .
drwxr-xr-x 4 root root 260 Oct 27 22:57 ..
lrwxrwxrwx 1 root root  12 Oct 27 22:57 pci-0000:00:0b.1-usb-0:3:1.2 -> ../controlC1
lrwxrwxrwx 1 root root  12 Oct 27 22:57 pci-0000:00:10.1 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Camera [DVC FINE PC Camera], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [NVidia]

Card hw:0 'NVidia'/'HDA NVidia at 0xd8000000 irq 23'
  Mixer name	: 'Analog Devices AD1986A'
  Components	: 'HDA:11d41986,1043818f,00100500'
  Controls      : 23
  Simple ctrls  : 14
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [off]
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [off]
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [on]
  Front Left: Playback 22 [71%] [-1.50dB] [off]
  Front Right: Playback 22 [71%] [-1.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Phone',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [off]
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mono',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]

!!-------Mixer controls for card 1 [Camera]

Card hw:1 'Camera'/'Vimicro Co.,ltd DVC FINE PC Camera at usb-0000:00:0b.1-3, high speed'
  Mixer name	: 'USB Mixer'
  Components	: 'USB0ac8:332d'
  Controls      : 3
  Simple ctrls  : 2
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 32
  Mono: Capture 0 [0%] [-27.00dB] [on]
Simple mixer control 'Auto Gain Control',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.NVidia {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 23
		value.1 23
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PCM Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 31
		value.1 31
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Aux Playback Volume'
		value.0 0
		value.1 0
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Aux Playback Switch'
		value.0 false
		value.1 false
	}
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value.0 22
		value.1 22
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mic Boost'
		value.0 0
		value.1 0
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.16 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 CD
		comment.item.2 Aux
		comment.item.3 Line
		comment.item.4 Mix
		comment.item.5 Mono
		comment.item.6 Phone
		iface MIXER
		name 'Capture Source'
		value Mic
	}
	control.17 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.18 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.19 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		comment.dbmin -4500
		comment.dbmax 0
		iface MIXER
		name 'Beep Playback Volume'
		value 15
	}
	control.23 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Beep Playback Switch'
		value false
	}
}
state.Camera {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Capture Switch'
		value true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 32'
		comment.dbmin -2700
		comment.dbmax 2100
		iface MIXER
		name 'Mic Capture Volume'
		value 0
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Auto Gain Control'
		value false
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
aes_i586
aes_generic
xt_limit
xt_tcpudp
ipt_LOG
ipt_MASQUERADE
xt_DSCP
ipt_REJECT
nf_conntrack_irc
nf_conntrack_ftp
xt_state
binfmt_misc
snd_hda_codec_analog
arc4
nvidia
iptable_nat
nf_nat
nf_conntrack_ipv4
nf_conntrack
nf_defrag_ipv4
iptable_mangle
iptable_filter
ip_tables
x_tables
snd_usb_audio
snd_usbmidi_lib
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
ath5k
snd_seq_midi_event
mac80211
snd_seq
ath
snd_timer
snd_seq_device
uvcvideo
videodev
cfg80211
v4l1_compat
snd
ppdev
led_class
joydev
parport_pc
psmouse
soundcore
serio_raw
snd_page_alloc
i2c_nforce2
asus_atk0110
agpgart
lp
parport
hid_logitech
ff_memless
usbhid
hid
skge
sata_nv
pata_amd


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x1a 0x0221401f
0x1b 0x01014010
0x1c 0x01a19020
0x1d 0x01813021
0x1e 0x511711f0
0x1f 0x02a19022
0x20 0x01813023
0x21 0x9997e1f0
0x22 0x9933112e
0x23 0x59b771f0
0x24 0x51f711f0
0x25 0x0145f1f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   11.017380] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   11.017386] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   11.017388] hda_intel: Disable MSI for Nvidia chipset
[   11.017413] HDA Intel 0000:00:10.1: setting latency timer to 64
[   11.093370] usbcore: registered new interface driver snd-usb-audio
--
[87448.563482] Inbound IN=eth0 OUT= MAC=00:18:f3:5a:66:70:00:1d:7e:f0:9e:3d:08:00 SRC=200.175.156.212 DST=192.168.11.5 LEN=147 TOS=0x00 PREC=0x00 TTL=53 ID=40741 PROTO=ICMP TYPE=3 CODE=3 [SRC=192.168.11.5 DST=200.175.156.212 LEN=119 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=UDP SPT=51003 DPT=1062 LEN=99 ] 
[87926.772012] hda_codec: invalid CONNECT_LIST verb 12[2]:2100


```

---

### Post by ozzman2 on 2010-10-29
lidex, thank you so much for all your time and help!  I honestly would have just given up without you - and I did learn a lot along the way.  Thank you.

I finally have this machine  working right - but I did end up formatting and starting over.  My system was just too screwed up from the many (failed) previous attempts.  All along, I had been trying to get the 5.1 going in Totem.  In the end, all I needed to do was install VLC instead.  

...Unless of course you know another alternative :P

---

### Post by johnmay on 2010-10-29
lidex,

I am facing a similar issue, where the sound card shoes up yet I cannot hear anything. Right now I am on 10.04, though I had the same problem on 10.10 

I used the bug audio info and submitted a bug which is located:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/668210](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/668210)

I will also run the commands that you provided for the others and post them at a later time

Thanks!  I really want to feel secure about shredding!

:guitar:

---

### Post by lidex on 2010-10-30
> **ozzman2 said:**
> lidex, thank you so much for all your time and help!  I honestly would have just given up without you - and I did learn a lot along the way.  Thank you.

I finally have this machine  working right - but I did end up formatting and starting over.  My system was just too screwed up from the many (failed) previous attempts.  All along, I had been trying to get the 5.1 going in Totem.  In the end, all I needed to do was install VLC instead.  

...Unless of course you know another alternative :P

I used totem for about two days when I began using ubuntu. It's been Mplayer and vlc since.

---

### Post by ozzman2 on 2010-11-03
> **lidex said:**
> I used totem for about two days when I began using ubuntu. It's been Mplayer and vlc since.

I'm hearing ya.
;-)

---

### Post by Lucky75 on 2010-11-03
Still having problems on my end if anyone has a solution. Thanks!

---

### Post by Lucky75 on 2010-11-15
bump

---

