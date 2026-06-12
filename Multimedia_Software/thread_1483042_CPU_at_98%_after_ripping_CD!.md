---
title: "CPU at 98% after ripping CD!"
date: 2010-05-14
forum: Multimedia Software
---

### Post by oxf on 2010-05-14
Hi, 

I  noticed the fan on this laptop is constantly runing after ripping a track from CD. I entered "top" into terminal and found this:

      ```
 top - 12:20:13 up  1:01,  2 users,  load average: 1.21, 0.96, 0.49
  Tasks: 128 total,   3 running, 125 sleeping,   0 stopped,   0 zombie
  Cpu(s):  1.3%us,  0.7%sy, 97.3%ni,  0.0%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
  Mem:    896172k total,   448328k used,   447844k free,    29160k buffers
  Swap:   393584k total,        0k used,   393584k free,   223420k cached
  

    PID   USER      PR  NI  VIRT   RES  SHR   S  %CPU %MEM    TIME+      COMMAND                                                          
   3238 mbdb      26   6  5080 1676 1024     R   98.2      0.2    30:18.74      oggenc                                                           
   1355 root        20   0   381m  27m   9m    R   1.7       3.2     41:03.60     Xorg                                                             
   
```First line explains it. So even after I closed Rubyripper its still hogging the CPU. 
Also another strange thing going on. I set Rubyripper to rip to Vorbis. The resultant .ogg file is empty and a second .wav file is generated.

Anyone ideas how to proceed with this?
Thanks

---

### Post by Midnighter on 2010-05-14
You using Lucid (10.04), or another release? Not used Rubyripper, so unsure what to suggest. I always use Asunder, small and light, and easy to use. Never had the issue you describe. Sorry not more help.

---

### Post by oxf on 2010-05-14
> **Midnighter said:**
> You using Lucid (10.04), or another release? Not used Rubyripper, so unsure what to suggest. I always use Asunder, small and light, and easy to use. Never had the issue you describe. Sorry not more help.

No I'm using Karmic. However, I suspect whatever is making the CPU run full blast long after the app is closed is not necessarily linked to Rubyripper. Could be wrong though.
Interesting that when I rip to MP3 this doesn't happen.
Anyone have any thought how I track this down?

---

### Post by oxf on 2010-05-14
Well I've just done extensive tests on this and can confirm that ripping to MP3 is fine.
Ripping to Vorbis sets the CPU running at 99% until I reboot the machine and outputs the error files as described above, ie. 0 bytes in the .ogg file and generates a .wav file (corrupted)

---

### Post by oxf on 2010-05-16
Bump Help!!!

---

### Post by mc4man on 2010-05-16
Don't see any issue's with rr and vorbis (oggenc) on various ubuntu releases

If it is rr related - what version of rr are you using, and where did you get it from? 
(or are you running rr directly from source folder?

What are the encoder parameters for vorbis (should be just -q [COLOR="RoyalBlue"]X[/COLOR]
Have you tried deleting ~/.rubyripper and starting w/ fresh settings

Does oggenc work by itself?
(rip a couple of .wavs - put into a folder, cd to it and run 
oggenc -q [COLOR="RoyalBlue"]5[/COLOR] *.wav

---

