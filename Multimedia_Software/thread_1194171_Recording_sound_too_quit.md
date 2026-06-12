---
title: "Recording sound too quit"
date: 2009-06-22
forum: Multimedia Software
---

### Post by moe19790 on 2009-06-22
hi,

not sure what is wrong, the playout sound is perfectly fine.. but the recording is too quit.. i opened the sound mixer and increased the sound level for the mic to max and still the same issue!

thanks

MOe!

---

### Post by moe19790 on 2009-07-19
Bump

---

### Post by igorzwx on 2009-07-19
which tool for recording?

---

### Post by moe19790 on 2009-07-23
i`m using Audacity :)

---

### Post by igorzwx on 2009-07-23
If you want to record only with Audacity,
and you do not use USB audio devices,
then you may consider installation of OSS4.
But, if you have HDA, it may not be so simple.

Can you install another Ubuntu in dual boot (for experiments)?

---

### Post by moe19790 on 2009-07-25
well, yes mainly the entire PC is for experimental use :D

---

### Post by neu2buntu on 2009-07-25
maybe try gnome-volume-control >preferences,and see if there is a "mic boost" option or in audacity itself ,look at the mic input slider and make sure it is all the way up.(see screenshot mouse pointer)

---

### Post by KingNeil on 2009-07-25
i'm having the same issue, except, I have no "mic boost" option. i had one on windows, but not ubuntu. very disappointing.

i have a dell xps m1530 btw

---

### Post by igorzwx on 2009-07-25
"well, yes mainly the entire PC is for experimental use"

Great!

I am making all kind of experiments every day on the old box.
We may have something to discuss.

It is convenient to have several Ubuntus installed in multiple boot.

If you have an old box, your hardware is most likely supported by OSS4.

If your have HDA (high definition audio) sound card (and/or USB audio devices)
you should check, if your hardware is supported by OSS4
**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document. 

[B]To install OSS4, your should folow this howto:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[/B]
If you feel very experimental, you may try to compile the 
latest version of OSS4 from Mercurial. I tried. It is very impressive,
really cool. The howto is the same:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Do not hesitate to ask questions.

General info about OSS4 is here:
[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

---

### Post by neu2buntu on 2009-07-25
KingNeil paste the output of ```
aplay -l ; arecord -l
``` and also ```
gedit /etc/modprobe.d/alsa-base.conf
``` from the terminal.and also ```
lspci -vvv
``` and just paste the "Audio" section as this command gives a large reading.

---

### Post by moe19790 on 2009-07-26
Thank you very much all for those info. Ganna try them and see :)

---

### Post by igorzwx on 2009-07-26
Skype works well with OSS4, Ekiga too.
Audacity works out of the box.

Good luck!

---

### Post by moe19790 on 2009-11-07
upgrading alsa mixer to the latest ver. solved the issue :)

thank you all for great help and effort :)

---

