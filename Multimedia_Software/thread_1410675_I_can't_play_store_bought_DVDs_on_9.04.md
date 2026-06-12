---
title: "I can't play store bought DVDs on 9.04?"
date: 2010-02-19
forum: Multimedia Software
---

### Post by S2UIRR3L on 2010-02-19
I can play movies that are burned on DVD-R (and DVD+R) but I can't play anything that I buy in a store. Is there a codec or decoder that I need to install? What do I look for and can I do it with Synaptic Package Manager?

A friend of mine (very good with Linux) installed Ubuntu-8 for me and DVDs worked great with VLC. I upgraded to Ubuntu-9 and was blowen away with all the new stuff. I'm not quite ready to move onto Ubuntu-10.

I can do things in Terminal, if it's copy and paste and some what explained to me in plain English. But I'd rather do things in Synaptic because I'm used to Control Panel in XP, but Synaptic is so much better and easier to use.

Is there something that I could (or should) search for in Synaptic Package Manager? Do I need some kind of code or DVD Decoder even tho I downloaded and installed VLC? Is there something that I can copy and paste into a Terminal?

Thanks in advance
-Leo in Massachusetts

---

### Post by grahams on 2010-02-19
You will need to install libdvdcss2 to watch protected dvds.

Good instructions at [https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)

---

### Post by dsavi on 2010-02-19
It's not all that hard, I did it a few days ago. (On 9.10, but I'm pretty sure that it works on 9.04 too)

1. Open a terminal

```
sudo apt-get install libdvdread4
```
2. And one more command:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

(Note to other people who know more about this than me: In Jaunty you don't have to do all that stuff with Mythbuntu repositories right? I looked in the Jaunty repositories and libdvdread4 was there.)

---

### Post by S2UIRR3L on 2010-02-20
Thanks a million for pointing me in the right direction... And may I add, DVDs play so much better on Ubuntu compared to the performance I get on the windows end of my laptop.

Thanks a million, grahams!!!
-Leo in Massachusetts

---

### Post by S2UIRR3L on 2011-12-03
**_BUMP_ - Now let me ask if the codes are the same for Lucid Lynx 64-bit?**

[SIZE=2]sudo apt-get install libdvdread4[/SIZE]

**and then followed by**

[SIZE=2]sudo /usr/share/doc/libdvdread4/install-css.sh[/SIZE]

**?**

---

### Post by S2UIRR3L on 2011-12-04
[COLOR=Red][SIZE=1]**bump**[/SIZE][/COLOR]

---

### Post by S2UIRR3L on 2011-12-04
Okay - This is me tapping out and going to a new thread or something. Marking this back to SOLVED again.

---

