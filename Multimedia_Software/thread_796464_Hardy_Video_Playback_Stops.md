---
title: "Hardy Video Playback Stops"
date: 2008-05-16
forum: Multimedia Software
---

### Post by Mizutsuki on 2008-05-16
Ever since I upgraded to Hardy, I can't watch videos.  In both mplayer and Totem, with any video output driver it does the same thing.
The video starts and the first 2-3 frames get rendered, and then the playback stops for some strange reason.  No error gets output to console, the video is not paused.  If I jog the video to near the end in Totem it starts to play back 1 frame at a time (very slow, but no tearing.)  There is very little CPU usage.
Has anyone had this problem?
Thanks.

---

### Post by Lostincyberspace on 2008-05-18
I have the same problem I am looking for a solution right now and for me it is not Dependant on the viewer I use.

If I find any thing I will post back.

EDIT: This is really weird I just tried to run again after nothing and it runs. might be a problem with the codec try loading one with a different codec.

---

### Post by Mizutsuki on 2008-05-19
The most recent update to gstream fixed this.  No comment in the changelog speaks to the problem... so... mysterious problem: mysteriously solved.
Thanks.

EDIT: Err.... it's back.  So this is some sort of a phantom bug, I guess.  I'm not sure what I did to bring it back!

---

### Post by rclimb514 on 2008-09-29
I've been having this exact problem since upgrading to Hardy.  However, I was just able to solve it this morning...by reading the release notes:

> **Totem movie player and PulseAudio sound server**

    *Some users report problems with video playback in the GNOME movie player, and audio playback in other applications, due to an error when connecting to the PulseAudio sound server. Investigation of this possibly hardware-specific issue is ongoing. A workaround is to enter the System -> Preferences -> Sound dialog and change the Music and Movies sound playback option from 'Autodetect' to 'ALSA'.


I still have issues with audio in VLC, but I suspect that is related to different problems connecting to PulseAudio.

---

### Post by Toci on 2008-10-07
> **rclimb514 said:**
> I've been having this exact problem since upgrading to Hardy.  However, I was just able to solve it this morning...by reading the release notes:


> Totem movie player and PulseAudio sound server

*Some users report problems with video playback in the GNOME movie player, and audio playback in other applications, due to an error when connecting to the PulseAudio sound server. Investigation of this possibly hardware-specific issue is ongoing. A workaround is to enter the System -> Preferences -> Sound dialog and change the Music and Movies sound playback option from 'Autodetect' to 'ALSA'.


I still have issues with audio in VLC, but I suspect that is related to different problems connecting to PulseAudio.


Mplayer didn't even start for me, I was using VLC and it started playing perfectly but after 1-10 seconds it went black and did nothing, the button remained in play but that was it.

 I already had the Music and Movies sound playback option in "ALSA", so I changed it to "Pulse Audio Sound Server" and VLC doesn't play but Mplayer finally does!. Thanks a lot.

---

### Post by wulfhound on 2008-10-25
> **Mizutsuki said:**
> Ever since I upgraded to Hardy, I can't watch videos.  In both mplayer and Totem, with any video output driver it does the same thing.
The video starts and the first 2-3 frames get rendered, and then the playback stops for some strange reason.  No error gets output to console, the video is not paused.  If I jog the video to near the end in Totem it starts to play back 1 frame at a time (very slow, but no tearing.)  There is very little CPU usage.
Has anyone had this problem?
Thanks.

I am getting the exact same thing. I know all my videos are good because I watched them all (the same files) on Fedora 9 with no issues with playback. 

I am currently looking for solution. Hopefully the option of changing to alsa instead of auto-detect will work...

Edit: This is not working as a fix. Does anyone have any suggestions? I'm on hardy heron, x64...

L

---

