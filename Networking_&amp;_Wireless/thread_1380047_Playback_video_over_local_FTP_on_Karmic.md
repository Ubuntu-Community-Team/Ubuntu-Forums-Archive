---
title: "Playback video over local FTP on Karmic"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by Patrik89 on 2010-01-13
Hi!

I recently just installed Ubuntu on this laptop and I have a issue with playing back videos on my LAN server.

Thing is, I've got another computer too where it works flawlessly so I was wondering what causes this on my laptop...

I mount the FTP location and I get access to all the files on the server. On my other computer, I can basically just click any video file and it would act as it would if it was on my HDD already, but when I try to do that on my laptop it will not play the video file at all.

I've tried several media players too, but I usually just use VLC so here is the VLC error:

```
[COLOR=#ff0000]File reading failed:[/COLOR] [COLOR=#000000]VLC could not read the file.[/COLOR]
```And then ask if I want to repair it. However, once I drag the file over to my desktop it works. 



So why won't my media players read video files over FTP?


Thanks in advance,
Patrik.


Edit:
And the whole "Connect to server" is acting a little weird. If I try to use the DNS of the server instead of the local IP I will not get any response. However, using the DNS in other applictions do work.

---

### Post by Lars Noodén on 2010-01-13
> **Patrik89 said:**
> 
So why won't my media players read video files over FTP?


Please give a little more detail about how you are connecting.

You might also be interested in looking at streaming video using [vlc](http://www.videolan.org/vlc/streaming.html) or [icecast](http://www.icecast.org/)?

---

### Post by Patrik89 on 2010-01-13
I go to "Places->Connect to server" and log in via ftp with login.

Once mounted, the window pop up with my server and all its files like they were on my own laptop.

However, once I try to double click a video file and VLC open it then it won't playback the video file. :(


EDIT:

Solved. Instead of FTP I used SFTP. Worked wonderfully. =)

---

