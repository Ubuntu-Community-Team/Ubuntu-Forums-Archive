---
title: "Capture Line-In"
date: 2010-07-08
forum: Multimedia Software
---

### Post by sk1nk on 2010-07-08
Greetings,

I switched to 10.04 lately but I have a TV card, which gives it sound into the Line-In of my Mainboard.

Tuning Up "Line" in the Alsamixer makes it playing the sound on the Analog Output/Headphones but not on the digital out the system uses normally.

Since the old mixer is gone, how could I make Ubuntu listen to the Line-In and play it on the SPDIF instead of the Analog device?


```
arecord -D hw:0,0 -f dat | aplay -D hw:0,1
```

works but has an annoying delay.

Thanks so far, 

Sk1nk

---

### Post by sk1nk on 2010-07-09
Or is there some Service wich just can play what is comming to the Line-In, like the selftest in Teamspeak where I just hear what I say?

---

### Post by cchhrriiss121212 on 2010-07-09
You can do this with audacity, add an audio track then enable monitoring after checking software playthrough from preferences.

---

### Post by sk1nk on 2010-07-09
Idea is nice, seems to do what I want exept I can't make it playback.

Switched through all playbackdevices but don't hear anything ... 

think I'll check the wiki, but maybe somebody got an idea while I do so.

---

### Post by cchhrriiss121212 on 2010-07-09
You need to select the correct recording device as well as the right playback device.

---

### Post by sk1nk on 2010-07-09
was my fault, I changed the asound.conf and forgot to restart.

Works for me now, thanks alot.

Only problem is that the record, and so the sound stops after around 3 minutes.

But this is a program that does what I need, so it isn't impossible.

Edit: I tried 2 times more, now it doesn't stop. Works fine, thanks alot ...
Edit2: stopped after 10 minutes now :(

---

### Post by sk1nk on 2010-07-09
Ok, I just kept googleing, and found [This Thread]("http://ubuntuforums.org/showthread.php?t=814285&page=3") where they configure a combined sink.

But I'm not able to follow all the steps in there so maybe could grap the idea and help me.

Finally got it to work:

pactl load-module module-loopback did the job.
Now i just have to make Ubuntu load it by default and everything is fine.

---

### Post by cchhrriiss121212 on 2010-07-09
You should be able to just paste that into /etc/modules using :
```
sudo gedit /etc/modules
```

---

