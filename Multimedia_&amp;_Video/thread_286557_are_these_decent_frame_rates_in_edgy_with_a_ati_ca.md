---
title: "are these decent frame rates in edgy with a ati card"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by lime4x4 on 2006-10-27
computer is a P4 2.6 ht chip with a gig of memory

john@john-ubuntu:~$ glxgears -printfps
1085 frames in 5.0 seconds = 216.900 FPS
1186 frames in 5.0 seconds = 237.185 FPS
1193 frames in 5.0 seconds = 238.392 FPS
1189 frames in 5.0 seconds = 237.791 FPS
1184 frames in 5.0 seconds = 236.786 FPS
1176 frames in 5.0 seconds = 235.188 FPS
john@john-ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
929 frames in 5.0 seconds = 185.800 FPS
785 frames in 5.0 seconds = 157.000 FPS
963 frames in 5.0 seconds = 192.600 FPS
978 frames in 5.0 seconds = 195.600 FPS
972 frames in 5.0 seconds = 194.400 FPS
980 frames in 5.0 seconds = 196.000 FPS
973 frames in 5.0 seconds = 194.600 FPS
john@john-ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.6011 (8.28.8)

---

### Post by didobuntu on 2006-10-27
+1 

same for me .. I have an ATI X1600 Mobility ..
normally I have higher scores ... 

this is very stange

---

### Post by RudolfMDLT on 2006-10-28
Same problem here. I ran 2000 fps in dapper, now down to 250....:-k

---

### Post by nbound on 2006-10-28
Im getting 580fps with a crappy 32MB shared mem ATI 200M... you should probably be getting getter than that!

---

### Post by lime4x4 on 2006-10-29
even installing the new ati drivers didn't help much

---

### Post by meng on 2006-10-29
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)
Don't fall into the trap of reading anything into those fps numbers. Instead, you'd be better off running a game and going with your subjective impression.

---

### Post by halitech on 2006-10-29
When I was in Dapper I was getting 80-100fps with my Radeon 7200 (64meg version with tv out) using MESA drivers. Comp is a Duron 1.3 with 256 Meg RAM. After upgrading to Edgy, I'm now geting this using stock drivers:

daryl@ubuntu:/storage/movies$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
1631 frames in 5.0 seconds = 325.653 FPS
1238 frames in 5.0 seconds = 247.271 FPS
1282 frames in 5.0 seconds = 256.265 FPS
1255 frames in 5.0 seconds = 250.784 FPS
1235 frames in 5.0 seconds = 246.410 FPS
1267 frames in 5.0 seconds = 253.274 FPS
1208 frames in 5.0 seconds = 241.473 FPS
daryl@ubuntu:/storage/movies$

---

### Post by didobuntu on 2006-10-29
+1

same problem for me. I have an ATI Mobility Radeon X1600 with 256 Mb. Under Drapper and Breezy I had about 4500 fps ... Now since Edgy I have the following:

glxgears -printfps
1219 frames in 5.0 seconds = 243.793 FPS
1251 frames in 5.0 seconds = 250.004 FPS
1250 frames in 5.0 seconds = 249.802 FPS
1251 frames in 5.0 seconds = 250.001 FPS
1244 frames in 5.0 seconds = 248.603 FPS
1239 frames in 5.0 seconds = 247.751 FPS

But under the 3D fps test, the fgl_glxgears, things are as before:

fgl_glxgears 
Using GLX_SGIX_pbuffer
3277 frames in 5.0 seconds = 655.400 FPS
3872 frames in 5.0 seconds = 774.400 FPS
3885 frames in 5.0 seconds = 777.000 FPS
3885 frames in 5.0 seconds = 777.000 FPS
3876 frames in 5.0 seconds = 775.200 FPS
3877 frames in 5.0 seconds = 775.400 FPS
3778 frames in 5.0 seconds = 755.600 FPS
3815 frames in 5.0 seconds = 763.000 FPS

with higher scores than the 2D glxgears.

I can agree that glxgears is not a benchmark test at all ... but, however, it is the same program running for the same graphic card product under different driver versions of the fglrx driver. The problem comes certainly from the fglrx 8.28.8

---

