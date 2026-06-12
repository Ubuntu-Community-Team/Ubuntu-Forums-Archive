---
title: "Custom (HD) dual monitor resolution in Hardy"
date: 2008-04-27
forum: Multimedia Software
---

### Post by analystscouch on 2008-04-27
Hi there, I'm hoping someone can help me:

I'm trying to output in HD from my laptop to my HDTV using the VGA out.

My laptop uses the Intel 945GM chipset and has a VGA output. My HDTV (Phillips 23") has  DVI-I input. I have a cable which goes from VGA to DVI.

When I connect up my laptop and goto the Screen Resolution applet the TV is detected and I am able to Clone the screen. However, the maximum resolution is 1280x768, even though my TV supports 1080i.

I'm trying to figure out how to force 720p or 1080i. I'm using Hardy and it appears that xorg.conf is no longer used to store the resolution. I think it is now stored in home/.gnome2/monitors.xml. Trouble is that when I edit the part of this file which corresponds to my TV and save it, I get nothing but a blank screen (on the TV). When I go back into the screen resolution applet I just get the same options, max 1280x768.

Any ideas?

Thanks,
Nick

---

### Post by ubuntu-freak on 2008-04-27
Xorg/Xserver has changed quite a bit. Try the command "gksudo displayconfig-gtk" and see if that helps. 
 
Nathan

---

### Post by analystscouch on 2008-04-27
Thanks for responding.

No luck with that I'm afraid. The TV doesn't appear by default in the applet that command opens (it does in Screen Resolution applet and in monitors.xml). Adding a monitor in the applet the command opens doesn't seem to do anything. I think its editing xorg.conf rather than monitors.xml which seems to be the config file now. Seemed to mess up my xorg.conf using the command though so in the end I had to delete it and regenerate.

---

### Post by analystscouch on 2008-04-28
Acually looks like just deleting and regenerating xorg.conf (to fix probs caused by gksudo displayconfig-gtk) didn't do the trick. I have text appearing when I logout, very slow login and 2 mode changes of my monitor between usplash and gdm at startup which I didn't have before. I'm also getting occassional freezes, though these seem to only last  few seconds.

Anybody got any suggestions?

---

### Post by ubuntu-freak on 2008-04-28
> **analystscouch said:**
> Acually looks like just deleting and regenerating xorg.conf (to fix probs caused by gksudo displayconfig-gtk) didn't do the trick. I have text appearing when I logout, very slow login and 2 mode changes of my monitor between usplash and gdm at startup which I didn't have before. I'm also getting occassional freezes, though these seem to only last  few seconds.

Anybody got any suggestions?

Not sure what to tell you. I'm having problems with upsplash too actually. If you were using an NVIDIA graphics device, I'd tell you to use "nvidia-settings", not sure what you can do with Intel though. Did it work well in Gutsy? If you had a copy of the xorg-conf used in Gutsy, that might cure the problem, some people never trust an auto-setup and always fill out there own xorg.conf.

Nathan

---

### Post by analystscouch on 2008-04-28
Thanks for replying Nathan. Thing is, that in Hardy xorg.conf appears to be a stub. All the config info seems to have moved to monitors.xml. Trouble is that monitors.xml seems to be set up correctly, so i'm wondering if there isn't another file containing config data involved that I don't know about. Anyone around who knows about the changes to Hardy with xorg.conf?

About your usplash problems, are the related to [this thread.]("http://ubuntuforums.org/showthread.php?t=746132&highlight=usplash+not+working&page=2")

---

### Post by ubuntu-freak on 2008-04-28
> **analystscouch said:**
> Thanks for replying Nathan. Thing is, that in Hardy xorg.conf appears to be a stub. All the config info seems to have moved to monitors.xml. Trouble is that monitors.xml seems to be set up correctly, so i'm wondering if there isn't another file containing config data involved that I don't know about. Anyone around who knows about the changes to Hardy with xorg.conf?

About your usplash problems, are the related to [this thread.]("http://ubuntuforums.org/showthread.php?t=746132&highlight=usplash+not+working&page=2")

 
Thanks for the link, I'll try it out. Tis strange though, worked fine in Gutsy and I didn't use Hardy beta at all.
 
Nathan

---

### Post by analystscouch on 2008-05-07
I still can't figure out how to get xrandr to output at a custom resolution to my secondary monitor (HDTV). Can anyone help? My intel drivers seem to only work with xrandr, so making changes to xorg.conf just crashes x.

PS Also I still have the problem of text appearing between gnome logout and gdmgreeter and lots of mode changes between usplash and gdmgreeter on startup, both since the last time i edited xorg.conf. Can anyone suggest how to troubleshoot that?

---

### Post by ubuntu-freak on 2008-05-07
> **analystscouch said:**
> I still can't figure out how to get xrandr to output at a custom resolution to my secondary monitor (HDTV). Can anyone help? My intel drivers seem to only work with xrandr, so making changes to xorg.conf just crashes x.

PS Also I still have the problem of text appearing between gnome logout and gdmgreeter and lots of mode changes between usplash and gdmgreeter on startup, both since the last time i edited xorg.conf. Can anyone suggest how to troubleshoot that?

 
Install Start-Up Manager and tinker with it:
 
**sudo apt-get install startupmanager**
 
Always seems to quieten my boot and shutdown.
 
Still can't help with your other issue. Have you searched Synaptic for any package which may give you advanced options?
 
Nathan

---

