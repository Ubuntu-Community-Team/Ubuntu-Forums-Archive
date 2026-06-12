---
title: "AverTV 303 - sound's problem"
date: 2010-01-02
forum: Multimedia Software
---

### Post by Qmix on 2010-01-02
I've got a problem with AverTV 303 card (chipset conexant CX 23883). At the beginning it was a problem with picture and sound. Now I'm in the middle of my way. I have a picture, but there is no sound. I'm using tvtime. Please advice what should be checked and how to sort the problem out.

---

### Post by jimmers on 2010-01-03
I use a AVerMedia USB Stick, and it works perfectly using Kaffeine,
no trouble at all.

May not be of any use to you, but worth a try.

By the way according to the web the AverTV 303 will soon be obsolete in the UK.

Best of Luck

---

### Post by Qmix on 2010-01-06
Thanks for the info. Even something is better then nothing. Unfortunatelly I still don't have a sound... Any help would be appreciated.

---

### Post by jimmers on 2010-01-06
Have a look at Uncle Spellbinder's thread Re TVTime No Sound in Karmic (Page 3)
It may or may not help, you dont say what dist you are using.

---

### Post by Qmix on 2010-01-06
Thanks a lot!!! It works. 
I used the code:
*pactl load-module module-loopback*
and then:
*tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r32000 | aplay -*

One thing. After reboot the system it doesn't work. I have to use code:
*pactl load-module module-loopback*

 then it works again. 

Is there any chance to run it automatically with tvtime? Create some config?

---

