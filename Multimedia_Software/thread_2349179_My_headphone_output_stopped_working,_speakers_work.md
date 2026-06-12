---
title: "My headphone output stopped working, speakers work fine"
date: 2017-01-11
forum: Multimedia Software
---

### Post by gunnar.grimsson2 on 2017-01-11
I'm using Ubuntu 16.04LTS on a new Dell XPS15 laptop. Everything worked fine for a couple of months after installing and then the headphone output stopped working. I managed to fix it after scouring the internet with making changes in Pavu, not sure anymore what they were but there was no visible audio signal before it being fixed but was visible when fixed. Before finding that solution I had made some other changes which did not work, I don't know what they were :|

This worked fine for a few weeks and then the headphone output stopped working again. I checked Pavu, fiddled with most settings but no sound. I have tried so many suggestions and solutions that worked for others from the internet but none of them worked. I would post links to them here but there are so many bookmarks in my browser on this issue that I really don't know which ones to post :| 

I've fiddled quite a bit with /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf and quite easily managed to disable my speakers! but no changes in headphones output at all. I tried to delete the complete contents of that file with no effect on headphones output. I've tried uninstalling and installing Pavu and rebooting in between (oh my how often I've rebooted my laptop in this quest) but nothing happens. 

The headphone output works fine when I boot into Ubuntu Live USB as do both my headphones which also work fine on my phone.  When I plug in my headphones Ubuntu pops up with the Unknown Audio Device dialog box [[http://imgur.com/juAaCtt](http://imgur.com/juAaCtt)] (and the volume level info box in top right) but whatever I click there, still silence. Pavu looks good [[http://imgur.com/MJe3pWw](http://imgur.com/MJe3pWw)], as far as I can see. Alsamixer as well [[http://imgur.com/Y9jNt1u](http://imgur.com/Y9jNt1u)]. 

No sound source works, none of my browsers (Chrome, Chromium, Firefox), Audacity, VLC, the default video player, probably others I'm forgetting. When I press the volume up and down buttons the visual indicator in the top right corner responds properly but no audio. When I plug and unplug the headphones the visual volume changes from speaker levels to headphone levels but of course (sorry) not headphone audio, only from speakers. 

My Alsa info is at [http://www.alsa-project.org/db/?f=c63a23a5751d896c8ef5f7d39619978011f39f7e](http://www.alsa-project.org/db/?f=c63a23a5751d896c8ef5f7d39619978011f39f7e)

Anybody out there that might have any pointers for me on this? 

I'm def willing to try most anything to fix this, I know my way around the shell as I've been using Linux on and off since '86. I'm actually getting close to doing a complete reinstall of Ubuntu in the hope that the problem is my fault and will not resurface a few weeks after reinstall. But of course I'd much rather fix the problem! 

Thanks for reading, sorry about verbosity but I did not want to omit potentitally useful information.

---

