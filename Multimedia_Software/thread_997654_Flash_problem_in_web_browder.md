---
title: "Flash problem in web browder"
date: 2008-11-30
forum: Multimedia Software
---

### Post by kalumb on 2008-11-30
hello  evry body,
i recvived Ubuntu cd's, i installed and it's working fine, without  1  thing,
the  flash in web browser's.
i trised to install and reinstall him(flash plugin) and it dosen't work.
when i want to listen for a clip in Youtube, the browser freezs, and become to gray.

what i can to  do to   fix this problem?

thank for  spending you'r time.

Dima.

---

### Post by gandaran on 2008-11-30
more information!
which ubuntu version you have and what package or packages you have installed for flash?

---

### Post by Kingkarloz on 2008-11-30
Hello- I have the same problem- or sometimes the thing will play nice, but if I pause the video, the sound comes back all choppy, and the browser crashes- causing me to completely restart my comp to get my sound back.  Another problem I have is I cannot have more than app use the soundcard in linux, but it works fine in Win XP.  If I have the YouTube player open, I cannot use any of the built in music players in Ubuntu, and vice versa.  

So, my stats are as follows:

Ubuntu 8.04
I have alsa-oss installed.
My soundcard is Intel ICH IEC958 (I think it's one of those AC'97 things)

My problem could stem from trying to install Jack as I thought I would see what Energy XT was like. (and it would never work for some reason, so I uninstalled Jack and EXT...)

Thanks in advance for any advice/help.

---

### Post by gandaran on 2008-11-30
> **Kingkarloz said:**
> Hello- I have the same problem- or sometimes the thing will play nice, but if I pause the video, the sound comes back all choppy, and the browser crashes- causing me to completely restart my comp to get my sound back.  Another problem I have is I cannot have more than app use the soundcard in linux, but it works fine in Win XP.  If I have the YouTube player open, I cannot use any of the built in music players in Ubuntu, and vice versa.  

So, my stats are as follows:

Ubuntu 8.04
I have alsa-oss installed.
My soundcard is Intel ICH IEC958 (I think it's one of those AC'97 things)

My problem could stem from trying to install Jack as I thought I would see what Energy XT was like. (and it would never work for some reason, so I uninstalled Jack and EXT...)

Thanks in advance for any advice/help.
I think you should try fixing pulseaudio and not use alsa-oss [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by kalumb on 2008-11-30
hello again,
I using Ubuntu 8.10,
my computer:
AMD Aphalon 64 bit,2800+,
1GB RAM.
Nvidia Gforce 5200 128 RAM
i web browsers i using Dvix' Web Player.

So, now it's ok?

thank's :)

---

### Post by gandaran on 2008-11-30
> **kalumb said:**
> hello again,
I using Ubuntu 8.10,
my computer:
AMD Aphalon 64 bit,2800+,
1GB RAM.
Nvidia Gforce 5200 128 RAM
i web browsers i using Dvix' Web Player.

So, now it's ok?

thank's :)
is your problem fixed? with dvix web player? where did you get this player?

---

### Post by kalumb on 2008-11-30
> **gandaran said:**
> is your problem fixed? with dvix web player? where did you get this player?

nope.
i got this player with Ubuntu live CD.

---

### Post by gandaran on 2008-11-30
> **kalumb said:**
> nope.
i got this player with Ubuntu live CD.

there isn't exactly any dvix web player that I know of! there are many players that handle dvix formats like totem. vlc, mplayer and many others 
now are you still using the live cd or have you install ubuntu to disk drive? and the ubuntu is 32-bits or 64-bits?
dvix is a video format, it has nothing to do with flash videos
to get flash working, you have to install adobe flash or any other open scource flash software, adobe flash is the best, don't install gnash or swfdec flash.
to install adobe flash you open synaptic package manager, scroll down to **flashplugin-nonfree** mark for install and hit the apply button or maybe it's better you install the **ubuntu-restricted-extras** package
this package intalls nearly everything you need, flash, java, microsoft fonts and codecs you need to play videos on your computer

---

### Post by salem80 on 2008-11-30
> **gandaran said:**
> there isn't exactly any dvix web player that I know of! there are many players that handle dvix formats like totem. vlc, mplayer and many others 
now are you still using the live cd or have you install ubuntu to disk drive? and the ubuntu is 32-bits or 64-bits?
dvix is a video format, it has nothing to do with flash videos
to get flash working, you have to install adobe flash or any other open scource flash software, adobe flash is the best, don't install gnash or swfdec flash.
to install adobe flash you open synaptic package manager, scroll down to **flashplugin-nonfree** mark for install and hit the apply button or maybe it's better you install the **ubuntu-restricted-extras** package
this package intalls nearly everything you need, flash, java, microsoft fonts and codecs you need to play videos on your computer
Thanx U give Me great help
But i was install swfdec flash but the video and the sound 
not work properly i want unstall it to i can install adobe flash.

---

### Post by gandaran on 2008-11-30
> **salem80 said:**
> Thanx U give Me great help
But i was install swfdec flash but the video and the sound 
not work properly i want unstall it to i can install adobe flash.
open synaptic, search for swfdec or mozilla-swfdec-plugin, mark for complete removal and hit the apply button, simple!

---

### Post by salem80 on 2008-11-30
> **gandaran said:**
> open synaptic, search for swfdec or mozilla-swfdec-plugin, mark for complete removal and hit the apply button, simple!

Thanx work will now

---

### Post by Kingkarloz on 2008-11-30
> **gandaran said:**
> I think you should try fixing pulseaudio and not use alsa-oss [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Dude, you're tight- thanks for the fast response!

---

