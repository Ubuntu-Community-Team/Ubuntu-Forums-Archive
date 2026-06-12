---
title: "3d acceleration"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by pau on 2006-08-08
Hi, I have followed the instructions given in

[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

and it doesn't work:


```
andromina| fglrxinfo 
display: :0.0 screen: 0 OpenGL vendor string: Mesa project: www.mesa3d.org OpenGL renderer string: Mesa GLX Indirect OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```



Also,


```

glxgears -iacknowledgethatthistoolisnotabenchmark
```


yields



```
576 frames in 6.1 seconds = 94.074 FPS 308 frames in 5.1 seconds = 60.870 FPS 398 frames in 6.9 seconds = 57.511 FPS 397 frames in 7.1 seconds = 56.268 FPS 398 frames in 6.7 seconds = 59.458 FPS 397 frames in 6.8 seconds = 58.275 FPS
```


and everytime I reboot I see a process consuming up to 90% of the cpu,

```
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND 
4576 root 25 0 2612 552 444 R 97.1 0.1 4:53.07 atieventsd 
```

related to ATI...

Also,


```
andromina| dmesg | grep fglrx 
[4294718.184000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel. [4294718.186000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes. [4294718.186000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0 [4294719.698000] [fglrx:firegl_unlock] *ERROR* Process 4512 using kernel context 0
```


I think that something went wrong, but I cannot tell what... any hint??

The card is an ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

---

### Post by JerMe on 2006-08-08
Did you follow the first part, or the second part?  (i.e., did you apt-get install xorg-driver-fglrx, or did you compile it yourself?)

I have an AIW 9600.  I used the first method (apt-get install xorg-driver-fglrx).

---

