---
title: "DVD playback problems"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by Elim on 2007-02-22
Hello, I've got a fairly new install of Dapper (with codecs and libdvdcss installed) and I just tried to play DVDs on it.  It didn't work.  Here's what happened:

1.) VLC

When I select File --> Open Disc..., VLC will *not* play the disc.  When I use mplayer to dump the stream to my hdd and play the .vob file, it works just fine.  Hmmm...


2.) TOTEM

When I insert a DVD, Totem automatically responds:

"Totem could not play 'dvd:///mnt/cdrom'.
No URI handler implemented for "dvd"."

When I select Movie ==> Play Disc:

"Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
Please install the necessary plugins and restart Totem to be able to play this media."

I have installed: totem, totem-gstreamer, gstreamer0.10-ffmpeg, gstreamer0.10-plugins-base, gstreamer0.10-plugins-good, gstreamer0.10-tools, gstreamer0.10-x


Any help is greatly appreciated.  Thanks for your time.

---

### Post by josesanders on 2007-02-22
I can never get the players to work initially, but I've had a lot of success with Automatix:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

It will install for you all of the needed codecs, players, etc.  I don't know why it isn't in the repos.

---

### Post by Toddy on 2007-02-22
Hi Elim.  You will want to refer to this page: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by RomeReactor on 2007-02-22
I'll just throw in my opinion here. Gstreamer can't handle most DVD's as of yet; you're better off installing Totem-Xine and Libxine-Extracodecs, which will let you watch DVD's with Totem. Look for the codecs in Synaptic, or in a terminal

```
sudo apt-get install totem-xine libxine-extracodecs
```

---

### Post by Elim on 2007-02-22
> **Toddy said:**
> Hi Elim.  You will want to refer to this page: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Thanks, I've been there already.  I don't think it's a codec problem for two reasons.  One, VLC comes with all its own codecs.  Two, I have gstreamer-ffmpeg installed, which handles most of the codecs that you would need.  So I'd have to assume that the problem is the drive or something like that.

(I can play DVDs fine using VLC in Windows, so I know the drive isn't outright defective or anything like that.)

---

### Post by Elim on 2007-02-22
> **RomeReactor said:**
> I'll just throw in my opinion here. Gstreamer can't handle most DVD's as of yet; you're better off installing Totem-Xine and Libxine-Extracodecs, which will let you watch DVD's with Totem. Look for the codecs in Synaptic, or in a terminal

```
sudo apt-get install totem-xine libxine-extracodecs
```

Hmm.  Can I install Totem-Xine alongside Totem-Gstreamer, or do I need to uninstall the latter first?  Any idea why VLC won't work?  I'm rather attached to VLC...

---

### Post by RomeReactor on 2007-02-22
Installing one automatically uninstalls the other, though the codecs themselves remain installed, so if you install Totem-Xine it will uninstall Totem-Gstreamer, but all of the Gstreamer codecs will remain installed for other applications to use (such as Rhythmbox).

---

### Post by Elim on 2007-02-22
Well, RomeReactor, you were quite right--Totem-xine quickly and easily solved that problem, so I guess it's xine for me!  Unfortunately, VLC is still dead, and I'm very attached to it!  Someone suggested running it from the console to see the output; vlc dvd:// gives the following:

```

VLC media player 0.8.4 Janus
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Can't stat
No such file or directory
libdvdnav: vm: faild to open/read the DVD
libdvdread: Can't stat
No such file or directory
[00000271] dvdread demuxer error: DVDRead cannot open source:
ioctl(): Input/output error
[00000274] vcdx access error: error reading Info sector (150)
[00000270] main input error: no suitable access module for `dvd://'
[00000261] main playlist: nothing to play
[00000261] main playlist: stopping playback

```

I don't suppose that illuminates anything?  Cheers.

---

### Post by RomeReactor on 2007-02-22
I haven't used VLC since Breezy, i think, and don't have it installed right now, but try this: Open Nautilus and go to **Computer** and then enter the **media** folder. you should have shortcuts there for your optical drives; now open VLC, and see if under the **File** tab there's something like **Open Location**. If there is, write

```
/media/cdrom
```

or any of the shortcuts you saw in the media folder.

---

### Post by Elim on 2007-02-23
RomeReactor, you're my new hero.  It worked perfectly--Open directory, /mnt/cdrom/video_ts.  Brilliant!  Thank you very much, kind sir!

---

### Post by ramasdf123 on 2007-10-22
I am having the same problem still. and i dont like using other software unless i have to.

---

