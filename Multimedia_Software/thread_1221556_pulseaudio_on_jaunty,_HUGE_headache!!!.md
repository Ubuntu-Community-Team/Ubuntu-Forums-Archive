---
title: "pulseaudio on jaunty, HUGE headache!!!"
date: 2009-07-24
forum: Multimedia Software
---

### Post by kakyoism on 2009-07-24
I used to follow THE most famous pulseaudio fix post here on the forum and fixed pulseaudio problems on every machine I saw. However, after installing Jaunty on an HP pavilion, soundcard Intel G45 DEVCTG. Those tips that worked with Hardy never worked again. I tried a dozen solutions on the web, none of them are exactly the same. I edited a dozen system files, /etc/pulse/system.pa, /etc/default/pulse......... asoundconf, I switched stuff in system preference sound ... I installed libao......and lots of recommended stuff. None of them worked!

Now my pulseaudio daemon can be turned on, but when putting on rhythmbox and trying to play a song, a few seconds later pulseaudio crashed. I sometimes see the volume flux on pavucontrol, but after a few seconds it crashes along with daemon.


I'm really out of luck and idea now.

Anybody help??

---

### Post by igorzwx on 2009-07-24
You may try OSS4,
if your hardware is supported
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by markbuntu on 2009-07-24
What more exactly is going on?
No sound at all or no sound through pulse only or just some apps?
Are you using 64 bit or 32 bit?
Do you have all the updates?
What does aplay -l have to say?
Did you try this guide here

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

try running pulseaudio from a terminal with 

pulseaudio -vvv
so we can see what is going on.

---

### Post by kakyoism on 2009-07-25
update:

I got sound back by filling out my "model" in alsa-base.conf correctly

FYI

HP dv-3 laptop -> "dell-m4-1" in that file
for the line

```
options snd-hda-intel model=dell-m4-1
```


[BAD NEWS]

I now get a highly stuttering sound for any sound app and system sound no matter how I tune the default.pa, daemon.pa, with well suggested ways on this forum: tuning the fragment size, editing asoundrc, changing rt priority....

Wonder if it's an ALSA bug. People also suggested using OSS4, but I really don't know if OSS4 is the same as OSS. I remember OSS is not multiplex? I really need multiplex....

Any help would be appreciated.

---

### Post by martinbaselier on 2009-07-25
Ossv4 is multiplex. You can set the volume for each application.

---

### Post by kakyoism on 2009-07-25
thanks,

I've searched the forum but rarely see successful stories with OSS4, guess not enough people have tried, at least with Jaunty...

I'm sorry I need to see more yeah's to start switching,
but thank you anyways!

Guess I'll just wait till more complaints and QA's and feedbacks.....

---

### Post by igorzwx on 2009-07-25
Hi!

some info in Wikipedia -> OSS -> Open Sound System

and here
	  [Howto: OSS4 with Ubuntu Lite (Beta, netboot)]("http://www.4front-tech.com/forum/viewtopic.php?t=3237")

I am usually making such experiments on the old box,
to see how it works.

If you have not a box for experiments,
you may install another Ubuntu 9.04 in dual boot.

In any case, Martin may help better than I,
but he can be busy, as usual.

---

### Post by martinbaselier on 2009-07-25
> 
I've searched the forum but rarely see successful stories with OSS4, guess not enough people have tried, at least with Jaunty...

You rarely see success stories in forums. :) They are mostly used for asking help to solve problems. I never posted on any forum that linux recognized all my hardware and worked flawlessly after installing it. I expected it to do so. I never applaud when a plane lands for the same reason.

If you're willing to try, I'm writing a simple guide at the moment, including potential problems (I'm good at causing problems, which helps solving them) and instructions on how to remove it too. Somehow a lot of linux users seem to be afraid of new technologies. I would have thought linux less conservative than that.

---

### Post by markbuntu on 2009-07-25
There was lots of threads around here about OSS4 frm about a year ago, mostly X-fi users, but interest seems to have waned lately.

If you know anything about the history of OSS you would also understand some more about why it faces so much resistance. OSS was the standard for audio in linux for years until the lead devs took it private and started trying to charge money for it. Needless to say that caused a lot of bad will with the linux community. 

Now these same people are back with OSS4.
Would you trust them?

---

### Post by igorzwx on 2009-07-25
This is a very interesting question, indeed.

I do not trust anybody.
And the logic of your argumentation is not new for me.
It seems that your target is my personal freedom of choice.
I got a good dose of this in Soviet Union.
Nothing new, indeed.
Capitalism is bad, and, therefore, socialism is good.
This is a road to slavery, it is obvious for me.

---

### Post by markbuntu on 2009-07-25
You can do whatever you want. If you want to argue about philosophy:

[http://forums.philosophyforums.com/](http://forums.philosophyforums.com/)

---

### Post by igorzwx on 2009-07-25
I know that for many people of your generation
the freedom of choice is of little value.

But this is a practical question.
People would run away, if you deprive them of freedom.
And they are already running away.
I belive there should be three versions of Ubuntu:
1. Ubuntoss - for ordinary users
2. Ubuntalsa - for the advanced
3. Ubuntulse - for those who are far away

---

### Post by lavinog on 2009-07-25
> **igorzwx said:**
> 
I belive there should be three versions of Ubuntu:
1. Ubuntoss - for ordinary users
2. Ubuntalsa - for the advanced
3. Ubuntulse - for those who are far away

They sound too similar. How about: Obuntu, Abuntu, Pubuntu
For kde: KObuntu, KAbuntu, and PuKbuntu

---

### Post by igorzwx on 2009-07-25
The names should be effective, first of all.
It is not easy to invent good names.

---

### Post by igorzwx on 2009-07-25
Actually, "Obuntu, Abuntu, Pubuntu" is, perhaps, O.K.
a bit unusual, although.

---

### Post by snargfish on 2009-07-25
Try updating PulseAudio.

[https://launchpad.net/~themuso/+archive/ppa]("https://launchpad.net/%7Ethemuso/+archive/ppa")

---

### Post by andy16666 on 2009-07-25
I had this same problem AFTER manually installing pavucontrol to control individual application volume. The pavucontrol package seems to create problems as does the device chooser. Uninstall them, reboot and sound will work more reliably. 

I know this really sucks because those packages add nice features but apparently they aren't stable enough for regular use.

---

### Post by kakyoism on 2009-07-25
wow&#65292; thanks guys, especially the Mr. Obuntu, Abuntu....you left me with a smile on my face for the first time these days struggling with pulseaudio!

As for pavucontrol, unfortunately, i just tried a fresh installation of Jaunty first, then Intrepid, without pavucontrol. I got the exactly the same stuttering. So I believe it's the driver. And yes, OSS4 might be a good context switch, but I'd really love to see one of our HP laptop owners show up with a solid hope!

I think OSS vs ALSA battle is healthy though, any monopoly would slow down the progress of technology.

---

### Post by igorzwx on 2009-07-26
1. Obuntu = Ubuntu + OSS4
2. Abuntu = Ubuntu + ALSA
3. Apubuntu = Ubuntu + ALSA + PulseAudio
4. Opubuntu = Ubuntu + OSS4 + PulseAudio

---

### Post by martinbaselier on 2009-07-26
You could give it a try if the sound is not working properly anyway at the moment.

---

### Post by igorzwx on 2009-07-26
see:
[http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html](http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html)
QUOTE:
**Thursday, June 18, 2009**

   ** [State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html") **

   About two years ago, I wrote an article titled the "[The Sorry State of Sound in Linux]("http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html")", hoping to get some sound issues in Linux fixed. Now two years later a lot has changed, and it's time to take another look at the state of sound in Linux today.

---

