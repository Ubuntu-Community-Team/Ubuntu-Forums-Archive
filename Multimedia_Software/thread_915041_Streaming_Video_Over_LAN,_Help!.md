---
title: "Streaming Video Over LAN, Help!"
date: 2008-09-09
forum: Multimedia Software
---

### Post by noname4444 on 2008-09-09
I installed Ubuntu for the first time last night and things have been running great.

I have all the codec I need installed as well as VLC.   I can play videos on the computer with no problem.

I currently have folders shared over my LAN on my Windows machines.  If I try to play videos from those folders (by opening them over the network, thus the streaming), they won't start.

Does anyone know why this is and what I can do to fix it?  Is it an issue with Samba?  I can copy them from the drive to the computer to play them but I much rather stream them if possible.

Thanks for the help!

---

### Post by noname4444 on 2008-09-09
Sorry for the bump.  Anyone on now who has any idea why this doesn't work?

---

### Post by lovinglinux on 2008-09-09
> **noname4444 said:**
> I can copy them from the drive to the computer to play them but I much rather stream them if possible.

As far as I know this is not streaming, which indeed occurs when the remote machine processes the video, encode them and stream a few pieces per second to your machine. If you click "Open File" in VLC and browse the network folder to select the video and open it, it's not streaming. What you trying to do is simply open an video file from a remote machine directory. Try downloading the file to local machine and test if it works with VLC, because if not it is a video/codec issue and not related to the network.

---

### Post by noname4444 on 2008-09-09
Ahh.  It appears that my wireless card was gimped by Ubuntu by default (A WMP54G Linksys).  After a lot of searching I found a 1 step way to fix the problem.  Now that I can stream faster than 1Mbps video is playing better.

Though it seems I have to use Totem and not VLC, VLC doesn't open it remotely very well...  (but Totem doesn't recognize the subtitles file...)

Edit: Ah ha! MPlayer will load the file over the network with no delays *and* load the subtitles file.  We have a winner.

---

### Post by lovinglinux on 2008-09-09
Good. Please don't forget to mark the thread as solved :)

---

### Post by HunterThomson on 2008-12-16
I mount the /home partition on my laptop with sshfs. If I try to open the file directly in VLC it will not pay. 

FIX. You just open a graphical file manager to execute the video file with VLC. You can even drag and drop into VLC. 

SSHFS works vary well for this. And hay it's encrypted :) So playing your home movies ;) over WLAN is safe from the prying eyes of the hacker kid next door. 

But you do know you can stream video over your LAN with VLC. 
VLC "Video LAN Client"

---

