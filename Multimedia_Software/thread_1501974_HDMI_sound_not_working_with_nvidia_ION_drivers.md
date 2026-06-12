---
title: "HDMI sound not working with nvidia ION drivers"
date: 2010-06-04
forum: Multimedia Software
---

### Post by n4mwd on 2010-06-04
I have a zotac IONITX motherboard with HDMI video.  The video seems fine, but I haven't been able to get the sound working through the HDMI cable.  Even the little speaker at the top is gone.  It was working fine when I had speakers hooked to the motherboard.  I have installed the latest 256 driver from nvidia.    If I run 'aplay -l' I get this:    **** List of PLAYBACK Hardware Devices ****   card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]   Subdevices: 1/1   Subdevice #0: subdevice #0  lspci -v gives :  00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)         Subsystem: PC Partner Limited Device 437b         Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22         Memory at fae78000 (32-bit, non-prefetchable) [size=16K]         Capabilities:          Kernel driver in use: HDA Intel         Kernel modules: snd-hda-intel   I am a newbie so I don't know if this is important, but I noticed that it says its running an intel driver for my nvidia sound.  Could this be the problem and if so, How do I fix it?  Also, if I click on system->preferences->sound it comes up with a dialog box that says that its waiting for the sound system to come up.  Does anybody have any clues as to why I am not getting any HDMI sound or even the little speaker icon at the top?  Thanks in advance.  PS-I don't know why the formatting isn't working on this post.  I hope you can read it.

---

### Post by farbird on 2010-06-05
try this

```

speaker-test -D:plughw:0,3

```

---

### Post by n4mwd on 2010-06-05
Thanks for your reply.

I ran the program you instructed and it did make noise in my TV speakers.  That is a big improvement from what it used to do.   Thanks for showing me the correct way to specify a device.  I was having trouble with that.

I have since run the Alsa upgrade script since my first post here.  

When I run:

> aplay -Dplughw:0,3 Music/Success.wavIt plays the sound file, but it plays very faint and tinny.

As a sanity check, I temporarily hooked up an XP drive to this motherboard and the HDMI sound played fine.  As such, I don't think it has to do with wiring or hardware.

When I use VLC to play a video, it displays the video just fine, but still no HDMI audio.

Any suggestions would be appreciated.

---

### Post by farbird on 2010-06-06
sudo apt-get install pavucontrol

look out for a new item in the apps menu under Sound & Video

use it to set the output to hdmi ...

last but not least, install smplayer... a frontend for mplayer which is easily configurable for hdmi sound output

---

### Post by n4mwd on 2010-06-06
Thanks for helping me.

I installed pavucontrol as directed.  When I run it it says that "Connection was refused".  In the main dialog box, it said that "No audio files were playing" so I tried starting it while a video was playing and it didn't make any difference.

A few things that I have noticed.... 

1. There is no speaker icon at the top of the screen.  When I had it working with regular speakers, there was a little speaker up there that I could control the volume.  Its not there since I switched to HDMI.

2. My earlier aplay experiment played tinny audio, but I tried a different file that was pure PCM rather than ADPCM.  The file plays just fine using aplay right now.

3. If I go to System->Preferences->Sound I get a dialog box that says "Waiting for sound system to respond."

4. I installed smplayer.  I switched the output to ALSA HDA and for some reason it plays tinny audio for the same audio WAV files that work for #2, but when I tried playing an MP3 file, it played flawlessly.  After that success, I played an MPG video flawlessly as well.

So thanks to you, I am getting a lot closer.  I still need it to play using VLC and Myth.  Do you know what I can do to fix that so that all players default to the HDMI device and also get my little speaker back?

Thanks.

UPDATE- Myth is now playing sound as well too.  That leaves the little speaker and VLC.

---

### Post by farbird on 2010-06-07
show here output of 
```

aplay -L
aplay -l

```

---

### Post by farbird on 2010-06-07
do u have the indicator panel applet added?

right click top panel and "add to panel" , make sure indicator applet is already in.

---

### Post by farbird on 2010-06-07
ehhehe
for myth and vlc, i am unable to help..

I am an mplayer and xbmc kinda guy...hehehe

---

### Post by n4mwd on 2010-06-07
This is what I got this morning.  It seems to do this occasionally.

> 
$ aplay -l
aplay: device_list:235: no soundcards found...

$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
After rebooting (without powering down), I get this...

> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio OutputIt has been doing that so I'm not convinced that things are stable just yet.  I don't hear the "Ubuntu Sound" when it boots up either.  I did when I used regular speakers.

I think that the indicator applet is already running.  I right-clicked the top bar and added indicator applet again and it just put another envelope on the top bar.  The ones that are already there are Network, envelope, time, switch user and logout.  But no speaker.

I was able to watch TV for several hours last night so we are getting close.  It seems like there is something probably wrong with a config file somewhere causing it to be right on the edge.  I have a log file from when I did the alsa upgrade.  Would that help?

Thanks again for your replies.

---

### Post by farbird on 2010-06-07
fyi, my setup , i used the default alsa package originally provided by ubuntu..

I didnt do the script update..

---

### Post by n4mwd on 2010-06-07
I wasn't getting anywhere until I did the alsa script update.  I'm also running the 256 beta version of the nvidia drivers.  I read on here that a lot of people were not getting the 195 version to work with the zotac motherboard. The 195 version is what comes with Ubuntu 10.04.   What motherboard and ubuntu version do you have?

This board I have may possibly be the problem.  However, since it worked fine with XP, I really can't say that its hardware.

Do you know if there is a log file somewhere that I can look at that might give a clue as to why aplay fails to show an audio device sometimes?

Also, is there a config file somewhere that will let me set -Dplughw:0,3 as my default sound device so that I get the "Ubuntu" sound when it boots up?

Thanks.

---

### Post by farbird on 2010-06-07
something to do with enable_msi

[http://forum.xbmc.org/showthread.php?t=69601&highlight=enable_msi](http://forum.xbmc.org/showthread.php?t=69601&highlight=enable_msi)

to use the hdmi as the primary sound output by editing your /etc/asound.conf
[instead of using the 1st detected sound hardware, which is the internal sound plug ]

---

### Post by farbird on 2010-06-07
most log files are stored in
/var/log

---

### Post by n4mwd on 2010-06-07
I went to that site which sent me to another site.  I got lost with the line "Ubuntu users make sure to remove the linux-backports-modules-alsa-`uname  -r` package or your newly compiled ALSA drivers will be ignored."  That makes no sense to me, but it sounds important.  What file would I find that line in?

Also, it references "/etc/modprobe.d/sound.conf" which does not exist on my computer.  The file "/etc/asound.conf" does not exist either.  There is a "/etc/asound.state" file.  Is that the same thing?

I'm really confused that all these config files are missing on my computer.

---

### Post by farbird on 2010-06-07
for ubuntu, u edit your alsa-base.conf in your /etc/modprobe.d/ folder

```

sudo nano /etc/modprobe.d/alsa-base.conf

```

add in the lines mentioned in the link above

below is an extract from the link above which u need to do [ no need to visit other links ]
[i]
aplay -l should show you something similar to this, depending on how many sound devices you have in your system:


Code:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Card 1 is the Nvidia card in this example.
open /etc/modprobe.d/alsa-base.conf and add this line:

Code:

options snd-hda-intel probe_mask=0xffff,0xfff2

If aplay -l shows Nvidia HDMI as card 0 you'll have to use this line:

Code:

options snd-hda-intel probe_mask=0xfff2

or for card 2:

Code:

options snd-hda-intel probe_mask=0xffff,0xffff,0xfff2

[/i]

---

### Post by farbird on 2010-06-08
someone solved their ion hdmi troubles here

[http://forum.xbmc.org/showthread.php?t=69479](http://forum.xbmc.org/showthread.php?t=69479)

---

### Post by n4mwd on 2010-06-08
I added the 'intel' line at the end of the file and the next reboot I did aplay -l and it said there were no sound cards.  I then did lspci and the following line was extracted:

> 00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)Which would seem to indicate that part of ubuntu knows the sound device is there, but it isn't sharing that information with the alsa system.  So then I added the alias line below to the alsa-base.conf file at the end...

> options snd-hda-intel probe_mask=0xfff2
alias snd-card-0 snd-hda-codec-nvhdmiRebooting still says that there is no sound card...  Then I ran a lsmod and the first several lines were...

> $ lsmod
Module                  Size  Used by
snd_hda_intel          20767  0
snd_hda_codec_nvhdmi    12658  0
snd_hda_codec          86936  2 snd_hda_intel,snd_hda_codec_nvhdmi
snd_hwdep               5604  1 snd_hda_codec
snd_pcm_oss            34539  0
snd_mixer_oss          13897  1 snd_pcm_oss
snd_pcm                71582  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
binfmt_misc             6587  1
snd_seq_dummy           1434  0
<snip>I don't know for sure what I am looking at, but it looks like the snd_hda_intel and snd_hda_code_nvhdmi modules are not getting called.  I tried rebooting several times and it consistantly failed.  Then I commented out the two new lines I added to alsa-base.conf and rebooted and aplay was now reporting that it found it.  Lsmod now shows:

> Module                  Size  Used by
snd_hda_codec_nvhdmi    12658  1
binfmt_misc             6587  1
snd_hda_intel          20767  0
snd_hda_codec          86936  2 snd_hda_codec_nvhdmi,snd_hda_intel
snd_hwdep               5604  1 snd_hda_codec
<snip>Unfortunatelty, subsequent reboots show no sound cards.  I found an asound.conf online and copied it to /etc/asound.conf.  That file contains:

> # Dewey Oxberger (aka Jon B)
# ASound.Conf file for HDMI Audio on MythTV
# HDMI configuration with volume control for MythTV
# Works in Ubuntu 9.04  5/9/2009

# Instructions for use
# 1) Find your hmdi hardware Card Number and Device Number.  Open a terminal and do:
#    aplay -L
#    That will list all of the hardware audio devices.  Look for the one labeled HDMI.
#    Note what Card Number and Device Number it lists (they seem to be card 0,
#    device 3 but your system may be different).
# 2) Edit the pcm.hdmi_hw device defined here to set your Card Number and Device Number.
# 3) Put this file in either /etc/asound.conf or in your home directory as .asoundrc.
#    sudo cp deweys_asound.conf /etc/asound.conf
#      or
#    sudo cp deweys_asound.conf $HOME/.asound.conf
# 4) Exit mythfrontend.  Then restart the sound system:
#    sudo /etc/init.d/alsa-utils restart
# 5) Start mythfrontend and go to the audio setup screen
#    "Utilities / Setup"  then "Setup" then "General" then "Next" until you
#    get to the Audio tab.
# 6) Fill in the info - it's case sensitive:
#    Audio output device: ALSA:hdmi_complete     <--- note you have to type in t
his field
#    Passthrough output devide: Default
#     ... Stereo... ... Passive...
#    Mixer Device: ALSA:default
#    Mixer controls: hdmi_volume                 <--- type in this field
# 7) Work your way back to Watch TV and give it a try.

pcm.hdmi_hw {
  type hw
  card 0     #  <-----  Put your card number here
  device 3  #  <-----  Put your device number here
}

pcm.hdmi_formatted {
  type plug
  slave {
    pcm hdmi_hw
    rate 48000
    channels 2
  }
}

pcm.hdmi_complete {
  type softvol
  slave.pcm hdmi_formatted
  control.name hdmi_volume
  control.card 0
}

#pcm.hdmi_complete {
#  type copy
#  slave.pcm hdmi_volume
#  slave {
#    pcm front
#  }
#}
Rebooting with that causes lsmod to show nothing at all.  Anyhow, I think I have taken a step backwards here as it is getting more resistant to working at all.

---

### Post by farbird on 2010-06-08
try posting your problem at nvnews under linux forums.

there may be some nvidia staff there that might read your thread.

---

### Post by n4mwd on 2010-06-08
I appreciate your help.  No one can say we didn't try.  But I'm starting to think that its a lost cause.  Ubuntu 10.04 was released just  a bit early.  Perhaps they'll have the hdmi audio bugs fixed in the next release.  I'd like to keep tinkering with it, but I've spent 2 weeks, about 100 hours and about $3K trying to get it to work.  Its time to throw in the towel and move on.

I'm going to look into porting myth over to windows and see what's involved in that.  It sounds fairly simple compared to the what I've been dealing with.

---

### Post by farbird on 2010-06-08
not a lost cause...
probably an incorrect forum..

the hdmi audio wasn't really ubuntu's problem as the updated drivers for nvidia are maintained by another ppa.

---

### Post by n4mwd on 2010-06-10
I've decided to put it aside for a few weeks and not be so rash.  However, its very frustrating that I can pop an xp drive in the same machine and everything works.  Nevertheless, I really want to make this work.  I'm thinking that the next time I try to get this going that I will wipe the disk and start with a fresh install.  When I installed the last time, I had speakers plugged in.  Maybe that ruined it for hdmi.  Thanks.

---

