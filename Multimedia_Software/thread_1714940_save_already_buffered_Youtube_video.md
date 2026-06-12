---
title: "save already buffered Youtube video"
date: 2011-03-26
forum: Multimedia Software
---

### Post by maphew on 2011-03-26
In Firefox, how can I save an already fully buffered Youtube video for offline viewing? 

My bandwidth cap is fairly low and overruns are expensive. All of the addons and bookmarklets I've tried download the video again from the beginning.

I used to just have a peek in /tmp/ and copy the relevant files somewhere else. However the files aren't showing up there anymore, I'm not sure when that stopped happening. (c.f. [http://www.youtube.com/watch?v=JJTuUBo8LB8](http://www.youtube.com/watch?v=JJTuUBo8LB8))

I've used 'about:cache' to and scanned for incidences of "get_video" and "videoplayback". From the date stamp I think can see the particular entry I'm interested in, but the size is 0 bytes. There are "videoplayback" Youtube videos in there that I can save, (c.f. [http://superuser.com/questions/32438/saving-previously-viewed-youtube-videos/32676#32676](http://superuser.com/questions/32438/saving-previously-viewed-youtube-videos/32676#32676)), but not the one in particular I'm after.

Going to the cache directory in Nautilus, ~/.mozilla/firefox/xxxxxxxx.default/Cache, shows a few video files, but none larger than 5-6mb and the video I'm interested in should be at least 10 times that.

I searched the filesystem for all files modifed in the last 24 hours and larger than 50mb (cd / && sudo find . -type f -mtime -1 -a -size +50M) (([http://www.debuntu.org/how-to-find-files-on-your-computer-with-find](http://www.debuntu.org/how-to-find-files-on-your-computer-with-find)))

The video has to be stored *somewhere*, I still have the tab open and I can play/pause at will, but where is it?

I'm using Firefox 3.6 on Ubuntu 10.10, 32bit.
thanks in advance for your thoughts.

---

### Post by Script Warlock on 2011-03-26
clipgrab or minitube is a good tool please read [first]("http://www.youtube.com/t/howto_copyright")

---

### Post by MrEgg on 2011-03-26
It used to be in /tmp, but now it's stored in RAM. You can install a firefox add-on such as [Easy Youtube Video Downloader]("https://addons.mozilla.org/en-us/firefox/addon/easy-youtube-video-downl-10137/"), or you can access your ram directly - a much geeker way you may find more satisfying.

The geek way. In Terminal :

1. Find flashplayer's pid
```
pgrep -f flashplayer
```

2. Navigate through ram
```
cd /proc/xxxx/fd
ls -l
```
Note: xxxx is for the pid returned in step 1

3. In ls -l returned, find the one that links to '/tmp/FlashXXXXXX (deleted)' (I find it's almost always 16 on my machine). Copy that to your drive :
```
cp 16 /home/joe/video.flv
```
Note: adjust 16 to your own result

That's it.

---

### Post by maphew on 2011-03-26
awesome! thank you MrEgg. For me it was 16 and 24, with 16 being the one I actually wanted. 

Sure wish I could navigate ram like this in Windows!

---

### Post by MrEgg on 2011-03-26
> **maphew said:**
> Sure wish I could ________ like this in Windows!

Stop hurting yourself !!  :D

---

### Post by reliablepankaj on 2011-04-01
> **MrEgg said:**
> It used to be in /tmp, but now it's stored in RAM. You can install a firefox add-on such as [Easy Youtube Video Downloader]("https://addons.mozilla.org/en-us/firefox/addon/easy-youtube-video-downl-10137/"), or you can access your ram directly - a much geeker way you may find more satisfying.

The geek way. In Terminal :

1. Find flashplayer's pid
```
pgrep -f flashplayer
```

2. Navigate through ram
```
cd /proc/xxxx/fd
ls -l
```
Note: xxxx is for the pid returned in step 1

3. In ls -l returned, find the one that links to '/tmp/FlashXXXXXX (deleted)' (I find it's almost always 16 on my machine). Copy that to your drive :
```
cp 16 /home/joe/video.flv
```
Note: adjust 16 to your own result

That's it.

wow..super cool post....:KS

---

### Post by nothingspecial on 2011-04-01
This load of gobbldygook will do it in one line and play it

```
f="$(ls -l  /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && cp /proc/$(pgrep -f flashplayer)/fd/"$f" . && mplayer "$f"
```

Ugly, I know.:roll:

It saves it to the directory you are in. It won't work if you have more than 1 video cached. If you don't rename the video then the chances are you will overwrite the last one with the new one.

Have fun :popcorn:

---

### Post by mavenuparker on 2011-05-09
You are awesome...thanks It really worked

---

### Post by anspectrum on 2012-10-21
> **MrEgg said:**
> It used to be in /tmp, but now it's stored in RAM. You can install a firefox add-on such as [Easy Youtube Video Downloader]("https://addons.mozilla.org/en-us/firefox/addon/easy-youtube-video-downl-10137/"), or .................................. 16 to your own result

That's it.


Hail to the KING.
=D>

---

### Post by howefield on 2012-10-21
Old thread closed.

---

