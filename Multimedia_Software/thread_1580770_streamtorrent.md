---
title: "streamtorrent"
date: 2010-09-23
forum: Multimedia Software
---

### Post by moheganer2 on 2010-09-23
has anyone figured out how to get streamtorrent working on ubuntu?there was a thread on this subject that went dead before being solved.

---

### Post by Kir_B on 2011-05-21
Anyone figure this out yet?

Kirby

---

### Post by dany666 on 2012-08-12
> **Kir_B said:**
> Anyone figure this out yet?

Kirby

StreamTorrent on Ubuntu Linux (worked on 12.04)

This is what worked for me P-E-R-F-E-C-T-L-Y

1. Install wine

Open a Terminal:

sudo apt-get install wine

2. Install Windows Media Player 7.0 with Wine...Right-click on the installer>Open with Wine Windows Program Loader (haven`t tried any other version and I don`t care, this worked for me and that`s that)

[http://www.oldversion.com/download-Windows-Media-Player-7.0.html](http://www.oldversion.com/download-Windows-Media-Player-7.0.html)

Again with StreamTorrent to
[http://www.softpedia.com/get/Internet/File-Sharing/Stream-Torrent.shtml](http://www.softpedia.com/get/Internet/File-Sharing/Stream-Torrent.shtml)

3. Install VLC

[http://www.videolan.org/](http://www.videolan.org/)

4. Open StreamTorrent (I don`t know maby from the icon on the desktop)


Hit "File> Add".....Paste the stream link ... example:  "st://A0MCgpwEdTsDOwW..........." and then hit OK


4. Open VLC (again I don`t know if it works with other, It worked with this one so it`s enough for me)


5. PLAYING the stream

After hitting Play on the stream you like in the StreamTorrent list, wait I don`t know untill 80 %, then do these steps in VLC:

-Click on "Open Network Stream..."
-Paste "http://127.0.0.1:15900/1.asf" in there and hit Play



ENJOY !!! :popcorn:

the cool thing is that you can change the Video>Aspect Ratio in VLC...wohoo

---

### Post by overdrank on 2012-08-13
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

