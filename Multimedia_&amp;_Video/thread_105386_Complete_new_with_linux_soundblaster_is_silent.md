---
title: "Complete new with linux soundblaster is silent"
date: 2005-12-18
forum: Multimedia &amp; Video
---

### Post by msitua on 2005-12-18
Hello, I have installed ubuntu today.

I do not hear sound, I have a Soundblaster pci card.
It sayes under system devices that "SB audigy LS" is found

Under audiosettings two cards are possible options one intel... which I guess is the build in on motherboard and it finds CAxxxxxxx where x stands for numbers.

Were do I start, I have not yet learned to use teminal window, so if you have advice please explain exactly what to do.

Shall I do comments in ASLA?

Thank you for help

---

### Post by mlomker on 2005-12-18
The first thing to check is all of the levels in **alsamixer** from a terminal.  If you search on that tool you'll find quite a few references on here.

---

### Post by msitua on 2005-12-18
Thank you, one step away from sound

I have trying out alsamixer
and now I hear uduntu sound but I can not play music because it is "lagging" music paus music paus .. etc

Thank You
Robert

---

### Post by mlomker on 2005-12-19
In KDE you can set the priority of the sound server to a higher setting to sometimes resolve that.  You might want to create a new post for this new issue (lots of people just read the Title's, so pick it well).

---

### Post by kathymacau on 2005-12-21
[QUOTE=msitua]Thank you, one step away from sound

I have trying out alsamixer
and now I hear uduntu sound but I can not play music because it is "lagging" music paus music paus .. etc

Thank You
Robert[/QUOTE]

I had the same problem.  I found that if I use Totem the sound is good, I think you need to try out various players to find what works for you.  I am using Soundblaster .

---

### Post by kathymacau on 2005-12-21
[QUOTE=kathymacau]I had the same problem.  I found that if I use Totem the sound is good, I think you need to try out various players to find what works for you.  I am using Soundblaster .[/QUOTE]

Must update, start XMMS open preferences set your output to ALSA.  I did and sound is good.

---

### Post by Cprav on 2005-12-22
Hi, Okay I'm sorry for hijacking this thread.  I am having the same problem.  First I tried to do the terminal thing.  I couldn't find a search option, so I just typed in alsamixer and I got this: 
alsamixer: function snd_ctl_open failed for default: No such file or directory

Then I scrolled further down the thread and tried just changing the options to alsa in the multimedia systems selector.  I tried all the of the options there and tested them and none of them worked.  (ESD, Alsa, and OSS).

So, what should my next step be?

Thanks in advance!

---

### Post by lawchilly on 2005-12-24
I have this problem with Default Source - none of the options work :???:

---

