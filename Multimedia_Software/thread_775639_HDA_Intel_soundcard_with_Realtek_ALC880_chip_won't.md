---
title: "HDA Intel soundcard with Realtek ALC880 chip won't work"
date: 2008-04-30
forum: Multimedia Software
---

### Post by Puistius Giganticus on 2008-04-30
Hey,
 
Some time ago I got a new, old, PC ;-). I installed hardy-kde4 on it (first the beta-version and later a clean install of the official release). after the installing the official release nearly everything worked (I had some difficulties with my nvidia card but that is solved yet :) )

Now I only have a problem with my soundcard. With my speakers on 100% (wich should make my deaf when I did that with my "old" PC) I hardly hear anything. and what I hear is more noise then music or system sounds.

I tried really everything with alsamixer, Kmix an system settings -> sound (or I think I did) but nothing works.. 

Searching with google results in scary-driver-download sites whit actually no possibility of downloading anythong and people who had the same problem but no solution (it seems to be a common problem with my PC, a HP Pavilion t3260.nl)
 
According to alsa I have a HDA Intel soundcard (onboard) with a Realtek ALC880 chip.
 
Does anybody know wich driver I should install or how to help alsa producing some sound or otherwise solve this problem?

Thanks already

Lieven

p.s.: I plugged te speakers in the right output :P
p.p.s.: sorry for my bad english

---

### Post by Puistius Giganticus on 2008-05-01
Nobody? :(

---

### Post by presston on 2008-05-02
look for my explane here

[http://ubuntuforums.org/showpost.php?p=4823979&postcount=53](http://ubuntuforums.org/showpost.php?p=4823979&postcount=53)

and howto here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by jonspencerbx on 2008-05-02
Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=616845&highlight=intel+hd+audio](http://ubuntuforums.org/showthread.php?t=616845&highlight=intel+hd+audio)

This fixed my realtek alc888 problem. I had to add ```
options snd-hda-intel model=auto
``` to /etc/modprobe.d/alsa-base

If that line doesn't work, look in the thread I just mentioned and try some other entries. Don't forget to reboot in between tries.

---

### Post by Eirikizer on 2008-05-02
Hi, that method in the last post really worked for me! I had the same soundcard and had been struggling for hours to get it working. Thanks!

---

### Post by Puistius Giganticus on 2008-05-04
Hi,

thanks for all the links. strange I didn't found these with google but that has more to do with the way I use search engines :oops: (mayby I should have searched with the forum-search-engine...  :oops: )

I tried adding the line jonspencerbx posted above and it helped a little but there is still much noise. I'll try to find out how to solve my problem on the linked pages. If I solved the problem I shall post how I did it :)

Again: Thanks for the help so far :)

---

### Post by MJ Britt on 2008-05-14
This worked beautifully on my Toshiba Satellite L45.

Thank you,
Matt

---

### Post by Puistius Giganticus on 2008-05-30
:) I fixed it thanx to the help topic jonspencerbx linked to. :)

I just had to add "options snd-hda-intel model=asus" to the alsa-base file
(i was a bit slow with try to solve this problem because I was a bit busy at the university :P )

Thanks for the help

---

