---
title: "DVD to mpeg2"
date: 2009-02-22
forum: Multimedia Software
---

### Post by xlr8ed on 2009-02-22
Does anyone know a good and easy way to rip straight from DVD to mpeg2? Handbreak works great for mpeg4, but that just doesn't work for what I am doing, and I can't locate a guide that walks me through for mpeg2. 

Any help would be appreciated.
Thanks

p.s. CLI only, I'm running this all though SSH to a Ubuntu server.

---

### Post by graysky on 2009-02-22
```
$ sudo aptitude install dvdrip
$ sudo aptitude install libdvdread3
$ sudo /usr/share/doc/libdvdread3/install-css.sh
```

Now simply load dvd::rip from Application>Sound & Video.

EDIT - ack, just realized you're doing this from an ssh session.  Can you install/use vnc4server on the box?  If you can, do it.  You can either use it unencrypted or through an ssh tunnel.

[HOWTO: Run vnc4server for totally parallel sessions to X](http://forums.debian.net/viewtopic.php?t=31848).
[HOWTO: Secure vnc or apache, etc. via ssh tunnels](http://knoppmyth.net/phpBB2/viewtopic.php?t=19211).

---

### Post by xlr8ed on 2009-02-22
> **graysky said:**
> ```
$ sudo aptitude install dvdrip
$ sudo aptitude install libdvdread3
$ sudo /usr/share/doc/libdvdread3/install-css.sh
```

Now simply load dvd::rip from Application>Sound & Video.

My edit didn't beat your post...

"p.s. CLI only, I'm running this all though SSH to a Ubuntu server."

---

### Post by graysky on 2009-02-22
I re-edtied my post with a suggestion :)

---

### Post by xlr8ed on 2009-02-22
> **graysky said:**
> ```
$ sudo aptitude install dvdrip
$ sudo aptitude install libdvdread3
$ sudo /usr/share/doc/libdvdread3/install-css.sh
```

Now simply load dvd::rip from Application>Sound & Video.

EDIT - ack, just realized you're doing this from an ssh session.  Can you install/use vnc4server on the box?  If you can, do it.  You can either use it unencrypted or through an ssh tunnel.

[HOWTO: Run vnc4server for totally parallel sessions to X](http://forums.debian.net/viewtopic.php?t=31848).
[HOWTO: Secure vnc or apache, etc. via ssh tunnels](http://knoppmyth.net/phpBB2/viewtopic.php?t=19211).

I have no GUI on my server and would really prefer not to install one. If I have to transcode in a GUI, I would just use my windows box, but that kinda defeats the purpose of doing it all on my Linux server

---

### Post by mc4man on 2009-02-22
When you say 'mpeg2' what are you looking for? One big file or to rip to DVD VIDEO format? (VIDEO_TS

Certainly transcode or vobcopy could suit your intended purpose.

For vobcopy in mirror mode (VIDEO_TS), if desired, you could create a simple script and set it to the auto run event for dvd insertion. Then you'd simply insert a disk(s) and it would be auto ripped. (works with multiple drives at same time

(with any method you would need to take into account titles with structure protection if you have any
(there may be a cli method in those cases, would need to experiment

Edit : forget the auto run, you'd probably need a gui to use the event.

---

### Post by xlr8ed on 2009-02-22
> **mc4man said:**
> When you say 'mpeg2' what are you looking for? One big file or to rip to DVD VIDEO format? (VIDEO_TS

Certainly transcode or vobcopy could suit your intended purpose.

For vobcopy in mirror mode (VIDEO_TS), if desired, you could create a simple script and set it to the auto run event for dvd insertion. Then you'd simply insert a disk(s) and it would be auto ripped. (works with multiple drives at same time

(with any method you would need to take into account titles with structure protection if you have any
(there may be a cli method in those cases, would need to experiment

Uhhh, not super good with video encoding.

I just want to rip a dvd to a .mpg with the mpeg2 codec, and I just want the movie and audio. I've done it in Windows, but I don't know what software or commands to do in in Ubuntu in a CLI. Hoping that this will give me a single file around a GB

---

### Post by FakeOutdoorsman on 2009-02-23
The VOB files in the VIDEO_TS directory on the DVD as mc4man mentioned contain mpeg2 encoded video.  Try just copying them (perhaps with vobcopy if needed) and renaming them to .mpg.  If it works, no encoding needed.

---

### Post by mc4man on 2009-02-23
I'm not sure what you where doing in windows but there is no way to re encode a DVD movie (mpeg2) to 1 Gb or so using mpeg2.
Even when using top quality encoders (CCE, procoder, hcenc) along with bitrate reallocation, aqm, ect. you *may* be able to get acceptable results at around 40% reduction (60% of orig. size
Anything more is really pushing it and depends on the orig. quality, bitrate, and source type (action vs. a lot of static scenes.

Sounds like your needing to encode to h.264, I sure someone here can give you a command line or script.

An interesting cli interactive shell script can be found here, (3 variations, h264, xvid, divx
[http://forum.doom9.org/showthread.php?t=134652](http://forum.doom9.org/showthread.php?t=134652)

At worst it can help you learn the setting (export the commands to text file to look thru

---

