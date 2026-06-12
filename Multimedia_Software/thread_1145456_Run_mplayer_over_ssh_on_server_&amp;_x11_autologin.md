---
title: "Run mplayer over ssh on server &amp; x11 autologin"
date: 2009-05-01
forum: Multimedia Software
---

### Post by darkscout on 2009-05-01
I would like to run mplayer over ssh, from my laptop to my desktop, to watch movies on my TV. I currently have an XBMC on an old XBOX which is showing its age, doesn't do high res and is probably going to live at my girlfriends for now. I ended up buying an [Asus M3N78 Pro w/HDMI]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131320") and I'm using an [Athalon X2 2.1GHz Dual Core]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103672").

For this setup I would like to call mplayer from ssh and have it run on my TV....
How do I play mplayer on my main monitor initiating the command via SSH. I've searched[0] and had limited success with ssh -X. DISPLAY=:0.0. mplayer -vo X11 Movie.avi

1) However, this doesn't seem to work in a screen session. I'd like to be able to detach/reattach control of the movie playback.
1a) I haven't tried this within function either, not sure if it'll like it. I plan on making a script that configures all of my mplayer settings (-vo to VDPAU and -ao to my HDMI) etc.
2) I'd like to be able to do this without -X. It seems to be an Xauth thing.
2a) I'd like to avoid having to do the display=:0.0, although I could toss it in the script if it works.
3) I'd like to autologin and drop into startx upon boot. Not as big of a priority since on my current server uptimes are in the months. I could always break out the keyboard and do initial login. I don't have any windowmanager installed, just a straight apt-get install xorg. Startx drops you straight into a terminal, albiet with fancy fonts and scaled to the screen.
4) Is there any vast improvement I would notice with 64bit? I'm looking at either Ubuntu Server or Debian Testing/Unstable.

Backstory: I originally planned on just installing XBMC, however its complete overkill for me. I only control XBMC through the web interface, I never use it for anything other than playing TV/Movies. I don't need this to pass any useability tests to anyone but myself, so I'm thinking of going with a plain mplayer setup. I'm a commandline junkie and when ever I watch movies with OS X it's always 'mplayer -ontop [-cache 10240]' in Terminal rather than a gui.

[0]A few unresolved threads:
[http://ubuntuforums.org/showthread.php?t=953605](http://ubuntuforums.org/showthread.php?t=953605)
[http://ubuntuforums.org/showthread.php?t=56107](http://ubuntuforums.org/showthread.php?t=56107)
[http://ubuntuforums.org/showthread.php?t=180991](http://ubuntuforums.org/showthread.php?t=180991)
[http://ubuntuforums.org/showthread.php?t=111963](http://ubuntuforums.org/showthread.php?t=111963)

---

### Post by darkscout on 2009-05-04
Well I spent all weekend on this... hurray for up to date man pages.

~/.mplayer/config
```

# Write your default config options here!
fs=yes
zoom=yes
cache=10240
vo=vdpau
display=:0.0

```

I couldn't get auto login working using both of the most popular methods so I just changed in /etc/X11/Xwrapper.config
```
#allowed_users=console
allowed_users=anybody

```

so I can run startx from ssh. I also had to do some xset stuff to turn off screen blanking.

Other major hurdle was getting sound working, for some reason audio over HDMI is muted by default. I went through alsamixer and cranked all the volumes up but didn't notice the little "MM" at the bottom, once I did, all good.

Last minor thing was for vdpau to work you have to specify -vc (even if you already have -vo as vdpau). WALL-E 1080p with 3-4% cpu is awesome. I played the 'killa sample' (the one that the XBMC guys use to benchmark how well stuff is working) with no problem.

---

