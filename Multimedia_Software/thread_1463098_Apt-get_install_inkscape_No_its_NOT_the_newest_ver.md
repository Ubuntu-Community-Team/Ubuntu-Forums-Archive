---
title: "Apt-get install inkscape???? No its NOT the newest version!"
date: 2010-04-26
forum: Multimedia Software
---

### Post by Inprogress on 2010-04-26
Hello there.

Could some one please help a linux noob here.

I see (been using Inkscape for couple of weeks now) that there are features that I want to harness in Inkscape 0.47. I have 0.46 on Ubuntu 9.04 in the "Ubuntu Ultimate flavour". Now from Inkscape I tried the upgrade method:

sudo apt-get update

then 

sudo apt-get install inkscape

ONLY!!! The upgrade/installation does not complete cause it reports back that I already have the newest version installed? Any ideas?

Oh by the way, is 10.04 stable? I read that 9.10 wasn't as stable cause of new programs and software and stuff that I have no clue about (I just want linux to be my stable OS in the back ground that doesn't require to much tinkering from me). And having asked that, can I upgrade to 10.04 via an installation disk? I usually get my OS disks from...well, wont say there name otherwise I might be accused of advertising. (downloading installations is expansive with a 3G card until I get ADSL).

But primarily, how do I upgrade my inkscape?

---

### Post by WinterRain on 2010-04-26
Go to system>administration>software sources>other software>+add button and copy **ppa:inkscape.testers/ppa** into it. Close window.

Then
```
sudo apt-get update && sudo apt-get upgrade inkscape
```

---

### Post by Inprogress on 2010-04-27
Hey there WinterRain.

Thanks for the reply. Two things, me in my ignorance, I see the word "testers" in that line, does that mean I will be upgrading to unstable version? I just want to upgrade to 0.47 which is the stable version.

From your guide, I go to the "Third-Party Software" tab. There I see the "+add" button. So I add the line you typed "ppa:inkscape.testers/ppa" but that is it, the "Add Source" button stays greyed out.

Then when I close that window just for the fun and try the sudo line, I get a message stating this:


321 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
Need to get 565MB/703MB of archives.
After this operation, 963MB disk space will be freed.
Do you want to continue [Y/n]?

This isn't exactly what I expected? What is missing or what am I doing wrong? Should I just upgrade to Ubuntu 9.10 and take it form there? Seems like its simpler.

P.S. Thats the one thing I like about Windows, if I want to install a new version of software, it a lot easier that Linux - from where I am sitting at least. If I knew more about Linux it will probably be just as easy hey?

---

