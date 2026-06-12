---
title: "Alsa 1.0.11 works only at 44.1 kHz with C-Media CM6501"
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by ceituna on 2007-01-24
Hello everybody,

I've bought since a couple of days a new Motherboard, and it seems I cannot enjoy as much the music as I did before...

I have a C-Media CM6501 sound chip :
> 
ceituna@hal:~$ lsusb 
...
Bus 002 Device 002: ID 0d8c:0201 C-Media Electronics, Inc.
...


The sound is all right, except when I want to play a DVD or when i Have 48kHz sounds...

The sound seems garbled, and after searching a bit, It seems that this problem is known, and solved since version 1.0.14 of alsa (unluckly not available with Ubuntu, even as experimental).

How would you suggest me to backport that version ? I've tried installing alsa-base_1.0.14~rc1-1_all.deb linux-sound-base_1.0.14~rc1-1_all.deb and from Debian. The installation was OK, but the garbled sound was still going on. Reinstalled then Edgy packages back (1.013).

Any Idea about a possible workaround ?

Thank you,

Oliver

---

### Post by Shinoda on 2007-02-06
Have you read [this](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#ALSA_driver_Compilation) yet?

Aside from your problem, can you please tell me what's your MB, how many audio channels it features, and if they're all working correctly? Thanks.

---

