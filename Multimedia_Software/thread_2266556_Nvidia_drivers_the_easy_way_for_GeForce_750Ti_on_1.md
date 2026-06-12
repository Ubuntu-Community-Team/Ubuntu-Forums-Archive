---
title: "Nvidia drivers the easy way for GeForce 750Ti on 14.04.2"
date: 2015-02-23
forum: Multimedia Software
---

### Post by Lance_Ryan on 2015-02-23
I been struggling trying to use PPA and manual methods from posts on the web. The results were not good. I tried using Synaptic Package manager and found if I select the correct 1st package and mark it for installation, Synaptic picked the correct other packages for me. After install and reboot after Synaptic finished, my 55" Samsung came up default in 1080p like it should. The video is now spectacular using VLC playing .iso dvd files from my hard drive. The icon for the Nvidia settings manager needs to be drug onto the desktop menu from installed software search app. I'm a home theater guy, so I can't say about game play, but I suspect similar results.

Here's what worked for me -

Open Synaptic and do a reload
Type nvidia into the quick filter and click search
Right click nvidia-331-updates and mark for installation
Accept the rather long list of other packages Synaptic says needs to be installed
Click mark all upgrades and then click apply
Be patient, there will be quite a bit of software generated and installed by Synaptic
Reboot after Synaptic says it's finished and you're done

I found turning on Deinterlace and selecting Blend in VLC gives the best results. Just hit the d key during playback to toggle between modes. Everything else in VLC is left default other than installing libdvdcss by modifying the sources.list file. Don't forget to select the VLC links in the sources list in software manager and then use Synaptic to install libdvdcss. I left the the default Nvidia control panel settings for my Samsung.

---

