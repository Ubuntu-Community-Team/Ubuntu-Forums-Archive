---
title: "Questions to M-Audio Delta users (ideally 1010LT)"
date: 2009-05-29
forum: Multimedia Software
---

### Post by mrowth on 2009-05-29
I'm planning to get an M-Audio Delta 1010LT. I can afford it, and I believe it'll be more than enough - if it works. So I'd really appreciate some more information on this card. 

For example, what do **aplay -l** and **cat /proc/asound/pcm** say? It'd be a start.

Thanks!



The clarifying extrablab:

I keep hearing things like "such-and-such app wants/takes/should be given full control of the sound hardware". But I have yet to encounter an app that HAD full control of my lil VIA8237 AC97 onboard soundchip. (Full control of "hw:0,1" - yes. But there's still "hw:0,0" which, it seems, can take 4 more apps for a total of 5 with just "hw:" interfaces.)

Because - besides getting it to work in a JACK setup, I'd like to use the Delta 1010LT to replace the onboard sound, i.e. Amarok, games, Flash, Wine, movies, preferably without Pulse and without .asoundrc dmix and rate conversion tricks and without worrying what'll grab the soundcard for itself. Problem? I'll use Pulse if I have to, but I'd rather keep things simple.

System is Kubuntu 9.04, 32 bit, with KDE 4.2.3, alsad 1.0.19 (other ALSA packages are 1.0.18), jackd 0.116.1, 2.6.28-11-generic kernel (-rt doesn't work!)

Grateful for any few scraps of information

---

### Post by tgalati4 on 2009-05-29
It's a challenge.  I have a Delta 66 card which uses envy24control.  M-Audio is decent quality for home recording.  Creating patches (linking inputs to output) is tricky.  You need different patch setups for recording, monitoring, and general computer use.

So yes, you can create a set of patches to use the semi-pro card for pc sound (with some alsa-base entries).  Switching back and forth from gaming to studio use is a mouse-click to select the required patch.

Jack adds another layer of complexity because now you need to set up application/device patches as well.

Most sound chips have multiple channels.  It requires trial and error to get applications to use channels other than default.  You need to consider software mixing vs on-chip mixing.

It's tricky but it can be done.  Post what works and what doesn't.

---

### Post by mrowth on 2009-05-30
> **tgalati4 said:**
> It's a challenge.  I have a Delta 66 card which uses envy24control.  M-Audio is decent quality for home recording.  Creating patches (linking inputs to output) is tricky.  You need different patch setups for recording, monitoring, and general computer use.

So yes, you can create a set of patches to use the semi-pro card for pc sound (with some alsa-base entries).  Switching back and forth from gaming to studio use is a mouse-click to select the required patch.

Jack adds another layer of complexity because now you need to set up application/device patches as well.

Most sound chips have multiple channels.  It requires trial and error to get applications to use channels other than default.  You need to consider software mixing vs on-chip mixing.

It's tricky but it can be done.  Post what works and what doesn't.

I'm ok with JACK (if it works).

I've been trying to familiarize myself with Pulseaudio just in case it'll become necessary. I have no idea if it will, only that everyone seems to be using it these days. I never have and so far it's been completely confusing.

I was hoping I could make Pulseaudio a JACK client with the JACK source and sink modules, but whatever should appear as a JACK output port (Readable client) vanishes before I can read the name. I can redirect JACK apps' audio to the "PulseAudio JACK source" input port, but that accomplishes nothing (no sound, either).

Then there're crashes, zombies processes, bumpy unpredictable volume sliders that sometimes seize control of Master volume and sometimes not. 

And I don't even know how to keep pulseaudio (and gconf-helper) from starting without uninstalling it. 

Too tired for the "10,000 pages" guide now.

---

### Post by tgalati4 on 2009-06-01
Both Jack and pulseaudio are sound server frameworks.  They may or may not play well together.  pulseaudio is difficult to remove in recent ubuntu releases as it is now the preferred audio framework for nearly all applicaitons under ubuntu.

For strictly audio session recording, I use a live CD called dynebolic (dynebolic.org).  This live CD saves "nests" as a single file on your system, which captures all of your user settings and work files.  This has the advantage of a real-time kernel, stripped down OS, jack and several audio applications.  When you are finished with your recording project, then you can boot back into ubuntu with pulseaudio and your normal desktop settings.

There are lots of posts about how buggy pulseaudio is, but it also seems to work well for a lot of people.  You can kill the pulseaudio server at bootup, but then many applications will need to be switched to alsa or oss to be heard.  Not difficult, just a pain.

---

### Post by mrowth on 2009-06-03
> **tgalati4 said:**
> Both Jack and pulseaudio are sound server frameworks.  They may or may not play well together.  pulseaudio is difficult to remove in recent ubuntu releases as it is now the preferred audio framework for nearly all applicaitons under ubuntu.

For strictly audio session recording, I use a live CD called dynebolic (dynebolic.org).  This live CD saves "nests" as a single file on your system, which captures all of your user settings and work files.  This has the advantage of a real-time kernel, stripped down OS, jack and several audio applications.  When you are finished with your recording project, then you can boot back into ubuntu with pulseaudio and your normal desktop settings.

There are lots of posts about how buggy pulseaudio is, but it also seems to work well for a lot of people.  You can kill the pulseaudio server at bootup, but then many applications will need to be switched to alsa or oss to be heard.  Not difficult, just a pain.
I always removed Pulseaudio more or less right away and only reinstalled it when I decided to try it out  - in case I might one day *have* to use it. 

Just plain ALSA has worked fine for me, with JACK "on top" if necessary. Maybe that's because I don't use GNOME (much). 

But since I have so little clarity, and since so many people - Kubuntu users included - complain they can only use sound in application 1 but not in application 2, or not at all, I'm worried this might be different with my future soundcard. 

So I thought if I could integrate Pulse as a JACK client into a JACK setup I wouldn't have to worry about JACK and Pulse conflicting because JACK alone would be in charge.

---

### Post by mrowth on 2009-06-03
How do I make the Pulseaudio server NOT START? It's disabled in my runlevel editor sysv-rc-conf. It seemed apps started it when they wanted to use it...? I'm not sure, but it popped back up even after I'd killed it for the 5th time. I don't want to kill, kill and re-kill it, or uninstall it every time I want it to leave me in peace. I guess I could rename the executable or make it non-executable... workarounds so stupid they must be unnecessary.

There's this: /etc/X11/Xsession.d/70pulseaudio
```
# If we are running the GNOME session, source ~/.gnomerc

if [ -x /usr/bin/pulse-session ]; then
        if [ "$BASESTARTUP" = gnome-session -o \
                \( "$BASESTARTUP" = x-session-manager -a \
                "`readlink /etc/alternatives/x-session-manager`" = \
                        /usr/bin/gnome-session \) ]; then
                STARTUP="/usr/bin/pulse-session $STARTUP"
        fi
fi
```
I don't understand all of that, but does it even apply when I run KDE?

Hm. A Gentoo user here blames kdeinit: [http://osdir.com/ml/kde-bugs-dist/2009-04/msg07935.html](http://osdir.com/ml/kde-bugs-dist/2009-04/msg07935.html).  "I removed the execution bit of /usr/bin/start-pulseaudio to workaround this bug." Heh.

---

