---
title: "NVidia GT220 Audio passthrough over HDMI"
date: 2010-06-09
forum: Multimedia Software
---

### Post by mod-u-lar on 2010-06-09
Hi,

I've been searching and reading for a solution for over a week now and the more I read the more I get confused and I'm just not able to connect the dots regarding NVidia, audio and HDMI.

I have Ubuntu 10.04 installed and updated the ALSA driver to version 1.0.23 using the script posted in another thread on this forum. Although I got a config issue in the process my NVidia HDA device shows up with

xbmc@MediaPortal:/etc/modprobe.d$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

xbmc@MediaPortal:/etc/modprobe.d$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, VT1708S Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, VT1708S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, VT1708S Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output

Which brings me to my first question, why do I see four NVidia HDMI devices (3,7,8 & 9) in aplay -l, I couldn't find an explanation for this?

Next I got smplayer giving audio over HDMI when selecting either of the HDMI devices in the audio config menu, but after a reboot, even if one of them is still selected I need to change and apply before I hear sound. Is Pulse Audio or alsa or some other thing interfering? 

Now as I'm really interested to get XBMC working, smplayer was just a first test, I really hit a wall, I just do net get sound working although XBMC lists HDMI for sound output and for passthrough. More precisely I have the options (High Definition Audio Controller Digital Stereo (HDMI), default, custom) for Output Device and (HDA NVidia hdmi and hdmi) for Passthrough of which I tried all combinations.

I'm thinking the system is currently confused as to which device to use but none of the things I read gave me a clue on what to change.

Any help, directions are more than welcome.

Cheers,
Jochen

---

### Post by mod-u-lar on 2010-06-11
Bump, anyone? I'm really stuck with this.

---

### Post by korser on 2010-07-20
I have the same problem and came across this: [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

Let me know if you manage to get it working

---

### Post by infraction on 2010-07-20
Korser and Mod-U-Lar:

I have been chasing this catastrophe for weeks.  The link Korser posted I've used before and was indeed helpful, but only up to a point (that being how to get and install alsa 1.0.23).  The remaining crap about changing .conf file(s) is lost on me....I've had zero success with that nonsense.

At this point (since I REALLY want a PC to provide content from my network as well as the net), is to locate a cheap but acceptable sound system that will take audio from my analog (that is, headphone) port.  That will be only stereo, I know, but I'm not one of the European college students that develop for Ubuntu who seems to think this **** is easy!!  I see no way around these HDMI audio problems besides much pain and disappointment.  And, of course, there is the added pain of losing alsa 1.0.23 when Ubuntu decides your kernal needs an upgrade.  Yeah, gotta love this linux 'love to everybody' attitude.

[MODERATORS:  please feel free to report me as a hostile poster.....why do you think my handle is 'infraction' ?????]

I may, however, have some ideas that even I don't expect....I actually work on Unix for a living.  Please continue your postings and will try to be more supportive.  At this time, I cannot do that.

Regards,
infraction

---

### Post by dream_coder on 2010-07-21
I got mine working, I installed newest alsa stable using the script and then rebooted, then followed this [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240) took me a while to get right combination but got there in the end hope this helps.

Remember to reboot each time you try a different option in alsa-base.conf to check if sound is working :) oh and also remember to use the sound preferences and select hdmi output and increase the volume :)

Alot of problems are caused because of nvidia on-board audio as I had the same problem but after tinkering about and 2 fresh installs I have it working all the time, for some reason if I installed the updates for lucid after I got sound working I did not have a problem but if I installed updates after the sound stuck and works flawlessly :S hence why it took me two fresh installed lol although it could be the proprietary driver for my gt210 that caused some issues I am not entirely sure.

Here is what I did:

1)Fresh Install
2)Updated Alsa using the Script here in the forums
3)Rebooted
4)Modified alsa-base.conf more than a few times and rebooted and selected hdmi output in preferences until I got sound)
5)Installed nvidia vdpau drivers from the ubuntu vdpau ppa
6)Updated ubuntu

---

### Post by korser on 2010-07-22
Can you post your alsa-base.conf so it can help us?

I've been trying for quite a few nights now and I haven't been successful. I looked at this link in hope to find how to configure multi card:

[http://alsa.opensrc.org/index.php/MultipleCards](http://alsa.opensrc.org/index.php/MultipleCards)
 
I still can't get any sound out. 

Are you using plug:default:1 when setting your audio output in XBMC?

---

### Post by dream_coder on 2010-07-22
yeah no worries here you go:

> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

---

### Post by gaelfx on 2010-10-01
Not that this information should matter to you at all, but I believe that in the nvnews forums, one of the moderators referenced the fact that the audio chip on those graphics cards is actually four separate devices (presumably for different channels/audio configurations), so that's why aplay -l displays four devices.

To swing back to relevant things, I was wondering if any of you have heard of solutions that allow pulseaudio to remain intact?

---

### Post by bprins on 2010-10-26
what did the trick on my laptop is following the xbmc documentation.

if you still have 4 devices listed, tune the probe_mask by editing the **/etc/modprobe.d/sound.conf**
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

Important note: the probe_mask is dependent on your hardware. For details check [http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

Second, make sure that your user account is member of the audio group:
- users & groups
- edit user
- manage groups
- check audio group
- enter name
- OK

Reboot, attach HDMI cable
aplay -D **plughw:1,3** /usr/share/sounds/alsa/Noise.wav
Important note: 1,3 refers to #card,#device, which depends on your hardware.

If you have sound, 
try via Xbmc and ...
:guitar:

If not, post back problems and I'll try to help out

---

### Post by dartmusic on 2010-10-26
I believe (in my own personal experience with this exact card) that PulseAudio is the culprit.  I am at work and not in front of my HTPC so some of these pointers below are from memory.

I did the ALSA upgrade on Lucid and had to hunt and peck through a number of options before I could get this to work, but I did.  I recently did a fresh Maverick install and below is all that *I* needed to do to get one stereo pair from the GT220 to pass stereo audio from my entire system via the default audio settings.

First, let me say that it seems that Pulse is only seeing 3 of the 4 sets of possible outputs. I believe that ALSA is showing your possible 7.1 (8 total) outputs as 4 stereo pairs. The only way that I could get stereo sound from my system (I only have a 2 channel receiver, so stereo was all I was concerned with getting out of my HTPC) was this:  

- In a terminal window type "gstreamer-properties". There will be a dropdown box - click to scroll through all possible outputs. These are not audio cards, but physical outputs across all possible audio cards, you may therefore see your built-in audio card outputs as well as your Nvidia HDMI outputs.  I had only 3 NVIDIA HDMI entries, where I should have had 4.  If you select each NVIDIA HDMI output, you'll notice a greyed out text box that changes info with each different entry chosen in the dropdown.  If you scroll between the 3 NVIDIA HDMI entries you'll see similar strings that all end with something like "hw:1,9". Note each one.  According to the aplay -l output listed at the beginning of this thread, the possible options are hw:1,3 or hw:1,7 or hw:1,8 or hw:1,9.  Whichever of these DOESN'T show up is what you need to note.  Close the gstreamer-properties window.

- While still in the terminal window type, "sudo gedit /etc/pulse/default.pa" and find the line (approx 147?) that reads "#load-module module-alsa-sink device=hw:x,x", delete the # at the start of the line and replace "hw:x,x" with the numbers that were missing from the options in gstreamer-properties.  For me, this was hw:1,8 which means that for some reason some part of the audio subsystem was ignoring output 8 on audio card 1 on my HTPC.  This will force PulseAudio to recognize this and make it the default stereo output on your computer.  I would recommend backing up this file before making any edits mentioned above.  A simple "sudo cp /etc/pulse/default.pa /etc/pulse/default.bak" should suffice.

Now reboot your computer.

When finished booting, open a terminal and check that alsamixer shows 4 separate outputs and that they are all unmuted.

Open sound preferences and check to make sure that the appropriate entry/card is selected on the hardware tab.  Try testing the output.  If you hear a "bonk" or whatever sound it should be making, you SHOULD be fine and XBMC should play sound with the default settings. 

If you still don't have sound, open a terminal and type "gstreamer-properties" and see what is selected.  I BELIEVE that Autoselect worked for me, but you can look in the dropdown (there should now be 4 NVIDIA HDMI listings) and click through each one and test to get a solid, clear "beeeeeep."  

IF you still don't get sound, choose any of the NVIDIA HDMI options, then immediately choose "Custom" and change the "hw:x,x" portion of the line that is now NOT greyed out to match what you entered in the /etc/pulse/default.pa file.  This should force the default output in gstreamer to be the same output as you forced PulseAudio to use when you edited the file above.  

Keep in mind that all of this definitely worked on my system on a fresh, clean install.  I did NOT do the ALSA upgrade and this was the first thing I did after the install, since I knew there would be problems and didn't want other package installs or updates to cause problems getting sound to work.

While this is ugly (and whoever is in charge of PulseAudio should be ashamed that this is what we have to resort to some 2+ years after this being being included in major distros), but not as bad as some of the other workarounds I read made it.

Hopefully if this doesn't completely work for you, at least it will point out some places to look to figure out how to get your system working.

Good luck!

---

