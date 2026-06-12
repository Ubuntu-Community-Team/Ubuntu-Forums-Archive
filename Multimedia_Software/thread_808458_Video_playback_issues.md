---
title: "Video playback issues"
date: 2008-05-26
forum: Multimedia Software
---

### Post by Bloemetjesgordijn on 2008-05-26
Hi All,

I am a complete newbee @ Ubuntu, so pls bare with me. Ihave some severe difficulty in playing my videos, and I cant get my head arround it.

I am using VLC, Totem and MPlayer. All are hanging / blurry images and audio is out of sync.

Error messages
MPlayer: Error opening/initializing the selected video_out (-vo) device)
VLC: none
Totem: failed to connect stream: Invalid argument

Already done:
- output to x11 in both Mplayer and VLC no success.
- disable pulse audio to salsa (in MPlayer) no success
- played video on FireFox -> no success
- googled for a solution -> no success
- diabled Compiz -> no success
- opend a beer ....helping but not regarding to video playback :-)


Pretty please with sugar on top, please help me out here

Kind regards,

Bloemetjesgordijn

---

### Post by Bloemetjesgordijn on 2008-05-27
- BUMP-

I have been thinking, cause multiple players have issues, it might be due to:
- HardWare ->onboard GPU is conflicting with add GPU card
- OS -> Ubuntu Hardy is not correct installed
- ATI drivers ->....


any sugestions.....

---

### Post by sayakb on 2008-05-27
If you do not use Compiz, try the OpenGL video output mode for VLC.

---

### Post by sent17inel on 2008-07-01
Im having the closest related problems to this you. I made sure all my players played video using X11 rendering. the reason why i want it to be x11 is because when i use compiz and use the cube effects or others it will draw the video perfectly. the downside is now all my videos i play look blurry. not horribly blurry. but not as clear as im used to. any ideas?

---

