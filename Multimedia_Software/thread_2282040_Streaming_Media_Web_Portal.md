---
title: "Streaming Media Web Portal"
date: 2015-06-11
forum: Multimedia Software
---

### Post by Monster_user on 2015-06-11
This might be the wrong forum,... I'm considering using an Ubuntu box as a media server. What I would like is a solution that allows me to browse, and manage my videos fairly easily, and be able to stream them to Windows PCs by simply clicking a hyperlink? Also, I'm wanting something to downgrade the quality dynamically, so that it wouldn't stutter trying to play HD video through an encrypted openvpn connection over a shared hotel wifi network.

An example.

Say I have a video server at my house. I generally use it to stream videos to my PC. However, I may view these videos while on vacation, streaming through OpenVPN. These are probably going to be short videos like you would put on YouTube, not feature length films. Such as clips from family get-togethers, to share with other family members. If I lowered the resolution on their cell phones/cameras, then that would lower the quality of video which could be played at home, just for consideration of playing occasionally at a remote location. 

So those recording the videos, and those playing the videos are not necessarily tech savvy, and I do not want to spend my time writing code, or managing this particular project, so I want to keep it simple. I am not above spending money on a solution that would do the job.

I am also hoping to translate this into a project that would work for the office as well, if possible. Get some experience at home, and then promote a similar solution at work. Win some brownie points with management, without taking on a second job at work.

---

### Post by TheFu on 2015-06-11
Plex Media Server.

There is a very specific directory structure required. Fighting that will lead to failure. It is similar to what XBMC / Kodi require.

The whole hyperlink thing sorta sucks. You learn why when you have a few thousand media files.  Plex is the best DLNA server I've found.  Of course, DLNA doesn't have much security (zero), so if that is important to you keep looking.

---

