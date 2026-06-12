---
title: "do i have direct rendering or not ?"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by yyagol on 2006-09-10
hi
i am using a ATI Radeon 9200SE
my problem is not installing the ATI modules but knowing that
i got 3D . i install it also on my CetOS machine and got the same FPS :
```

[root@localhost ~]# fgl_glxgears 
Using GLX_SGIX_pbuffer
635 frames in 5.0 seconds = 127.000 FPS
509 frames in 5.0 seconds = 101.800 FPS
496 frames in 5.0 seconds = 99.200 FPS
507 frames in 5.0 seconds = 101.400 FPS

```
so i check to see that direct rendering is on :
```

[root@localhost ~]# glxinfo |grep direct
direct rendering: Yes

```
now i try to see what glx have to say , and then it hit me . take a look :
```

[root@localhost ~]# glxgears 
5745 frames in 5.0 seconds = 1149.000 FPS
5814 frames in 5.0 seconds = 1162.800 FPS
5814 frames in 5.0 seconds = 1162.800 FPS
5814 frames in 5.0 seconds = 1162.800 FPS

```
[SIZE="4"]so now do i or do i not have 3D ?[/SIZE]:-k 


.

---

### Post by tseliot on 2006-09-10
yes, you do.

---

### Post by yyagol on 2006-09-10
Thanks

---

