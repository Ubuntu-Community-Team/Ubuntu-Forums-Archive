---
title: "persisting pulseaudio jack-module setup"
date: 2010-09-25
forum: Multimedia Software
---

### Post by dewdrop_world on 2010-09-25
From a handful of online sources, I have a sequence of events that connects pulse audio to Jack instead of to the physical hardware -- so I can run jack audio apps (e.g. supercollider) and also get audio from pa apps (rhythmbox).

1. Start jack server.

2. Load jack modules for pulse audio:

pactl load-module module-jack-source
pactl load-module module-jack-sink

3. Open pulse audio device chooser and manually set the sink to other (type in jack_out) and the source to other (jack_in).

4. Tell gstreamer where to route audio.

gconftool-2 -t string --set /system/gstreamer/0.10/default/audiosink pulsesink
gconftool-2 -t string --set /system/gstreamer/0.10/default/audiosrc pulsesrc
gconftool-2 -t string --set /system/gstreamer/0.10/default/musicaudiosink pulsesink

I would like to have this as my default setup -- boot up, login and all audio is going through Jack. Or, if that isn't feasible*, can this be done as a script instead?

* Come to think of it, maybe I shouldn't make it the default because Skype does not get along with the pulse audio jack plug-ins. If my session always starts with this configuration, I wouldn't be able to use Skype in Linux!

TIA,
James

---

### Post by cchhrriiss121212 on 2010-09-25
The advice I would give to you is that jack should be used for audio work, and pulse should be used for everything else.
It is possible to do it, but whether it is worth it is questionable. [Here is a solution]("http://alsa.opensrc.org/index.php/Jack_%28plugin%29") that may work, but I have not tried it on 10.04.

If you want to be able to play music while using jack, then try using VLC or alsaplayer which both have jack plugins.

---

### Post by dewdrop_world on 2010-09-25
In the "why people shovel money at Apple or Microsoft" department...

> **cchhrriiss121212 said:**
> The advice I would give to you is that jack should be used for audio work, and pulse should be used for everything else.
It is possible to do it, but whether it is worth it is questionable. [Here is a solution]("http://alsa.opensrc.org/index.php/Jack_%28plugin%29") that may work, but I have not tried it on 10.04.

If you want to be able to play music while using jack, then try using VLC or alsaplayer which both have jack plugins.

OK, so not as a default then.

How well does VLC integrate with my (pre-switch to linux) ipod? I've been using rhythmbox b/c it works great with the pod. I'm open to alternatives, but don't care to deal with a crap interface either.

A couple of dumb things that I would not do with the pa --> jack config:

Plug pulse into jack when I'm playing a concert. DUH... in that case I'd be running jack + supercollider ONLY.

Run hard-core synthesis in supercollider while banging away at pulseaudio from a few other apps.

Sometimes I have to write code for my music that is more about logic than sound. I like to play music then. If I need to test something that makes noise, then, workflow without pa -> jack:

Kill the music player.
Start jack (and hope it can get hold of the HW).
Start SC server.
Load resources.
Test.
Quit SC server.
Stop jack.
Relaunch the music player.

Or I can do a little umpty umpty at login and be able to just, y'know, *pause* the music for a few seconds. There's only so much inconvenience I'll take for the sake of being prim and proper... :P  I was just hoping to streamline the umpty umpty, but if it's too naughty for that, then I'll keep doing it by hand.

Oh, I did try the ALSA -> jack trick awhile back, failed. No sound from non-jack apps.

Thanks :)
James

---

### Post by cchhrriiss121212 on 2010-09-25
OK, I understand what you want to achieve, you want to play music while working on your music right? I like to do the same thing using alsaplayer through jack.

You can keep Rhythmbox around for your iPod, and use alsaplayer/VLC to play music when you are using jack. No starting/stopping jack required. Just install the packages alsaplayer-gtk and alsaplayer-jack from synaptic.

I know it is not what you asked for specifically, but I prefer to avoid using 2 sound servers when one will do.

If you don't like that, I have heard that pulse+jack compatibility steps up in 10.10, but I will believe that when I see it.

---

### Post by dewdrop_world on 2010-09-26
Actually, I discovered that pa device chooser does persist jack_out and jack_in as defaults! So all I have to do is boot the Jack server first thing when I log in. If I'm not using any non-jack apps, no need to do anything but if I want to listen to something on the iPod later, I can simply load the jack modules. Pulseaudio then appears as an input and output client in qjackctl's connections window, automatically connected to system in and out.

I understand about avoiding two sound servers. I'm also trying to avoid loading my music library onto my HD (which I always hated about iTunes on the Mac -- you can't sync anything to the iPod unless it's on the hard drive -- copy directly from an external disk to the iPod? No... why would you want to do that?). Currently for me, listening to music on my Linux box requires an iPod-ready player, and I'm not going to copy almost 40 GB of files onto the hard drive just so that I can use VLC for music listening.

I'll have to use it more extensively to know how stable it is (or isn't). The phase of work in my current project is such that I'm making more noise than doing logic programming, so I won't be able to beat this to death in the near future. Also I have a bad memory chip, so I don't want to draw any conclusions about stability until that's replaced.

Thanks for the suggestions, though.
James

---

### Post by dewdrop_world on 2010-10-04
> **dewdrop_world said:**
> * Come to think of it, maybe I shouldn't make it the default because Skype does not get along with the pulse audio jack plug-ins. If my session always starts with this configuration, I wouldn't be able to use Skype in Linux!

Update -- I based this assertion on some bitter arguments on web forums between PA and Skype people, where the Skype people claimed that PA's jack connection was badly written and the PA folks claimed that Skype uses the API incorrectly. Whatever the issue was, it seems to have been fixed because last night, I had Skype running through pulse audio connected to Jack using the above configuration (no need for the gstreamer commands, though). I had to use pavucontrol to switch Skype to use the jack source/sink, but other than that it was painless.

!!

James

---

