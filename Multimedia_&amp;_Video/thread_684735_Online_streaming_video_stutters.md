---
title: "Online streaming video stutters"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by VMOS on 2008-02-01
I've been scratching my head over this for a while and looked about but not seen this issue mentioned elsewhere or any solutions that actually work

When watching streaming video online, be it youtube, google, videojug, in fact any website that has any kind of flash video player things, the video will play along and at some point the picture will freeze and the sound will replay the same half second over and over like a broken record, this will last between 3 and 10 seconds and then the picture and sound will carry on having skipped the time that it was juddering (so if it judders for 10 seconds I miss out 10 seconds of action)
actually now that I think about it I'm not certain this si limited to flash video, but you don't seem to see much other kinds these days but hey

now here;s what's really baffling me, I uninstalled everything that mentioned "flash" went right through synaptic and still all the flash stuff is there, I uninstalled most stuff that mentioned "stream" and reinstalled anything that was listed as essential

that seemed to cure the problem but bam, 5 videos later, there it was again, it doesn't happen if I watch a movie in vlc or something, but it happens in pretty much every video I watch online, it might happen once, it might happen a dozen times and it's really beginning to piss me off

any suggestions?

---

### Post by ubuntu-freak on 2008-02-02
Just a long shot, but some said my [how-to](http://ubuntuforums.org/showthread.php?t=661833) cured some problems. You might be missing a certain package.
 
Nathan

---

### Post by VMOS on 2008-03-11
sorry for not replying sooner, I've been away a while.

thanks mr offensive, but that didn't work.
I removed all flash plugins and codecs and started from scratch, I tried gnash. It doesn't seem to stutter, however it does run like a dead dog and doesn't display a lot of stuff properly.
So I removed that and stuck in adboe flash, and the problem's back again.

Incidentally I'm using gstreamer codec if that makes any difference

---

### Post by ubuntu-freak on 2008-03-11
Did you try my troubleshooting section and edit Firefox's configuration? Are you running a 32-Bit Ubuntu or 64-Bit?
 
Nathan

---

### Post by VMOS on 2008-03-11
yeah, tried the relevant troubleshooting, including a different mplayer driver, also tried firefox 3 just in case, no change.
I'm on 32 bit ubuntu

---

### Post by ubuntu-freak on 2008-03-12
> **VMOS said:**
> yeah, tried the relevant troubleshooting, including a different mplayer driver, also tried firefox 3 just in case, no change.
I'm on 32 bit ubuntu

 
Uninstall flashplugin-nonfree and[ try this older version](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.48.0.0ubuntu1~7.04.1_i386.deb). I don't think it has the checksum error, but if it does, try [installing flash manually](http://www.psychocats.net/ubuntu/flashmanual) (not my page, saw it posted by forum staff member aysiu).  
 
Hope those suggestions help you.
 
Nathan

---

### Post by mathomas3 on 2008-03-20
did this work for you?

---

