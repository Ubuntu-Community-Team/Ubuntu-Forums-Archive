---
title: "Amarok not playing MP3's, even though Songbird/Rhythbox does"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by Toastfuzz on 2007-04-29
So I'm just first starting with Ubuntu, and I like it alot except that I cannot make MP3's play in AmaroK. They play in Rhythbox and Songbird, but those two programs don't have a graphical equalizer, which is a real drawback for me.

When I try to play a song, the visual volume levels go all over the place, and the song is playing in the program, just there is no audio output. I can't figure out what the issue is; MP3's wouldnt play in the regular media player either. For some reason some programs will play but others just think they're playing but theres no sound. Any ideas?

Thanks

---

### Post by frohike759 on 2007-04-29
I have the same problem.  I have read that the sound server select might me the issue. I will  be working on it so I will post back if I find a solution.  For now I see you have something working.  I am currently using XMMS just to do simple mp3 playback.

Hope to post again soon

---

### Post by frohike759 on 2007-04-29
I am running Kubuntu 6.10 (Edgy) so this may be different but here is what I did to get it to work.

Open up amarok and go to Settings - Configure Amarok - Engine tab (on the left side)
Where it says "Output plugin" there is a drop down menu for me with five options.
alsa
oss
arts
esd
file


I selected **_oss_** to make it work. 

At a command prompt try _lsmod | grep alsa_  and see if you get any results 
also try _lsmod | grep arts_

If you get result from either of them try the "Output plugin" setting to either of those.
You should get results from one or the other.  Then change the setting accordingly. I hoped this helped.

From the Lone Gunmen - Later

---

### Post by Toastfuzz on 2007-04-30
I got output from OSS, but it still won't play any sound. Like I said, the playbar still has the file playing, just no sound coming out of the speakers. I'm still trying to find an answer, but right now I'm stumped.

---

### Post by Sethalos on 2007-04-30
Ok, have you checked if the volume level on AmaroK is down?  Should see it to the right of the EQ?  I know it's probably a stupid question, but never know.

Seth

---

### Post by Toastfuzz on 2007-04-30
I've determined its a problem with Xine. I installed a bunch of Xine stuff but when I ran the diagnostic it had a bunch of things missing, and told me to get the latest xine-lib. This wouldnt be a problem if I wasn't a Linux noob, because I downloaded the xine-lib-1.1.6.tar.bz2 but for the life of me I cant figure out how to extract and install it.

When I put this in:

tar xfvz xine-lib-1.1.6.tar.bz2

It says it can't find the directory. I've tried typing out the whole command line to the desktop and all, but it still doesnt see it. Why is this?

EDIT: By the way, I know its the Xine issue because sound also doesnt work in Xine movie player (movie plays but no sound) and like I said before, the diagnostic told me there were multiple things missing and I needed the xine-lib. I just dont know how to install it.

---

