---
title: "mplayer with vdpau needs &quot;reset&quot;"
date: 2010-12-12
forum: Multimedia Software
---

### Post by beew on 2010-12-12
Hi,

I am using mplayer with vdpau enabled in Ubuntu 10.10. It works very well in general, reducing cpu usage for hd from 50% to 60% to around 10 -15% or less. There is however one slightly annoying problem. It is that mplayer would appear to "forget" its vdpau output setting once in a while and especially after rebooting. When that happens it needs to be "reset" in order to use vdpau. "Resetting" basically just means opening gnome-mplayer and change video output to xv and then back to vdpau again (Edit: I should clarify that the setting has not actually been lost, it still says "vdpau", it just need resetting). 

It is not a big deal but still kind of annoying. I wonder if this is a known bug and if there is a way to work around it.

Thanks.

---

### Post by Regnix on 2011-05-07
I have this same problem, Ubuntu 10.10 with Gnome MPlayer.

---

### Post by beew on 2011-05-07
Actually that problem has disappeared long time ago for me. Now mplayer works flawlessly with VDPAU. Maybe because I have stopped using Ubuntu's version of mplayer and installed the up to date version from a ppa instead.

This is the ppa I use
[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc") 

I don't use coreavc, just install the player. Hope that helps.

P.S. Sorry, just reread my own thread. The problem was with gnome-mplayer (th front end) but not mplayer itself. Smplayer and Umplayer (and mplayer on the terminal ) all work fine. Recently a new issue arise, gnome-mplayer appears to have stopped working at all unless I leave the video output box blank, in particular can't set output to vdpau (or xv for that matter) I only need gnome-mplayer for the gecko-mplayer plugin, otherwise I would just use Umplayer, which is a much better front end for mplayer anyway.

---

