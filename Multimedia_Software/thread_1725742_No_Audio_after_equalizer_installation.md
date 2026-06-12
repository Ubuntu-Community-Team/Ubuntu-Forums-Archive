---
title: "No Audio after equalizer installation"
date: 2011-04-10
forum: Multimedia Software
---

### Post by kawaiipikachu on 2011-04-10
After following instructions in [this]("http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/") page I found I got *mostly* no audio.
the sound test within system/preference/sound works but Youtube, Movie player, sidplay & rhythm box won't play audio.

Then I noticed the first comment on the page for which i quote below
> To make it work in Meerkat:

1. Follow all the steps described above

2. Edit psyke83-ppa-maverick.list and
change &#8220;maverick&#8221; to &#8220;lucid&#8221; in both of the two lines

$ sudo pico /etc/apt/sources.list.d/psyke83-ppa-maverick.list

3. Copy the missing icon

$ sudo cp /usr/share/icons/Humanity/apps/16/gnome-volume-control.svg /usr/share/icons/hicolor/16×16/apps/gnome-volume-control.svg

So I followed these new instructions

Followed step 2 fine but step 3 it came up with this message 
> cp: cannot create regular file `/usr/share/icons/hicolor/16×16/apps/gnome-volume-control.svg': No such file or directory

And it still didn't work

I need help in fixing it or reversing the changes.

**edit**
I just extracted info about my soundcard if it helps

> 00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Elitegroup Computer Systems Device 0a44
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at d800 [size=256]
        I/O ports at dc00 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0


---

### Post by kawaiipikachu on 2011-04-13
**_*Update***_
Update I tried various tricks after an online search but I'm halfway fixing it but not fully.

I haven't realized I actually did a partial fix until I stumbled upon a flash site.

Things that fixed are Flash including You tube Video player & Rythimbox but things that still don't work are System sounds (e.g. startup & alerts) some applications including simutrans don't have audio working.
 
If I go into the System Preference Sound It comes up with a message saying "Waiting for sound system" & just hangs there.

Any solutins?

---

