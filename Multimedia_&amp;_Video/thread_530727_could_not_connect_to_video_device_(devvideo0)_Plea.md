---
title: "could not connect to video device (/dev/video0) Please check connection.."
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by xarroyo on 2007-08-20
I have the following webcam
i got this by typing on the konsole: lsusb

ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam. How can i make it work on ubuntu fiesty fawn??

from what i have read i t is necessary to download the spca5xx-source.. i did it with the Synaptics Package Manager.. i have also download the gspca... then i downloaded the camorama to test the webcam.. and when i ran the program i recieve the following messege: 
could not connect to video device (/dev/video0)
Please check connection..

 i have my webcam plugged... if i go to /dev i dont have the folder video0... 
if you type this on the konsole 

ls -la /dev/video0  

i get the following message crw-rw---- 1 root video 81, 0 2007-08-20 17:20 /dev/video0

i read from a website in spanish that says that i have to add my user in a group that is allow to have the webcam.. i tried it by doing the:

sudo adduser nickUser video

i did that but i dont have anyresults.. so.. what else do i need to do!!!?????

---

### Post by Lord Illidan on 2007-08-29
Can you give us more details about the type of camera, and where is it? Is it in a laptop? Sony Vaio?

---

### Post by Lord Illidan on 2007-08-29
According to [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html), your webcam seems to be unsupported atm...I couldn't find it on the list. Did you find your instructions on a specific website?

There is little I can do for you here, besides.

---

### Post by xarroyo on 2007-08-29
Here's the link of the webcam i use: [http://www.tripplite.com/products/product.cfm?ProductID=3173](http://www.tripplite.com/products/product.cfm?ProductID=3173)
Is a tripplite Notebook Clip-on Camara!

Isn't this my webcam model??

Vimicro 	176 	0x0ac8 	0x303b 	Generic 		Zc0301p 	PB330 	Yes 	jpeg 	spca5xx/LE gspca v4l1/v4l2

Thanks for your help!

---

### Post by xarroyo on 2007-08-30
This site i found it useful
[http://mmejiav.wordpress.com/2007/06/07/modulo-gspca/](http://mmejiav.wordpress.com/2007/06/07/modulo-gspca/)

it is in spanish, and he is installing the webcam in Debian Etch, but it doesn't matter.. the steps are the same..

i use sudo nautilus to place the gspcav1-20070508.tar.gz on the /usr/src/modules and the i extracted the file with the right click and selecting extract here!

finally where says:
./configure i placed sudo ./gspca_build and followed the other steps..

now it works!! i tested it on Kopete and also aMsn!!

---

### Post by xarroyo on 2007-09-03
It worked.. but few days later i wanted to use the webcam.. and now it seems it is not recognized.. if i open the camorama sends the same message!! 
i did the sames steps to restore the settings, but now nothing happens!! is it possible that with the restart the settings that i did the first time are erased everytime i restart the machine??

now my camara is not recognized... please, help!!

---

### Post by spupy on 2007-09-03
Hi xarroyo. lsusb says i have exactly the same camera, but mine is branded as A4Tech :confused:
I am on Debian, but my camera worked on Feisty before with no problem. It worked on debian too, but recently it wont. I followed the spanish guide but no success. Did you restart you computer or X? Do i need to modprobe any modules? (i don't know spanish i just made copypasta of the commands)

[COLOR="DarkOrange"]EDIT: A restart solved it for me! The spanish guide was quite usefull. Thanks.[/COLOR]

---

### Post by xarroyo on 2007-09-03
```
xavi@dellota:~$ ls /dev/vid*
ls: /dev/vid*: No such file or directory
xavi@dellota:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 413c:8126 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
xavi@dellota:~$ ls /dev/vid*
/dev/video0
xavi@dellota:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 413c:8126 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
xavi@dellota:~$ 
```

if the webcam is not connected the ls /dev/vid* directory is not recognized.. and it is recognized when plugged.. but when i start camorama is still not recognized the camara!! *_please, i would appreciate if someone knows a solution to my problem.._* the first time i followed the guide steps and it worked on Kopete, aMsn and also Camorama.. but now i am trying again with the webcam and i can't.. Camorama send the message: could not connect to video device (/dev/video0) Please check connection!

---

### Post by spupy on 2007-09-03
The device /dev/video0 appears only when the camera is connected. Does camorama give some output about what happens? Try the v4l-conf package, it has a program called v4l-info, it gives some info about the camera.

---

### Post by xarroyo on 2007-09-03
```
xavi@dellota:~$ v4l-info

### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "zc0301"
        card                    : "ZC0301[P] PC Camera"
        bus_info                : "usb-0000:00:1d.2-1"
        version                 : 1.0.5
        capabilities            : 0x5000001 [VIDEO_CAPTURE,READWRITE,STREAMING]

standards

inputs
    VIDIOC_ENUMINPUT(0)
        index                   : 0
        name                    : "Camera"
        type                    : CAMERA
        audioset                : 0
        tuner                   : 0
        std                     : 0x0 []
        status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
        index                   : 0
        type                    : VIDEO_CAPTURE
        flags                   : 1
        description             : "JPEG"
        pixelformat             : 0x4745504a [JPEG]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
        type                    : VIDEO_CAPTURE
        fmt.pix.width           : 640
        fmt.pix.height          : 480
        fmt.pix.pixelformat     : 0x4745504a [JPEG]
        fmt.pix.field           : NONE
        fmt.pix.bytesperline    : 0
        fmt.pix.sizeimage       : 307200
        fmt.pix.colorspace      : unknown
        fmt.pix.priv            : 8

controls

```

Displays the info of the webcam.. but it is still not working!!

---

### Post by Icarosaurus on 2007-09-04
Sorry.I'm only reading quickly this thread. I'll read better soon.
try:
```

lsmod |grep gspca

```
if nothing appears
do:
```

sudo modprobe gspca

```
Test if it works.
And when you want to load the driver every time you start the machine, open the file /etc/modules and add the line
```

gspca

```

Sorry if I didn't catch the solution...

---

### Post by xarroyo on 2007-09-04
```
xavi@dellota:~$ lsmod |grep gspca
gspca                 607824  0 
videodev               28160  2 gspca,zc0301
usbcore               134280  6 gspca,zc0301,hci_usb,ehci_hcd,uhci_hcd
xavi@dellota:~$ 

```

I have added that line on the modules.. but nothing happens!! I am looking on the web for a solution, but if anyone know how to solve it, i would appreciate it!!

---

### Post by laurad on 2007-09-06
I have been having the exact same problem with a Logitech QuickCam/IM camera.  I know this isn't a total solution.but I tried running 'sudo camorama' and it worked.  I then ran 'sudo ekiga' and I also had success with my video.  I'm still a bit of a newbie so I'm sure there is another solution to this.  From what I gather it appears I do not have access to /dev/video unless I am root.
Any other solutions would be great but for now I am happy that I have my camera working!

---

### Post by spupy on 2007-09-06
> **laurad said:**
> I have been having the exact same problem with a Logitech QuickCam/IM camera.  I know this isn't a total solution.but I tried running 'sudo camorama' and it worked.  I then ran 'sudo ekiga' and I also had success with my video.  I'm still a bit of a newbie so I'm sure there is another solution to this.  From what I gather it appears I do not have access to /dev/video unless I am root.
Any other solutions would be great but for now I am happy that I have my camera working!

Yes, do that, i remember now that this was a solution for me too.

---

### Post by xarroyo on 2007-09-06
Thanks.. Now the webcam is working... :)
If any problems i will post again! :lolflag:

---

### Post by ecschiel on 2007-11-02
> **laurad said:**
> I have been having the exact same problem with a Logitech QuickCam/IM camera.  I know this isn't a total solution.but I tried running 'sudo camorama' and it worked.  I then ran 'sudo ekiga' and I also had success with my video.  I'm still a bit of a newbie so I'm sure there is another solution to this.  From what I gather it appears I do not have access to /dev/video unless I am root.
Any other solutions would be great but for now I am happy that I have my camera working!

Try adding your user to the video group

---

### Post by raymondx on 2007-12-07
My webcam stopped working since left the Breezy Badger version.  It has been giving the same error message on camorama since then...

error:

could not connect to video device (/dev/video0) Please check connection..

running "v3l-info" gives the following output...

> ### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "zc0301"
        card                    : "ZC0301[P] PC Camera"
        bus_info                : "usb-0000:00:03.0-2"
        version                 : 1.1.7
        capabilities            : 0x5000001 [VIDEO_CAPTURE,READWRITE,STREAMING]

standards

inputs
    VIDIOC_ENUMINPUT(0)
        index                   : 0
        name                    : "Camera"
        type                    : CAMERA
        audioset                : 0
        tuner                   : 0
        std                     : 0x0 []
        status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
        index                   : 0
        type                    : VIDEO_CAPTURE
        flags                   : 1
        description             : "JPEG"
        pixelformat             : 0x4745504a [JPEG]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
        type                    : VIDEO_CAPTURE
        fmt.pix.width           : 640
        fmt.pix.height          : 480
        fmt.pix.pixelformat     : 0x4745504a [JPEG]
        fmt.pix.field           : NONE
        fmt.pix.bytesperline    : 0
        fmt.pix.sizeimage       : 307200
        fmt.pix.colorspace      : unknown
        fmt.pix.priv            : 8

controls

Please help :confused:

---

### Post by raymondx on 2007-12-08
solved!...i ditched my gutsy gibbon and went back to dapper drake! next time i'll think twice before upgrading my ubuntu ..hehehe

---

### Post by xarroyo on 2007-12-10
Hey raymondx, Did you try the steps that are mentioned on this thread??? I am sorry to hear you went back to Dapper Drake.. When you went back to DD did you have to do any configuration for your webcam?

---

### Post by raymondx on 2007-12-10
i downloaded and installed gutsy gibbon and it worked too.  The problem probably started when i was messing up with the webcam drivers years ago back when i was using breezy, it never got fixed and was carried along through subsequent upgrades.  A fresh install of a new system did the trick...but months of work got lost. :cry:

---

### Post by wford002 on 2007-12-11
Hi, I'm having similar problems with my webcam. 

According to lsusb I get: Bus 002 Device 003: ID 093a:2608 Pixart Imaging, Inc. 

This webcam is supposedly supported by the gspcav1 driver. According to:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

 So I've followed the instructions from this thread, and the spanish article, to install the driver, and everything seems to go well until I get to ls /dev/vid*, which returns "no such file or directory". I'm really at a loss at this point. I've also tried the program "easycam", which didn't work either. Any help would be greatly appreciated. Thanks.

My computer is a toshiba satellite laptop. model a135-s4467, and the webcam is a cheap clip-on style, also a toshiba, but from what I've read the numbers returned from lsusb are more important.

---

### Post by asnd16 on 2007-12-13
>  
could not connect to video device (/dev/video0)
Please check connection..

 i have my webcam plugged... if i go to /dev i dont have the folder video0... 
if you type this on the konsole 

ls -la /dev/video0  

i get the following message crw-rw---- 1 root video 81, 0 2007-08-20 17:20 /dev/video0

i read from a website in spanish that says that i have to add my user in a group that is allow to have the webcam.. i tried it by doing the:

sudo adduser nickUser video

i did that but i dont have anyresults.. so.. what else do i need to do!!!?????


moses@moses-liltravler:~$ lsusb 
my output is like this . . . 
Bus 005 Device 009: ID 046d:0990 Logitech, Inc. 
Bus 005 Device 007: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


oses@moses-liltravler:~$ ls -la /dev/video0
ls: /dev/video0: No such file or directory

can anyone help?

---

### Post by xarroyo on 2007-12-15
>  laurad
	  	
Join Date: Sep 2007
Beans: 2
Re: could not connect to video device (/dev/video0) Please check connection..
I have been having the exact same problem with a Logitech QuickCam/IM camera. I know this isn't a total solution.but I tried running 'sudo camorama' and it worked. I then ran 'sudo ekiga' and I also had success with my video. I'm still a bit of a newbie so I'm sure there is another solution to this. From what I gather it appears I do not have access to /dev/video unless I am root.
Any other solutions would be great but for now I am happy that I have my camera working!

I perform this... sudo camorama which was the program i installed to test the webcam... and then the folder dev/vid* appear.. try that wford002, about asnd16 i didn;t find the model of your webcam, but since it is a Logitech it should work.. for which program you want to use the webcam??? in my case  i wanted to use it with kopete, so i did "sudo kopete" once.. and then, in the next restart i opened the OS it worked fine.. i hope this helps you both!!

---

### Post by asnd16 on 2007-12-17
yeah same error when doing sudo camorama

---

### Post by xarroyo on 2007-12-17
Hey...
Did you download the and compiled the 20070508.tar.gz (or the latest version if avaliable)??? Check this site>> [http://mmejiav.wordpress.com/2007/06/07/modulo-gspca/](http://mmejiav.wordpress.com/2007/06/07/modulo-gspca/)
Basically says to download the gspca and the steps of how to extract the files and compile them!!

You're a Fedora user, have you tried your webcam on Fedora??

---

### Post by asnd16 on 2007-12-17
I have not tried it in fedora yet . . . but I will give the other a chance. .Alright pretty interesting . . now I am trying something new. . .
but there is no modules folder in the usr/src/ 
Getting close but here is my output . . . I still get the same error 
>  lsmod | grep gspca 
gspca                 608336  0 
videodev               29312  2 gspca,uvcvideo
usbcore               138632  10 gspca,ndiswrapper,snd_usb_audio,snd_usb_lib,uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
moses@moses-liltravler:/usr/src/modules/gspcav1-20071214$ ls /dev/v*
/dev/vcs   /dev/vcs4  /dev/vcs8   /dev/vcsa3  /dev/vcsa7
/dev/vcs1  /dev/vcs5  /dev/vcsa   /dev/vcsa4  /dev/vcsa8
/dev/vcs2  /dev/vcs6  /dev/vcsa1  /dev/vcsa5  /dev/video0
/dev/vcs3  /dev/vcs7  /dev/vcsa2  /dev/vcsa6
moses@moses-liltravler:/usr/src/modules/gspcav1-20071214$ camorama
moses@moses-liltravler:/usr/src/modules/gspcav1-20071214$ sudo camorama
moses@moses-liltravler:/usr/src/modules/gspcav1-20071214$ gqcam-v /dev/video0
bash: gqcam-v: command not found
moses@moses-liltravler:/usr/src/modules/gspcav1-20071214$ 



---

### Post by jlidgard on 2007-12-19
I'm having same problem with a quickcam messenger (046:08da).
I need to sudo camorama to get it to connect to /dev/video0.
However camstream works OK without sudo-ing. Can't get any of my phone apps to see the
camera though (ekiga / wengophone / skype 2.0 beta).
Tried becoming a member of video group but didn't fix it.
Why does camstream as a normal user work ? Does it access the webcam via a different method ?

---

### Post by jlidgard on 2007-12-19
Managed to get the webcam working although I'm not exactly sure how I did it.
I went back to the original gspca driver that came with ubuntu 7.10 & did a depmod -ea. & a reboot. Suddenly everything started working including skype 2.0 beta.

---

