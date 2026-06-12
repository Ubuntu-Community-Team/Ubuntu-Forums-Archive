---
title: "nf4 ultra sound chip, spdif doesn't work"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by Wille on 2005-10-13
New that breezy is "out", I have some hope of this problem being noticed...

I have an nforce 4 ultra motherboard with ALC850 sound chip. The sound works ok through line-out, but optical spdif won't work at all. It works correctly in Windows. Messing around in alsamixer doesn't help.

alsamixer shows:

Card: NVidia CK804                                                           
Chip: Realtek ALC850 rev 0

I've googled the net, seen the bug posted in alsa bugzilla, but apparently it was never resolved. Are there going to be proprietary nvidia binary drivers or something to make this work?

---

### Post by fordp on 2005-10-15
I have the same problem on my NF2 IGP MSI Mega 180 system.

This is the third version with this problem.

I got the previous two going by manually installing the nvidia drivers.

I never got midi working in Warty or Hoary :(

I have tried to install the latest nvidia driver in Breezy. I managed to get it to build. I have not got it to take over from the snd-intel8x0 driver yet.

If you want to try follow the instructions for preparing to install the nvidia graphics drivers, that will help for the audio driver too.

In particular you seem to need to install

1) Kernel Sources and Headers
2) Build Essentials
3) GCC3.4
4) and enable GCC3.4 in a command line
5) sudo sh .. the installer !

Good luck.

Any ideas out there ?

---

### Post by mcduck on 2005-10-15
Well, in my nForce2-motherboard (A7N8X-E Deluxe with SoundStorm) the S/PDIF seems to work as a separate sound card. For example in xmms I choose ALSA as output plugin, then I click 'configure' and write hw:0,2 in the 'audio device-field. Then xmms plays everything through s/pdif, not analog output.

Same thing for other programs, hw:0,0 for analog, hw:0,2 for S/PDIF.

I wonder what hw:0,1 would do.. ;)

(I haven't installed any drivers for nVidia, I don't mind the missing Dolby Digital mixing, It's actually better this way. I can put some music on through the S/PDIF and use analog outputs for other audio)

---

### Post by viz_e on 2005-12-07
I have the same prob too.... :???: 

I have a AMD64 with Gigabyte MoBo with NF4 and no Spdif output :confused: 

After a lot of time, I could install the Nforce drivers but they also didn't helped... Now I have the new Kernel 2.6.12-10-amd64-generic and I can not find the sources to try again...

I also have hw:0,2 but it also does not help...

Any new ideas/fixes? Thx!

---

### Post by PsyberOneZero on 2005-12-07
I had the same problem and with enough playing I found the settings that work, see attached thumbnails. They are the ALSA mixer panels, once these are set do not mess with the OSS settings it will mess it up (not badly but you have to change the settings in alsa back).

This method requires no additional software or compiling :)

To get all these go in to preferences and just check everything.
The most important settings are in the options tab set this exactly as shown as well as switches, and IEC958 Playback AC97-SPSA must be all the way down or muted.
As I'm writing this I've got (Fall Out Boy - Yule Shoot Your Eye Out) playing through my coax to my 5.1's

---

### Post by viz_e on 2005-12-08
Thank you, I will try... :D :D 

I hope that the Nforce drivers does not mess up this solution...

---

### Post by viz_e on 2005-12-08
It is unbelivable!!! :D :D It works!!

I don't know why.... but, who cares? ;)

Thank you very much again! :cool:

---

### Post by viz_e on 2005-12-11
Any idea to enable direct ac3 output (for 5.1 stream)? I tried to open mplayer with the proposed option (I don't remember right now which), but I always get a stereo sound.... :rolleyes:

---

### Post by polt on 2005-12-20
SPDIF also does not work on Intel sound boards (it's a STAC9223 chip and ICH7 controller). The board has 5 analog and one digital optical output in the back, and two analog outputs in the front. But... if you display volume control there is hardly anything! We just get PCM and MUX, not all the wonderful Dolby 7.1 controls that you guys are picking up on the nVidia board. Messing with mutes does not seem to work here.

Details: The analog outputs on the back work fine. The digital (SPDIF or IEC958) output is optical. I'm using AMD64 version of Breezy. alsamixer displays the same controls as the volume control -- basically only a switch for IEC958.

There is some info about inserting a "model" description. Does this go in /etc/modules.conf? What is the precise format? The things I've tried do not work. The applicable models are "allout" and "5digital_out". You can see documentation of this in ALSA-Configuration.txt,  which is on your system, just search from /).

The snd-hda-intel module is loaded, as are the rest of the ALSA driver modules. The optical cable is OK, as is the amplifier, which is turned on, etc. The board and the computer are new and so it probably isn't borken or burned out. Is this output mode supported? Any ideas?

---

### Post by Jason_25 on 2006-01-04
I found how to get the nvidia audio module to "take over" once built.  SPDIF works like a dream after this.

[http://www.nvnews.net/vbulletin/showthread.php?t=54595&highlight=spdif](http://www.nvnews.net/vbulletin/showthread.php?t=54595&highlight=spdif)

Check mo_x's post.

---

### Post by Unrivaled on 2006-01-25
I have an N-Force 2 audio adaptor and it uses the hw:0,2 for SPDIF. After hours of searching the net for solutions, there was a solution!
First, I switched "Multimedia Systems Selector" to ALSA. I then created a file called .asoundrc in both my home directory and my /etc/ directory. I filled it with the following and rebooted. It worked perfectly!

[I]pcm.!default {
type plug
slave.pcm "dmixer"
}


pcm.dmixer {
type dmix
ipc_key 1024
slave {
pcm "hw:0,2"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
bindings {
0 0
1 1
}
}

ctl.dmixer {
type hw
card 0
}[/I]

---

### Post by andefeldt on 2006-06-10
Well, I'm having problems getting my SPDIF to work on my nForce4 chipset motherboard (Asus A8N-SLI). I've changed my mixer settings (gnome-volume-control) to the exact same as PsyberOneZero. 

If I play a song in mplayer without any options, the song is played in my 2 monitor speakers. I then try to do:

mplayer -ao alsa:device=spdif test.mp3

mplayer plays the song, but no sound is heard from neither my monitor speakers nor my surround speakers connected to my receiver. My computer is connected to my receiver via Coax SPDIF. 

I'm running Ubuntu-5.10. I don't have a .asoundrc file. I've also checked my alsamixer for muted entries, but no one is found.

A strange thing though, when I look in the "Multimedia Systems Selector" the sound settings are set to ESD and OSS. I don't know if that has anything to do with this?

But what could be the problem? Anybody with an idea? Also, isn't it possible in Ubuntu (as you can in Windows) to output all sounds to BOTH the regular monitor speakers and to the SPDIF?

Please help me...

Anders

---

### Post by Jason_25 on 2006-06-10
It doesn't work with the ALSA snd-intel8x0 driver period.  I challenge someone to show me otherwise.  The OSS driver from nvidia's website works fine though.  The OSS driver isn't all that good for desktop use because you can't have multiple sounds, but I use the PC I have connected with SPDIF just as a media center, not a desktop.

---

### Post by andefeldt on 2006-06-10
This seems a bit strange to me, since (as far as I've found out) people have SPDIF working with this driver and I saw it on the alsa-project.org page ([http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Nvidia&card=.&chip=nForce&module=intel8x0](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Nvidia&card=.&chip=nForce&module=intel8x0))

Search for spdif on that page. The comments are from 2003, 2004. And then it worked! However, a lot of the people are having a motherboard with the nforce2 chipset and not the nforce4. I guess that's the problem. 

I not really sure, if I want to use the nForce drivers from NVidia, since it's OSS and I've had so many troubles with them earlier (in Mandriva).

---

### Post by Jason_25 on 2006-06-10
Looks like quite a project to me.  With the nvidia driver, when you run a program with sound, it comes through the spdif.  Very simple.

Anyway, post back if you have any success.  Especially with AC3 passthrough ;)

---

### Post by andefeldt on 2006-06-11
Is the sounds coming through both the normal output and the spdif?

---

### Post by Jason_25 on 2006-06-11
I'll have to check on that.  I've never used the normal output of that board.

---

### Post by andefeldt on 2006-06-11
Well, well, well...

It works with snd_intel8x0!:D 

I haven't tried a dvd yet, but will do that later today. But now, I have sound in both my monitor speakers AND through my receiver via the SPDIF connection! SWEET!

I just used the .asoundrc file from 
[http://www.mythtv.org/wiki/index.php/DigitalSoundHowTo](http://www.mythtv.org/wiki/index.php/DigitalSoundHowTo) 
but changed the device from 1 to 2 in the following section:

```

pcm.digital-hw {
  type hw
  card 0
  device 2 # Used to be device 1
}

```

I'll report back later with my dvd-story :) 

Anyway, my entire .asoundrc file is:

```

# ~/.asoundrc or /etc/asound.conf
# ALSA configuration file

##### USAGE #####
# Save this file as "~/.asoundrc" (for user-specific sound configuration) or
# "/etc/asound.conf" (for system-wide sound configuration) and specify ALSA
# device names ad described in the next section.


##### DEVICE NAMES #####
# This configuration file defines four devices for use by the user.  Those
# devices are "analog", "mixed-analog", "digital", and "mixed-digital".  The
# user may also re-define "default" to be identical to one of the above-named
# devices (i.e. to send all sound output to the digital output unless otherwise
# specified).  Use the device names as described below:
#  - "analog" outputs to the analog output directly and (at least on software
#  sound cards) blocks other audio output.  After playback completes, "queued"
#  sounds are output in sequence.
#  - "mixed-analog" mixes audio output from multiple programs into the analog
#  output (so you can hear beeps, alerts, and other noises while playing back
#  an audio stream).
#  - "digital" outputs to the digital output directly.  Since most (all?)
#  digital outputs expect 48kHz PCM audio, this may not work for some playback
#  (i.e. CD's--which are 44.1kHz PCM audio--or 32kHz audio streams from TV
#  recordings, etc.).
#  - "mixed-digital"

# All other devices created within this file are used only by the configuration
# file itself and should /not/ be used directly.  In other words, do not use
# the devices "analog-hw", "dmix-analog", "digital-hw", or "dmix-digital".


##### IMPORTANT #####
# To make this ALSA configuration file work with your sound card, you will need
# to define the appropriate card and device information for the "analog-hw" and
# "digital-hw" devices below.  You can find the card and device information
# using "aplay -l".


##### Configuration File #####

# Override the default output used by ALSA.  If you do not override the
# default, your default device is identical to the (unmixed) "analog" device
# shown below.  If you prefer mixed and/or digital output, uncomment the
# appropriate four lines below (only one slave.pcm line).
#
# Note, also, that as of ALSA 1.0.9, "software" sound cards have been modified
# such that their default "default" device is identical to the "mixed-analog"
# device.  Whether using an ALSA version before or after 1.0.9, it does no harm
# and has no affect on performance to redefine the device (even if the
# redefinition does not change anything).  Also, by using this ALSA
# configuration file, you once again have access to unmixed analog output using
# the "analog" device.
pcm.!default {
  type plug
## Uncomment the following to use "mixed-analog" by default
  slave.pcm "dmix-analog"
## Uncomment the following to use (unmixed) "digital" by default
#  slave.pcm "digital-hw"
## Uncomment the following to use "mixed-digital" by default
#  slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the card
ctl.!default {
  type hw
  card 0
}

# Alias for (converted) analog output on the card
# - This is identical to the device named "default"--which always exists and
# refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog" to access analog
# output on the card
# - Note that as of ALSA 1.0.9, "software" sound card definitions redefine
# "default" to do mixing, meaning this device is different from "default" and
# allows playback while blocking other sound sources (until playback
# completes).
pcm.analog {
  type plug
  slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the card
ctl.analog {
  type hw
  card 0
}

# Alias for (converted) mixed analog output on the card
# - This will accept audio input--regardless of rate--and convert to the rate
# required for the dmix plugin (in this case 48000Hz)
# - Note that as of ALSA 1.0.9, "software" sound card definitions redefine
# "default" to do mixing, meaning this device is identical to "default" for
# "software" sound cards.
pcm.mixed-analog {
  type plug
  slave.pcm "dmix-analog"
}

# Control device (mixer, etc.) for the card
ctl.mixed-analog {
  type hw
  card 0
}

# Alias for (converted) digital (S/PDIF) output on the card
# - This will accept audio input--regardless of rate--and convert to the rate
# required for the S/PDIF hardware (in this case 48000Hz)
pcm.digital {
  type plug
  slave.pcm "digital-hw"
}

# Control device (mixer, etc.) for the card
ctl.digital {
  type hw
  card 0
}

# Alias for mixed (converted) digital (S/PDIF) output on the card
#  - This will accept audio input--regardless of rate--and convert to the rate
#  required for the S/PDIF hardware (in this case 48000Hz)
pcm.mixed-digital {
  type plug
  slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the card
ctl.mixed-digital {
  type hw
  card 0
}

# The following devices are not useful by themselves.  They require specific
# rates, channels, and formats.  Therefore, you probably do not want to use
# them directly.  Instead use of of the devices defined above.

# Alias for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.analog-hw {
  type hw
  card 0
  # The default value for device is 0, so no need to specify
#  - Uncomment one of the below or create a new "device N" line as appropriate
#    for your sound card or 
#  device 1
#  device 4
}

# Control device (mixer, etc.) for the card
ctl.analog-hw {
  type hw
  card 0
}

# Alias for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.digital-hw {
  type hw
  card 0
  device 2
#  - Comment out "device 1" above and uncomment one of the below or create a
#    new "device N" line as appropriate for your sound card or 
#  device 2
#  device 4
}

# Control device (mixer, etc.) for the card
ctl.digital-hw {
  type hw
  card 0
}

# Direct software mixing plugin for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.dmix-analog {
  type dmix
  ipc_key 1234
  slave {
    pcm "analog-hw"
    period_time 0
    period_size 1024
    buffer_size 4096
    rate 48000
  } 
}

# Control device (mixer, etc.) for the card
ctl.dmix-analog {
  type hw
  card 0
}

# Direct software mixing plugin for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.dmix-digital {
  type dmix
  ipc_key 1235
  slave {
    pcm "digital-hw"
    period_time 0
    period_size 1024
    buffer_size 4096
    rate 48000
  } 
}

# Control device (mixer, etc.) for the card
ctl.dmix-digital {
  type hw
  card 0
}

```

Make sure that "IEC958 Playback AC97-SPSA" is turned down in alsamixer.

So there you go Jason_25 - SPDIF using the snd_intel8x0 drivers in Ubuntu on a nForce4 chipset. :cool: 

Anders

---

### Post by Jason_25 on 2006-06-11
How is the AC3 passthrough?  Digital output is no good to me if there is no Dolby digital 5.1, 2.0, etc...

BTW, I have tried that route before with no success.  I have other ALSA problems like delayed sound, microphone problems on half the pcs I work with...I hate ALSA with a passion.

---

### Post by andefeldt on 2006-06-12
Well, I haven't been able to get AC3 or DTS to work yet. However, I do think that this is a tweaking problem, which might be solved once I update my ALSA version. 

I have to agree with you Jason, a little any way. I'm also not the biggest ALSA fan. It seems to me like it is a lot better than OSS, far more configurable and so on, but it's very hard to get a good running installation of ALSA, and I don't get why the Linux OS' aren't build with a decent setup tool that can help you out, when you're having problems. Sound in Linux has always been one of the things I really don't understand.

Anders

---

### Post by ZenPsycho on 2006-06-29
[QUOTE=andefeldt]Well, well, well...

It works with snd_intel8x0!:D 

I haven't tried a dvd yet, but will do that later today. But now, I have sound in both my monitor speakers AND through my receiver via the SPDIF connection! SWEET!

I just used the .asoundrc file from 
[http://www.mythtv.org/wiki/index.php/DigitalSoundHowTo](http://www.mythtv.org/wiki/index.php/DigitalSoundHowTo) 
but changed the device from 1 to 2 in the following section:

```

pcm.digital-hw {
  type hw
  card 0
  device 2 # Used to be device 1
}

```

I'll report back later with my dvd-story :) 

Anyway, my entire .asoundrc file is:

[snipped]

Make sure that "IEC958 Playback AC97-SPSA" is turned down in alsamixer.

So there you go Jason_25 - SPDIF using the snd_intel8x0 drivers in Ubuntu on a nForce4 chipset. :cool: 

Anders[/QUOTE]


I am sorry to bump a 2 week old thread, but I wanted to add my report.
I had exactly the same problem with no sound coming through the SPDIF. I tried the above asound.conf with no success. That is, until I changed the following lines.

from
```

# configuration file, you once again have access to unmixed analog output using
# the "analog" device.
pcm.!default {
  type plug
## Uncomment the following to use "mixed-analog" by default
  slave.pcm "dmix-analog"
## Uncomment the following to use (unmixed) "digital" by default
#  slave.pcm "digital-hw"
## Uncomment the following to use "mixed-digital" by default
#  slave.pcm "dmix-digital"
}

```

I commented out the "dmix-analog" line and uncommented the "dmix-digital" line

```

# configuration file, you once again have access to unmixed analog output using
# the "analog" device.
pcm.!default {
  type plug
## Uncomment the following to use "mixed-analog" by default
#  slave.pcm "dmix-analog"
## Uncomment the following to use (unmixed) "digital" by default
#  slave.pcm "digital-hw"
## Uncomment the following to use "mixed-digital" by default
  slave.pcm "dmix-digital"
}

```

a little subtle, but that worked like a charm. I also made sure that it was at /etc/asound.conf , and that there was no .asoundrc file in my home directory that overides it. I am really pleased that worked and I didn't have to install some propriatary driver nonsense.

=D>

also, AC3 passthrough works perfectly. I had problems with xine-ui locking up in the settings, so I installed totem-xine instead. Full ubuntu integration, and no crashes. this makes me happy.

---

### Post by mark60008 on 2006-08-26
You say you got this working with alsa and dmix-digital.  Can you tell me if this was nf4 or nf2 board.  I currently trying to get this to work on a nf2 board.

By the way, alot of posts talk about the nvsound driver.  I am willing to take on a proprietary driver if it enables AC3 passthrough.  Can anyone tell me if they got AC3 passthrough working on nf2 board using the nvsound.

I currently got SPDIF working on a nf2 board using ALSA.  Like everyone else it is just stereo.  In my setting a I am using dmix-analog.

---

### Post by Craig Caldwell on 2006-12-20
Here is the .asoundrc file I used in my home directory to get Totem, Mplayer and VLC to work through my spdif. I tried so many different things before this and nothing worked. My alsa sliders can be any where and it still works.
It was this site that finally had some answers. [http://home.comcast.net/~alf_park/mythtv.html](http://home.comcast.net/~alf_park/mythtv.html)


```
pcm.nforce-hw {
   type hw
   card 0
}
 
pcm.!default {
   type plug
   slave.pcm "nforce"
}
 
pcm.nforce {
   type dmix
   ipc_key 1234
   slave {
     pcm "hw:0,2"
     period_time 0
     period_size 1024
     buffer_size 32768
     rate 48000
   }
}
 
ctl.nforce-hw {
   type hw
   card 0
}

```

---

### Post by tigrez on 2007-02-08
Ok, this worked for me (I've nforce3). 

I've some problem with freevo, but I've resolved forcing the output.
MPLAYER_AO_DEV      = 'alsa'

---

### Post by schlaef420 on 2007-03-13
> **PsyberOneZero said:**
> I had the same problem and with enough playing I found the settings that work, see attached thumbnails. They are the ALSA mixer panels, once these are set do not mess with the OSS settings it will mess it up (not badly but you have to change the settings in alsa back).

This method requires no additional software or compiling :)

To get all these go in to preferences and just check everything.
The most important settings are in the options tab set this exactly as shown as well as switches, and IEC958 Playback AC97-SPSA must be all the way down or muted.
As I'm writing this I've got (Fall Out Boy - Yule Shoot Your Eye Out) playing through my coax to my 5.1's


i was pulling my hair out until i ran this mixer, is was a dos like one but same settings. as you said, it was the IEC958 channel. thanks:guitar:

---

### Post by Draken_1337 on 2007-05-08
Hi!
I followed the last reply in this thread: [http://ubuntuforums.org/showthread.php?t=260272]("http://ubuntuforums.org/showthread.php?t=260272")
It worked! Just paste this in a terminal amixer sset 'IEC958 Playback AC97-SPSA' 0 
Thanks l4nkou!

---

### Post by lvkyle on 2008-07-04
been awhile since this thread was active, but just letting you know only way i got the sound working on mis k8n neo nforce 4 ultra was to selected duplicate front in switches tab, and select 2 channel mode "seems to sound better"

best advice is just to play around with it a lot. I was very close to giving up until i checked duplicate front and heart noise come from speakers and it worked. Also I have speakers plugged into black aux connection in back.

peace.

---

