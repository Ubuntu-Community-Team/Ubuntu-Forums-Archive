---
title: "Connecting UPnP to a Samsung TV"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by Thoddy on 2011-03-20
Hi all,

I'm trying to connect my new Samsung TV (with AllShare - DLNA compliant) to my ubuntu 10.10... but do not succeed!

I've tried quite some things now:
[LIST]
[*]**xbmc** Nice UI! But no matter what I do, I can see the shares on my TV but cannot connect?
[*]**MediaTomb** Installation: fine, configuration: fine until some moment (German Umlauts??) - from that moment on I get the following error in my browser window:
> Error: SQLITE3: (1) near "RANSACTION": syntax error
Query:INSERT RANSACTION;
error: near "RANSACTION": syntax error

[*]**uShare** Easy to install, easy to configure command line tool - all I need! I got the furthest with this one: I could see every single file (pictures, audio and video files) on my TV, but could not open a single one, no matter what mime-type: "unsupported file type"!?
[/LIST]

Has anyone else ever had such problems?

And way more interesting: does anyone have a solution for this?? :D

Thanks in advance!!

---

### Post by Thoddy on 2011-03-21
For whatever reason today MediaTomb works fine!? :P

I had strange characters -or: question marks! :) So what I needed to do is change to UTF-8 according to: [http://www.synology-forum.de/showthread.html?3476-Mediatomb-Problem-mit-deutschen-Umlauten](http://www.synology-forum.de/showthread.html?3476-Mediatomb-Problem-mit-deutschen-Umlauten) - but hey: works!! :)

Does anyone know if I can change to root of the share so it does not show the full path and thus I don't have to navigate from /mnt (on my machine) all the time... ?

---

### Post by lordyosch on 2011-11-13
I just got my Samsung smart TV on Friday. I spent a couple of hours last night and a couple more this morning getting AllShare to play with Ubuntu.

-perfect success!

Mediatomb- could be seen by the TV but declared nothing but some Jpegs could play.

Googled lots, came across Serviio. Problem solved!

An issue I did run into though was the serviio server script aborted without telling me. I found and followed instructions to install the latest version of FFMPEG (which I thought I had already). Sorted that, now it runs like a charm.


I'm running Ubuntu Natty 64bit and the TV is a Samsung 6-series LED

(currently streaming Shrek and hardly affecting this PC's resources.


Jay

---

### Post by Fraoch on 2012-01-03
I already had Serviio installed which worked fine on my Samsung "C" series TV as well as a WD TV Live.  I just got an Xbox 360 and googled how to get it to read media on my Ubuntu box, settling on uShare.

I was disappointed.  The Xbox 360 supports such a limited range of media formats that although uShare worked fine, there was really not much to see or play.

Then I remembered I had Serviio installed and lo and behold, it has an Xbox 360 profile.  More importantly, Serviio transcodes, converting file formats on-the-fly without requiring a duplicate media library.  So you can play a whole range of formats the client machine may not support, all transparent to you because the Serviio profile has already been set up and knows which media format is required.

So another recommendation for Serviio and although I've recommended it twice on these forums today ;) I'm not affiliated in any way.  Just happy that this one server program will support just about anything.

---

