---
title: "Pulseaudio configuration utility"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by nstamoul on 2008-04-18
Hallo there.

I 've been seeing a lot of people complain about the absence of a configuration utility for pulseaudio so I took the time to make one myself.It cat do as simple as select the output of your choice as far as sound card and the number of speakers is concerned.Should you have more than one sound cards you could combine these into one virtual sink.

Of course these features are not my addition to pulseaudio,I just provide a GUI for them.

I tried to make the program as generic as possible as far as the sound cards are concerned.I would appreciate some beta testing.Up to now it has worked wherever I tried it (works solid on Audigy,CA0106,Intel laptop card).

So if it does not work for your setup,please give a simple output of the following:
[LIST]
[*]aplay -l
[*]arecord -l
[*]~/.pulse/default.pa
[*]output of pulseaudio when you run it from a terminal.
[/LIST]

---

### Post by nstamoul on 2008-04-22
Anybody tried it out yet?

Success stories also welcome ;) .

Give me some beta testing please,the program does not bite :D

---

### Post by onno on 2008-04-25
nstamoul, it works like a charm! I was finally able to get my CA0106 card (that's a Soundblaster Live for the rest of the world) up and running again under Ubuntu 8.04 (Hardy Heron).

Thanks a lot!

Onno

---

### Post by pborman on 2008-04-25
Great! works here too. I had sound from exaile and mplayer, but not totem or the "mouse over" in nautilus. All working fine now.
Thanks,

Phil

---

### Post by rubinstein on 2008-04-26
Thanks nstamoul!

Your program was my salvation for my sblive card on 8.04, as nothing I had tried previously seemed to work.

---

### Post by nstamoul on 2008-04-28
Glad to hear it addresses part of the problem :) .

Has anybody tried recording?It should work,but I would be very interested in confirming that.

Onno I happen to have the same card on one of my PCs.If you have a problem with the recording,pm me,there seems to be a quite strange solution for this card,alsa related.

So waiting for your recording results :D

---

### Post by Quake on 2008-04-28
I find it quite "stupid" (sorry for the harsh word) for Ubuntu to release a LTS version without fully releasing the PulseAudio configuration and testing it.

A LOT of users have surround speakers and with alsa, all we had to do was go to the alsamixer utility and enable it, easy!

---

### Post by nstamoul on 2008-04-28
First of all I am not an official developer or maintainer or whatever of ubuntu or of pulseaudio.I just happened to write this script which people might find useful.

On topic now,this is not always the case for many many sound cards.Do not confuse alsa with pulseaudio.Pulseaudio does not substitute alsa or oss or jack.Think of it as an abstraction layer.Pulseaudio's "autodetection" (hal) does not always work correctly,even with correct alsa configuration.

Apart from that it is not mandatory to use the script,it is just a GUI.All of the configurations can be written to default.pa, as long as you know what to write.

---

### Post by Quake on 2008-04-28
Hey, I'm not against you! Just a bit pissed off that something is broken when it wasn't in 7.10.

Btw, **Thanks** for the utility! I can't really test it since I'm running the live CD but when I'll install it, I'll test it.

---

### Post by IgnacioMiller on 2008-04-30
It worked with no problems for me, but did not solve my Sounblaster Live! 24-bit soundcard's problems. Still no sound. =(

---

### Post by nstamoul on 2008-04-30
Some details about your sound problems please :)

---

### Post by whi8esauce on 2008-05-01
thankkkkkkkkkkkkkkkk youuuuuuuuuuuuuuuu soooooooooooooooooo muuuuuuuucccccccccccccccccchhhhhhhhhhhhh!

you made my day! :KS

btw: i used it to configure my creative 5.1 sound blaster card with a 5.1 speaker system. and it worked like a charm!
> **nstamoul said:**
> Hallo there.

I 've been seeing a lot of people complaining about the absence of a configuration utility for pulseaudio so I took the time to make one myself.It cat do as simple as select the output of your choice as far as sound card and the number of speakers is concerned.Should you have more than one sound cards you could combine these into one virtual sink.

Of course these features are not my addition to pulseaudio,I just provide a GUI for them.

I tried to make the program as generic as possible as far as the sound cards are concerned.I would appreciate some beta testing.Up to now it has worked wherever I tried it (works solid on Audigy,CA0106,Intel laptop card).

So if it does not work for your setup,please give a simple output of the following:
[LIST]
[*]aplay -l
[*]arecord -l
[*]~/.pulse/default.pa
[*]output of pulseaudio when you run it from a terminal.
[/LIST]

---

### Post by whitethorn on 2008-05-02
I tried it out I have a USB 24bit Live creative card Modell #  SB0490  and it worked for me.  I let the program run and I rebooted and it works great so far. (haven't tested it with skype or mpd yet). Thx

---

### Post by chrisneedshelp on 2008-05-05
THANK YOU THANK YOU THANK YOU!!!!!!

I am a complete nube, 3rd day on linux/ubuntu, spent all three days trying to rescue my xp drive as i royaly screwed things up during installs, now after all day today i'm finally up dual boot, and what did i find?  no sound on ubuntu!!!!!!   and then all my reading around shows that everyone has this problem!

well, your thing works great!  one thing of note though, if i did the merge of both card(i have sb audigy 4 and onboard) it would not work, period...so i undid that and it works beautifully...

I wonder if that could be because i have disabled the onboard in windows via hardware mngr?  idk enough about linux to know if that could effect it, but whatever, it works..

Thank you!

---

### Post by nstamoul on 2008-05-05
Tnx for the report.

Please try using both cards again and paste the output of:
```
cat ~/.pulse/default.pa
```
and paste it here.Then revert to the previous setup to get your sound working again.

---

### Post by l0b0 on 2008-05-05
> **nstamoul said:**
> So if it does not work for your setup,please give a simple output of the following:
[LIST]
[*]aplay -l
[*]arecord -l
[*]~/.pulse/default.pa
[*]output of pulseaudio when you run it from a terminal.[/LIST]

Hello, and thanks for this utility! Here's to it (or something similar) making it into the standard Ubuntu distro - It's sorely needed.

Now, over to the problems: I've got an onboard audio card which outputs an optical signal via S/PDIF (aka. IEC958) to a 5.1 surround amplifier. I've got it sort of working in the sense that I get digital output, but there's still choppy sound, so I tried your utility to see if it fixed the problem. But after running it I get no sound. Some relevant output:

```
$ diff ~/.pulse/default.pa /etc/pulse/default.pa
37,38d36
< load-module module-alsa-sink device=surround51:Intel sink_name=Intel
< load-module module-alsa-source device=hw:Intel
42c40
< #load-module module-hal-detect
---
> load-module module-hal-detect
107c106,107
< load-module module-combine sink_name=combined master= slaves=Intel,
---
> load-module module-alsa-sink device=pulseaudio rate=48000 channels=6 sink_name=alsa_surround mmap=0
> set-default-sink alsa_surround

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 1: U0x46d0x8ce [USB Device 0x46d:0x8ce], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by nstamoul on 2008-05-05
Try changing 

load-module module-alsa-sink device=surround51:Intel sink_name=Intel
to
load-module module-alsa-sink device=surround51:1 sink_name=Intel

Restart pulseaudio and report back :)

---

### Post by derichoi on 2008-05-08
> **nstamoul said:**
> Hallo there.

I 've been seeing a lot of people complaining about the absence of a configuration utility for pulseaudio so I took the time to make one myself.It cat do as simple as select the output of your choice as far as sound card and the number of speakers is concerned.Should you have more than one sound cards you could combine these into one virtual sink.

Of course these features are not my addition to pulseaudio,I just provide a GUI for them.

I tried to make the program as generic as possible as far as the sound cards are concerned.I would appreciate some beta testing.Up to now it has worked wherever I tried it (works solid on Audigy,CA0106,Intel laptop card).

So if it does not work for your setup,please give a simple output of the following:
[LIST]
[*]aplay -l
[*]arecord -l
[*]~/.pulse/default.pa
[*]output of pulseaudio when you run it from a terminal.
[/LIST]

I'm new in Ubuntu, can you explain to me in details please? where should I use the above command? In Terminal? My Creative Sound Blaster live 2.4 still no sound at all. I have put a command in Terminal to test my speaker 5.1 surround, it works! Anyway when I play MP3, no sound at all... What is the problem?  How to use the attachment that you provided?

---

### Post by nstamoul on 2008-05-08
The attachment provided is the equivalent of a setup.exe in windows.Just double click on it and it will install the program.
Then all you have to do is run the program and make the correct configuration.

IF you encounter a problem put the commands into a terminal and paste the output of each command here so we can help you.

For any further question don't hesitate to ask ;)

---

### Post by MemoryDump on 2008-05-08
does this script change the settings for all users or only the current logged one? I'd love to make this settings apply to all the users.

great script btw!! thanks!

---

### Post by nstamoul on 2008-05-08
In order to make your configuration global all you have to do is copy the users configuration to the /etc/pulse directory.So a simple ```
cp ~/.pulse/default.pa /etc/pulse/default.pa
``` would be enough ;)

---

### Post by ShinjiLeery on 2008-05-08
With pulseaudio when i listen a mp3 with Rhythmbox there's always a high cpu usate of the deamon pulseaudio (about 15%). There's any solution of this problem?

---

### Post by nstamoul on 2008-05-08
This is kinda inevitable since pulseaudio is a sound server with many more features than plain alsa or oss or anything else.

One workaround would be to nice it (google it) but I would not recommend that.

---

### Post by ShinjiLeery on 2008-05-09
> **nstamoul said:**
> This is kinda inevitable since pulseaudio is a sound server with many more features than plain alsa or oss or anything else.

One workaround would be to nice it (google it) but I would not recommend that.

Inevitable? 15% of cpu only for sound? I don't think is a step foward...

---

### Post by nstamoul on 2008-05-12
Well great features come at a cost.Anyway I don't think this is something modern processors can't handle.

---

### Post by MemoryDump on 2008-05-15
I'm having some probs getting Pulse working with my 2 sound cards.
Please see this post for further details as I don't want to double-post.
[http://ubuntuforums.org/showthread.php?p=4965992#post4965992](http://ubuntuforums.org/showthread.php?p=4965992#post4965992)
thanks :D
-MD

---

### Post by nstamoul on 2008-05-15
You could give it a try with my "program".

Go to advanced configuration.Select both cards.DONT combine them since there seems to be a problem with the current version of pulseaudio and module-combine.Then go to padevchooser->volume control->input devices and  select the one you want to use as the default.

Good luck.Report back with the results (hopefully positive)

---

### Post by MemoryDump on 2008-05-16
> **nstamoul said:**
> You could give it a try with my "program".

Go to advanced configuration.Select both cards.DONT combine them since there seems to be a problem with the current version of pulseaudio and module-combine.Then go to padevchooser->volume control->input devices and  select the one you want to use as the default.

Good luck.Report back with the results (hopefully positive)

ahh.. this makes sense.. I tried using your program before, however I ended losing my sound for Wine so I went back to my original config. 
Anyways, I just tried as you suggested and now I can see both my sound devices listed in the Pulse Manager! woohoo!! :guitar:
now my question is: What do I set my Sound properties to for Audio Conference so I can use my headset as described in my other post?

(not at home atm so I'm connected to my pc via VNC! ;))

thanks for the help :P
-MD

---

### Post by nstamoul on 2008-05-16
My guess is to set it to pulseaudio and then define the default source from padevchooser to the one you want.

As always report back :)

---

### Post by gaussfan on 2008-05-16
Hey - thanks for putting this together!  Just installed Hardy Heron using wubi, and this hasn't worked for me yet, so here are the details you mention in your first post.  Maybe there will be something obvious in here to you?  Thanks for any help . . .

**From aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


**From arecord -l**
**** List of CAPTURE Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 1: Intel ICH - MIC ADC [Intel ICH5 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 2: Intel ICH - MIC2 ADC [Intel ICH5 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 3: Intel ICH - ADC2 [Intel ICH5 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


**Here is the whole file default.pa:**
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
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
load-module module-alsa-sink device=front:Live sink_name=Live
load-module module-alsa-source device=hw:Live

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
#load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
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
#set-default-source input
load-module module-combine sink_name=combined master= slaves=Live,


As far as running pulseaudio, when I type that in a terminal, I get nothing - just the next prompt.  Sorry, pretty much a complete newbie.  Please let me know if I can provide any other information that'd be helpful.

Thanks again,
Mike

---

### Post by nstamoul on 2008-05-16
I can tell you have two soundcards but only need one for your configuration.It would be better to go into imple rather than advanced configuration and select the card you wish to use.

Also what kind of output are you using for your speaker system?

---

### Post by gaussfan on 2008-05-16
> **nstamoul said:**
> I can tell you have two soundcards but only need one for your configuration.It would be better to go into imple rather than advanced configuration and select the card you wish to use.

Also what kind of output are you using for your speaker system?

Thanks for such a quick reply!  I did try the simple setup first, and when that didn't work, went through the advanced.  I've just gone back through the simple, choosing the Live soundcard.

I have just a simple 2.1 setup - Altec Lansing.

---

### Post by gaussfan on 2008-05-17
Latest update - after the latest reboot, I hear the Ubuntu login & logout sounds, but I still can't hear sound when playing videos or music files online (youtube, etc.)

---

### Post by nstamoul on 2008-05-17
Have you installed the pulseaudio device chooser applet?It will help us a great deal with some debuging.So:```
sudo apt-get install padevchooser
```
Then fire it up by hitting alt+f2 and typing ```
padevchooser
```

Then click on the applet located on the uper right corner of your screen (the one that looks like a jack) and hit volume control.With this open try playing some music and a sink should show up.

Report back so I know if we are on the right track on solving your problem :)

---

### Post by gaussfan on 2008-05-18
OK, it's installed, but when I play a video, nothing shows up under the Playback tab of the app.  Just "No Streams Available".  I tried showing all streams instead of just applications, and still nothing.  Does that tell us anything?

Thanks,
Mike

---

### Post by gaussfan on 2008-05-18
This may just be a flash thing now.  I can get sound from music files & video on my PC, just not online.  (Not that that tells me what to do, but it at least gives a direction to the hunt!)

---

### Post by nstamoul on 2008-05-18
Yep this is definitely a flash issue.Might I suggest installing libflashsupport.It **might** solve your problem

```
sudo apt-get install libflashsupport
```

---

### Post by gaussfan on 2008-05-18
Issue solved - thanks for all your help!

---

### Post by nstamoul on 2008-05-18
Glad to help :)

---

### Post by diex on 2008-05-19
Hi nstamoul!

The script that you made is very impressive for me! After upgrading from 7.10 to 8.04 there was no sound at all, however I used the pulsaudio and here I can get all the sounds. 

In the begining your script showed me that I have three soundcards on my system.I choosed live ( cause I am using Sound Blaster Live!) and after that I also choosed 4.1 speaker configuration. 

In the end I can only get sound from my front left and right speakers. No matter what I do, I couldnt get sound from rear speakers. I am searching for this issue like a month and I ended up with nothing. Maybe I am not a good researcher:D

If you have any suggestions I would like to hear them,

Thanks

Hasan

---

### Post by nstamoul on 2008-05-19
One thing you should try first is to run alsamixer from a terminal.Then you should look for a mixer named surround or something like that and/or anything relevant to this and unmute/maximize them

I suspect this is clearly alsa related.If this does not work there are a couple of things we could try.

---

### Post by diex on 2008-05-19
even I tried like 30 times with alsa to change default configurations nothing happened. Still I don't have sound from rear speakers. It started to  piss me of however I wont give up and if I find a solution I'll write it here

---

### Post by nstamoul on 2008-05-20
Please post your ~/.pulse/default.pa here so I can suggesgt a modification

---

### Post by p4inkiller on 2008-05-20
Hello mate. A lot of thanks for your work.
I've got 5.1 speakers. Finnally, I could make the rear ones to get working, and they sound OK now. I've configured the sound with alsamixer and it sounds well.
But the center speaker doesn't work. so, ahead -> left and right, behind -> left and right, and the surround box working, but the center speaker (wich I've got ahead), doesn't work.
It does work in XP.

Could you help me? 
Here is pa file:


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
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
load-module module-alsa-sink device=surround51:CK804 sink_name=CK804
load-module module-alsa-source device=hw:CK804

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
#load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
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
#set-default-source input

---

### Post by nstamoul on 2008-05-20
I would suggest you look at alsamixer one more time.There usually is a seperate center output sink so be sure to unmute it and give it some volume.

Your pulseaudio configuration seems to be correct.One thing I could suggest is to append the phrase channels=6 to the sink line so it reads :

```
load-module module-alsa-sink device=surround51:CK804 sink_name=CK804 channels=6
```

So give that a try and see what happens.

---

### Post by p4inkiller on 2008-05-20
Thanks for answering that fast. I added it and restarted the computer.
Center sink is unmuted, and I've already tried changing volume, but it has no effect. It's max now, but it doesn't work.
Should I try anything else? Thanks

---

### Post by nstamoul on 2008-05-20
Then this should be some kind of switch.

So first install the padevchooser utility whick should help us debug.Launch the utility by hitting alt+f2 and running ```
padevchooser
```
Next find a 5.1 source file such as a movie,start the playback and go to padevchooser (upper right corner) and hit volume merer (playack).Do you see any output concerning the center speaker?

Report back :)

---

### Post by p4inkiller on 2008-05-20
Yes, there's output concerning it, the same as the rest. I'm playing a music concert dvd and every output is moving. So does front center, but I hear no sound from it.

---

### Post by nstamoul on 2008-05-20
Ok,I guess this is totally alsa related since you get the output for center.Does this also occur when you e.g. preview something with mouse over or is it a specific player?

Try this:Go into gnome-volume-control,from file select change device and find the alsa mixer for your sound card.Then go to edit->preferences and select everything.A number of tabs should show up.Try finding something relevant to the center speaker.This should probably be a switch ;)

---

### Post by p4inkiller on 2008-05-20
it happens all the time. rythmbox, amarok, and totem movie player is what I've tried so far.
there's a switch called CENTER, it's unmuted and at max volume. playing with the others (master right, left, surround...) actually change the correct speaker (according to the switch I modify) volume, but CENTER does nothing.

---

### Post by nstamoul on 2008-05-20
Stupid question.If you kill pulseaudio (pulseaudio -k) and play back a 5.1 source file do you have any output?

And there is nothing under the swiches tab?Hmmmmmmm.....

Please post your soundcard model and I 'll try to find a pc with the same kind,see if I can do something else.

---

### Post by p4inkiller on 2008-05-20
nope, no sound anywhere now. 

The soundcard I'm using is the one that comes with my motherboard.
My motherboard is MSI K8N NEO4F
[http://asia.msi.com.tw/index.php?func=proddesc&prod_no=177&maincat_no=1&cat2_no=&cat3_no=](http://asia.msi.com.tw/index.php?func=proddesc&prod_no=177&maincat_no=1&cat2_no=&cat3_no=)
Audio (i took this from that link)

&#8226; 7.1 channel audio codec RealTek ALC850.
- Compliance with AC97 v2.3 Spec.
- Meet PC2001 audio performance requirement.

Thank you for everything. I'll keep reading the post.

---

### Post by nstamoul on 2008-05-20
A quick search through the forum revealed several other users with the same problem.

You could try [this]("http://ubuntuforums.org/showpost.php?p=1397018&postcount=10") 

Anyways I will look around for a solution and if I find one I ll post it here :)

---

### Post by p4inkiller on 2008-05-20
solved! 
turned out, in gnome-volume center, that the option SURROUND JACK MODE was SHARED, tried it INDEPENDENT, and now the center speaker is working. 
However, I have the feeling that the rest of the speakers sound "better" if that option is shared, and the surround box sounds stronger.
I'll try setting the speakers in alsa mixer and see what I get. 

Thank you for everything. Bye

---

### Post by nstamoul on 2008-05-20
This goes for everyone,ALWAYS set the volume at about 80% max from alsamixer.You will have much better sound quality.You can then regulate the volume through pulse.

Glad you worked it out :guitar:

---

### Post by ElEdwards on 2008-05-21
Maybe trying your method will save the remainder of my hair. ;)

I have a Compaq Presario 2170us laptop.  My soundcard is reported by **lspci** as:
```
Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
```
I do commercial voice-overs with it and in Ubuntu 7.10, recording in Audacity was flawless.... but in 8.04, my recording has been so choppy and/or skippy that I had to switch back to WinXP to make my recordings.  Hopefully I can configure Pulse your way and return to using only Ubuntu and Audacity. :)

I'll let you know.

Thanks!
El

---

### Post by nstamoul on 2008-05-22
I don't think my utility could help you with this problem.

What you are describing is a known bug (and an anoying one too)

[https://bugs.launchpad.net/paconfig/+bug/190754](https://bugs.launchpad.net/paconfig/+bug/190754)

You could try switching back to alsa used in previous versions of ubuntu by killing pulseaudio ( pulseaudio -k will do the trick ) or you could try some of the solutions mentioned in the link above.Good luck with it,I hope it helps you get back to ubuntu full time ;)

---

### Post by FabioTursi on 2008-05-22
Hello!
I have a problem with my old (but always great) Soundblaster Live! Platinum. I have an integrated sound card, too, but none of them seems to work (of course, I'd like to have the SB working).

Here's what comes from play and record. If I try to run ~/.pulse/default.pa, it says "Permission denied". If i run pulseaudio (always from terminal), nothing happens.

**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: ICH5 [Intel ICH5], dispositivo 0: Intel ICH [Intel ICH5]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: ICH5 [Intel ICH5], dispositivo 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: Live [SBLive! Platinum [CT4760P]], dispositivo 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Sottoperiferiche: 32/32
  Sottoperiferica #0: subdevice #0
  Sottoperiferica #1: subdevice #1
  Sottoperiferica #2: subdevice #2
  Sottoperiferica #3: subdevice #3
  Sottoperiferica #4: subdevice #4
  Sottoperiferica #5: subdevice #5
  Sottoperiferica #6: subdevice #6
  Sottoperiferica #7: subdevice #7
  Sottoperiferica #8: subdevice #8
  Sottoperiferica #9: subdevice #9
  Sottoperiferica #10: subdevice #10
  Sottoperiferica #11: subdevice #11
  Sottoperiferica #12: subdevice #12
  Sottoperiferica #13: subdevice #13
  Sottoperiferica #14: subdevice #14
  Sottoperiferica #15: subdevice #15
  Sottoperiferica #16: subdevice #16
  Sottoperiferica #17: subdevice #17
  Sottoperiferica #18: subdevice #18
  Sottoperiferica #19: subdevice #19
  Sottoperiferica #20: subdevice #20
  Sottoperiferica #21: subdevice #21
  Sottoperiferica #22: subdevice #22
  Sottoperiferica #23: subdevice #23
  Sottoperiferica #24: subdevice #24
  Sottoperiferica #25: subdevice #25
  Sottoperiferica #26: subdevice #26
  Sottoperiferica #27: subdevice #27
  Sottoperiferica #28: subdevice #28
  Sottoperiferica #29: subdevice #29
  Sottoperiferica #30: subdevice #30
  Sottoperiferica #31: subdevice #31
scheda 1: Live [SBLive! Platinum [CT4760P]], dispositivo 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Sottoperiferiche: 8/8
  Sottoperiferica #0: subdevice #0
  Sottoperiferica #1: subdevice #1
  Sottoperiferica #2: subdevice #2
  Sottoperiferica #3: subdevice #3
  Sottoperiferica #4: subdevice #4
  Sottoperiferica #5: subdevice #5
  Sottoperiferica #6: subdevice #6
  Sottoperiferica #7: subdevice #7
scheda 1: Live [SBLive! Platinum [CT4760P]], dispositivo 3: emu10k1 [Multichannel Playback]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0




**** Lista di CAPTURE dispositivi hardware ****
scheda 0: ICH5 [Intel ICH5], dispositivo 0: Intel ICH [Intel ICH5]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: ICH5 [Intel ICH5], dispositivo 1: Intel ICH - MIC ADC [Intel ICH5 - MIC ADC]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: ICH5 [Intel ICH5], dispositivo 2: Intel ICH - MIC2 ADC [Intel ICH5 - MIC2 ADC]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: ICH5 [Intel ICH5], dispositivo 3: Intel ICH - ADC2 [Intel ICH5 - ADC2]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: Live [SBLive! Platinum [CT4760P]], dispositivo 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: Live [SBLive! Platinum [CT4760P]], dispositivo 1: emu10k1 mic [Mic Capture]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: Live [SBLive! Platinum [CT4760P]], dispositivo 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

Thank you!!!

---

### Post by nstamoul on 2008-05-22
Hallo there FabioTursi  

I didn't quite understand what ou meant by running default.pa.It is not an executable,it is a config file.

If you mean you are trying to "cat" the file then it means you don't have permission to view and hence use the file.So I would suggest you first change the ownership of the file to your current user.

Also what kind of physical connection do you use to connect to the speakers.I mean analog,digital,optical etc.

---

### Post by chief1972 on 2008-05-22
nstamoul, thanx worked just fine now i can jam alice in chains!

---

### Post by chiefci on 2008-05-24
I tested it, this works great.
Now, I can simple switch between my two sound cards
and change speakers.
Thank's again for this great tool.

Chief

PS. Now I see there is another chief that's funny

---

### Post by gapce on 2008-05-24
Thanks nstamoul!

You have solved my sound problems in hardy.
I got your reference from onno in this forum.
Thanks again, now i just want to solve my printer solution.
God bless you.

tegap

---

### Post by hugh_h_chen on 2008-05-27
> **nstamoul said:**
> I would suggest you look at alsamixer one more time.There usually is a seperate center output sink so be sure to unmute it and give it some volume.

Your pulseaudio configuration seems to be correct.One thing I could suggest is to append the phrase channels=6 to the sink line so it reads :

```
load-module module-alsa-sink device=surround51:CK804 sink_name=CK804 channels=6
```

So give that a try and see what happens.

I would like to thank you for your solution and your maintenance of this thread. To be honest, I tried almost every thread in this forum to fix my 5.1 surround without perfect fix. In fact, I installed the NVmixer as introduced by some thread there (I am very thankful also to that thread owner), but after an update of the system, the hacked closed source nvmixer went missing and I hated to re-install it. From your thread, i found out that all functionality of 5.1 surround is there with alsamixer and pulseaudio, they are just up there for us to use/enable!

you suggestion of adding "channels=6" is very crucial, as it can't be changed in the alsamixer brought out by Terminal. After this change, WOW, my 5.1 surround is back again! Of course, Firefox flash sound is missing, well your flashsupport suggest just fix that like a charm, whereas, some other thread i used to use calls for change of some config file of firefox, which i think is not as easy and permanent as this one. 

Well, thank you again for your kind support/help to all of us. I think this thread needs to get more attention by Ubuntu ussers.

Only draw back, CPU usage, totem and pulseaudio can take 40% of my CPU usage.....my poor AMD Athlon ...

---

### Post by bve on 2008-05-28
> **Quake said:**
> Hey, I'm not against you! Just a bit pissed off that something is broken when it wasn't in 7.10.

Btw, **Thanks** for the utility! I can't really test it since I'm running the live CD but when I'll install it, I'll test it.

Dude I could relate if you spent $400 bucks for a license, but seriously it's FREE software - almost completely coded by volunteers, Ubuntu is pretty solid for the most part and support is a lot better than most commercial/proprietary software.

---

### Post by nstamoul on 2008-05-28
First of all I would like to thank all of you for your kind words :)

About the channels=X parameter maybe I ought to make this part of the configuration made by the script.It is not necessary on most of the sound cards but it is for some.Maybe I will write a revised script some time later with some more options.And we probably should bump this thread up to the non-archive section of the forum,if that is possible.

For the time being I have a serious lack of time as I have to graduate from university.Last semester,cross your finger :D

---

### Post by cacus on 2008-05-30
Hi nstamoul!, it worked for my two weeks ago too :) great work!
But, I'm here to ask you for something else.
Hope it don't bother you.
Could you please send me your paconfig source code?, obviously if it's under GPL or something like that.
I don't want to copy your job, just want to take a look at the parameters and the libs you used because I want to make some GUI for the LADSPA EQ plugin to make an utility to control a system wide equalizer with presets, custom presets, etc under Ubuntu, but, I really don't know very well where to start at.
Primary I would like to try with Glade and Python.
Greetings.

cacus

---

### Post by nstamoul on 2008-05-30
Of course you are wilcome to see the "source code" of paconfig.But I doubt it will help you since you want to code in python.

Paconfig is written in bash scripting language and uses a simple module called  zenity which can generate a number of simple menus in gtk.I used bash because it is simply the best choice when it comes to text manipulation,since it has powerful tools like sed and grep.

You can review the source code located at **/usr/bin/paconfig** in your system.

Good luck with your project,I look forward to seeing the results :)

---

### Post by DanielBerry on 2008-05-31
Hi Nstamoul

am having some issues with my sound
i am running mythbuntu 8.04 with a sound blaster live card

i have run your setup program in both simple and advanced modes without success.

i used to have sound in myth but only in the front 2 speakers
now i get no sound at all
i am running a 5.1 speaker system

here are the outputs of aplay, arecord my defult.pa and when running pulse audio

dberry@Mythbuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dberry@Mythbuntu:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


==================================================================

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
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
load-module module-alsa-sink device=surround51:CA0106 sink_name=CA0106
load-module module-alsa-source device=hw:CA0106

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
#load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
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
#set-default-source input



=================================================================

dberry@Mythbuntu:~$ pulseaudio
W: alsa-util.c: Device surround51:CA0106 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Device surround51:CA0106 doesn't support 2 channels, changed to 6.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL surround51:CA0106


(note it dosnt go back to a command prompt unless i do a ctrl + C

====================================================================

few other things of intrest if i try to start alsamixer at command prompt it gives

dberry@Mythbuntu:~$ alsamixer 
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused
dberry@Mythbuntu:~$ 


===================================================================

also if i start pavucontrol and go to volume control it gives me the error  "Connection failed: connection refused:




thanks In advanced for any help you can give

ps i am a bit of a linux noob am great in windows though

Thanks 

Daniel

---

### Post by nstamoul on 2008-05-31
It is obviously not a pulseaudio issue.I had the exact same card with the exact same configuration and it worked flawlessly.

It seems you have not loaded alsa at all.Try ```
sudo alsa reload
``` in a terminal and then see if you have any output.

---

### Post by DanielBerry on 2008-05-31
Hi Nstamoul

I tried that command and i got this

dberry@Mythbuntu:~$ sudo alsa reload
[sudo] password for dberry: 
Unloading ALSA sound driver modules: snd-ca0106 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-ca0106 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
dberry@Mythbuntu:~$ 


looks fine to me i think
also i have now been able to get sound but only through the front 2 speakers

thanks

Daniel

---

### Post by nstamoul on 2008-06-01
Now you have to unmute all you speakers in alsa to be able to hear surround sound.You can do that through alsamixer in a terminal or throung gnome-volume-control.

Let us know how it went.

---

### Post by secretlondon on 2008-06-01
I have an Audigy 1 and have sound through ALSA but nothing through pulse, and total silence in Second Life :(

cat ~/.pulse/default.pa
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
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
#load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
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
#set-default-source input
load-module module-combine sink_name=combined master= slaves=
secret@colossus:~/Desktop/SecondLife_i686_1_20_8_88152_RELEASECANDIDATE$

---

### Post by nstamoul on 2008-06-01
You seem to have run the script in advanced mode and have selected no cards.

Rerun the script in simple mode (since you have only one card) and restart pulseaudio.

---

### Post by neymac on 2008-06-07
With this script I got 5.1 sound playing all my sound applications.
Thanks.

But when I run pulseaudio manager I saw that there is only one sound card there, and I cannot choose the other sound card for Skype.
How can I configure to have both sound cards and pick the one I want for Skype? (I use the on board sound device for Skype)

---

### Post by 22Ti on 2008-06-15
nstamoul, Bloody brilliant!!!
We sound blaster 24 bit owners with surround salute you!:-({|==D>

---

### Post by nstamoul on 2008-06-16
> **neymac said:**
> With this script I got 5.1 sound playing all my sound applications.
Thanks.

But when I run pulseaudio manager I saw that there is only one sound card there, and I cannot choose the other sound card for Skype.
How can I configure to have both sound cards and pick the one I want for Skype? (I use the on board sound device for Skype)

Sorry I didn't get back to you sooner.

You must run the script,choose advanced mode,tick both cards.Do not combine them.

Then every time a sound stream occurs you can go to volume control in padevchooser applet,right clik on it and select the card you wish to use for this stream.

Hope this helps you.Feel free to ask again if there are problems.

---

### Post by gotfork on 2008-06-20
For some reason I can't access my bios menu to disable my onboard sound card (heh heh heh).  After trying a lot of other things to install a new soundblaster live this finally did the trick.  Thanks a ton!

---

### Post by nstamoul on 2008-06-23
That's one way of resolving it ;)

I 'm sure you can find the option in your bios but it won't hurt you to leave it as it is.

---

### Post by stoneage on 2008-06-30
Doesn't quite work for me. I get sound in i think, all applications, but I lose system sounds. I get the log in screen 'boink', but not the post log in fanfare. I guess I'm not losing much, but the fact that it is missing is surely indicative of having something not set up properly.

Nice utility though.

---

### Post by fivecoins on 2008-07-07
> **nstamoul said:**
> Hallo there.

I 've been seeing a lot of people complain about the absence of a configuration utility for pulseaudio so I took the time to make one myself.It cat do as simple as select the output of your choice as far as sound card and the number of speakers is concerned.Should you have more than one sound cards you could combine these into one virtual sink.

Of course these features are not my addition to pulseaudio,I just provide a GUI for them.

I tried to make the program as generic as possible as far as the sound cards are concerned.I would appreciate some beta testing.Up to now it has worked wherever I tried it (works solid on Audigy,CA0106,Intel laptop card).

So if it does not work for your setup,please give a simple output of the following:
[LIST]
[*]aplay -l
[*]arecord -l
[*]~/.pulse/default.pa
[*]output of pulseaudio when you run it from a terminal.
[/LIST]


Sorry I can't seem to get it to do anything. I'm very new to Linux (1 month) and not sure what I'm doing wrong.  

I'm pretty happy with Ubuntu in general, but the lack of sound is a deal breaker. I've seen so many complaints about the lack of sound with no solutions.

Output results:

"aplay -l"
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

"arecord -l"
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC882 Analog [ALC882 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

"~/.pulse/default.pa"
bash: /home/john/.pulse/default.pa: Permission denied

tried again with "sudo ~/.pulse/default.pa"
sudo: /home/john/.pulse/default.pa: command not found

I've tried using all of the settings from the "paconfig".
The headphones, front, surround and center jack have output. But the laptop speakers do not have sound.

 Any suggestions?

---

### Post by nstamoul on 2008-07-08
You are not using any command.If you wish to edit the default.pa file you must type nano .pulse/default.pa.

As for the laptop speakers not having sound it is surely an alsa switch.Try launching gnome-volume-control and unmute everything.Also check the switches and you will surely get output from the laptop speakers.

---

### Post by fivecoins on 2008-07-08
Thank You for responding so quickly, but I'm not sure I understand.

"You are not using any command.If you wish to edit the default.pa file you must type nano .pulse/default.pa."

I used the command you suggested and this is the result:
-------------

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnom$
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Load additional modules from GConf settings. This can be configured with th$
### Please keep in mind that the modules configured by paprefs might conflict w$
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
#set-default-source input
load-module module-combine sink_name=combined master= slaves=

-------------

What is it that I am to edit?

-------------

I checked the volume control as you suggested and it only has a "Master" slider.

Currently, It is set to "Simultaneous output to Simultaneous output (Pulse Audio Mixer)"

I changed it to "HDA Intel (Alsa mixer) and checked the sliders.
(Playback Tab) Master, PCM, Front, Front Mic are all set near full volume.
(Switches Tab) Both Headphone and Speaker are checked.
If I edit this setting it appears that I can all several more sliders and I did and none of them are muted. Most are not at full volume, but I move some of them to no effect. 

If I change it to Realtek ALC885 (OSS Mixer)
Again the playback tabs are near full volume and there is not a switches tab.

If I change it to "Simultaneous output (PulseAudio Mixer)
Again there is only one slider "Master" and it is at full.

Which device do I use?

Something that seems rather odd is that the "OSS Mixer" says that I have a Realtek ALC885 and the "aplay-l" shows an ALC882. Is that significant?

I also have the Gnome ALSA Mixer installed and checked it.
It indicates an ALC885 and nothing is muted, Headphones, Speakers & IEC958 are checked, but the Input Sources are not.

I checked the PulseAudio Manager and it is set to combined playback is that correct?

There are way too many place to check audio. Is there one that I can use and get rid of the rest?

Uhhh...now I have no sound at all. Guess I better step back from this thing for a little while.

I would really hate to break it.

---

