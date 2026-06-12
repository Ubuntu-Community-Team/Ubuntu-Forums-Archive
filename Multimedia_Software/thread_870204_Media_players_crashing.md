---
title: "Media players crashing"
date: 2008-07-25
forum: Multimedia Software
---

### Post by nav211 on 2008-07-25
Hi guys.. 

Please help. Everything was working fine last night. Then today I installed the latest [Ati drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29") and now all media players crash when I play anything.avi/mp4/ogm. I have tried Movie Player, Mplayer and VLC. I know the video files are not corrupt and I can see icon previews. 

Is there any log file I can access to see whats causing the crash? 

My hardware:
DELL E1505/core duo/Ati X1400

Please help!!:(

Nav

---

### Post by ewanm89 on 2008-07-25
Which video output mode are the players using?

X11
XV
OpenGL...?

---

### Post by nav211 on 2008-07-25
Thank you.. Was set to default in vlc. I switched to X11 and it works!! Now I can get back to scrubs:) Thanks again ewanm89..

---

### Post by ewanm89 on 2008-07-25
np, I think default is xv, which uses the 2D graphics acceleration of the driver. So something seems broken in the driver (X11 uses no acceleration, opengl uses the 3D acceleration of the card).

---

### Post by nav211 on 2008-07-27
Can you help me decode this message?
```
VLC media player 0.8.6e Janus
[00000344] main private error: option glx-shm does not exist
libGL error: drmGetMagic failed
libGL error: reverting to (slow) indirect rendering
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  58
  Current serial number in output stream:  58

```

---

