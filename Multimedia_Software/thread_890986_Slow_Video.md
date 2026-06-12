---
title: "Slow Video"
date: 2008-08-15
forum: Multimedia Software
---

### Post by jclarkneedshelp on 2008-08-15
Hey there guys, I'm a little confused about something here on Ubuntu Studio 8.04. One of the things I'm liking about Linux as opposed to Windows so far is that it has been very, very fast at just about everything. One thing however that hasn't lived up to this observation is video playback, this is particularly strange to me since it is a distro that's meant to be made for that sort of thing. 

I could accept the possibility that hardware is at fault, but I've not had such issues with my hardware in Windows. I'm running an SLI Nvidea Geforce 7800 configuration though I've not configured any specific drivers since my Linux install. Is there something I should be doing, I didn't install any drivers since there was any playback at all, which suggested to me that there must have been some installed during the setup of Ubuntu to begin with.

Also, I downloaded Cinelerra and tried to test it out by editing some .avi files and they displayed similarly slow playback and also had no sound despite the sound being present in mplayer. I can increase playback speed to a bearable level in mplayer if I reduce the resolution size of the player but I've watched these same files in full screen before in Vista. Any clues?

---

### Post by TenPlus1 on 2008-08-15
Try installing "mplayer" and/or "vlc" and testing your video on those players...  They are always very fast, especially on h.264 HD videos...

---

### Post by mateuszbaranski on 2008-09-11
Three things about slow video playback in cinelerra:
1) proprietary driver for nvidia ( "nvidia" driver - not "nv" in /etc/X11/xorg.conf) is a must if you want to work with Cinelerra. With standard nv driver even the desktop works not so fast (of course depends on resolution).

2) Cinelerra needs much memory - on 512MB PentiumIV I rarely had real time playback (25 fps). Now I have 2GB - I encounter no problems.

3) in Project -> Format  try to change to YUVA-8bit or YUV-8bit (without transparency) . The dafult is RGBA-float which is extremally slow - this setting gives you the best quality by rendering but it is not needed usually during editing. So during editing I use YUVA-8bit, and then by final rendering RGBA-float.
 
hope this helps

---

