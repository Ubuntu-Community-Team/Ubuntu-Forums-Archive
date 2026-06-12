---
title: "Ubuntu video blues"
date: 2008-11-01
forum: Multimedia Software
---

### Post by craigni on 2008-11-01
I'm in the process of migrating from fedora to ubuntu, and much is better in ubuntu.  One thing that at first glance appears to be better in fedora is DVD support.

I'm running 64 bit 8.04 LTS on an Intel Quad, 8 GB RAM and NVidia GeForce 8800GTX.

I've installed 64 bit video codes and VLC with

```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update
sudo apt-get install w64codecs libdvdcss2
sudo apt-get install mozilla-mplayer
sudo apt-get install vlc

```

Here are my problems:
1. Totem does not bring up a menu, and often jumps into the "commentary" track of a DVD.  I haven't figured out how to play the actual movie for these DVDs.
2. VLC plays some videos in the wrong color--skin tones are very blue.

Any ideas how to fix these, especially the blue hue problem?

Many TIA,
Craig

---

### Post by gandaran on 2008-11-01
for the video color try changing the video driver/output in mplayer or vlc preferences to x11, xv or any other, but first try setting the color in totem preferences » screen tab
totem-gstreamer doesn't support DVD's menus only totem-xine can do that

---

### Post by craigni on 2008-11-01
Thanks!  I have a menu working with totem-xine -- much appreciated.

Any idea why two totem windows spring to life when I insert a DVD?  Very annoying...  Any idea how to get totem-xine or VLC to automatically play a DVD when inserted instead of totem?

Hue doesn't seem to work at all in totem-xine video preferences.

> video driver/output in mplayer or vlc preferences to x11, xv or any other, but first try setting the color in totem preferences » screen tab

Tried all sorts of things, and everything is still blue... in totem-xine and VLC.  Any ideas?

---

### Post by gandaran on 2008-11-01
> Any idea why two totem windows spring to life when I insert a DVD? Very annoying... Any idea how to get totem-xine or VLC to automatically play a DVD when inserted instead of totem?
you didn't remove totem-gstreamer? it would be better, maybe they conflict
to set the player to open a dvd go to nautilus » edit » preferences » media tab
> Tried all sorts of things, and everything is still blue... in totem-xine and VLC. Any ideas?
sorry no more ideas! or try  disabling special effects if you running compiz

---

### Post by craigni on 2008-11-01
Weeeeird.  It's working now.  About all I did was install libxine1-ffmpeg and nvidia-settings, mainly out of desperation.  I then opened totem-gstreamer, and noticed that the hue button actually works now, cranked it all the way over to the right, and hues were OK.  I then closed totem-gstreamer, opened totem-xine, and with the hue slider in the center, hues are OK.  I have no idea what solved the problem, if anything other than demons leaving the computer.

Again, many thanks,
Craig

---

### Post by Portable_Jim on 2008-11-22
> **craigni said:**
> Thanks!  I have a menu working with totem-xine -- much appreciated.

Any idea why two totem windows spring to life when I insert a DVD?  Very annoying...  Any idea how to get totem-xine or VLC to automatically play a DVD when inserted instead of totem?

Hue doesn't seem to work at all in totem-xine video preferences.



Tried all sorts of things, and everything is still blue... in totem-xine and VLC.  Any ideas?
I have created a tutorial on how to fix the hue: [http://portablejim.site-hosts.net/Problems-and-Solutions/Hue-wrong-in-videos.html](http://portablejim.site-hosts.net/Problems-and-Solutions/Hue-wrong-in-videos.html)

---

### Post by mattycoze on 2008-11-26
Hey there

While I found that editing the gstreamer-properties box was useful for fixing videos in Totem Movie Player, when it came to watching DVD's the blue-video problem persisted in VLC player and gxine. I found (by chance) that if you go into the video output properties of VLC; tools => Preferences => Video Output => Select "X11 Video Output" => Save => Restart VLC 

And I can watch my DVD's in perfect colour again! 

It seems like just a patch-solution to a bigger problem though... I'm really no expert...

---

