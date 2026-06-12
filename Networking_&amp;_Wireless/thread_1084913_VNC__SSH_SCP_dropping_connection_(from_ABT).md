---
title: "VNC / SSH /SCP dropping connection (from ABT)"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by H.Callahan on 2009-03-02
I originally [posted this in ABT,](http://ubuntuforums.org/showthread.php?t=1067042) but suggestions and ideas have petered out.  I really am desperate to get this working as the alternative is to chuck Ubuntu and go to WinXP.  I have pretty much eliminated hardware as a cause and have tried all the suggestions that were posted in the previous thread with no improvement.  I am currently in the process of reinstalling everything again (this would be the fourth time) hoping that something will change.  I'm hoping someone here will actually know what the error messages are saying and might have a suggestion to help me out.

Thanks!

> Ok, I am pulling out my hair again!

I scrounged a new set of hardware to make another machine and decided to go 100% Ubuntu on it. It is basically a Dell 1.8 Ghz P4 with 1Gb RAM (soon to be upgrade to 1.5GB) and an NVidia 7800 GS AGP video card (probably a bit of overkill for the CPU, but it is what I had). I pulled teeth trying to get the video to display anything over 800x600 resolution. Finally got it to 1280x1024, but still can't get Compiz to work, but that is a "later" issue.

What is driving me nuts now, is that I have setup the box for remote administration using VNC. I have gotten to work with out a whole lot of trouble. I have also set up SSH and a tunnel so that I can VNC through the Internet somewhat securely and also SSH into the box for a command line if I want it.

It all works except for the fact that after about 30 seconds to several minutes, I lose the connection. This happens whether I am VNCing in through the internet via SSH, VNCing through the Internet without SSH (for testing purposes, I don't intend actually use it that way), VNCing in from another machine on the same LAN (either with or without SSH) inside the firewall/router and when I am using just a vanilla SSH connection or trying to SCP files. From the new machine itself, it does not appear to be generically loosing the network as I have been able to browse on it and download both through the browser and via bittorrent without interruptions that I can see.

The messages that I have seen when directly VNCing in (without tunneling through SSH) have been "ReadExact: Socket error while reading" and "Error while waiting for server message". When SSH has been thrown into the mix (either using SSH directly, trying to SCP something or tunneling with VNC), the message has been "Network error: Software caused connection abort". If I wait a few moments, it will recover and I can reestablish the connection and log in again -- only to be dropped again shortly thereafter.

I have searched on those phrases and found a lot of mention them, but no answers or discussion of what is actually happening with those messages. Does anyone have any ideas on where to go to next?

---

