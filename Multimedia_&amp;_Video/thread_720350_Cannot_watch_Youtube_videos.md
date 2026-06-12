---
title: "Cannot watch Youtube videos"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by ekmon1582 on 2008-03-10
When I want to watch a Youtube video it comes up and says I don't have the plugin's, yet when I try to install them it says it cannot find them. I'm currently running Ubuntu 7.10 off a LiveCD (soon a flash drive).

---

### Post by luisromangz on 2008-03-10
You have to install the flash plugin, and the best way isn't the Firefox assistant, which in linux is essentially broken (one apps updating and installing software themselves doesn't seem to be the linux way to software management). You should activate the universe/multiverse repositories and search and install the adobe flash plugin.

---

### Post by GGROD on 2008-03-10
I was able to get the Adobe Non-free flash plug-in installed.  The only issue I have is the frame rate.  It looks like the video is playing at 4 fps even with flash web sites.  Is there a way to fix this?

---

### Post by SRGT. DeGreene on 2008-03-10
> **GGROD said:**
> I was able to get the Adobe Non-free flash plug-in installed.  The only issue I have is the frame rate.  It looks like the video is playing at 4 fps even with flash web sites.  Is there a way to fix this?

I had the same problem, i fixed it by turning off my desktop effects so that it runs faster. ;p

---

### Post by theaceoffire on 2008-03-10
^_^ I have a dirty hack!

Step 1, go to Applications, then Add/Remove, and install VLC media player.
(Or type in terminal "sudo apt-get install vlc")

Step 2, install Greasemonkey:
[https://addons.mozilla.org/en-US/firefox/addon/748](https://addons.mozilla.org/en-US/firefox/addon/748)

Step 3, install this greasemonkey script I made:
[http://userscripts.org/scripts/show/23751](http://userscripts.org/scripts/show/23751)

^_^ Now youtube pages will be replaced with a direct link to the flv video, which you can either save or open with VLC to watch!

Using the non-free plugin, youtube videos take up to 85-96% of my cpu, but using VLC I can play 3-5 of them at once with only 50% cpu usage.

Its not a long term fix, but at least you can watch veoh, megavideo, and youtube without lag!

---

### Post by GGROD on 2008-03-10
Re (SRGT. DeGreene) I do not have desktop effects turned on.

Re (theaceoffire) So this should fix the issue of flash video but not viewing Flash based web sites.  Correct?

---

### Post by theaceoffire on 2008-03-10
Correct, although if you can find a stand alone swf player, you might be able to play them off line as well.

---

### Post by Ashrael on 2008-03-13
i have the same problems here... it wasn't always so... my 700 mhz 384MB laptop used to play flash effortlessly, but not anymore.... maybe the upgrade to gutsy or one of the flashupdates has gone wrong? Even my 2.4 ghz p4 1Gb ram runs at 100% when playing flash....I was thingking to downgrade and see what's up.. got a spare hd for my laptop...;)

so i'll keep you posted...

---

### Post by GGROD on 2008-03-26
Ok...so far the issues I have with the workaround:

1. Does not fix viewing flash based web sites.

2. If you visit a new site that has flash video then you need to edit the Greasmonkey script to include that site as well.

Thanks.

---

### Post by mtopro on 2008-04-29
Do any of you possibly have the swfdec installed?  That bugger was the source of my processor troubles.  Simple flash animations or games and I was running 80% usage of my processor. The only flash player I have installed now is flashplugin-nonfree.

It works great for me.. Youtube, complex animations, etc are now easy on the processor.  The only place I cannot view flash animations is at citicards DOT com. But that appears to be the only site giving me trouble. If you are using Firefox, go to Tools - Add Ons - Plugins and right click on the Shockwave Flash plugin to temporarily disable. 

Much better!:)

---

### Post by bilal.17 on 2008-04-29
> **mtopro said:**
> Do any of you possibly have the swfdec installed?  That bugger was the source of my processor troubles.  Simple flash animations or games and I was running 80% usage of my processor. The only flash player I have installed now is flashplugin-nonfree.

It works great for me.. Youtube, complex animations, etc are now easy on the processor.  The only place I cannot view flash animations is at citicards DOT com. But that appears to be the only site giving me trouble. If you are using Firefox, go to Tools - Add Ons - Plugins and right click on the Shockwave Flash plugin to temporarily disable. 

Much better!:)

i also recommend flashplugin -nonfree it works better than gnash for now but in the future it might be a good idea to try gnash. But now its probably better not to mess with it.

---

### Post by ruetheday on 2008-04-29
How do you get rid of swfdec  because i have tried and it won't go away!!!

---

### Post by ruetheday on 2008-04-29
i just want the add on's in firefox to be default i don't know where to uninstall the one i...installed

---

### Post by mtopro on 2008-06-10
> **ruetheday said:**
> i just want the add on's in firefox to be default i don't know where to uninstall the one i...installed

To figure out which plugin you are currently using.
In FireFox go to Edit/Preferences.  Click on the Icon far left that is called 'Main' then click button 'Manage Add-ons...'
Under the 'Plugins' icon you should be able to see a list of all the plugins you currently have being used by Firefox.

Want to know how to uninstall your current flash plugin?  If Add/Remove (under Applications) will not let you uninstall this program, it will probably give you the error message telling you that it has dependencies and you need to remove the packages using Synaptic Package Manager.

In that case go to System/Administration/Synaptic Package Manager.  You should be able to scroll to the plugin that you are trying to remove. Right-click on it and select 'Mark for Complete Removal'.  Then uninstall.

Again, I have been trying all the flash plugins and the best by far appears to be the flashplugin non-free.

Sorry the reply is so late, but I hope that helps.

---

