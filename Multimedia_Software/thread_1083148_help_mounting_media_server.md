---
title: "help mounting media server"
date: 2009-02-28
forum: Multimedia Software
---

### Post by pdcox on 2009-02-28
i have a old cpu that i would like to set up as a server
its 1.4 ghz, 512 mb, video capture.(i can use a monitor to set up but wont be able to stay with it, so i have to be able to acess remotely)

any ideas ?

---

### Post by pdcox on 2009-02-28
bump

---

### Post by pdcox on 2009-02-28
i thought would be a good brainstorm kid of thread

---

### Post by pdcox on 2009-02-28
i was thinking in turning on the remote acess, instaling mythtv, and sharing the hd over the network for storing files.
any more ideas to improve?

---

### Post by pdcox on 2009-02-28
Bump

---

### Post by rhcm123 on 2009-02-28
Ok, quick lesson in forum policy. No offence, but don't bump posts unless nobody has posted in the thread for 24 hours.

I reccomend the following, (it's what i use)

-Ubuntu 8.10 
-LAMP (P being php)
-Jinzora2
-Samba shares with a public directory and private directories 
-CUPS for printer sharing
-SSH (cause you said you needed remote access, comes standard in ubuntu)

---

### Post by pdcox on 2009-02-28
sorry rhcm123, i am kind of new in the forum, i didnt know about the 24 hours. in your server do u stream what u capture from the video card

---

### Post by rhcm123 on 2009-02-28
> **pdcox said:**
> sorry rhcm123, i am kind of new in the forum, i didnt know about the 24 hours. in your server do u stream what u capture from the video card

no, as it's all headless :), and doesn't even have a video card (i'm assuming your talking about somthing like VNC)

I've been reading this thread, found it very interesting (might be relevant to your interests)
[http://ubuntuforums.org/showthread.php?t=628835](http://ubuntuforums.org/showthread.php?t=628835)

---

### Post by pdcox on 2009-03-01
it would be more like capturing the tv with the computer ur using as the server and streaming the video and audio over the network so you could watch tv in your notebook without a tv capture device in the notebook

---

### Post by rhcm123 on 2009-03-02
> **pdcox said:**
> it would be more like capturing the tv with the computer ur using as the server and streaming the video and audio over the network so you could watch tv in your notebook without a tv capture device in the notebook

You'd need to get a TV card in the server, and i don't even know what programs you would have to use on it.... google it, for google is your friend.

---

### Post by punx45 on 2009-03-02
for your system specs, i would suggest the Hauppage tuners, like the PVR-150.   They hardware encode in MPEG2 on the card, which takes alot of strain off the system.   If you have mythtv installed, that can take care of alot of the media serving duties, as you can view content through a MythTV frontend on other computers, and it also acts as a UPnP server which can be useful to tons of other devices.

as for HDD sharing, i suggest NFS for a wholly *nix environment, and SAMBA if you need to cater to any Windows people.

keep in mind that full rez MPEG2 video takes up about 1GB per 30 minutes, so disk space should be a priority.  also, video encoding is a disk intensive process (constant write for long durations) so i think it would be best to have the OS on one disk, and video encodes on another, or even better, a RAID.

---

### Post by pdcox on 2009-03-02
good idea, how big moreless the hd should be ?

---

### Post by cariboo on 2009-03-02
You can use vlc to stream audio/video over the network. It can be done from the command line if you don't want to install X.

Jim

---

### Post by punx45 on 2009-03-03
> **pdcox said:**
> good idea, how big moreless the hd should be ?

as big as you can afford :-D

and yes, you can use VLC for a great many things, but in my opinion, its streaming is less elegant than something else like a Myth frontend, or a UPnP device.   why shell in and run a command when you can just browse a menu?   plus, with Myth Frontend im pretty sure the client does the decoding, which also helps keep strain off the server.   I believe the same would be said for a UPnP device as well.

---

### Post by rhcm123 on 2009-03-03
> **pdcox said:**
> good idea, how big moreless the hd should be ?

you can get a cheap RAID 0 for about 750$-ish

---

