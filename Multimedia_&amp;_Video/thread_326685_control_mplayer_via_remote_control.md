---
title: "control mplayer via remote control"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by NT4usB on 2006-12-28
I have MthtTV working fine. 
Trying to get the Hauppauge gray remote to control volume when playing videos. I had it working for a little while... crs if it was before I updated to 0.20 or not.
The following commands work as they should (or as I have them configured)  for mplayer on the remote: 
back/exit, pause, SkipForward\Replay/SkipBackward (30 seconds), Skip\Replay (10 seconds), Mute, PrCh (fullscreen), Menu i (OSD).

Volume Up Volume Dn, Right\Left Up\Down, etc do not work.
Here's links to the various config files.

[http://home.pacbell.net/clayt/input.conf](http://home.pacbell.net/clayt/input.conf)
[http://home.pacbell.net/clayt/irwoutput.txt](http://home.pacbell.net/clayt/irwoutput.txt)
[http://home.pacbell.net/clayt/lircd.conf](http://home.pacbell.net/clayt/lircd.conf)
[http://home.pacbell.net/clayt/lircrc-haupgrey-g3.txt](http://home.pacbell.net/clayt/lircrc-haupgrey-g3.txt)

Any ideas which setting I have jacked up so the volume control won't work?

---

### Post by NT4usB on 2007-01-08
Anyone?

---

### Post by ebishop on 2007-04-26
I just looked at my lircrc file (which I haven't touched in a year or so).  It looks like I have 

    begin
            button = VOL_DOWN
            remote = rca        
            prog = mplayer
            config = VOLUME -1
            repeat = 1
    end

    begin
            button = VOL_UP
            remote = rca        
            prog = mplayer
            config = VOLUME 1
            repeat = 1
    end

try the config = VOLUME -1 & config = VOLUME 1

---

### Post by NT4usB on 2007-04-27
No joy...
Thanks for digging up the old post and the suggestion though!
For now, I've resigned to use the TV volume.
I'm sure that when/if I ever upgrade to Edgy or Feisty it will work again.

---

