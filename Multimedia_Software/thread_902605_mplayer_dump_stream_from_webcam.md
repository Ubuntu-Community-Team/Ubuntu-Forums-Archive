---
title: "mplayer dump stream from webcam"
date: 2008-08-27
forum: Multimedia Software
---

### Post by josvanr on 2008-08-27
hi

with mplayer one can view the webcam stream:
```

mplayer -tv driver=v4l2:gain=1:width=640:height=480:device=/dev/video1:fps=30:outfmt=yuy2 tv://
```

Now when i try to save the stream:

```
mplayer -tv driver=v4l2:gain=1:width=640:height=480:device=/dev/video1:fps=30:outfmt=yuy2 tv:// -dumpstream -dumpfile x.avi  

```
this doesnt work. (see below) 

Anyone have suggestions to make this work?


josvanr


__________________________________

```

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
Core dumped ;)

Exiting... (End of file)
```

---

### Post by www.rzr.online.fr on 2009-01-12
> **josvanr said:**
> 


Playing tv://.
Core dumped ;)

Exiting... (End of file)[/CODE]


I had the same issue, maybe vlc does the job 
-- 
[http://rzr.online.fr/q/webcam](http://rzr.online.fr/q/webcam)

---

### Post by andrew.46 on 2009-01-12
Hi josvanr,

> **josvanr said:**
> Now when i try to save the stream:

```
mplayer -tv driver=v4l2:gain=1:width=640:height=480:device=/dev/video1:fps=30:outfmt=yuy2 tv:// -dumpstream -dumpfile x.avi  

```
this doesnt work. (see below) 

```

[...]
Playing tv://.
**[COLOR="Red"]Core dumped ;)[/COLOR]**

Exiting... (End of file)
```

Note the smiley, this is a 'feature' which annoys many people: the 'Core' has not really been 'dumped' and this represents a little MPlayer joke. Are you sure that MPlayer has not created a file called x.avi in the directory from which you called MPlayer?

If not try your Mplayer command again and this time add the -v option so you can see what is going on.

Andrew

---

### Post by josvanr on 2011-06-18
hi 

it has been some time. but maybe you are still here...


yes, there is an avi.x, but mplayer exits after 0.x seconds
and then it cant open it...

the output of -v: maybe you can make something of it:

jos@samsungsucks:~$ mplayer -tv driver=v4l2:gain=1:width=640:height=480:device=/dev/video1:fps=30:outfmt=yuy2 tv:// -dumpstream -dumpfile x.avi -v                                                                                                                                   
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team                                                                                                                                                                                                                                      
CPU vendor name: GenuineIntel  max cpuid level: 11                                                                                                                                                                                                                                   
CPU: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz (Family: 6, Model: 37, Stepping: 5)                                                                                                                                                                                             
extended cpuid-level: 8                                                                                                                                                                                                                                                              
extended cache-info: 16801856                                                                                                                                                                                                                                                        
Detected cache-line size is 64 bytes                                                                                                                                                                                                                                                 
Testing OS support for SSE... yes.                                                                                                                                                                                                                                                   
Tests of OS support for SSE passed.                                                                                                                                                                                                                                                  
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1                                                                                                                                                                                                               
Compiled with runtime CPU detection.                                                                                                                                                                                                                                                 
get_path('codecs.conf') -> '/home/jos/.mplayer/codecs.conf'                                                                                                                                                                                                                          
Reading /home/jos/.mplayer/codecs.conf: Can't open '/home/jos/.mplayer/codecs.conf': No such file or directory                                                                                                                                                                       
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory                                                                                                                                                                                   
Using built-in default codecs.conf.                                                                                                                                                                                                                                                  
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --disable-arts --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --enable-joystick --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui                                                                                                                 
CommandLine: '-tv' 'driver=v4l2:gain=1:width=640:height=480:device=/dev/video1:fps=30:outfmt=yuy2' 'tv://' '-dumpstream' '-dumpfile' 'x.avi' '-v'                                                                                                                                    
init_freetype                                                                                                                                                                                                                                                                        
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay                                                                                                                                                                                                                             
get_path('fonts') -> '/home/jos/.mplayer/fonts'                                                                                                                                                                                                                                      
Using nanosleep() timing                                                                                                                                                                                                                                                             
get_path('input.conf') -> '/home/jos/.mplayer/input.conf'                                                                                                                                                                                                                            
Can't open input config file /home/jos/.mplayer/input.conf: No such file or directory                                                                                                                                                                                                
Parsing input config file /etc/mplayer/input.conf                                                                                                                                                                                                                                    
Input config file /etc/mplayer/input.conf parsed: 91 binds                                                                                                                                                                                                                           
Setting up LIRC support...                                                                                                                                                                                                                                                           
mplayer: could not connect to socket                                                                                                                                                                                                                                                 
mplayer: No such file or directory                                                                                                                                                                                                                                                   
Failed to open LIRC support. You will not be able to use your remote control.                                                                                                                                                                                                        
get_path('.conf') -> '/home/jos/.mplayer/.conf'                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                                                                     
Playing tv://.                                                                                                                                                                                                                                                                       
get_path('sub/') -> '/home/jos/.mplayer/sub/'                                                                                                                                                                                                                                        
STREAM: [tv] tv://                                                                                                                                                                                                                                                                   
STREAM: Description: TV Input                                                                                                                                                                                                                                                        
STREAM: Author: Benjamin Zores, Albeu                                                                                                                                                                                                                                                
STREAM: Comment:                                                                                                                                                                                                                                                                     
Core dumped ;)                                                                                                                                                                                                                                                                       
vo: x11 uninit called but X11 not initialized..                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                                                                     
Exiting... (End of file)                                                                                                                                                                                                                                                             



> **andrew.46 said:**
> Hi josvanr,



Note the smiley, this is a 'feature' which annoys many people: the 'Core' has not really been 'dumped' and this represents a little MPlayer joke. Are you sure that MPlayer has not created a file called x.avi in the directory from which you called MPlayer?

If not try your Mplayer command again and this time add the -v option so you can see what is going on.

Andrew

---

