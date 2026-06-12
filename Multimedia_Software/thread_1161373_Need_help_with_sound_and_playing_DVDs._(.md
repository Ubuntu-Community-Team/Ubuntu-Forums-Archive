---
title: "Need help with sound and playing DVDs. :("
date: 2009-05-16
forum: Multimedia Software
---

### Post by Plastic Dinosaur on 2009-05-16
Hi everyone! I have a few questions. They are in the same category, so I decided to put them in the same thread.:D

[B]1. I have an Acer Aspire notebook model 5735-6694. When I plug in my headphones, the sound come through the headphones AND the speakers. How can I fix this?
Oh, and my sound card is: Card: HDA Intel, Chip: Realtek ALC268

2. Only some DVDs play. I guess it just plays them when it feels like it. It played my friend's pirated copy perfectly. It won't play region 2 DVDs...or a few region 1s..such as Little Miss Sunshine. :( I get messages like, "You're not aloud to play this" or something like that.[/B]

I'll appreciate some help and guidance. My mic doesn't work either, but will get to that. It's not as important right now.

:) Have a lovely day!):P

- Hayley

---

### Post by mprince on 2009-05-16
This thread may help with issue#1

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

### Post by Plastic Dinosaur on 2009-05-16
It won't let me edit "gedit /ect/modprobe.d/alsa-base" Says I can't save, because the file doesn't exist.

---

### Post by mprince on 2009-05-16
If you are using 9.04 I think it is now called **alsa-base.conf**. I assume it's in the same directory. You could edit that and give it a shot.

---

### Post by mprince on 2009-05-16
**This thread also pertains to this issue:
[http://ubuntuforums.org/showthread.php?p=5830831](http://ubuntuforums.org/showthread.php?p=5830831)

Someone suggests doing the following:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this line and specify your model. Which is Acer.
```
options snd-hda-intel model=**acer**
```

Hope this helps.

---

### Post by Plastic Dinosaur on 2009-05-17
Ok, I figured how to open the file manually. And added the line at the end...but I've tried a bunch of different things now, and can not get the switch option. :(

I'm about to loose my mind.

---

### Post by mprince on 2009-05-18
[QUOTE=Plastic Dinosaur]2. Only some DVDs play. I guess it just plays them when it feels like it. It played my friend's pirated copy perfectly. It won't play region 2 DVDs...or a few region 1s..such as Little Miss Sunshine.  I get messages like, "You're not aloud to play this" or something like that.[/QUOTE]

Your drive will probably only play unencrypted DVDs. That's why it plays your friends copy.

There is something you need to install to be able to play a encrypted DVDs . I'm going to dig up a guide for this.

---

### Post by mprince on 2009-05-18
To get your dvd player to play encrypted DVDs, you would have to install **libdvdcss2**

Here is a guide to help you do that:
 *This will all be done with a terminal.

[http://www.detector-pro.com/2009/04/how-to-install-dvd-and-all-audiovideo.html](http://www.detector-pro.com/2009/04/how-to-install-dvd-and-all-audiovideo.html)

You only need to follow the second set of steps on that page.

1. Add the Medibuntu repository
2. Then add GPG key
3. then sudo apt-get install libdvdcss2
4. You _don't_ have to install the w32codecs

This will *not* allow you to play region 2 discs, but if you followed the steps right, you should be able to play all discs for your region now.

---

