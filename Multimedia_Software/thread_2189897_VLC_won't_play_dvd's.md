---
title: "VLC won't play dvd's"
date: 2013-11-24
forum: Multimedia Software
---

### Post by blightedagent on 2013-11-24
I know my dvd player works because I was using it before switching to linux.  VLC is working properly for everything else and after some searching I thought I might need a CSS decryption library.  The only one I could find in software manager was libdvdcss, which is in brasero.  Is there another package I need to download?  thanks for any help.

---

### Post by mc4man on 2013-11-24
In a terminal - 
```
sudo /usr/share/doc/libdvdread4/install-css.sh

```

---

### Post by electrohandyman501 on 2013-11-24
You may also need to reboot after you install. I had to, in order for it to work.

---

### Post by blightedagent on 2013-11-25
worked like a charm, thanks electrohandyman.  I'm curious, what did I download and why isn't that included in any of my system updates?  Seems like that's a basic thing that should be included in Ubuntu from the start.

---

### Post by electrohandyman501 on 2013-11-25
Can't say for sure why, but I suppose you could play your own home made dvd movies without the decode files. Unlike the purchased dvd's that require the decoding.

---

### Post by frank18 on 2013-11-25
> **blightedagent said:**
> I know my dvd player works because I was using it before switching to linux.  VLC is working properly for everything else and after some searching I thought I might need a CSS decryption library.  The only one I could find in software manager was libdvdcss, which is in brasero.  Is there another package I need to download?  thanks for any help.

try this:
[https://www.thinkpenguin.com/gnu-linux/playing-digitally-restricted-dvds-gnulinux](https://www.thinkpenguin.com/gnu-linux/playing-digitally-restricted-dvds-gnulinux)

---

### Post by rk86pandey on 2013-11-28
No any software is get installed from ubuntu software centre. trying to install vlc, netbeans and mysql but not working at all.

---

### Post by Frank_T._Morgan on 2013-12-05
*...That's it!  That's it!*

I used the code provided, rebooted my system for good measure, *and it works!*  \\:D/ (I feel more like putting a dancing banana here, but you get the idea.)

Thanks, mc4man!!  Dude, you rock. =D>

---

### Post by ciunasecho on 2014-02-11
> **mc4man said:**
> In a terminal - 
```
sudo /usr/share/doc/libdvdread4/install-css.sh

```

mc4man's solution worked for me as well.

---

### Post by Warrick_Sutton on 2014-08-23
Sir,

Without going near the topic of the religion-like mysteries of why the command that you provided is not, as mentioned by others, a standard element of the VLC package - breathe - please accept my very deep gratitude for your (thus far) perfect solution.

For the sake of my unstable self-image, let's not ask why it me so long to think of the google search that led to your answer, but suffice to say that your post was a beam of sunshine for me and no mistake.

Thanks again,

Warrick Sutton

Dude, I wish my reply was able to say it as expressively as yours!

---

