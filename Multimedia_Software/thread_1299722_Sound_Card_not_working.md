---
title: "Sound Card not working"
date: 2009-10-24
forum: Multimedia Software
---

### Post by yd123 on 2009-10-24
I am a linux newbie

My sound is not working

I am on 9.04

Have dug around and installed ALSA and so on no joy

This is what I have so far

udo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

Am stuck now any help appreciated

---

### Post by RichardLinx on 2009-10-24
See this post: [http://ubuntuforums.org/showpost.php?p=8139087&postcount=2](http://ubuntuforums.org/showpost.php?p=8139087&postcount=2)
You have no idea how many times I've answered the same question with the same answer. While I don't mind answering the question it's a little eery to think that because someone didn't bother to do a search they were unable to fix there issue. 

I'm not taking a go at you or anything, but please don't be afraid to use the forum search function if you have any issues in the future. It might save you a lot of time. :)

---

### Post by yd123 on 2009-10-24
I am terribly sorry but did all that and still no joy

:(

---

### Post by AutoStatic on 2009-10-24
yd123, your problem is probably not related to PulseAudio. Removing PulseAudio is a bad thing, it breaks a lot of stuff. And installing esound instead is even worse. Just my 2 cents.
What is the output of the following commands in a terminal:
- **aplay -l**
- **cat /proc/asound/card*/codec#* | grep -i codec**

---

