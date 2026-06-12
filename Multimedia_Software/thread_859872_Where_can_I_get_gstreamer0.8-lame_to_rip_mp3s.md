---
title: "Where can I get gstreamer0.8-lame to rip mp3s"
date: 2008-07-15
forum: Multimedia Software
---

### Post by Charlie Wilkes on 2008-07-15
I have enabled everything in my sources.list file but still get an error message:

Couldn't find package gstreamer0.8-lame

Any help much appreciated.

Charlie

---

### Post by gandaran on 2008-07-15
> **Charlie Wilkes said:**
> I have enabled everything in my sources.list file but still get an error message:

Couldn't find package gstreamer0.8-lame

Any help much appreciated.

Charlie

you can get it from the gutsy repos.
how do you want to rip mp3's? with sound juicer?
for sound juicer and other ripping applications in hardy you use the **gstreamer0.10-plugins-ugly-multiverse**.

---

### Post by Charlie Wilkes on 2008-07-15
> **gandaran said:**
> you can get it from the gutsy repos.
how do you want to rip mp3's? with sound juicer?
for sound juicer and other ripping applications in hardy you use the **gstreamer0.10-plugins-ugly-multiverse**.

Thanks.  I installed everything I could find and none of it worked... I finally figured out that I had to create a new mp3 entry in Sound Juicer rather than expecting the existing one to work.  Once I did that, it worked fine.

Charlie

---

