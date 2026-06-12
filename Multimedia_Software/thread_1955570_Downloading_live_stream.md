---
title: "Downloading live stream"
date: 2012-04-09
forum: Multimedia Software
---

### Post by sowieso on 2012-04-09
I´m trying to save a stream to my computer from this adress:[http://www.landsdómur.is/adalmedferd/]("http://www.landsd%C3%B3mur.is/adalmedferd/") . These are hours of sound files and I have not been able to use programs like streamripper to grab it. The only way I find is playing it in VLC and using Sound Recorder to record what is playing on the computer. But that would mean playing around 30 hours of sound files. 

Is there any way to do it quicker? I´m using Ubuntu 12.04 Beta.

---

### Post by ron999 on 2012-04-09
> **sowieso said:**
> . 
Is there any way to do it quicker? 
Hi
The streams can be downloaded using **mPlayer**.

It won't be any quicker.:(
But you can download several files at the same time.:p

An example...
File number 1 on this page:- ```
http://www.landsdómur.is/adalmedferd/nr/9
```
Use this command:-
 
```
mplayer -dumpstream -dumpfile 5_mars_a_GHH_1.mp3 http://netvarp.althingi.is/landsdomur/5_mars_a_GHH_1.mp3
```

(Use right-click 'copy link location' to find the links)

Or you can use VLC instead of mPlayer like this:-
```
cvlc http://netvarp.althingi.is/landsdomur/5_mars_a_GHH_1.mp3 --sout="#std{access=file,mux=raw,dst='5_mars_a_GHH_1.mp3'}" vlc://quit
```

---

### Post by sowieso on 2012-04-09
@ron999 Thnx alot. I´ll give it a try.

---

