---
title: "AC97 Audio"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by general.chaos on 2007-05-14
Hi guys, I'm not new to Linux (been running since RedHat 6) or Ubuntu, but I am new to the forums.

First off, I must say that Ubuntu 7.04 is the first version to support enough of my hardware for me to actually use it full time.  I had to do some hacks to get things like my 1440x900 monitor to work properly, as well as get AIGLX and Beryl running for my Radeon x800xl.  I also had to do a hack for my fonts DPI to make them readable.

I got everything running well with the exception of my sound.  My card supports 5.1 surround sound, and I have a system hooked up to it (Creative 5.1 Speaker System), but I can only get stereo sound.  I have installed every mixer under the plannet, all of which show a surround and center mixer, but they don't do anything.

I have changed everything I could find to 5.1 as opposed to surround, but I still can't get my other speakers to produce sound.

Any advice would be appreciated!

TIA!

==========
EDIT: If there is no way to make this work, can someone please reccommend a good sound card that will work with 5.1 in both windows and Ubuntu?
==========

---

### Post by packjamNL on 2007-05-14
I can' t get this msg awaay, I thought I had the answer but I do not

---

### Post by general.chaos on 2007-05-14
I already have all the w32 codecs and alsa installed.  I've tried every mixer, including alsamixer, and I still can't get surround sound.  It works fine on my XP install on the same machine however.

I'm thinking I'm going to need a new soundcard to solve this problem.  Google has returned nothing but people who couldn't get it working.

---

### Post by josephus on 2007-05-14
have you tried compiling the newest version of alsa?

---

### Post by general.chaos on 2007-05-14
I wasnt aware there was a newer version than the one that shipped with 7.04

---

### Post by josephus on 2007-05-14
[http://www.alsa-project.org/](http://www.alsa-project.org/)

they are up to 1.0.14rc4, feisty is shipped with 1.0.13

---

### Post by general.chaos on 2007-05-14
thanx for the tip!  I will try it when I get home tonight and post back.

---

### Post by Innova on 2007-05-14
I have the [same problem]("http://ubuntuforums.org/showthread.php?t=443179").

Please let me know if that works for you, or if you find any other solutions.

---

### Post by general.chaos on 2007-05-15
the update didn't work.  Can someone sugest a card that will work with 5.1 support

---

### Post by josephus on 2007-05-15
have you tried playing with the options in /etc/modprobe.d/alsa-base

you might need to add a line at the end of the file:

options snd-emu10k1 extin="0x3fc3" extout="0x07cff"

there is a file included in the alsa-base package that tells you all the different options available for each driver.

look at [http://alsa.opensrc.org/Emu10k1](http://alsa.opensrc.org/Emu10k1) for some more info.  the location of configuration file is different in ubuntu, but otherwise i think most things apply.

---

### Post by general.chaos on 2007-05-15
I'll check it out tonight and post back.  In the mean time, can anyone suggest a sound card in the probable event that this doesn't work?

---

### Post by Innova on 2007-05-15
I was just looking at the alsa site, and they mention that all USB devices should work...I wonder if something like this would work?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16829118002](http://www.newegg.com/Product/Product.aspx?Item=N82E16829118002)

---

### Post by general.chaos on 2007-05-15
Hrmm... Ill have to look for a nice 5.1 USB sound card then.  

I always thought USB sound card to be inferior, is this a poor assumption?

I think I found my solution!

[http://www.newegg.com/Product/Product.aspx?Item=N82E16829126101](http://www.newegg.com/Product/Product.aspx?Item=N82E16829126101)

Works on Linux, 5 ports, only $20

---

### Post by AlanD on 2007-05-20
I managed to get 4.1 by going opening alsa, turning on surround sound (edit -> preferences), turning that volume up, enabling "duplicate front", and checking that. Still can't get centre speaker working. Mobo is an Asus A8V deluxe.

---

