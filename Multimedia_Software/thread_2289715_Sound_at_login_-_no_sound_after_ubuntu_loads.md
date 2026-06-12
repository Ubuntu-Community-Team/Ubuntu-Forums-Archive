---
title: "Sound at login - no sound after ubuntu loads?"
date: 2015-08-06
forum: Multimedia Software
---

### Post by Ace..... on 2015-08-06
[SIZE=3]**Sound at login - no sound after ubuntu loads?**[/SIZE]

This has been a problem, I think since I upgraded to 12.04.

The drum roll at login shows that the speaker works.
Pulse audio panel shows that sound is passing through the sys, as the monitor bar is jumping around nicely.

No config changes I make in Pulse nor Sound settings make a difference.

Can I check for a conflict, when ubuntu loads?

Note: sound will exit, but only through external speakers.... only this is a laptop.... so that's pointless.
However it ties it down to an area.

Note it is a single internal speaker.

Anybody any ideas?

---

### Post by Ace..... on 2015-08-06
> **Ace..... said:**
> 
[SIZE=3]**Sound at login - no sound after ubuntu loads?**[/SIZE]

This has been a problem, I think since I upgraded to 12.04.

The drum roll at login shows that the speaker works.
Pulse audio panel shows that sound is passing through the sys, as the monitor bar is jumping around nicely.

No config changes I make in Pulse nor Sound settings make a difference.

Can I check for a conflict, when ubuntu loads?

Note: sound will exit, but only through external speakers.... only this is a laptop.... so that's pointless.
However it ties it down to an area.

Note it is a single internal speaker.

Anybody any ideas?


Could a problem with fglrx cause this?

I recently removed 37 kernels, and it identified a problem with fglrx:
```
-------- Uninstall Beginning --------
Module:  fglrx-updates
Version: 13.350.1
Kernel:  3.2.0-87-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

fglrx_updates.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-87-generic/updates/dkms/
 - Original module
**[COLOR=#0000cd]   - No original module was found for this module on this kernel.[/COLOR]**
**[COLOR=#0000cd]   - Use the dkms install command to reinstall any previous module version.[/COLOR]**
```

When I ran FSlint [COLOR=#000000] - largest package installed is fglrx updates 259.7M
I note DKMS is [/COLOR]Dynamic Kernel Module Support.

[COLOR=#000000]Could this be to do with sound...... or should I start another thread, say in General Help?

:)

[/COLOR]

---

### Post by Ace..... on 2015-08-06
Saw on this page a tip:
[http://askubuntu.com/questions/135778/no-sound-on-ubuntu-12-04](http://askubuntu.com/questions/135778/no-sound-on-ubuntu-12-04)

```
[COLOR=#000080]sudo killall pulseaudio[/COLOR]
mark@mark-eME644:~$ [COLOR=#000080]sudo alsa force-reload[/COLOR]
Unloading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc ([COLOR=#000080]failed: modules still loaded[/COLOR]: snd-hda-codec-conexant snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-conexant snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```
It looks like the kill all didn't work.
I'll try again without any progs running.

logged out logged back in ran the commands..... same result.

---

### Post by Ace..... on 2015-08-06
I've been reading:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

```
killall pulseaudio; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*; ~/.config/pulse
```
This first suggestion drew a blank, because it couldn't find a .config/pulse directory.

They also suggest this...... however one [commenter stated]("http://askubuntu.com/a/171693") that running it, ruined his login screen

```
sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
```

Has anybody any experience running this command?

---

### Post by Yellow Pasque on 2015-08-06
> **Ace..... said:**
> This first suggestion drew a blank, because it couldn't find a .config/pulse directory.
The pulse settings weren't moved to .config until Ubuntu 13.04. The command sequence is meant to work on older and newer versions, so one of the rm commands will definitely fail.

Also, note that if you kill pulseaudio, it will instantly respawn/restart itself unless you tell it not to:
```
echo autospawn = no >> ~/.pulse/client.conf
```

> Has anybody any experience running this command?
I wouldn't run it, and if I did, I would omit the lightdm reinstall, as your login sound is working. I'm personally not a fan of these "reinstall everything" commands.

I would try creating another user and seeing if sound works for them.

---

### Post by Ace..... on 2015-08-07
> **Temüjin said:**
> 
The pulse settings weren't moved to .config until Ubuntu 13.04. The command sequence is meant to work on older and newer versions, so one of the rm commands will definitely fail.

Also, note that if you kill pulseaudio, it will instantly respawn/restart itself unless you tell it not to:
```
echo autospawn = no >> ~/.pulse/client.conf
```
I wouldn't run it, and if I did, I would omit the lightdm reinstall, as your login sound is working. I'm personally not a fan of these "reinstall everything" commands.

I would try creating another user and seeing if sound works for them.

**Thanks for your response.**
The Ubuntu Document below, states the killall command was specifically for 12.04 and later.
Your comments, and my testing, indicate there may be an error in that documentation:

[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
> **[COLOR=#000080]#1A. If you are using Ubuntu 12.04.3 LTS (Precise Pangolin) or later, try this first: [/COLOR]**

killall pulseaudio; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*; ~/.config/pulse
wait ten seconds, then run this: 
pulseaudio -k 

#1B. Should the approach above fail to correct the problem (it is only known to work on some variations), you can try this next. If you are using Ubuntu 12.04.3 LTS (Precise Pangolin) or later: 

killall pulseaudio; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*; ~/.config/pulse
wait 10 seconds, then reboot (putting the machine to sleep is not enough -- fully power it off and then back on). Make sure to save your work first. 

#1C. If that still did not help, please proceed...

If you are using Ubuntu 12.04.3 LTS (Precise Pangolin) or Ubuntu 14.04 LTS (trusty), then execute this command and reboot:

sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`

Concerning Ubuntu releases older than Ubuntu 12.04 LTS (Precise), please read this: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)


Re: the command, or the 'command assembly'........ it's frightening.
The Ubuntu doc warns:
**"Please exercise caution when running these commands! Carefully read and understand what they do."**

...... easily said ;)

I don't feel confident ...... why reinstall ubuntu-desktop, when I have no sound in XFCE / Xubuntu ?
I installed the latter, after I'd lost sound.
.... and as Temüjin said..... why install lightdm?

It seems that a specific command could have the wrong switch, because the sound feed is present..... it is just not being channeled to the speaker.

[B]Can we determine which command 'channels' sound to the speaker?

Or is it just a case of trying everything?[/B]

---

### Post by Ace..... on 2015-08-07
[SIZE=3]**Moving on to more in depth testing:**[/SIZE]
```
wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh && chmod +x ./alsa-info.sh && ./alsa-info.sh
```

Running it, I noted that the driver version (24) was different to the library and utilities version (25).
[Sound Trouble Shooting]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") Step 3 stated they should all be the same.

As a consequence; to update, I ran:

```
bash alsa-info.sh --stdout
```

I ran the test again, yet still the version numbers are different.
My kernel generation is fine: 3.2.0-88-generic

The test log is below:
The version numbers are just a few lines down.

It appears that this therefore is incorrect, and that I should upgrade the ALSA components.

The commands to achieve this are contained in the large command assembly discussed earlier.
> **[COLOR=#000080]sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install[/COLOR]** pavucontrol linux-sound-base **[COLOR=#000080]alsa-base[/COLOR]** **[COLOR=#000080]alsa-utils[/COLOR]** lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; **[COLOR=#000080]sudo apt-get -y --reinstall install[/COLOR]** linux-sound-base **[COLOR=#000080]alsa-base alsa-utils[/COLOR]** lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`

**How should I write the command?**
Do I exclude anything without a reference to alsa?

Eg.
```
sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install alsa-base alsa-utils; sudo apt-get -y --reinstall install alsa-base alsa-utils
```
Please correct me. ;)


**Here's the test log:**

Anybody familiar with these test results might be able to spot another problem, but I guess the first thing is to get the driver up to date.

```
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Fri Aug  7 14:49:10 UTC 2015


!!Linux Distribution
!!------------------

Ubuntu 12.04.5 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.5 LTS)"


!!DMI Information
!!---------------

Manufacturer:      eMachines
Product Name:      eME644
Product Version:   V1.07
Firmware Version:  V1.07


!!Kernel Information
!!------------------

Kernel release:    3.2.0-88-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xd0444000 irq 40
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd0440000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:01.1 0403: 1002:1314
    Subsystem: 1025:0520
--
00:14.2 0403: 1002:4383 (rev 40)
    Subsystem: 1025:0520


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
!!---------------------------

!!Module: snd_hda_intel
    align_buffer_size : Y
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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
    snoop : Y

!!Module: snd_hda_intel
    align_buffer_size : Y
    bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
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
    snoop : Y


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Converter: stream=1, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02
Codec: Conexant CX20584
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x14f15068
Subsystem Id: 0x10250520
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x10 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x47 0x47]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x47 0x47]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x12 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x13 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x00]
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="CONEXANT Analog", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x50 0x50] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=4, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x15 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x16 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x17* 0x18 0x23 0x24
Node 0x17 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x04 0x04]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x18 [Audio Selector] wcaps 0x30050d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 4
     0x1a* 0x1b 0x1d 0x1e
Node 0x19 [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Headphone Jack", index=0, device=0
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x04211040: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11*
Node 0x1a [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00001324: IN Detect
    Vref caps: HIZ 50 80
  Pin Default 0x95a70120: [Fixed] Mic at Int Top
    Conn = Analog, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Mic Jack", index=0, device=0
  Pincap 0x00011334: IN OUT EAPD Detect
    Vref caps: HIZ 50 80
  EAPD 0x2: EAPD
  Pin Default 0x04a11030: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010034: IN OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x1e [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x92170110: [Fixed] Speaker at Int Front
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D3, actual=D3
  Connection: 2
     0x10* 0x11
Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x22 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 1
     0x21
Node 0x23 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x04, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400001f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
Node 0x24 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Power states:  D0 D1 D2 D3 D3cold
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T  1 root audio 116,  4 Aug  7 16:46 /dev/snd/controlC0
crw-rw---T  1 root audio 116,  8 Aug  7 16:46 /dev/snd/controlC1
crw-rw---T  1 root audio 116,  3 Aug  7 16:46 /dev/snd/hwC0D0
crw-rw---T  1 root audio 116,  7 Aug  7 16:46 /dev/snd/hwC1D0
crw-rw---T  1 root audio 116,  2 Aug  7 16:46 /dev/snd/pcmC0D3p
crw-rw---T  1 root audio 116,  6 Aug  7 16:46 /dev/snd/pcmC1D0c
crw-rw---T  1 root audio 116,  5 Aug  7 16:46 /dev/snd/pcmC1D0p
crw-rw---T  1 root audio 116,  1 Aug  7 16:46 /dev/snd/seq
crw-rw---T  1 root audio 116, 33 Aug  7 16:46 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Aug  7 16:46 .
drwxr-xr-x 3 root root 240 Aug  7 16:46 ..
lrwxrwxrwx 1 root root  12 Aug  7 16:46 pci-0000:00:01.1 -> ../controlC0
lrwxrwxrwx 1 root root  12 Aug  7 16:46 pci-0000:00:14.2 -> ../controlC1


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Generic]

Card hw:0 'Generic'/'HD-Audio Generic at 0xd0444000 irq 40'
  Mixer name    : 'ATI R6xx HDMI'
  Components    : 'HDA:1002aa01,00aa0100,00100200'
  Controls      : 6
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [SB]

Card hw:1 'SB'/'HDA ATI SB at 0xd0440000 irq 16'
  Mixer name    : 'Conexant CX20584'
  Components    : 'HDA:14f15068,10250520,00100302'
  Controls      : 16
  Simple ctrls  : 9
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 74
  Mono: Playback 71 [96%] [-3.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 7 [100%] [0.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [on]
  Front Right: Capture 80 [100%] [6.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%] [40.00dB]
  Front Right: 4 [100%] [40.00dB]


!!Alsactl output
!!--------------

--startcollapse--
state.Generic {
    control.1 {
        iface CARD
        name 'HDMI/DP,pcm=3 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.5 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.6 {
        iface PCM
        device 3
        name ELD
        value ''
        comment {
            access read
            type BYTES
            count 0
        }
    }
}
state.SB {
    control.1 {
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 74
        value.1 74
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 74'
            dbmin -7400
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.2 {
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.3 {
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 74
        value.1 74
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 74'
            dbmin -7400
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.4 {
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.5 {
        iface MIXER
        name 'Auto-Mute Mode'
        value Enabled
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Disabled
            item.1 Enabled
        }
    }
    control.6 {
        iface MIXER
        name 'Internal Mic Boost Volume'
        value.0 4
        value.1 4
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 4'
            dbmin 0
            dbmax 4000
            dbvalue.0 4000
            dbvalue.1 4000
        }
    }
    control.7 {
        iface MIXER
        name 'Capture Volume'
        value.0 80
        value.1 80
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 80'
            dbmin -7400
            dbmax 600
            dbvalue.0 600
            dbvalue.1 600
        }
    }
    control.8 {
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.9 {
        iface MIXER
        name 'Master Playback Volume'
        value 71
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 74'
            dbmin -7400
            dbmax 0
            dbvalue.0 -300
        }
    }
    control.10 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.11 {
        iface MIXER
        name 'Beep Playback Volume'
        value 7
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 7'
            dbmin -2800
            dbmax 0
            dbvalue.0 0
        }
    }
    control.12 {
        iface MIXER
        name 'Beep Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.13 {
        iface CARD
        name 'Headphone Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.14 {
        iface CARD
        name 'Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.15 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 255'
            tlv '0000000100000008ffffec1400000014'
            dbmin -5100
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.16 {
        iface MIXER
        name 'Digital Capture Volume'
        value.0 60
        value.1 60
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 120'
            tlv '0000000100000008fffff44800000032'
            dbmin -3000
            dbmax 3000
            dbvalue.0 0
            dbvalue.1 0
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
vesafb
acer_wmi
sparse_keymap
arc4
ath9k
dm_multipath
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
mac80211
snd_seq
ath9k_common
ath9k_hw
ath
cfg80211
snd_seq_device
fglrx
snd_hda_codec_conexant
joydev
snd_hda_codec_hdmi
snd_hda_intel
snd_hda_codec
snd_hwdep
psmouse
serio_raw
snd_pcm
k10temp
snd_timer
i2c_piix4
shpchp
snd
soundcore
snd_page_alloc
mac_hid
wmi
video
parport_pc
ppdev
rfcomm
bnep
bluetooth
lp
parport
binfmt_misc
atl1c
dm_raid45
xor
usbhid
dm_mirror
dm_region_hash
dm_log
hid


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:

/sys/class/sound/hwC1D0/init_pin_configs:
0x19 0x04211040
0x1a 0x95a70120
0x1b 0x04a11030
0x1c 0x400001f0
0x1d 0x400001f0
0x1e 0x400001f0
0x1f 0x92170110
0x20 0x400001f0
0x22 0x400001f0
0x23 0x400001f0

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D0/hints:


!!ALSA/HDA dmesg
!!--------------

[   22.149383] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   22.382887] snd_hda_intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   22.383017] snd_hda_intel 0000:00:01.1: irq 40 for MSI/MSI-X
[   22.383068] snd_hda_intel 0000:00:01.1: setting latency timer to 64
[   22.436088] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   22.436533] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input8
[   22.439890] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.439997] snd_hda_intel 0000:00:14.2: setting latency timer to 64
[   22.514658] hda_codec: CX20584: BIOS auto-probing.
[   22.536234] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input9
[   22.538689] [fglrx] Maximum main memory to use for locked dma buffers: 2597 MBytes.
[   22.539607] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
[   22.562783] [fglrx]   vendor: 1002 device: 9804 count: 1



```

---

### Post by Ace..... on 2015-08-08
Ran the command:
```
sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install alsa-base alsa-utils; sudo apt-get -y --reinstall install alsa-base alsa-utils
```

Retested using:
```
wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh && chmod +x ./alsa-info.sh && ./alsa-info.sh
```

> !!ALSA Version
!!------------
Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25


This is annoying news.
The driver version should have changed to 25.

I've joined the Alsa mail group, and alerted them to the situation.

Anybody any ideas?

---

### Post by Yellow Pasque on 2015-08-08
> The driver version should have changed to 25.
No, the driver version is based on the kernel module. If you want to update it, see [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

> I've joined the Alsa mail group, and alerted them to the situation.
Alerted them of what? If your sound works at the login screen, but not after you login, then this is probably a pulseaudio issue. Have you tried creating another user yet? Are you trying to use the motherboard audio or the HDMI audio? Have you made sure the proper device is selected?
```
pavucontrol
```

---

### Post by Ace..... on 2015-08-08
> **Temüjin said:**
> No, the driver version is based on the kernel module. If you want to update it, see [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
Alerted them of what? 
[COLOR=#000080]**If your sound works at the login screen, but not after you login, then this is probably a pulseaudio issue.**[/COLOR] 
Have you tried creating another user yet? 
Are you trying to use the motherboard audio or the HDMI audio? 
Have you made sure the proper device is selected?
```
pavucontrol
```

Thank you Temüjin for that insight :)
This could be key information that really helps tie down the area to look at......... it could be the key to solving this issue.

**Re: Alerted them of what? **

I linked to the [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) (step 3)
and the advice given on how to re-install alsa...... and the fact that my driver remains at v24, when the other drivers are at v25.

I also provided the link to their 'script output' (they have an auto upload to their site from terminal)...... in the hope that somebody might confirm if there is a problem with the mismatching versions.
Additionally, I listed the command used to re-install the alsa components (my previous post in this thread).

Primarily, I'm hoping to get a view from Alsa experts, as to whether the root cause of my sound problems, can be traced back to the mismatching drivers.
Either way..... there appears to be a problem with that, according to Ubuntu documentation.

**Re: If you want to update it, see [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)**

Thanks for that link.... I'll try it and report back.

**Re: Have you tried creating another user yet?**
 
Not as yet.
It may seem like I'm working slowly..... but I first chose to move through those Sound Trouble Shooting steps, and check the Alsa versions.
At this point I had no knowledge of the fact that the problem is most likely due to a pulseaudio issue.

I'm thinking of using these commands:
```
[FONT=monospace]sudo useradd -d /home/testuser -m testuser
[/FONT][FONT=monospace]sudo passwd testuser[/FONT]
```

**Re: Are you trying to use the motherboard audio or the HDMI audio? **

:) While I am fairly certain, the sound coming out of my internal speaker is not HDMI..... I am human..... I've tried all configs :)

I've managed to locate two audio panels: Pulse & Std Sound Settings.
No change of config produced the required result :(

**Re: Have you made sure the proper device is selected?**

Assuming that this is achieved in one of the two control panels...... I presume that I must have done.

For Std. Sound Settings:
I'm favouring in output: 'built in audio analogue stereo' rather than HDMI (there are only two options, and I've tried both).
Hardware is set at duplex..... so that the mic will work..... but I've tried them all.

In pulse.... playback shows chromium playing the sound on the monitor bar..... but nothing from the speaker.

Obv... tried mute and volume.

**So where are we?**

I think that first I must try the DKMS upgrade.
Then try adding a new user.

Let's take it from there.

Thanks again for the support :)

---

### Post by Ace..... on 2015-08-08
Okay.....following on from my previous post..... **I tried the DKMS install**
```
sudo apt-get install dkms
```
It reports I already have the latest version.

Checked out the 2nd page of packages.
It's a bit of a nightmare.
> the output of "uname -r" starts with... 3.2 
- use the oem-audio-hda-daily-dkms


Under the new section "Package files", click the file ending with "**.deb**", download and install it:

The problem is that **oem-audio-hda-daily-dkms** only has packages ending in:
.dsc
.tar.gz

So for the time being, i must assume that DKMS is up to date.

**New User**
Added testuser.
No change :(

**Next step?**
If the thinking that this is a pulse audio problem...... are there any pulse audio tests?

---

### Post by Yellow Pasque on 2015-08-08
> and the fact that my driver remains at v24, when the other drivers are at v25.
This is not an issue/problem. These are the correct versions for Ubuntu Precise. I guess other people were confused by mismatching component versions, which is why ALSA devs switched to simply printing the kernel version in newer alsa info (example: [http://www.alsa-project.org/db/?f=765ebb6d1347e57bab7bace7b49a92e6e5d0391a](http://www.alsa-project.org/db/?f=765ebb6d1347e57bab7bace7b49a92e6e5d0391a) )

> the sound coming out of my internal speaker is not HDMI
I missed the internal speaker part.

---

### Post by Ace..... on 2015-08-08
> **Temüjin said:**
> This is not an issue/problem. These are the correct versions for Ubuntu Precise. I guess other people were confused by mismatching component versions, which is why ALSA devs switched to simply printing the kernel version in newer alsa info (example: [http://www.alsa-project.org/db/?f=765ebb6d1347e57bab7bace7b49a92e6e5d0391a](http://www.alsa-project.org/db/?f=765ebb6d1347e57bab7bace7b49a92e6e5d0391a) )

I missed the internal speaker part.

Thanks for confirming that there is no problem with v24 and v25 existing together.
When this is over, I think I will contact the authors of the sound trouble shooting doc, and alert them to some of the conflicting info that we have experienced.

Anyway..... Latest Test....... and it could be informative.

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

States that this code often fixes no sound probs (log out/in), for 12.1 and earlier:
```
rm -r ~/.pulse*; pulseaudio -k
```

Result:
```
rm -r ~/.pulse*; pulseaudio -k
**E: [pulseaudio] main.c: Failed to kill daemon: No such process**

```

So the process that should be running.... isn't?

EDIT: just thinking..... should I try your norespawn kill command.
If I reboot, will pulseaudio then respawn?

---

### Post by Ace..... on 2015-08-08
**2nd Test following on from last test a few minutes ago:**

```
pacmd
No PulseAudio daemon running, or not running as session daemon.

```

Okay, so these two tests show that even though the pulseaudio panel runs, there is a problem with both test results.

Surely we are nearly there now :)

---

### Post by Yellow Pasque on 2015-08-08
Hmm, based on your previous info that you could see the sound bar when playing sound and your alsa info saying the following, I thought pulseaudio was at least starting/running.
```
Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes
```

So, maybe the next step is to get a log and see why pulseaduio is not starting (or crashing). [https://wiki.ubuntu.com/PulseAudio#Getting_A_Verbose_Diagnostic_Log](https://wiki.ubuntu.com/PulseAudio#Getting_A_Verbose_Diagnostic_Log)

---

### Post by Ace..... on 2015-08-08
> **Temüjin said:**
> Hmm, based on your previous info that you could see the sound bar when playing sound and your alsa info saying the following, I thought pulseaudio was at least starting/running.
```
Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes
```

So, maybe the next step is to get a log and see why pulseaduio is not starting (or crashing). [https://wiki.ubuntu.com/PulseAudio#Getting_A_Verbose_Diagnostic_Log](https://wiki.ubuntu.com/PulseAudio#Getting_A_Verbose_Diagnostic_Log)

I ran it for just 30 seconds or so.
Haven't really examined it yet, but I'm about to do so.
Looking forward to comments.

tried to upload it but the file must be too large.
I'll split it up into 3

part 1:

```
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
(   0.000|   0.000) D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
(   0.026|   0.025) D: [pulseaudio] core-util.c: RealtimeKit worked.
(   0.026|   0.000) I: [pulseaudio] core-util.c: Successfully gained nice level -11.
(   0.026|   0.000) I: [pulseaudio] main.c: This is PulseAudio 1.1
(   0.026|   0.000) D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
(   0.026|   0.000) D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
(   0.026|   0.000) D: [pulseaudio] main.c: Running on host: Linux x86_64 3.2.0-88-generic #126-Ubuntu SMP Mon Jul 6 21:33:03 UTC 2015
(   0.026|   0.000) D: [pulseaudio] main.c: Found 2 CPUs.
(   0.026|   0.000) I: [pulseaudio] main.c: Page size is 4096 bytes
(   0.026|   0.000) D: [pulseaudio] main.c: Compiled with Valgrind support: no
(   0.026|   0.000) D: [pulseaudio] main.c: Running in valgrind mode: no
(   0.027|   0.000) D: [pulseaudio] main.c: Running in VM: no
(   0.027|   0.000) D: [pulseaudio] main.c: Optimized build: yes
(   0.027|   0.000) D: [pulseaudio] main.c: All asserts enabled.
(   0.027|   0.000) I: [pulseaudio] main.c: Machine ID is dcb82b7097b3082e6a16dada0000000a.
(   0.027|   0.000) I: [pulseaudio] main.c: Session ID is dcb82b7097b3082e6a16dada0000000a-1439071373.346840-469937643.
(   0.027|   0.000) I: [pulseaudio] main.c: Using runtime directory /home/mark/.pulse/dcb82b7097b3082e6a16dada0000000a-runtime.
(   0.027|   0.000) I: [pulseaudio] main.c: Using state directory /home/mark/.pulse.
(   0.027|   0.000) I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-1.1/modules.
(   0.027|   0.000) I: [pulseaudio] main.c: Running in system mode: no
(   0.028|   0.000) I: [pulseaudio] main.c: Fresh high-resolution timers available! Bon appetit!
(   0.029|   0.000) D: [pulseaudio] memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472
(   0.029|   0.000) I: [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 MMXEXT 
(   0.029|   0.000) I: [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions.
(   0.029|   0.000) I: [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers.
(   0.029|   0.000) I: [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions.
(   0.029|   0.000) I: [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers.
(   0.029|   0.000) I: [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions.
(   0.029|   0.000) I: [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions.
(   0.032|   0.002) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/mark/.pulse/dcb82b7097b3082e6a16dada0000000a-device-volumes.tdb'
(   0.032|   0.000) I: [pulseaudio] module-device-restore.c: Successfully opened database file '/home/mark/.pulse/dcb82b7097b3082e6a16dada0000000a-device-volumes'.
(   0.032|   0.000) I: [pulseaudio] module.c: Loaded "module-device-restore" (index: #0; argument: "").
(   0.034|   0.001) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/mark/.pulse/dcb82b7097b3082e6a16dada0000000a-stream-volumes.tdb'
(   0.034|   0.000) I: [pulseaudio] module-stream-restore.c: Successfully opened database file '/home/mark/.pulse/dcb82b7097b3082e6a16dada0000000a-stream-volumes'.
(   0.034|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 added for object /org/pulseaudio/stream_restore1
(   0.034|   0.000) I: [pulseaudio] module.c: Loaded "module-stream-restore" (index: #1; argument: "").
(   0.036|   0.001) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/mark/.pulse/dcb82b7097b3082e6a16dada0000000a-card-database.tdb'
(   0.036|   0.000) I: [pulseaudio] module-card-restore.c: Successfully opened database file '/home/mark/.pulse/dcb82b7097b3082e6a16dada0000000a-card-database'.
(   0.036|   0.000) I: [pulseaudio] module.c: Loaded "module-card-restore" (index: #2; argument: "").
(   0.037|   0.000) I: [pulseaudio] module.c: Loaded "module-augment-properties" (index: #3; argument: "").
(   0.037|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-udev-detect.so': success
(   0.040|   0.003) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(   0.041|   0.000) D: [pulseaudio] module-udev-detect.c: /devices/pci0000:00/0000:00:01.1/sound/card0 is busy: no
(   0.041|   0.000) D: [pulseaudio] module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="0" name="pci-0000_00_01.1" card_name="alsa_card.pci-0000_00_01.1" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"'
(   0.052|   0.011) D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus session bus 1a722241f0a166c614f98d3600000044 as :1.115
(   0.054|   0.001) D: [pulseaudio] reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
(   0.056|   0.002) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-mono
(   0.056|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
(   0.056|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.061|   0.004) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.062|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.062|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-mono+input:analog-mono
(   0.062|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
(   0.062|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.062|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.062|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.062|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-mono+input:analog-stereo
(   0.062|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
(   0.062|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.063|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.063|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.063|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-mono+input:iec958-stereo
(   0.063|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
(   0.063|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.063|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.063|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.064|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo
(   0.064|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
(   0.064|   0.000) D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.071|   0.007) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.072|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: No such file or directory
(   0.072|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.072|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.072|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.072|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-mono
(   0.072|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
(   0.072|   0.000) D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.073|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.073|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: No such file or directory
(   0.073|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.073|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.073|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.073|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-stereo
(   0.073|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
(   0.073|   0.000) D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.074|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.074|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: No such file or directory
(   0.074|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.074|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.075|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.075|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo+input:iec958-stereo
(   0.075|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
(   0.075|   0.000) D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.075|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.075|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: No such file or directory
(   0.075|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.076|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.076|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.076|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-40
(   0.076|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
(   0.076|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.076|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.076|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround40:0: No such file or directory
(   0.077|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-mono
(   0.077|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
(   0.077|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.077|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.077|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround40:0: No such file or directory
(   0.077|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-stereo
(   0.077|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
(   0.077|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.078|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.078|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround40:0: No such file or directory
(   0.078|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-stereo
(   0.078|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
(   0.078|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.079|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.079|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround40:0: No such file or directory
(   0.079|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-41
(   0.079|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
(   0.079|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.080|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.080|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround41:0: No such file or directory
(   0.080|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-mono
(   0.080|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
(   0.080|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.080|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.081|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround41:0: No such file or directory
(   0.081|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-stereo
(   0.081|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
(   0.081|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.081|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.081|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround41:0: No such file or directory
(   0.081|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-stereo
(   0.081|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
(   0.081|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.082|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.082|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround41:0: No such file or directory
(   0.082|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50
(   0.082|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
(   0.082|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.083|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.083|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:0: No such file or directory
(   0.083|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-mono
(   0.083|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
(   0.083|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.084|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.084|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:0: No such file or directory
(   0.084|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-stereo
(   0.084|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
(   0.084|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.084|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.084|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:0: No such file or directory
(   0.085|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-stereo
(   0.085|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
(   0.085|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.085|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.085|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:0: No such file or directory
(   0.085|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51
(   0.085|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
(   0.085|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.086|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.086|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:0: No such file or directory
(   0.086|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-mono
(   0.086|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
(   0.086|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.087|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.087|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:0: No such file or directory
(   0.087|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-stereo
(   0.087|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
(   0.087|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.088|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.088|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:0: No such file or directory
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-stereo
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
(   0.088|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.088|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.088|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:0: No such file or directory
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71
(   0.088|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
(   0.088|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.089|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.089|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:0: No such file or directory
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-mono
(   0.089|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
(   0.089|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.090|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.090|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:0: No such file or directory
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-stereo
(   0.090|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
(   0.090|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.091|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.091|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:0: No such file or directory
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-stereo
(   0.091|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
(   0.091|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.091|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.092|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:0: No such file or directory
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo
(   0.092|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
(   0.092|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.092|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
(   0.093|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-mono
(   0.093|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
(   0.093|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.093|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
(   0.094|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-stereo
(   0.094|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
(   0.094|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.094|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
(   0.094|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-stereo
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
(   0.095|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.095|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
(   0.095|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
(   0.095|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
(   0.096|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.096|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
(   0.096|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-mono
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
(   0.096|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.096|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
(   0.096|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-stereo
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
(   0.096|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.096|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
(   0.096|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-stereo
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
(   0.096|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.096|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
(   0.096|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
(   0.096|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
(   0.096|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.096|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
(   0.097|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-mono
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
(   0.097|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.097|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
(   0.097|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-stereo
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
(   0.097|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.097|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
(   0.097|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-stereo
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
(   0.097|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.097|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
(   0.097|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo
(   0.097|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
(   0.097|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.099|   0.001) D: [pulseaudio] alsa-util.c: Managed to open hdmi:0
(   0.099|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.099|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
(   0.099|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:hdmi-stereo supported.
(   0.100|   0.000) I: [pulseaudio] (alsa-lib)control.c: Invalid CTL hdmi:0
(   0.100|   0.000) I: [pulseaudio] alsa-util.c: Unable to attach to mixer hdmi:0: No such file or directory
(   0.100|   0.000) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'hdmi-output-0'
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'HDMI/DP,pcm=3 Jack' succeeded (found!)
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Path Set 0x1c458b0, direction=1
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Path hdmi-output-0 (HDMI / DisplayPort), direction=1, priority=59, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Jack HDMI/DP,pcm=3, alsa_name='HDMI/DP,pcm=3 Jack', detection possible
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-mono
(   0.100|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
(   0.100|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.101|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
(   0.101|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-stereo
(   0.101|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.101|   0.000) D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.102|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
(   0.102|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: No such file or directory
(   0.102|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.102|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
(   0.102|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-stereo
(   0.102|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
(   0.102|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.103|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
(   0.103|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile input:analog-mono
(   0.103|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
(   0.104|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.104|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
(   0.104|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.104|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile input:analog-stereo
(   0.104|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.104|   0.000) D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.105|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
(   0.105|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: No such file or directory
(   0.105|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.105|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
(   0.105|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.105|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile input:iec958-stereo
(   0.105|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
(   0.105|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.106|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
(   0.106|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
(   0.107|   0.000) D: [pulseaudio] alsa-mixer.c: Profile set 0x1c18120, auto_profiles=yes, probed=yes, n_mappings=1, n_profiles=1, n_decibel_fixes=0
(   0.107|   0.000) D: [pulseaudio] alsa-mixer.c: Mapping hdmi-stereo (Digital Stereo (HDMI)), priority=54, channel_map=front-left,front-right, supported=yes, direction=1
(   0.107|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:hdmi-stereo (Digital Stereo (HDMI) Output), priority=5400, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.107|   0.000) D: [pulseaudio] alsa-mixer.c: Output hdmi-stereo
(   0.107|   0.000) D: [pulseaudio] module-card-restore.c: Database contains invalid data for key: alsa_card.pci-0000_00_01.1 (probably pre-v1.0 data)
(   0.107|   0.000) D: [pulseaudio] module-card-restore.c: Attempting to load legacy (pre-v1.0) data for key: alsa_card.pci-0000_00_01.1
(   0.107|   0.000) D: [pulseaudio] module-card-restore.c: Size does not match.
(   0.108|   0.000) D: [pulseaudio] module-card-restore.c: Unable to load legacy (pre-v1.0) data for key: alsa_card.pci-0000_00_01.1. Ignoring.
(   0.108|   0.000) I: [pulseaudio] card.c: Created 0 "alsa_card.pci-0000_00_01.1"
(   0.110|   0.002) D: [pulseaudio] reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio0'
(   0.110|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.112|   0.001) D: [pulseaudio] alsa-util.c: Managed to open hdmi:0
(   0.112|   0.000) I: [pulseaudio] alsa-util.c: Trying to disable ALSA period wakeups, using timers only
(   0.112|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.112|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
(   0.112|   0.000) I: [pulseaudio] alsa-util.c: ALSA period wakeups disabled
(   0.112|   0.000) I: [pulseaudio] alsa-sink.c: Successfully opened device hdmi:0.
(   0.112|   0.000) I: [pulseaudio] alsa-sink.c: Selected mapping 'Digital Stereo (HDMI)' (hdmi-stereo).
(   0.112|   0.000) I: [pulseaudio] alsa-sink.c: Successfully enabled mmap() mode.
(   0.113|   0.000) I: [pulseaudio] alsa-sink.c: Successfully enabled timer-based scheduling mode.
(   0.113|   0.000) I: [pulseaudio] (alsa-lib)control.c: Invalid CTL hdmi:0
(   0.113|   0.000) I: [pulseaudio] alsa-util.c: Unable to attach to mixer hdmi:0: No such file or directory
(   0.113|   0.000) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.114|   0.000) D: [pulseaudio] alsa-mixer.c: Added 1 ports
(   0.114|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:alsa_output.pci-0000_00_01.1.hdmi-stereo (probably pre-v1.0 data)
(   0.114|   0.000) D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink:alsa_output.pci-0000_00_01.1.hdmi-stereo
(   0.114|   0.000) D: [pulseaudio] module-device-restore.c: Size does not match.
(   0.114|   0.000) D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: sink:alsa_output.pci-0000_00_01.1.hdmi-stereo. Ignoring.
(   0.114|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:alsa_output.pci-0000_00_01.1.hdmi-stereo:null
(   0.115|   0.000) I: [pulseaudio] sink.c: Created sink 0 "alsa_output.pci-0000_00_01.1.hdmi-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.resolution_bits = "16"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.api = "alsa"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.class = "sound"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.class = "generic"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.subclass = "generic-mix"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.name = "HDMI 0"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.id = "HDMI 0"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.subdevice = "0"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.subdevice_name = "subdevice #0"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.device = "3"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.card = "0"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.card_name = "HD-Audio Generic"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.long_card_name = "HD-Audio Generic at 0xd0444000 irq 40"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.driver_name = "snd_hda_intel"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.bus_path = "pci-0000:00:01.1"
(   0.115|   0.000) I: [pulseaudio] sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:01.1/sound/card0"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.bus = "pci"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.vendor.id = "1002"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.product.name = "Wrestler HDMI Audio"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.form_factor = "internal"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.string = "hdmi:0"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.buffering.buffer_size = "65536"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.buffering.fragment_size = "32768"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.access_mode = "mmap+timer"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.profile.name = "hdmi-stereo"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.profile.description = "Digital Stereo (HDMI)"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.description = "Built-in Audio Digital Stereo (HDMI)"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.mixer_name = "ATI R6xx HDMI"
(   0.115|   0.000) I: [pulseaudio] sink.c:     alsa.components = "HDA:1002aa01,00aa0100,00100200"
(   0.115|   0.000) I: [pulseaudio] sink.c:     module-udev-detect.discovered = "1"
(   0.115|   0.000) I: [pulseaudio] sink.c:     device.icon_name = "audio-card-pci"
(   0.116|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.116|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_output.pci-0000_00_01.1.hdmi-stereo.monitor (probably pre-v1.0 data)
(   0.116|   0.000) D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: source:alsa_output.pci-0000_00_01.1.hdmi-stereo.monitor
(   0.116|   0.000) D: [pulseaudio] module-device-restore.c: Size does not match.
(   0.116|   0.000) D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: source:alsa_output.pci-0000_00_01.1.hdmi-stereo.monitor. Ignoring.
(   0.116|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_output.pci-0000_00_01.1.hdmi-stereo.monitor:null
(   0.116|   0.000) I: [pulseaudio] source.c: Created source 0 "alsa_output.pci-0000_00_01.1.hdmi-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.116|   0.000) I: [pulseaudio] source.c:     device.description = "Monitor of Built-in Audio Digital Stereo (HDMI)"
(   0.116|   0.000) I: [pulseaudio] source.c:     device.class = "monitor"
(   0.116|   0.000) I: [pulseaudio] source.c:     alsa.card = "0"
(   0.116|   0.000) I: [pulseaudio] source.c:     alsa.card_name = "HD-Audio Generic"
(   0.116|   0.000) I: [pulseaudio] source.c:     alsa.long_card_name = "HD-Audio Generic at 0xd0444000 irq 40"
(   0.116|   0.000) I: [pulseaudio] source.c:     alsa.driver_name = "snd_hda_intel"
(   0.116|   0.000) I: [pulseaudio] source.c:     device.bus_path = "pci-0000:00:01.1"
(   0.116|   0.000) I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:01.1/sound/card0"
(   0.116|   0.000) I: [pulseaudio] source.c:     device.bus = "pci"
(   0.116|   0.000) I: [pulseaudio] source.c:     device.vendor.id = "1002"
(   0.116|   0.000) I: [pulseaudio] source.c:     device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
(   0.116|   0.000) I: [pulseaudio] source.c:     device.product.name = "Wrestler HDMI Audio"
(   0.116|   0.000) I: [pulseaudio] source.c:     device.form_factor = "internal"
(   0.116|   0.000) I: [pulseaudio] source.c:     device.string = "0"
(   0.116|   0.000) I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
(   0.116|   0.000) I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
(   0.116|   0.000) I: [pulseaudio] alsa-sink.c: Using 2.0 fragments of size 32768 bytes (185.76ms), buffer size is 65536 bytes (371.52ms)
(   0.117|   0.000) I: [pulseaudio] alsa-sink.c: Time scheduling watermark is 20.00ms
(   0.117|   0.000) D: [pulseaudio] alsa-sink.c: hwbuf_unused=0
(   0.117|   0.000) D: [pulseaudio] alsa-sink.c: setting avail_min=15502
(   0.117|   0.000) D: [pulseaudio] alsa-mixer.c: Activating path hdmi-output-0
(   0.117|   0.000) D: [pulseaudio] alsa-mixer.c: Path hdmi-output-0 (HDMI / DisplayPort), direction=1, priority=59, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.117|   0.000) D: [pulseaudio] alsa-mixer.c: Jack HDMI/DP,pcm=3, alsa_name='HDMI/DP,pcm=3 Jack', detection possible
(   0.117|   0.000) I: [pulseaudio] alsa-sink.c: Driver does not support hardware volume control, falling back to software volume control.
(   0.117|   0.000) I: [pulseaudio] alsa-sink.c: Driver does not support hardware mute control, falling back to software mute control.
(   0.117|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_dump():
(   0.117|   0.000) D: [pulseaudio] alsa-util.c: Hooks PCM
(   0.117|   0.000) D: [pulseaudio] alsa-util.c: Its setup is:
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   stream       : PLAYBACK
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   format       : S16_LE
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   subformat    : STD
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   channels     : 2
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   rate         : 44100
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   msbits       : 16
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   period_size  : 8192
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   period_time  : 185759
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   period_step  : 1
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   avail_min    : 15502
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   period_event : 0
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   start_threshold  : -1
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   stop_threshold   : 4611686018427387904
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   silence_threshold: 0
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   silence_size : 0
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   boundary     : 4611686018427387904
(   0.117|   0.000) D: [pulseaudio] alsa-util.c: Slave: Hardware PCM card 0 'HD-Audio Generic' device 3 subdevice 0
(   0.117|   0.000) D: [pulseaudio] alsa-util.c: Its setup is:
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   stream       : PLAYBACK
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   format       : S16_LE
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   subformat    : STD
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   channels     : 2
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   rate         : 44100
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   msbits       : 16
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   period_size  : 8192
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   period_time  : 185759
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   period_step  : 1
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   avail_min    : 15502
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   period_event : 0
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   start_threshold  : -1
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   stop_threshold   : 4611686018427387904
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   silence_threshold: 0
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   silence_size : 0
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   boundary     : 4611686018427387904
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   appl_ptr     : 0
(   0.117|   0.000) D: [pulseaudio] alsa-util.c:   hw_ptr       : 0
(   0.119|   0.001) D: [alsa-sink] alsa-sink.c: Thread starting up
(   0.144|   0.025) D: [alsa-sink] core-util.c: RealtimeKit worked.
(   0.144|   0.000) I: [alsa-sink] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
(   0.144|   0.000) I: [alsa-sink] alsa-sink.c: Starting playback.
(   0.144|   0.000) D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(   0.145|   0.000) D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(   0.145|   0.000) D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(   0.145|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:alsa_output.pci-0000_00_01.1.hdmi-stereo:null
(   0.145|   0.000) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.146|   0.000) D: [pulseaudio] module-alsa-card.c: Jack 'HDMI/DP,pcm=3 Jack' is now unplugged
(   0.146|   0.000) D: [pulseaudio] device-port.c: Setting port hdmi-output-0 to status no
(   0.146|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.146|   0.000) I: [pulseaudio] module.c: Loaded "module-alsa-card" (index: #4; argument: "device_id="0" name="pci-0000_00_01.1" card_name="alsa_card.pci-0000_00_01.1" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"").
(   0.146|   0.000) I: [pulseaudio] module-udev-detect.c: Card /devices/pci0000:00/0000:00:01.1/sound/card0 (alsa_card.pci-0000_00_01.1) module loaded.
(   0.146|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
(   0.147|   0.000) D: [pulseaudio] module-udev-detect.c: /devices/pci0000:00/0000:00:14.2/sound/card1 is busy: no
(   0.147|   0.000) D: [pulseaudio] module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="1" name="pci-0000_00_14.2" card_name="alsa_card.pci-0000_00_14.2" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"'
(   0.151|   0.003) D: [pulseaudio] reserve-wrap.c: Successfully acquired reservation lock on device 'Audio1'
(   0.153|   0.002) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-mono
(   0.153|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
(   0.153|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.154|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:1
(   0.154|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.154|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.154|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:1
(   0.155|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.155|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.155|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
(   0.156|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.156|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.156|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
(   0.157|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.157|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:1: Invalid argument
(   0.157|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-mono+input:analog-mono
(   0.157|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
(   0.157|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.158|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:1
(   0.158|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.158|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.158|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:1
(   0.159|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.159|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.159|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
(   0.159|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.160|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.160|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
(   0.161|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.161|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:1: Invalid argument
(   0.161|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-mono+input:analog-stereo
(   0.161|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
(   0.161|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.161|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:1
(   0.162|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.162|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.162|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:1
(   0.162|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.162|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.163|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
(   0.163|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.163|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.163|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
(   0.164|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.164|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:1: Invalid argument
(   0.164|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-mono+input:iec958-stereo
(   0.164|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
(   0.164|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.164|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:1
(   0.165|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.165|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.165|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:1
(   0.165|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.165|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.166|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
(   0.166|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.166|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.166|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
(   0.167|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.167|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:1: Invalid argument
(   0.167|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo
(   0.167|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
(   0.167|   0.000) D: [pulseaudio] alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.168|   0.000) D: [pulseaudio] alsa-util.c: Managed to open front:1
(   0.168|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.169|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
(   0.169|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo supported.
(   0.173|   0.003) I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:1
(   0.173|   0.000) I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:1: No such file or directory
(   0.173|   0.000) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.173|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output'
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line HP Swap' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=2, switch=1, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Surround' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Center' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'LFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-speaker'
(   0.174|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (found!)
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Headphone Jack' succeeded (not found)
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Speaker Phantom Jack' succeeded (not found)
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=1, switch=1, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Surround' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Surround Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Center' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Center Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'LFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'LFE Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
(   0.175|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-speaker'
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=2, switch=2, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' failed.
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-headphones'
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Headphone Jack' succeeded (not found)
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (found!)
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
```

---

### Post by Ace..... on 2015-08-08
Part 2. (continued from previous post):

```


(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=1, switch=1, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line HP Swap' succeeded (volume=0, switch=0, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=2, switch=2, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Surround' succeeded (volume=0, switch=0, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.176|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Center' succeeded (volume=0, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'LFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-headphones'
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' failed.
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-mono'
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=2, switch=2, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' failed.
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-lfe-on-mono'
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' failed.
(   0.177|   0.000) D: [pulseaudio] alsa-mixer.c: Removing path 'analog-output' as it is a subset of 'analog-output-speaker'.
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Path Set 0x1c8fe30, direction=1
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-output-speaker (Speakers), direction=1, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=74, min_dB=-199, max_dB=0
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection possible
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Front Headphone, alsa_name='Front Headphone Jack', detection unavailable
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Speaker Phantom, alsa_name='Speaker Phantom Jack', detection unavailable
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-output-headphones (Headphones), direction=1, priority=90, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=74, min_dB=-199, max_dB=0
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Element Speaker, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Front Headphone, alsa_name='Front Headphone Jack', detection unavailable
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection possible
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Headphone Mic, alsa_name='Headphone Mic Jack', detection unavailable
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-mono
(   0.178|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
(   0.178|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.179|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:1
(   0.179|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.179|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.180|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:1
(   0.180|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.180|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.180|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
(   0.180|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.180|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.181|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
(   0.181|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.181|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:1: Invalid argument
(   0.181|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-stereo
(   0.182|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.182|   0.000) D: [pulseaudio] alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.182|   0.000) D: [pulseaudio] alsa-util.c: Managed to open front:1
(   0.182|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.183|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
(   0.183|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo supported.
(   0.192|   0.009) I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:1
(   0.192|   0.000) I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:1: No such file or directory
(   0.193|   0.000) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-front'
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Mic Jack' succeeded (not found)
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.193|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-front', none of required-any elements preset.
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-rear'
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Rear Mic Jack' succeeded (not found)
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.194|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-rear', none of required-any elements preset.
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-internal'
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Mic Jack' succeeded (found!)
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Dock Mic Jack' succeeded (not found)
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Mic Jack' succeeded (not found)
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Rear Mic Jack' succeeded (not found)
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Internal Mic Phantom Jack' succeeded (not found)
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=1, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Int Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Int Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.195|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-dock'
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Dock Mic Jack' succeeded (not found)
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.196|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-dock', none of required-any elements preset.
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input'
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Int Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Int Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' failed.
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone'
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Mic Jack' succeeded (found!)
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.197|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Select' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost (+20dB)' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-linein'
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Jack' succeeded (not found)
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.198|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-linein', none of required-any elements preset.
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input'
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' failed.
(   0.199|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-video'
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' failed.
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-video'
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' failed.
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-radio'
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' failed.
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input'
(   0.200|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' failed.
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone'
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Auto-Mute Mode' succeeded (volume=0, switch=0, enumeration=1).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.201|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone', none of required-any elements preset.
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-headset'
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headset Mic Jack' succeeded (not found)
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headset Mic Phantom Jack' succeeded (not found)
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (found!)
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headset Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Headset Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.202|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-headset', none of required-any elements preset.
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Path Set 0x1c93e60, direction=2
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-input-microphone-internal (Internal Microphone), direction=2, priority=89, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=4, min_dB=-74, max_dB=46
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Element Internal Mic Boost, direction=2, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Mic, alsa_name='Mic Jack', detection possible
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Dock Mic, alsa_name='Dock Mic Jack', detection unavailable
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Front Mic, alsa_name='Front Mic Jack', detection unavailable
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Rear Mic, alsa_name='Rear Mic Jack', detection unavailable
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Internal Mic Phantom, alsa_name='Internal Mic Phantom Jack', detection unavailable
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-input-microphone (Microphone), direction=2, priority=87, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=80, min_dB=-74, max_dB=6
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Element Internal Mic Boost, direction=2, switch=0, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Mic, alsa_name='Mic Jack', detection possible
(   0.203|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo+input:iec958-stereo
(   0.204|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
(   0.204|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.205|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D1c' failed (-2)
(   0.205|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:1: No such file or directory
(   0.205|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-40
(   0.205|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
(   0.205|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.206|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround40:1
(   0.206|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.206|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.207|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround40:1
(   0.208|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.208|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.208|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround40:1
(   0.209|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.209|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround40:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.210|   0.001) D: [pulseaudio] alsa-util.c: Managed to open plug:surround40:1
(   0.211|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.211|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround40:1: Invalid argument
(   0.211|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-mono
(   0.211|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
(   0.211|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.212|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround40:1
(   0.212|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.212|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.213|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround40:1
(   0.213|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.213|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.214|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround40:1
(   0.215|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.215|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround40:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.216|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround40:1
(   0.216|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.216|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround40:1: Invalid argument
(   0.217|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-stereo
(   0.217|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
(   0.217|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.218|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround40:1
(   0.218|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.218|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.219|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround40:1
(   0.219|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.219|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.220|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround40:1
(   0.220|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.220|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround40:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.221|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround40:1
(   0.222|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.222|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround40:1: Invalid argument
(   0.222|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-40+input:iec958-stereo
(   0.222|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
(   0.222|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.223|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround40:1
(   0.224|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.224|   0.000) D: [pulseaudio] alsa-util.c: Trying surround40:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.224|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround40:1
(   0.225|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.225|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.226|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround40:1
(   0.226|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.226|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround40:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.227|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround40:1
(   0.228|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.228|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround40:1: Invalid argument
(   0.228|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-41
(   0.228|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
(   0.228|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.229|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround41:1
(   0.229|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.229|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.230|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround41:1
(   0.230|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.230|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.231|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround41:1
(   0.231|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.231|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.231|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround41:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.232|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround41:1
(   0.232|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.232|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.232|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround41:1: Invalid argument
(   0.232|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-mono
(   0.232|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
(   0.233|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.233|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround41:1
(   0.234|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.234|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.235|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround41:1
(   0.235|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.235|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.236|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround41:1
(   0.236|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.236|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.236|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround41:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.237|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround41:1
(   0.237|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.237|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.237|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround41:1: Invalid argument
(   0.237|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-stereo
(   0.237|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
(   0.237|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.238|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround41:1
(   0.238|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.238|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.239|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround41:1
(   0.239|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.239|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.240|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround41:1
(   0.240|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.240|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.240|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround41:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.241|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround41:1
(   0.241|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.241|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.241|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround41:1: Invalid argument
(   0.242|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-41+input:iec958-stereo
(   0.242|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
(   0.242|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.242|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround41:1
(   0.243|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.243|   0.000) D: [pulseaudio] alsa-util.c: Trying surround41:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.244|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround41:1
(   0.244|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.244|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.245|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround41:1
(   0.245|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.245|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.245|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround41:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.246|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround41:1
(   0.246|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.246|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.246|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround41:1: Invalid argument
(   0.246|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50
(   0.246|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
(   0.246|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.247|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround50:1
(   0.247|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.247|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.248|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround50:1
(   0.248|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.248|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.249|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround50:1
(   0.249|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.249|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.249|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround50:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.250|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround50:1
(   0.250|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.250|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.250|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround50:1: Invalid argument
(   0.251|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-mono
(   0.251|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
(   0.251|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.251|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround50:1
(   0.252|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.252|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.252|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround50:1
(   0.253|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.253|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.253|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround50:1
(   0.254|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.254|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.254|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround50:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.255|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround50:1
(   0.255|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.255|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.255|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround50:1: Invalid argument
(   0.255|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-stereo
(   0.255|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
(   0.255|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.256|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround50:1
(   0.256|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.256|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.257|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround50:1
(   0.257|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.257|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.258|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround50:1
(   0.258|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.258|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.258|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround50:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.259|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround50:1
(   0.259|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.259|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.259|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround50:1: Invalid argument
(   0.259|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-stereo
(   0.259|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
(   0.260|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.260|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround50:1
(   0.260|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.261|   0.000) D: [pulseaudio] alsa-util.c: Trying surround50:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.261|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround50:1
(   0.261|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.262|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.262|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround50:1
(   0.263|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.263|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.263|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround50:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.264|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround50:1
(   0.264|   0.000) I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
(   0.264|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
(   0.264|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround50:1: Invalid argument
(   0.264|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51
(   0.264|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
(   0.264|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.265|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround51:1
(   0.265|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.265|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.266|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround51:1
(   0.266|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.266|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.267|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround51:1
(   0.268|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.268|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround51:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.269|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround51:1
(   0.269|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.269|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround51:1: Invalid argument
(   0.269|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-mono
(   0.270|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
(   0.270|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.270|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround51:1
(   0.271|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.271|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.272|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround51:1
(   0.272|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.272|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.273|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround51:1
(   0.273|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.274|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround51:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.275|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround51:1
(   0.275|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.275|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround51:1: Invalid argument
(   0.275|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-stereo
(   0.275|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
(   0.275|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.276|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround51:1
(   0.277|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.277|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.277|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround51:1
(   0.278|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.278|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.279|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround51:1
(   0.279|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.279|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround51:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.280|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround51:1
(   0.281|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.281|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround51:1: Invalid argument
(   0.281|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-stereo
(   0.281|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
(   0.281|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.282|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround51:1
(   0.282|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.282|   0.000) D: [pulseaudio] alsa-util.c: Trying surround51:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.283|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround51:1
(   0.283|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.283|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.284|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround51:1
(   0.285|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.285|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround51:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.286|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround51:1
(   0.286|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
(   0.287|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround51:1: Invalid argument
(   0.287|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71
(   0.287|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
(   0.287|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.288|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround71:1
(   0.288|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.288|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.289|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround71:1
(   0.289|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.289|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.290|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround71:1
(   0.290|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.291|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround71:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.291|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround71:1
(   0.292|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.292|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround71:1: Invalid argument
```

---

### Post by Ace..... on 2015-08-08
Part 3. (continued from previous post):

```


(   0.292|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-mono
(   0.292|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
(   0.292|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.293|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround71:1
(   0.293|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.294|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.294|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround71:1
(   0.295|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.295|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.296|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround71:1
(   0.296|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.296|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround71:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.297|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround71:1
(   0.298|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.298|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround71:1: Invalid argument
(   0.298|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-stereo
(   0.298|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
(   0.298|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.299|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround71:1
(   0.299|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.299|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.300|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround71:1
(   0.300|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.300|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.301|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround71:1
(   0.302|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.302|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround71:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.303|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround71:1
(   0.303|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.303|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround71:1: Invalid argument
(   0.304|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-stereo
(   0.304|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
(   0.304|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.304|   0.000) D: [pulseaudio] alsa-util.c: Managed to open surround71:1
(   0.305|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.305|   0.000) D: [pulseaudio] alsa-util.c: Trying surround71:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.306|   0.001) D: [pulseaudio] alsa-util.c: Managed to open surround71:1
(   0.306|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.306|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.307|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround71:1
(   0.308|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.308|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:surround71:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.309|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:surround71:1
(   0.309|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.309|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround71:1: Invalid argument
(   0.310|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo
(   0.310|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
(   0.310|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.310|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D1p' failed (-2)
(   0.311|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:1: No such file or directory
(   0.311|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-mono
(   0.311|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
(   0.311|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.311|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D1p' failed (-2)
(   0.312|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:1: No such file or directory
(   0.312|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-stereo
(   0.312|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
(   0.312|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.312|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D1p' failed (-2)
(   0.313|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:1: No such file or directory
(   0.313|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-stereo
(   0.313|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
(   0.313|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.313|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D1p' failed (-2)
(   0.314|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:1: No such file or directory
(   0.314|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
(   0.314|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
(   0.314|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.314|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:1
(   0.314|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:1: No such file or directory
(   0.314|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-mono
(   0.314|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
(   0.314|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.314|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:1
(   0.314|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:1: No such file or directory
(   0.314|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-stereo
(   0.314|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
(   0.314|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.314|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:1
(   0.314|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:1: No such file or directory
(   0.314|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-stereo
(   0.314|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
(   0.314|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.314|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:1
(   0.315|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:1: No such file or directory
(   0.315|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
(   0.315|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
(   0.315|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.315|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:1
(   0.315|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:1: No such file or directory
(   0.315|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-mono
(   0.315|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
(   0.315|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.315|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:1
(   0.315|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:1: No such file or directory
(   0.315|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-stereo
(   0.315|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
(   0.315|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.315|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:1
(   0.315|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:1: No such file or directory
(   0.315|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-stereo
(   0.315|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
(   0.315|   0.000) D: [pulseaudio] alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.315|   0.000) I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:1
(   0.315|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device a52:1: No such file or directory
(   0.315|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo
(   0.315|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
(   0.316|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.316|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D3p' failed (-2)
(   0.316|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:1: No such file or directory
(   0.317|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-mono
(   0.317|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
(   0.317|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.318|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D3p' failed (-2)
(   0.318|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:1: No such file or directory
(   0.318|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-stereo
(   0.318|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
(   0.318|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.319|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D3p' failed (-2)
(   0.319|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:1: No such file or directory
(   0.319|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-stereo
(   0.319|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
(   0.319|   0.000) D: [pulseaudio] alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.320|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D3p' failed (-2)
(   0.320|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:1: No such file or directory
(   0.320|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile input:analog-mono
(   0.320|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
(   0.320|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.320|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:1
(   0.321|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.321|   0.000) D: [pulseaudio] alsa-util.c: Trying hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.321|   0.000) D: [pulseaudio] alsa-util.c: Managed to open hw:1
(   0.321|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.321|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.322|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
(   0.322|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.322|   0.000) D: [pulseaudio] alsa-util.c: Trying plug:hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.323|   0.000) D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
(   0.323|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.323|   0.000) I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:1: Invalid argument
(   0.323|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile input:analog-stereo
(   0.323|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.323|   0.000) D: [pulseaudio] alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.324|   0.000) D: [pulseaudio] alsa-util.c: Managed to open front:1
(   0.324|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.324|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
(   0.324|   0.000) D: [pulseaudio] alsa-mixer.c: Profile input:analog-stereo supported.
(   0.325|   0.000) D: [pulseaudio] alsa-mixer.c: Looking at profile input:iec958-stereo
(   0.325|   0.000) D: [pulseaudio] alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
(   0.325|   0.000) D: [pulseaudio] alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.326|   0.000) I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D1c' failed (-2)
(   0.326|   0.000) I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:1: No such file or directory
(   0.326|   0.000) D: [pulseaudio] alsa-mixer.c: Profile set 0x1c3e6f0, auto_profiles=yes, probed=yes, n_mappings=1, n_profiles=3, n_decibel_fixes=0
(   0.327|   0.000) D: [pulseaudio] alsa-mixer.c: Mapping analog-stereo (Analog Stereo), priority=60, channel_map=front-left,front-right, supported=yes, direction=0
(   0.327|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo (Analog Stereo Output), priority=6000, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.327|   0.000) D: [pulseaudio] alsa-mixer.c: Output analog-stereo
(   0.327|   0.000) D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo (Analog Stereo Duplex), priority=6060, supported=yes n_input_mappings=1, n_output_mappings=1
(   0.327|   0.000) D: [pulseaudio] alsa-mixer.c: Input analog-stereo
(   0.327|   0.000) D: [pulseaudio] alsa-mixer.c: Output analog-stereo
(   0.327|   0.000) D: [pulseaudio] alsa-mixer.c: Profile input:analog-stereo (Analog Stereo Input), priority=60, supported=yes n_input_mappings=1, n_output_mappings=0
(   0.327|   0.000) D: [pulseaudio] alsa-mixer.c: Input analog-stereo
(   0.328|   0.000) D: [pulseaudio] module-card-restore.c: Database contains invalid data for key: alsa_card.pci-0000_00_14.2 (probably pre-v1.0 data)
(   0.328|   0.000) D: [pulseaudio] module-card-restore.c: Attempting to load legacy (pre-v1.0) data for key: alsa_card.pci-0000_00_14.2
(   0.328|   0.000) D: [pulseaudio] module-card-restore.c: Size does not match.
(   0.328|   0.000) D: [pulseaudio] module-card-restore.c: Unable to load legacy (pre-v1.0) data for key: alsa_card.pci-0000_00_14.2. Ignoring.
(   0.328|   0.000) I: [pulseaudio] card.c: Created 1 "alsa_card.pci-0000_00_14.2"
(   0.330|   0.002) D: [pulseaudio] reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio1'
(   0.331|   0.000) D: [pulseaudio] alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.332|   0.001) D: [pulseaudio] alsa-util.c: Managed to open front:1
(   0.332|   0.000) I: [pulseaudio] alsa-util.c: Trying to disable ALSA period wakeups, using timers only
(   0.332|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.332|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
(   0.332|   0.000) I: [pulseaudio] alsa-util.c: ALSA period wakeups disabled
(   0.332|   0.000) I: [pulseaudio] alsa-sink.c: Successfully opened device front:1.
(   0.332|   0.000) I: [pulseaudio] alsa-sink.c: Selected mapping 'Analog Stereo' (analog-stereo).
(   0.332|   0.000) I: [pulseaudio] alsa-sink.c: Successfully enabled mmap() mode.
(   0.332|   0.000) I: [pulseaudio] alsa-sink.c: Successfully enabled timer-based scheduling mode.
(   0.333|   0.000) I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:1
(   0.333|   0.000) I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:1: No such file or directory
(   0.333|   0.000) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.334|   0.000) D: [pulseaudio] alsa-mixer.c: Added 2 ports
(   0.334|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.334|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:alsa_output.pci-0000_00_14.2.analog-stereo (probably pre-v1.0 data)
(   0.334|   0.000) D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink:alsa_output.pci-0000_00_14.2.analog-stereo
(   0.334|   0.000) D: [pulseaudio] module-device-restore.c: Size does not match.
(   0.334|   0.000) D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: sink:alsa_output.pci-0000_00_14.2.analog-stereo. Ignoring.
(   0.334|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:alsa_output.pci-0000_00_14.2.analog-stereo:null
(   0.335|   0.000) I: [pulseaudio] sink.c: Created sink 1 "alsa_output.pci-0000_00_14.2.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.resolution_bits = "16"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.api = "alsa"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.class = "sound"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.class = "generic"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.subclass = "generic-mix"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.name = "CONEXANT Analog"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.id = "CONEXANT Analog"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.subdevice = "0"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.subdevice_name = "subdevice #0"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.device = "0"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.card = "1"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.card_name = "HDA ATI SB"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.long_card_name = "HDA ATI SB at 0xd0440000 irq 16"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.driver_name = "snd_hda_intel"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.bus_path = "pci-0000:00:14.2"
(   0.335|   0.000) I: [pulseaudio] sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card1"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.bus = "pci"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.vendor.id = "1002"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.product.name = "SBx00 Azalia (Intel HDA)"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.form_factor = "internal"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.string = "front:1"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.buffering.buffer_size = "65536"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.buffering.fragment_size = "32768"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.access_mode = "mmap+timer"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.profile.name = "analog-stereo"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.profile.description = "Analog Stereo"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.description = "Built-in Audio Analog Stereo"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.mixer_name = "Conexant CX20584"
(   0.335|   0.000) I: [pulseaudio] sink.c:     alsa.components = "HDA:14f15068,10250520,00100302"
(   0.335|   0.000) I: [pulseaudio] sink.c:     module-udev-detect.discovered = "1"
(   0.335|   0.000) I: [pulseaudio] sink.c:     device.icon_name = "audio-card-pci"
(   0.335|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.335|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_output.pci-0000_00_14.2.analog-stereo.monitor (probably pre-v1.0 data)
(   0.335|   0.000) D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: source:alsa_output.pci-0000_00_14.2.analog-stereo.monitor
(   0.336|   0.000) D: [pulseaudio] module-device-restore.c: Size does not match.
(   0.336|   0.000) D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: source:alsa_output.pci-0000_00_14.2.analog-stereo.monitor. Ignoring.
(   0.336|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_output.pci-0000_00_14.2.analog-stereo.monitor:null
(   0.336|   0.000) I: [pulseaudio] source.c: Created source 1 "alsa_output.pci-0000_00_14.2.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.336|   0.000) I: [pulseaudio] source.c:     device.description = "Monitor of Built-in Audio Analog Stereo"
(   0.336|   0.000) I: [pulseaudio] source.c:     device.class = "monitor"
(   0.336|   0.000) I: [pulseaudio] source.c:     alsa.card = "1"
(   0.336|   0.000) I: [pulseaudio] source.c:     alsa.card_name = "HDA ATI SB"
(   0.336|   0.000) I: [pulseaudio] source.c:     alsa.long_card_name = "HDA ATI SB at 0xd0440000 irq 16"
(   0.336|   0.000) I: [pulseaudio] source.c:     alsa.driver_name = "snd_hda_intel"
(   0.336|   0.000) I: [pulseaudio] source.c:     device.bus_path = "pci-0000:00:14.2"
(   0.336|   0.000) I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card1"
(   0.336|   0.000) I: [pulseaudio] source.c:     device.bus = "pci"
(   0.336|   0.000) I: [pulseaudio] source.c:     device.vendor.id = "1002"
(   0.336|   0.000) I: [pulseaudio] source.c:     device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
(   0.336|   0.000) I: [pulseaudio] source.c:     device.product.name = "SBx00 Azalia (Intel HDA)"
(   0.336|   0.000) I: [pulseaudio] source.c:     device.form_factor = "internal"
(   0.336|   0.000) I: [pulseaudio] source.c:     device.string = "1"
(   0.336|   0.000) I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
(   0.336|   0.000) I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
(   0.336|   0.000) I: [pulseaudio] alsa-sink.c: Using 2.0 fragments of size 32768 bytes (185.76ms), buffer size is 65536 bytes (371.52ms)
(   0.336|   0.000) I: [pulseaudio] alsa-sink.c: Time scheduling watermark is 20.00ms
(   0.336|   0.000) D: [pulseaudio] alsa-sink.c: hwbuf_unused=0
(   0.336|   0.000) D: [pulseaudio] alsa-sink.c: setting avail_min=15502
(   0.336|   0.000) D: [pulseaudio] alsa-mixer.c: Activating path analog-output-speaker
(   0.337|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-output-speaker (Speakers), direction=1, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=74, min_dB=-199, max_dB=0
(   0.337|   0.000) D: [pulseaudio] alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
(   0.337|   0.000) D: [pulseaudio] alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.337|   0.000) D: [pulseaudio] alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.337|   0.000) D: [pulseaudio] alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.337|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection possible
(   0.337|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Front Headphone, alsa_name='Front Headphone Jack', detection unavailable
(   0.337|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Speaker Phantom, alsa_name='Speaker Phantom Jack', detection unavailable
(   0.337|   0.000) I: [pulseaudio] alsa-sink.c: Successfully enabled synchronous volume.
(   0.337|   0.000) I: [pulseaudio] alsa-sink.c: Hardware volume ranges from -199.00 dB to 0.00 dB.
(   0.337|   0.000) I: [pulseaudio] alsa-sink.c: Fixing base volume to 0.00 dB
(   0.337|   0.000) I: [pulseaudio] alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
(   0.337|   0.000) I: [pulseaudio] alsa-sink.c: Using hardware mute control.
(   0.337|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_dump():
(   0.337|   0.000) D: [pulseaudio] alsa-util.c: Soft volume PCM
(   0.337|   0.000) D: [pulseaudio] alsa-util.c: Control: PCM Playback Volume
(   0.337|   0.000) D: [pulseaudio] alsa-util.c: min_dB: -51
(   0.337|   0.000) D: [pulseaudio] alsa-util.c: max_dB: 0
(   0.337|   0.000) D: [pulseaudio] alsa-util.c: resolution: 256
(   0.337|   0.000) D: [pulseaudio] alsa-util.c: Its setup is:
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   stream       : PLAYBACK
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   format       : S16_LE
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   subformat    : STD
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   channels     : 2
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   rate         : 44100
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   msbits       : 16
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   period_size  : 8192
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   period_time  : 185759
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   period_step  : 1
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   avail_min    : 15502
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   period_event : 0
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   start_threshold  : -1
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   stop_threshold   : 4611686018427387904
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   silence_threshold: 0
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   silence_size : 0
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   boundary     : 4611686018427387904
(   0.337|   0.000) D: [pulseaudio] alsa-util.c: Slave: Hardware PCM card 1 'HDA ATI SB' device 0 subdevice 0
(   0.337|   0.000) D: [pulseaudio] alsa-util.c: Its setup is:
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   stream       : PLAYBACK
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   format       : S16_LE
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   subformat    : STD
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   channels     : 2
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   rate         : 44100
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   msbits       : 16
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   period_size  : 8192
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   period_time  : 185759
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   period_step  : 1
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   avail_min    : 15502
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   period_event : 0
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   start_threshold  : -1
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   stop_threshold   : 4611686018427387904
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   silence_threshold: 0
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   silence_size : 0
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   boundary     : 4611686018427387904
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   appl_ptr     : 0
(   0.337|   0.000) D: [pulseaudio] alsa-util.c:   hw_ptr       : 0
(   0.339|   0.001) D: [pulseaudio] alsa-sink.c: Read hardware volume: 0:  89% 1:  89%
(   0.339|   0.000) D: [pulseaudio] alsa-sink.c:                in dB: 0: -3.00 dB 1: -3.00 dB
(   0.339|   0.000) D: [alsa-sink] alsa-sink.c: Thread starting up
(   0.363|   0.024) D: [alsa-sink] core-util.c: RealtimeKit worked.
(   0.364|   0.000) I: [alsa-sink] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
(   0.364|   0.000) I: [alsa-sink] alsa-sink.c: Starting playback.
(   0.364|   0.000) D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(   0.364|   0.000) D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
(   0.364|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:alsa_output.pci-0000_00_14.2.analog-stereo:null
(   0.365|   0.000) D: [pulseaudio] alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.366|   0.001) D: [pulseaudio] alsa-util.c: Managed to open front:1
(   0.366|   0.000) I: [pulseaudio] alsa-util.c: Trying to disable ALSA period wakeups, using timers only
(   0.366|   0.000) D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
(   0.367|   0.000) D: [pulseaudio] alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
(   0.367|   0.000) I: [pulseaudio] alsa-util.c: ALSA period wakeups disabled
(   0.367|   0.000) I: [pulseaudio] alsa-source.c: Successfully opened device front:1.
(   0.367|   0.000) I: [pulseaudio] alsa-source.c: Selected mapping 'Analog Stereo' (analog-stereo).
(   0.367|   0.000) I: [pulseaudio] alsa-source.c: Successfully enabled mmap() mode.
(   0.367|   0.000) I: [pulseaudio] alsa-source.c: Successfully enabled timer-based scheduling mode.
(   0.367|   0.000) I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:1
(   0.367|   0.000) I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:1: No such file or directory
(   0.368|   0.000) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.369|   0.001) D: [pulseaudio] alsa-mixer.c: Added 2 ports
(   0.369|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.369|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_input.pci-0000_00_14.2.analog-stereo (probably pre-v1.0 data)
(   0.369|   0.000) D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: source:alsa_input.pci-0000_00_14.2.analog-stereo
(   0.369|   0.000) D: [pulseaudio] module-device-restore.c: Size does not match.
(   0.369|   0.000) D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: source:alsa_input.pci-0000_00_14.2.analog-stereo. Ignoring.
(   0.369|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_input.pci-0000_00_14.2.analog-stereo:null
(   0.369|   0.000) I: [pulseaudio] source.c: Created source 2 "alsa_input.pci-0000_00_14.2.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.resolution_bits = "16"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.api = "alsa"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.class = "sound"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.class = "generic"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.subclass = "generic-mix"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.name = "CONEXANT Analog"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.id = "CONEXANT Analog"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.subdevice = "0"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.subdevice_name = "subdevice #0"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.device = "0"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.card = "1"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.card_name = "HDA ATI SB"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.long_card_name = "HDA ATI SB at 0xd0440000 irq 16"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.driver_name = "snd_hda_intel"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.bus_path = "pci-0000:00:14.2"
(   0.369|   0.000) I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card1"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.bus = "pci"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.vendor.id = "1002"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.product.name = "SBx00 Azalia (Intel HDA)"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.form_factor = "internal"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.string = "front:1"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.buffering.buffer_size = "65536"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.buffering.fragment_size = "32768"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.access_mode = "mmap+timer"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.profile.name = "analog-stereo"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.profile.description = "Analog Stereo"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.description = "Built-in Audio Analog Stereo"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.mixer_name = "Conexant CX20584"
(   0.369|   0.000) I: [pulseaudio] source.c:     alsa.components = "HDA:14f15068,10250520,00100302"
(   0.369|   0.000) I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
(   0.369|   0.000) I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
(   0.371|   0.001) I: [pulseaudio] alsa-source.c: Using 2.0 fragments of size 32768 bytes (185.76ms), buffer size is 65536 bytes (371.52ms)
(   0.371|   0.000) I: [pulseaudio] alsa-source.c: Time scheduling watermark is 20.00ms
(   0.371|   0.000) D: [pulseaudio] alsa-source.c: hwbuf_unused=0
(   0.371|   0.000) D: [pulseaudio] alsa-source.c: setting avail_min=15502
(   0.371|   0.000) D: [pulseaudio] alsa-mixer.c: Activating path analog-input-microphone-internal
(   0.371|   0.000) D: [pulseaudio] alsa-mixer.c: Path analog-input-microphone-internal (Internal Microphone), direction=2, priority=89, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=4, min_dB=-74, max_dB=46
(   0.371|   0.000) D: [pulseaudio] alsa-mixer.c: Element Internal Mic Boost, direction=2, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.371|   0.000) D: [pulseaudio] alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.371|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Mic, alsa_name='Mic Jack', detection possible
(   0.371|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Dock Mic, alsa_name='Dock Mic Jack', detection unavailable
(   0.371|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Front Mic, alsa_name='Front Mic Jack', detection unavailable
(   0.371|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Rear Mic, alsa_name='Rear Mic Jack', detection unavailable
(   0.371|   0.000) D: [pulseaudio] alsa-mixer.c: Jack Internal Mic Phantom, alsa_name='Internal Mic Phantom Jack', detection unavailable
(   0.371|   0.000) I: [pulseaudio] alsa-source.c: Successfully enabled synchronous volume.
(   0.371|   0.000) I: [pulseaudio] alsa-source.c: Hardware volume ranges from -74.00 dB to 46.00 dB.
(   0.371|   0.000) I: [pulseaudio] alsa-source.c: Fixing base volume to -46.00 dB
(   0.371|   0.000) I: [pulseaudio] alsa-source.c: Using hardware volume control. Hardware dB scale supported.
(   0.371|   0.000) I: [pulseaudio] alsa-source.c: Using hardware mute control.
(   0.372|   0.000) D: [pulseaudio] alsa-util.c: snd_pcm_dump():
(   0.372|   0.000) D: [pulseaudio] alsa-util.c: Hardware PCM card 1 'HDA ATI SB' device 0 subdevice 0
(   0.372|   0.000) D: [pulseaudio] alsa-util.c: Its setup is:
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   stream       : CAPTURE
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   format       : S16_LE
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   subformat    : STD
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   channels     : 2
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   rate         : 44100
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   msbits       : 16
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   period_size  : 8192
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   period_time  : 185759
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   period_step  : 1
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   avail_min    : 15502
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   period_event : 0
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   start_threshold  : -1
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   stop_threshold   : 4611686018427387904
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   silence_threshold: 0
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   silence_size : 0
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   boundary     : 4611686018427387904
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   appl_ptr     : 0
(   0.372|   0.000) D: [pulseaudio] alsa-util.c:   hw_ptr       : 0
(   0.373|   0.001) D: [pulseaudio] alsa-source.c: Read hardware volume: 0: 100% 1: 100%
(   0.373|   0.000) D: [pulseaudio] alsa-source.c:                in dB: 0: -0.00 dB 1: -0.00 dB
(   0.373|   0.000) D: [alsa-source] alsa-source.c: Thread starting up
(   0.399|   0.026) D: [alsa-source] core-util.c: RealtimeKit worked.
(   0.399|   0.000) I: [alsa-source] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
(   0.399|   0.000) I: [alsa-source] alsa-source.c: Starting capture.
(   0.400|   0.001) I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.400|   0.000) D: [pulseaudio] module-alsa-card.c: Jack 'Headphone Jack' is now unplugged
(   0.401|   0.000) D: [pulseaudio] module-alsa-card.c: Jack 'Headphone Jack' is now unplugged
(   0.401|   0.000) D: [pulseaudio] device-port.c: Setting port analog-output-headphones to status no
(   0.401|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.401|   0.000) D: [pulseaudio] module-alsa-card.c: Jack 'Mic Jack' is now unplugged
(   0.401|   0.000) D: [pulseaudio] module-alsa-card.c: Jack 'Mic Jack' is now unplugged
(   0.401|   0.000) D: [pulseaudio] device-port.c: Setting port analog-input-microphone to status no
(   0.401|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.401|   0.000) I: [pulseaudio] module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id="1" name="pci-0000_00_14.2" card_name="alsa_card.pci-0000_00_14.2" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"").
(   0.401|   0.000) I: [pulseaudio] module-udev-detect.c: Card /devices/pci0000:00/0000:00:14.2/sound/card1 (alsa_card.pci-0000_00_14.2) module loaded.
(   0.401|   0.000) I: [pulseaudio] module-udev-detect.c: Found 2 cards.
(   0.401|   0.000) I: [pulseaudio] module.c: Loaded "module-udev-detect" (index: #6; argument: "").
(   0.402|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-jackdbus-detect.so': failure
(   0.402|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-bluetooth-discover.so': success
(   0.410|   0.008) D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus system bus 3290c733a70e07d4604def230000001f as :1.66
(   0.419|   0.008) D: [pulseaudio] bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
(   0.420|   0.001) I: [pulseaudio] module.c: Loaded "module-bluetooth-discover" (index: #7; argument: "").
(   0.420|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-esound-protocol-unix.so': failure
(   0.421|   0.001) D: [pulseaudio] authkey.c: Got 0 bytes from cookie file '/home/mark/.pulse-cookie', expected 256
(   0.422|   0.000) I: [pulseaudio] module.c: Loaded "module-native-protocol-unix" (index: #8; argument: "").
(   0.422|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-gconf.so': success
(   0.456|   0.033) I: [pulseaudio] module.c: Loaded "module-gconf" (index: #9; argument: "").
(   0.457|   0.001) I: [pulseaudio] module.c: Loaded "module-default-device-restore" (index: #10; argument: "").
(   0.458|   0.001) I: [pulseaudio] module.c: Loaded "module-rescue-streams" (index: #11; argument: "").
(   0.459|   0.000) I: [pulseaudio] module.c: Loaded "module-always-sink" (index: #12; argument: "").
(   0.460|   0.000) I: [pulseaudio] module.c: Loaded "module-intended-roles" (index: #13; argument: "").
(   0.461|   0.001) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_01.1.hdmi-stereo becomes idle, timeout in 5 seconds.
(   0.461|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_14.2.analog-stereo becomes idle, timeout in 5 seconds.
(   0.461|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_00_14.2.analog-stereo becomes idle, timeout in 5 seconds.
(   0.462|   0.000) I: [pulseaudio] module.c: Loaded "module-suspend-on-idle" (index: #14; argument: "").
(   0.462|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-console-kit.so': success
(   0.469|   0.007) I: [pulseaudio] client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
(   0.469|   0.000) D: [pulseaudio] module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session2
(   0.469|   0.000) I: [pulseaudio] module.c: Loaded "module-console-kit" (index: #15; argument: "").
(   0.470|   0.001) I: [pulseaudio] module.c: Loaded "module-position-event-sounds" (index: #16; argument: "").
(   0.471|   0.000) I: [pulseaudio] module.c: Loaded "module-filter-heuristics" (index: #17; argument: "").
(   0.472|   0.000) I: [pulseaudio] module.c: Loaded "module-filter-apply" (index: #18; argument: "").
(   0.473|   0.001) D: [pulseaudio] module-switch-on-port-available.c: finding port hdmi-output-0
(   0.474|   0.000) D: [pulseaudio] module-switch-on-port-available.c: finding port analog-output-headphones
(   0.474|   0.000) D: [pulseaudio] module-switch-on-port-available.c: finding port analog-input-microphone
(   0.474|   0.000) I: [pulseaudio] module.c: Loaded "module-switch-on-port-available" (index: #19; argument: "").
(   0.475|   0.001) D: [pulseaudio] main.c: Got org.PulseAudio1!
(   0.480|   0.005) D: [pulseaudio] main.c: Got org.pulseaudio.Server!
(   0.481|   0.000) I: [pulseaudio] main.c: Daemon startup complete.
(   0.481|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:alsa_output.pci-0000_00_01.1.hdmi-stereo (probably pre-v1.0 data)
(   0.481|   0.000) D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink:alsa_output.pci-0000_00_01.1.hdmi-stereo
(   0.481|   0.000) D: [pulseaudio] module-device-restore.c: Size does not match.
(   0.481|   0.000) D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: sink:alsa_output.pci-0000_00_01.1.hdmi-stereo. Ignoring.
(   0.481|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:alsa_output.pci-0000_00_01.1.hdmi-stereo:null
(   0.481|   0.000) I: [pulseaudio] module-device-restore.c: Storing port for device sink:alsa_output.pci-0000_00_01.1.hdmi-stereo.
(   0.482|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:alsa_output.pci-0000_00_01.1.hdmi-stereo:hdmi-output-0.
(   0.482|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_output.pci-0000_00_01.1.hdmi-stereo.monitor (probably pre-v1.0 data)
(   0.482|   0.000) D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: source:alsa_output.pci-0000_00_01.1.hdmi-stereo.monitor
(   0.482|   0.000) D: [pulseaudio] module-device-restore.c: Size does not match.
(   0.482|   0.000) D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: source:alsa_output.pci-0000_00_01.1.hdmi-stereo.monitor. Ignoring.
(   0.482|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_output.pci-0000_00_01.1.hdmi-stereo.monitor:null
(   0.482|   0.000) I: [pulseaudio] module-device-restore.c: Storing port for device source:alsa_output.pci-0000_00_01.1.hdmi-stereo.monitor.
(   0.482|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port source:alsa_output.pci-0000_00_01.1.hdmi-stereo.monitor:null.
(   0.482|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:alsa_output.pci-0000_00_14.2.analog-stereo (probably pre-v1.0 data)
(   0.482|   0.000) D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink:alsa_output.pci-0000_00_14.2.analog-stereo
(   0.482|   0.000) D: [pulseaudio] module-device-restore.c: Size does not match.
(   0.482|   0.000) D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: sink:alsa_output.pci-0000_00_14.2.analog-stereo. Ignoring.
(   0.482|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:alsa_output.pci-0000_00_14.2.analog-stereo:null
(   0.483|   0.000) I: [pulseaudio] module-device-restore.c: Storing port for device sink:alsa_output.pci-0000_00_14.2.analog-stereo.
(   0.483|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:alsa_output.pci-0000_00_14.2.analog-stereo:analog-output-speaker.
(   0.483|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_output.pci-0000_00_14.2.analog-stereo.monitor (probably pre-v1.0 data)
(   0.483|   0.000) D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: source:alsa_output.pci-0000_00_14.2.analog-stereo.monitor
(   0.483|   0.000) D: [pulseaudio] module-device-restore.c: Size does not match.
(   0.483|   0.000) D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: source:alsa_output.pci-0000_00_14.2.analog-stereo.monitor. Ignoring.
(   0.483|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_output.pci-0000_00_14.2.analog-stereo.monitor:null
(   0.483|   0.000) I: [pulseaudio] module-device-restore.c: Storing port for device source:alsa_output.pci-0000_00_14.2.analog-stereo.monitor.
(   0.483|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port source:alsa_output.pci-0000_00_14.2.analog-stereo.monitor:null.
(   0.483|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_input.pci-0000_00_14.2.analog-stereo (probably pre-v1.0 data)
(   0.483|   0.000) D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: source:alsa_input.pci-0000_00_14.2.analog-stereo
(   0.483|   0.000) D: [pulseaudio] module-device-restore.c: Size does not match.
(   0.483|   0.000) D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: source:alsa_input.pci-0000_00_14.2.analog-stereo. Ignoring.
(   0.483|   0.000) D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:alsa_input.pci-0000_00_14.2.analog-stereo:null
(   0.483|   0.000) I: [pulseaudio] module-device-restore.c: Storing port for device source:alsa_input.pci-0000_00_14.2.analog-stereo.
(   0.483|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port source:alsa_input.pci-0000_00_14.2.analog-stereo:analog-input-microphone-internal.
(   0.484|   0.001) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(   0.485|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
(   2.602|   2.116) I: [pulseaudio] client.c: Created 1 "Native client (UNIX socket client)"
(   2.602|   0.000) D: [pulseaudio] protocol-native.c: Protocol version: remote 26, local 26
(   2.602|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(   2.602|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(   2.602|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(   2.603|   0.000) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for indicator-sound-service
(   2.604|   0.001) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   5.464|   2.860) I: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_00_14.2.analog-stereo idle for too long, suspending ...
(   5.465|   0.000) D: [pulseaudio] source.c: Suspend cause of source alsa_input.pci-0000_00_14.2.analog-stereo is 0x0004, suspending
(   5.465|   0.000) I: [alsa-source] alsa-source.c: Device suspended...
(   5.465|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(   5.466|   0.000) I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_14.2.analog-stereo idle for too long, suspending ...
(   5.466|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_14.2.analog-stereo is 0x0004, suspending
(   5.469|   0.002) I: [alsa-sink] alsa-sink.c: Device suspended...
(   5.469|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(   5.469|   0.000) I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_01.1.hdmi-stereo idle for too long, suspending ...
(   5.469|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_01.1.hdmi-stereo is 0x0004, suspending
(   5.472|   0.002) I: [alsa-sink] alsa-sink.c: Device suspended...
(   5.472|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(   5.473|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(   5.473|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
(  10.487|   5.014) I: [pulseaudio] module-device-restore.c: Synced.
(  34.365|  23.877) I: [pulseaudio] main.c: Got signal SIGINT.
(  34.365|   0.000) I: [pulseaudio] main.c: Exiting.
(  34.365|   0.000) I: [pulseaudio] main.c: Daemon shutdown initiated.
(  34.365|   0.000) I: [pulseaudio] module.c: Unloading "module-device-restore" (index: #0).
(  34.365|   0.000) I: [pulseaudio] module.c: Unloaded "module-device-restore" (index: #0).
(  34.365|   0.000) I: [pulseaudio] module.c: Unloading "module-stream-restore" (index: #1).
(  34.366|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 removed from object /org/pulseaudio/stream_restore1
(  34.366|   0.000) I: [pulseaudio] module.c: Unloaded "module-stream-restore" (index: #1).
(  34.366|   0.000) I: [pulseaudio] module.c: Unloading "module-card-restore" (index: #2).
(  34.366|   0.000) I: [pulseaudio] module.c: Unloaded "module-card-restore" (index: #2).
(  34.366|   0.000) I: [pulseaudio] module.c: Unloading "module-augment-properties" (index: #3).
(  34.366|   0.000) I: [pulseaudio] module.c: Unloaded "module-augment-properties" (index: #3).
(  34.366|   0.000) I: [pulseaudio] module.c: Unloading "module-alsa-card" (index: #4).
(  34.366|   0.000) D: [pulseaudio] module-rescue-streams.c: No sink inputs to move away.
(  34.366|   0.000) D: [pulseaudio] module-rescue-streams.c: No source outputs to move away.
(  34.366|   0.000) D: [alsa-sink] alsa-sink.c: Thread shutting down
(  34.367|   0.000) I: [pulseaudio] sink.c: Freeing sink 0 "alsa_output.pci-0000_00_01.1.hdmi-stereo"
(  34.367|   0.000) I: [pulseaudio] source.c: Freeing source 0 "alsa_output.pci-0000_00_01.1.hdmi-stereo.monitor"
(  34.367|   0.000) I: [pulseaudio] card.c: Freed 0 "alsa_card.pci-0000_00_01.1"
(  34.367|   0.000) I: [pulseaudio] module.c: Unloaded "module-alsa-card" (index: #4).
(  34.367|   0.000) I: [pulseaudio] module.c: Unloading "module-alsa-card" (index: #5).
(  34.367|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  34.368|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  34.368|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  34.368|   0.000) D: [pulseaudio] module-always-sink.c: Autoloading null-sink as no other sinks detected.
(  34.369|   0.001) I: [pulseaudio] sink.c: Created sink 2 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(  34.369|   0.001) I: [pulseaudio] sink.c:     device.description = "Dummy Output"
(  34.369|   0.001) I: [pulseaudio] sink.c:     device.class = "abstract"
(  34.369|   0.001) I: [pulseaudio] sink.c:     device.icon_name = "audio-card"
(  34.369|   0.000) I: [pulseaudio] source.c: Created source 3 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(  34.369|   0.000) I: [pulseaudio] source.c:     device.description = "Monitor of Dummy Output"
(  34.369|   0.000) I: [pulseaudio] source.c:     device.class = "monitor"
(  34.369|   0.000) I: [pulseaudio] source.c:     device.icon_name = "audio-input-microphone"
(  34.370|   0.000) D: [null-sink] module-null-sink.c: Thread starting up
(  34.370|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink auto_null becomes idle, timeout in 5 seconds.
(  34.370|   0.000) I: [pulseaudio] module.c: Loaded "module-null-sink" (index: #20; argument: "sink_name=auto_null sink_properties='device.description="Dummy Output"'").
(  34.371|   0.000) D: [pulseaudio] module-rescue-streams.c: No sink inputs to move away.
(  34.371|   0.000) D: [pulseaudio] module-rescue-streams.c: No source outputs to move away.
(  34.372|   0.001) D: [alsa-sink] alsa-sink.c: Thread shutting down
(  34.373|   0.000) I: [pulseaudio] sink.c: Freeing sink 1 "alsa_output.pci-0000_00_14.2.analog-stereo"
(  34.373|   0.000) I: [pulseaudio] source.c: Freeing source 1 "alsa_output.pci-0000_00_14.2.analog-stereo.monitor"
(  34.373|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  34.373|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  34.373|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  34.373|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  34.373|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  34.373|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  34.374|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  34.374|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  34.374|   0.000) D: [pulseaudio] module-rescue-streams.c: No source outputs to move away.
(  34.374|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(  34.374|   0.000) D: [alsa-source] alsa-source.c: Thread shutting down
(  34.374|   0.000) I: [pulseaudio] source.c: Freeing source 2 "alsa_input.pci-0000_00_14.2.analog-stereo"
(  34.375|   0.000) I: [pulseaudio] card.c: Freed 1 "alsa_card.pci-0000_00_14.2"
(  34.376|   0.001) I: [pulseaudio] module.c: Unloaded "module-alsa-card" (index: #5).
(  34.377|   0.000) I: [pulseaudio] module.c: Unloading "module-udev-detect" (index: #6).
(  34.418|   0.040) I: [pulseaudio] module.c: Unloaded "module-udev-detect" (index: #6).
(  34.418|   0.000) I: [pulseaudio] module.c: Unloading "module-bluetooth-discover" (index: #7).
(  34.429|   0.011) I: [pulseaudio] module.c: Unloaded "module-bluetooth-discover" (index: #7).
(  34.430|   0.000) I: [pulseaudio] module.c: Unloading "module-native-protocol-unix" (index: #8).
(  34.430|   0.000) I: [pulseaudio] client.c: Freed 1 "Indicator Sound"
(  34.430|   0.000) I: [pulseaudio] module.c: Unloaded "module-native-protocol-unix" (index: #8).
(  34.430|   0.000) I: [pulseaudio] module.c: Unloading "module-gconf" (index: #9).
(  34.431|   0.000) I: [pulseaudio] module.c: Unloaded "module-gconf" (index: #9).
(  34.431|   0.000) I: [pulseaudio] module.c: Unloading "module-default-device-restore" (index: #10).
(  34.431|   0.000) I: [pulseaudio] module.c: Unloaded "module-default-device-restore" (index: #10).
(  34.431|   0.000) I: [pulseaudio] module.c: Unloading "module-rescue-streams" (index: #11).
(  34.431|   0.000) I: [pulseaudio] module.c: Unloaded "module-rescue-streams" (index: #11).
(  34.431|   0.000) I: [pulseaudio] module.c: Unloading "module-always-sink" (index: #12).
(  34.431|   0.000) I: [pulseaudio] module.c: Unloaded "module-always-sink" (index: #12).
(  34.431|   0.000) I: [pulseaudio] module.c: Unloading "module-intended-roles" (index: #13).
(  34.431|   0.000) I: [pulseaudio] module.c: Unloaded "module-intended-roles" (index: #13).
(  34.431|   0.000) I: [pulseaudio] module.c: Unloading "module-suspend-on-idle" (index: #14).
(  34.431|   0.000) I: [pulseaudio] module.c: Unloaded "module-suspend-on-idle" (index: #14).
(  34.431|   0.000) I: [pulseaudio] module.c: Unloading "module-console-kit" (index: #15).
(  34.431|   0.000) D: [pulseaudio] module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session2
(  34.431|   0.000) I: [pulseaudio] client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
(  34.438|   0.007) I: [pulseaudio] module.c: Unloaded "module-console-kit" (index: #15).
(  34.439|   0.000) I: [pulseaudio] module.c: Unloading "module-position-event-sounds" (index: #16).
(  34.439|   0.000) I: [pulseaudio] module.c: Unloaded "module-position-event-sounds" (index: #16).
(  34.439|   0.000) I: [pulseaudio] module.c: Unloading "module-filter-heuristics" (index: #17).
(  34.439|   0.000) I: [pulseaudio] module.c: Unloaded "module-filter-heuristics" (index: #17).
(  34.439|   0.000) I: [pulseaudio] module.c: Unloading "module-filter-apply" (index: #18).
(  34.439|   0.000) I: [pulseaudio] module.c: Unloaded "module-filter-apply" (index: #18).
(  34.439|   0.000) I: [pulseaudio] module.c: Unloading "module-switch-on-port-available" (index: #19).
(  34.439|   0.000) I: [pulseaudio] module.c: Unloaded "module-switch-on-port-available" (index: #19).
(  34.439|   0.000) I: [pulseaudio] module.c: Unloading "module-null-sink" (index: #20).
(  34.439|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
(  34.439|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
(  34.439|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
(  34.439|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
(  34.440|   0.000) D: [null-sink] module-null-sink.c: Thread shutting down
(  34.440|   0.000) I: [pulseaudio] sink.c: Freeing sink 2 "auto_null"
(  34.440|   0.000) I: [pulseaudio] source.c: Freeing source 3 "auto_null.monitor"
(  34.440|   0.000) I: [pulseaudio] module.c: Unloaded "module-null-sink" (index: #20).
(  34.440|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
(  34.440|   0.000) I: [pulseaudio] main.c: Daemon terminated.
```

---

### Post by Ace..... on 2015-08-08
I don't really know what I'm looking for, but, in the first 300 lines, there is a flood of errors of the type:

```
Error opening PCM device a52:0: No such file or directory
```

lines around 1200:

```
Failed to set hardware parameters on plug:surround71:1: Invalid argument
```

---

### Post by Ace..... on 2015-08-09
I've created an odt file from the log, in order to highlight the mention of the following words:

Error (70)
Failure (196)
Unable (18)

It allows 'at a glance' viewing of error messages:

[http://filebin.ca/2BXzR9XJUhBD/pulseverbosecopy.odt](http://filebin.ca/2BXzR9XJUhBD/pulseverbosecopy.odt)

Here is the unedited log file:

[http://filebin.ca/2BYEAFV6WLpi/pulseverbosecopy.log](http://filebin.ca/2BYEAFV6WLpi/pulseverbosecopy.log)

I like some of the comments in the file:

line 23: Fresh high-resolution timers available! Bon appetit!

:D

---

### Post by Yellow Pasque on 2015-08-09
If you want to share a lot of text, pastebin is probably best/easiest. Ubuntu has 'pastebinit' package to quickly pastebin a text file in the terminal, or you can got pastebin.com and manually copy/paste the text.

I'm not going to claim to be an expert at reading pulseaudio logs (I personally don't even use pulseaudio), but I believe the log doesn't show any major issues, despite all of the errors/failure messages.

If I had to try something next, it would be this: [http://unix.stackexchange.com/a/62687](http://unix.stackexchange.com/a/62687)
chromium and other browsers are notorious for using whatever sound device has index 0, regardless of what you have chosen in the sound settings.

---

### Post by Ace..... on 2015-08-09
I think that it goes deeper than the browser.
Standard Sound Settings panel has a test feature to play a sound through the speaker..... and it doesn't.

What's clear is that the two basic pulse audio tests carried out, show that the processes aren't running.

I note at:
[https://en.wikibooks.org/wiki/Configuring_Sound_on_Linux/Pulse_Audio/Testing](https://en.wikibooks.org/wiki/Configuring_Sound_on_Linux/Pulse_Audio/Testing)

Is stated:
> To test a PulseAudio installation use pacat which is equivalent to ALSA's aplay utility

[http://www.alsa-project.org/main/index.php/SoundcardTesting](http://www.alsa-project.org/main/index.php/SoundcardTesting)

They mention -w switch but this doesn't exist.
Either way..... couldn't get sound to play, nor the vu meter using -v
version is 1.0.25

So neither pulseaudio nor alsa seem to work.
Somebody somewhere will know what the problem is.

Re pastebin...... I tried it, but the text file was too large, so it was refused...... hence why I went to filebin.

Thanks for all the help.

---

### Post by Ace..... on 2015-08-09
Just searched on re-installing pulseaudio.

[http://askubuntu.com/questions/426648/how-to-reinstall-pulseaudio-ubuntu-12-04](http://askubuntu.com/questions/426648/how-to-reinstall-pulseaudio-ubuntu-12-04)

One response was:
> sudo apt-get purge pulseaudio
sudo apt-get clean && sudo apt-get autoremove
Reboot. Open a terminal again and type (ignore any errors with the rm command):


rm -r ~/.pulse ~/.asound* ~/.pulse-cookie ~/.config/pulse
sudo apt-get install pulseaudio
sudo alsa force-reload
pavucontrol
The last command should restart the PulseAudio server and launch a desktop application for its settings. Another thread notes that there might be conflicts with IPv6. If so, then edit /etc/avahi/avahi-daemon.conf and set use-ipv6 to no:


[server]
use-ipv4=yes
use-ipv6=no
Restart the avahi-daemon (e.g., reboot again).


This sounded sweet and easy to try, however, here's the first command result:
```
sudo apt-get purge pulseaudio
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  indicator-sound* indicator-sound-gtk2* libcanberra-pulse* pulseaudio*
  pulseaudio-module-bluetooth* pulseaudio-module-gconf* pulseaudio-module-x11*
  ubuntu-desktop*
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
After this operation, 4,491 kB disk space will be freed.

```

I aborted.
I noted it would remove ubuntu-desktop.
Yet no mention of reinstalling desktop was made.

What's the situation here?
It seems that to purge pulseaudio, I must remove ubuntu-desktop.

But I am also using xubuntu/xfce

What are the implications of this command?

---

### Post by Ace..... on 2015-08-11
Well, I've asked a question on Unix & Linux.
[http://unix.stackexchange.com/questions/222158/sound-at-login-but-no-sound-after-login-where-is-the-problem](http://unix.stackexchange.com/questions/222158/sound-at-login-but-no-sound-after-login-where-is-the-problem)

One of the high posters saw it and helped by editing in a third link (which was good of him, cos as a new member I could only add two).
However, he didn't upvote the question, and it remains at 0, which doesn't help get it seen.
(does anybody here have voting privileges?)

Still, it's been seen 18 times, but no responses.

I'm in conversation with an Alsa chap, through their mailing list, but no concrete suggestions.
The pulseaudio mailing list has yet to produce a response.

I have a sinking feeling that this is going to be a problem that remains unresolved, but let's see.

---

### Post by Ace..... on 2015-08-12
Got a response :)

Here are the suggested tests, and all results:

[http://pastebin.com/3nhedfx6](http://pastebin.com/3nhedfx6)

---

### Post by Ace..... on 2015-08-13
Advised to test with alsamixer.
Downloaded gnome-alsamixer.

Here's the results:
[http://pastebin.com/4UVxCJXM](http://pastebin.com/4UVxCJXM)

Got a response from the pulseaudio mailing list :)

Suggested to try (with sound playing):
```
PULSE_LOG=99 pactl info
```

Here's the log:

[http://pastebin.com/XxbSDvRR](http://pastebin.com/XxbSDvRR)

I note that the default channel is front-left front-right.


The laptop only has a single speaker.


Could the sound be being channeled to an external speaker output that doesn't exist?


But there again..... strange that at login, the sound is channeled correctly.


If the pactl log doesn't help....
Can we check the setup at login, and compare to the 'post desktop load' setup? 


At least we would then see a working setup.

---

### Post by Yellow Pasque on 2015-08-13
> The laptop only has a single speaker.
Maybe you need to do something like this:
[https://wiki.archlinux.org/index.php/PulseAudio/Examples#Remap_stereo_to_mono](https://wiki.archlinux.org/index.php/PulseAudio/Examples#Remap_stereo_to_mono)

---

### Post by Ace..... on 2015-08-13
> **Temüjin said:**
> Maybe you need to do something like this:
[https://wiki.archlinux.org/index.php/PulseAudio/Examples#Remap_stereo_to_mono](https://wiki.archlinux.org/index.php/PulseAudio/Examples#Remap_stereo_to_mono)

That's interesting.
Here's the instructions:

> **Remap stereo to mono**
[FONT=sans-serif]Remap a stereo input-sink to a mono sink by creating a virtual sink. 

It would be useful if you only have one speaker. Add to ```
/etc/pulse/default.pa:
```[/FONT]
```
load-module module-remap-sink master=alsa_output.pci-0000_00_1f.5.analog-stereo sink_name=mono channels=2 channel_map=mono,mono
# Optional: Select new remap as default
set-default-sink mono
```
[FONT=sans-serif]replace alsa_output.pci-0000_00_1f.5.analog-stereo in the sound card name shown from ```
pacmd list-sinks
```[/FONT]
[FONT=sans-serif]Switch player between virtual mono sink and real stereo sink.[/FONT]

I tried editing the default.pa file in Gedit, but couldn't save the new file, or even save as.
How does one add the above code?

However, I also noted that the script comments warn:
**This startup script is used only if PulseAudio is started per-user (i.e. not in system mode)**

Is 'system mode', at the login screen?

Here is the script and comments..... I note it must detect hardware....... is it screwing up?

```
#!/usr/bin/pulseaudio -nF#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.


# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)


.nofail


### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav


.fail


### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore


### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties


### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink


### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Use the static hardware detection module (for systems that lack udev/hal support)
load-module module-detect
.endif


### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect
.fail
.endif


### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif


### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix


### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish


### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv


### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor


### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif


### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore


### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams


### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink


### Honour intended role device property
load-module module-intended-roles


### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle


### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif


### Enable positioned event sounds
load-module module-position-event-sounds


### Cork music streams when a phone stream is active
#load-module module-cork-music-on-phone


### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply


### Load DBus protocol
#.ifexists module-dbus-protocol.so
#load-module module-dbus-protocol
#.endif


# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.


### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system


### Register ourselves in the X11 session manager
#load-module module-x11-xsmp


### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif


load-module module-switch-on-port-available


### Make some devices default
#set-default-sink output
#set-default-source input
```

---

### Post by Yellow Pasque on 2015-08-13
> Is 'system mode', at the login screen?
No, Ubuntu does not use system mode. It uses per-user/daemon mode so pulseaudio starts when you log in.

> I tried editing the default.pa file in Gedit, but couldn't save the new file, or even save as.
As always, you need root permissions to edit a system file.
```
gksu gedit /etc/pulse/default.pa
```

---

### Post by Ace..... on 2015-08-14
> **Temüjin said:**
> No, Ubuntu does not use system mode. It uses per-user/daemon mode so pulseaudio starts when you log in.
As always, you need root permissions to edit a system file.
```
gksu gedit /etc/pulse/default.pa
```

Thanks Temujin.

Went to bed last night (this morning) vowing to drop this.

Anyway, managed to get some work done.... didn't look at any feeds, until I'd achieved something :D

Pulseaudio got back to me...... apparently they need
```
pactl list
```

This should provide the info we need :? :)
Anyway, here it is with no sound:
[http://pastebin.com/meqqh3m7](http://pastebin.com/meqqh3m7)

Here it is with youtube:
[http://pastebin.com/PnuFzQcW](http://pastebin.com/PnuFzQcW)

Here are the differences I found between the two files:
[http://pastebin.com/dgK5uFQG](http://pastebin.com/dgK5uFQG)

Thanks for the reminder on gedit.
I'll check out the stereo to mono mod tomorrow :)

---

### Post by Ace..... on 2015-08-15
Tried modding default.pa this morning, by adding this to then end of the file.
```
load-module module-remap-sink master=alsa_output.pci-0000_00_1f.5.analog-stereo sink_name=mono channels=2 channel_map=mono,mono
```
It was a fail.
I lost all sound and devices.

After returning.pa to original state, I rebooted...... but I had the external speakers plugged in.

I noticed that no sound (drum roll) could be heard.
I rebooted again, without the speakers, and once more I had sound at login screen.

It made me wonder about whether the desktop sound systems should be loaded at all.

---

### Post by Ace..... on 2015-08-17
Here are a set of tests requested by the pulseaudio bods:

The amixer output showed that the "Speaker" mixer element was muted.That would explain why no sound is coming from the internal speakers.
 PulseAudio is supposed to unmute that element when activating the analog
-output-speaker port (unless the sink in pulseaudio is muted too, but
at least when you ran "pactl list", the sink wasn't muted).


You can control the Speaker mute state with these commands:


    amixer -c1 sset Speaker on
    amixer -c1 sset Speaker off


If you unmute Speaker, does that help?


To get a little better understanding, could you check what happens both
in PulseAudio when you plug in and unplug the external speakers? I'd
like to know if there's any automatic activity. So, first check the
Speaker state with "amixer -c1 sget Speaker", and also check what port
is active with "pactl list sinks" (see the "Active Port" field). Then,
plug in the external speakers and repeat the checks. Finally, unplug
the external speakers and repeat the checks again. Are there any
automatic changes in either the Speaker mixer element, or the active
port in PulseAudio?

[http://pastebin.com/jRbugw7a](http://pastebin.com/jRbugw7a)


NOTES:


we can see that by inserting and removing the jack..... the software recognises these actions, yet still fails to channel the sound to the internal speaker.


Also note, that the command to mute the internal speaker worked.
Of course..... no sound was emitting, but the graphic sound bar showed 'muted'.


My view is that almost all of the software commands are functioning.
The problem remains, that NO sound is actually being channelled to the actual internal speaker.


Please note: I ran tests at login screen using 'text to voice menu audio' (a std component of ubuntu).
This worked through both internal and external speakers.


also note: zero decibels with jack removed.
So it knows that there is no sound emitting!!!!


Nice choice of tests there ;)


Summary


The systems work vis a vis jack in/out
It recognises that no sound is being emitted.


So we are left with one option (yes?)...
... The sound is not being channelled to the internal speaker.


It must be the channelling of the sound, at a different level to jack in/out.


My guess is that the associated channel command failure is occurring before jack in/out.


Again.... we need to look at the sequence of commands, as the desktop loads.
It is there that we lose the internal speaker.


Close?
Are we closer now?

---

