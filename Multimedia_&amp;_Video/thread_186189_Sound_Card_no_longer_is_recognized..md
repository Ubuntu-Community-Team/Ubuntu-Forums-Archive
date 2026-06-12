---
title: "Sound Card no longer is recognized."
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by capi on 2006-06-01
Well, the sound card not being recognized is my guess at least. Nothing appears in System->Sound.

I'm getting the "No volume control GStreamer plugins and/or devices found." error for sound. I've tried the stuff in a couple other threads, but nothing has solved it thus far.

It was working before on breezy a little while ago, but then all of a sudden it just stopped(probably with an update I didn't notice). I updated to dapper, and nothing was fixed.

> 
$ cat /proc/asound/cards
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                     Intel 82801DB-ICH4 with ALC202 at 0xe8080c00, irq 209


and /etc/modrprobe.d/alsa-base is an empty file.

> 
$ sudo aptitude search libgstreamer
c   libgstreamer-gconf0.8-0         - GConf support for GStreamer
p   libgstreamer-gconf0.8-dev       - Development files for GConf support for GS
i A libgstreamer-plugins-base0.10-0 - GStreamer libraries from the "base" set
p   libgstreamer-plugins-base0.10-d - GStreamer development files for libraries
c   libgstreamer-plugins0.8-0       - Various GStreamer libraries and library pl
p   libgstreamer-plugins0.8-dev     - Development files for various GStreamer li
i A libgstreamer0.10-0              - Core GStreamer libraries and elements
i   libgstreamer0.10-0-dbg          - Core GStreamer libraries and elements
i   libgstreamer0.10-dev            - GStreamer core development files
i   libgstreamer0.8-0               - Core GStreamer libraries, plugins, and uti
p   libgstreamer0.8-dev             - GStreamer development libraries and header
p   libgstreamer0.8-ruby            - GStreamer 0.8 bindings for the Ruby langua


---

### Post by JGKC9AYC on 2006-06-01
I can't help you, but if it's any consolation, i'm getting the same message as well after I did an upgrade.  
I'm also without a display.  If I didn't have Breezy still on my system I would be here as my Windows XP was taken off grub.

---

### Post by georgevn on 2006-06-02
i'm also experiencing the same problem. Sound was ok with Breezy but now not available in Dapper even though both 2 my  sound cards are recognized, previously only creative, but realtek, was seen.
can someone help me with that?

ps: everything is nice withh Dapper other than above problem, thank all you guys

---

### Post by ktulu1115 on 2006-06-05
Same problem here.  My sound got hosed when I added totem-xine (which removed totem-gstreamer).

You can check out my thread here: [http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

---

### Post by capi on 2006-06-09
My solution can be found here. . .

[http://www.ubuntuforums.org/showthread.php?t=188872](http://www.ubuntuforums.org/showthread.php?t=188872)

---

