---
title: "Data stream from Wacom Bamboo tablet"
date: 2010-06-06
forum: Multimedia Software
---

### Post by MichaelBen on 2010-06-06
Hi 
I have recently purchased a Wacom Bamboo Pen & Touch tablet and have got it working with Ubuntu 9.10 (Karmic) by following this post: [http://ubuntuforums.org/showpost.php?p=8283168&postcount=1](http://ubuntuforums.org/showpost.php?p=8283168&postcount=1). 
 
I am now trying to trap the actual data coming from the bamboo as I write with the pen and found some threads suggesting that if I do an xxd one of /dev/ttyS[0-4] I should be able to see output. However when I do a "sudo xxd /dev/ttyS0" the xxd command finishes straight away.
 
If I run the command "xxd /dev/input/mouse1" I can the data coming from the mouse movement so I am expecting to be able to see the same sort of thing coming from the wacom bamboo pen. Both the bamboo and the mouse are USB connected.
 
Does anyone know if the stream of data coming form the wacom bamboo should go to /dev/ttyS[0-4] or should I be looking elsewhere?
 
Thanks

---

### Post by Favux on 2010-06-06
Hi MichaelBen,

Welcome to Ubuntu forums!

The Wacom Bamboo Pen & Touch is a usb device so it won't be present on serial ports like /dev/ttyS[0-4].

You could use xidump followed by the device you want to look at:
```
xidump stylus
```
Or you could figure out the event it is on and do:
```
sudo hexdump /dev/input/event6
```

I'm not sure what data you're looking for.  If you search the thread you linked to and the first P & T  thread:  [http://ubuntuforums.org/showthread.php?t=1290251](http://ubuntuforums.org/showthread.php?t=1290251)  you'll find more ways to extract the data with debug etc.  Ayuthia's first patches on the first thread were mainly to pull data from the kernel into Xorg.0.log in /var/log, for example [wcm2_patch]("http://ubuntuforums.org/showpost.php?p=8137912&postcount=188").  But it's not available anymore except maybe from Ayuthia.  So you could ask Ayuthia for help if you have something specific in mind.

Hope this helps.

---

### Post by MichaelBen on 2010-06-09
[FONT=Calibri][SIZE=3]Hi Favux, thank you for helping me out. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]You have got me on the right track. I was begining to loose heart with all things Wacom and Ubuntu. My reason for asking the question is that I am doing some research into on-line signature verification and I need to be able to get at the x-axis, y-axis and pressure measurements and thanks to you I can get the information that I require from the xidump command.[/SIZE][/FONT]
```

[FONT=Calibri][SIZE=3]xidump -u raw "Wacom BambooFun 2FG 4x5 Pen" [/SIZE][/FONT]

```
```

[SIZE=3][FONT=Calibri]2.72430506: Proximity In[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]2.72446706: Motion: x= +7456 y= +4472 p=   0 tx=  +0 ty=  +0 w=   +0 [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]2.73985406: Motion: x= +7463 y= +4473 p=   0 tx=  +0 ty=  +0 w=   +0 [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]2.75037206: Motion: x= +7469 y= +4474 p=   0 tx=  +0 ty=  +0 w=   +0 [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]2.75192006: Motion: x= +7476 y= +4475 p=   0 tx=  +0 ty=  +0 w=   +0[/FONT][/SIZE]

```
 
[FONT=Calibri][SIZE=3]I got the name of my input device using xsetwacom list[/SIZE][/FONT]
```

[FONT=Calibri][SIZE=3]xsetwacom list[/SIZE][/FONT]

```
```

[FONT=Calibri][SIZE=3]Wacom_BambooFun_2FG_4x5_Pen     stylus[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Wacom_BambooFun_2FG_4x5_Finger     stylus[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Wacom_BambooFun_2FG_4x5_Finger_touch     touch[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Wacom_BambooFun_2FG_4x5_Finger_pad     pad[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Wacom_BambooFun_2FG_4x5_Pen_eraser     eraser[/FONT][/SIZE]

```
[FONT=Calibri][SIZE=3]I now have what I need however I did notice a few things I could not explain while doing my troubleshooting. I found thread [/SIZE][/FONT][[FONT=Calibri][SIZE=3][COLOR=#800080]http://old.nabble.com/Bamboo-Fun-multi-touch-td28236711.html[/COLOR][/SIZE][/FONT]]("http://old.nabble.com/Bamboo-Fun-multi-touch-td28236711.html")[FONT=Calibri][SIZE=3] helpful (Favux, you are participating in that thread). [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Just for the record I will list my observations here. I am using my tablet in plug and play mode so use the [/SIZE][/FONT][COLOR=black][FONT=Courier New]/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi[/FONT][/COLOR][SIZE=3][FONT=Calibri] configuration file instead of the xorg.conf file. [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I notice that if I rename 10-linuxwacom.fdi to 10-linuxwacom.fdi.sav and reboot then my tablet and pen still work and can interact with gimp 2.6. However xsetwacom only lists 2 devices instead of the 5 that it did previously. I expected no devices to be listed because there is no 10-linuxwacom.fdi or xorg.conf file available. [/FONT][/SIZE]
```

[FONT=Calibri][SIZE=3]xsetwacom list[/SIZE][/FONT]

```
```

[FONT=Calibri][SIZE=3]Wacom_BambooFun_2FG_4x5_Pen     stylus[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Wacom_BambooFun_2FG_4x5_Finger     stylus[/FONT][/SIZE]

```
 
[FONT=Calibri][SIZE=3]The wacomcpl command does not start.[/SIZE][/FONT]
 
[SIZE=3][FONT=Calibri]Once that test was done I put my 10-linuxwacom.fdi file back in place and plugged out the tablet and plugged it back in again. The xsetwacom command lists the 5 devices as before.[/FONT][/SIZE]
```

[FONT=Calibri][SIZE=3]xsetwacom list[/SIZE][/FONT]

```
```

[FONT=Calibri][SIZE=3]Wacom_BambooFun_2FG_4x5_Pen     stylus[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Wacom_BambooFun_2FG_4x5_Finger     stylus[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Wacom_BambooFun_2FG_4x5_Finger_touch     touch[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Wacom_BambooFun_2FG_4x5_Finger_pad     pad[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Wacom_BambooFun_2FG_4x5_Pen_eraser     eraser[/FONT][/SIZE]

```
[FONT=Calibri][SIZE=3]The wacomcpl comand now works and produces the Wacom Control Panel[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I could not get xxd to produce any output when it is used against the 2 wacom event character files in /dev/input[/SIZE][/FONT]
```

[FONT=Calibri][SIZE=3]ls –lrt /dev/input/[/SIZE][/FONT]

```
```

[FONT=Calibri][SIZE=3]lrwxrwxrwx 1 root root      7 2010-06-09 18:38 wacom-touch -> event10[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]lrwxrwxrwx 1 root root      7 2010-06-09 18:38 tablet-wacom-bamboo-pen_touch-touch -> event10[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]crw-r----- 1 root root 13, 74 2010-06-09 18:38 event10[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]lrwxrwxrwx 1 root root      6 2010-06-09 18:38 wacom -> event8[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]lrwxrwxrwx 1 root root      6 2010-06-09 18:38 tablet-wacom-bamboo-pen_touch-stylus -> event8[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]crw-r----- 1 root root 13, 72 2010-06-09 18:38 event8[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]crw-r----- 1 root root 13, 34 2010-06-09 18:38 mouse2[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]crw-r----- 1 root root 13, 75 2010-06-09 18:38 event11[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]drwxr-xr-x 2 root root    160 2010-06-09 18:38 by-id[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]crw-r----- 1 root root 13, 36 2010-06-09 18:38 mouse4[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]crw-r----- 1 root root 13, 76 2010-06-09 18:38 event12[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]drwxr-xr-x 2 root root    220 2010-06-09 18:38 by-path[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]crw-r----- 1 root root 13, 77 2010-06-09 18:38 event13[/FONT][/SIZE]

```
[FONT=Calibri][SIZE=3]From what I can see the wacom links point at event8 and event10 and running the xxd against either of them produces nothing when I use the wacom pen and tablet. Again while carrying out this test I am able to use the pen to interact with gimp 2.6.[/SIZE][/FONT]
 
```

[FONT=Calibri][SIZE=3]sudo xxd event8[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]^C[/FONT][/SIZE]

```
[FONT=Calibri][SIZE=3]The wacdump command also fails everytime with “segmentation fault” when I run it for event8 and event10. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Anyway, I can get the data I am looking for using the xidump command so I am happy with what I have and can proceed with my project. [/SIZE][/FONT]

[FONT=Calibri][SIZE=3]Thanks[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]MichaelBen[/SIZE][/FONT]

---

### Post by Favux on 2010-06-09
Hi Michael,

Thanks for the update.  Glad xidump is giving you what you need.  The wacdump command won't work when X is running because the X driver wacom_drv.so is grabbing the input.  So you'd need to stop X to use it.

---

