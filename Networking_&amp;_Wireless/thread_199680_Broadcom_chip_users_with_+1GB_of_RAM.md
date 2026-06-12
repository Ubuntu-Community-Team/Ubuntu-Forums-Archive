---
title: "Broadcom chip users with +1GB of RAM"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by hardhu on 2006-06-19
Hello,
I would like to know at which point is in Ubuntu the solution of the bug reported here:
[http://www.ubuntuforums.org/showthread.php?t=157582&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=157582&highlight=broadcom)
I am using dapper amd64 with kernel 2.6.15-25-amd64-k8 and i have tried the workaround suggested in last post of that thread, that is 'sudo modprobe bcm43xx pio=1', but I still get this error when i try to bring the interface up:
SIOCSIFFLAGS: Cannot allocate memory

Is there any progress, have we to wait for 2.6.16 kernel, or something else?

---

### Post by pksings on 2006-06-20
Your problem is that you are missing the firmware that it needs to initialize. I fixed this by finding and providing the necessary firmware. 
That still didn't work for me, my system froze when I tried to use it. I would up blacklisting bcm43xx and using ndiswrapper and the windows driver.

PK

---

### Post by hardhu on 2006-06-21
[QUOTE=pksings]Your problem is that you are missing the firmware that it needs to initialize. I fixed this by finding and providing the necessary firmware. 
That still didn't work for me, my system froze when I tried to use it. I would up blacklisting bcm43xx and using ndiswrapper and the windows driver.

PK[/QUOTE]

No I am not missing it: I have successfully extracted it with fwcutter from windows driver and copied it in /lib/firmware:

drwxr-xr-x 3 root root  1768 2006-05-20 10:25 2.6.15-21-amd64-generic
drwxr-xr-x 3 root root  1768 2006-05-24 18:06 2.6.15-23-amd64-generic
drwxr-xr-x 3 root root  1768 2006-05-29 14:00 2.6.15-23-amd64-k8
drwxr-xr-x 3 root root  1768 2006-06-16 13:14 2.6.15-25-amd64-generic
drwxr-xr-x 2 root root  2328 2006-06-19 12:04 2.6.15-25-amd64-k8
-rw-r--r-- 1 root root  3504 2006-05-26 16:51 bcm43xx_initval01.fw
-rw-r--r-- 1 root root    16 2006-05-26 16:51 bcm43xx_initval02.fw
-rw-r--r-- 1 root root  3504 2006-05-26 16:51 bcm43xx_initval03.fw
-rw-r--r-- 1 root root    16 2006-05-26 16:51 bcm43xx_initval04.fw
-rw-r--r-- 1 root root  2536 2006-05-26 16:51 bcm43xx_initval05.fw
-rw-r--r-- 1 root root   248 2006-05-26 16:51 bcm43xx_initval06.fw
-rw-r--r-- 1 root root  2536 2006-05-26 16:51 bcm43xx_initval07.fw
-rw-r--r-- 1 root root  2536 2006-05-26 16:51 bcm43xx_initval08.fw
-rw-r--r-- 1 root root   248 2006-05-26 16:51 bcm43xx_initval09.fw
-rw-r--r-- 1 root root   248 2006-05-26 16:51 bcm43xx_initval10.fw
-rw-r--r-- 1 root root 16216 2006-05-26 16:51 bcm43xx_microcode2.fw
-rw-r--r-- 1 root root 19960 2006-05-26 16:51 bcm43xx_microcode4.fw
-rw-r--r-- 1 root root 22520 2006-05-26 16:51 bcm43xx_microcode5.fw
-rw-r--r-- 1 root root  1312 2006-05-26 16:51 bcm43xx_pcm4.fw
-rw-r--r-- 1 root root  1312 2006-05-26 16:51 bcm43xx_pcm5.fw

---

