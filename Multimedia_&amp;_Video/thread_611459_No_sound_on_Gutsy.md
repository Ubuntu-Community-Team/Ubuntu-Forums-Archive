---
title: "No sound on Gutsy"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by raja.aydina on 2007-11-13
my sound has suddenly stopped working in the last couple of days.. ive checked through the volume controls and through sound thing from system>sound pref.. here is my lspci. i would really appreciate any help

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by Yellow Pasque on 2007-11-13
I'm not good with ALSA problems, but if all else fails, you can always remove alsa (deselect alsa-base in synaptic) and use OSS instead.
([http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi) and install the x86 or AMD64 DEB package for Linux 2.6.x)
The Nvidia MCP51 High Def Audio is on the list of supported devices in OSS ([http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html)).

---

### Post by raja.aydina on 2007-11-28
I tried switching to OSS and when I do a sound test theres only static. When I tried switching back to alsa, it wasn't recognized either. When I click on the volume, it says "No volume control GStreamer plugin and/or device found." Any ideas?

---

### Post by vetruven on 2007-11-29
I would Like to join to this thread - i had the very same problem - all of the sudden my sound stopped (disappeared).
here is my lspci
```
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 70)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: V8233 [VIA 8233], device 0: VIA 8233 [VIA 8233]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8233 [VIA 8233], device 1: VIA 8233 [VIA 8233]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by A + on 2007-11-29
Just downloaded it Sunday to a Toshiba Equium laptop celeron processor etc.  I didn't imagine I'd be having such nutty problems playing a CD!!!  Depending on something (the weather?) the sound gets muted after playing two or three songs or a youtube video - it works fine up to that.  Either of you experience these problems?  Because it worked perfect on first install and i got the drum roll and all.  I figure it's some buffer in the sound card or sound device not getting cleared.  I also got feedback while CD playing but that went away after a fresh (third) install yesterday.

Because I'm guessing some hardware switches are not getting set on boot-up, if I am closing Vista now and want to go into Ubuntu I mute the sound in Vista in the volume control panel before I shut down and reboot into Ubuntu and now the sound is restored in ubuntu :) ...  :confused:.  Right now I've just played some songs off a CD, went into youtube, played a song and then that was that - Ubuntu went back to Africa - time to reboot so I can hear the rest of the CD.  Three letters: WTF?!

---

### Post by vetruven on 2007-11-30
HI wanted to update - my problem was less strange than i thought - i've used gxine - and for some reason if you mute in it - it mutes all the sounds - also ALSA is not looking muted.

Oh well - stupid things happen sometimes :)

---

### Post by raja.aydina on 2007-12-04
i reinstalled ubuntu hoping to get sound back but it didnt help

---

### Post by stegreen on 2007-12-04
Hi 
I am having the exact same problems. Sound works perfectly after a reboot, but once I touch the volume control in any of the applications I lose sound and can't get anything back.

I have been searching all over the place for a solution and it seems that there is some merit in looking further into the .asoundrc file but at the moment I am not sure what needs to go in there.

Here's some of my outputs
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 lspci 
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1)
04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

If I find anything that sorts it out I'll post a solution here:)

---

### Post by capella on 2007-12-04
Ubuntu Gutsy 7.10 Gnome Desktop AMD Athlon 64 (32bit Software) HDA Nvidia ALC861 ALSA 
I had the same problem.
Initially sound was partially available but poor quality. Then at some point it failed in most apps. I had somehow acquired some modules of Pulseaudio. The error log showed that the OS could not load Pulseaudio modules so I thought the problem was that the other Pulseaudio modules should be loaded and did so. Sound improved for Amarok and system sound but no sound in BBC streaming audio which uses Realplayer, no sound in streaming Flash video in YouTube or Google, and no sound in Audacity and no recording ability or microphone for Skype.
I also now had a confusing array of sound settings with multiple mixers.
I followed the advice on this site [http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753) and reinforced here [http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound](http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound)
Most of the Howto: Happy ALSA, OSS, ESD, with Duplex - Sound Settings written by "Intangible" but many of the comments and additional links are useful.

Procedure is:
1  Disable sound server startup if you have this option in System - Preferences - Sound (I don't, maybe it isn't in Gutsy but in previous releases)
2  Ensure you have libesd-alsa0 and the Gnome Alsa Mixer installed - these should be available from Synaptic Package Manager.
3  Change or, if none already exists, create an /etc/asound.conf page ("sudo gedit /etc/asound.conf" - then paste in the code)to look like:
Code:

# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}

The first setting will let you select a different sound card as your primary if you have multiple sound cards.

4  Change the /etc/esound/esd.conf entry to:
code:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
 

5  Change the /etc/libao.conf to:
Code:

default_driver=alsa

6  Reboot

REALPLAYER
1  To ensure that RealPlayer will play ram files by default change this in Firefox - Edit - Preferences - Content tab - File Types Manage. Select the Ra file type then Change action. Browse to the realplay script in the realplay-10.0.9 folder in /usr/lib and select it.
Follow the BBC help advice here: [http://www.bbc.co.uk/radio/audiohelp_nix.shtml](http://www.bbc.co.uk/radio/audiohelp_nix.shtml) for workarounds to realplayer problems, particularly, to copy nphelix.so and nphelix.xpt into the firefox plugins folder /usr/lib/firefox/Plugins (it should already be in the Mozilla plugins folder in /usr/lib). I also copied it into mozilla-firefox plugins folder for good measure. 

2  To ensure that Realplay doesn't stutter when playing, change the buffer value in the asound.conf file from 4096 to 8192
3  To ensure that Realplayer will play even if other sound modules are running, follow this advice here [http://ubuntuforums.org/showpost.php?p=80282&postcount=21](http://ubuntuforums.org/showpost.php?p=80282&postcount=21)  which is #21 from the "What's wrong with my Realplayer" thread [http://ubuntuforums.org/showthread.php?t=7017](http://ubuntuforums.org/showthread.php?t=7017)
 
4  Finally, in, System -Administration - Sound, set Alsa for playing sound playback and Music and Movies and set OSS for sound recording (required by Audacity and others). Select the Alsa mixer for default mixer tracks and PCM as "keyboard" control (actually sets which systray icon alters volume.)
In the Sounds Tab, enable software sound mixing.

However I still had to remove all the Pulseaudio modules before Flash video sound would work. Most modules could be Marked for Complete Removal but padevchooser could only be partially removed because of shared libraries with Amarok and others. Choose "Mark for Removal" in Synaptic Package Manager for this package.
Now, system sound works, Flash video works, Realplayer and Audacity work, Amarok works.Have not yet tried Skype or recording.
Skype advice on OSS here [http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html)
Apologies for length of this reply!

---

### Post by raja.aydina on 2007-12-04
I followed the instructions and after the reboot i still got no sound, either in flash plugins or mp3 files on the computer. When tried testing the sound in the sound preferences, I would get the following error: (for all settings)

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not establish connection to sound server

Is it possible im missing some packages?

---

### Post by capella on 2007-12-05
I think you must have missing sound modules, or still have pulseaudio modules installed. I typed "pulseaudio" into the Synaptic search which listed all the modules so I could then uninstall them.
However - I do get the error message:
"Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'" for the audio conferencing - sound capture test.
I haven't tried recording yet and assumed this error was because I don't have a mic attached. Also, posts in the "Happy Alsa" thread suggest the OSS mixer should be selected for recording.  Will follow this up and post back if I have success.
All other sound tests work with the ALSA mixer selected and HDA NVidia (Alsa Mixer) selected as device for default miixer tracks. I use Amarok for music, Audicity for converting and realplayer as the streaming audio app. Xine does the streaming video and I have the Flash non-free plugin.

---

### Post by capella on 2007-12-05
Just noticed that you didn't have gstreamer installed. Maybe that's what's missing. Here are all the gstreamer modules I have - listed in Synaptic:
gstreamer-tools
gstreamer0.10-alsa
gstreamer0.10-esd
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-gl
gstreamer0.10-gnomevfs
gstreamer0.10-gnonlin
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-farsight
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-schroedinger
gstreamer0.10-sdl
gstreamer0.10-tools
gstreamer0.10-x

---

