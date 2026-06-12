---
title: "Avermedia M115 T V cards on laptops"
date: 2007-03-30
forum: Multimedia &amp; Video
---

### Post by brazzmonkey on 2007-03-30
AVERMEDIA M115

this hybrid analog/digital TV card is integrated into several laptops, such as ASUS A7J or Acer 9800 series.

i discovered a tutorial that _should_ make this TV card work on ubuntu (edgy) on french wiki here : [http://doc.ubuntu-fr.org/materiel/avermediam115](http://doc.ubuntu-fr.org/materiel/avermediam115)

therefore credits go to its original author skadge.

this is a rough translation of this tutorial ; i followed the instructions it provides and installed the dirvers but i haven't been able to test my TV card yet. 

this TV card is detected as "Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)" in lspci.

 dmesg give the corresponding identifiers : 1461:a836

first you need to get a recent version of Video For Linux (V4L) and compile it from sources. V4L sources are managed with Mercurial versioning system so you need to install this one first :
```
sudo apt-get install mercurial
```

in case you haven't done so already, you should also install your kernel headers in order to be able to compile L4V modules against your current kernel.
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

now get the latest V4L
```
hg clone http://linuxtv.org/hg/~mrechberger/v4l-dvb-kernel-history  ****no longer works, use next line instead****
hg clone http://mcentral.de/hg/~mrec/v4l-dvb-experimental/
```

and compile it
```
cd v4l-dvb-kernel-history/v4l  ****no longer works, use next line instead****
cd v4l-dvb-experimental/
make
sudo make install
```

latest command should have been a "depmod". you should then be able to load new modules :
```
sudo modprobe xc3028-tuner
sudo modprobe -r saa7134_alsa & sudo modprobe -r saa7134
sudo modprobe saa7134 card=104 tuner=71
```

****update****
last line doesn't seem to work any more, i get :
```
WARNING: Error inserting video_buf (/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/video-buf.ko): Invalid module format
```
any hint ??
********

card and tuner settings should roughly be similar to those of AverMedia Cardbus 506
doing a "dmesg", maybe you will see a tuner error, but that doesn't seem to be relevant.
now test it using tvtime
```
sudo apt-get install tvtime
tvtime
```

for additional info regarding television, please search forums or wiki

more info :
[http://linuxtv.org/v4lwiki/index.php/AVerMedia_Cardbus_Hybrid_TV_FM_E506R](http://linuxtv.org/v4lwiki/index.php/AVerMedia_Cardbus_Hybrid_TV_FM_E506R) 
[http://marc.info/?l=linux-video&m=117430070008368&w=2](http://marc.info/?l=linux-video&m=117430070008368&w=2)

---

### Post by chisu on 2007-04-03
Hello, I have an Acer Aspire 5650 with this TV card. Thanks for the information. It works correctly. The only problem that I have is that when I restart the computer TVtime does not recognize the video card capture. Then I have to repeat the last three steps in order that it returns to work again. You can say to me for that this happens, I am new in ubuntu and think that it is incredible.

---

### Post by brazzmonkey on 2007-04-04
hi there,
glad it works for you !
from what you wrote, it looks like you need to load the proper modules at boot time, therefore adding the following to /etc/modules shoud do it. use nano for instance :
```
$ sudo nano -w /etc/modules
```
add this
```
# tvtuner
xc3028-tuner
saa7134 card=104 tuner=71
```
save and exit nano (<Ctrl+X>  then <Y> then <Enter>). it should work for you next time you reboot.

in order to get it working without rebooting, simply run
```
$ sudo modprobe xc3028-tuner 
$ modprobe saa7134 card=104 tuner=71
```

---

### Post by chisu on 2007-04-09
Hello and thanks. I have done what you said to me but it continues without working. Only it works when I write on terminal:
sudo modprobe xc3028-tuner
sudo modprobe -r saa7134_alsa & sudo modprobe -r saa7134
sudo modprobe saa7134 card=104 tuner=71

The first time when i run " sudo modprobe -r saa7134_alsa & sudo modprobe -r saa7134" command line displays:

FATAL: Module saa7134 is in use.

But if i re-run the same command the second time it displays Ok.

[3] 5673
[2]   Done                    sudo modprobe -r saa7134_alsa
[3]-  Done                    sudo modprobe -r saa7134_alsa

I have no idea because do it.

---

### Post by Nano on 2007-04-20
jeez, I have an Acer 9814 at home. I'll try it out as soon as I get there and post the results.
Thanks for bumping up the hope! :D

---

### Post by Nano on 2007-04-23
> 
  CC [M]  /home/mariano/Desktop/v4l-dvb-kernel-history/v4l/flexcop-pci.o
/home/mariano/Desktop/v4l-dvb-kernel-history/v4l/flexcop-pci.c: In function 'flexcop_pci_irq_check_work':
/home/mariano/Desktop/v4l-dvb-kernel-history/v4l/flexcop-pci.c:119: warning: passing argument 1 of 'schedule_delayed_work' from incompatible pointer type
/home/mariano/Desktop/v4l-dvb-kernel-history/v4l/flexcop-pci.c: In function 'flexcop_pci_stream_control':
/home/mariano/Desktop/v4l-dvb-kernel-history/v4l/flexcop-pci.c:226: warning: passing argument 1 of 'schedule_delayed_work' from incompatible pointer type
/home/mariano/Desktop/v4l-dvb-kernel-history/v4l/flexcop-pci.c:229: warning: passing argument 1 of 'cancel_delayed_work' from incompatible pointer type
/home/mariano/Desktop/v4l-dvb-kernel-history/v4l/flexcop-pci.c:378:71: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/mariano/Desktop/v4l-dvb-kernel-history/v4l/flexcop-pci.c: In function 'flexcop_pci_probe':
/home/mariano/Desktop/v4l-dvb-kernel-history/v4l/flexcop-pci.c:378: error: 'INIT_WORK' undeclared (first use in this function)
/home/mariano/Desktop/v4l-dvb-kernel-history/v4l/flexcop-pci.c:378: error: (Each undeclared identifier is reported only once
/home/mariano/Desktop/v4l-dvb-kernel-history/v4l/flexcop-pci.c:378: error: for each function it appears in.)
make[2]: *** [/home/mariano/Desktop/v4l-dvb-kernel-history/v4l/flexcop-pci.o] Error 1
make[1]: *** [_module_/home/mariano/Desktop/v4l-dvb-kernel-history/v4l] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2


It blocks there :(

Any tips?

---

### Post by delojo on 2007-04-25
I have the same problem :(

My processor is Centrino Duo.

Can somebody help us???

Thank you!!

---

### Post by brazzmonkey on 2007-04-25
same here... something changed with feisty (kernel ?). i don't have any idea yet.

---

### Post by Nano on 2007-04-27
Jeez, somehow I have to get this working.
Any help?

---

### Post by kaiza on 2007-05-05
And same here. Well, at least I'm not the ony one...

k.

---

### Post by Newlad on 2007-05-10
also too

---

### Post by Nano on 2007-05-10
I'm afraid this problem goes beyond my knowledge, how could we solve it?
Is it a matter of kernel headers?

---

### Post by brazzmonkey on 2007-05-10
try to get the files from the following url :
```
 hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-stable
```

or maybe, try :
```
hg clone http://mcentral.de/hg/~mrec/v4l-dvb-experimental
```
and let me know...

of course, do this at your own risk.

---

### Post by kaiza on 2007-05-11
I tried v4l-dvb-stable and I can compile it, only it does not seem to contain the tuner module: 

```
kaiza@kaiza-laptop:~/v4l-dvb-stable/v4l$ sudo modprobe xc3028-tuner
FATAL: Module xc3028_tuner not found.

```

TvTime loads, but obviously it doesn't detect any signal.

k.

---

### Post by Nano on 2007-05-16
> **brazzmonkey said:**
> try to get the files from the following url :
```
 hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-stable
```

or maybe, try :
```
hg clone http://mcentral.de/hg/~mrec/v4l-dvb-experimental
```
and let me know...

of course, do this at your own risk.


Hi there, the second repo worked but I couldn't load the final module:
```

mariano@nanodromo:$ sudo modprobe saa7134 card=104 tuner=71
FATAL: Error inserting saa7134 (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for saa7134


```

---

### Post by xevilstar on 2007-07-06
v4l-dvb-experimental compiles in a whiff and the modules load fine but... tvtime stil complains about no signal......
solutions ?

---

### Post by xevilstar on 2007-07-06
opps found something in the dmesg
saa7133[0]/dvb: frontend initialization failed
I have installed the v4l-firmware version 4
what is happening ?:confused:](*,):(

---

### Post by xevilstar on 2007-07-07
no signal



Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /root/.tvtime/tvtime.xml
cpuinfo: CPU Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz, family 6, model 15, stepping 6.
cpuinfo: CPU measured at 1828.718MHz.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 70200000
xfullscreen: Single-head detected, pixel aspect will be calculated.
xfullscreen: Pixel aspect ratio on the primary head is: 1/1 == 1.00.
xfullscreen: Using the XFree86-VidModeExtension to calculate fullscreen size.
xfullscreen: Fullscreen to 0,0 with size 1680x1050.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is KWin and is EWMH compliant.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 275: NV17 Video Texture.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /root/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'saa7134', card 'Avermedia M115' (bus PCI:0000:09:04.0).
videoinput: Version is 526, capabilities 5010015.
videoinput: Maximum input width: 720 pixels.
tvtime: Sampling input at 720 pixels per scanline.
mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (66).
xcommon: Window fully obscured, marking window as hidden (66).
xcommon: Window made visible, marking window as visible (75).
tvtime: Cleaning up.
Thank you for using tvtime.

---

### Post by stingksl on 2007-07-22
Thanks everyone for the information.

I am using Acer Aspire 5510 notebook which also uses the Avermedia M115 card.

I followed instruction and finally go TV with sound working properly.
I am new to ubuntu and not familiar with linux. 
so hope this information is useful.

Essentially I followed the instruction on this link
[http://mcentral.de/wiki/index.php/AverMedia_Cardbus_Hybrid_TV_FM_E506R](http://mcentral.de/wiki/index.php/AverMedia_Cardbus_Hybrid_TV_FM_E506R)

Used the firmware_v3 from this link
[http://mcentral.de/firmware/](http://mcentral.de/firmware/)

At this stage the system was able to detect that card=119

I was able to get picture but no sound, until the command below was done
sox -r 16000 -w -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

hope it helps...

now to try to get FM radio to work.

---

### Post by stingksl on 2007-07-22
hmmm.....

after reboot, i lost sound again.

then got it back by

sudo rmmod saa7134_alsa
sudo rmmod saa7134
sudo modprobe saa7134 card=119 alsa=1
sox -r 16000 -w -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

how to make it permanent ?

---

### Post by stingksl on 2007-07-23
hmmmmm........ just made a discovery.

all i needed to do was use this command
sox -r 16000 -w -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

and then switched the audio type 
For instance, i was using PAL-BG; So I cycled the choices and finally end up with PAL-BG again
This made sound work

---

### Post by brazzmonkey on 2008-06-18
anyone got his tv card working on hardy ? someone told me my tutorial no longer works, and i'm unable to look for a solution atm.

(i updated the tutorial to take new repository into account - see first post - but i get a warning when loading saa7134 with options, i suppose these options are not supported any more...)

thanks.

---

### Post by Zorael on 2008-06-19
I've had *some* success but it's still not working.

The v4l build available over at [http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/) compiles and runs without error messages about missing symbols if you have a 2.6.25+ kernel. It will autodetect the card as an Avermedia M115 and you won't need to define any card= or tuner= options. Further, if you compile and run the 2.6.26-rc6 kernel, the included v4l in the kernel source, while a bit older than the one available at that linuxtv.org repository, detects it automatically as well.

Regardless, it does not work. It doesn't detect the DVB-T capabilities of the card and the tuner module doesn't work. As per suggestions from some friendly developers over at #linuxtv on irc.freenode.net, I patched the source file for the saa7134 module to hopefully make it dvb-aware, but no luck. Even so, we'd need the tuner to work.

The mercurial repository at [http://mcentral.de/hg/~mrec/em28xx-new/](http://mcentral.de/hg/~mrec/em28xx-new/) is fresh and contains the source for a hopefully newer build of dvb-xc2028 (the Xevie xc2028/xc3028 tuner module), but I can't get it to compile. I've sent a private message to the developer who maintains it and I'm waiting to see if he has the time to help.

So both the saa7134 and the dvb-xc2028 modules need to be fixed for this to work; saa7134 to get dvb working and dvb-xc2028 to, well, just work without errors. That you had gotten it to work by defining it as an Avermedia Cardbus 507 is promising, but does that card even have DVB-T support?

Noteworthy is that dvb-xc2028 won't run at all unless you extract a firmware from a Hauppage Windows driver and put it in /lib/firmware, and it's exactly that firmware that the module is complaining about. If you don't have it, it spams in dmesg that it can't find it. If you run a semi-new build, such as the one in the 2.6.26-rc6 kernel, it spams dmesg when it tries to tune, stating that it's starting to read the firmware. When it does this, the system "micro-hangs" where the mouse doesn't move for a second every four or so. If you have the super-new build from the linuxtv.org repository, it complains about there occuring errors when reading the firmware file. So perhaps just a new firmware would do the trick, but I've no idea where to get one of those.

---

