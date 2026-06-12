---
title: "[SOLVED] How do I copy (rip?) my DVDs?"
date: 2008-12-30
forum: Multimedia Software
---

### Post by stephanecharette on 2008-12-30
I would like to store my children's DVDs on their computer for them to watch.  I already know that I can create .iso files using:
```
cat /dev/cdrom > ~/Desktop/name_of_dvd.iso
```
The kids know how to play these with VLC, but this produces 4GB files, which is much larger than I want for my children's movies.

What software should I use to copy or rip DVDs so I only have files between 300MB and 700MB instead of 4GB?

(At 2, 4, and 6 years old, I'm certain they wont mind if some of their Thomas The Train videos are at a lower quality than the original dvd.)

Thanks!

Stéphane

---

### Post by soxs on 2008-12-30
DVDs without copyright: ```
dd if=/dev/cdrom of=/home/$USER/dvdimage.iso
```
This may work for all DVDs if you install libdvdcss2 and some other things from medibuntu (see [www.medibuntu.org](www.medibuntu.org) ).

I personally prefery ripping to mkv videos.

---

### Post by amauk on 2008-12-30
Handbrake

[http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)

---

### Post by Bluebell392 on 2008-12-30
Try Handbrake. It copies the entire DVD to one file, with the quality settings you specify.

---

### Post by stephanecharette on 2008-12-30
> **soxs said:**
> DVDs without copyright: ```
dd if=/dev/cdrom of=/home/$USER/dvdimage.iso
```

Er?  How is that any different than what I wrote in my original post?

And what does copyright have anything to do with me watching DVDs I purchased on my computer?

Stéphane

---

### Post by SuperSonic4 on 2008-12-30
k9copy is a winner for me. It can either rip to mpeg or avi (both will play in vlc) and you can explicitly set the filesize.

---

### Post by MartyBuntu on 2008-12-30
AcidRip to .avi is what I would recommend.

---

### Post by axel206 on 2008-12-30
One more vote for k9copy. Check this also: [k9copy tutorial](http://www.my-guides.net/en/content/view/77/26/)

---

### Post by soxs on 2008-12-31
> **stephanecharette said:**
> Er?  How is that any different than what I wrote in my original post?

And what does copyright have anything to do with me watching DVDs I purchased on my computer?

Stéphane

Sorry, I meant copy-protected.

And dd will make a 1:1 backup from your DVD, I doubt cp is supposed to do that.

---

### Post by amauk on 2008-12-31
cp /dev/cdrom > ~/Desktop/name_of_dvd.iso
&
dd if=/dev/cdrom of=/home/$USER/dvdimage.iso
are identical

---

### Post by stephanecharette on 2008-12-31
Thank you for all the suggestions.  In summary, these were suggested:

1) handbrake
2) k9copy
3) acidrip

First one I tried was Handbrake, and not only does it work well, it is available for download via .deb file on their web site.

Thanks again.

Stéphane

---

### Post by stephanecharette on 2008-12-31
> **amauk said:**
> cp /dev/cdrom > ~/Desktop/name_of_dvd.iso
&
dd if=/dev/cdrom of=/home/$USER/dvdimage.iso
are identical

My fault -- there is a typo in my original command.  Don't use cp, but cat.  The quote above contains my typo.  The corrected commands that are identical are:
```
cat /dev/cdrom > ~/Desktop/name_of_dvd.iso
&
dd if=/dev/cdrom of=/home/$USER/dvdimage.iso
```

Sorry about the confussion.

Stéphane

---

### Post by soxs on 2008-12-31
So, cat is somewhat different to cp :-D and you're right, this should have the same result.

---

