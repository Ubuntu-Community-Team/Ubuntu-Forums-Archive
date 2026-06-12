---
title: "Creative Webcam installation"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by frank002 on 2007-09-04
I am a newbie with Linux( Been using Feisty for about 2 weeks). I have a Creative Labs webcam sitting on top of my monitor but I do not know how to get it to work in Feisty. Need help. Thanks.

---

### Post by linuxwizard on 2007-09-04
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by loell on 2007-09-04
try plugging your webcam

then type the command


```
lsusb
```

copy and paste the output here , 

if you would like to know first hand if your webcam is compatible with ubuntu out of the box,

install camorama ```
sudo apt-get install camorama
``` then execute camorma through 

the command line, it will show images from your webcam or prompts you an error if its no detected.

---

### Post by frank002 on 2007-09-12
Sorry it took so long to thank you but better late than never.

---

### Post by iohmie on 2007-09-13
Bus 005 Device 006: ID 041e:403d Creative Technology, Ltd WebCam Notebook Ultra

Heres my webcam, i having trouble installing it. pls help

---

### Post by linuxwizard on 2007-09-13
iohmie
According to this you need the driver Spca5xx. 
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

Which the spca5xx driver is included in the Ubuntu kernel and works out of the box in Ubuntu 6.06 and higher. So all you need is plug it in and should work for you.

Look at this for more info
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by iohmie on 2007-09-14
Thanks for the reply. but i cant get it work it says "No camera found or no compatible camera found"
any suggestion...

---

### Post by chiyanksriraj on 2007-09-14
I am using a Creative Live! Cam Video IM Pro

And I am unable to make it work with Fiety Fawn. I am not sure as to what drivers were supposed to install...My webcam id would be 041e:4055 I searched using this also but in vain...can anyone help me finding a driver.

Thanks in advance.

---

### Post by loell on 2007-09-14
you could try compiling this driver [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

even then, the chances are still very slim :( , its one of those webcam who has not yet been supported in linux.

---

### Post by shark1970 on 2008-02-22
i am trying to install a Creative Live! Cam Vista IM (model: VF0420) using the following instructions:

for "Install debian module package", as follows:

sudo apt-get update
sudo apt-get install ov51x-jpeg-source module-assistant
sudo module-assistant a-i ov51x-jpeg 

it appeared to have installed as there were no error messages but Easycam is still not recognizing the device...

any suggestions?

---

### Post by shark1970 on 2008-02-22
hey guys...?  anyone out there?  this device should work!  would appreciate some help!

---

### Post by linuxwizard on 2008-02-22
If you installed the driver. Try using Ekiga to see if cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

---

### Post by shark1970 on 2008-02-22
still no device detected... what concerns me is if i missed a step during the installation ie. all this mumbo jumbo:

 Compilation and installation

First, you must have a working kernel module build and the videodev module compiled. In most distributions, this you may need some kernel headers corresponding to your kernel. See the command uname -r to get your kernel version.

Basically, you need a kernel with its headers, and the videodev module built with video4linux option (try modprobe videodev as root).

Then, as normal user, type in the ov51x-jpeg-x.x.x directory:

% make

and, as root:

# make install
# modprobe ov51x-jpeg

or if this fails for any reason:

# modprobe videodev
# insmod ./ov51x-jpeg.ko

sorry dude - i'm a very new user and have relied heavily on my techy for installations... gotta spoon feed me... thanx!

---

### Post by shark1970 on 2008-02-22
i don't think the issue is with "ekiga" or with "skype" (which i've also installed)... the device is not being recognized... i tried installing it with the instructions from my original email but skipped the step above (not sure if i needed to do more)... i really need to get this thing working!!

frustrating!!

---

### Post by shark1970 on 2008-02-22
Seriously you guys!!  is there someone out there who can help me out here???

I need clear explicit "do this" instructions to get this little piece of plastic working!!!!!!  i hate MS and love all that Linux represents but unfortunately i am not familiar enough to make it work yet!!!!  

PLEASE give me a few minutes of your time and help me out!!!

---

### Post by linuxwizard on 2008-02-22
You need to be ALOT MORE PATIENCE you are not the only one in this forum.

According to this > [http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx) > you need this driver > [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource) > look over make sure you didn't miss something.

---

### Post by shark1970 on 2008-02-22
this is what i'm not sure about... i have followed the installation instructions for the debian module package... i do not understand what they are talking about in the "compilation and installation" section above it, ie. modprobe, videodev, kernel headers... isn't that stuff already part of ubuntu?

---

### Post by shark1970 on 2008-02-22
simply put... how do i do the following???  what is the command for typing in a "directory"?

Then, as normal user, type in the ov51x-jpeg-x.x.x directory:

% make

and, as root:

# make install
# modprobe ov51x-jpeg

---

### Post by mjukis on 2008-03-03
Regardless what's mentioned earlier in this thread there are no drivers for your webcam so far as you can see on

[http://opensource.creative.com/webcam.html](http://opensource.creative.com/webcam.html)

if you search for

"WebCam Live! Ultra for Notebooks".

Sorry, I have the same webcam and the problems as you.
[http://ubuntuforums.org/showthread.php?t=276181](http://ubuntuforums.org/showthread.php?t=276181)

---

### Post by linuxwizard on 2008-03-03
mjukis
You are using outdated website > [http://opensource.creative.com/webcam.html](http://opensource.creative.com/webcam.html) >  the new website and that webcam has a driver. Stop causing confusion. Here is the new website > [http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx)

---

### Post by fragimar on 2008-07-02
I'm pretty new with Ubuntu but I also have a Creative webcam. I also can't get it to work with Camorama. But when I turn on Skype, go to options, and video devices I can hit the test button and see my beautiful mug. :popcorn:

If it was a driver problem then wouldn't every program have the same problem recognizing the webcam? Let me know cause I'd like to see my webcam with something else besides Skype.

---

