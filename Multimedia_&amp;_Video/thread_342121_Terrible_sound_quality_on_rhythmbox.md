---
title: "Terrible sound quality on rhythmbox"
date: 2007-01-19
forum: Multimedia &amp; Video
---

### Post by zeeR on 2007-01-19
The sound quality when I make the volume high on Rhythmbox is terrible, crispy and grainy...

I tried the same on Beep Media Player, which is using Alsa, according to its settings, and the quality is perfect...

How can I make Rhythmbox have good quality?

On Dapper, everything worked fine...I'm seriously thinking of downgrading =\

On the " Comprehensive Sound Problem Solutions Guide ", all I can find are solutions for users with NO SOUND at all...

---

### Post by zeeR on 2007-01-19
Bump...

---

### Post by deadgobby on 2007-01-19
It sound like you may need to play with the sound levels. It is like sound card levels + Applications sound levels = distorted sound. The best way I can come up with is turn down the card card level and the programs like Beep. Slowly turn up the levels.
I know it it may sound silly. Or that you may have the head phone in the wrong jack,
Gobby

---

### Post by zeeR on 2007-01-19
> **deadgobby said:**
> It sound like you may need to play with the sound levels. It is like sound card levels + Applications sound levels = distorted sound. The best way I can come up with is turn down the card card level and the programs like Beep. Slowly turn up the levels.
I know it it may sound silly. Or that you may have the head phone in the wrong jack,
Gobby

On previous linux installs, this didnt happen...and Beep isn't a Library player, so it doesn't organize the music by artist, album, etc...

When I use Rhythmbox with the volume over half way, the sound obviously gets better..but still, when the music is too loud, it distorts the sound, and it's really annoying..=\

---

### Post by sgx on 2007-01-19
> **zeeR said:**
> The sound quality when I make the volume high on Rhythmbox is terrible, crispy and grainy...

I tried the same on Beep Media Player, which is using Alsa, according to its settings, and the quality is perfect...

How can I make Rhythmbox have good quality?

On Dapper, everything worked fine...I'm seriously thinking of downgrading =\

On the " Comprehensive Sound Problem Solutions Guide ", all I can find are solutions for users with NO SOUND at all...

Rule #1, if it ain't broke, don't upgrade it...really, incremental upgates
offer little for anyone with a working system. Were you promised
breathtaking speed increases? Massive numbers of new miraculous
applications? All audio/video bugs erradicated? The truth on my computer is that linux has bloated and gloated, and lost its competetive edge. The many new distros I try all have serious design blunders, ruining the joy and satisfaction one might expect with promised 'major improvements', which is living proof that hundeds of stubborn, unfunded experts can arrogantly insist that only 'my way' is worthy, so I won't team up with the other unworthy ones...please do go back to a working version, and enjoy your music collection, and mail that new and wonderfully silent frisbee back to Ubuntu, COD...like we really want a hunded bugridden distros, upgraded willynilly, rather
than a couple that are stable and fully functional 365 days a year...

---

### Post by zeeR on 2007-01-20
Maybe you are right on some things...

But I'd rather not reinstall Linux again =\ ...And I like Edgy, if only I could solve this problem...

---

### Post by jimbobjones on 2007-02-04
you need a media player with an equalizer to improve the sound quality

Amarok will do the job

though i switched to beep as its gives the best sound quality imo

---

### Post by WinterWeaver on 2007-02-04
I noticed the same problem with my Rhythmbox, and therefore I don't use it anymore. I now use Amarok.

It seems that it only happens on certain songs though. Is this the same in your case?
the other think about my problem, is that it's only the Left speaker which distorts. O.o

I believe that there is too much base being pushed through the one speaker only.

anyway, that was my solution, install amarok, and dump rhythmbox, it worked for me.

---

### Post by 3kravinarayan on 2007-02-05
simple  change over to amarok  rhythymbox is quite sad   

amarok will sound great and has a great interface plus a good equaliser    :guitar: 

Ravi

---

### Post by tortsto on 2007-02-17
I read somewhere a while ago that for some reason on the volume control, Ubuntu goes over the max.  So like if you slide it all the way to the top, it's at 110% output.  I'm having great results capping both master volume, PCM volume (right click the sound applet to access advanced sound control), and Rhythmbox volume at 70%.  From then on it's got be hardware.  I was going to poke out my speakers if I couldn't resolve this problem, so thank goodness I found out how to fix it.

---

### Post by FactTech on 2007-03-10
I'm experiencing the same problem using a Riptide PCI Audio controller on an HP Pavilion 8570c running Ubuntu 6.10 with all updates as of Mar 09 2007.

It appears that the issue is specific to the ALSA subsystem, if you switch to ESD, Rhythmbox will play without the static. Go to System, Preferences, Sound, and under the "Music and Movies" section, switch from "Autodetect" to "ESD".

I still notice the occasional minor faint click in the background, especially when starting a new song, but it's MUCH better.

If I ever figure out a fix for the overall ALSA issue, I'll come back and post it.

---

### Post by camellochapin on 2007-03-23
[FONT="Comic Sans MS"][COLOR="MediumTurquoise"][B]I had the same problems, although I am also a Linux-beginner, I tweaked the "volume control"... exaclty the PWM settings... just don't put it in 100%, reduce it a little bit and voilá... you start getting good sound-quality!!

Hope it works for you[/B][/COLOR]![/FONT]

---

### Post by regomodo on 2007-04-24
I thought i'd add my solution to my problem. I thought it was the sliders at max problem but l later found out it was a  gstreamer codec problem

Here's the link to the thread [http://ubuntuforums.org/showthread.php?t=394661](http://ubuntuforums.org/showthread.php?t=394661)

---

