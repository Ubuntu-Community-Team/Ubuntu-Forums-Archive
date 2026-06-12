---
title: "Woes with Nvidia settings on two machines"
date: 2010-05-12
forum: Multimedia Software
---

### Post by Taffu on 2010-05-12
I've been using Ubuntu on a secondary machine for a while now, however I'm now converting my main machine to Ubuntu and was hoping to get a little help with video card & display setup. Both machines are updated to the latest Ubuntu version. For reference, I primarily play Final Fantasy XI on both of these machines.
 
My secondary machine is running an 8500 GT, and I've used EnvyNG to install the graphics drivers. I'm running at 1280x1024. Resolution is fine, I haven't had any problems other than graphical glitches & artifacts in the game environment. Everything loads fine, but lighting & shadows throw all kinds of glitches. I've tried tweaking what little I can in the X-server settings, but there really isn't much information I've been able to find on troubleshooting this problem. So for all intents and purposes, everything is working except actual aesthetic issues in-game, and I've found no way to tweak settings or confirm hardware acceleration in Ubuntu.
 
My main machine is a dual monitor. Primary monitor is a 22" running 1680x1050. After an initial install last night, the resolution is fine. However, along with being concerned about running into the same issue as my secondary machine (graphical glitches), I'm wondering if Ubuntu has the ability to extend the desktop the way the Windows display environment does. This machine is running a 9500 GT. I have not installed graphics drivers yet, other than the initial Restricted Driver update the Ubuntu performs.
 
From what I've found, I understand I need to run "sudo /etc/X11/xorg.conf" in terminal and modify settings there. I glanced over a brief "How To" and listing of different settings that can be added to that file, however the description of each section & setting was fairly brief and didn't really answer any of my questions...I felt it would be better to ask then start mucking around with settings I don't understand yet. 
 
Any & all help would be greatly appreciated. My current xorg.conf is pretty bare, only showing basic monitor information and a few (two, I believe) module settings.
 
Edit: To further clarify, FFXI is running in Wine, and I don't know if this affects graphics performance.

---

