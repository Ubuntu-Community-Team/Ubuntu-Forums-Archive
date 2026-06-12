---
title: "NIVIDIA MCP61 sound card suddenly not working"
date: 2008-04-23
forum: Multimedia Software
---

### Post by bear garden on 2008-04-23
Decided to install VirtualBox and a virtual machine (Windows XP) so I could use a specific program for coursework. Sound was working fine, until I rebooted shutdown my computer to leave for class. While I was gone, my girlfriend booted up the system and my graphics card was not detected. When I booted up when I got home, it worked fine, but my sound card was not being detected.

After a bit of searching and trying to figure out what was wrong, I followed the steps in this topic: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449), which led me to believe everything would work. Seeing the warning about GDM not working after purging/re-installing alsa and the like, I went ahead and
```
sudo apt-get install gdm ubuntu-desktop
```
and it installed. I then rebooted, assuming that my computer would boot, and perhaps my sound would work.

My computer didn't get past the usplash screen. I'm now booting from a live CD. My sound card is being recognized and it works, but I can't boot from my HDD. I don't know that if I manage to get my main Ubuntu partition booted up, that my card will even work.

Is this a problem with GDM? Or is it something far worse?

Here's my lshw -C sound from before:
> 
  *-multimedia UNCLAIMED  
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2

And here is the most recent check (from the Live CD):
> 
  *-multimedia            
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

---

