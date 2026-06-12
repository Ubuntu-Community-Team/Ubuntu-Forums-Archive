---
title: "Which are a music player that uses the equalizer"
date: 2010-09-06
forum: Multimedia Software
---

### Post by Rintindumb on 2010-09-06
I use several players, but all of it was no equalizer , while i was using Aimp with wine
but there are some problems, when i stop the songs in the play, and run it back , i hear no sound on it , are we life in digital world ? music player without equalizer its like nightmare for me , like going back into the past , it was like seeing my father met my mother at the time of their first date

---

### Post by steve161 on 2010-09-06
Both Banshee and exaile have equalizers, and both are in the repos.

---

### Post by Rintindumb on 2010-09-07
well thanks banshee worked perfectly

---

### Post by steve161 on 2010-09-07
You are welcome.

---

### Post by tommcd on 2010-09-07
Also, if you would like a simple old school winamp like music player, **audacious** comes with an equalizer. The **xmms** music player is also a winamp clone and comes with an equalizer; but it is not present in the Ubuntu repos. 
I never use equalizers though. A flat response is always the best.

---

### Post by Linuxforall on 2010-09-07
If you have a good card, equalizers make them sound bad but Amarok, vlc, Banshee, Exalie, Audacious all have eqs, vlc has more than eq, it has spatializer etc.

---

### Post by wainbee on 2010-09-08
> **Rintindumb said:**
> I use several players, but all of it was no equalizer , while i was using Aimp with wine
but there are some problems, when i stop the songs in the play, and run it back , i hear no sound on it , are we life in digital world ? music player without equalizer its like nightmare for me , like going back into the past , it was like seeing my father met my mother at the time of their first date
Rhythmbox has an excellent equalizer plug-in.
Qmmp is a simple player with a rich sounding on-board equalizer.

My favourite is DeaDBeef which has a built-in 18 band equalizer.
DeaDBeef is a simple and powerful music player.

To install DeaDBeeF in Ubuntu 10.04 or 9.10:
Open the terminal and run the following commands 

sudo add-apt-repository ppa:alexey-smirnov/deadbeef 
sudo apt-get update 
sudo apt-get install deadbeef

Good luck!

---

### Post by shantiq on 2010-09-08
all info you need to [install xmms]("http://ubuntuforums.org/showthread.php?t=1525072") on karmic/lucid/maverick    to my mind still the player with the best sound



and the newest of them all many say the best [deadbeef]("http://ubuntuforums.org/showthread.php?t=1503749") has the equalizer option too

[IMG]http://img842.imageshack.us/img842/4681/deadbeef041004.png[/IMG]

---

### Post by tommcd on 2010-09-08
> **shantiq said:**
> all info you need to [install xmms]("http://ubuntuforums.org/showthread.php?t=1525072") on karmic/lucid/maverick    to my mind still the player with the best sound ...

Yeah, I saw that but I have not tried it. That is quite seems like quite a lot to do just for xmms.
Fortunately, Slackware still includes xmms.

---

### Post by shantiq on 2010-09-09
> **tommcd said:**
> Yeah, I saw that but I have not tried it. That is quite seems like quite a lot to do just for xmms.
Fortunately, Slackware still includes xmms.



which is such a shame that it is no longer in the repo since it has the best sound of them all maybe i should start a campaign to bring back xmms

---

### Post by cascade9 on 2010-09-09
> **Linuxforall said:**
> If you have a good card, equalizers make them sound bad but Amarok, vlc, Banshee, Exalie, Audacious all have eqs, vlc has more than eq, it has spatializer etc.

If you've got a good card (or even a bad card) and typical 'PC' speakers, EQ can help. Those cheap speakers always how some 'hole' that you can help fill at least a little by playing with the EQ levels.

> **shantiq said:**
> which is such a shame that it is no longer in the repo since it has the best sound of them all maybe i should start a campaign to bring back xmms

'Best sound of them all'? After that whole discussion about lossless where you think that .shn sounds better than other lossless, I'm not going into THAT gain LOL ;) 

As for 'bring back XMMS'- eeerrr....it still use GTK1.x. Which is part of the reason why its been dropped by at least some distros. Other reasons are the some developesr say that XMMS has design and maintainance issues and its been out of development for years. Heck, even the BMP fork of XMMS is out of development now, I think the only fork still going is audacious (which is actually a fork of a fork, being forked off BMP).

---

### Post by shantiq on 2010-09-09
well cascade many still really rate it

to me it is number 1
then deadbeef
vlc is astounding but to me not so much for music more for film
audacious is ok qmmp too

all the library ones i never use   not my thing


as for shorten i still maintain what i said    the best clear as a bell  ::::))))


ps   > and its been out of development for years. Heck, even the BMP fork of XMMS is out of development now, I think the only fork still going is audacious (which is actually a fork of a fork, being forked off BMP)

that is true but does not say anything about its quality

some cars were made in the 30's which were perfect
vinyl was better than cds and yet taken away   how about betamax

new or recent does not always mean better   it often does but not always:KS:KS

---

### Post by andrew.46 on 2010-09-09
Hi Rintindumb,

Has anybody mentioned SMPlayer / MPlayer? It bristles with equalisers :).

Andrew

---

### Post by shantiq on 2010-09-09
wow another one.  is that one SM player for the sadomasochistic amongst us andrew:KS:KS:KS:KS


will check it out the version on maverick is 0.6.9-1 (smplayer)
Version: 0.6.9 (SVN r3447)

i take it that is state of the art?

it claims all these **nice features**


SMPlayer intends to be a complete front-end for MPlayer, from basic features like playing videos, DVDs, and VCDs to more advanced features like support for MPlayer filters and more.


[COLOR="Red"]One of the most interesting features of SMPlayer: it remembers the settings of all files you play. So you start to watch a movie but you have to leave... don't worry, when you open that movie again it will resume at the same point you left it, and with the same settings: audio track, subtitles, volume...[/COLOR]   now that is cool

Other additional interesting features:

[LIST=1]
[*]Configurable subtitles. You can choose font and size, and even colors for the subtitles.
[*]Audio track switching. You can choose the audio track you want to listen. Works with avi and mkv. And of course with DVDs.
[*]Seeking by mouse wheel. You can use your mouse wheel to go forward or backward in the video.
[*]Video equalizer, allows you to adjust the brightness, contrast, hue, saturation and gamma of the video image.
[*]Multiple speed playback. You can play at 2X, 4X... and even in slow motion.
[*]Filters. Several filters are available: deinterlace, postprocessing, denoise... and even a karaoke filter (voice removal).
[*]Audio and subtitles delay adjustment. Allows you to sync audio and subtitles.
[*]Advanced options, such as selecting a demuxer or video & audio codecs.
[*]Playlist. Allows you to enqueue several files to be played one after each other. Autorepeat and shuffle supported too.
[*]Preferences dialog. You can easily configure every option of SMPlayer by using a nice preferences dialog.
[*]Possibility to search automatically for subtitles in opensubtitles.org.
[*]Translations: currently SMPlayer is translated into more than 20 languages, including Spanish, German, French, Italian, Russian, Chinese, Japanese....
[*]It's multiplatform. Binaries available for Windows and Linux.
[*]SMPlayer is under the GPL license.
[/LIST]



also playing around found out "shift D" gives a **series of snapshots**     that feature is not on vlc that i know of

---

### Post by andrew.46 on 2010-09-09
Hi shantiq,

> **shantiq said:**
> [...] playing around found out "shift D" gives a **series of snapshots**     that feature is not on vlc that i know of

If you have a look in the 'Video' options of vlc you may find this feature :). Coming soon for the svn MPlayer will be a capture mechanism for streams which will capture a live stream if the appropriate commandline option is given and the default 'c' key is used, it will be a great addition to a great program.

BTW if you are interested in taking screenshots with the commandline MPlayer have a look at Tip 5 here:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

Andrew

---

### Post by oldos2er on 2010-09-09
I've been using the system-wide Pulseaudio equalizer for a few weeks now, and it's working very well. [http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/](http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/)

---

### Post by tommcd on 2010-09-09
> **cascade9 said:**
> 
As for 'bring back XMMS'- eeerrr....it still use GTK1.x. Which is part of the reason why its been dropped by at least some distros. Other reasons are the some developesr say that XMMS has design and maintainance issues and its been out of development for years. ...
Pat Volkerding does not seem to have any trouble maintaining xmms on Slackware. Nothing is included with Slackware unless it is 100% stable. Slackware 13.1 includes both gtk+-1.2.10 and gtk+2-2.18.9. Also, xmms uses less CPU resources than audacious and most other media players.

---

### Post by andrew.46 on 2010-09-09
Hi tommcd,

> **tommcd said:**
> Pat Volkerding does not seem to have any trouble maintaining xmms on Slackware.

Although of course he did remove it from [slackware 12.0]("http://slackware.osuosl.org/slackware-12.0/ChangeLog.txt"):

```

**[COLOR="Red"]Thu Mar 15 19:43:10 CDT 2007[/COLOR]**
[...]
xap/xmms-1.2.10-i486-3.tgz:  XMMS developers:  THANK YOU for your years of
  dedication.  We look forward to considering a new GTK+2 based design some
  time in the future.  (Package removed).

```

and then reinstated it for [12.2]("http://slackware.osuosl.org/slackware-12.2/ChangeLog.txt"):

```

**[COLOR="Red"]Thu Sep 11 16:02:24 CDT 2008[/COLOR]**
xap/xmms-1.2.11-i486-1.tgz:  Added xmms-1.2.11.  This is an audio player that
  is similar to audacious, but uses about a third of the CPU power.
  Please note that "doublesize" mode seems broken -- if it is enabled, XMMS
  will crash, and then will not start again until $HOME/.xmms is cleared out.
  Any patch for this issue would be appreciated.

```

Not quite sure what went on behind the scenes...

Andrew

---

### Post by Linuxforall on 2010-09-10
> **cascade9 said:**
> If you've got a good card (or even a bad card) and typical 'PC' speakers, EQ can help. Those cheap speakers always how some 'hole' that you can help fill at least a little by playing with the EQ levels.



'Best sound of them all'? After that whole discussion about lossless where you think that .shn sounds better than other lossless, I'm not going into THAT gain LOL ;) 

As for 'bring back XMMS'- eeerrr....it still use GTK1.x. Which is part of the reason why its been dropped by at least some distros. Other reasons are the some developesr say that XMMS has design and maintainance issues and its been out of development for years. Heck, even the BMP fork of XMMS is out of development now, I think the only fork still going is audacious (which is actually a fork of a fork, being forked off BMP).


My card is hooked to Yamaha active monitor speakers, they are as accurate and flat as any of the best out there.

---

### Post by shantiq on 2010-09-10
> 
Not quite sure what went on behind the scenes...

Andrew


maybe requests maybe quality always wins out in the end:KS:KS:KS ha but we know that not to be true   it would not be hard to have it back on ubuntu but it is true that it is no longer maintained

---

### Post by lystor on 2010-09-10
> **Rintindumb said:**
> Which are a music player that uses the equalizer
My favourite music player with equalizer support in [Ubuntu 10.10 is vlc 1.1.4]("http://pkgs.org/ubuntu-10.10-i386/ubuntu-universe/vlc_1.1.4-1ubuntu1_i386.deb.html").

---

### Post by cascade9 on 2010-09-10
> **shantiq said:**
> that is true but does not say anything about its quality

some cars were made in the 30's which were perfect
vinyl was better than cds and yet taken away   how about betamax

new or recent does not always mean better   it often does but not always:KS:KS

If XMMS did have some quality increase over other linux media player, then IMO somebody would (or at l;east should) have fixed the code, somehow, or got that code working on a different player. Fair enough, you think it sounds better, and I'm not going to convince you of any different

I agree, newer doesnt always mean better. 

Vinyl was different to CDs. Better? Maybe, for play no#1, but one of the advanatges for CDs was that no wear and tear (causing track wear and data loss). Vinyl has not been 'taken away'...sure, the majors dont put out much vinyl these days, but that is about profit, logistics and the percivied market.   

I cant think of anything car from the 1930s that was prefect. Come to think of it, I dont think there are any prefect cars now.......but I am biased, I HATE cars. 

@ andrew.46- interesting. From what you've posted, seems like slackware removed XMMS due to it needing GTk1., and gave a subtle 'push' to the XMMS developers to fix the issue. Considering that GTK2.0 was released in 2002, and slack 12.0 2007, it makes sense in at least somes way to me. I'd *guess* that be slack12, XMMS would be the only GTK1.X program left, and including GTK1.X just for 1 application could be PITA. 

@ tommcd- "Nothing is included with Slackware unless it is 100% stable" doesnt square with the crashing if doublesize is used. 

> **Linuxforall said:**
> My card is hooked to Yamaha active monitor speakers, they are as accurate and flat as any of the best out there.

Whcih is great for you, but making a blanket statement that "if you have a good card, equalizers make them sound bad" is misleading, at best. For you? Yeah, EQ probably would make things sound worse, but not everybody has good (or even decent) speakers.

---

### Post by shantiq on 2010-09-10
> **oldos2er said:**
> I've been using the system-wide Pulseaudio equalizer for a few weeks now, and it's working very well. [http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/](http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/)



ok can you say a bit more about this one how to install

i have got it running but it does not show up as a gui

do i need to set

my sound to pulse audio first?

using   ```
gstreamer-properties
```

alsa is the default sound system on lucid and maverick

so yes could you please say a few words to get it going

it modifies the sound on my alsa set up but i cannot see it

is there anything else that needs to be allowed in the synaptic first?



thanx

```
shantiq@shantiq-desktop:~$ pulseaudio-equalizer enable
PulseAudio Equalizer/LADSPA Processor 2.7 (05/02/2010)
-------------------------------------
Current operation: disabling equalizer
-------------------------------------
Unloading & reloading stream-restore module...
Unloading module-ladspa-sink...
Moving active PulseAudio clients to ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo)...
Transferring current mute (0) & volume (100%) to ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo)...
-------------------------------------
Current operation: enabling equalizer
-------------------------------------
Unloading & reloading stream-restore module...
Loading module-ladspa-sink...
Transferring current mute (0) & volume (100%) to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
Setting ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo) preamp (1.0x)...
Setting LADSPA sink (ladspa_output.mbeq_1197.mbeq) as default sink...
Moving active PulseAudio clients to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
-------------------------------------
Equalizer status: [enabled]
Equalizer configuration status: [enabled]
Equalizer plugin: [mbeq_1197/mbeq]
Equalizer control: [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]
NOTE: Using user-customized settings from '/home/shantiq/.pulse/equalizerrc'...
-------------------------------------
shantiq@shantiq-desktop:~$ 

```


ps oh and i run my sound through external alpha lexicon box



```

```

---

### Post by andrew.46 on 2010-09-12
Hi cascade,

> **cascade9 said:**
>   @ tommcd- "Nothing is included with Slackware unless it is 100% stable" doesnt square with the crashing if doublesize is used.

Mind you that changelog is written for the *testing* branch of Slackware known as Slackware -current. When the stable version of Slackware 12.2 was released there was a patch in place that addressed this problem...

Andrew

---

### Post by tommcd on 2010-09-13
Y'know, I did not remember that xmms was removed from Slackware 12.0. I was relatively new to Slackware at the time. I was mostly using **audacious** (an xmms clone / fork) at that time anyway. When I discovered that xmms was lighter on system resources than audacious, I began using xmms.

Anyway, my point was that:
Xmms is a light, fast, and perfectly capable music player for linux. I currently have no need for anything else or more 
"full featured" for playing music. And xmms comes with the (apparently !!!) much sought after graphic equalizer that many people obviously want.
It should not (from my completely non-technical end user experience and knowledge level) be all that difficult for the Ubuntu devs to put xmms back in the Ubuntu repos.

It is a shame that xmms is no longer being developed. There will always be a need for light, fast, and simple apps for every computer task. Xmms continues to fill that niche for a light fast and simple music player very well.

---

### Post by oldos2er on 2010-09-13
> **shantiq said:**
> ok can you say a bit more about this one how to install

i have got it running but it does not show up as a gui

do i need to set

my sound to pulse audio first?



is there anything else that needs to be allowed in the synaptic first?



thanx

[CODE]shantiq@shantiq-desktop:~$ pulseaudio-equalizer enable
PulseAudio Equalizer/LADSPA Processor 2.7 (05/02/2010)
-------------------------------------
Current operation: disabling equalizer
-------------------------------------
Unloading & reloading stream-restore module...
Unloading module-ladspa-sink...
Moving active PulseAudio clients to ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo)...
Transferring current mute (0) & volume (100%) to ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo)...
-------------------------------------
Current operation: enabling equalizer
-------------------------------------
Unloading & reloading stream-restore module...
Loading module-ladspa-sink...
Transferring current mute (0) & volume (100%) to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
Setting ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo) preamp (1.0x)...
Setting LADSPA sink (ladspa_output.mbeq_1197.mbeq) as default sink...
Moving active PulseAudio clients to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
-------------------------------------
Equalizer status: [enabled]
Equalizer configuration status: [enabled]
Equalizer plugin: [mbeq_1197/mbeq]
Equalizer control: [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]
NOTE: Using user-customized settings from '/home/shantiq/.pulse/equalizerrc'...
-------------------------------------
shantiq@shantiq-desktop:~$ 


Yeah, I'd think you need to set sound to pulseaudio first. For the GUI, try running **pulseadio-equalizer-gtk**

Let me know if it works.

---

### Post by shantiq on 2010-09-14
thaNKs THAT did it  ```
pulseaudio-equalizer-gtk
```



going to write a little guide to explain whole process from start to finish on maverick


thank you  ps   seems to have started it now it will open from desktop

```
shantiq@shantiq-desktop:~$ pulseaudio-equalizer-gtk
Getting settings...
ls: cannot access /home/shantiq/.pulse/presets/*.preset: No such file or directory
Applying settings...
Disabling persistence...
Current operation: saving configuration (disable-config)
-------------------------------------
Equalizer setting saved (disable-config).
-------------------------------------
Enabling...
PulseAudio Equalizer/LADSPA Processor 2.7 (05/02/2010)
-------------------------------------
Current operation: disabling equalizer
-------------------------------------
Unloading & reloading stream-restore module...
Unloading module-ladspa-sink...
Moving active PulseAudio clients to ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo)...
Transferring current mute (0) & volume (100%) to ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo)...
-------------------------------------
Current operation: enabling equalizer
-------------------------------------
Unloading & reloading stream-restore module...
Loading module-ladspa-sink...
Transferring current mute (0) & volume (100%) to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
Setting ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo) preamp (1.0x)...
Setting LADSPA sink (ladspa_output.mbeq_1197.mbeq) as default sink...
Moving active PulseAudio clients to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
-------------------------------------
Equalizer status: [enabled]
Equalizer configuration status: [disabled]
Equalizer plugin: [mbeq_1197/mbeq]
Equalizer control: [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]
NOTE: Using user-customized settings from '/home/shantiq/.pulse/equalizerrc'...
-------------------------------------
shantiq@shantiq-desktop:~$ pulseaudio-equalizer-gtk
Getting settings...
ls: cannot access /home/shantiq/.pulse/presets/*.preset: No such file or directory
Match!
Applying settings...
Disabling persistence...
Current operation: saving configuration (disable-config)
-------------------------------------
Equalizer setting saved (disable-config).
-------------------------------------
Enabling...
PulseAudio Equalizer/LADSPA Processor 2.7 (05/02/2010)
-------------------------------------
Current operation: disabling equalizer
-------------------------------------
Unloading & reloading stream-restore module...
write(): Broken pipe
Unloading module-ladspa-sink...
write(): Broken pipe
Moving active PulseAudio clients to ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo)...
Transferring current mute (0) & volume (100%) to ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo)...
-------------------------------------
Current operation: enabling equalizer
-------------------------------------
Unloading & reloading stream-restore module...
Loading module-ladspa-sink...
Transferring current mute (0) & volume (100%) to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
Setting ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo) preamp (1.0x)...
Setting LADSPA sink (ladspa_output.mbeq_1197.mbeq) as default sink...
Moving active PulseAudio clients to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
-------------------------------------
Equalizer status: [enabled]
Equalizer configuration status: [disabled]
Equalizer plugin: [mbeq_1197/mbeq]
Equalizer control: [4.8,4.8,3.5,2.5,0.0,-7.0,-14.0,-10.0,-10.0,-8.0,1.0,1.0,5.2,7.7,9.5]
NOTE: Using user-customized settings from '/home/shantiq/.pulse/equalizerrc'...
-------------------------------------
Match!
Applying settings...
Disabling persistence...
Current operation: saving configuration (disable-config)
-------------------------------------
Equalizer setting saved (disable-config).
-------------------------------------
Enabling...
PulseAudio Equalizer/LADSPA Processor 2.7 (05/02/2010)
-------------------------------------
Current operation: disabling equalizer
-------------------------------------
Unloading & reloading stream-restore module...
Unloading module-ladspa-sink...
write(): Broken pipe
Moving active PulseAudio clients to ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo)...
Transferring current mute (0) & volume (100%) to ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo)...
-------------------------------------
Current operation: enabling equalizer
-------------------------------------
Unloading & reloading stream-restore module...
Loading module-ladspa-sink...
Transferring current mute (0) & volume (100%) to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
Setting ALSA sink (alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.analog-stereo) preamp (1.0x)...
Setting LADSPA sink (ladspa_output.mbeq_1197.mbeq) as default sink...
Moving active PulseAudio clients to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...
-------------------------------------
Equalizer status: [enabled]
Equalizer configuration status: [disabled]
Equalizer plugin: [mbeq_1197/mbeq]
Equalizer control: [2.7,2.7,2.7,1.5,1.5,1.4,0.0,-3.6,-8.0,-7.2,-9.8,-8.9,-6.6,1.4,5.8]
NOTE: Using user-customized settings from '/home/shantiq/.pulse/equalizerrc'...

```

---

### Post by STart_Blender on 2011-02-08
One of the best EQ is SMPlayer, look at freequency range from 31hz  up to 16khz AND it doesn't distort sound even when highest values are set. It would be nice that pulseaudio eqaliser used the same algorithm or the same code part from SMPlayer becaus when I tryed pulseaudio EQ it distorts sound when high values are set.

---

