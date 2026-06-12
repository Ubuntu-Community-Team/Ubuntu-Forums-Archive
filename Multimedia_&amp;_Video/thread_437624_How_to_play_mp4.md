---
title: "How to play mp4?"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by trishacupra on 2007-05-09
Hi, 

I've had Ubuntu installed for about a week, though it feels like forever. I haven't used Windows on my dual-boot system at all yet.

I thought I'd installed all the codecs, and I've been watching AVI videos heaps. And mp3 files also work.

Just now I tried watching an mp4 video, and Totem complained about it...

> **Totem could not play 'file:///home/trisha/Desktop/jh2.mp4'**
There is no plugin to handle this movie.

Can you plese tell me where/how to get this plugin?

---

### Post by trotur on 2007-05-09
If you have totem-gstreamer, try
```
sudo apt-get install gstreamer0.10-ffmpeg
```
Or if you have totem-xine, try
```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by krussell on 2007-05-09
Hello :-)
Everything plays in my PC (Ubuntu Edgy), no matter what the format is.
What i did:
1) Firstly, i replaced totem-gstreamer (so far cannot do a thing) with totem-xine. Now totem can play all files (except VCD, revert to Gxine).
2) Downloaded all the win32 codecs from here (slackware is always this simple!): [http://www.slacky.eu/repository/slackware-11.0/multimedia/all/20061022/all-20061022-noarch-1sal.tgz](http://www.slacky.eu/repository/slackware-11.0/multimedia/all/20061022/all-20061022-noarch-1sal.tgz)
3) Unzipped and copy the codecs into **/usr/lib/win32** (mkdir /usr/lib/win32 first)
4) Created a symlink of win32 to codecs (in **/usr/lib** do this command: *ln -s win32 codecs*) because sometimes xine/totem look for the codecs in /usr/lib/codecs
5) installed libxine-extracodecs ([http://packages.ubuntu.com/edgy/libs/libxine-extracodecs](http://packages.ubuntu.com/edgy/libs/libxine-extracodecs))

Now, Gxine/Xine/Totem is ready for any format to play.

---

### Post by gauravdott on 2008-04-11
Sorry to say but your link is outdated. Can you suggest some other link please :(

---

### Post by bambam82 on 2008-05-19
> **gauravdott said:**
> Sorry to say but your link is outdated. Can you suggest some other link please :(
[http://repository.slacky.eu/slackware-12.1/multimedia/all/20071007/all-20071007-noarch-1sal.tgz](http://repository.slacky.eu/slackware-12.1/multimedia/all/20071007/all-20071007-noarch-1sal.tgz)

---

### Post by justineve on 2008-05-19
> **bambam82 said:**
> [http://repository.slacky.eu/slackware-12.1/multimedia/all/20071007/all-20071007-noarch-1sal.tgz](http://repository.slacky.eu/slackware-12.1/multimedia/all/20071007/all-20071007-noarch-1sal.tgz)

Hi, bambam82.
Your suggested link is really good. It is useful to me. Thank's for sharing it with us.

---

