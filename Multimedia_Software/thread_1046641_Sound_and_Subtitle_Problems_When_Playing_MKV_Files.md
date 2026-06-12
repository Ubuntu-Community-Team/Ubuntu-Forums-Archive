---
title: "Sound and Subtitle Problems When Playing MKV Files"
date: 2009-01-21
forum: Multimedia Software
---

### Post by flylehe on 2009-01-21
Hi,
I am using SMplayer and KMplayer (in which I choose Mplayer) to play MKV video files. My problems are:
In both cases, the sound is messed up when fast/back forwarding. 
It seems MKV-embeded subtitle cannot be shown in KMplayer and a nonEnglish subtitle cannot be shown properly in SMplayer. 
Thanks for help!

---

### Post by rvm4000 on 2009-01-21
If you're using mplayer 1.0rc2 try to update it. You can find a recent version here: [https://launchpad.net/~rvm/+archive](https://launchpad.net/~rvm/+archive)

Otherwise try to change the demuxer. In smplayer you can do it in Options->View info & properties->Demuxer. Change it from "mkv" to "lavf" or vice versa.

---

### Post by flylehe on 2009-01-21
Thanks! I read the page you linked but could you tell me how to upgrade?

---

### Post by rvm4000 on 2009-01-22
You can download from there individual packages (click on the mplayer links) but maybe the easiest would be to add this line to your /etc/apt/sources.list:

```
deb http://ppa.launchpad.net/rvm/ubuntu intrepid main
```

Or if you use hardy, this one:
```
deb http://ppa.launchpad.net/rvm/ubuntu hardy main
```

Then run these commands from a terminal:
sudo apt-get update
sudo apt-get install mplayer

---

### Post by flylehe on 2009-01-22
Thanks anyway. The problems still remain.

---

