---
title: "videos play slow across network"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by roger_doger on 2006-10-23
When playing videos from a network shared drive, mplayer will buffer the video, play about 10 seconds, then buffer, and so on.
It is slightly better watching avi file as opposed to mpeg files.

This worked fine when my laptop was running windows xp.

I can copy the file to my desktop, and watch it from there, and it works fine.

Suggestions?

---

### Post by dannyboy79 on 2006-10-24
this is not the ideal way to play video or music over a network if you are just using a normal media player. you need to use vlc or similar. I use a modified xbox with Xbox Media Center on it which sees my network shares over smb and somehow plays them fine without any buffering or slowdown. Some how Xbox Media Center uses mplayer to show the movies but I believe that there is another program that runs also which buffers it all previous to showing it. I wish I could tell you better how Xbox Media Center works. here is a link to vlc, [www.videolan.org/vlc/](www.videolan.org/vlc/), by the way, vlx stands for video lan center.

---

### Post by roger_doger on 2006-10-26
I've got vlc, and it works fine when playing files from a local drive, but, when I open up a network shared folder, and open up the file with vlc, it runs vlc, then stops. It doesn't even load the file into vlc.

Also, If try to open a file from within vlc, I can't see the network drive.

---

### Post by dannyboy79 on 2006-10-26
sounds like you have a bottleneck in your network somewhere. are there any firewalls blocking vlc from being able to run a file from a certain computer? you should get some network benchmark tools and try to establish what is holding up your file from playing smoothly. I unfortunately can't tell you what the names would be because I haven't had a need to do any benchmarking of my network but if you do find some for linux or for winbloz and they are free, I would appreciate it if you could post back what they are. they I can post my results for you to give you an idea where you need to be since I have no problem playing files over my network. did you look into any streaming software? how long does a 675mb file take to transfer over your network? are all your ethernet cards gigabit? do you have a router in the mix, if so, I am sure that what your bottleneck since consumer routers are very rarely gigabit. I have an old netgear wgr624 I think, and I don't have any issues playing files over the network, although, I use xbox media center ,which uses smb protocol and I believe mplayer to play the file. oh, are you using wireless? if so, then that's definitly why, I don't even think super G can stream movies fast enough, maybe music, test that out, can you play music over the network? what about trying a different protocol, I am guessing that you are using smb to play a file, well, maybe there is a player that can play files from an ftp server, or an nfs server, what about that? I wish I could give ya a definitive solution. to be totally honest, if I were you I would just buy a used xbox for $100, hack it so you can install linux on it or xbox media center, they use that as your media center in your family room. It's totally awesome. I put a 80gb hdd drive in it but am thinking about putting a 200, 300, or even 500 in it but I am not sure about compatibility. it could just be an extra ftp server that I could use for backup or whatever. currently I just store all copies on the games I own so I don't have to worry about the disc's getting scratched or ruined.

---

### Post by roger_doger on 2006-10-26
Thanks for the reply. I am using 802.11g, and it does seem slow when transferring files from my desktop (xp) to my laptop (ubuntu). However, it worked fine when it was running xp before.

I can access the files with mplayer, but there is buffering which slows things down. No firewall issues.

I'll look into the network throughput test to see where it stands.

---

