---
title: "No signal w/ KWorld ATSC 110 Tuner in Jaunty"
date: 2009-04-26
forum: Multimedia Software
---

### Post by mboudro on 2009-04-26
I am normally able to figure everything out after a little searching, but this one I've been working on for some time and still haven't found a solution. 

I'm running Jaunty 9.04 on a P4 with 1GB ram. I have a KWorld ATSC 110 tuner card installed. I read through several tutorials and I believe I have installed everything correctly. I can see the log items for the initialization of the card, including the saa713x and nxt2004 firmware. When I run either MythTV or TVTime, I cannot find any signal from the tuner card. I originally thought it may be a MythTV configuration problem, but I installed TVTime and it cannot pick up an analog signal from the card as well. When using VLC Media Player I receive typical "noise" on the screen, but no stations. MythTV will not let me access the card at all, it seems. TVTime just displays the no signal error.

Does anyone have any experience getting this particular card working? I am not a Linux/Ubuntu beginner, although I don't have a lot of knowledge in the tuner card area.

Thanks in advance for any assistance.

---

### Post by mboudro on 2009-04-28
*Bump

No one has any idea on this one? Can anyone even point me in the right direction??

Thanks.

---

### Post by mcendoo on 2009-05-05
There have been issues with the KWorld 110/115 cards for some time, see this thread [http://ubuntuforums.org/showthread.php?t=959407&highlight=kworld](http://ubuntuforums.org/showthread.php?t=959407&highlight=kworld).  I have a Kworld 115 and have the analog tuner working in Jaunty with tvtime, and I understand that the 110 has the same issues.  To get it working I had to compile and install the lastest version of v4l.

---

### Post by azmyth on 2009-05-31
I use the same exact card in Jaunty without issue. There's a process where you have download the kernel docs then you have to download the proper firmware and move it to the proper directory. Did you do all that? I didn't have to compile anything.

---

