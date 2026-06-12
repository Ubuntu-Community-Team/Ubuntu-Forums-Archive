---
title: "Gutsy XVideo broken"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by Kakihara on 2007-10-20
I just upgraded to gutsy and found my xvideo rendering broken. When playing video, i only get moving colorful vertical lines on output. This affects each player which uses xv output (mplayer, vlc, totem).
I can use mplayer -vo x11 , which doesn't play fullscreen + i really want my XVideo fixed.
My gfx card is ATI Radeon X200M and i don't use fglrx now(will try later). /var/log/Xorg.0.log shows XVideo extension succesfully loaded.
I had to delete /etc/X11/xorg.conf, to get my xserver working after upgrade.
Any hints?

---

### Post by mikeh on 2007-10-24
Similar problem. Playing video with Xv just gives a blue window for me.
Thinkpad X23, radeon mobility M6. just "radeon" driver.

You can try software scaling in mplayer to get fullscreen, e.g. "mplayer -vo x11 -vf scale=1024:-2 ..."

Worse is that suspend/hibernate is broken. Back to Feisty on the laptop for me.

---

### Post by gatman3 on 2007-10-25
Same here on my Radeon 200M based laptop.  I'm using fglrx, and it loads successfully from the restricted driver option, but no Xv.  This worked in Feisty.  Anyone have any ideas?  I'm thinking about trying the new ATI 8.42 driver, but I have read a lot of horror stories with that as well... so basically I'm just shooting in the dark.

---

### Post by gatman3 on 2007-10-25
Well, I just solved my problem:

sudo aticonfig --overlay-type=Xv

did the trick.  Funny, I don't remember doing that in Feisty, but it's been a while.  Now Xv is working and mplayer is smooth as silk.

---

### Post by haralf on 2007-10-26
Same problem on my machine.
Reconfiguring the X-Server using
sudo dpkg-reconfigure xserver-xorg
helped for me.

Good luck,

  Haralf

---

### Post by Kakihara on 2007-10-26
latest fglrx driver solved the problem for me though being a bit unstable

but definitely something is rotten in the new xorg radeon driver..

---

### Post by dstromberg on 2008-01-01
I managed to work around my Laptop's apparent lack of XVideo (It seems to be there, but gives blue windows), in a manner detailed [here]("http://stromberg.dnsalias.org/~dstromberg/mplayer-without-xvideo.html").  The gist is I turned on some options to make decoding faster, and used sdl without hardware acceleration, or svgalib.

---

