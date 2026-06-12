---
title: "Webcam Q-TEC 310 USB - need driver"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by eekfonky on 2008-02-07
Does anyone know how I can get a driver for my Q-TEC 310 USB webcam?

---

### Post by linuxwizard on 2008-02-07
Have you tried using Ekiga to see if webcam works/detected ? Post results of the command > lsusb

---

### Post by eekfonky on 2008-02-07
It doesn't work with Ekiga

Here's the code

```
lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0c45:602c Microdia Clas Ohlson TWC-30XOP WebCam
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by linuxwizard on 2008-02-07
This is the driver that may work with your webcam >[http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/) >

---

### Post by eekfonky on 2008-02-07
That worked a treat. Thanks! I can't configure it for camorama, it's still looking for the wrong thing any suggestions as to which applications I can use to take pic etc.

---

### Post by linuxwizard on 2008-02-07
What problems are you having with Camorama ? When you open Camorama their should be a white box on the right side, right click in that box will beings up some filter settings you can use.

---

### Post by vivalant on 2008-02-07
> **eekfonky said:**
> That worked a treat. Thanks! I can't configure it for camorama, it's still looking for the wrong thing any suggestions as to which applications I can use to take pic etc.

You can use "videoview" available at the author's homepage:
[http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=5](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=5)

I use to use that application to set the properties of my webcam, for recording, etc. It even works while streaming with another application like Camorama ..

A list of applications is in the FAQ:
[http://www.linux-projects.org/downloads/FAQ.html](http://www.linux-projects.org/downloads/FAQ.html)

---

### Post by eekfonky on 2008-02-07
First camorama  is looking for a generic video device rather than the correct one. The whie box is for filters not for changing the video source.

Second how would I compile videoview?

---

### Post by eekfonky on 2008-02-11
Can anyone help??? Please!!

---

### Post by linuxwizard on 2008-02-11
eekfonky
What do you need ? What have you tried or done?

---

### Post by eekfonky on 2008-02-11
Ok, I can get my webcam to work with Ekiga or Skype 2.0 beta but not with any other app. For both Ekiga and Skype I have to change the input from generic/unknown to sn9cxxx driver. Can I make any other app work e.g camorama? how do I default my settings to the correct driver?

Thanks

---

### Post by linuxwizard on 2008-02-11
Your webcam is working in Ekiga & Skype you would think it should work in other appls. Not sure what to say. Check through the settings in the other appls. you are trying, you may not have something setup right within those appls.

---

### Post by eekfonky on 2008-02-12
how do you configure Camaorama to look for the correct driver - antone?

---

### Post by linuxwizard on 2008-02-12
I have only used Camorama maybe 1 time. So i went and looked around I don't see anyway to change which driver you use. It must just pick it up automatically. Looks like you will need to find something else to use. Or maybe someone else will offer some help where or how to change the driver you use.

---

### Post by eekfonky on 2008-02-12
thanks anyway - can anyone else give me an app that can be used?

---

### Post by Motorhead Kaze on 2008-03-14
Howdy,
```
This is the driver that may work with your webcam http://www.linux-projects.org/modules/news/
```

I need a driver for my Microdia Clas Ohlson TWC-30XOP WebCam as well, and I followed your link, but this is a time limited driver.  Anyone have a driver that is not time limited?

---

### Post by linuxwizard on 2008-03-14
Motorhead Kaze
For Microdia webcams this is the only place I know you can get a driver for your cam > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by apienk01 on 2008-05-07
I have made this cam (0c45:602c Microdia Clas Ohlson TWC-30XOP WebCam) to work in all applications (except xawtv) when I blacklisted the sn9c102 module in Gutsy. Without it, the kernel loads sn9c102 and identifies the cam as v4l2 webcam. Now, v4l2 is a quite new standard, so few applications support it correctly. Ekiga does, but not camorama, gqcam or vlc - or so it seems in my case. Also, Ekiga has a very poor framerate with this driver. Fortunately, this cam is also supported by gspca kernel module in Gutsy. All you have to do is unload sn9c102 and load gspca. If you don't have gspca, get it from repositories. The package name is gspca-modules. So first close all applications using the cam, and then:

```
sudo rmmod sn9c102
sudo modprobe gspca
```

Now camorama, gqcam and vlc should work fine, and Ekiga should have better framerate. :biggrin: To make this permanent, blacklist sn9c102 in /etc/modprobe.d/blacklist by adding this line:

```
blacklist sn9c102
```

Some problems still persist. I cannot adjust image parameters in any of the applications. And the cam requires to own the whole USB bus. In order to make it work I have to disconnect all USB devices, including mouse. Otherwise I get "No space left on device" error. It's good laptops have touchpads :)

EDIT: The name of the webcam is Media-Tech EOS MT4004, in case someone searches for this.

---

