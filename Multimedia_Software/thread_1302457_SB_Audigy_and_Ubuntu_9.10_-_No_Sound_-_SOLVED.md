---
title: "SB Audigy and Ubuntu 9.10 - No Sound - SOLVED"
date: 2009-10-27
forum: Multimedia Software
---

### Post by TBerk on 2009-10-27
OK, I had a world of trouble getting 9.04 to work with my Sound Blaster Audigy 2 sound card.  But eventually I got it working.

During the update to Ubuntu 9.10 I formatted the / Partition (my /Home resides on a another partition, I mention this because in my case a LOT of my previously configured apps just 'worked' post 9.10 Install. Not all, but most...)

Right after 9.10 came to rest, being all patched and everything, I noticed I had No Sound; not system sounds, no wave file, no DVD Audio, etc.

I poked and prodded, installed the medibuntu files, non-free codecs, ALSA and it's gui Mixer- lots of stuff, but still No Sound.

Finally I was noticing most stuff ref'd AUDIGY;

```

02:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs Device 1006
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at dc00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

```

but the Applications:Sound & Video:Gnome ALSA Mixer was talking **SigmaTel STAC9721,23** .

A Google search turned up a lot of references to Ubuntu and Sigmatel, esp the Digital/Analog toggle being *inverted* as far as **Mute**, so I tried it- And it worked!

{For Example}
> 
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg301043.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg301043.html)

-----Original Message-----
From: [EMAIL PROTECTED] [EMAIL PROTECTED] Behalf Of
Daniel T Chen
Sent: 24 April 2007 15:25
To: [EMAIL PROTECTED]
Subject: [Bug 107863] Re: no sound: Audigy card, SigmaTel STAC9721 mixer


This looks like a candidate for the inverted digital toggle issue - that
is, try muting 'Audigy Analog/Digital Output Jack'.


I have a bug-report out there I'm going to have to follow up on (it was self reported out of something to do with 'Python', but it now seems unrelated...), Also I think I have at least one thread in 'Installs' related to No Sound as well to close off.

I hope this helps somebody.


berk

---

### Post by rogercruse on 2009-10-27
Thank you. My sound now works!

Now if you would just like to give me the lottery numbers...

---

### Post by TBerk on 2009-10-28
> **rogercruse said:**
> Thank you. My sound now works!

Now if you would just like to give me the lottery numbers...


I was going to go on and on about the number Three, but then I'd want a cut....



berk
it all goes back to this stage play I saw re: Buckyballs,,

---

### Post by abitwise on 2009-10-31
Yeah, this was it, Thanks alot! :popcorn: Basically what you need to do (2.0 style, without terminal):

1. Istall GNOME Alsa Mixer (synaptic: gnome-alsamixer)
2. Run it like this: Applications -> Sound & Video -> GNOME ALSA Mixer
3. Choose the tab: "SigmaTel..."
4. Turn on "Audigy Analog/Digital Output Jack

That's it, your sound is working again! Don't look for the other solutions like installing pulseaudio or purging all the configuration, that doesn't work and you just loose your quality time (i did - 2 hours of it).

Problem was: No sound after upgrading from Ubuntu 9.04 to 9.10.

---

### Post by abitwise on 2009-10-31
1.0 style in this post..

I also wanted to say, if you have some kind of quality issues, then try this (Sound Blaster Audigy users): [http://ubuntuforums.org/showpost.php?p=6066790&postcount=5](http://ubuntuforums.org/showpost.php?p=6066790&postcount=5)

After configuration change restart pulseaudio:

[http://ubuntuforums.org/showpost.php?p=6892782&postcount=2](http://ubuntuforums.org/showpost.php?p=6892782&postcount=2)

---

### Post by bezolaam on 2009-10-31
Thanks for  this solution, but it's to late personally for me. I wasted 2 days to solve this in different ways but no result.
So, I just returned to 9,04 today, because 9,10 is to buggy for me yet :(

---

### Post by prj44 on 2009-11-02
THANK YOU TBerk.  Changes provide full sound for my Audigy 

Much appreciated.

---

### Post by king2007 on 2009-11-03
> **bezolaam said:**
> Thanks for  this solution, but it's to late personally for me. I wasted 2 days to solve this in different ways but no result.
So, I just returned to 9,04 today, because 9,10 is to buggy for me yet :(
think so too, cause it is getting way much too much time to solve this sound-problem. had the same issue when upgrading from the earlier version into 9.04

---

### Post by TBerk on 2009-11-19
(somebody mentions devolving back to 9.04 from 9.10 because sound no-workee...)

> **king2007 said:**
> think so too, cause it is getting way much too much time to solve this sound-problem. had the same issue when upgrading from the earlier version into 9.04

Well, actually I had a much longer time w/ 9.04 getting the Sound Blaster Audigy2 to 'put out'.  It was partly the same trouble, but more. (I'd have to search archives to remember it all...) There were at least three aspects of failure to contend with.

It might just be plausible, in my case, due to my retained & separate /HOME partition (w/ it's pre-existing/retained settings and config files) that were saved from the oblivion that was a 'clean' install of 9.10; maybe that helped in my case.


berk

---

### Post by gkh73 on 2009-11-23
Just a friendly reminder... because this happened to me... once you follow the helpful instructions above, scroll across all your sound input/output options.
I followed the advice above and still didn't have any sound until I scrolled over to the far right to discover that my PC speakers were muted.  I clicked off mute and my sound is up and running!  :)
By the way, thanks to all you posters who make my life much better!   Ubuntu Forums=best/friendliest forums on the interwebs!

---

### Post by CRIMPS on 2009-11-28
> **abitwise said:**
> Yeah, this was it, Thanks alot! :popcorn: Basically what you need to do (2.0 style, without terminal):

1. Istall GNOME Alsa Mixer (synaptic: gnome-alsamixer)
2. Run it like this: Applications -> Sound & Video -> GNOME ALSA Mixer
3. Choose the tab: "SigmaTel..."
4. Turn on "Audigy Analog/Digital Output Jack

That's it, your sound is working again! Don't look for the other solutions like installing pulseaudio or purging all the configuration, that doesn't work and you just loose your quality time (i did - 2 hours of it).

Problem was: No sound after upgrading from Ubuntu 9.04 to 9.10.


Hmm, for me, I unchecked/disabled the "Audigy Analog/Digital Output Jack".  I can't believe this was the problem!  Same here in that I upgraded from 9.04 to 9.10.  

Thanks!!!

---

### Post by svenakela on 2009-12-18
Oohh... I've been struggling with this.
The Gnome mixer-enable-thing solved it for me as well. :)

---

### Post by Hawk__0 on 2010-01-21
Thanks a lot for this, however my situation was slightly different.  I had to unmute "analog C", "audigy a" and turn up the volume on "analog M" and "analog C".  I'm not sure which of these did it but I did all 4 and it works :D

I used the commandline "alsamixer" utility

---

### Post by andvary88 on 2010-04-29
Turning on "Audigy Analog/Digital Output Jack" worked just fine for me. Thanks!

---

### Post by TBerk on 2010-05-09
Just a follow up: After I upgraded to 10.04 (Lucid) I found I was soundless, again.  Toggling the same Digital/Analog jack button fixed the problem.


berk

---

### Post by TBerk on 2010-10-13
> **abitwise said:**
> Yeah, this was it, Thanks alot! :popcorn: Basically what you need to do (2.0 style, without terminal):

1. Istall GNOME Alsa Mixer (synaptic: gnome-alsamixer)
2. Run it like this: Applications -> Sound & Video -> GNOME ALSA Mixer
3. Choose the tab: "SigmaTel..."
4. Turn on "Audigy Analog/Digital Output Jack

That's it, your sound is working again! Don't look for the other solutions like installing pulseaudio or purging all the configuration, that doesn't work and you just loose your quality time (i did - 2 hours of it).

Problem was: No sound after upgrading from Ubuntu 9.04 to 9.10.



Just another Follow up; I had to use the 'code' above to get the mixer back on a new install of Meerkat Maverick.  The video I had playing immediately started putting out sound as I toggled the 'digital Jack'.


TBerk

---

