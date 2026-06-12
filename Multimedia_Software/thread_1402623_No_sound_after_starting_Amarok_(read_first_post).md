---
title: "No sound after starting Amarok (read first post)"
date: 2010-02-09
forum: Multimedia Software
---

### Post by damnated on 2010-02-09
In detail: If I run Amarok right after ubuntu starts, and then start a movie, there is no sound. It doesn't matter that the playback in Amarok is paused, stopped or active, there is no sound in the other player. Even if i exit Amarok, i don't get any sound. 

It is important to note that the other player is definitely a gnome application. I tried playing a song in Rhythmbox after Amarok was started, or play a video in Movie Player: no sound. I get sound from KDE video players, but the video doesn't work there, so that isn't an option. 

The only explanation i can think of, is that Amarok somehow "occupies" the sound drive, and it remains "occupied" even after the application was closed. Because if i start Movie Player before Amarok, this problem never appears. 

However, it is not a solution to start Movie Player after each system start-up just to avoid this issue. Any help would be greatly appreciated.

---

### Post by mustard greens on 2010-05-13
I am having the same problem.  ever since 10.04 upgrade, if I open amarock I loose sound in flash, VLC etc.  system sounds are still intact.

---

### Post by myk02k on 2010-05-13
Same, but now I have no sound at all except Amarok :(

---

### Post by grege on 2010-05-13
I do not have tis problem, but something to try

Start Amarok and in it's preferences configure Playback -> Configure Phonon - which is the KDE sound preferences applet - and set it to pulseaudio (it will be on the default ALSA)

Might require a log out and back to check if it works.

---

### Post by myk02k on 2010-05-13
> **grege said:**
> I do not have tis problem, but something to try

Start Amarok and in it's preferences configure Playback -> Configure Phonon - which is the KDE sound preferences applet - and set it to pulseaudio (it will be on the default ALSA)

Might require a log out and back to check if it works.

I got my sound back, but I was fooling around with this option before I did. I set Amarok to pulseaudio in the sound system configuration, and it continued to work despite every other application in Ubuntu. 

To the author of this thread, try this for a temporary fix:

Run 'pavucontrol'     (ALT+F2 or a terminal, it doesn't matter)
Try changing the inputs for applications within the 'Playback' tab if/until you can get sound from other applications to work.

---

### Post by cybrsaylr on 2010-05-18
I had no sound and couldn't play mp3s with Amarock after installing 10.04

I solved this sound problem the same way I did with 9.10 and the version before 9.10.

I just put this code in terminal and Amarock plays  perfect again.

> sudo apt-get install libxine1-plugins

Here's the thread that I got it from:
[http://ubuntuforums.org/showthread.php?p=8205915#post8205915](http://ubuntuforums.org/showthread.php?p=8205915#post8205915)

---

### Post by mustard greens on 2010-05-18
along with a fresh install and finding advice for the same plugin I have got everything working for the moment.  I will report back if that changes.

---

