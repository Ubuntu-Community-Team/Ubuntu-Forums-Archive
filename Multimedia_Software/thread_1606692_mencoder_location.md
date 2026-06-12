---
title: "mencoder location"
date: 2010-10-26
forum: Multimedia Software
---

### Post by Derekgnr on 2010-10-26
Hi, I installed mencoder but I don't know where to find it. Where is it located?

---

### Post by tommcd on 2010-10-27
Mencoder is a command line application. There is no GUI for it. Depending on what you want to do though, there are a number of graphical apps that use mencoder to do the video encoding. For example, if you want to make a DVD disc of your video file(s), you can install **devede** from the Ubuntu repos:
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html) 
Here is a tutorial for using mencoder from the terminal:
[http://www.linux.com/archive/articles/121385](http://www.linux.com/archive/articles/121385)
Perhaps if you tell us exactly what you want to do, we could direct you to the best app or a good tutorial for it.

---

### Post by andrew.46 on 2010-10-27
Hi Derek,

> **Derekgnr said:**
> Hi, I installed mencoder but I don't know where to find it. Where is it located?

On my system:

```

$ **[COLOR="Red"]sudo find /usr -iname mencoder[/COLOR]**
/usr/bin/mencoder

```

Andrew

---

### Post by Derekgnr on 2010-10-27
Ok I found it in /usr/bin/mencoder. But now how do I open it to use it? I tried to open it but it wouldn't open. I know I'm supposed to open up a command but how do I do that? I tried the terminal and it didn't work with that.

---

### Post by andrew.46 on 2010-10-27
Hi Derek,

As Tom mentioned it runs from the commandline, perhaps test it with a simple command:

```

andrew@skamandros~$ **[COLOR="Red"]mencoder -ovc help[/COLOR]**
MEncoder SVN-r32533-4.3.3 (C) 2000-2010 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding
   x264     - H.264 encoding


```

This merely demonstrates the available output video codecs but it should demonstrate also if your copy of MEncoder is working or not :).

Andrew

---

### Post by SeijiSensei on 2010-10-27
Mencoder manual: [http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html](http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html)
Encoding guide:  [http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html](http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html)

Also there's a [wiki]("http://en.gentoo-wiki.com/wiki/Mencoder") at Gentoo Linux that's very helpful.

---

### Post by andrew.46 on 2010-10-27
Highly instructive as well is [this comment]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-October/081366.html") from an MPlayer developer:

> 
Just in case you don't know:
MEncoder is not an actively maintained program, you should usually use FFmpeg
for all encoding operations.


Andrew

---

### Post by Derekgnr on 2010-10-27
I'm trying to change .ogg to avi. Am I doing this right? Is it supposed to go in the terminal?


derekgnr@derekgnr-System-Product-Name:~$ mencoder out.ogg -o out.avi -oac mp3lame -ovc lavc
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
File not found: 'out.ogg'
Failed to open out.ogg.
Cannot open file/device.

---

### Post by andrew.46 on 2010-10-27
Hi Derek,

> **Derekgnr said:**
> I'm trying to change .ogg to avi. Am I doing this right? Is it supposed to go in the terminal?


```
derekgnr@derekgnr-System-Product-Name:~$ mencoder out.ogg -o out.avi -oac mp3lame -ovc lavc
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
File not found: 'out.ogg'
Failed to open out.ogg.
Cannot open file/device.
```

You need to give the correct path to your input file. Perhaps drag out.ogg to the Desktop and then navigate from the terminal as follows:

```
cd $HOME/Desktop
mencoder out.ogg -o out.avi -oac mp3lame -ovc lavc

```

This would be only a start I suspect as you would be best to embellish your commandline a little...

Andrew

---

### Post by Linuxforall on 2010-10-27
Or you can install programs like Acidrip, DeVeDe or K9 which use mencoder with GUI.

---

