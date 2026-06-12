---
title: "Streaming video problem"
date: 2013-04-28
forum: Multimedia Software
---

### Post by billcauley on 2013-04-28
After the upgrade to 13.04, I am no longer able to view online video.  A picture (see attachment) is there, and there's sound.  The computer is an older P4 2.4Ghz using integrated graphics.  Since it worked before the upgrade, I'm thinking that Adobe Flash got changed to not include older machines.

[ATTACH=CONFIG]241927[/ATTACH]

---

### Post by Rich55 on 2013-04-29
I'm having a similar problem with video. Dell Dimension 2400 P4 2.8Ghz integrated graphics with 1mb ram
I updated from xfce 12.10 to 13.04 using the software updater and have a similar issue with flash video.
I thought the upgrade might have not gone smoothly so I downloaded xubuntu 13.04. 
Formatted the hard drive first using Gparted and did a fresh install. 
I did the software update after the install and then installed restricted extras. I have rebooted and the problem still persists. 
I hope this info helps with a bug fix
Thanks
I am in awe of the technical knowledge of people on this forum

---

### Post by billcauley on 2013-04-29
>>I did the software update after the install and then installed restricted extras. I have rebooted and the problem still persists.

Same here.  After installing, removing, reinstalling various combination, I still can't correctly see the videos, though the sound is all right.  It seems to be a codec problem that occurred after the update to 13.04, as all worked fine before.

I'm sure an answer will be provided shortly.

---

### Post by Resistent on 2013-04-29
Try another Web Browser, for example Chromium shows you Flash Videos, but not with the Adobe Flash Player.
When you use Chrome, then it will use the Adobe Flash Player... 
--> ups , that 's not the situation any more.. 

Try alternatives:
[h=1][Is there an alternative to Adobe Flash?]("http://askubuntu.com/questions/163439/is-there-an-alternative-to-adobe-flash")[/h][http://askubuntu.com/questions/163439/is-there-an-alternative-to-adobe-flash](http://askubuntu.com/questions/163439/is-there-an-alternative-to-adobe-flash)

---

### Post by Rich55 on 2013-04-29
Just tried Chromium no go. I could try an alternative to Adobe Flash but have no experience doing that and I believe this bug can be fixed.
I have limited knowledge as is evident.....
Got my first Bean today ha ha. 
Seriously this is the first time I have had to ask for help because this forum almost always has an answer.
It may be on another post and I just haven't found it yet.

---

### Post by billcauley on 2013-04-29
I've tried it with Firefox, Epiphany, and Chromium.... no luck!  Also, the videos in news feeds give the same unpleasant result.

A comment at Askbuntu reads: "I have played with Gnash and Lightspark on different distros and different machines. My conclusion is that they are complete waste of time. They never work except for a few demos. I see people recommending them on many Linux sites, either they have better experience somehow or these guys have never tried it themselves."

So I didn't bother with the flash alternatives.  BTW, every comment here rules out something, and is therefore useful.  Thanks.

---

### Post by monkeybrain2012 on 2013-04-29
Here is a flash replacement that would work on Youtube and a few supported sites. Install Greasemonkey addon for Firefox and then install the script. It also works on Chrome (have to install the temparmonkey addon)

[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

There is another
[http://linterna-magica.nongnu.org/#download-unstable](http://linterna-magica.nongnu.org/#download-unstable)

It works on more sites but the downside is on rare occasions may freeze your browser (because it works on sites that are not even supported so sometimes it may tie up the machine to parse too many flash objects I think). The work around is to exclude those sites in Greasemonkey or Tampermonkey's settings. 

In my experience gecko-mediaplayer is recommended as a backend for Firefox and Totem for Chrome (because gecko-mediaplayer doesn't load in Chrome for some reasons)

---

### Post by billcauley on 2013-04-30
Before I attempt to work with the Flash replacements, I'd like to find the answer as to why my computer isn't properly using the installed Flash.  I can see the video (sort of) and the sound works.  I would think that it is being used by others, some with the same configuration as mine (or maybe not).

This has been the cleanest distribution upgrade in my six years of using Ubuntu, and a fix usually happens after the correct person(s) sees the query.  Here's for hoping!;)

---

### Post by Rich55 on 2013-04-30
I just did an install of lubuntu and video playback is still not working. 
Other than the video playback everything else I have tried on both distros
appears to be smoother and faster. 

My thanks to all those that work on this project you are amazing

---

### Post by monkeybrain2012 on 2013-04-30
May be you can try different flash settings (right click on a flash video and see the menu) I have tested and found  no problem with flash (both FF and Chrome) on several 13.04 installations, though as I said, I normally don't use flash for sites where those scripts work.

---

### Post by Rich55 on 2013-04-30
Thanks monkeybrain, I had tried that but the settings menu comes up distorted also and I am unable to make selections.
I also uninstalled Adobe flash plugin and reinstalled it from the software center. I had originally installed restricted extras using 
apt-get from the terminal. I have reverted back to 12.10 for the time being. I will continue working on this issue until resolved as others may be experienceing a similar problem.

---

### Post by wojeda on 2013-04-30
Hmmm... I have Kubuntu 13.04  running Chrome with flash and have no problems streaming video and audio. Even through HDMI out.
All I did was create a sym-link in the plugins directory to the .so of the flash install directory.

---

### Post by billcauley on 2013-04-30
In my System Setting, Details, Graphics, it says "Driver - Unknown, Experience - Fallback.  This could be the problem!  Before the dist-upgrade, it showed the driver's Intel integrated motherboard designation.  What do you all think?  And, how is that fixed?

---

### Post by Rich55 on 2013-05-01
Bill I'm not able at the moment to try this (perhaps you already did). I could not uncheck the hardware acceleration tick box using youtube maybe you could give it a try and report back. 
Thanks in advance 
Rich

- surf to the website [http://moodstream.gettyimages.com](http://moodstream.gettyimages.com)
(or to another website with a certain kind of Flash content; not Youtube, because it has a different kind)

- wait until the content of the website has been loaded

- right-click mouse on the window - Settings - remove the tick for:
[COLOR=#0000FF]Enable hardware acceleration[/COLOR]

---

### Post by billcauley on 2013-05-01
Ah, there's the rub.  I see it (barely), but the image is distorted to the point of not being able to focus on the box to unclick it.

---

### Post by monkeybrain2012 on 2013-05-01
You seem to have a graphic driver problem, I don't know how old your card is. If it is old may be the new driver doesn't support it, or may be you need newer driver because the default one has bugs..

---

### Post by billcauley on 2013-05-01
Integrated graphics on an old Intel 845G motherboard.  I agree that the problem is that it's not "fully" supported, as everything works fine except streaming videos.  If no workable solutions show in the next few day, I'll just replace it.  Thanks for your help!

---

### Post by billcauley on 2013-05-02
Decided to use the prior kernel 3.5 instead of 3.8, and whatdayaknow, the driver Intel® 845G x86/MMX/SSE2 is no longer "unknown", and streaming video works.  Don't know why I didn't try that at first!

Kernel 3.8 will more than likely work after the first kernel update.

I'll consider my issue SOLVED, but I don't see how to mark the thread as such.

---

