---
title: "Ati 8.25.18 powerstate now works!!"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by zasf on 2006-06-02
```
matteo@burnt:~$ sudo aticonfig --lsp
Password:
    core/mem      [flags]
-----------------
  1: 105/149 MHz  [low voltage]
  2: 209/182 MHz  [low voltage]
* 3: 351/284 MHz  [default state]
matteo@burnt:~$ sudo aticonfig --set-powerstate 1
Warning : Option 'PowerState' is exclusive, other options will be ignored.
matteo@burnt:~$ sudo aticonfig --lsp
    core/mem      [flags]
-----------------
* 1: 105/149 MHz  [low voltage]
  2: 209/182 MHz  [low voltage]
  3: 351/284 MHz  [default state]
matteo@burnt:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1147 frames in 5.0 seconds = 229.400 FPS
1422 frames in 5.0 seconds = 284.400 FPS
matteo@burnt:~$ sudo aticonfig --set-powerstate 3
Warning : Option 'PowerState' is exclusive, other options will be ignored.
matteo@burnt:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
3033 frames in 5.0 seconds = 606.600 FPS
3125 frames in 5.0 seconds = 625.000 FPS
3069 frames in 5.0 seconds = 613.800 FPS
matteo@burnt:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

---

### Post by barney_1 on 2006-06-02
Congratulations, what method of installation did you use for the new drivers?  I've been unable to accomplish the same with my r9800.

---

### Post by shuaiant on 2006-06-02
what method of installation did you use for the new drivers?

---

### Post by zasf on 2006-06-02
fresh dapper install and 

```
sudp apt-get update
$ sudo apt-get install xorg-driver-fglrx
$ sudo dpkg-reconfigure xserver-xorg

```

---

### Post by jecos on 2006-06-02
**Powerstates are available mobility cards only.**

---

