---
title: "can't run alsamixer on usb audio - no mixer elems found"
date: 2008-06-23
forum: Multimedia Software
---

### Post by fred@forte-systems.com on 2008-06-23
Repost - originally posted to m-audio ozone archive but no quick responses.... 

Greetings,

Thanks for all the great help here, I've also gotten my ozone working (mostly, see below) using the info here.

I did have to do the /dev to /proc change and make edits to the 42-mafuload.rules file, etc.

I'm wondering if alsamixer works wth the ozone. I can't seem to get it to respond. Let me know if I should repost this in a new thread.

I get the following whenever I try to run it:

fredimac@musicmaker:~$ alsamixer -D hw:0
No mixer elems found

Results of cat /proc/asound/pcm

00-00: USB Audio : USB Audio : playback 1 : capture 1
01-04: Intel ICH - IEC958 : Intel ICH5 - IEC958 : playback 1
01-03: Intel ICH - ADC2 : Intel ICH5 - ADC2 : capture 1
01-02: Intel ICH - MIC2 ADC : Intel ICH5 - MIC2 ADC : capture 1
01-01: Intel ICH - MIC ADC : Intel ICH5 - MIC ADC : capture 1
01-00: Intel ICH : Intel ICH5 : playback 1 : capture 1


alsamixer works with the Intel using the command alsamixer -D hw:1

Really what I'm looking for is a way to control volume and EQ for all apps when not running jack. Currently only the volume control in individual applications work.


Thanks in advance,
Fred

---

### Post by fred@forte-systems.com on 2008-06-28
Can't anyone pipe in on this?  

The original M-Audio post was very busy, but here 4 days and nothing!?!

Thanks in Advance,

Fred

---

### Post by rundgren on 2009-01-20
Hey!

I recently had the same problem, but found this page:
[http://alsa.opensrc.org/index.php/Alsamixer](http://alsa.opensrc.org/index.php/Alsamixer)

It says that "No mixer elems found" means that the card has no mixer interface and that this is common on USB interfaces.

---

