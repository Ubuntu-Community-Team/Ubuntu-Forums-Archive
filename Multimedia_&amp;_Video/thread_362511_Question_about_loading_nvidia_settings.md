---
title: "Question about loading nvidia settings"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by lambesk on 2007-02-15
I'm a bit new to Kubuntu, but I had a quick question about the Nvidia drivers that hopefully somebody can answer for me.  I've got the drivers installed and functioning perfectly except for one really small problem.  It won't load my AA, AF and other preferences upon rebooting the computer.  Obviously I'm running KDE.  I tried making an autorun script, but all that will do is bring up the control panel and not actually load the settings I need it to load.  From the command line, this is the command I'm wanting to run...

nvidia-settings -a FSAA=2 -a LogAniso=3 -a TextureSharpen=1 -a [gpu:0]/DigitalVibrance[CRT-1]=25

That's really the only unique things I want to load up, but the .nvidia-settings-rc doesn't seem to be worth much of anything as it never gets loaded either.  Is there any way to make a script that will run that command for me?  Sorry, I don't much at all about scripting on linux as of yet.  Thanks for any help you can give me.  
:)

EDIT -> Oh, quick edit.  I also tried running nvidia-settings as sudo, but that didn't seem to help either with autoloading my settings...

2nd EDIT -> Seems I answered my own question again.  In case anybody wants to know the answer, here's the script I wrote using kwrite or any other plain text editor.

#!/bin/bash
clear
nvidia-settings -a FSAA=2 -a LogAniso=3 -a TextureSharpen=1 -a [gpu:0]/DigitalVibrance[CRT-1]=25

I saved it as .morning mainly because I first figured out how to get my script to say good morning...  Anyway, for KDE users, place this script file in /home/username/.kde/Autostart and it'll run your script upon logging in to KDE.  Putting the .nvidia-settings-rc file doesn't work either, but whatever special commands you want are there.  For me, all I modified was AA, AF, DV, and TS, so that's all I made my script run.  Maybe this post will help somebody.  Maybe.  :p

---

