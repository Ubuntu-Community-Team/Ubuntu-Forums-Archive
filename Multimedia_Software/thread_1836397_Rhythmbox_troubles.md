---
title: "Rhythmbox troubles"
date: 2011-08-31
forum: Multimedia Software
---

### Post by G_khan on 2011-08-31
Hello all,

This is my first post so be merciful.  Also I am a newb.  I've been searching for a solution on google and start page for a couple days now and have not found a solution. Now, the problem I am having is that rhythmbox will not play certain tracks all the way.  It'll freeze up and the red sign with the white line through it appears next to the track.  I immediately change the track so that I won't have to force quit and restart it and have to wait a few minutes to be able to play tracks.  I started rhythmbox via the terminal and this is what appears:
   
** (rhythmbox:5480): DEBUG: Loading the real store page
** (rhythmbox:5480): DEBUG: navigation requested to [https://one.ubuntu.com/music/store-no-token](https://one.ubuntu.com/music/store-no-token)
** (rhythmbox:5480): DEBUG: navigation requested to file:///usr/share/libubuntuone/1/javascript/load_error.html?[https://one.ubuntu.com/music/store-no-token](https://one.ubuntu.com/music/store-no-token)
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|Windows Media Audio decoder|decoder-audio/x-wma, wmaversion=(int)4, bitrate=(int)1152000
Rhythmbox-Message: Automatic missing codec installation not supported (helper script missing)

(rhythmbox:5480): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

(rhythmbox:5480): Rhythmbox-CRITICAL **: playing_stream_cb: assertion `entry != NULL' failed

The last two messages appeared when I played a track and froze up after a minute or so.  I ran this command:

sudo apt-get remove rhythmbox-ubuntuone-music-store

I opened rhythmbox via the terminal again and I got the same output minus the first three lines.  I am dual booting Ubuntu lucid lynx with windows 7 on a toshiba a665-s6050.  I'd remove the windows 7 part of it but I'm not sure how without having to reinstall lucid.  But that's a problem to solve some other time.  

Any help will be very much appreciated and thanks in advance.

---

### Post by Steeperton on 2011-08-31
have you tried:

```
sudo apt-get install ubuntu-restricted-extras
``` ?

---

### Post by garvinrick4 on 2011-08-31
In ubuntu software center here is all your codec's gstreamer. Type gstreamer in search box
and hit enter. Install. 
Many ways to install this is one and lets you see the packages you need.

---

### Post by G_khan on 2011-08-31
@Steeperton:
I ran the code in the terminal and this is the output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  rpm2cpio librpmbuild0 librpmio0 librpm0 rpm-common python-rpm rpm
  python-sqlite python-sqlitecachec python-urlgrabber
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

So it looks like I already had that package.  I don't really understand the last bit of it about removing those packages.  Does that mean I don't need them?  That's probably going off subject here so I'll probably look into it later.  

@garvinrick4:
Is there a specific package I should download or should I just download all of 'em?  I've searched in the synaptic manager also, by the way, for any package, with gstreamer of course, that has to do with wma files specifically that wasn't already installed. In fact, the only such package is called "GStreamer plugin for using MS Windows binary codecs" (I searched "gstreamer windows" on that one and with "gstreamer wma" I got nothing).

---

### Post by Steeperton on 2011-08-31
Are they lossless or DRM/protected wma? I get the feeling that rhythmbox/Linux won't play them at all. You may have to convert them to something a bit more standard instead :(

---

### Post by G_khan on 2011-08-31
Oh yeah.  I remember doing that for a few tracks a couple months back.  But given that it might be for over 500 songs I hesitate to do it.  Damn windows.  Oh well.  Seems to be the only working solution at this point.  Thanks a lot.

---

