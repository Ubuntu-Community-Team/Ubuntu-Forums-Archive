---
title: "Can't play Online NOVA videos"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by rbhkamal on 2007-09-23
[NOVA Video]("http://www.nvcc.edu/tvcenter/vod/CourseView.aspx?Course=BEN+FRANKLIN+VISITS+NOVA")

Can anyone tell me why I can't watch that online video? I tried mplayer, xgine and tetom but they all gave me errors that the video cannot be found... :(
I really need this because I'm taking an online course and I have about 12 hours of videos to watch. :popcorn:

Please help me.

Edit: The error is actually:
"Totem could not play 'mms://vod01.nvcc.edu/vod/Public/Ben Franklin visits NOVA/Ben_Franklin.wmv".

---

### Post by yabbadabbadont on 2007-09-23
I ran this in a terminal and it worked:
```
mplayer mms://vod01.nvcc.edu/vod/Public/Ben%20Franklin%20visits%20NOVA/Ben_Franklin.wmv
```

---

### Post by R.Bucky on 2007-09-23
check out VLC media player...

---

### Post by rbhkamal on 2007-09-23
Thanks, it worked when I opened it with mplayer using the terminal.

But it doesn't work when I do: 1) Play with captions 2) Open the downloaded file using VLC, Mplayer or Tetom?

How do I set me default media player?

Edit:
Here is what heppens when I try to play the file
```

*username*@*username*-laptop:~/Downloads$ mplayer MTH
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing MTH.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll


Exiting... (End of file)
*username*@*username*-laptop:~/Downloads$ dir MTH 
MTH

```

---

### Post by rbhkamal on 2007-09-23
Here is what happens when I use VLC:
```

####@###-laptop:~/Downloads$ vlc MTH 
VLC media player 0.8.6 Janus
[00000348] main access error: Connection to www.nvcc.edu port 1755 failed: Connection timed out
[00000348] access_mms access error: failed to open a connection (tcp)
[00000348] main access error: Connection to www.nvcc.edu port 1755 failed: Connection timed out
[00000348] access_mms access error: failed to open a connection (tcp)
[00000348] access_mms access error: cannot connect to server
[00000348] access_mms access error: invalid chunk FATAL (0x533c)
[00000348] access_mms access error: header size == 0
[00000351] main access error: Connection to www.nvcc.edu port 1755 failed: Connection timed out
[00000351] access_mms access error: failed to open a connection (tcp)
[00000351] main access error: Connection to www.nvcc.edu port 1755 failed: Connection timed out
[00000351] access_mms access error: failed to open a connection (tcp)
[00000351] access_mms access error: cannot connect to server
[00000351] access_mms access error: error: HTTP/1.1 400 Bad Request
[00000346] main input error: no suitable access module for `mms://vod01.nvcc.edu/vod/Students/MTH%20173/MTH%20173%20-%2001.wmv?SAMI=http://www.nvcc.edu/tvcenter/vod/PlayCaptions.aspx?p=MTH+173,MTH+173+-+01'
[00000280] main playlist: nothing to play
[00000280] main playlist: stopping playback
###@##laptop:~/Downloads$ 


```

Let me know if you have any questions.

---

### Post by Neobuntu on 2008-06-28
What's the deal?

Quicktime and wmv video play; from other sites, but not Nova.

I'm using Kubuntu Hardy and the mplayer plugin.

---

### Post by rbhkamal on 2008-06-29
If I remember correctly I was able to play it from mplayer directly using CL mplayer <url>. But it was UGLY!!! ](*,)

If you go to college, you should give up on Linux in general. There is too much time waisting just to get things working; Linux is not yet ready. I used dual boot between Fedora 9 and Windows XP and they lived happily ever after. ):P

Regards,
RK

---

