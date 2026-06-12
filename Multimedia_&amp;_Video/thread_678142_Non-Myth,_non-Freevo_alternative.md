---
title: "Non-Myth, non-Freevo alternative"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by Weidbrewer on 2008-01-25
I'm hoping that someone on here can help me.  I've played around with both MythTV and Freevo, but have found them both lacking in critical errors.  (Well, Freevo I just couldn't get working well.)  Myth is working fine for organization and playback of media, but I would like to back up all of my old VHS tapes on to a hard drive.  However, recordings coming in through the TV tuner card are *horrible*.   It's not just tapes, but live tv as well.   Tweaking things, I've been able to get the picture quality close to TVTime (which looks and sounds great) but the sound quality is still unbearable.  


I have a pcHDTV 5500 (so, no hardware encoding available.)  I am looking for either a program, or a script tutorial on how to just capture what's coming in through my card from the VCR (or TV) that has the quality of TVTime.  Any suggestions?

---

### Post by Weidbrewer on 2008-01-29
Nothing?   This seems to be a biggie with Ubuntu.   I've seen lots of people ask about it here and else-where, but no one seems to have anything but Freevo and MythTV.

---

### Post by phil90 on 2008-01-29
I know there is Elisa


[http://elisa.fluendo.com/](http://elisa.fluendo.com/)


Linuxmce

[http://www.linuxmce.org/](http://www.linuxmce.org/)


Mymediasystem

[http://mymediasystem.org/](http://mymediasystem.org/)


Sage Tv
[http://sagetv.com/](http://sagetv.com/)

---

### Post by Weidbrewer on 2008-01-29
Thanks for the response...however, I think that I might be missing something.  SageTV seems to be a hardware solution, and the other three seem to be just play-back, not recording.  What I need is something that can record from a TV tuner card at a respectable quality.   For playback, Myth is just fine.

---

### Post by steefjeqv on 2008-01-29
Hi,

VDR maybe worth your while.

It's mainly conceived around the (European) DVB standard.

It's not that straightforward to get going.
But it's a killer application (for DVB).

There is a version + some plugins available in the Ubuntu repos.


[http://www.cadsoft.de/vdr/]("http://www.cadsoft.de/vdr/")

[http://www.linuxtv.org/vdrwiki/index.php/Main_Page]("http://www.linuxtv.org/vdrwiki/index.php/Main_Page")

Greetings,
Steven

---

### Post by Weidbrewer on 2008-01-29
We're starting to get somewhere.  I will look in to that one.

One (presumably stupid) question:   Don't DVB apps only work with actual digital feeds?   As stated in my original post, I'm trying to back up some old VHS tapes, so the feed would not be digital.   Main reason that i ask is that I can't get any digital cable channels in the DVB settings of apps unless I have a set-top box hooked up as well.

---

### Post by steefjeqv on 2008-01-29
Hi,

One nice thing about VDR :
There's lots of plugins available to make it do lots of stuff.

Sometimes not so nice : getting these plugins to work.

Anyway, this might solve your problem, but I don't think it's available in the Ubuntu VDR version.
You can always try installing it from source.

[http://www.linuxtv.org/vdrwiki/index.php/Analogtv-plugin]("http://www.linuxtv.org/vdrwiki/index.php/Analogtv-plugin")

Greetings,
Steven

---

### Post by Weidbrewer on 2008-01-29
Nothing's easy, is it?  :)

I'll keep this one in mind if i don't find anything else.   


I must say, it really surprises me that there are so many options out there for complex solutions - by which I mean things like MythTV's record and watch at the same time features, but nothing "simple."

If TVTime can output such good quality, I'm surprised that no one has a simple "record" function.   Weird.

---

### Post by phil90 on 2008-01-30
Sagetv is actually a "Media Center, a personal video recording (PVR) and media center software package for Windows and Linux PCs, "

---

### Post by Weidbrewer on 2008-01-30
Yes, I figured that out when i gave it a better look last night.  Wasn't very obvious when I first looked at the page.  I might give it a try this weekend.

---

### Post by fenian on 2008-01-30
I have used Mythtv to import a few VHS tapes and have had no issues.I have used cards from Hauppauge , AverMedia as well as the pcHD5500.The pcHD550 was a little weird to set up ,you should look at the page[ here]("http://www.mythtv.org/wiki/index.php/PcHDTV_HD-5500#Other_analog_options") pay close attention to the other analog section.If you are trying to view video from VHS or analog tv on a HDTV you should be aware that it may not look very good at all.

---

### Post by phil90 on 2008-01-30
Sagetv is actually a "Media Center, a personal video recording (PVR) and media center software package for Windows and Linux PCs, "


Elisa does not record yet but they are working on it.


LinuxMCE does record TV, "Whenever you choose to record or save any media - TV shows, DVD movies, music, etc. - you are given the option of making it public, so the whole family can enjoy it, or private, so only you can access it. When you first get your LinuxMCE system, just be sure to tell"

---

### Post by Weidbrewer on 2008-01-30
> **fenian said:**
> The pcHD550 was a little weird to set up ,you should look at the page here

I had noticed that, and set things up accordingly  It made the picture quality better, but the sound was still terrible (just slightly less terrible than it had been before.)   This is why I was looking for a non-Myth option.   At least for the current generation of myth, I think that I have exhausted the capabilities of it.  It's good enough for some people, and that's fine.   It just doesn't seem to meet my needs for recording.

---

### Post by Weidbrewer on 2008-03-03
Okay, here is my update as to where I am:   I tried many of the suggestions above (thanks!), a number of other things - I also tried some mencoder stuff, and hijacking a local linux guru to work on it.....nothing paid off.   I was about to just say "screw it" and move on....but as one last-ditch effort, I erased the drive, installed Mythbuntu 7.10 with the Ubuntu desktop and.....it worked.

System still needs some tweaks, but at least they're tweaks.   It's no long, "This crap doesn't freakin' WORK!"


Thanks to all for the help.

---

