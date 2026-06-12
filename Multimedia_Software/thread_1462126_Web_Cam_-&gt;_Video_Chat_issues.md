---
title: "Web Cam -&gt; Video Chat issues"
date: 2010-04-25
forum: Multimedia Software
---

### Post by jv2112 on 2010-04-25
I have web cams on two Linux Machines.


Asus Eee Netbook
Linux Mint 8
Pidgin

Cheese recognizes the web cam but the pidigin video-plug in does not seem to work.

 
Personal Build Desktop
Ubuntu 10.04
Evolution IM Program

If "start a call" it recognzes the vdioe camera but it does not appear the system at the other end recieves the call. 

When I use the IM feature the "video" call options seem to be greyed out.


In either scenario the recieving system are using various chat clients and are windoze machines as well as Linux systems. Any direction would be appreciated. The grandparents would like to see the Grandchildren.....

---

### Post by gradinaruvasile on 2010-04-25
The best free audio/video program for Linux is Skype hands down (i did test every available free program) - i use it with Ubuntu/Debian and works perfectly well under Linux. The used bandwidth is very low (6 or so KiB up/down for voice, 15 or so for video), sound quality is perfect, reliability is very good (i frequently had 1-3 hours of talks and no crashes). Also it interoperates with Windows/Mac version perfectly.

On your specific problem:

Use only 1 program on both machines if you want it to work consistently and well.
Empathy doesnt worked consistently for me, it is not a mature program yet. Best is to use Pidgin on both ends, make sure it is the voice/video enabled version.
For Ubuntu there is a PPA with the latest video-enabled Pidgin:

[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

Here is how to configure audio/video on Pidgin:

1. Open Pidgin, tools, plugins, voice/video, configure

Audio will work most likely left on default.

Video on the other hand needs a bit of attention:
Output - select xv output (probably the default is xv too, but best is to specify).

Input - here is a bit tricky:
You explicitly MUST select a device in order to work:

1. Press alt+f2, type gstreamer-properties, see what combination works in order to see your camera when you press "test"
2. Configure the exactly the same options in the voice/video configurations video tab.
3. If you want a video conference between a computer that has video camera and the other doesnt, on the computer that does not have camera YOU MUST SPECIFY the "Test Input" plugin otherwise it wont work. The other side (that has camera) will see a color striped box in the place where video should be.

Bottom line: both Pidgins must have a specified video input device in the plugins configuration options otherwise it wont work.

Potential problems:
Some usb webcams mostly using the gspca driver (like mine) dont work correctly by default with some programs, Skype and Pidgin is some of these - green/black+white/ping garbled video. The workaround is the following:

Launch the program (example pidgin) like this:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so pidgin

Edit:

If you want Windows/Linux interoperability, definitely use Skype.
Pidgin's video/voice plugin is not present in the windows version AFAIK.

---

