---
title: "problems with qjackctl and pulseaudio"
date: 2011-08-17
forum: Multimedia Software
---

### Post by alina.bolero on 2011-08-17
I'm running Natty 11.04 x64.

I'd fired up jackd, via qjackctl, and things were going well on the MIDI side of things.  I'd gotten my M-Audio Axiom 49 keyboard controller to connect to Qsynth and I could route and hear my synths with Jack.

However, I could not hear my regular pulse audio apps (Rhythmbox, Firefox, MPlayer, etc) when I started Jack.

I have copied the /etc/pulse/default.pa over to ~/.pulse/pulsejack.pa, but I didn't change anything because I noted that it already had:

```
.ifexists module-jackdbus-detect.so
load-module module-jackdbus-detect
.endif
```

the ~/.pulse/client.conf has "autospawn = no"

I added this to my Jack setup:

Execute Script on Startup: pulseaudio -k
Execute Script after Startup: pulseaudio -DnF ~/.pulse/pulsejack.pa
Execute Script on Shutdown: pulseaudio -k
Execute Script after Shutdown: killall jackd; pulse-session

However, that seemed to make Qjackctl very grumpy, and now it won't even start!

---

### Post by bikodog on 2011-08-17
I recommend installing kxstudio. It does an excellent job of getting everything to work with jack.

[http://http://ubuntuforums.org/showthread.php?t=1815769]("http://ubuntuforums.org/showthread.php?t=1815769")

---

### Post by alina.bolero on 2011-08-17
Found this link:  [http://fossplanet.com/f10/module-jackdbus-detect-pulseaudio-84602/](http://fossplanet.com/f10/module-jackdbus-detect-pulseaudio-84602/)

I enabled the "D-Bus" in Qjackctl, restarted, and my PulseAudio JACK Sink & Source shows up in the Connections.

Still not hearing anything though.

---

### Post by alina.bolero on 2011-08-18
OK, I think I'm very close ...

Qsynth works.
Mixxx works.
I have the PulseAudio JACK Sink in Jack connections.

I have set the Default Output in gstreamer-properties to "Plugin: Custom" and "Pipeline: jackaudiosink".  When I click "Test" I see the "gstreamer-properties" output port show up in Jack connections and I hear the tone on the right channel.

However, I STILL don't get any sound out of Rhythmbox or Firefox (Youtube/Hulu).

---

### Post by madeinfamous on 2011-08-18
allo alina.bolero!

[https://help.ubuntu.com/community/UbuntuStudioPreparation#PulseAudio%20and%20Jack](https://help.ubuntu.com/community/UbuntuStudioPreparation#PulseAudio%20and%20Jack)


and see my pic here, sorry it's french, but you'll get it! ;)


[https://lh4.googleusercontent.com/-Jd99YUovpI4/Tkwu9f3Dd3I/AAAAAAAAAHI/-m-x17YJNVw/s1280/hangouts%2Bjam.png](https://lh4.googleusercontent.com/-Jd99YUovpI4/Tkwu9f3Dd3I/AAAAAAAAAHI/-m-x17YJNVw/s1280/hangouts%2Bjam.png)

hope this help

have a nice day!

---

### Post by alina.bolero on 2011-08-18
Ha!  Funny thing.  As soon as I closed Mixxx, Rhythmbox, which I THOUGHT was closed, started playing the first song in the queue, and I HEARD IT!

So, it would seem that I have some sort of merging problem.  Will the PulseAudio JACK Sink only take input from one application at a time?  But, frankly, that doesn't seem to make sense either, because Mixxx had its own Port called "PortAudio" in connections.  I'm so confused.   lol

I also need to figure out why I don't get a Rhythmbox task icon, if in fact, it is still running after you "Quit".

---

### Post by alina.bolero on 2011-08-18
OK ... I found the task tray icon enable preference for Rhythmbox.  I've also found out that I can play both Rhythmbox and Firefox stuff at the same time.  However, when I start Mixxx, the PortAudio port shows up and I lose the sound from the PulseAudio JACK Sink (Rhythmbox and Firefox).   So, they seem to be mutually exclusive.  I've tried configuring Mixxx to send to Jack Rack, which works, but that does not seem to allow Rhythmbox and Firefox to play at the same time.

---

### Post by alina.bolero on 2011-08-20
SOLVED!

Some naughty boy put "pasuspender" in the startup command for Mixxx!   Apparently, that effectively pauses all PulseAudio activity.

So, go to Edit Menus and modify the launcher properties to remove pasuspender.

Call me Miss Mixxx A Lot!  :guitar: :guitar:

---

