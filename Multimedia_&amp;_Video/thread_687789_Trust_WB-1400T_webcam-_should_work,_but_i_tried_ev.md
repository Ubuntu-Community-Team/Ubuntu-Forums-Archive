---
title: "Trust WB-1400T webcam- should work, but i tried everything and it doesn't"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by savethewabbit on 2008-02-04
hello, 
i'm trying to install my new trust wb-1400t webcam. i read on the spca5xx website that it was supported, and that's why i bought it.

first of all, i'm running gutsy gibbon. 

when i type lsusb the webcam is found
```
Bus 002 Device 002: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam
```

typing ls -l /dev/vid* this is what shows up when the webcam is plugged in:
```

lrwxrwxrwx 1 root root     11 2008-02-04 22:07 /dev/video -> /dev/video0
crw-rw---- 1 root video 81, 0 2008-02-04 22:46 /dev/video0
crw-r--r-- 1 root root  81, 1 2008-02-04 22:24 /dev/video1

```

and this is what it shows when the cam is unplugged :
```

lrwxrwxrwx 1 root root    11 2008-02-04 22:07 /dev/video -> /dev/video0
crw-r--r-- 1 root root 81, 1 2008-02-04 22:24 /dev/video1

```
then i suppose the webcam is /dev/video0.

so i tried downloading the spca5xx tar gz, tried to install it (with make and make install) but when i tried to load the module, it said it didn't exist. 
so i tried with easycam. installed it fine, but when i start it and select my webcam from the list, it says : 
<i>This software, EasyCam, is still in test status.  If your webcam is not detected, it may be not compatible with autodetection yet.  Thank you to read the file easycam generated on your desktop.</i> 
and the file on my desktop only contains ways to contact the easycam creator.
in fact, my webcam is not on the 'automated webcam installation' list, but i thought it would work nonetheless.

i've also tried installing easycam2 - 
when i start it and try to install the drivers an error window comes up saying
<i>l'installation a échouer
erreur lors de la commande make install </i>

i don't speak french, but that doesn't seem good.

so, i think i've followed every possible how-to and my camera is indeed recognized by my  system. what do i do now? if i try to open 'camorama webcam viewer' it says
<i>
Could not connect to video device (/dev/video0).
Please check connection. </i>

i've also read on the answers.launchpad.net website that a guy had it work by simply replacing the gspca.ko file in the /lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1 directory with the one that the gspca itself made up. i tried to copy-paste the gspca.ko file from the gspcav1-20071224 folder on my desktop (from which i tried to install the spca5xx the first time around) but found out that apparently i don't have the permission to write in the /lib/modules/2.6etc folder - which is weird as i'm the administrator.
so if first of all i could get a way to copy-paste that file and see if it works, i'd be grateful.

i'm really disappointed because i thought it would work easily. i hope you guys can help me figure out what i'm doing wrong.
thanks!

---

### Post by _xray7224 on 2008-03-12
to edit documents you need root permission not administrator, root acts as a super administrator. i would suggest going to terminal and type something like this:

```
sudo gedit /lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/file-name-you-wish-to edit
```

then it will open gedit as a root and you should be able to copy things in, by the way im still searching for a way to get the trust WB-1400T webcam to work on my ubuntu gutsy gibbon

---

### Post by ffion on 2008-07-05
i have a trust wb-1400t webcam and do not have the installation disc that was with it when i bought it.
could you please assist me with how i can get my webcam to work on my laptop without the disc 
                                  thank you

---

