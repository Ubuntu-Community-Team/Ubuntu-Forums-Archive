---
title: "Setting default audio out"
date: 2013-11-15
forum: Multimedia Software
---

### Post by Dustie on 2013-11-15
Hello!

I got an annoying problem with Ubuntu always picking the wrong audio output by default and I have to change it every time i use it to get audio. I have fixed it in some applications by changing it locally (like in VLC) but system-wide it is still wrong. This means that some applications (XBMC, Parole, etc.) doesn't work, as they have no option to change output as far as I can tell. 

Isn't there a simple way to do this systemwide? 

The problem is that it wants to use Pulseaudio and I cannot get it to work with passthrough/SPDIF to DTS. In VLC choosing SPDIF makes it work perfect, but this doesn't solve it for everything else on the system :(


Here's VLC working perfect:
[IMG]http://i.imgur.com/KGnZh5K.png[/IMG]


Here's Ubuntu default that I cannot find a way to change systemwide. VLC even looks like this with pulseaudio *purged*(!) ...
[IMG]http://i.imgur.com/JaR4pdR.png[/IMG]

---

### Post by Yellow Pasque on 2013-11-15
There's some instructions here: [http://ubuntuforums.org/showthread.php?t=1109812&p=11652332#post11652332](http://ubuntuforums.org/showthread.php?t=1109812&p=11652332#post11652332)

The only difference I would recommend is creating ~/.config/pulse/default.pa file instead of editing the system one (unless you have multiple users).

---

### Post by Dustie on 2013-11-15
EDIT: Nevermind, I'm trying again with Pulse. It is really strange though: DTS and Dolby is using SPDIF and stereo is using HDMI. So I end up with Sound in either my TV OR my reciver -depending on if source is surround or not.

---

### Post by Dustie on 2013-11-16
Using XBMC nightly fixed it. Ubuntu's use of Pulseaudio was the problem.

---

