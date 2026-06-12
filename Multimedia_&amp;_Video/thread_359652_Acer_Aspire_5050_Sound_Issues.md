---
title: "Acer Aspire 5050 Sound Issues"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by Sarghm on 2007-02-12
Hi there, I'm having some problems with my Acer Aspire 5050. I recently installed Ubuntu and managed to configure the graphics hardware (I have an ATI Xpress 1100), but I am now faced with the new problem of sound. I receive none whatsoever. I believe ALSA is installed, but upon entering 'alsamixer' into Terminal I receive the error:

alsamixer: function snd_mixer_load failed: Invalid Argument

The default sound card displays as HDA ATI SB. Can anybody assist me in getting this to work?

Regards,

---

### Post by conxorxa on 2007-02-17
I got the sound to work by installing the latest alsa drivers (1.0.14rc2) from [http://www.alsa-project.org/](http://www.alsa-project.org/).  

I also added:
options snd-hda-intel model=auto 
to /etc/modprobe.d/snd-hda-intel.modprobe and the end of /etc/modprobe.d/alsa-base.

I still haven't got alsamixer to work though.  It did work once but when I rebooted it stopped working.  I keep getting the same error as you.

---

### Post by srt5 on 2007-03-03
I had a similar problem with my sound - it's a common problem. I have an Acer 5051 (an arrangement of the 5050) and I tried several ways to fix the sound. Only one method worked for me....

[http://uk.blog.360.yahoo.com/blog-kLgobDE_cqVv1JH8Yrs5u0AOygiyr1iiv0erhcaU_BKG?p=5](http://uk.blog.360.yahoo.com/blog-kLgobDE_cqVv1JH8Yrs5u0AOygiyr1iiv0erhcaU_BKG?p=5)

hope this helps.

:)

---

### Post by manaluxx on 2007-05-25
hello srt5....
can u make the detail procedure to make the sound works in acer 5051?
cause i've checked the site you mentioned before:
[http://uk.blog.360.yahoo.com/blog-kLgobDE_cqVv1JH8Yrs5u0AOygiyr1iiv0erhcaU_BKG?p=5](http://uk.blog.360.yahoo.com/blog-kLgobDE_cqVv1JH8Yrs5u0AOygiyr1iiv0erhcaU_BKG?p=5)
And I'm Still confuse to make the sound works. 
I'm a newbie in Linux.
Thanks.

---

### Post by defri on 2007-06-08
Try this little trick. I also same problem and i have the answer for this. Open your surround mixer and don't mute this. Try to make the volume at the maximum. After i try this my sound is out of my speaker. Thanx to EduMaxwell for this trick.

---

### Post by ruyadorno on 2007-12-17
defri is right, I also solve the problem just activating the surround option... it's hide on sound controls, I set my controller to Alsa mixer and then on Edit > Preferences I activated the Surround option, worked!

---

