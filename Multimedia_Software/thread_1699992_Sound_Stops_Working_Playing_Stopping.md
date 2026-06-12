---
title: "Sound Stops Working Playing Stopping"
date: 2011-03-04
forum: Multimedia Software
---

### Post by tangoking on 2011-03-04
As the title implies, the sound on my rig stops working after a while. Annoying as hell: I have to reboot my machine to get it to work again, which means that I have to reset my entire programming environment (with five full workspaces).

************ HOW DO YOU EXPECT ME TO PROGRAM WITHOUT TRANCE MUSIC????????????????

I'm running 9.10 Karmic.

Any suggestions? I have no problem killing processes to make this work.

---

### Post by tangoking on 2011-03-04
So I was a little upset, started whacking processes, and got it working again. So, if all else fails, try this:

DISCLAIMER: This may very well hang your system, and you may have to reboot.

1. Open terminal
2. type "sudo ps -e | grep pulse"
3. Note the <process ID> (for me, a four-digit number)
4. type "kill -9 <process ID>"
5. lather, rinse, repeat for any pulseaudio processes
5. type "pulseaudio"

Also--if you have any browser windows open (from games or anything) that might play music, close them.

Love,
tk

---

