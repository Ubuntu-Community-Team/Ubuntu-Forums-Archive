---
title: "Things not working after recent upgrade to Kubuntu 15/KDE"
date: 2015-10-25
forum: Multimedia Software
---

### Post by richlion2 on 2015-10-25
Hello, 

I upgraded a few of my computers to the recent Kubuntu 15 version. Looks awesome - I never thought Ubuntu can pull off this trick with only ONE reboot :guitar:

KDE looks awesome :KS especially using Dark Breeze colour theme. 

I do have some issues though. One of them is playing some of the media types:

1) Encrypted DVD - some DVD's cannot be played/ripped. I found instructions here (From Ubuntu 15.10 onwards):
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
I usually use K3B to dump an .iso copy. The majority of DVD's are ok, but one box set I have is giving me some trouble.
I can use DVD-Rip to dump the .VOB files and watch them. I can watch the DVD's using VLC. So why can't I open the .iso version using VLC?
Just stops on a back screen, no errors.
Any way I can debug this?

2) VLC  can't play .flv files. One computer with previous version of Kubuntu - no problem at all. Upgraded - nothing, just a black screen.
 I am trying to use HandBrake to decode it into an m4v file and same thing. There is the sound, but no video. 
Are we missing some codecs here?

Regards, 
Richard

---

### Post by richlion2 on 2015-10-29
Hello, 

I guess I may have found my issue. The PC I updated did not have my AMD enabled in the System Settings, so I clicked on the box, the driver was downloaded and after the reboot I can now play files like .flv and .MOD (videos recorderd on cameras). 

However I still have some problem, for example both on Nvidia and my AMD card when I have other applications running the Skype text window flickers and the bottom of it has artifacts and the cannot see the part of the window where I need to type my text. Does anyone have the same issues? This looks like something not quite right with KDE.

Regards, 
Richlion

---

### Post by richlion2 on 2015-11-03
Hi, 

As I am still searching and still having problems and I wanted to post an update, as one day I could watch .MOV files, oddly the next day I could only here the sound, but no vision. After searching a lost I found that this has somehow fixed the problem with VLC:
```

sudo apt-get install ubuntu-restricted-extras

```

I still have some issues, Skype can still become flickery and jittery. All other applications are running smothely, I can start Skype and all is well, but then after minimizing and starting some applications Skype is getting garbled. 
Anyone has any problems like this?

Thanks, 
Richlion

---

### Post by richlion2 on 2015-11-10
Hello, 

it seems I am not getting any hints here. I think the main problem with some of the multimedia is related to applications blocking each other. I don't know what is at fault here, KDE, Pulseaudio, etc. When I reboot my machine I can run the videos using VLC. When I start watching videos in the web browser that is when I am having issues - no sound or no video. 

I keep getting updates to the system every day, but these issues so far has not been fixed. There are no errors. I can watch videos in web browsers, talk in Skype, listen to music using Audacious, but when I launch VLC , nothing. I have to reboot.

Any suggestions?

Regards, 
Richlion2

---

### Post by richlion2 on 2015-11-16
I found a hint on this thread:
[https://askubuntu.com/questions/44425/black-screen-when-playing-a-movie-in-vlc-player-just-the-sound-is-enabled](https://askubuntu.com/questions/44425/black-screen-when-playing-a-movie-in-vlc-player-just-the-sound-is-enabled)

So switching Accelerated Video Output solves the problem, although when you want to do fast-forward, the video becomes jittery. 
I shall mark this thread as resolved, however this is more of a workaround, because the real functionality in VLC is a bit buggy.

---

