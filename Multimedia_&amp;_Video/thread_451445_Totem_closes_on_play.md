---
title: "Totem closes on play"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by shiznatix on 2007-05-22
Hello,

I recently downloaded some video torrents and when I go to the folder, the preview thumbnail thing shows up just find and everything but as soon as I try to play them with Totem, totem opens then closes right away. Other avi files work just fine but these 2 obviously don't.

When I run totem from the command line and try to play them it does the same thing but I get this output in the terminal:

> shiznatix@shiznatix-laptop:~$ totem
No accelerated IMDCT transform found
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 48 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


If anyone has any ideas that would be fantastic.

---

### Post by shiznatix on 2007-05-22
Ok so I decided to try different video players and since mplayer never ever works for me I tried vlc player. Installed it and opened the file and bam, success! Then, thinking all would be well, I closed VLC and did other stuff. A few minutes later I reopened VLC and opened the file again and now its doing the same thing totem was doing! It was working before, I skipped through the entire video watching different segments, no problem. I don't see how it all of a sudden stopped working.

So, I ran VLC from the command line to see what it said when it closes. Here is the entire output:

> shiznatix@shiznatix-laptop:~$ vlc
VLC media player 0.8.6 Janus

** (.:6077): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
[00000335] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83


It says 'insufficient resources' but I am not running anything crazy, I just restarted my computer and I am only running Firefox and a terminal. When it worked the 1 time I had like 10 programs running so I don't see where that is coming from. Any help would be awesome.

---

### Post by shiznatix on 2007-05-23
*bump* please, anyone?

---

### Post by floydwilde on 2007-05-29
I've a similar issue, using VLC, and seems like not enough memory.   Thought my system would have enough resources 

root@ipex:~# grep "model name" /proc/cpuinfo 
model name      : Intel(R) Celeron(R) CPU 1.80GHz

root@ipex:~# free -m
             total       used       free     shared    buffers     cached
Mem:           756        710         45          0         11        461
-/+ buffers/cache:        238        518
Swap:         1576          3       1572

root@ipex:~# lspci | grep Graphics
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

I see these errors:
VLC media player 0.8.6 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86


Trying to play stuff on [http://www.railscasts.com/](http://www.railscasts.com/)

---

### Post by mpphilli on 2007-06-07
Are either of you using Beryl?
I have the same issue with just about any player that i try if i have Beryl running.

MIKE

---

### Post by DizzyTech on 2007-06-13
I hate to say this, but turn off Desktop Effects (Compiz or Beryl).  That fixes it.

---

