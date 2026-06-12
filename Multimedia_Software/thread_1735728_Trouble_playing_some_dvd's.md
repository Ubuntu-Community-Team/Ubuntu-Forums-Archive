---
title: "Trouble playing some dvd's"
date: 2011-04-21
forum: Multimedia Software
---

### Post by sunebach on 2011-04-21
Hi all

Hope you can help.

I'm having trouble playing some dvd's, but not all. I have recently formatted my hard disk and installed Ubuntu 10.10.

I use VLC and have both libdvdread4 and libdvdcss installed. Have tried [HTML]help.ubuntu.com/community/RestrictedFormats/PlayingDVDs[/HTML]It looks to me as if both my drive and the dvd's are region2 and the drive plays other region2 dvd's without problems.

From [HTML]ubuntuforums.org/showthread.php?t=1625019[/HTML] I got the idea to run  ```
export DVDCSS_VERBOSE=2
``` followed by ```
export DVDCSS_METHOD=title && vlc dvd:// > vlc_output.log 2>&1
```.

This gave the output in the attached file.

So, now I'm confused and therefore I hope that someone else can get something useful out of all this.

---

### Post by KegHead on 2011-04-21
Hi!

You could try;

1. Goto software center and search for restricted extras.

2. Install.

Please advise if this works!

KegHead

---

### Post by sunebach on 2011-04-21
Hi Keghead

Have got the extras, so that's not it.

But thanks for trying. All ideas are welcome.

---

### Post by KegHead on 2011-04-22
Hi!

Can you play any other dvd's?

KegHead

---

### Post by sunebach on 2011-04-22
I have checked a few things.

I cannot play the dvd in windows either. It can't play on my laptop running ubuntu 10.4.

It does run without problems on my dvd-player.

And for your question KegHead: yes, it plays other dvd's without problems. Also others with the same region code.

---

### Post by KegHead on 2011-04-22
Hmm,

Maybe they are defective.

KegHead

---

### Post by sunebach on 2011-04-24
I guess they might be - but it would have to be a script in them, that the normal dvd-player doesn't read.

---

