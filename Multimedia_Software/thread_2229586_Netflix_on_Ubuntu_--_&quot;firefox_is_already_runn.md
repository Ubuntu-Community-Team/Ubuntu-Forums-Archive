---
title: "Netflix on Ubuntu -- &quot;firefox is already running&quot;"
date: 2014-06-14
forum: Multimedia Software
---

### Post by JohnDillinger43 on 2014-06-14
I've gone through a lot of trouble to try to get Netflix to run on my Ubuntu laptop, with no success yet.  I've tried pretty much every suggested solution with pipelight, but I always end up with a Netflix page saying I need to either install or update Silverlight, and when I try to actually do that through Mono, I get the message that Firefox is already running.  Has anything dealt with this problem and resolved it successfully?  Everything I've looked at so far either says that this problem shouldn't occur, or that you must use Windows.

---

### Post by TheFu on 2014-06-14
I solved this with money - roku - after screwing around for a few weeks trying to get Amazon streaming working. For a netflix-loving household, I'd lean towards a $35 chromecast these days, if you have an android tablet that stays near the TV (it is the remote control). No remote is provided, hence why it is cheap.  There are sub-$50 alternatives as well.  The wireless streaming of the Chromecast does a good job of hiding wifi issues (buffering).  BTW, Mint worked with Amazon streaming out of the box, but I'd already spent the money.

The how-to-Geek has a guide to get netflix working on ubuntu: [http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/](http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/)  I never tried it, but it might be useful. It may be important which Ubuntu release you are running. Best to add that to the OP above.  Also - what have you tried so far?

---

### Post by SeijiSensei on 2014-06-14
All I've needed to do is follow the instructions here: [http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

```

sudo apt-add-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update
sudo pipelight-plugin --enable silverlight

```

Mono won't help.  It has none of the code needed to interface with Silverlight's DRM protocols.  The **wine-compholio** package installs a customized version of Wine with Microsoft's Silverlight DLLs and other required code.  However these packages do require updating from time to time.  Both wine-compholio and **pipelight-multi** were updated in the past week.  This happens automatically if you install the PPA as described in the article linked above.

---

### Post by JohnDillinger43 on 2014-06-28
I'll clarify some stuff I probably should have mentioned in the original post.  I'm trying to get Netflix working on my System76 laptop just to make things easier.  I do have a Blu-Ray player with a Netflix app, as well as a Chromecast, so it's not that I don't have any access.

What I've tried:
-installing netflix-desktop (tells me no installation candidate)
-installing wine-browser-installer (same thing)
-adding the compholio repository and then installing netflix-desktop: this works, but generates the "firefox is already running" error mentioned in the thread title
-installing pipelight: it says "silverlight is now enabled", but when I try to test it I'm instructed to download silverlight, which of course doesn't work
-installing the Chrome UA switcher: it identifies me as running FF on Windows, but again asks me to download silverlight

I also should mention that whenever I add compholio, I get errors from apt that "the cache contains no package named compholio" any time I run an update.  It's exceedingly annoying and so I always remove it when I'm not actively trying to figure out this issue.  It seems like there should be a fix that that issue as well.

In sum, I can get the netflix-desktop package installed, but it won't run, instead telling me firefox is already running.  I've run the typical pipelight instructions, but every time I try to use Netflix (with the wine-compholio package) I get instructions on how to download silverlight.

---

### Post by SeijiSensei on 2014-06-28
That error can happen when Firefox crashes.  Look in your Firefox profile ($HOME/.mozilla/firefox/yadayada.default) and delete any "lock" or ".parentlock" files that you see there.

---

### Post by JohnDillinger43 on 2014-07-01
There was indeed a .parentlock file in the folder, but after deleting it I still get the same error trying to run the Netflix app.  Trying it in a browser still gives me the old "Silverlight not installed" page.

---

### Post by monkeybrain20122 on 2014-07-01
Does silverlight work here [http://www.iis.net/media/experiencesmoothstreaming1080p](http://www.iis.net/media/experiencesmoothstreaming1080p) ?

---

### Post by Jake_A on 2014-08-13
> **JohnDillinger43 said:**
> I'll clarify some stuff I probably should have mentioned in the original post.  I'm trying to get Netflix working on my System76 laptop just to make things easier.  I do have a Blu-Ray player with a Netflix app, as well as a Chromecast, so it's not that I don't have any access.

What I've tried:
-installing netflix-desktop (tells me no installation candidate)
-installing wine-browser-installer (same thing)
-adding the compholio repository and then installing netflix-desktop: this works, but generates the "firefox is already running" error mentioned in the thread title
-installing pipelight: it says "silverlight is now enabled", but when I try to test it I'm instructed to download silverlight, which of course doesn't work
-installing the Chrome UA switcher: it identifies me as running FF on Windows, but again asks me to download silverlight

I also should mention that whenever I add compholio, I get errors from apt that "the cache contains no package named compholio" any time I run an update.  It's exceedingly annoying and so I always remove it when I'm not actively trying to figure out this issue.  It seems like there should be a fix that that issue as well.

In sum, I can get the netflix-desktop package installed, but it won't run, instead telling me firefox is already running.  I've run the typical pipelight instructions, but every time I try to use Netflix (with the wine-compholio package) I get instructions on how to download silverlight.

I have been going through the same issue with "NETFLIX STREAMING" I am running a fresh loaded version of "[SIZE=2]Ubuntu 14.04.1 LTS" I am new to Ubuntu and I am loving not beeing part of Microsoft. 
I have gone through all of the same steps as you stated above with a very similar outcome until I found the following freeware patch, 

    "User Agent Switch" by Chris Pederick    [http://chrispederick.com/work/user-agent-switcher](http://chrispederick.com/work/user-agent-switcher)    after I installed this it made Netflix Streaming possible through the Firefox  web browser
[/SIZE]
Make sure that you check the user agent override in the upper right corner of the firefox browser and pick the correct preference and click it on. 

I hope this works for you, 
Jake A

---

