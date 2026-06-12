---
title: "Upgraded to Flash 9 in Firefox 2 on Dapper. Problems"
date: 2006-12-07
forum: Multimedia &amp; Video
---

### Post by Statik on 2006-12-07
Hi all,

Like most of you, I got the update to the flash9 plugin earlier this week so I tried a couple of sites. I'm using Firefox2 in Dapper and I'm running into troubles. They are:
1. No sound in anything Flash based online.
2. Cannot browse away from the page, or enter new URLs.
3. Need to close and restart Firefox to go anywhere else.

Websites I've tried this with:
[http://forces.ca](http://forces.ca)
[http://video.google.ca](http://video.google.ca)
[http://www.youtube.com](http://www.youtube.com)

Anyone have a solution?

Thanks in advance,
Statik

---

### Post by DX 00 on 2006-12-07
I got it to work by installing firefox2 using this directions:
[http://www.ubuntuforums.org/showthre...stall+firefox2](http://www.ubuntuforums.org/showthre...stall+firefox2)

and then downloading the flash player from here 
[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)
and following the instructions on the readme file.

Look at this Thread for more help:
[http://www.ubuntuforums.org/showthread.php?t=303031&highlight=install+flash9](http://www.ubuntuforums.org/showthread.php?t=303031&highlight=install+flash9)

---

### Post by Statik on 2006-12-08
I've followed the instructios and still nothing. Sound is not present and firefox becomes unresponsive. If I manage to close it, it goes to a sleeping or zombie process. Also, the next time I start it I get the restore session prompt.

Firefox 2 seemed to be working fine before the flash9 upgrade. I'm wondering if there is something in my Ubuntu setup for sound that is causing the trouble.

Firefox reports itself as:
Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.1) Gecko/20061010 Firefox/2.0

Flash reports itself as:
You have version 9,0,21,78 installed

](*,) 

Statik

---

### Post by Statik on 2006-12-12
Still nothing. I've tried all the solutions in [this]("http://ubuntuforums.org/showthread.php?t=255422&page=8&highlight=howto+fix+flash+firefox") thread as well, to no avail. There is simply no sound.

Statik

---

### Post by Statik on 2007-01-05
well, I played around a bit, uninstalling and reinstalling everything (firefox 1.5 and 2.0 as well as flash). Still nothing.

I did get this error tho:
```
statik@statik-main:~$ aoss firefox
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_direct.c:185:(make_local_socket) socket failed: Too many open filesALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card

(Gecko:25063): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWidget'

(Gecko:25063): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(Gecko:25063): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed
/opt/firefox/run-mozilla.sh: line 131: 25063 Segmentation fault      "$prog" ${1+"$@"}

```

Any ideas?

Statik

---

### Post by Statik on 2007-01-21
well, I've fixed the problem . . . but in a rather extreme way. While working on installing cinelerra, I had to install some extra packages, which broke other packages in a way I couldn't fix. Finally, in frustration, I did the upgrade to Edgy. Guess what? Flash now has sound!

Ah well. At least in the end the results are the same.

Statik

---

### Post by ChrisC on 2007-01-29
Upgrading the entire OS to fix the problem?  Yecch.

I'm patiently waiting for Flash 9 to appear in the repositories as a clean update for Dapper.  Is this ever going to happen?  The Edgy-package/backports-package solution sounds messy.

I'm trying to keep everything on my system within the apt/Synaptic mechanism, which is why I'm trying to avoid the manual solution described at [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) .

I searched the forums first, will try posting here first, and then will open a new thread. Any idea if work is underway to officially bring Flash 9 to Dapper?

---

