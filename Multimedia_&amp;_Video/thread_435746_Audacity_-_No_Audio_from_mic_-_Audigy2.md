---
title: "Audacity - No Audio from mic - Audigy2"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by ksudbury on 2007-05-07
Right, I can speak through the Mic and hear it on my speakers through my sound card. 

I load up Audacity and try to record this and get nothing!? Any ideas 

In audacity I have tried every different input method in the drop down currently it is set on /dev/dsp 

The record and Mic volume is turned up in Audacity... 

The sound card is a sound blaster Audigy2.

Anyone got any ideas? 


Thanks in advance

---

### Post by Jeffj on 2007-05-13
I was using Audacity in Windows and I thought I would try it in Ubuntu.

If I use alsamixer on the command line I can turn microphone boost on and off.

If I right click on the speaker I get a Volume control that lets me switch between an alsa mixer and an oss mixer. This interface lacks the microphone boost but has separate record and playback controls. Change with File|Change Device.

The main difference I see is that the changing the record level does not change the height of the wave in Audacity. I'm not sure what control I need to change.

---

### Post by detyabozhye on 2007-05-19
Same problem here, recordong worked fine with Dapper I think, I'm not sure if I did any recording when I ran Edgy.

---

### Post by detyabozhye on 2007-05-19
Check out this post: [http://ubuntuforums.org/showpost.php?p=2681937&postcount=7](http://ubuntuforums.org/showpost.php?p=2681937&postcount=7)

---

### Post by euchrid on 2007-06-07
I had to update the Alsa drivers; nothing else would work. See this post: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

---

### Post by PhilJ on 2007-06-07
I cured my Audacity problems by installing Audacity1.3.2 beta. Now the input selection button shows up and I can record BBC Radio Player streams like I used to in Dapper

[http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/](http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/)

Philj

Xubuntu Fiesty 7.04

---

