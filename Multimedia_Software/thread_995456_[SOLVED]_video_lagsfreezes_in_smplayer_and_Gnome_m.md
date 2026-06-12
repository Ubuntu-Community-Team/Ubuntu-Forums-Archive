---
title: "[SOLVED] video lags/freezes in smplayer and Gnome movie player"
date: 2008-11-27
forum: Multimedia Software
---

### Post by spandanj on 2008-11-27
Hi,

sometimes video in smplayer and gnome movie player freezes. However, VLC player is able to play those files. I think it has something to do with adobe flash 10 latest version because usually the video freezes after I have been using flash player in firefox for a while. 

Closing all firefox windows solves the problem. I am able to play video in smplayer and gnome mplayer again. Or sometimes logging back in solves it.


How can I fix this permanently?

---

### Post by binbash on 2008-11-27
This maybe a pulse audio issue.Disable pulse audio for a while and try again.

---

### Post by spandanj on 2008-11-29
Update on situation; still unsolved.

Ok. smplayer stopped playing even though I was not using flash in firefox. I did have one firefox window open. Although, NOT using flash 10.

If it is a conflict in pulse-audio, then how come I don't see a stream of flash-10 of firefox when in PAVU-CONTROL when I am using flash 10. It suggests to me that flash-10 is not even using pulse. However, I have no way to find out for sure since there isn't a flash 10 configuration window.

Also, although vlc is able to play files when Smplayer or Gnome player can't, VLC does not give me any audio output. THOUGH, VLC doesn't give me audio output AT ALL - even in a normal situation - since I upgraded it to latest 0.9 or something. So, I don't use VLC at all. However, it can always play video even when smplayer and gnome are freezing. 

So, what do I do?

---

### Post by spandanj on 2008-11-29
Ok,


SMplayer is freezing more frequently now. I need a solution to this ASAP.

SMplayer seems to be freezing if I have a video paused on it for too long ~ more than 3 minutes. I did have one firefox window open concurrently when this occurred. However, I only had gmail open.....this is making me believe that this freezing problem has different cause - probably not a conflict with adobe flash 10. ALSO, re-opening SMplayer does not solve the problem. If I close smplayer and restart the program to play the video - its still frozen....!

This is separate from the other problem that I am having which is no audio in flash player 10 if I have banshee open. Flash 10 does not show up as a stream in my pavu-control which means it's not using pulse-audio. BUT, that is a separate problem with a separate thread that I have made.

does anyone have a solution to SMplayer/Gnome movie player freeze-up problem???

thank you.

---

### Post by rvm4000 on 2008-11-29
Have you tried to change the audio driver in smplayer to alsa instead of pulse?

---

### Post by spandanj on 2008-11-29
> **rvm4000 said:**
> Have you tried to change the audio driver in smplayer to alsa instead of pulse?


It Worked!!!!!

changed audio driver to ALSA. It works now.


So, the problem was with pulse...damn it. what's so hard about simplying things, ubuntu devs???? don't throw new **** at us just to try it out. first, make it work flawless, and then give it to us. **and, please don't confuse me with alsa, and pulse, and what not. JUST MAKE IT WORK.** I am not asking you to make a super-complicated program work here! it's about the freaking system audio. Please, Just.Make.It.Work! I don't know how alsa, and pulse work. And, I don't want to know! I can't believe I have to waste time dealing with this **** instead of doing actual work. 

[I]**thank you for helping me. also, to the person who helped me -- can you also help me with flash 10's no audio WHEN I have banshee open. any clue about that. Infact, does flash 10 even use pulse? cuz it doesn't show up in my streams. Also, I set vlc to use pulse-audio. It shows up as a stream in pavucontrol. However, No audio from VLC. what's wrong.  THANK YOU. **
[/I]

---

### Post by spandanj on 2008-11-29
ok,

So, I don't want to use ALSA in SMplayer because it only lets me one SMplayer window at a time. I want to be able to have two different videos open in seperate SMplayer videos which I was able to do when I selected pulse-audio...


any solution?

---

### Post by rvm4000 on 2008-11-30
Actually alsa should allow you to play several things at a time.

I've just tried to open two videos in smplayer and it works perfectly.

Just be sure the option "Use only one running instance of smplayer" in Preferences->Interface is not checked.

---

### Post by spandanj on 2008-11-30
> **rvm4000 said:**
> 
Just be sure the option "Use only one running instance of smplayer" in Preferences->Interface is not checked.

Yup. that solved it. Although I don't remember selecting ONe instance at a time. And, I was able to play multiple videos only yesterday. weird.

thanks

---

### Post by Gouz on 2009-11-24
Hey all

I know that the problem is a bit old. For me ALSA does not work. It freezes
I had to use pulse to make it not freeze :/

Weird isnt it?


Gouz

---

### Post by Light-kun on 2012-07-22
Me too - with ALSA SMplayer freezes randomly until stop/play activated, after switching audio output to pulse - it lags instead of freezes, but continues to play - so it's way better.

---

