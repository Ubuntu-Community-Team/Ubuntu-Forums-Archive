---
title: "DVD howto"
date: 2009-10-23
forum: Multimedia Software
---

### Post by jrev on 2009-10-23
Hi,

I am with eeebuntu 9.04 and I consulted the advices given at the following address :

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

When I insert the DVD I can see the introduction of the film then it stops after a minute and I cannot get the rest of the film.
As I am a beginner on playing videos, can you show me where to start ?

I can play the videos I get on the net (youtube or BBC news )

When I want to copy this DVD it's protected against the copy.
Is it possible that it's also protected against playing ?

This DVD comes from the UK and I am in France 

Please help :)

---

### Post by John Bean on 2009-10-23
I guess you installed the ubuntu-restricted-extras package but haven't run the script that adds the DVD decryption routines. It doesn't do this automatically for legal reasons.

Open a terminal and type
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by druunk.otter on 2009-10-23
I'm brand new to Linux & Umbuntu (installed 2 days ago!) but I was having this problem and I just managed to fix it this morning.
Initially I couldn't get my region protected DVDs to even open at all. Then I had a quick read of:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

so I installed the **libdvdread4** package


I could then get to the initial copyright screens of the DVD, but the appllication closed when it came to the main DVD menu, which is where it sounds like you are now.

I followed the advice on the link you gave and did the following:

I enabled the [Medibuntu]("http://www.medibuntu.org/") repository

I then ran the installation script.

After checking that there were no installation errors, I restarted and yay - all my region protected DVDs work! 

I was having all sorts of sound & playback problems with 8.10 (toshiba notebook - hooray) but I've upgraded to Intrepid and seems to have fixed a lot of the old issues.

Hope this was of some help?

---

### Post by jrev on 2009-10-23
> **John Bean said:**
> I guess you installed the ubuntu-restricted-extras package but haven't run the script that adds the DVD decryption routines. It doesn't do this automatically for legal reasons.

Open a terminal and type
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Thanks a lot John !

Then this DVD was designed to be read in England only ?

---

### Post by John Bean on 2009-10-23
> **jrev said:**
> Thanks a lot John !

Then this DVD was designed to be read in England only ?

All commercial DVDs are encrypted; none of them will play without decryption - which the script installs for you. I don't think your problem had anything to do with regionalisation; how could your computer know where you were when you played a DVD? ;-)

---

### Post by druunk.otter on 2009-10-23
> **John Bean said:**
> All commercial DVDs are encrypted; none of them will play without decryption - which the script installs for you. I don't think your problem had anything to do with regionalisation; how could your computer know where you were when you played a DVD? ;-)

Players/drives often have a region code built into them - so a region 4 drive will play region 4 DVDs. I'm really impressed by Medibuntu getting around that headache!

---

### Post by jrev on 2009-10-23
> **druunk.otter said:**
> Players/drives often have a region code built into them - so a region 4 drive will play region 4 DVDs. I'm really impressed by Medibuntu getting around that headache!

I knew there could be a regional lock and I am really impressed too to learn how to bypass it  :confused:

---

### Post by John Bean on 2009-10-23
> **druunk.otter said:**
> Players/drives often have a region code built into them - so a region 4 drive will play region 4 DVDs. I'm really impressed by Medibuntu getting around that headache!
I think you're confusing using consumer DVD players with using an optical data drive on a computer to do the same job. In the latter case it's entirely down to the software what it does with the data it reads from the DVD.

---

### Post by vinutux on 2009-10-23
if it fixed Mark thead SOLVED...

---

