---
title: "Bad Video Playback horizontal lines."
date: 2009-09-14
forum: Multimedia Software
---

### Post by dsevastakis on 2009-09-14
hi,

to begin with, my pc setup is: 4core at 2,66GHz, nVidia GeForce 9800GT, Ubuntu 9.04 x64-bit. I have 2 screens connected as TwinView. main screen is 19" 1280x1024 75Hz and secondary screen is 32" 1360x768 60Hz.

The problem is that when i play a video (all media players have this problem) i get 1 or 2 horizontal lines flickering across the screen. this happens when there is a lot and fast motion. It is very disturbing:/ 
I also read some other posts about this, and tried some of the solutions but nothing works for me.. 
video output on vlc is Xv, i tried disabling compiz (compiz-switch) still nothing.. sync VBlank enabled still nothing..(although i read that for the sync VBlank to work good i have to set the refresh rate above 60HZ, but my secondary screen only goes up to 60.. so i don't know if that has anything to do with.. any ideas?

thanks in advance..!!!!

---

### Post by lovinglinux on 2009-09-14
I had this issue on Hardy Heron and like you, I have tried lots of workarounds without success. When I installed Jaunty (I'm on 32bit), the problem went away.

Yesterday I have tried Karmic alpha, but decided to go back to Jaunty. For my surprise, the video tearing was back, even after re-installing all previous installed applications and libraries. Additionally, I didn't change any settings, since I have a separate home and I have restored any changes to configuration files outside home, like xorg.conf for example.

Anyway, I figured out the problem. There is a bug in the nVidia driver related to permissions, that removes the direct rendering settings from xorg anytime I start nVidia settings.

If I run the code below, it tells direct rendering is off, unless I run it with sudo:

```
glxinfo | grep -i direct
```

So after some research, I found [this bug report](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249), which also provides a fix.

Basically, I had to edit /etc/rc.local

```
gksudo gedit /etc/rc.local
```

and add the following before "exit 0":

```
chmod 666 /dev/nvidia* &
```

Works like a charm now. No tearing at all. I hope this helps.

---

### Post by dsevastakis on 2009-09-15
hi again and thanks for your fast reply!
i tried your solution but still no good. i'll reinstall ubuntu to give it's partition more space, coz when i installed it i didn't have a lot of free space.. anyway, i'll see after the new installation the problem still occurs and i'll post back later! thanks again!:)

---

### Post by dsevastakis on 2009-09-15
So, i reinstalled ubuntu x64, made the changes in the xorg.conf and the rc.local as you said, i still get the tearing effect. i haven't install anything but the suggested updates, and vlc. so, no compiz no nothing.. what could cause this problem in a clean install?:/

---

### Post by lovinglinux on 2009-09-15
> **dsevastakis said:**
> So, i reinstalled ubuntu x64, made the changes in the xorg.conf and the rc.local as you said, i still get the tearing effect. i haven't install anything but the suggested updates, and vlc. so, no compiz no nothing.. what could cause this problem in a clean install?:/

Check the bug report link on my previous post and try the other workaround suggested there.

What do you get from running the command below?

```
glxinfo | grep -i direct
```

---

### Post by dsevastakis on 2009-09-15
direct rendering: Yes
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access,

---

### Post by lovinglinux on 2009-09-15
> **dsevastakis said:**
> direct rendering: Yes
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access,

Forget it, you already have direct rendering.

---

### Post by bekind2thenoob on 2009-09-15
are desktop effects enabled?

---

### Post by dsevastakis on 2009-09-15
nope.. only things i installed after ubuntu installations is: updates, vlc, amarok, etc..  but even before those where installed i could see the lines.. any thoughts?

---

### Post by mc4man on 2009-09-15
may help you, may not, see here
[http://ubuntuforums.org/showthread.php?p=7781484#post7781484](http://ubuntuforums.org/showthread.php?p=7781484#post7781484)

---

### Post by dsevastakis on 2009-09-16
still no luck:/ it's frustrating watching others people with the same kinda problem getting it fixed while yours just wont go away:P but you learn a lot in the progress, so it's worth it..:) any other ideas?

---

### Post by dsevastakis on 2009-09-16
in the VLC preferences window, advanced tab, in the "Memory copy module" should i be able to see the SSE and SSE2 options? coz i see that it is checked in the CPU features and i know my CPU supports both, so why isn't it in the Memory copy module opotions?:/ i dont know if that's the problem that causes the "tearing", it's just an observation..

---

### Post by dsevastakis on 2009-09-16
i just got another hint.. i dissabled the main monitor (19" 1280x1024) and played a video on the 32" 1360x768 and played without the tearing.. it was great.. so what causes this effect when having 2 monitors running on twinview?:/

---

