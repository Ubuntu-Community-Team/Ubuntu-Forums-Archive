---
title: "Flash player (in FireFox) through JACK?"
date: 2008-06-14
forum: Multimedia Software
---

### Post by cha0s on 2008-06-14
I have Ubuntu Studio and I was wondering if there's some way to get the output from the flash plugin in Firefox going through JACK. I use the non-free plugin to run Flash, but I would be willing to try the free one in order to get something like this.

Any help appreciated, thanks.

---

### Post by reduzent on 2008-07-25
i was looking for that since weeks. i would be really happy to find a solution for that.

---

### Post by keithacole on 2008-08-12
i found this on the alsa wiki

put this in your .asoundrc and default sound should run through jack

```
pcm.!default {
    type plug
  slave { pcm "jack" }
}

pcm.jack {
  type jack
  playback_ports {
      0 alsa_pcm:playback_1
      1 alsa_pcm:playback_2
  }
  capture_ports {
      0 alsa_pcm:capture_1
      1 alsa_pcm:capture_2
  }
}

ctl.mixer0 {
  type hw
  card 1
}



```

however with this code,i still dont get the audio from flash to play, but it is atleast making an attempt because i can see the messages in jack about connection graph change.

so its one step closer, but not there yet

---

### Post by markbuntu on 2008-08-12
Go here, this will tell you how to get ANY application that plays through ALSA/pulseaudio to play into/through jack:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

see the jack section at the bottom.

---

### Post by lordmyth on 2008-09-03
I want to have my sound through jack too, but I'm getting the same problem when it comes to flash... I don't really want to start using pulseaudio again only to make it use jack :/

---

### Post by markbuntu on 2008-09-10
> **lordmyth said:**
> I want to have my sound through jack too, but I'm getting the same problem when it comes to flash... I don't really want to start using pulseaudio again only to make it use jack :/

Well, you may not have a lot of choice in that matter. Other solutions do not seem to be working so well at the moment. You could try removing pulseaudio and reverting to a strictly alsa setup. You could try OSS4 but I do not know about how that works with jack.

Admittedly, it would be a great thing if every sound application would work with every sound server but that is not the case so workarounds must be implemented. 

So far, pulseaudio seems to be the workaround that can connect the most of these applications with jack.

---

### Post by lordmyth on 2008-09-10
the thing is, i already have a strict alsa setup, but something in the way the flash plugin uses alsa makes the jack output plugin for alsa not work

i just connected the output from my on-board soundcard to my firewire audio device - works good enough for now

---

### Post by markbuntu on 2008-09-10
Yes, the flash 9 is very buggy as far as audio is concerned, even with libflashsupport. The initial flash10b seemed to have fixed that but is now very hard to find. The flash10b2 and flash10rc seem to have regressed from 10b in other areas. Fourtunately for me, I retained the initial 10b and that is what I use.

I had a strictly alsa setup for a while but decided that I would do some exploring and figure out this pulseaudio thing and get jack working with it. All I wanted to do was use jackrack to put some depth effects on my streaming audio from sofaspace in some easy way. So I did.

I think the biggest problem with pulseaudio in Ubuntu was that they left all the pulseaudio GUIs out of the install. No one could figure out how to use it. 

It is really great for multiple sound cards, it will let you choose which streams go where. One card or the other or both. It will sync the card playbacks together so they don't drift due to variations in their internal clock timing. It will connect to jack and give it a card to use while it uses the other one.

It can connect your non-jack apps with your jack apps in a simple and easy to use and control manner. 

You should really read my guide.

---

### Post by alecz20 on 2008-09-22
> **keithacole said:**
> i found this on the alsa wiki

put this in your .asoundrc and default sound should run through jack

```
pcm.!default {
    type plug
  slave { pcm "jack" }
}

pcm.jack {
  type jack
  playback_ports {
      0 alsa_pcm:playback_1
      1 alsa_pcm:playback_2
  }
  capture_ports {
      0 alsa_pcm:capture_1
      1 alsa_pcm:capture_2
  }
}

ctl.mixer0 {
  type hw
  card 1
}



```

however with this code,i still dont get the audio from flash to play, but it is atleast making an attempt because i can see the messages in jack about connection graph change.

so its one step closer, but not there yet

I am having trouble findinf this file ".asoundrc"

---

### Post by lordmyth on 2008-09-23
you simply make it?
do "gedit ~/.asoundrc"

---

### Post by eye208 on 2008-09-23
If the Jack plugin for ALSA doesn't work for you, there's another option: the loopback driver provided by ALSA. Here's how it works:

Enter this command to load the loopback driver:
```
sudo modprobe snd-aloop
```

Now enter this to find out which card number was assigned to it:
```
aplay -l
```

In most cases the loopback card will be "hw:1" unless you have more than one physical soundcard.

Now make the loopback card your default soundcard using the following instructions in your .asoundrc file:
```
pcm.!default {
    type hw
    card 1
    device 1
}
```

Configure Jack to capture from "hw:1,0" and output to "hw:0,0", then run Firefox. Now you have Flash audio in Jack.

---

### Post by lordmyth on 2008-09-23
this still doesn't work if you have a firewire device though

---

### Post by eye208 on 2008-09-23
> **lordmyth said:**
> this still doesn't work if you have a firewire device though
Jack doesn't work with firewire devices?

---

### Post by lordmyth on 2008-09-23
sure it does, but you can't select an alsa device as input and the firewire device as output...

---

### Post by eye208 on 2008-09-23
> **lordmyth said:**
> sure it does, but you can't select an alsa device as input and the firewire device as output...
I see. How about selecting firewire for both input and output and linking the ALSA device through NetJack instead?

---

### Post by lordmyth on 2008-09-23
:o

---

### Post by alecz20 on 2008-09-23
oh... okay... i tried that, and it didn't really work.

But I fixed my problem by changing the default sound-card for ALSA.

I have 2 cards: onboard, and Echoaudio GINA 3G, so the default is onboard, but jack uses ALSA, now I have all the sounds, but flash is on onboard.

I'm fine with this for now.

---

### Post by eye208 on 2008-09-24
Flash always uses "default". If you redefine it, Flash will use the other card as well.

---

### Post by lordmyth on 2008-09-24
did you try it yourself? with a non-alsa card?

---

### Post by eye208 on 2008-09-24
> **lordmyth said:**
> did you try it yourself? with a non-alsa card?
I don't have any non-ALSA cards.

---

### Post by lordmyth on 2008-09-24
well it just doesn't work, all other apps work, but somehow the flash alsa to jack output keeps disconnecting and reconnecting the whole time, with no sound

---

### Post by eye208 on 2008-09-24
I guess Flash and Jack are running at different sample rates, so you need a sample rate converter between them. Dmix or NetJack should do the trick.

---

### Post by markbuntu on 2008-09-24
Flash opening and closing the sound server connection is the same symptom in pulseaudio that was fixed with libflashsupport. I have no idea how you would fix that in alsa.

---

### Post by patrickballeux on 2008-10-05
Hi,  

Here is how I am able to use Flash + PulseAudio + Jack so Flash will play and record from JACK via PulseAudio.

I did a lot of trial and error, but finally found how to do it.

Requirement:
- PulseAudio (padevchoose make's it easy to visualize PuseAudio server)
- Jack and all that you need for jack.  JackControl is a must
- Alsa/Oss sound card that is well supported by jack.
- Flash 10 (Tried with Flash 9, but it crashed all the time)

Package installation:
sudo apt-get install puslseaudio gstreamer0.10-pulseaudio (and whatever other pulseaudio tool you may need)
sudo apt-get install jackd qjackctl (And whatever other jack tool...)
sudo apt-get install flashpplugin-nonfree
And, download pulseaudio-module-jack for your architecture from that site and install: 
X86   : [http://packages.debian.org/sid/i386/pulseaudio-module-jack/download](http://packages.debian.org/sid/i386/pulseaudio-module-jack/download)
AMD64 : [http://packages.debian.org/sid/amd64/pulseaudio-module-jack/download](http://packages.debian.org/sid/amd64/pulseaudio-module-jack/download)

Now everything should be ready on your computer.  Now let's do some configuration...

In Preferences-Sound, set your sound server for output and capture to PulseAudio.   Run gstreamer-properties, and validate that everything is set to PulseAudio.  

Alsa configuration:
**~/.asoundrc**
# ALSA library configuration file
# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/YOUR_USER/.asoundrc.asoundconf>


**~/.adoundrc.adoundconf**
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
pcm.!default { type pulse }
ctl.!default { type pulse }

These two files were generated by the utility: Default Sound Card in Prefenreces (need to install: sudo apt-get install asoundconf-gtk)

You are simply telling the the default Alsa sound card is PulseAudio...

Then, configure your PulseAudio server for a particular setup.

In the file **~/.pulse/default.pa ** (If it does not exists, create it...)

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
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink device=hw:0,0
load-module module-jack-sink
load-module module-jack-source
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif

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

This will simply load the jack plugins and not load any ALSA driver.  You'll end-up with a PulseAudio that must rely on jack to capture and play audio.

Now Jack configuration...

Open Jack Control, and create a setup that captures and output to your alsa sound card (or OSS, should work...).  In the options ,make it auto-start and when you jack setup is done, everything should work for the sound...

Now Flash,  Remember that you installed from the repository, this will be Flash 9.  Now go to Adobe site, download the Flash plugin version 10 ([http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)).  AMD64 user, the easy way to do this it to simply open the archive, and overite the plugin in /usr/lib/flashplugin-nonfree/libflashplayer.so .  By overwriting, you will avoid playing with the plugin wrapper.  x86 user, you can do the same actually...

Ok, now, we are ready...  Reboot your computer to be sure that we are ok...

Then, when you'll login, you should hear the login sound, and try playing a video in Totem...  Open padevchooser (will show as an icon in the notification area), and show the volume control to validate that All you have as devives are Jack_Out and Jack_In.  You can stop the video, open the Jack Control, and click "Channels", you should see System and PulseAudio as sources and sinks on both side...  It means that your setup should work...

Make sure that the PulseAudio sink is connected to the System output and that the System capture is connected to the PulseAudio Source...  

Now start Firefox, go to any website that as flash videos (Youtube?)...  Play one, you should see that Flash is connected in PulseAudio, you should hear sound and if you disconnect PuseAudio Sink from System Output, you won't hear any sound.

Do the same for recording (right click on the flash, and open properties for the microphone)..  You should be able to record from a jack source...

If everything worked as it did for me, then you can now use Jack with Flash to broadcast your own unique show!  :guitar:

(Try Creox... quite fun!).

As I found out, Flash, even if we specify that the default input is jack instead of Alsa, will pick the first device found in the list.  And generally, this is the alsa (oss) sound card.  With the custom configuration, we do not load any hardware in PulseAudio and only the jack modules.  All the hardware stuff will be handle by jack.  

Of course, for those application that cannot support Jack or PulseAudio, you will be stuck.  But, that's the small price to pay to have full control of the audio...  And is you really need the Alsa access, shutdown jack the time of using/playing with your software...

It took me a few hours to find the right config, but I'm glad I did.  Everything is in the repository except for the pulseaudio-jack modules.  

Done on Hardy AMD64, latest updates.

Have fun!
(Have you tried WebcamStudio for GNU/Linux on Sourceforge.net)

---

### Post by markbuntu on 2008-10-05
There is a way to just have the pulse-jack sink and server connected only when you use jack so when you are not using jack everything acts normally. You have made a good and simple solution so kudos to you

I have written instructions for making the pulse-jack sink/source only when jack is running here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by patrickballeux on 2008-10-05
Part of the inspiration was from your own work also...

I made a little modification on my setup to set PulseAudio to connect with default or only to jack by using scripts in the startup and shutdown script of Jack Control...

load_jack
```

#load pulseaudio jack modules
#!/bin/bash
pulseaudio -k
sleep 1
pulseaudio -F /home/pballeux/.pulse/jackd.pa -n -D

```

unload_jack
```

#load pulseaudio as default
#!/bin/bash
killall jackd
pulseaudio -k
sleep 1
pulseaudio -D

```


Now, instead of using "default.pa", I renamed the file to "jackd.pa" as proposed in your thread.  This way, when jack is not running, you are setup as default.  But as soon as you start jack (Jack control), you rely on jack for hardare and puseaudio is just an abstract layer that will use jack for sink and source.  

So, this way, Flash player will play/record in jack and any other application that is compatible with jack or pulseaudio.

---

### Post by patrickballeux on 2008-10-05
Ok, to make things easier, I created a small debian package.

Note that you still need to download the pulseaudio-modules-jack to be able to install that package.

See the README.txt in /usr/share/pulseaudioandjack/ for final setup so it will work in Jack Control...

Hope it will help you...

---

### Post by markbuntu on 2008-10-06
Easier is always better, thank you for getting this to the next step.:guitar:

---

