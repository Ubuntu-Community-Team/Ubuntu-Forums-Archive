---
title: "Am I getting reasonable performance from my ATI card?"
date: 2006-02-14
forum: Multimedia &amp; Video
---

### Post by gremlin hunter on 2006-02-14
I think I am getting low perfromance from my Radeon 9250.

george@george:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1050 (X4.3.0-8.22.5)

george@george:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
407 frames in 5.0 seconds = 81.400 FPS
436 frames in 5.0 seconds = 87.200 FPS
433 frames in 5.0 seconds = 86.600 FPS
444 frames in 5.0 seconds = 88.800 FPS
429 frames in 5.0 seconds = 85.800 FPS

george@george:~$ fgl_glxgears -fbo
Using GL_EXT_framebuffer_object
798 frames in 5.0 seconds = 159.600 FPS
841 frames in 5.0 seconds = 168.200 FPS
870 frames in 5.0 seconds = 174.000 FPS
837 frames in 5.0 seconds = 167.400 FPS

(is it meant to be in black and white?)

glxgears -printfps
3720 frames in 5.0 seconds = 743.312 FPS
3766 frames in 5.0 seconds = 753.153 FPS
3748 frames in 5.0 seconds = 749.588 FPS
3423 frames in 5.0 seconds = 684.411 FPS

The odd thing is is that it looks like it is going really slow. Or is it going so fast that it looks slow?

In darwinia I struggle to get 20 fps with medium detail and 1024x768.

---

### Post by alfonz on 2006-02-14
Those numbers seem ok for a 92XX series card, but someone else might say otherwise that have that card, I have the 9600Xt and get higher numbers


what version of fglrx drives do you have installed?

---

### Post by gremlin hunter on 2006-02-14
I forgot to mention the reason I thought about it. My brother has some i810 class chip which is running with shared memory of 8mb but he gets around 500fps on a 700mhz machine. I just thought my card Should *atleast* double his numbers.

---

### Post by Pancetilla on 2006-02-14
I'm getting 400 FPS with fgl_glxgears with 8.21 and 9600 XT. I'll try 8.22 tonight.

---

### Post by ubu_dynamite on 2006-02-14
dynamite@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 TX Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

dynamite@ubuntu:~$ fgl_glxgears
2166 frames in 5.0 seconds = 433.200 FPS
2448 frames in 5.0 seconds = 489.600 FPS
2443 frames in 5.0 seconds = 488.600 FPS
2459 frames in 5.0 seconds = 491.800 FPS
2439 frames in 5.0 seconds = 487.800 FPS
2451 frames in 5.0 seconds = 490.200 FPS
2453 frames in 5.0 seconds = 490.600 FPS

dynamite@ubuntu:~$ glxgears -printfps
12109 frames in 5.0 seconds = 2421.694 FPS
12072 frames in 5.0 seconds = 2414.379 FPS
12072 frames in 5.0 seconds = 2414.356 FPS
12071 frames in 5.0 seconds = 2414.001 FPS
12074 frames in 5.0 seconds = 2414.608 FPS
12073 frames in 5.0 seconds = 2414.447 FPS

xorg-driver-fglrx 6.8.0-8.16.20-0ubuntu16.1

---

### Post by Disastorm on 2006-02-15
I dont have radeon 9250, but on my laptop with a Radeon XPress 200m, I get 900 fps on glxgears -printfps

---

### Post by slashem on 2006-02-16
root@box:~# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

root@box:~# fgl_glxgears
1280 frames in 5.0 seconds = 256.000 FPS
1690 frames in 5.0 seconds = 338.000 FPS
1696 frames in 5.0 seconds = 339.200 FPS

root@box:~# glxgears -printfps
9462 frames in 5.0 seconds = 1890.338 FPS
9740 frames in 5.0 seconds = 1943.877 FPS
9590 frames in 5.0 seconds = 1917.982 FPS

---

### Post by number nine on 2006-03-23
Here's my performance from an X700. It seems lower than it should be compared to all the Radeon 9xxx reports above:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

$ fgl_glxgears
2761 frames in 5.0 seconds = 552.200 FPS
2937 frames in 5.0 seconds = 587.400 FPS
2885 frames in 5.0 seconds = 577.000 FPS
3658 frames in 5.0 seconds = 731.600 FPS
3990 frames in 5.0 seconds = 798.000 FPS
4097 frames in 5.0 seconds = 819.400 FPS
3896 frames in 5.0 seconds = 779.200 FPS

$ glxgears -printfps
12708 frames in 5.0 seconds = 2528.338 FPS
12385 frames in 5.0 seconds = 2476.842 FPS
14294 frames in 5.0 seconds = 2858.749 FPS
13838 frames in 5.0 seconds = 2767.431 FPS

---

