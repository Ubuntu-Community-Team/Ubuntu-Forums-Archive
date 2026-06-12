---
title: "Remotely (http) controlled media server with playback ON server not remote client"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by jptechnical on 2007-04-24
Here is my goal, read it all the way through because it is not the usual scenario. I am sure there is an app out there specifically designed for this, but I am new to desktop linux.

System info: 
xubuntu 6.10 (just for speed and simplicity, and ubuntu desktop would be fine)
iMac G3 (but I am not married to it, I can use any machine, this imac is just fun to poke around with. I run a pc repair shop, so I have no shortage of older machines and parts.)

I want to make a media server I can put in my server rack in my office that will store and playback mp3s and the like. I have a stereo in the rack and speakers in the office, I will run headphone out from the server to the stereo line-in and I can remotely control volume for the stereo with the included remote. 

What I need is a way to build/modify/play playlists and files on the server through, preferably, a web interface. Basically something like slingbox for local playback on the server itself, not a streaming media server to the client connected to the web interface.

Ideally, how can I control a media player on a remote machine to change playlists without using ssh or vnc or some other screen forwarding tech?

I know there is something out there, any help would be appreciated. I have learned alot from this forum, it has been a great resource. Thanks!

---

### Post by will_in_wi on 2007-04-24
I think vlc can do what you want with a web interface.

---

### Post by jptechnical on 2007-04-24
Holy Cow, it does work, works damn good too. I even set my root path and it displays the directory structure! 500 points to you (if this were Experts-Exchange.com). I think this will do what I need to do. I just need to get smbfs and samba working properly now, and figure out how to make this an autostart function.

Thanks for the rapid reply!

---

### Post by jptechnical on 2007-04-25
I spoke too soon. I can get VLC HTTP running once, but after that I cannot get it running again and I didn't even touch the settings. I have reset all the defaults and even uninstalled/reinstalled with no success. I am searching their forums now. 

any other solutions?

Thanks.

---

