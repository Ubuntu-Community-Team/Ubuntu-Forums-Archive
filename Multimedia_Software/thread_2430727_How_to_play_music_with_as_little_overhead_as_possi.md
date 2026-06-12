---
title: "How to play music with as little overhead as possible?"
date: 2019-11-06
forum: Multimedia Software
---

### Post by strapped on 2019-11-06
Every post about DJ'ing refers to MIXXX or running one of the commercial apps in a simulator.
My quest is different.
I want to take two EEE netbooks (with the ATOM chip) and use them as "turntables."
Attach a USB drive to each one with a complete catalog of identical tunes.
Attach a low cost USB sound card (like the TOPPING D30 or similar) and use VLC or similar to actually play the music.

How much could be stripped out of Ubuntu or another OS for this strict function?
Networking would never be used.

Keeping the heat down and taxing the ATOM chip as little as possible would be the key.

Anyone have ideas?

Anyone interested in doing a stripped-down ultra solid package for netbooks for this purpose?
(10 inch screens with a Solid state drive make them perfect for this use as long as you could keep the overhead down)

---

### Post by uRock on 2019-11-06
I have an Asus Netbook. Mine is 32bit. If your's is 32bit as well, then you may want to look into Debian 10 with LXDE as the desktop. I use Audacious as the music player, which seems to have little overhead.

---

### Post by TheFu on 2019-11-06
The title threw me off - came here to say use **cmus** for the lightest music player possible. No GUI required, which will drastically drop the overhead.  If you don't actually need a GUI, dropping that will let cheaper computers work for any need.

As for the rest of the post - I haven't a clue.  Atom is overkill for music playback.  I'd get an SBC (rock64 or other ARM CPU) with a quality hifi audio head for silent playback.

---

### Post by strapped on 2019-11-06
MUST have a GUI.
No question about that.
I would just like to remove all non-essential stuff.
We had a Netbook running "wattOS" and it FLEW compared to Windows (or straight Ubuntu)
It would be nice to have a one-purpose twin laptop setup.
Basically, making them strictly digital turntables. No networking, no updates, no nothing but the needed components for playing music from a USB source/drive/stick.
Ras-pie would be more hassle than worthwhile, since the setup would need a monitor anyway.
(I already have the netbooks and the USB drives.)

---

### Post by Skaperen on 2019-11-06
the actual sound part is trivial.  i did something like this with a ASUS EEE netbook a few years ago to play Christmas music at church.  but i didn't use any GUI.  it was desktop Ubuntu, i think 10.04, started without GUI, activating 12 text consoles.  was never stressing the CPU to play music. it ran about 8%  an SSD is the way to go for music playback.  all my music was on a couple SD cards but USB memory sticks worked just as well.

GUI could be problematic.  use the lightest GUI you can or learn shell commandeering.

---

### Post by strapped on 2019-11-08
One of the netbooks is a EEE!
1015 or something like that.
The one with the monster battery that cost $400 when it first came out.
I might try an old version of "wattOS" and see how that works.

---

### Post by Holger_Gehrke on 2019-11-08
Instead of using Ubuntu and trying to strip it down, I'd go with one of the minimal distributions - probably Tiny Core since I've used it before (on a Wyse Thin Client with a 100MB Disk on Module as it's only drive; had lots of space left over to install some packages, base system uses something like 16MB including a GUI) - and built up from that. A lot of music players are available as tcz-packages (just at a glance at the repository I saw audacious, rhythmbox, vlc, cmus, mpd (server) and mpc (client) ...

Holger

---

