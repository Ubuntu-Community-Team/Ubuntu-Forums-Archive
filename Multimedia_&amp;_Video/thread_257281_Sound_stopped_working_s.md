---
title: "Sound stopped working :s"
date: 2006-09-14
forum: Multimedia &amp; Video
---

### Post by Martin A on 2006-09-14
Thats it.... I was listening to music with XMMS and the sound just died. I've tried rebooting, the speakers and soundcard both work OK.... I don't know what else to try!

Any Ideas?

Thanx,

Martin, Eternal N00b.

---

### Post by the lush on 2006-09-15
OK, I am very new to this Ubuntu stuff, but have experienced this problem myself. It started on Monday, my headphones would only produce small clicking sounds, and then a while later would do nothing. I tried re-booting, changing volume levels, adding all sorts of stuff gleaned from these forums using terminals and editing files, but nothing worked. After the last attempt I was ready to give up (mostly due to all the problems I am having with Ubuntu on my home machine - this problem was affecting my work machine), when I managed to get sound back. Here's what I did:

1. Right-click on the volume icon in the tray
2. Select 'Open Volume Control'
3. Click 'File'
4. Go to 'Change Device'
5. It was set on Alsa, I changed it to OSS
 Sound immediately started - I was showing a video in Youtube
6. Change device back to Alsa - because all the people who know all those command line things seem to think it is better
 Sound still works

I have no idea why this worked, but it did, perhaps someone out there can explain it? Hope it helps someone else.

\still a huge believer that turning things off and then on again is normally the best way to fix a problem
\\ now I have to try and do battle with Automatix on my home machine - does pppoe stop it from working? Gah, new thread needed.

---

### Post by deadgobby on 2006-09-15
Some times sound just gets a little funky. What you can do is open up the terminal and type in 
killall esd

Gobby

---

### Post by Martin A on 2006-09-15
Thanks for the replies:) 

But sound still doesn't work....

I can see me haing to reinstall Ubuntu in the not too distant future....

](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by adds2one on 2006-09-17
My sound died in the last few days too. I was listening to music maybe three days ago and then I installed the recent kernel updates through synaptic. I haven't even used my computer since then until right now when I discovered that I have no sound. My sound cards aren't loading properly, dmesg is full of errors.

I have posted my errors here: [http://ubuntuforums.org/showthread.php?t=259436](http://ubuntuforums.org/showthread.php?t=259436)

---

