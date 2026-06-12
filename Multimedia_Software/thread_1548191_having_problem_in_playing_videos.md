---
title: "having problem in playing videos"
date: 2010-08-07
forum: Multimedia Software
---

### Post by supersas on 2010-08-07
hi,
i am new at using ubuntu. i am having problem in playing any kind of videos. i have installed many codecs but the video still dont work properly. 
when i try to play an .flv video then it runs for some time(atmost 1minute) then it stops giving the error:"Disconnected:connection terminated" 
and when i try to play .avi video then that i can hear the voices but there is a bad video and it also stop after a while giving the same error:"Disconnected:connection terminated".

here is my system's hardware: 
processor: 1.2 ghz
ram: 480mb
graphics: 32mb
harddisk space: 60 gb

Please help me through this problem

---

### Post by little_penguin on 2010-08-08
There seem to be a few threads with this "Disconnected: connection refused" problem lately - I'm not sure why it is happening but it seems to be affecting the default Movie Player program (Totem)? You could try playing the files in vlc and see if it helps. To install the vlc player, you can either search for it in Synaptic Package Manager

or open a terminal and type 

```
sudo apt-get install vlc
```

Then run vlc and open one of your video files.

---

### Post by luigi_mb on 2010-08-08
I am afraid your hardware (32MB of video memory and 4980MB RAM) can not cope with your video files.


/luigi

---

### Post by supersas on 2010-08-08
hey,, that vlc solved my video problem. now i can see a very good quality video. thanks.. 
but i've got another problem and that is when i play the movie on vlc player then i hear the sound for 5 to 10 minutes and then it stops whereas the video keeps on playing. now whats that???

---

### Post by little_penguin on 2010-08-09
Good, there's been progress with the video then :) As for the sound problem, check out the following thread, and its links/suggestions:
 
[http://ubuntuforums.org/showthread.php?t=1484569](http://ubuntuforums.org/showthread.php?t=1484569)
 
If the above thread doesn't help, you might want to create a new thread for the sound problem, so it hopefully catches the eye of a sound expert. Good luck.

---

### Post by supersas on 2010-08-13
thanx for the help :)

---

