---
title: "Configure mozplugger for VLC"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by Hero of Time on 2007-05-05
I got after some problems feisty fawn running smoothly, wireless and all but now I want to watch video's. No problem, installed VLC so I can watch everything I want, but now I want to use VLC to embed in my browser. The plugin for VLC doesn't work for Opera, it just won't pick it up. I have installed mozplugger for it and Opera sees that one just fine. The only problem that's left is to set Mozplugger to use VLC. I don't have Totem or Mplayer installed, because I have vlc for all video stuff. My audio player is XMMS, but I also have BMP installed and gxine (which doesn't work, after the little 'check wizard' it just closes and everytime I open it, that wizard pops up).

Now how do I set mozplugger to use VLC? I'm pretty new to Linux so I don't know much (yet). I use Xubuntu btw.

---

### Post by kerry_s on 2007-05-05
In opera use mozplugger+gxine, in firefox use media player connectivty plugin+vlc.

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

sudo apt-get install gxine

---

### Post by Hero of Time on 2007-05-05
As I said, I only use Opera, there is no need for Firefox. Also, it doesn't matter what I do to gxine, it stays broken. It just won't open anything without the annoying wizard thingy and once I finish it, gxine closed immediatly with it. I noticed that on my previous install Mplayer closed down right after playback of a video (also when I hit stop).

All I want is to set mozplugger to use VLC.

---

### Post by Hero of Time on 2007-05-05
What I added to /etc/mozplugger doesn't work as planned. I get a white screen where the video should be. Any idea what need to be changed, since I took most of the config from Totem.

```
### VLC

define(VLC_CMD, [vlc $1</dev/null])

define(VLC_EMBED,[embed noisy ignore_errors])

define(VLC_NOEMBED,[noembed noisy ignore_errors: VLC_CMD("$file")])

define(VLC_VIDEO_STREAM,[stream VLC_EMBED("$file")
	stream VLC_NOEMBED("$file)])

define(VLC_AUDIO_STREAM,[controls stream noisy ignore_errors: VLC_CMD("$file")])
```

---

### Post by Hero of Time on 2007-05-06
Bump.
Anyone has any idea how to setup vlc in the plugin?

---

### Post by kerry_s on 2007-05-06
Did you add it to the bottom to tell when to use it. I'm guessing you would add your VLC_VIDEO_STREAM where ever you see MP_VIDEO_STREAM() that way it knows you want to use it with ?.mov, qt, etc...

Ohh, and you were right the gxine is broken now, i ended up going with mplayer+w32codec, my nephew just has to check out those apple trailers. :)

---

### Post by Hero of Time on 2007-05-06
Yes, I did add VLC_VIDEO_STREAM() to them where I found the MP and TM parts aswell. If I didn't then I wouldn't see a white square where there should be the video or "Plugin Content".

---

### Post by kerry_s on 2007-05-07
I think i found the problem-> [http://my.opera.com/community/forums/topic.dml?id=186457](http://my.opera.com/community/forums/topic.dml?id=186457)

---

### Post by Hero of Time on 2007-05-07
Thanks for the link. I tried what they said there, but the plugin doesn't work. It gets loaded, I can set it to media types, but I keep getting a white space. Guess I have no other choice then to install Mplayer. At least I know that Opera is working on some of the problems with the VLC plugin, so perhaps on the next release it's fixed. I'm just happy that everything works alright. Luckily most sites use flash player for media, only a few use quicktime or windows media. One thing is sure, Linux is now my main OS on my laptop, just need to 'convert' my NTFS data partition to ext3 for linux to write on (I know there is a NTFS-write driver, but I don't trust it yet).

Thanks for your help kerry_s. Perhaps someone else has tried mozplugger with vlc and got it working somehow. For now, I will install mplayer.

---

### Post by kerry_s on 2007-05-07
Yeah, mplayer worked right away for me. I did look around alot for the vlc problem but i haven't found anything more, if i stumble on anything else later i'll post back here. I'm still trying to get the feel of opera so i been googleing all kinds of things opera, there's alot to read. So far i got the speed were i want it, finally figured out my host block list was slowing it down, so i just put a block list right in to opera. I put a open with firefox line in the menu. Made a couple of buttons so i can minimize the look.

Oh, i also snagged that speed dial for my firefox. :)

---

