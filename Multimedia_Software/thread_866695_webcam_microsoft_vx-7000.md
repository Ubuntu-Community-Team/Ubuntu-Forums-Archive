---
title: "webcam microsoft vx-7000"
date: 2008-07-22
forum: Multimedia Software
---

### Post by foton2 on 2008-07-22
Hi,
I have webcam microsoft vx-7000 (please don't aske me why I have this f*cking webcam). I would like to use it under xubuntu in skype. If I connect webcam to computer (notebook Lenovo x61s) I get this message:
```

Jul 22 09:50:23 foton2 kernel: [ 1216.884915] Linux video capture interface: v2.00
Jul 22 09:50:23 foton2 kernel: [ 1216.929772] uvcvideo: Found UVC 1.00 device Microsoft<AE> LifeCam VX-7000 (045e:0723)
Jul 22 09:50:23 foton2 kernel: [ 1216.930128] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
Jul 22 09:50:23 foton2 kernel: [ 1216.931985] usbcore: registered new interface driver uvcvideo
Jul 22 09:50:23 foton2 kernel: [ 1216.931991] USB Video Class driver (v0.1.0)
Jul 22 09:50:23 foton2 NetworkManager: <debug> [1216713023.300379] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_723_noserial_if0'). 
Jul 22 09:50:23 foton2 kernel: [ 1217.411760] usbcore: registered new interface driver snd-usb-audio

```

And Skype knows about webcam but when I press test button in video options I get nothing.

```

root@foton2:/home/david# lsusb
Bus 006 Device 004: ID 045e:0723 Microsoft Corp.

```

Xubuntu 8.04
Thank you for any suggestion, David.

---

### Post by loell on 2008-07-22
hi, found this chinese or probably korean blog, [http://planet.nccucs.org/2008/04/26/186/]("http://planet.nccucs.org/2008/04/26/186/")

it would seem that UVC driver SVN version may have an improvement on this webcam.

all the commands in there are mostly straight-forward, hope it helps.

---

### Post by foton2 on 2008-07-22
The requested site did not respond to a connection request and the browser has stopped waiting for a reply.:cry:

---

### Post by loell on 2008-07-22
anyway, i'll just paste the commands, add a little run through,

install subversion

```
sudo apt-get install subversion
```

get uvc svn version

```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
```

get kernel header

```
sudo apt-get install linux-headers-`uname -r`
```


in the uvc MAKEFILE

change

```
INSTALL_MOD_DIR := usb/media
to
INSTALL_MOD_DIR := ubuntu/media/usbvideo
```

compile and install

```
make && make install
```

load the module

```
sudo modprobe -r uvcvideo
sudo modprobe uvcvideo
```

---

### Post by nascimento on 2008-07-30
Thnkx for the posting, dudes...

But... (always a BUT, hun..)

This micro$ft webcam just works in luvcview ( USB Video Class grabber ) from my command line, and not in Amsn, Ekiga, Mercury, camorama - nothing!

I kknow all that apps uses v4l2 (  Video4Linux v2 ) and my webcam is uvc with this driver... but...

I don'thave any ideia right know how to solve it...
Perraps my changing the luvcview-code so that it feeds vloopback and make it work with v4l software?

Any ideias? For now - I'm working on that.

:(

---

### Post by art00r on 2008-10-18
Hi,

same problem here. luvcview works showing good image but nothing in skype, ekiga etc. maybe someone has solved this?

---

### Post by Jexel on 2008-11-05
also having this issue :( has anybody found a solution yet?

---

### Post by jico84 on 2010-02-13
:popcorn:

So much for reviving old posts... but I ran into this while working to get mine running. 

Here's what you need to do:

Go to main menu, System, Preferences, Menus: Applications, Internet, Items: Skype, Properties, and replace the Command with

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

you can do the same with other applications.

Regards,

Jico

---

### Post by kblake007 on 2010-02-27
@ Jico84, 

The command bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype' worked perfectly from the command line.  I replaced that with command in the launcher and that solved the issue.  Thanks for the tip!

---

### Post by thirstyghost on 2010-04-05
Wow!  Using that bash command does make it work, however, it's only the video portion for me.   I have to use a separate plug-in mic since I'm only getting the Pulse Audio option in Skype for audio choices.    Too bad it doesn't work for the vx-6000's which I have a couple of.   But hey, it's better than a few years ago when I tried it.

Ubuntu 9.04
Skype 2.1.0.81 (beta)

UPDATE:  When I tried the test call,the separate mic works fine but in an actual call there's all kinds of static.   After Googling the problem, the fix is to (#1) *uncheck* the option in Skype's Sound Settings about letting Skype automatically adjust your mixer. (#2) And then in Ubuntu's volume mixer, click on Preferences and make sure you select Mic Boost as something that will show up in the Switches tab of the Volume Mixer.   UNCHECK this mic boost and everything should work well.    I got a slight echo like some others have reported, but no more static noise.   You can even verify this by clicking on the mic boost while in a call and it'll bring back the static.    A headset mic seems to work better than a stand alone mic because you can't increase the gain on the mic and it needs to be close to your mouth.

---

