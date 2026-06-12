---
title: "surround on Audigy (ca0106) .asoundrc file, (combine settings)"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by studo77 on 2007-10-22
After seeing  many posts on the Audigy SE card (ca0106) and troubles.
I have two working modes, but would like to combine them.

[http://ubuntuforums.org/showthread.php?p=3592393](http://ubuntuforums.org/showthread.php?p=3592393)

This is my original post, and am now moving it here. It seems to be the right place.

Now, here is the text from the original post:
Ok, here goes.

I have my Creative Audige SE card, chip ca0106

Sound is working pretty ok. But i have two sets of .asoundrc i would like to combine.

The first is where i get a mix of stereo to 5.1, and this i done by:
Found on [http://pastebin.ca/464795?srch=upmix]("http://pastebin.ca/464795?srch=upmix")
```
pcm.!dmix {
   type plug
   slave {
       pcm surround51
       channels 6
   }
}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 6
   route_policy duplicate
}
```

This upmixes my stereo, and lets 5.1 audio through. But, it does not let me play multiple audiosources.

This next one is found at
[http://ubuntuforums.org/showthread.php?t=285065]("http://ubuntuforums.org/showthread.php?t=285065")

Which i cut down to only analog:
```
# Override the default output used by ALSA.
# If you do not override the default, your default
# device is identical to the (unmixed) analog device
# shown below.  If you prefer mixed and/or digital
# output, uncomment the appropriate four lines below
# (only one slave.pcm line).
### comment out this entire section to use unmixed
pcm.!default {
  type plug
  slave.pcm "dmix-analog"

}

# Alias for analog output on the Audigy (hw:0,0)
# - This is identical to the device named "default"--which
# always exists and refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog"
# to access analog output on the Audigy
pcm.analog {
 type plug
 slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the Audigy card
ctl.analog {
 type hw
 card 0
}

# Alias for (rate-converted) mixed analog output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the dmix plugin
# (in this case 48000Hz)
pcm.mixed-analog {
 type plug
 slave.pcm "dmix-analog"
}

# Control device (mixer, etc.) for the Audigy card
ctl.mixed-analog {
 type hw
 card 0
}




# The following devices are not useful by themselves.  They
# require specific rates, channels, and formats.  Therefore,
# you probably do not want to use them directly.  Instead use
# of of the devices defined above.

# Alias for analog output on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.analog-hw {
 type hw
 card 0
 # The default value for device is 0, so no need to specify
}

# Control device (mixer, etc.) for the Audigy card
ctl.analog-hw {
 type hw
 card 0
}


# Direct software mixing plugin for analog output on
# the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format. You can edit the rate to use 
# another sampe rate like 9600
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

# Control device (mixer, etc.) for the Audigy card
ctl.dmix-analog {
 type hw
 card 0
}

```

This plays multiple audiosources, and lets 5.1 pass through. 

BUT it only plays stereo on front speakers.

I tried putting 
       pcm surround51
       channels 6

and
   slave.channels 6
   route_policy duplicate

Into the multiple working, where i thought they belonged, but then my soundcard gets locked up.
And letting all lines in the .asoundrc also gives troubles.

So how do i combine the two? Where to put in lines from the first, into the second to get a working .asoundrc?
And if i am very lucky, also explanation on why...

If i get the right answer i will post it on other posts on nearly the same issue, but the posts are dead, and long time since. (pops up on query)


Bonusinfo:
If i use a
```
pcm.ch51dup {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}
```

to distribute the sound, i get sound on all 5.1 speakers, but the sound is very choppy, and not listenable.

---

### Post by werewolfzx8 on 2007-11-15
This is the exact thing I've been trying to do.

I can either get multiple applications to play at once, OR I can get surround sound, but I can't get both at the same time.

This is a major problem for me, because I love my surround sound in games, but I need to be able to have multiple sound applications running at the same time.

I'm probably going to end up buying a different card. That M-Audio Revolution sounded pretty good, but right now I need to get THIS card to do what I want.

I messed around with the .asoundrc file all freakin night, and was still unable to get it working.

This is so frustrating :mad:

---

### Post by keithacole on 2007-11-23
just gonna chime in and say i have the same problems, i however have just been under the assumption in the past that getting multiple instances of audio was just broke under MANY MANY soundcards. i upgraded to gutsy, then went and upgraded my alsa to the latest version and my .asoundrc had to be removed for me to even get sound. but when i did get it it was only stereo through the front channels, and my left side has lower gain then the right side.but i get seemless stable sound, and multiple sounds at the same time. just need to get the surround working

---

### Post by Neo7891 on 2008-02-04
Got the same Problem with my Creative Audigy SE. Either 5.1 Sound or sound from multiple
Programs using dmixer. Both at a time doesn't work.
Hope a solution will be found soon.

---

### Post by darck on 2008-02-06
I've got same problem. Can make surround or dmix, but can't both at once. I hope that someone will find solution, because it'is major issue with cards using ca0106:

SB Live 24-bit (sb0410)
SB Audigy 7.1 (sb0570)
SB X-Fi Xtreme Audio (sb0790)

I've tried with ALSA Version 1.0.15.
below code which worked for integrated ALC650, but doesn't with ca0106:
```
###################################    via8235
pcm.via8235-dmix {
	type dmix
	ipc_key 1024
	slave {
		pcm "hw:1,1"
		channels 4
		period_time 0
		period_size 1024
		buffer_time 0
		buffer_size 4096
	}
}

pcm.via8235 {
	type plug
	slave.pcm "via8235-dmix"
	slave.channels 4
	route_policy duplicate  **#this line causes error for ca106**
}

ctl.via8235 {
	type hw
	card 1
}
```

---

### Post by darck on 2008-02-09
reported as bug at ALSA bugtracker. You can give some feedback over here:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3755](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3755)
bug id: 0003755
simple registration required

---

### Post by raashell on 2008-02-25
Thanks for help!  I was having a problem getting surround sound with my new Audigy SE card.  The bass and center speaker weren't working.  I pasted your script into a new file I named, .asoundrc , in my home directory, and rebooted.  Sounds great now.  :)  With Linux on the rise I hope Creative Labs will start offering Linux drivers.

Thanks again,

John

---

### Post by DkkD on 2008-05-12
Does anyone know how to solve this? Surround plus dmix on CA0106 (sb live!)?

Sorry for bringing back an old thread, but I was just going to start a new one with the same question. I have seen the problem on many forums, but nobody seems to have the solution. Thanks.

---

### Post by xjgnsdof on 2008-06-14
In Hardy, I can only get sound in either a) the front, front L, and front R speakers, or b) the front, rear L, and rear R speakers. Much like you, I can play sound in multiple apps. I'd much rather have surround, though.

---

### Post by crudolphy on 2008-06-14
If you are running Hardy with Pulse Audio, this has worked for me in both 32 bit and 64 bit versions.  Change /etc/pulse/default.pa as follows:

```

#!/usr/bin/pulseaudio -nF
#
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

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
[COLOR="Red"]load-module module-alsa-sink device="surround51" channels=6 sink_name=sur51[/COLOR]
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

[COLOR="Red"]### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif[/COLOR]

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

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input


```

The main line that gets added is:
> load-module module-alsa-sink device="surround51" channels=6 sink_name=sur51
and commenting out all the stuff with "Hal detect".

I get stereo playback with Exaile and Rhythmbox through all of my 5.1 speakers and when I pop in a surround sound DVD and play it in either Totem or VLC I get 5.1 playback.

I can't guarantee it will work for you but it worked for me.  I have SBLive 24 bit 7.1 card (ca0106) paired with a 5.1 speaker system.  Hardy 8.04 AMD64.  No issues with Flash, Divx, WMA, Quicktime, MPG, all play with sound either embedded in browser or in Totem with stereo mixed to the 5.1 speakers.  My tunes sound awesome to my ears.

---

### Post by Keneo on 2008-06-22
thank you so much!
I've been looking for this for a long time, I hoped pulseaudio would provide an easy way to do this, but never found it

thx so much

but do you really have to comment out the hal stuff?
it seems to mess up some gnome/X settings

I just left it there, and everything seems to work now...

---

### Post by crudolphy on 2008-06-22
On an earlier version I had to comment out the HAL stuff or I couldn't get the daemon to start, so I did with this version also.  I haven't tried it with the HAL stuff un-commented.  It doesn't seem to affect any other stuff on my setup.

Glad it worked for you:)

---

