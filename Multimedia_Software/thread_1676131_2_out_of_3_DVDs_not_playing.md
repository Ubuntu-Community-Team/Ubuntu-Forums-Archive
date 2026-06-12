---
title: "2 out of 3 DVDs not playing"
date: 2011-01-26
forum: Multimedia Software
---

### Post by coldraven on 2011-01-26
I just got three brand new DVDs all Region 2, PAL Movies with no scratches or fingerprints on them.
Only one will play (perfectly) the others just make the drive grunt a couple of times before giving up.
I have not had any problems with any media on this laptop before.
Is there a log file that would give me any insight into this problem?
All ideas gratefully received.
Thanks

---

### Post by wilee-nilee on 2011-01-26
> **coldraven said:**
> I just got three brand new DVDs all Region 2, PAL Movies with no scratches or fingerprints on them.
Only one will play (perfectly) the others just make the drive grunt a couple of times before giving up.
I have not had any problems with any media on this laptop before.
Is there a log file that would give me any insight into this problem?
All ideas gratefully received.
Thanks

Can you describe the media players you have used and the codecs you have installed.

---

### Post by coldraven on 2011-01-26
I just followed the advice here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
and have Medibuntu 10.10 Free Non-free
lib2css
W64, libavcodec-extra-52 , gnome-codec-install and loads more. Unfortunately when I type codec in Synaptic (installed section) I get more than a page worth so a screenshot is a problem.
What command would output a text file with them all in? The man page for apt is very empty!

Update: "dpkg --get-selections | grep -v deinstall| grep codec"  gives this result
chromium-codecs-ffmpeg                install
gnome-codec-install                install
libavcodec-extra-52                install
w64codecs                    install

---

### Post by wilee-nilee on 2011-01-26
Install the ubuntu-restricted-extras and w32 and libdvdread4. These are all in synaptic, if you have a different desktop then ubuntu then install its restricted-extras. Try vlc and smplayer as media players.

---

### Post by coldraven on 2011-01-26
> Install the ubuntu-restricted-extras and w32 and libdvdread4. These are  all in synaptic, if you have a different desktop then ubuntu then  install its restricted-extras. Try vlc and smplayer as media players.

Yes, apart from w32 I already have them. I have the W64 codec.
I am using VLC all the time but these disks will not mount, it's as if they were damaged.
I can't believe that two new DVDs can both be faulty.

---

### Post by wilee-nilee on 2011-01-26
> **coldraven said:**
> Yes, apart from w32 I already have them. I have the W64 codec.
I am using VLC all the time but these disks will not mount, it's as if they were damaged.
I can't believe that two new DVDs can both be faulty.

It may be a simple as trying the DVD's on another computer to confirm their viability.  Sometimes a reboot will fix this, and checking if the DVD reader is clean. Check in menu-places-computer to see if the reader is showing there when you try the DVD reader again.

---

### Post by coldraven on 2011-01-27
Thanks wilee-nilee, I could not post back yesterday because the forum would not let me log-in.
The answer was to clean the lens but this is what made such a strange problem.
I cleaned it with a dry cotton bud before my first post. Result: 2 out 3 DVDs would not play.
I cleaned it again with Methylated spirit. Result: 1 out of 3 not playing.
I cleaned it again with a dry cotton bud. Result: All working!
It must be that damned nicotine getting in the works! :P

---

