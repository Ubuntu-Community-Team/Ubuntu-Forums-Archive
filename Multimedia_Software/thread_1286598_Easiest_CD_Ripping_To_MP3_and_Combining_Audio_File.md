---
title: "Easiest CD Ripping To MP3 and Combining Audio Files"
date: 2009-10-09
forum: Multimedia Software
---

### Post by uv_goth on 2009-10-09
I need an easy to use CD ripper suggestion that will rip straight to MP3 please!

Also I'm using Audacity to combine the files (each disc of my audiobooks rips to several tiny bits about 5mins long) but it's a lengthly process. Is there any easier way to do this, either after ripping or during?

---

### Post by StuartN on 2009-10-09
> **uv_goth said:**
> I need an easy to use CD ripper suggestion that will rip straight to MP3 please!

The standard Audio CD Extractor will rip to wav and encode these to mp3. I prefer grip because it has more configuration options.

Apparently k3b can rip a CD into a single file, saving you the effort of splicing the little pieces back together - also good for many electronica albums that should play directly from one track into the next, where mp3 players insert an annoying pause.

---

### Post by uv_goth on 2009-10-09
Thankyou!

---

### Post by uv_goth on 2009-10-12
Someone has suggested using CAT to combine the files and adding correct ID3 information via Rhythmbox.

Has anyone else done this?

(I'll only be playing audiobooks on my PC using VLC or Rhythmbox)

---

### Post by StuartN on 2009-10-12
> **uv_goth said:**
> Someone has suggested using CAT to combine the files and adding correct ID3 information via Rhythmbox.

You can use a command like **cat ch1.mp3 ch2.mp3 ch3.mp3 > book.mp3** which would make one long file, book.mp3, out of all the input files. All of the ID3 tags of all the files (and all the album art, etc) will be inside the big file and may confuse some players, but you can try it.

The two commands mp3wrap and mp3splt will combine a set of mp3 files into one playable mp3 file that can be split again, without any loss of tags etc. You can get these comands from the Synaptic package manager.

---

### Post by uv_goth on 2009-10-12
I looked at mp3wrap but I saw this about it not working properly and it's no longer updated:

[https://bugs.launchpad.net/ubuntu/+source/mp3wrap/+bug/188025](https://bugs.launchpad.net/ubuntu/+source/mp3wrap/+bug/188025)

As I would then need to change the ID3 information anyway and mp3wrap is a command-line utility, it seemed a bit pointless to use it

---

### Post by SuperSonic4 on 2009-10-12
kid3 is a good GUI tag editor - you could use it with cat

---

### Post by TracyO on 2009-10-14
I'm also trying to rip straight to mp3s, but both Rhythmbox and the cd extractor will not allow me to select that option.  It's not listed in the drop down menu, but it IS an option under edit preferred format.  However, I cannot select it or save it as my preference.  Why is this?  

I'm using Hardy, and please keep responses simple--I've been using Ubuntu for 2 years, but I'm still a Linux newbie.

---

### Post by StuartN on 2009-10-14
> **TracyO said:**
> both Rhythmbox and the cd extractor will not allow me to select that option.

MP3 encoding is not enabled by default. It should be as simple as "Enable the universe and multiverse repositories. Then, install the package ubuntu-restricted-extras." ([https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping))

---

### Post by TracyO on 2009-10-14
Thanks--it worked.  You're my new hero!

---

