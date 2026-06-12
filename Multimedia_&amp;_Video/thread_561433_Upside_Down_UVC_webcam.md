---
title: "Upside Down UVC webcam"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by cristiantm on 2007-09-27
Ie bought myself a W7S notebook... And I decided to put Ubuntu on it. Because of the new hardware, I updated to latest Gutsy and except some usual problems of any unstable Linux version,  It is working very very fine... except the webcam. 

This notebook have a 1,3 WebCam that i realy want to use. But all programs or cant see the webcam, or show the image upside down:

 * AMSN: Shows a very good image, but upside down;
 * Ekiga: since last update i have some problems with it crashing... but it was detecting a non-working UVC 1,3 webcam.
 * Camorama: shows an "cannot connect to /dev/video0" device
 * luvcvideo: works with "-f yuv" parameters, but is a king of ugly image (much worse than on amsn) and is upside down too...

Someone can help me on that? My main objective is to use it with amsn, at least... Or with anyprogram that can do webcam streaming... But showing the image correctly. I am almost thinking that asus sent me a notebook with a inverted webcam, but i dont want to install Windows to test that :lolflag: 

Some info that may help:

lsusb:
> Bus 006 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd 


./luvcview -f yuv -l
> 
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Available controls of device 'Camera 1' (Type 1=Integer 2=Boolean 3=Menu 4=Button)
V4L2_CID_BASE         (predefined controls):
 index:9963776    name:Brightness                       type:1 min:-128  max:127   step:1     def:0     now:-14 
 index:9963777    name:Contrast                         type:1 min:0     max:100   step:1     def:0     now:0 
 index:9963778    name:Saturation                       type:1 min:0     max:100   step:1     def:0     now:3 
 index:9963779    name:Hue                              type:1 min:-20   max:20    step:1     def:0     now:0 
 index:9963792    name:Gamma                            type:1 min:1     max:500   step:1     def:1     now:5 
V4L2_CID_PRIVATE_BASE (driver specific controls):
 index:134217728  name:Backlight Compensation           type:1 min:0     max:1     step:1     def:0     now:0 
 index:134217729  name:Power Line Frequency             type:3 min:0     max:2     step:1     def:2     now:2 
  Menu items:
  index:0 name:Disabled
  index:1 name:50 Hz
  index:2 name:60 Hz
 index:134217730  name:Sharpness                        type:1 min:0     max:6     step:1     def:3     now:3

---

### Post by carl.alv on 2007-10-15
I see the image upside down on camorama :(, does anyone knows how to solve this?

---

### Post by daynah on 2007-11-09
Same laptop, same problem. I was actually about to post it, but the gream forum monster jumped me and said NO DOUBLE POSTING!

Can someone please help us! cristian has some great documentation here.

A new update since the posts, skype has us upside down. Which is fun and all, but it gets old pretty quick.

And this is a BUILT IN webcam on a laptop. So no jokes about "just turn the camera upside down" thanks. :)

---

### Post by bluvy on 2007-11-10
I just got my Asus W7S and installed Kubuntu on it and my webcam is upside down on Kopete too! I've been googling this problem, and it seems that many *ubuntu users with the Asus W7 have the same webcam problem too. Grr, it's getting really annoying.
Any help is greatly appreciated!

---

### Post by Markus72 on 2007-12-11
Hi,

I have the same issue but with an ASUS F3Sa.
I somewhere read that it's because the cam is built in upside down.
[And I read that there is no possibility to rotate the image on device level]("http://linux-uvc.berlios.de/#introduction")  - whatever that means.

I try to use Skype but everything is upside down (Kubuntu 7.10).
With Windows the cam works fine.

No ideas how to solve this

Markus

I have to correct myself: even with XP the image is upside down

---

### Post by Markus72 on 2007-12-12
I posted the problem in the Asus VIP forum.
Let's see what happens.

I'm thinking about installing Vista with the original Asus drivers just check out how the cam behaves then.

Markus

---

### Post by daynah on 2007-12-12
> **Markus72 said:**
> I posted the problem in the Asus VIP forum.
Let's see what happens.

I'm thinking about installing Vista with the original Asus drivers just check out how the cam behaves then.

Markus

Don't waste your time, it behaves fine.

---

### Post by Markus72 on 2007-12-12
Hi Daynah,

so you already tested it, right?

M

---

### Post by ema on 2008-01-15
Did anyone solved this?
I'm using Ekiga and or Skype...but still upside down images...

Thanks,
Ema.

---

### Post by slekkas on 2008-03-15
Does anyone know if theres a way to invert the webcam? The webcam is very important to me. In windows XP the webcam is also upside down but in every software theres an option to flip. Are there similar options in Linux? this is a reason for me to go back to Windows even though i hate the idea:-(.

---

### Post by Bazilio on 2008-03-21
Same problem on Asus G1S laptop
In windows system it works perfect, webcam detects as D-Max_GD-5A35, device PID code: USB\VID_174F&PID_5A35

In linux it detects as Sonix Technoogy Co., Ltd USB 2.0 Camera

String with "syntek" about my webcam:
```

bazilio@ASUSG1S:~$ lsusb
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 003: ID 0b05:1726 ASUSTek Computer, Inc. Laptop OLED Display
Bus 006 Device 002: ID 174f:5a35 Syntek
Bus 006 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
```

```
bazilio@ASUSG1S:~$ lsmod | grep video
video 18060 0
uvcvideo 57480 0
compat_ioctl32 2304 1 uvcvideo
videodev 29312 1 uvcvideo
v4l1_compat 15364 2 uvcvideo,videodev
v4l2_common 18432 2 uvcvideo,videodev
usbcore 138632 7 xpad,uvcvideo,hci_usb,usbhid,ehci_hcd,uhci_hcd
```

Can anyone solve the problem?

---

### Post by Kaisersoze on 2008-04-13
For those who get the image upside down use this command in bash:

echo 1 >/sys/class/video4linux/video0/vflip


Regards

---

### Post by Bazilio on 2008-04-14
> **Kaisersoze said:**
> For those who get the image upside down use this command in bash:

echo 1 >/sys/class/video4linux/video0/vflip


Regards

there is no "vflip" :(

```
bazilio@ASUSG1S:/sys/class/video4linux/video0$ ls -l
-r--r--r-- 1 root root 4096 2008-04-14 12:20 dev
lrwxrwxrwx 1 root root    0 2008-04-14 12:18 device -> ../../../devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0
-r--r--r-- 1 root root 4096 2008-04-14 12:20 name
lrwxrwxrwx 1 root root    0 2008-04-14 12:18 subsystem -> ../../../class/video4linux
--w------- 1 root root 4096 2008-04-14 12:20 uevent

```

---

### Post by superdexter on 2008-04-24
I'm just posting to follow if a fix comes up.  I can confirm that this occurs on an Asus F7F as well.  Confirm that with the Vista drivers it works fine.  With XP drivers it's upside down.  Seems they only really fixed this (or put the tweak) in the Vista driver.

~$ lsusb
Bus 005 Device 003: ID 04f2:b012 Chicony Electronics Co., Ltd

---

### Post by Bazilio on 2008-04-25
> **superdexter said:**
> I'm just posting to follow if a fix comes up.  I can confirm that this occurs on an Asus F7F as well.  Confirm that with the Vista drivers it works fine.  With XP drivers it's upside down.  Seems they only really fixed this (or put the tweak) in the Vista driver.

Yes! It's f***ing vsta-design. Everywere it's upside-down, but in vista it's flipped on driver level...

---

### Post by hhpeter on 2008-04-25
> **Kaisersoze said:**
> For those who get the image upside down use this command in bash:

echo 1 >/sys/class/video4linux/video0/vflip


Regards

THANKS that did it for me I have asus s96s with 174f:6a51 webcam

---

### Post by superdexter on 2008-04-25
On my system vflip doesn't exist.  This command does not help me at all on my system.  Was there some additional v4l package to install to get that?

---

### Post by hhpeter on 2008-04-25
> **hhpeter said:**
> THANKS that did it for me I have asus s96s with 174f:6a51 webcam

well it worked but after I restart the system the image is upside down again .... is there a way to make this permanent?

---

### Post by Bazilio on 2008-04-26
> **hhpeter said:**
> well it worked but after I restart the system the image is upside down again .... is there a way to make this permanent?
write this command in /ets/rc.local

---

### Post by hhpeter on 2008-04-26
> **Bazilio said:**
> write this command in /ets/rc.local

Thanks....

---

### Post by Kaisersoze on 2008-04-26
> **slekkas said:**
> Does anyone know if theres a way to invert the webcam? The webcam is very important to me. In windows XP the webcam is also upside down but in every software theres an option to flip. Are there similar options in Linux? this is a reason for me to go back to Windows even though i hate the idea:-(.

Hi!

Type the following command in console:

echo 1 >/sys/class/video4linux/video0/vflip

Hope it helps

---

### Post by nickless on 2008-04-28
I get an upside down image as well using a philips webcam and there is no /sys/class/video4linux/video0/vflip on my system (Ubuntu 8.04).

---

### Post by Bazilio on 2008-04-29
> **Kaisersoze said:**
> Hi!

Type the following command in console:

echo 1 >/sys/class/video4linux/video0/vflip

Hope it helps
[http://ubuntuforums.org/showpost.php?p=4713334&postcount=13](http://ubuntuforums.org/showpost.php?p=4713334&postcount=13)

---

### Post by Kaisersoze on 2008-04-29
> **Bazilio said:**
> there is no "vflip" :(

```
bazilio@ASUSG1S:/sys/class/video4linux/video0$ ls -l
-r--r--r-- 1 root root 4096 2008-04-14 12:20 dev
lrwxrwxrwx 1 root root    0 2008-04-14 12:18 device -> ../../../devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0
-r--r--r-- 1 root root 4096 2008-04-14 12:20 name
lrwxrwxrwx 1 root root    0 2008-04-14 12:18 subsystem -> ../../../class/video4linux
--w------- 1 root root 4096 2008-04-14 12:20 uevent

```

Sorry, I got that line of code by googling my problem and it worked for me.. unfortunately, I havent sufficient Linux knowledge to help you more.
Sorry guys

---

### Post by onemanclapping on 2008-05-04
> **Kaisersoze said:**
> For those who get the image upside down use this command in bash:

echo 1 >/sys/class/video4linux/video0/vflip


Regards

thank you very much, it worked on my ASUSS96S! :)

---

### Post by superdexter on 2008-05-04
It's really great that some people have found the 
    ```
echo 1 >/sys/class/video4linux/video0/vflip
```
helpful to resolve their problem.  The bigger issue, I should think is that some of us don't have the option to set vlip. 

If you post that it worked for you, could you please also post the lsusb output to see if it is for the same camera.  Here is mine, and it is STILL upside down.

```
:~$ lsusb
Bus 005 Device 003: ID 04f2:b012 Chicony Electronics Co., Ltd 
```

This problem also persists into Hardy Heron 8.04....upgrade doesn't resolve the issue.

---

### Post by Bazilio on 2008-05-07
> **superdexter said:**
> 
This problem also persists into Hardy Heron 8.04....upgrade doesn't resolve the issue.
Confirm
```
bazilio@bazilio-laptop:~$ lsusb | grep 174
Bus 003 Device 002: ID 174f:5a35
```
[QUOTE=asus.com]
 D-Max_GD-5A35 Camera Driver
D-Max_GD-5A35 Camera Driver for Vista
1. Please refer to below FAQ to check your camera's PID code:
[http://support.asus.com/faq/faq_right_second_detail.aspx?kb_guid=02B6B989-4468-5237-CB04-BCF5B9FE9714&model_name=A3E&SLanguage=en-us](http://support.asus.com/faq/faq_right_second_detail.aspx?kb_guid=02B6B989-4468-5237-CB04-BCF5B9FE9714&model_name=A3E&SLanguage=en-us)

2. This driver is for below PID code:

HW_ID_1 = USB\VID_05E1&PID_0501
HW_ID_2 = USB\VID_174F&PID_A821
HW_ID_3 = USB\VID_174F&PID_AA11
HW_ID_4 = USB\VID_174F&PID_A351
HW_ID_5 = USB\VID_174F&PID_A311
HW_ID_6 = USB\VID_174F&PID_6A31
HW_ID_7 = USB\VID_174F&PID_6A51
**HW_ID_8 = USB\VID_174F&PID_5A35**
HW_ID_9 = USB\VID_174F&PID_6A33
[/QUOTE]

---

### Post by erlingwl on 2008-06-05
Same issue here, 8.04 and no /sys/class/video4linux/video0/vflip

Have an acer Travelmate 6460.

---

### Post by arjos85 on 2008-06-22
PROBELM SOLVED!!!!

Hi guys,
have a look to my posts here:
[https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/thread.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/thread.html)

I've just modified the source code of uvcvideo driver in oreder to flip the images!! ;)

The 3D is "SOLVED: upside-down image from SONIX laptop embedded webcam"

Please read all my messages because I've solved some bugs of first posts but first of all because i've created two modded uvcvideo.

Have a look and try both my solutions!!
And then tell me what you think is the best and fastest!!

Thank you very much...
please let me know!!

marco

---

### Post by Bazilio on 2008-06-22
> **arjos85 said:**
> PROBELM SOLVED!!!!

Hi guys,
have a look to my posts here:
[https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/thread.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/thread.html)

I've just modified the source code of uvcvideo driver in oreder to flip the images!! ;)

The 3D is "SOLVED: upside-down image from SONIX laptop embedded webcam"

Please read all my messages because I've solved some bugs of first posts but first of all because i've created two modded uvcvideo.

Have a look and try both my solutions!!
And then tell me what you think is the best and fastest!!

Thank you very much...
please let me know!!

marco


Thank you! It works! 
Asus G1S. I just did that:
[https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003632.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003632.html)

Image on vebcam now in right position. But image quality not qood:

Before patch:
[[IMG]http://img131.imageshack.us/img131/3056/32147540rc8.th.png[/IMG]](http://img131.imageshack.us/my.php?image=32147540rc8.png)

after patch:
[[IMG]http://img58.imageshack.us/img58/7963/39967448uk2.th.png[/IMG]](http://img58.imageshack.us/my.php?image=39967448uk2.png)

---

### Post by Bazilio on 2008-06-22
i changed pixel_size to 2 and image quality become good.

but this patch hangs my system.. if i look to kopete settings for 1 minute, my system hangs...

---

### Post by Bazilio on 2008-06-22
ok. probably it's kopete bug.
in skype it works perfect!

problem __SOLVED__

---

### Post by arjos85 on 2008-06-22
I'm very very happy ...
you are the first who tried my modded driver...
really thank you
;)

> **Bazilio said:**
> i changed pixel_size to 2 and image quality become good.

but this patch hangs my system.. if i look to kopete settings for 1 minute, my system hangs...


Well...
on my system I get poor quality if I set pixel_size=2 (bpp=16)...
really I can't understand why...

any ideas?

---

### Post by arjos85 on 2008-06-22
> **Bazilio said:**
> Thank you! It works! 
Asus G1S. I just did that:
[https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003632.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003632.html)


NO wait...

yuo are wrong...

that was an old patch...
let go on reading my messages...
I've solved that kind of poor quality problem...
there are two final working solutions...
let see here:
First solution
[https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003656.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003656.html)
Second solution
[https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003644.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003644.html)
and 
[https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003648.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003648.html)

Just for now try the first solution,
you'll get better color and resolution quality!! ;)

let me know

---

### Post by arjos85 on 2008-06-22
> **Bazilio said:**
> 
but this patch hangs my system.. if i look to kopete settings for 1 minute, my system hangs...

this problem is due to the fact that i forgot to free the allocated memory...
just refer to my next messages in uvcvideo mailing list..
don't stop to the first messsage because it is full of bug!! :S

If you can,
please try both solution I've explained in my posts in uvcvideo mailing-list...and let me know which one is the best in your opinion!!

Thank you very much!!! ;)

Marco

---

### Post by Bazilio on 2008-06-22
Thank you, Marco, for correcting me!
there is 4 my tries:

1st with the memory eating (patch from here: [https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003632.html]("https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003632.html")):
full screen in skype:
[[IMG]http://img292.imageshack.us/img292/6353/12wx4.th.png[/IMG]](http://img292.imageshack.us/my.php?image=12wx4.png)
memory eating (see on superkaramba aplet)
[[IMG]http://img59.imageshack.us/img59/6615/13hq2.th.png[/IMG]](http://img59.imageshack.us/my.php?image=13hq2.png)
Memory eating, sistem hangs and bad image. So it isn't correct patch.


2nd witn the patch from here: [https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003644.html]("https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003644.html")

full screen in skype:
[[IMG]http://img508.imageshack.us/img508/2483/10fm5.th.png[/IMG]](http://img508.imageshack.us/my.php?image=10fm5.png)
no memory eating (see on superkaramba aplet)
[[IMG]http://img242.imageshack.us/img242/3258/11ed9.th.png[/IMG]](http://img242.imageshack.us/my.php?image=11ed9.png)
No memory eating and system hangs, but image not good yet. So, let's continue.


3rd with remarks from here: [https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003648.html]("https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003648.html")
full screen in skype:
[[IMG]http://img131.imageshack.us/img131/8703/14fp0.th.png[/IMG]](http://img131.imageshack.us/my.php?image=14fp0.png)
no memory eating (see on superkaramba aplet)
[[IMG]http://img398.imageshack.us/img398/2579/15nj7.th.png[/IMG]](http://img398.imageshack.us/my.php?image=15nj7.png)
No memory eating, no system hangs, good image, but image mirrored. May be it isn't critical, but let's try last patch:


4th patch from here: [https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003656.html]("https://lists.berlios.de/pipermail/linux-uvc-devel/2008-June/003656.html")
full screen in skype:
[[IMG]http://img528.imageshack.us/img528/6518/73964701ww0.th.png[/IMG]](http://img528.imageshack.us/my.php?image=73964701ww0.png)
no memory eating (see on superkaramba aplet)
[[IMG]http://img528.imageshack.us/img528/4830/95361062eg7.th.png[/IMG]](http://img528.imageshack.us/my.php?image=95361062eg7.png)
Situation the same as the previous. I didn't see that video becoms bit slower then in previous try. So i desided to use this patch as the last version.

Thank you, Marco, for this patch! I am happy as a big white bear with bucket of vodka!
Greetings from Russia, Moscow! (;

P.S. it would be nice if the image would not be mirrored.

---

### Post by Bazilio on 2008-06-22
> **arjos85 said:**
> 
Well...
on my system I get poor quality if I set pixel_size=2 (bpp=16)...
really I can't understand why...

any ideas?

I had in mind that there is no big pixels, but colors are bad.

---

### Post by arjos85 on 2008-06-23
> **Bazilio said:**
> Situation the same as the previous. I didn't see that video becoms bit slower then in previous try. So i desided to use this patch as the last version.

If you don't see any difference, it's better the last version of the patch!!
So you are right!! ;)

> Thank you, Marco, for this patch! I am happy as a big white bear with bucket of vodka!
Greetings from Russia, Moscow! (; 

Thank you Brazilio for having tried my patch...
you are really the first one (after me ;) )!!!

> P.S. it would be nice if the image would not be mirrored.

Yeha...I know...but I really don't know how to get "not mirrored" images with good color quality!! :cry:
I'm afraid...when I'll find out how...I will let you know!!!

Ciao ciao
from Italy, Turin  ;)

---

### Post by neandertal on 2008-06-23
Hi arjos85 and Bazilio,
thanks for all the work,
it looks like a lot of trouble to flip this UVC webcam image. I really want to remove microvista from my computer (PB bg46) and the webcam is the only reason I still have it on. I kind of had a hard time following all the steps that lead to the image flipped and with the right color.
Could you please help me with some kind of a "how to"?

:)

---

### Post by arjos85 on 2008-06-23
> **neandertal said:**
> 
Could you please help me with some kind of a "how to"?
:)

Sure, very soon I'll tell you where to find this HOT-TO...
;)

---

### Post by arjos85 on 2008-06-23
Ok...as I promise...
here you can find a quick HOW-TO...that should help you to solve your problems with your webcam:
[http://ubuntuforums.org/showthread.php?t=838210](http://ubuntuforums.org/showthread.php?t=838210)

good luck ;)

arjos85

---

