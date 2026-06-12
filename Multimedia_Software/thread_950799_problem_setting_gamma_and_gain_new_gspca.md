---
title: "problem setting gamma and gain new gspca"
date: 2008-10-17
forum: Multimedia Software
---

### Post by micheleo on 2008-10-17
Hi guys!

I have this problem setting the gamma and gain parameters for the new gspca module: 

with 8.04 everything went right, thanks also to this guide for the dark image problem: [http://forum.skype.com/index.php?showtopic=106357](http://forum.skype.com/index.php?showtopic=106357)

after upgrading to 8.10 the image of my webcam ( 046d:092f Logitech, Inc. QuickCam Express Plus ) is again very dark and the previous guide does not work anymore. 

some notes:
/sys/modules/gspca does not exist anymore, in its place I find  /sys/module/gspca_spca561/ and /sys/module/gspca_main/  and in these directories I can't do the thing suggested in the guide ( setting the parameters ) because it seems like I don't have write permission on it even if I am root:

```
 /sys/module/gspca_main/parameters/GGreen: No such file or directory
```

is it mounted readonly now? :confused:

if I try to add the options in /etc/modprobe.d/options at modprobing ( I tried on both gspca_main and gspca_spca561 ) it complains that these options are not valid.

any clue?

Thank you guys!

Michele :)

---

### Post by otc242 on 2008-10-17
have you tried "autoexpo" module option?

p.s. worst case scenario - you can set any option (override default value) directly in source file of module.

---

### Post by micheleo on 2008-10-17
> **otc242 said:**
> have you tried "autoexpo" module option?

p.s. worst case scenario - you can set any option (override default value) directly in source file of module.

thanks for replying!

unfortunately I get the same:

```
 gspca_main: Unknown parameter `autoexpo'
```

and compiling is not possible because there's an open bug that prevents to do it as far as I know: 
[https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/273727](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/273727)

any suggestion? :(

---

### Post by otc242 on 2008-10-17
looks like gspca is now part of the kernel and that could be the reason of these problems - so, compiling is not needed. from what i've read, it should work properly with latest versions (and of course with final version of 8.10).

anyway, back to problem - try this:
```
modinfo -F parm gspca
```

that should give all available module parameters and their description - maybe they are renamed now?

---

### Post by micheleo on 2008-10-18
thanks again for replying.

```

michele@micheleo:~$ modinfo -F parm gspca_main
debug:Debug (bit) 0x01:error 0x02:probe 0x04:config 0x08:stream 0x10:frame 0x20:packet 0x40:USBin 0x80:USBout 0x0100: v4l2

```

gspca_spc561 does not return anything.

---

### Post by otc242 on 2008-10-18
gspca_main? this is what i get (on hardy, still hadn't had time to get intrepid):

```
modinfo -F parm gspca

force_sensor_id:Forced assigning ID sensor (Zc03xx only). Dangerous, only for experts !!!
force_gamma_id:Forced assigning ID of contrast settings (0=default,1,2,3) Zc03xx only
lightfreq:Light frequency banding filter. Set to 50 or 60 Hz, or 0 for NoFlicker (default=50) Zc03xx only
usbgrabber:Is a usb grabber 0x0733:0x0430 ? (default 1) 
compress:Turn on/off compression (not functional yet)
GGreen:Gain Green setting range 0 to 512 /256 
GBlue:Gain Blue setting range 0 to 512 /256 
GRed:Gain Red setting range 0 to 512 /256 
OffGreen:OffGreen setting range -128 to 128
OffBlue:OffBlue setting range -128 to 128
OffRed:OffRed setting range -128 to 128
gamma:gamma setting range 0 to 7 3-> gamma=1
force_rgb:Read RGB instead of BGR
debug:Debug level: 0=none, 1=init/detection, 2=warning, 3=config/control, 4=function call, 5=max
autoexpo:Enable/Disable auto exposure (default=1: enabled) (PC-CAM 600/Zc03xx/spca561a/Etoms Only !!!)
```

i hope this is only a "beta" related thing and that it will be resolved until final release :(

---

### Post by micheleo on 2008-10-18
yes, I really hope it! 
thank you very much for your kind help!
see you! :)

---

### Post by otc242 on 2008-10-18
you're very welcome :)

i think it will all work well in final version - if not, i'll have the same problem and we'll be on this thread again until we find a fix :D

---

### Post by tyk on 2008-10-20
same problem here on intrepid. webcam is a logitech something or the other.. image was fine on hardy.
cheers.

---

### Post by otc242 on 2008-10-20
mine is logitech too: quickcam for notebooks, new version (hardware id via lsusb is 046d:08dd)

---

### Post by otc242 on 2008-11-01
ok, i've hit the wall too... there are no more module parameters, the picture is pitch black (tried with cheese), skype shows black picture or crashes...

however, ekiga works perfectly with video plugin - v4l2

---

### Post by wirespot on 2008-11-13
To fix the too dark image problem, install package v4l2ucp and run it on the camera device:

```
v4l2ucp /dev/video1
```

Crank up the exposure, then press the  "update" button next to it. The setting will be kept in V4L v1 applications as well (mplayer, skype etc.)

Haven't yet tested whether the setting is kept after reboot.
LE: It isn't. :( *sigh* And the tool is graphical, with no means of storing and restoring v4l2 device settings from command line, which would've allowed fixing the issue from startup scripts. Still, better than nothing.

Fix found reading this thread:
[http://lists-archives.org/video4linux/24830-gspca-v2-vs-v1-webcam-picture-very-dark.html](http://lists-archives.org/video4linux/24830-gspca-v2-vs-v1-webcam-picture-very-dark.html)

---

### Post by wirespot on 2008-11-15
So, I got angry enough to write a small program that will work from the command line and set the exposure for a V4L2 device to whatever you want.

Credits: source code examples from the following websites.
[http://www.thedirks.org/v4l2/](http://www.thedirks.org/v4l2/)
[http://www.linuxtv.org/downloads/video4linux/API/V4L2_API/spec-single/v4l2.html](http://www.linuxtv.org/downloads/video4linux/API/V4L2_API/spec-single/v4l2.html)

Source code is attached. How to use:

1. Unpack the file (I had to gzip it to be accepted as attachment):

```
gunzip set_cam_exp.c.gz
```

2. You need the gcc compiler installed. Installing "build-essential" will probably do it.

```
sudo apt-get install build-essential
```

3. Compile the source code:

```
gcc set_cam_exp.c -o set_cam_exp
```

4. Enjoy. If you simply run the program it will tell you how to use it. Basically, you need to pass the device as the 1st parameter and the exposure as the 2nd. It will tell you if the device is not there, isn't a V4L2 device, or if setting the exposure failed for some reason (and why), such as too big a value. Example:

```
./set_cam_exp /dev/video0 2000
```

**Remember: the higher the exposure, the lower the fps.**

That's about it. Place the executable somewhere you won't forget about it and call it from the startup scripts. /etc/rc.local seems like a good place. Just make sure you call it with the full path, ie. if you put it in /home/john/bin/set_cam_exp then use that exact entire path to call it.

It's perfectly possible to write a program to set any of the things we used to set as kernel module params. But I won't write it, I don't technically know how to program in C :) and even this small program was a stretch for me. Besides, setting the exposure is good enough for me. Feel free to expand upon it.

I'm guessing the reason the kernel devs took those params out of the kernel module is because there's now a perfectly good userland API anybody can use to control any V4L2 device. My little program and v4l2ucp are perfect examples. So what I'm saying is, don't expect the kernel module params to ever come back, but instead hope that people write more programs like these two.

---

### Post by guayusa on 2008-11-18
Anyone found the solution yet to change the gspca parameters in Intrepid?

There is a wide range of tutorials and how-tos for setting the parameters in 8.04 Hardy, but they dont' work in 8.10 Intrepid :(

---

### Post by wirespot on 2008-11-19
Between the releases, Ubuntu devs switched from the old third-party gspca drivers to the new drivers, that now come with the kernel. It's a very good thing to have the drivers come with the vanilla kernel because you're guaranteed they'll always be there and work, with all new kernel releases. On the downside, they don't yet have all the parameters that the old drivers had. See above in my post for a possible reason why I think they might never will.

Just in case you're wondering, you can still compile and use the old drivers. But you'll need a patch that's floating somewhere around this forum to make them compile with kernel 2.6.27+.

(I'm assuming you read my post above about v4l2ucp and set_cam_exp and they don't do what you want.)

---

### Post by guayusa on 2008-11-19
I see.

Thanks. And I missed the second page of the the thread, sorry. Didn't see it until I had posted. Ooops :)

Anyway,

Pheeew. It is getting ever more stressful being an Ubuntu (or GNU/Linux user in general) - every distribution is a totally new paradigm and all you thought you knew, all you could do, changes - and if you don't upgrade you will be stuck with ancient Firefox and OpenOffice etc.

Slowly getting on my nerves and certainly making it _very_ difficult to advocate or encourage Winbloat users to migrate.

Also, nothing personal, and I am very grateful that you coded this little thing, but I am, then, left with having to trust some code posted in a forum and which no one has given any feedback on. It is simply not a sustainable development for the community.

---

### Post by guayusa on 2008-11-19
> **wirespot said:**
> 
**Remember: the higher the exposure, the lower the fps.**



Ok, thanks a lot for this - works a charm!

The procedure is exactly as described. It takes only 2-3 minutes to download, unpack, install build-essentials (depending on your bandwidth of course), compile and run. And it works. 

And frame rate drops dramatically, - for me setting it at a 1000 is enough and the framerate is still fairly OK:

./set_cam_exp /dev/video0 1000


I also had a quick look at the code of this little programme - ¡¡I AM NOT A PGORAMMER!! - and there is nothing in there that looks dodgy :)

Should be safe to use........

:popcorn:

---

### Post by wirespot on 2008-11-19
I kinda like the way it forces you to adapt, keeps me fresh (I'm on Debian unstable myself, by choice). :) But in all fairness, Intrepid is not a LTS release and there are bound to be some quirks. Bleeding edge comes with caveats, don't upgrade unless you're willing to put up with them, and so on.

I'm betting these issues will be smoothed out at some point and a future LTS won't give users these headaches.

Good thing you don't trust code you don't understand, that's a very safe approach. I see some positive feedback has already been given. I've also added the code to [bug 287336](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287336) so you can also look for feedback there.

---

### Post by zarap on 2008-11-25
my logitech 046d:092f was working from feisty to hardy out of the box.
Stopped working after installing ubuntu 8.10
I got it kind of working with installing libv4l-0.5.0 ([http://ubuntuforums.org/showthread.php?t=966105](http://ubuntuforums.org/showthread.php?t=966105))
But the controls for brightness, contrast ... don't work in any program.
After compiling "set_cam_exp" I can adjust the cam with even a better result as it was in hardy. Thank's a lot for that

---

### Post by hrimhari on 2009-04-18
Well, I wanted to improve the performance of my Chicony built-in while outdoors, so I decided to try the little tool by wirespot. I got some compilation problems for missing includes that I could only figure out after activating -Wall. Which were:

sys/ioctl.h
unistd.h

In the end, my webcam did not support exposure, so I decided to figure out what it DID support. Then I modified the tool to probe for all "known" V4L2 controls and report which were supported, and finally to allow me to set any parameter.

The result is two "generic" tools based on the first one by wirespot, which I now attach.

Usability is pretty similar:

gcc probe_cam.c -o probe_cam
gcc set_cam_parm.c -o set_cam_parm

Then, to probe, I do:

./probe_cam | fgrep Support

To set, say, contrast:

./set_cam_parm V4L2_CID_CONTRAST 10

You'll have to try the parameters out with a variety of values. I didn't look to know how to figure the supported range.

One nice thing is that I was able to set the parameters while the webcam was in use by Cheese. Unfortunately, this webcam of mine is great indoors but sucks outdoors. It's too sensitive to light.

Good luck!
~hri

---

### Post by 1heinz on 2009-07-07
Hi,

nice small utilities ;-)
I tried them with my Philips Webcam (sonixj 0471:0330 Philips SPC 710NC)
and Ubunutu 9.04.

If You need something with a GUI you can try v4l2ucp.
I just downloaded it from ([http://sourceforge.net/projects/v4l2ucp]("http://sourceforge.net/projects/v4l2ucp/")/),
After 'configure; make; make install' everything worked out of the box...

Heinz.

---

### Post by wirespot on 2009-07-07
I think you can find it in the Ubuntu repositories, no need to install from source. Package v4l2ucp.

---

### Post by Cyan_Fire on 2009-10-08
[This search]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=v4l2ucp") seems to indicate it will be available in Karmic, but it's not a package for Jaunty as far as I could find. I compiled it from sf.net, though, just needed to install qt3-dev-tools.

---

