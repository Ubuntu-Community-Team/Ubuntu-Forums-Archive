---
title: "Still no sound whatsoever"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-04-09
First, a little history. I upgraded to Edgy Eft sometime in November last year. For some reason, this caused me to lose sound on a system that up until then had absolutely no sound problems at all. I then got a new PC, installed Edgy Eft again, and found I still had no sound.

That was now nearly six months ago, and I have gotten **NOWHERE** with this problem. At the moment, I'm reaching the point of desperation. Clutching at straws. Willing to do almost anything to fix this problem before it drives me permanently insane.

You may say to get a new sound card, but there are some problems with that:

a) That's not answering my question, that's avoiding it entirely.
b) We're low on money at the moment, getting this PC stretched funds pretty hard, getting more new hardware is pretty much out of the question for now.
c) Once we sell our house I *will* be getting a new PC and I don't want to upgrade the hardware on what will be a dead end pretty soon.

So on to what I know. I'm using Kubuntu 6.10 right now, the motherboard manual rather unhelpfully tells me I either have a Realtek ALC861VD or a Realtek ALC883 (either one would be integrated hardware), and Kubuntu does not detect any sound hardware whatsoever.

Getting this working on Kubuntu 6.10 now seems like a lost cause, so I'm more here to ask whether it'll work with anything else. Debian just got an update for once, will that do any better? Ubuntu Feisty is on the horizon now, do the test releases have anything resembling support in them? Does any other distro have even experimental support?

Imagine six months with no sound, poor video, and no one even seeming to be listening, and you have my situation. I'm desperate, willing to do anything no matter how crazy, and will gratefully take any suggestions.

Edit: I should've checked my old topics first. I may have solution to this, and it looks like Feisty Fawn will have native support.

---

### Post by Ambimom on 2007-04-09
Have you tried Dapper?  I had a lot of trouble with Feisty too, not sound, but other things.  I returned to Dapper and it works!

---

### Post by bmt on 2007-04-09
> **Rhapsody said:**
> ... I either have a Realtek ALC861VD or a Realtek ALC883 ...
There are many problems with these Realtek chips, I think.  (Just do a search on 'hda-intel' to see how many people are having problems.)  They are general purpose audio subsystems, with many features built-in to the actual chip.  So the chip can be configured in many different ways, according to what the motherboard manufacturer wants to provide.  Even the inputs and outputs can be either input or output -- so you may have sound coming *out* of a microphone input, for example.

This means that every different configuration must be allowed for in the ALSA drivers for a given audio chip, but this isn't possible unless users tell the developers what is happening in each case.

Have you tried compiling the ALSA drivers from the latest source?  (It's not difficult -- [this Ubuntu document]("https://help.ubuntu.com/community/HdaIntelSoundHowto") will walk you through it.

If that doesn't make any difference, file a bug against Ubuntu (in Launchpad) and/or go and register at the ALSA site and file a bug there.  There is no other way, other than waiting for someone else, who has exactly the same hardware, to go and do it for you.  This is your opportunity to contribute, so that another user, some time in the future, can say 'wow, this Linux is great, my sound just worked straight out of the box'.

The changes need to be made in the ALSA drivers, so no other Linux distribution will be any better than what you can do for yourself with the latest sources.

---

### Post by PurplePenguin on 2007-04-09
I hope that Feisty will solve your problem.  Have you tried running the beta live disc?  If not, there's no shame in your first option (getting a sound card) - sometimes you just can't get support for certain pieces of hardware.  That's life!  

If you need a sound card but don't have the cash, I'm sure somebody will send you one for the cost of shipping.  Everybody's got old machines and old cards hanging around.  They give soundblaster cards away in cereal boxes these days, don't they? ;)

---

### Post by BHelts on 2007-04-09
Hello, I had the same problem with edgy.  I went through the HDA_INTEL howto that was posted earlier in this thread ([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)) and what got me going was the last step, configuring /etc/modprobe.d/alsa-base so that it read options snd-hda-intel model=fujitsu.  the specific options for your realtek chipset are in alsa-kernel/Documentation/ALSA-configuration.txt.  i am using a toshiba tecra A8 laptop, so it was strange that fujitsu was what got it working, but i had to try three other model= options before i got it to work.  hope this helps.

---

### Post by filterpipe on 2007-04-10
This seems to have solved the problem in the case of a
Toshiba Satellite A100-SK4 (PSAA8C-SK400E): Followed
the [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
document, but, unlike that document suggested, I appended
this line to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=auto

I had tried model=toshiba, but that didn't work.

On the other hand, I've only rebooted the laptop twice since
the model=auto line was added, so the fix might be illusory.\

---

### Post by yj09 on 2007-04-11
I also got same problem.. realtek alc262 running on fujitsu laptop.. trying on both edgy and feisty and with latest alsa driver..but still no sound on internel speaker. anyway sound are available on phone jack. just connect to external speaker. but hopefully there are solution coming to solves these problem..

---

### Post by locolbd on 2007-04-11
LOL i must say i have had this problem and i almost lost my mind, but reading this thread really helped me, now my sound play a ok.

What i did was configured /etc/modprobe.d/alsa-base so that it read options 

snd-hda-intel model=3stack-dig

this really helps alsa-kernel/Documentation/ALSA-configuration.txt

---

### Post by suseHacker on 2007-04-18
This hack  also works on the HP dc7700, which with the Realtek alc262 chipset the Line Out does not work at all, when the headphone jack does work.

I ended up using: snd-hda-intel model=hp-bpc

The frustrating part of this whole thing is, that Realtek's linux drivers DON'T WORK on their own Chipset.

The alsa driver, 1.0.13rc3 is what I ended up using.

They go to such great lengths to emulate intel, but there are still a few gaps.... ;)

--Cheers

---

### Post by fastb on 2007-04-19
I folloved the instruction given on that link but there were errors compiling alsa drivers:

```
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.14rc1  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/src/alsa/alsa-driver-1.0.14rc1/acore/pcm.o
In file included from /usr/src/alsa/alsa-driver-1.0.14rc1/acore/../alsa-kernel/core/pcm.c:29,
                 from /usr/src/alsa/alsa-driver-1.0.14rc1/acore/pcm.c:1:
/usr/src/alsa/alsa-driver-1.0.14rc1/include/sound/pcm.h: In function ‘snd_pcm_mmap_data_open’:
/usr/src/alsa/alsa-driver-1.0.14rc1/include/sound/pcm.h:977: error: dereferencing pointer to incomplete type
/usr/src/alsa/alsa-driver-1.0.14rc1/include/sound/pcm.h: In function ‘snd_pcm_mmap_data_close’:
/usr/src/alsa/alsa-driver-1.0.14rc1/include/sound/pcm.h:983: error: dereferencing pointer to incomplete type
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.14rc1/acore/pcm.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.14rc1/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.14rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2

```

Can anyone help me

---

### Post by ububaba on 2007-04-19
I have tried every suggestion and advice to get the sound working. Have found no solution even after
several weeks of struggle. Feisty users, would you suggest it would be a better choice than Edgy?
Would love to have a frank opinion. Promise, I won't get hurt.):P

---

### Post by You bunt to? on 2007-04-19
> **ububaba said:**
> I have tried every suggestion and advice to get the sound working. Have found no solution even after
several weeks of struggle. Feisty users, would you suggest it would be a better choice than Edgy?
Would love to have a frank opinion. Promise, I won't get hurt.):P

I'm having the same problems! Reading between the lines, it seems to be a code war between ALSA and OSS and the decision is a recent kernel change (2.6?) to abandon OSS in favour of ALSA, mainly because OSS is a commercial product. Read [http://4front-tech.com/hannublog/](http://4front-tech.com/hannublog/) for more background. I'm dumping Ubuntu for the moment but will continue to watch these and other conversations. One thing is very clear -- an awful lot of people are struggling with sound problems. What really surprises me is that nobody in the Linux community has suggested designing (and selling) a sound card, geared specifically to this OS. It can't be that difficult, with all these very smart people around but I suppose it goes against the grain, the "freeware" grain, that is. I would be interested to hear (no pun intended) if sound problems exist on other (other than x86) platforms, where the big boys play?

..now back to Win2k

---

### Post by ububaba on 2007-04-19
> **You bunt to? said:**
> I'm having the same problems! Reading between the lines, it seems to be a code war between ALSA and OSS and the decision is a recent kernel change (2.6?) to abandon OSS in favour of ALSA, mainly because OSS is a commercial product. Read [http://4front-tech.com/hannublog/](http://4front-tech.com/hannublog/) for more background. I'm dumping Ubuntu for the moment but will continue to watch these and other conversations. One thing is very clear -- an awful lot of people are struggling with sound problems. What really surprises me is that nobody in the Linux community has suggested designing (and selling) a sound card, geared specifically to this OS. It can't be that difficult, with all these very smart people around but I suppose it goes against the grain, the "freeware" grain, that is. I would be interested to hear (no pun intended) if sound problems exist on other (other than x86) platforms, where the big boys play?

..now back to Win2k
Thanks for response. Had no idea about the *unfriendly fire*.  Let's see who benefits from this 
war of territory. You may have a point that it appears to be a cavalier attitude of the movers 
and the shakers that the discussions border on what seems to a bit chatic. If people decided 
to abandon Ubuntu that would not be a positive development. It is your own choice.

---

### Post by seesixty on 2007-04-19
I've just installed 7.04 on a toshiba satellite A100 and sound no work.
I installed hurd 5 on a different satellite A100 earlier in the week and could only get sound if I was using 2.6.20-9  But the release of 7.04 doesn't give me the option to downgrade my kernel, so I'm stuck with no sound.

So my shot in the dark is it's something related to the kernel modules, since it is working on 2.6.20-9.

---

### Post by You bunt to? on 2007-04-19
> **ububaba said:**
> Thanks for response. Had no idea about the *unfriendly fire*.  Let's see who benefits from this 
war of territory. You may have a point that it appears to be a cavalier attitude of the movers 
and the shakers that the discussions border on what seems to a bit chatic. If people decided 
to abandon Ubuntu that would not be a positive development. It is your own choice.

I've found some references ([http://www.thisishull.net/archive/index.php/f-13.html](http://www.thisishull.net/archive/index.php/f-13.html) - search for "alsa")  that confirm that OSS was only available up to the 2.4 kernel, and thereafter ALSA:

[http://www.thisishull.net/archive/index.php/t-28818.html](http://www.thisishull.net/archive/index.php/t-28818.html)

"Yes - ditch alsa. It's a POS that will give you lots of headaches. You'd better rebuild your kernel with the 2.4.* drivers instead."

"The only thing predictable about alsa is that it will mess things up. Why is it that such underperforming software has been selected as the preferred sound software for Linux? Fortunately, for 2.4.* kernels one can still use the OSS drivers - which may not be quite as nicely architected as the alsa ones, but at least they are not a pain in the butt."

"What really annoys me is that we have been repeatedly told, for years now, that the OSS drivers are messy, incomplete, buggy, you name it; and that ALSA is wonderful. Maybe one day it will, but for the time being, it ain't - and it trails OSS in general usability."

Those remarks were in 2004, 3 years ago, by guys who obviously know their way around in Linux (in this case Slackware) so you can imagine the hardships a mere Noob suffers.

Of course there is a very well written [http://www.linux.com/howtos/Soundblaster-AWE.shtml](http://www.linux.com/howtos/Soundblaster-AWE.shtml) but when you examine it ( [http://www.linux.com/howtos/Soundblaster-AWE-6.shtml#ss6.1](http://www.linux.com/howtos/Soundblaster-AWE-6.shtml#ss6.1) - 6.2 Sources ) you'll find they were using the 2.029 kernel! -- in 1997!

---

### Post by AhronZombi on 2007-04-20
I have a toshiba laptop. none of the guides worked at all for me, and i saw on the lauchpad that it was a kernel bug and the fix has not been streamed into updates yet. So what i did for a work around is install the debian etch kernel, and compile and install the madwifi and fglrx modules from source. its really shameful that the ubuntu people couldnt fix such a big bug before the final release cd came out, considering it worked fine in some of the beta kernels. O well if Xgl was easyer to install on etch id switch, hope ubuntu gets on track soon

---

### Post by bmt on 2007-04-23
> **You bunt to? said:**
> Those remarks were in 2004, 3 years ago ...
Exactly, so stop spreading FUD.  Three years is a *very* long time in any computer environment. Quoting something that old and suggesting that it is relevant today is just ridiculous.

---

### Post by You bunt to? on 2007-04-23
> **bmt said:**
> Exactly, so stop spreading FUD.  Three years is a *very* long time in any computer environment. Quoting something that old and suggesting that it is relevant today is just ridiculous.

I don't have to spread it, it's up to our knees already. Do a Google search for Linux "sound problem" (118k  hits), search for Windows "sound problem" (216k hits). Considering that Windows has 90% of the market (some say more) that's an amazing result for Linux. Not very scientific, yet the trend is clear: Linux sound sucks!

Does Linux dictate which editor you use? OF COURSE NOT! Does Linux dictate which browser you use? OF COURSE NOT! etc, etc  Does Linux dictate the usage of OSS and ALSA?  YES, YES, YES
(with apologies to 'My Fair Lady')

---

### Post by bmt on 2007-04-24
> **You bunt to? said:**
> Does Linux dictate the usage of OSS and ALSA?  YES, YES, YES
Well, NO, actually.  Just because some parts are in the kernel doesn't mean that you have to use them.  Some of the other parts of a *distribution* may get in the way of ditching ALSA (Gnome sound daemon comes to mind), but you can certainly do it if you want to.

---

