---
title: "FFmpeg problem"
date: 2008-08-23
forum: Multimedia Software
---

### Post by kane77 on 2008-08-23
I have a problem with ffmpeg and I am afraid I am the one who caused it, but I will be very grateful if someone help me to solve it..
I was using medibuntu's ffmpeg before I decided to try to compile my own, but that was before I knew of checkinstall so I just installed it using "sudo make install", but then I probably mistakenly reinstalled it with the repository package.. Now I cannot run ffmpeg.. I get this error message:

ffmpeg: symbol lookup error: ffmpeg: undefined symbol: ffm_nopts

I tried numerous times to
a) sudo make uninstall the compiled version of ffmpeg 
b) sudo aptitude remove ffmpeg && sudo aptitude purge ffmpeg
but nothing helps and I still get the same error message
And I tried the normal repository version and medibuntu, but they all give the same error..
Can someone help me to clean this mess?

---

### Post by kane77 on 2008-08-25
bump

---

### Post by jstaczek on 2008-08-27
Same problem here. Looks like there was an issue installing libavformat. The following worked for me:

sudo rm /usr/local/lib/libavformat*
sudo make install

Hope this helps.

---

### Post by My_web on 2008-08-30
I'm having the same problem as Kane77 and I can't seem to solve it, anyone have any more ideas as everything I've tried has failed so far :(

Thanks in advance for your help :)

---

