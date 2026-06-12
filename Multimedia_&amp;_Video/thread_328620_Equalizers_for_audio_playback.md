---
title: "Equalizers for audio playback"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by Jefim on 2006-12-31
Hi, I don't get it - why there are NO equalizers in audio players? Why Rhythmbox, Listem, Banshee, BMPx and a bunch of other players try to surprize us with new innovative features, but not with equalizers? Is it that hard to make one? I really don't like players like BMP (v1.0)/XMMS, but I have no choise! These are he only ones, which have equalizers. Or maybe I am blind? Please, someone, tell me - is this a anti-equalizer strike or what?

Oh, and, BTW, can anyone point out at least one player like BMPx/Listen/Rhythmbox WITH an equalizer?

---

### Post by pseudonym on 2006-12-31
oops, didn't read this close enough before answering....sorry...I don't know...it's new year's eve...cheers!:)

---

### Post by arvster on 2006-12-31
Well, XMMS is a player with an equalizer (although from what I know it is not developed anymore). Amarok has one (although I had some problems with it). I will have to agree with this argument though- equalizers seem to be a rare thing in Linux multimedia world. My favorite player (Exaile) doesn't have one too. My solution to this problem was to use an external  hardware equalizer, but that's not really a true solution.

---sorry I didn't read your post carefully enough about you using XMMS already--------

---

### Post by Jefim on 2006-12-31
Yeah, XMMS is dead (AFAIK) and so is Beep Media Player (I mean the first one). BMPx (aka BMP2) too doen't have an equalizer and that's quite strange. Don't know about Amarok (I'm using Gnome and just don't want to use it). The thing is that I like these players with music libraries (where I don't have to point everytime to the music which I want to listen) and their dynamic playlists are nice, but they all lack this equalizer feature (well, at least these, which I have seen - Rhythmbox, Muine, Banshee, Listen, BMPx etc.).
I'm really confused... :confused:

---

### Post by Falcorian on 2007-01-01
It's one of the things I miss whenever a try a new media player. I agree it should be included by default.

Amarok has one if you want to try a KDE apt. Infact, I'd have to say it's still the best (and most complete) music player for Gnome, even though it's not a gnome program. ;)

---

### Post by merlyn on 2007-01-01
You could try [Audacious]("http://audacious-media-player.org/Main_Page"), which I believe is based on the code from Xmms.

It does have an equaliser, however as I do not use it I can not vouch for how good it is.

Cheers.

---

### Post by Falcorian on 2007-01-01
> **merlyn said:**
> You could try [Audacious]("http://audacious-media-player.org/Main_Page"), which I believe is based on the code from Xmms.

It does have an equaliser, however as I do not use it I can not vouch for how good it is.

Cheers.
It lacks a library (if I remember) though, Amarok has a library feature (infact... I maybe the only one with both a library and a equalizer...)

---

### Post by MrRoboto on 2007-01-06
read here

[http://www.mail-archive.com/rhythmbox-devel@gnome.org/msg02966.html](http://www.mail-archive.com/rhythmbox-devel@gnome.org/msg02966.html)

---

### Post by SuperDindon on 2007-01-06
Amarok!

Furthermore the right way to equalize every playback would be a LADSPA equalizer plugin for ALSA, but it doesn't exist/I haven't found one yet ( apart from the TAP peaking equalizer ). 


**PS :** There may be this one : [http://packages.ubuntu.com/edgy/sound/fil-plugins.html](http://packages.ubuntu.com/edgy/sound/fil-plugins.html) , even if its description doesn't specify the type of eq.
If you want to give it a try, the configuration of a LADSPA plugin through ALSA may look quite unintelligible to you though :-k . Look into the ALSA wiki for more info and here's one ( bad ) example I backup when I tried to configure the tap-eq plugin ( which isn't what I wanted ) for my Sennheiser HD-595 headphones which may be helpful :
```
# [COLOR="Red"]/etc/asound.conf[/COLOR] or [COLOR="Red"]~/.asoundrc[/COLOR]

pcm.hd595_ladspa {
    type ladspa
    slave.pcm "plughw:0,0";
    playback_plugins [ {
        label tap_equalizer
        input {
            controls [ -4.5 0 -4.5 -11 -8.5 -13 -15 -8.2
                       60 170 310 600 1000 3000 12000 14000 ]
        }
    } ]
}

pcm.!default {
    type plug
    slave.pcm "hd595_ladspa";
}
```
It may also be possible to combine it with Dmix.

( Sorry for my approximative english )

---

### Post by reaganf2 on 2007-10-28
I've recently migrated from windows to ubuntu, and find the ubuntu default media player rhythmbox pretty amazing, except for the fact that it has no equalizer... In fact, this is a problem I've noticed in most open source media players... They either don't have equalizers at all (eg: rhythmbox), or have ones that are extremely poor in performance and insufficient (eg: amarok)... So far, the best music player I've seen quality-wise has been audacious, which I continue to use only because of the impeccable sound quality I can obtain from it... I however haven't been able to find the EQ-Audacious plugin mentioned on the audacious website... All links to this plugin seem to be dead... Does anybody know where I can get this from..??

---

### Post by phaidros on 2007-10-29
> **reaganf2 said:**
> I however haven't been able to find the EQ-Audacious plugin mentioned on the audacious website... All links to this plugin seem to be dead... Does anybody know where I can get this from..??

erm, there are 2 faders and 2 buttons right below the display in the default skin. the faders are for volume and balance. the button with the bars on is the EQ :) 
the button with the stripes on is the playlist, they both will show up as seperate attachable windows to audacious.

hth :)

---

### Post by reaganf2 on 2007-10-29
thanks for the enlightenment phaidros...
i was referring to the 31 band equalizer plugin mentioned on the audacious plugins page...

---

### Post by qix on 2007-10-31
Audacious 31-band eq: [http://gd.tuwien.ac.at/opsys/linux/gentoo/distfiles/eq-audacious-0.21.tgz](http://gd.tuwien.ac.at/opsys/linux/gentoo/distfiles/eq-audacious-0.21.tgz)

If it doesn't work, then just search google for 'eq-audacious-0.21.tgz' which seems to be the newest version.

You need to compile it yourself, but it's rather simple. Extract the archive and browse to the folder. Then do ```
./configure --verbose
``` and fix it if it reports missing dependencies. To get the needed dependencies, you probably want to do a ```
sudo apt-get audacious-dev
``` If you still need more stuff, then try ```
sudo apt-get build-dep audacious
```

Once you can run './configure' without errors, do a
```
make && sudo make install
```

Restart Audacious and it should work.

Disclaimer: It worked for me this way, but I can't guarantee it will for you...
Btw to be sure, you probably need to shut down Audacious before you compile, just to be sure.

---

### Post by reaganf2 on 2007-11-02
thanx a ton for that... was lookin' all over for that link...
now since problem one is sorted out, anybody heard of a volume normalizing plugin for audacious...??

---

### Post by reaganf2 on 2007-11-14
hi all...
recently upgraded to audacious 1.4...
eq-audacious-0.21 doesn't seem to work anymore... it doesn't appear in the plugins list even after recompiling...
[http://sacredspiral.co.uk/audacious](http://sacredspiral.co.uk/audacious) however mentions the latest version of the plugin eq-audacious-ng... anybody know where to find it..?? or at least one that works with audacious 1.4...??

---

### Post by koleoptero on 2007-11-14
If you people are really intent on getting good sound from your players you should try aqualung. I started using it because I wanted the gapless playback feature it has that works great. But then I wanted an equalizer too. The thing is aqualung uses the LADSPA plugins for sound processing. I installed the TAP plugins that are mentioned in aqualung's homepage, and voila, it has a parametric equalizer.
The only problem is to find a nice setting that agrees with your ears since you'll have to select the banc frequencies, gain, and range yourselves. It sounds daunting, and it seems useless but you'll be surprised with the results.

In these plugins also is a very nice one called TAP Dynamics, that can act as a compressor to normalize the sound volume. It works fine and honestly way better than replaygain in my opinion.

Audacity sounds ok, but I've found that aqualung sounds much much better than anything else I've used either in linux or in windoze.

If you want though a program that can do just about everything (including a library, streaming etc) you can also use exaile which is GTK based, has an equalizer that works (almost) fine and all the features needed by a large music collection.

---

### Post by ktoulgaridis on 2008-06-06
Hello there!

Only one q about aqualung.
Does it support devices? (ipod)?

---

### Post by Dorjin on 2008-07-05
I was looking at Aqualung because I need something with seamless playback and an EQ, but I'm new to Linux and haven't attempted to compile anything yet - how difficult was it to get up and running? 

Also - the biggest problem i find with digital audio seems to be clipping - without an EQ in the software i can't turn down the pre-amp enough to get a clean sound (sounds like static otherwise - VLC has an EQ that fixed the gain, but the transition between tracks is almost jagged) 

Shame there doesn't seem to be any reliable DJ software for linux yet - since every DJ who runs a laptop seems to resort to a dual-boot for live performances.

---

### Post by edm1 on 2008-07-05
> **Dorjin said:**
> Shame there doesn't seem to be any reliable DJ software for linux yet - since every DJ who runs a laptop seems to resort to a dual-boot for live performances.

There is some decent DJing software called Mixxx. I've recently set it up using time coded vinyl which works very nicely although my laptop isnt quite good enough to get the latency low enough to be able to scratch with.

---

### Post by Dorjin on 2008-07-05
> **edm1 said:**
> There is some decent DJing software called Mixxx. I've recently set it up using time coded vinyl which works very nicely although my laptop isnt quite good enough to get the latency low enough to be able to scratch with.

 Funny you should mention it - I'd just started reading up on it this morning. Installed it, tried it, love it. The sound quality is clean enough that i didn't feel like i needed an elaborate EQ right away (but still going to see if one can be added in - i like the idea of having everything built into the software...and therefore as portable as a laptop with no peripherals as possible for some occasions) - bright side is that until then, it sounds nice piped through an external 32 band Behringer. 

 Still reading through the forums - and if i haven't already found them - could you direct me to a "how-to" on adding in custom scripts... and maybe a library of already tested scripts? 

 - looking to set something up that allows auto-quing and beat matching of a set play list? 

 (Normally, I'd understand that such a thing might seem offensive to truly talented DJ's... but i've got a wedding coming up - specifically, my own... meaning i won't be avail to run the audio, my talented DJ friends will be too busy celebrating (read: wasted) to be dependable throughout the reception - and i'm hoping that my "responsible" friend can get set up with set play lists... and essentially a couple red "start" and "stop" buttons that will handle fading automatically.) 

 On a related note - finding a more elaborate EQ to tie in and setting up the auto-fade for the playlist que would make this usable as a really sweet daily use media player for when you couldn't be in front of the screen constantly - but still handle things 'manually' when so desired... 

 Thoughts?

---

