---
title: "No Sound via HDMI"
date: 2010-06-04
forum: Multimedia Software
---

### Post by jda8818 on 2010-06-04
Ubuntu 10.04 LTS installed 6/3/2010 on Zotac H55ITX w/i3 530.  DVI -> VGA & analog stereo sound & video OK but NO sound w/HDMI (into Samsung UN40C7000WF)

I've upgraded when prompted by Upgrade Manager.

aplaly -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I've added my username to /etc/group so that grep 'audio' /etc/goup returns
audio:x:29:pulse, jadcock

alsamixer (v1.0.22) has no muted paths, and reports: Card: HDA Intel; Chip: Intel G45 DEVIBX

I've tried all sorts of combinations with the 'Sound Preferences' dialog as well as 'Multimedia Systems Selector' without any luck

Thank you all in advance for any help/comments,

JA

---

### Post by jda8818 on 2010-06-04
Just ran AlsaUpgrade-1.0.23-2 ... all OK per soundcheck's post, all completed OK,

but:

on reboot: 17.289992 Kernel Panic - not syncing: No init found. etc, etc.

are you guys working for Bill Gates?

---

### Post by jda8818 on 2010-06-05
Well, another reboot, and guess what?  ZZTop!!!  I'm stoked!

[LEFT]the AlsaUpdate script solved the problem!  (temporarily?)

we'll see

thanks for the knowledge base!

JA
[/LEFT]

---

### Post by jda8818 on 2010-06-05
Update:

HDMI audiio is working. Rhythmbox Audio OK, systems sounds OK, but no audio from Firefox (Youtube, Pandora, etc)

Thanks in advance for any comments or suggestions,

JA

---

### Post by lidex on 2010-06-05
Check these out:
[http://ubuntuforums.org/showpost.php?p=9214160&postcount=15]("http://ubuntuforums.org/showpost.php?p=9214160&postcount=15")
[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")
[http://ubuntuforums.org/showthread.php?t=1412153]("http://ubuntuforums.org/showthread.php?t=1412153")

---

### Post by jda8818 on 2010-06-06
Thanks lidex for your reply!

Looking  at the three posts you referenced, it seemed to me that perhaps flash is not interacting properly with the ALSA API, so I decided to create (gsku gedit /etc/asound.conf) an /etc/asound.conf file with the code:

pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }

(reply window doesn't like tabs)  (no semicolons?)

save, quit, verify file exists in /etc/, look at it OK, reboot and ... ... and ...

no sound at all. no more system sounds, no more rhythmbox, and a red x next to my sound preferences dialog icon in the topscreen toolbar.

so i guess i'll remove the file

interestingly enough, my aplay -l command results have changed, since the ALSA .23 upgrade i think, to include a card 0 device 7 INTEL HDMI 1 [INEL HDMI 1] listing:

jadcock@HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jadcock@HTPC:~$ ^C

is there a sudo command to delete the file from /etc/ ?

I'll be keepin' on

Thanks again

JA

---

### Post by jda8818 on 2010-06-06
Removed /etc/asound.conf (sudo rm /etc/asound.conf), verified gone, rebooted, no sound at all. rebooted again, no sound at all.

Back at square one.

Still have the red x adjacent to sound preferences icon.  

Apparently running the asound.conf file had a (semi?) permanent affect.  Where would this affect live?  how can i correct it?

As before,:confused: suggestions or comments are more than welcome.

JA.

---

### Post by jda8818 on 2010-06-06
DVI -> VGA & analog sound: no sound.  So I have killed the analog sound that was working all along!

four lines of code in a configuration file that no longer exists!

reinstall the OS?

Help!

---

### Post by lidex on 2010-06-06
You should be able to click on volume icon and select 'unmute'

---

### Post by jda8818 on 2010-06-06
right you are lidex!

so at this point I have system sounds and rhythmbox  back when using HDMI input. but no flash thru firefox.

On the otherhand, when using good old VGA & analog audio I have no system sounds, no rhythmbox, yet flash audio works via firefox.

whew!

thanks for your interest!  I certainly appreciate it lidex!

My goal, however, is HDMI video and sound, is it possible?

as always, thanks in advance for all comments and suggestions.  

JA

---

### Post by lidex on 2010-06-06
Since you know how to unmute now try using that config file again. Use sound preferences to select the correct outputs and gnome-alsamixer to enable spdif/digital.

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

---

### Post by jda8818 on 2010-06-06
dear lidex,
please try to control your sarcasm,

I'm certainly trying to control mine.

thank you again

JA

---

### Post by lidex on 2010-06-06
> **jda8818 said:**
> dear lidex,
please try to control your sarcasm,

I'm certainly trying to control mine.

thank you again

JA

I'm not sure what you mean but no slight is intended, however it may read :rolleyes:  This link may be of service:
[http://ubuntuforums.org/showthread.php?t=1466111]("http://ubuntuforums.org/showthread.php?t=1466111")

---

### Post by jda8818 on 2010-06-06
OK, well then, what is gnome-alsamixer?  so far it seems that ALSA runs on top the hardware, and Pluseaudio runs on top of ALSA and acts as a server to whomever clients (maybe not flash).

where in this mix does gnome-alsamixer live? what does it do?

as always, lidex, 

your dear friend,

JA

---

### Post by lidex on 2010-06-06
It's a gui frontend for alsamixer. It exposes the available elements for your soundcards in a much more accessible way than the terminal alsamixer. Makes it a lot easier to enable/mute/unmute etc. With the digital elements they have to be manually unmuted.

---

### Post by jda8818 on 2010-06-06
to let you know, i resent your 'roll your eyes (sarcastic)' smiley in your reply

as always

your dear friend

JA

---

### Post by jda8818 on 2010-06-07
Sound via HDMI works! In fact, everything seems to be working!

To sum up (chronologically):

Zotac H55ITX (BIOS 08.0.15 3/2/2010) i3-530
New 10.04 LTS Install plus all updates per prompts from Update Manager.
VGA & analog sound OK, but no HDMI sound.
Obtained and ran ALSA Upgrade Script AlsaUpgrade-1.0.23-2.
HDMI system sounds & Rhythmbox sound OK, but no sound in Firefox.
Created /etc/asound.conf file consisting of the code:

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

Success

Notes:
When the original install was finished I was prompted to reboot.  The machine did not shut down cleanly & I was forced to power down after a string of I/O errors.  Subsequent reboots OK.

After the AlsaUpgrade script the machine hung on first reboot - but subsequent reboots OK. 

First reboot after /etc/asound.conf file creation the sound was muted for some reason.  Which admittedly I didn't recognize. I may have been alble to simply unmute at that point, but I'll never know.  I removed the file, then recreated it, rebooted, and everything seems to be working properly, including flash in Firefox.  The first reboot after the /etc/asound.conf file was recreated did not result in muted sound.  Subsequent reboots have all been normal (boring). 

thanks to everyone for their help!

JA

---

### Post by Hopey on 2010-08-24
jda8818 I've been figuring this out and finally got it working thanks to your asound.conf file. Thank you!

---

### Post by agarciamog on 2010-10-01
Thank you. 

I spent many hours trying all sorts of things. What ultimately worked on my Linux Mint Debian box was creating the /etc/asound.conf file.



Additional Tags: flash hdmi sound ubuntu effects pulseaudio alsa asound.conf

---

