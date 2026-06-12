---
title: "Help me make my webcam working"
date: 2011-11-30
forum: Multimedia Software
---

### Post by dumitru on 2011-11-30
Hi guys,

Help me make my webcam working  on Ubuntu 11.10 (64-bit). 

The webcam: "Gear Head Quick 5.0 MP WebCam w/ 720P HD Video"
It is not working both in Cheese and Skype. But it works in Windows.

lsusb gives:
[FONT=Courier New]Bus 002 Device 006: ID 0ac8:3420 Z-Star Microelectronics Corp. Venus USB2.0 Camera[/FONT]

I think that the system sees it. When it is disconnected, Cheese gives me "No device found". When I connect the camera it's just the black screen  in Cheese and all the menus are inactive.

I'm not and advanced Linux user and I just don't know what to do.

---

### Post by papibe on 2011-12-01
Hi dumitru.

Have you try the LD_PRELOAD trick? Read about it [here]("http://ubuntuforums.org/showthread.php?t=1469720").

Hope it helps.
Regards.

---

### Post by no2498 on 2011-12-01
open a terminal type dmesg click enter
after it stops click close retry cheese

---

### Post by dumitru on 2011-12-01
I tried to install "video4linux", but id didn't help as well. When it starts, it gives the following message: 
"Unable to get menu item for Exposure, Auto, index=0      Will use Unknown"
"Unable to get menu item for Exposure, Auto, index=2      Will use Unknown"

---

### Post by dumitru on 2011-12-01
> **papibe said:**
> Hi dumitru.

Have you try the LD_PRELOAD trick? Read about it [here]("http://ubuntuforums.org/showthread.php?t=1469720").

Hope it helps.
Regards.


Thank you, but I think the problem is how my system detects the webcam, not just Skype.
I've inserted the line "alias skype='LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype' but nothing happened.

---

### Post by dumitru on 2011-12-01
> **no2498 said:**
> open a terminal type dmesg click enter
after it stops click close retry cheese

I did this, nothing has changed.

---

### Post by no2498 on 2011-12-02
install guvcview
rerun dmesg
click close
try it in guvcview

---

### Post by kensum on 2011-12-02
When you start skype, right click the skype icon and choose options. pick video devices. Is your camera listed as a UVC device. If it is not, then you will need to find the correct driver.

---

### Post by dumitru on 2011-12-03
> **no2498 said:**
> install guvcview
rerun dmesg
click close
try it in guvcview

Did everything. Guvcview detected my webcam "Devices: Venus USB2.0 Camera" but the screen is black, the same as with Cheese.
I tried my webcam in Windows again and it works.

PS: By the way, "guvcview" seems to be more user-friendly than "Cheese"

---

### Post by dumitru on 2011-12-03
> **kensum said:**
> When you start skype, right click the skype icon and choose options. pick video devices. Is your camera listed as a UVC device. If it is not, then you will need to find the correct driver.

My camera is in the list - Venus USB2.0 Camera (/dev/video0), but when I press Test button, the screen is black.

---

### Post by no2498 on 2011-12-04
thinking this may be the auto gain in guvcview
see if you can turn it off

---

### Post by dumitru on 2011-12-04
Nobody can help me?

---

### Post by no2498 on 2011-12-05
look in your system/preferences multimedia systems selector open it
click video wright down what plugin is up
change the plugin to something else use the bottom test button
should see your cam come on

---

### Post by dumitru on 2011-12-05
> **no2498 said:**
> look in your system/preferences multimedia systems selector open it
click video wright down what plugin is up
change the plugin to something else use the bottom test button
should see your cam come on

OK, how can I access "Multimedia Systems Selector" in Ubuntu 11.10?
There is System Settings in Ubuntu 11.10 and no System/Preferences etc.

---

### Post by step21 on 2011-12-05
@no2498 Hey, it's nice that you try to help people but just running dmesg in of itself will just display some system output, it can't and won't change anything. So maybe it would be better if you would not advocate that anymore.

---

### Post by no2498 on 2011-12-06
ive seen dmesg  load a cam grabber on my two computer's sorry

dumitru im still using 10.04 so im no help for that way
try this in a terminal
type 
gstreamer-properties click enter

click video

---

### Post by dumitru on 2011-12-14
> **no2498 said:**
> ive seen dmesg  load a cam grabber on my two computer's sorry

dumitru im still using 10.04 so im no help for that way
try this in a terminal
type 
gstreamer-properties click enter

click video

no2498, thanks for trying to help me. I did what you said. I tried different settings but nothing happened.

---

### Post by TiberiusT on 2011-12-14
[FONT=Verdana][SIZE=2]long shot but u never know... Had a similar sounding problem with a Syntek webcam the other day on an SL300 laptop - everything seemed fine except I just got a black screen. After tonnes of lsusb/dmesg...ing  I eventually did this and it worked...but doan ask me why

[/SIZE][/FONT] [FONT=Verdana][SIZE=2][COLOR=#000000]unload the driver module: [/COLOR][COLOR=#000000]*sudo modprobe -r uvcvideo*[/COLOR]
[COLOR=#000000]Then reload with the correct parameter: [/COLOR][COLOR=#000000]*sudo modprobe uvcvideo quirks=16*[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]

and if that works then make it permanent:
[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]
edit the options file (u might have to create one) in:[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]*cd /etc/modprobe.d*[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]*gksudo gedit options*[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]
At the bottom (or just add it if empty) add the following line:[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]*options uvcvideo quirks=16*[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]
and save, reboot and done![/COLOR][/SIZE][/FONT]
[COLOR=#000000][FONT=Calibri]
T

[/FONT][/COLOR]

---

### Post by dumitru on 2011-12-14
> **TiberiusT said:**
> [FONT=Verdana][SIZE=2]long shot but u never know... Had a similar sounding problem with a Syntek webcam the other day on an SL300 laptop - everything seemed fine except I just got a black screen. After tonnes of lsusb/dmesg...ing  I eventually did this and it worked...but doan ask me why

[/SIZE][/FONT] [FONT=Verdana][SIZE=2][COLOR=#000000]unload the driver module: [/COLOR][COLOR=#000000]*sudo modprobe -r uvcvideo*[/COLOR]
[COLOR=#000000]Then reload with the correct parameter: [/COLOR][COLOR=#000000]*sudo modprobe uvcvideo quirks=16*[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]

and if that works then make it permanent:
[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]
edit the options file (u might have to create one) in:[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]*cd /etc/modprobe.d*[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]*gksudo gedit options*[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]
At the bottom (or just add it if empty) add the following line:[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]*options uvcvideo quirks=16*[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]
and save, reboot and done![/COLOR][/SIZE][/FONT]
[COLOR=#000000][FONT=Calibri]
T

[/FONT][/COLOR]

Wow, man! I was so glad when I could see the image captured by my webcam, but it is only a static image and only when I turn on Cheese or Skype.
I think we are close to the solution. It's almost working, maybe it needs another line or parameter?!

---

### Post by TiberiusT on 2011-12-15
> **dumitru said:**
> 
I think we are close to the solution. It's almost working, maybe it needs another line or parameter?!

Groan! Video works fine in the SL300 I used that on. I couldn't find any details on what the quirks settings actually do and the guy who resolved it that way didn't either. Maybe someone else? 


T

---

### Post by Dareth on 2012-02-22
```
sudo modprobe uvcvideo quirks=64
```

Try it like this. I have the same webcam, and this is the most usable it gets. I hope you don't like using Cheese. It worked perfectly on 32-bit Ubuntu, but not 64-bit for some reason.

---

### Post by TiberiusT on 2012-02-23
@Dareth

A ha! Another mysterious quirks=xx :)

Do u know what this setting does/means? If u have any further info cud yu post a link to it, since I cannot find anything abt it...

Tks
T

---

### Post by Dareth on 2012-02-23
> **TiberiusT said:**
> @Dareth

A ha! Another mysterious quirks=xx :)

Do u know what this setting does/means? If u have any further info cud yu post a link to it, since I cannot find anything abt it...

Tks
T

Nope, I found it through trial and error, using the 2^n sequence of numbers. I'm just happy I can do hangouts and video chat on Google+. I haven't tested Skype yet, but I think it will work for that too.

---

### Post by dumitru on 2012-02-25
> **Dareth said:**
> ```
sudo modprobe uvcvideo quirks=64
```Try it like this. I have the same webcam, and this is the most usable it gets. I hope you don't like using Cheese. It worked perfectly on 32-bit Ubuntu, but not 64-bit for some reason.

After I type-in this command I receive the following message:  *WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.*

My camera is not working in both Cheese and Skype. When I start my webcam in these applications it just shots the first frame of the image and that's it. This was possible after I did "options uvcvideo quirks=16" on December 15 last year. Since then I couldn't do anything.  :(

By the way, I work in Ubuntu 11.10, 64 bit.

---

### Post by jrela2000 on 2012-03-15
Don't want to impose on this thread too much, but I am seeking resolution for the same issue with the same camera running 10.04.

SO I will be checking back in to see how this all turns out.

Would like to do some G+ hangouts:
[IMG]https://lh5.googleusercontent.com/-3lHQPElvdCA/T2JlZw87p7I/AAAAAAAACeg/Q3t3EuaMr-4/s494/hangout.png[/IMG]

---

### Post by BicyclerBoy on 2012-03-15
Just in case..Make sure your cam is directly plugged into USB2 port.
The USB id 
0ac8:3420  Venus USB 2.0 Camera (Tevion MD 85872 and Minoru3D) Vimicro
is listed as supported with the footnote that:
Resolutions below 640x480 might only work at the full 30fps frame rate.
[http://www.ideasonboard.org/uvc/#footnote-8](http://www.ideasonboard.org/uvc/#footnote-8)

Not sure it will help you or me but from the above website...
To increase the debug info in system log:
$ sudo echo 0xffff > /sys/module/uvcvideo/parameters/trace

run qv4l2, guvcview and luvcview for a couple of seconds..

Stop the debug stuff:
$ sudo echo 0 > /sys/module/uvcvideo/parameters/trace

Save the syslog stuff:
dmesg > uvcvideo-dmesg.log

You could try building the latest driver from linuxtv.org..

You will find the UVC quirks listed in uvc/uvcvideo.h (kernel <=2.6.42) or linux/uvcvideo.h..

---

### Post by jrela2000 on 2012-03-16
taking a cue from the post above, I opened Cheese and change the resolution to 320X240 and it works perfectly...... for Cheese.

Anywhere else that doesn't really give the option to adjust the resolution is still a problem.....

Does Ubuntu have something like Media Encoder or even Webcam max that will let you adjust you camera settings for broadcasting?

---

### Post by BicyclerBoy on 2012-03-16
qv4l2, guvcview and luvcview

Have only used guvcview, it seems to be able to configure all possible settings on my webcam..
I un-installed cheese long ago...

Not sure what you mean by broadcasting.
You can use ffmpeg to capture from v4l2 & believe you can stream the output.
(no actual example)
[http://ffmpeg.org/ffmpeg.html#toc-video4linux-and-video4linux2](http://ffmpeg.org/ffmpeg.html#toc-video4linux-and-video4linux2)
ffmpeg -f video4linux2 -i /dev/video0 out.mpeg

---

### Post by jrela2000 on 2012-03-16
ok this is what worked for me.

I downloaded webcam studio.

it recognized the Venus 2.0 stuff.

It set the camera to 320X240 @ 15FPS

Adjusting the settings will shut the program down.

I can do all the online streaming stuff now (Ustream, Stickam Justin TV, and Google Hangouts)

Still cannot use for Skype, but I don't really care about that.

[IMG]https://lh4.googleusercontent.com/-0PucQxRolHs/T2Om9LGbkdI/AAAAAAAACfQ/7QoEKRT5cEM/s456/working.png[/IMG]

---

### Post by BicyclerBoy on 2012-03-16
Who's that handsome dude..

I think skype needs the exported variable LD_PRELOAD library trick so it does not use the default video4linux2 api library.

---

### Post by omerori on 2012-04-29
> **TiberiusT said:**
> [FONT=Verdana][SIZE=2]long shot but u never know... Had a similar sounding problem with a Syntek webcam the other day on an SL300 laptop - everything seemed fine except I just got a black screen. After tonnes of lsusb/dmesg...ing  I eventually did this and it worked...but doan ask me why

[/SIZE][/FONT] [FONT=Verdana][SIZE=2][COLOR=#000000]unload the driver module: [/COLOR][COLOR=#000000]*sudo modprobe -r uvcvideo*[/COLOR]
[COLOR=#000000]Then reload with the correct parameter: [/COLOR][COLOR=#000000]*sudo modprobe uvcvideo quirks=16*[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]

and if that works then make it permanent:
[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]
edit the options file (u might have to create one) in:[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]*cd /etc/modprobe.d*[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]*gksudo gedit options*[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]
At the bottom (or just add it if empty) add the following line:[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]*options uvcvideo quirks=16*[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]
and save, reboot and done![/COLOR][/SIZE][/FONT]
[COLOR=#000000][FONT=Calibri]
T

[/FONT][/COLOR]

Thank you so much Tiberius! That really helped!

---

