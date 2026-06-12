---
title: "Sweex Webcam with Crescentec Corp. bridge"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by MrQuincle on 2007-04-30
Dear forum members and ubuntu users,

Currently I have Feisty running; uname -r: 
2.6.20-15-generic

The following USB devices can be found; lsusb:
```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 0932:1100 Crescentec Corp. 
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  
```

The webcam has Sweex printed upon it, but is listed under Crescentec Corp over here. I didn't know that gspca is installed by default, so I compiled the spca5xx driver like explained here: [https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx). Afterwards I tried the gscpa module (removed spca5xx); dmesg | grep spca
```

[ 4529.282491] usbcore: registered new interface driver spca5xx
[ 4529.282497] /usr/src/modules/spca5xx/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
[ 5577.392253] usbcore: deregistering interface driver spca5xx
[ 5577.392286] /usr/src/modules/spca5xx/drivers/usb/spca5xx.c: driver spca5xx deregistered

[ 6044.702819] usbcore: registered new interface driver gspca
[ 6044.702828] /usr/src/gspcav1-20070426/gspca_core.c: gspca driver 01.00.16 registered
[ 6537.488322] usbcore: deregistering interface driver gspca
[ 6537.488362] /usr/src/gspcav1-20070426/gspca_core.c: driver gspca deregistered

[ 6540.672283] usbcore: registered new interface driver gspca
[ 6540.672295] /usr/src/modules/gspca/gspca_core.c: gspca driver 01.00.12 registered

```
Like you see, I installed gspca twice. First manually, secondly I discovered that it is possible to do: m-a auto-install gspca (although that appeared to lag some minor version releases behind). 

Also important, there is no webcam recognized! Only references to the new driver, not to the webcam!

Anyway, I'm willing to provide more information, I don't know what by now. I'm a semi-noob. 

I have two questions:
[LIST]
[*]Which driver should work for my Sweex webcam in Feisty?
[*]What is the most easy way to test if a webcam works? Currently I look if a device appears at /dev/video (it does not). The next step I know is directly bothering somebody else using amsn.
[/LIST]

Thanks a lot for your time!

---

### Post by MrQuincle on 2007-08-24
I guess that it's not possible to use this webcam with Ubuntu. Good project to write my own driver some time. I will keep it around here.

Can anybody of you recommend a webcam that is sort of guaranteed to work with Ubuntu (Feisty Fawn)? Thanks in advance.

---

### Post by wangrui on 2008-03-18
I have the exact same webcam. I bought it long long time ago. It feels like the first 640x480 webcam in China. The resolution is high but quality is not good.  I only used it several times. But I would like to write a driver for it if possible. Can anyone gives some link on how to write a webcam driver for linux? Is there any open source examples? I have googling for quite a time. But still didn't find any definition of the linux video interface. I'm new to linux and it sounds very interesting to me.

---

### Post by MrQuincle on 2008-04-30
Dear all,

Now more than a year later and with Ubuntu Hardy Heron I am still not being able to get this webcam working, which works on my nerves. That is not good for the people around me, the universe, and above all, myself. :popcorn:

So, let's see. Is there any, any way to get some data from this webcam into Linux? Let's check again lsusb for what is known regarding this thingy: Bus 002 Device 002: ID 0932:1100 Crescentec Corp. 

**The big term: 0932:1100**
On searching for 0932:1100 I get on this site [http://listing.driveragent.com/usb/0932/1100?q=0932%3A1100&PHPSESSID=e8hltk7vo550feqao1ktd9sub4](http://listing.driveragent.com/usb/0932/1100?q=0932%3A1100&PHPSESSID=e8hltk7vo550feqao1ktd9sub4) some Windows drivers. It is called a USB2.0 Video Enhancement Device over there. Ha ha. :-) The driver is 13.2 MB, wow! Curious what's in there!? The bad thing is that you need a subscription to this site to obtain this driver. Good thing is that I actually still have that CD! The worst thing though is that I actually will need to use it in Windows later on!

My quest continues... I can find 0932:1100 also on [http://alpha.dyndns.org/ov511/cameras.html](http://alpha.dyndns.org/ov511/cameras.html) titled "Linux OVCam drivers - list of known devices". And with the header "known OmniVision-based devices and the ones that are easily confused"!! Okay, a bit my own words here... ;-) 

Over there a Video Capture Device or TV Tuner from Belkin is mentioned: 
Hi-Speed USB 2.0 DVD Creator (F5U228) with bridge Crescentec DC1100 (0932:1100) with ADC SAA7113h. Mmmm, what is a bridge? It is again listed at "Common Webcam Chipsets" with VID (vendor id) 0932 (Crescentec), PID (product id) 1100 and chipset name: Crescentec DC1100 USB2.0 Video Capture Controller. It bluntly states for Linux support: No. Yeah, I figured that out by now. :lolflag: But what exactly is the chipset? And where can I get the specs of that chipset? Is it reversed engineered by someone? 

**The big term: DC1100**
Okay, so let's search for the Crescentec DC1100. At [http://www.thefreelibrary.com/CRESCENTEC+WEB+CAM+CONTROLLER+MEETS+USB+2.0+COMPLIANCE.-a087346988](http://www.thefreelibrary.com/CRESCENTEC+WEB+CAM+CONTROLLER+MEETS+USB+2.0+COMPLIANCE.-a087346988) there is a positive article about the CT-DC1100 web camera controller. Namely that it has been added to the USB-IF integrators list. It has a CMOS sensor interface module (apparently for the actual camera) and a USB 2.0 high-speed (not full-speed) device controller module, a UTMI or ISP1501 transceiver interface (for what?) an EEPROM interface (for some additional memory) and some GPIO. There seems to be a software image enhancement filter. I guess that means that some configuration parameters can be sent to the chipset, to adjust some stuff in the image processing pipeline in a very early stage.

**The big term: CT-DC1100**
Okay, so let's resume our everlasting quest. Searching on the CT-DC1100 chipset, we come at [http://www.datasheetcatalog.com/datasheets_pdf/C/T/-/D/CT-DC1100.shtml](http://www.datasheetcatalog.com/datasheets_pdf/C/T/-/D/CT-DC1100.shtml) where you can download a datasheet: [http://www.datasheetcatalog.org/datasheets2/33/331732_1.pdf](http://www.datasheetcatalog.org/datasheets2/33/331732_1.pdf)

There is even an internal block diagram, but the PDF is bad quality. There is a crystal and PLL for the clock. A Sensor Interface Unit for indeed the CMOS sensor. There is a FIFO buffer that goes to a Video Decoder Interface Unit. There is Endpoint Logic, funny terms they invent... The end of the universe logic... It's a pity that the stuff that is important for us, is not shown anywhere: some kind of API. What do I do besides sending an "open" or "close" command? What kind of protocols do I have to adhere to? (I hope I can find something that obeys to standard USB 2.0 that I can use of course.)

**A commercial driver somewhere?**
Before I continue, I list a post from linux-usb-devel. Seems like someone else is also fooling around with this chipset.
[http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg28934.html](http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg28934.html) It seems they are talking about this driver: [http://www.qbik.ch/usb/devices/showdr.php?id=101](http://www.qbik.ch/usb/devices/showdr.php?id=101) But this is for companies only(?) [http://www.tazforum.thetazzone.com/viewtopic.php?t=2805&sid=f25431bab0cae59af14368da3edee243](http://www.tazforum.thetazzone.com/viewtopic.php?t=2805&sid=f25431bab0cae59af14368da3edee243) I don't know who Luca Risolia is, but it seems he has been developing those. See also [http://www.linux-usb.org/devices.html](http://www.linux-usb.org/devices.html) where he did some other chipsets too. Good starting point for later! Probably those chipsets are not that different! One option: he was working for himself. Never mind, skip that option. Only option: he was working for a company who had datasheets. And a company makes most often similar chipsets, not reinventing the protocol wheel each time again.

**Some other dead ends**
Funny by the way that Intel uses the CT-DC1100 chipset as an example (and a better block diagram!) for its USB compliance at [http://www.intel.com/technology/magazine/computing%2Fdt06012.pdf&ei=IXEYSNviBp_8wwGKr8j7Cw&usg=AFQjCNFCktwy9S3sKtD0V0iV3YfmkXb3OA&sig2=h9wTTfwe4u3G7rALhUn0QA](http://www.intel.com/technology/magazine/computing%2Fdt06012.pdf&ei=IXEYSNviBp_8wwGKr8j7Cw&usg=AFQjCNFCktwy9S3sKtD0V0iV3YfmkXb3OA&sig2=h9wTTfwe4u3G7rALhUn0QA)

At [http://www.techspot.com/vb/all/windows/t-28555-CRESCENTEC-search.html](http://www.techspot.com/vb/all/windows/t-28555-CRESCENTEC-search.html) they are talking about a possible link between Crescentec and Syntex. So I checked the driver at [http://www.sanghua.com/technology.asp](http://www.sanghua.com/technology.asp)
It's a pity but it is binary, seems only to be about the DC112X series and is Windows-based. That's what he said, spitting over his left shoulder... 

**What's more in there?**
Let's check the tuner that uses the same chipset. [http://www.digit-life.com/articles2/aver-tv-usb20/aver-tv-usb20.html](http://www.digit-life.com/articles2/aver-tv-usb20/aver-tv-usb20.html)
Here you see also the Philips transceiver, ah, logical it is a USB transceiver. The ISP1501. I guess lots of specs can be found about that one. But the big question mark is still the DC1100 of course.

The Crescentec links to [http://www.empiatech.com.tw/](http://www.empiatech.com.tw/) so that's nice to know. Apparently Crescentec was overtaken by Empia some while ago. However, I cant find anything on that on the web. Empia is founded in 2002, based in Taiwan and the Silicon Valley. 

In the pictures I dont see "SAA7113h" somewhere, but the Crescentec chip, contains some more numbers. DC1100-A4, and that's not the format. :-) And STK68C3323. Although, if I search for it online I see only DC1100-A3, so perhaps I cant read it correctly.

**The ISP1501**
On NXP, founded by Philips - in other words, they changed their name, they fools - you can find the Product Specification of the ISP1501: [http://www.nxp.com/#/pip/pip=[pip=ISP1501-02]|pp=[v=d,t=pip,i=ISP1501-02,fi=,ps=0][0]](http://www.nxp.com/#/pip/pip=[pip=ISP1501-02]|pp=[v=d,t=pip,i=ISP1501-02,fi=,ps=0][0])
Check the cool block diagram, I love diagrams! You see the high and the full speed transceivers. 
There is a large PDF about the ISP1501 at [http://www.openhw.org/data/openhard/source/bb2b43d5b3cd3536539ee2d6019f695c.pdf](http://www.openhw.org/data/openhard/source/bb2b43d5b3cd3536539ee2d6019f695c.pdf)

**Deep in there again :-p **
Hey, scratch! Done that! FYI: In the meanwhile I was trying to open my webcam, and it was really screwed. :-) The chipsets are indeed the ones that are also in the aver-tv-usb20 tuner. On the front I see the board number K37-66201-M4A, Ver: 2C. On the back, the Cresentec chip: DC1100-A4, STK68C3323 (I read it correctly!). And 0341 and 203A014-7019 as additional numbers. Except for the ISP1501 chip nothing interesting here. Bunch of resistors and capacities, that's all. 

**Conclusion: reverse engineer it!**
So, it seems we have to reverse engineer it. How to start with such thing? Let's take a look at an Empia device, perhaps they used some of the same stuff: [http://www.linuxtv.org/v4lwiki/index.php/Em28xx_devices](http://www.linuxtv.org/v4lwiki/index.php/Em28xx_devices)
Over there is stated that em2750 seems to be used by webcams. Now we encounter another interesting link to Reverse Engineering USB Webcams at [http://www.linuxtv.org/v4lwiki/index.php/Reverse_Engineering_USB_Webcams](http://www.linuxtv.org/v4lwiki/index.php/Reverse_Engineering_USB_Webcams)
Apparently there is no "pure" reverse engineering by launching some default protocols on the device, but it is by inspecting the messages that go hence and forth by connecting the USB device to windows and using the binary drivers from the producer. They don't tell anything at that wiki by the way. 

**Example...**
In this group they are reverse engineering a microdia chipset. Interesting info all over the place. E.g. &#65279;at [https://groups.google.com/group/microdia/browse_thread/thread/513347f2aa4d3848#](https://groups.google.com/group/microdia/browse_thread/thread/513347f2aa4d3848#) I learned that the main reason for having a bridge driver in the kernel is because webcams need ISO transfers, that are very time sensitive. So, you don't want to have it in userspace land, where it can be preempted (interrupted by the kernel) on random moments. It is cool to read the posts of Gray Water, just wanting to write a driver, even without knowing C, but going for it! :-) See: &#65279;[https://groups.google.com/group/microdia/browse_thread/thread/d5c82835e861b9d2#](https://groups.google.com/group/microdia/browse_thread/thread/d5c82835e861b9d2#)

**Some loose ends**
Over here they tell us that we don't have to expect that there is some standard protocol used for USB cams: [http://osdir.com/ml/usb.devel/2002-04/msg00553.html](http://osdir.com/ml/usb.devel/2002-04/msg00553.html) so that is not very promising! 

Over here Erik Andrén tells some of the register writes for an Ali M5602 webcam: [http://eriksdatadump.blogspot.com/2008/02/reverse-engineering-ali-m5602-webcam.html](http://eriksdatadump.blogspot.com/2008/02/reverse-engineering-ali-m5602-webcam.html)

And now I am finished for today. Just snooped the traffic between my webcam and windows by using usbsnoop. I can't post it here, but will attach it later. Maybe we can figure it out together, what exactly the protocol is, using that is as a starting point. See you later!

---

### Post by taslinux on 2008-06-28
Mr Quincle,

Thank you for your careful (but so far unprofitable!) research. I have been working unsuccessfully on the same problem, but with a different approach. I noticed that when I plugged in my Crescentec 0932 1100, Ubuntu decided it was an *audio* device:

May  5 08:32:16 bobs-dell640m kernel: [  115.994575] usbcore: registered
new interface driver snd-usb-audio
May  5 08:32:16 bobs-dell640m pulseaudio[5900]: alsa-util.c: Device hw:1
doesn't support 44100 Hz, changed to 8000 Hz.
May  5 08:32:16 bobs-dell640m pulseaudio[5900]: alsa-util.c: Device hw:1
doesn't support 2 channels, changed to 1.
May  5 08:32:16 bobs-dell640m pulseaudio[5900]: alsa-util.c: Device hw:1
doesn't support sample format s16le, changed to u8.
May  5 08:32:16 bobs-dell640m pulseaudio[5900]: alsa-util.c: Cannot find
fallback mixer control "Mic".

So I tried telling Ubuntu that it was a video device by writing the rule

KERNEL=="video*",SYSFS{idVendor}=="0932",SYSFS{idProduct}=="1100",SYMLINK+="webcam"

I named this rule '50-minicam.rules' and put it into /etc/udev/rules.d/

This *should* tell Ubuntu when I plug in the device that it's a video camera. I could then do a search for webcam drivers that might operate it.

However, the rule didn't work. When I plug in the camera, no new video device appears as /dev/video. Instead, a set of 5 new files appears in /dev. These are named usbdev5.9_epX, where X is 00, 81, 82, 83 and 84. These 5 files disappear when the camera is unplugged.

Mysterious...

---

