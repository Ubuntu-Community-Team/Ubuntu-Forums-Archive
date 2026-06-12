---
title: "Mp3 file problems"
date: 2009-01-19
forum: Multimedia Software
---

### Post by Bandanna on 2009-01-19
-ubuntu 8.10-


When I try to play Mp3 files through Totem, Totem will start and then do nothing... The program becomes unresponsive and I must force quit Totem.
Now I have played about a quarter of a song using it once prior. So I am very confused as to what the problem is...

When I try to play Mp3 through rhythm box it just... refuses to play.
The song shos up in playlist box (as it also does in totem) and it is unpaused but the song "time-bar" will not progress but I am able to drag the button to different times along the time bar. There is no audio however.

I have songbird installed also but I can not import my Mp3's for a reason unknown to me. the songs I have are grayed out and not able to be selected for import.

I read some guides that suggest using synaptics checking the repositories and then installing gstream-something.8
When I search "gstream" in synaptics It shows a great deal of gstream packages that are already installed, but they are all gstream10 something.10 or something, point being it is already a higher version than what the guides suggest which leads me to believe the guides are possibly outdated.
But what I have done is while in synaptics while under the search list for "gstream" once I scrolled to the bottom I saw "totem" and "totem g-streamer" So I right clicked the green box next to them and clicked mark for upgrade.I upgraded them and this is when I went back and tried to play an mp3 through totem and it worked! but only for about a quarter of the song and then it locked up and program became unresponsive and I had to force quit.

This is where I stand now, any suggestions?

---

### Post by metallicamike on 2009-01-19
do you have all of your sound settings set to alsa? and also do you have all of the gstreamer plugins? let me know

---

### Post by Bandanna on 2009-01-19
Sorry, I'm very new, and I have no Idea really as to how to go about checking these things.
And on a sidenote audio does play from youtube and other places.
So it's just my mp3 files and not like speaker problems  or anything like that

---------Edit----------------
Update: I have just found out that my totem movie player locks up and becomes unresponsive making it necessary to force quit all the time. Not just when using to open an mp3 file. It becomes unresponsive if I just go to apps>music and sounds> movie player.

-------Edit(2)------------------
Also when using rythm box I forgot to mention that after I try to play a music file and it doesn't work, it causes the program to become unresponsive and I have to force quit it also

---

### Post by metallicamike on 2009-01-19
tell me what happens with this command
```
aplay -q sound.wav
```

---

### Post by Bandanna on 2009-01-19
zack@ubuntu:~$ aplay -q sound.wav
sound.wav: No such file or directory

there was about a second 10 second pause after  entering the code.

---

### Post by metallicamike on 2009-01-19
ok, try it with ```
aplay -q question.wav
```

---

### Post by Bandanna on 2009-01-19
zack@ubuntu:~$ aplay -q question.wav
question.wav: No such file or directory


with the same delay

---

### Post by metallicamike on 2009-01-19
hmm, okay. go to system>preferences>sound and make sure that the mixer tracks devise is set to the one that says "(ALSA mixer)" and that you also test the other sections as well.

---

### Post by Bandanna on 2009-01-19
I set every option to ALSA or at least to whatever selection pertained to it. still same problems. rythm box locks up when trying to play song totem locks up when I run and songbird can't import.

---

