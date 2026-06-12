---
title: "Ubuntu 13.04 multiple monitor issues (fullscreen, general settings)"
date: 2013-04-26
forum: Multimedia Software
---

### Post by bmass on 2013-04-26
I just installed Ubuntu 13.04 on my ASUS G74S Republic Of Gamers laptop w/ 12GB ram, intel i7 and GeForce GTX 560M

I installed proprietary graphics drivers via:
```
sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update 
sudo apt-get install nvidia-current nvidia-settings
```

I plugged in my TV through an HDMI cable

In System Settings > Displays I unchecked Mirror Displays

Using Ubuntu Software Centre I downloaded: vlc, ubuntu restricted extras, chromium, pulse audio volume controller



I'm trying to set things up so that I can watch things on my TV while working and playing around with Ubuntu on my laptop. I've been having all sorts of issues that seem to come and go, but the main one troubling me right now is staying fullscreen on my TV while working on the laptop. I noticed through googling that other people are having similar issues and that there are some interesting workarounds for getting flash (like YouTube videos) in fullscreen by running some codes, and I'll get to those when I want to get flash working, but I'm mainly just trying to watch videos in VLC.

So I drag VLC over to my TV and  double-click to go fullscreen. Everything is fine, I click back to my laptop and the bar at the top (I want to call it a taskbar because I just switched to Ubuntu from Windows) along with the application launcher re-appear. Now in my Displays setting I can set the application launcher to only appear on the laptop, but I still have no way of getting rid of the taskbar at the top. This isn't really feasible for watching videos, so I am wondering how I canfix this so that VLC stays completely fullscreen while I'm working in my laptop display.


EDIT: I updated the linux kernal via: [http://ubuntuforums.org/showthread.php?t=2136493](http://ubuntuforums.org/showthread.php?t=2136493) in the process of trying to fix HDMI sound. Updating the kernel fixed the HDMI audio and also fixed this multiple monitor issue

---

