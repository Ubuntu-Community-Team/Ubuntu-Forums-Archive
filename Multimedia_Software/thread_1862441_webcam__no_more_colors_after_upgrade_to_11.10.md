---
title: "webcam : no more colors after upgrade to 11.10"
date: 2011-10-16
forum: Multimedia Software
---

### Post by pgogan on 2011-10-16
I use an external usb webcam (Creative Labs Live! Cam Notebook Ultra) wich worked perfectly under xubuntu 11.04.  After installing xubuntu 11.04, this webcam works but **in Black-and-White **only !
The output of "lsusb" is :
ID 041e:405b Creative Technology, Ltd 
The output of "lsmod" for this device is :
uvcvideo               67271  0 
gspca_vc032x           31999  1 
gspca_main             27610  2 gspca_vc032x
videodev               85626  3 uvcvideo,gspca_main
Thus the module is loaded, but does not works properly.
Any workaround for this problem ?

---

### Post by ergo-proxy on 2011-10-17
I have a similiar issue in oneiric though my webcam is green but my friend's webcam with whom I tested had everything in black-white like you... seems something is broken in 11.10 (ubuntu 64)

---

### Post by no2498 on 2011-10-17
see if these programs help you guvcview and v4lucp
v4lucp comes up in system/preferences as video4linux control panel
guvcview comes up in applications sound and video

---

### Post by SpEcIeS on 2011-10-17
Similar problem with my Logitech webcam, but it works as normal via VLC. This is a gstreamer on my system.

---

### Post by pgogan on 2011-10-18
The program guvcview works perfectly and I  get a color image. 
On the contrary, cheese display a black and white image of very poor quality.
To use the logitek cam with Skype I must LD_PRELOAD v4l2convert.so and the image is as bad as when using cheese. 
Thus the problem is probably  related to video4linux.

---

### Post by no2498 on 2011-10-19
vlc changes the output file type to like mpeg
you may be able to reset it in guvcview to avi

---

### Post by ppatalano on 2011-10-22
Same problem with my microsoft webcam. It is now green and sometimes black and white and the microphone no longer works. Any word on how to fix this?

---

### Post by no2498 on 2011-10-22
ppatalano
? what program you using for the cam

---

### Post by dunbrokin on 2011-10-22
I have a similar problem....webcam worked in 10.10 and has not worked since. ....well that is not true it works for 1 go after the kernel has an upgrade and then goes bock to not working. I have tried 3 different webcams from 3 different suppliers...

---

### Post by ppatalano on 2011-10-22
no2498,

I'm using chrome browser, cheese, the messaging client that came installed on the distribution. It happens with all of these. The only thing it seems not to do this is in guvcview. It was working fine and dandy with 11.04, mic, color, everything.

---

### Post by no2498 on 2011-10-23
look in your package manager for wxcam or 
[http://sourceforge.net/projects/wxcam/?_test=beta](http://sourceforge.net/projects/wxcam/?_test=beta)

---

### Post by ppatalano on 2011-10-23
Installed wxcam, still having the same issue.

---

### Post by ppatalano on 2011-10-23
Let's see if this flicks anyone's light bulb...

Ok in guvcview if I change the output to YU12 or YV12 I experience the video problems as I have seen with the other programs. No idea on the sound.

---

### Post by marcosba on 2011-10-26
I have Ubuntu 11.10 and a Logitech HD Webcam C510.

guvcview and VLC Works fine for me, But Cheese and Google Chrome don't work.

---

### Post by m-silverx on 2011-10-29
Hi All
I've ugraded ubuntu from 11.04 to 11.10 64bit, and now is there a problem with my webcam Creative, 
with guvcvier the windows is black and using others software the cam and microphon doesn.t work 

lsub 
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 041e:4058 Creative Technology, Ltd Live! Cam Optia AF
Bus 002 Device 003: ID 07ca:850a AVerMedia Technologies, Inc. AverTV Volar Black HD (A850)
Bus 005 Device 002: ID 045e:0734 Microsoft Corp. Wireless Optical Desktop 700

Do you have any idea ?
Thanks

---

### Post by SpEcIeS on 2011-10-29
Installed v4l2ucp and there seems to be no problem. Again, the problem only seems to be relevant with gstreamer interaction on my machine. All other programs, such as cheese, that use gstreamer do not display a proper image. (lines through the image and erratic color with mostly b&w)

---

### Post by robertorc87 on 2011-11-05
11.10 64bit here.

same problem. Using a Lenovo W520 notebook. The webcam works fine in VLC, but it doesn't work with cheese or other programs, I get a b&w image with some graphical corruption going on (lines and artifacts).
Cam works perfectly on VLC and on windows.

---

### Post by no2498 on 2011-11-05
look in your package manager see if you have gstreamer 
good set , bad set , ugly set , and 0.10
for the ubuntu/linux you use

---

### Post by m-silverx on 2011-11-05
[SIZE=3]Hi ALL
I've resolved by kernel downgrade (natty kernel) 
go to [/SIZE][SIZE=3][http://packages.ubuntu.com/](http://packages.ubuntu.com/) and download linux-image (= 2.6.38.12.27)  [/SIZE][SIZE=4][SIZE=3] 
After modify  /etc/apt/sources.list comment all row and add deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main

sudo apt-get update
sudo dpkg -i linux-image-2.6.38-12-generic_2.6.38-12.51_amd64.deb
sudo apt-get install linux-headers-2.6.38-12-generic

reboot and all work fine include Skype and Cheese .........

:P
[/SIZE][/SIZE]

---

### Post by dunbrokin on 2011-11-05
Hmmm, presumably you can just reverse the procedure to get back to the current kernel?

---

### Post by dsfitzpat on 2011-11-06
There's an open bug on the problem: [https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/838739](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/838739)
Reverting to the old kernel seems like a bit of an extreme step; I'm hoping this will get fixed.

---

### Post by ppatalano on 2011-11-15
Here's the solution that finally worked for me.

```
sudo add-apt-repository ppa:libv4l
sudo apt-get update
sudo apt-get install libv4l-0 libv4l-dev
```


I hope this works out for everyone experiencing the same thing.

---

### Post by dsfitzpat on 2011-11-15
This was reported on Launchpad as Bug #838739, and a fix was released today.
The ppa you've given will work as well, but the problem can also be solved by adding the ubuntu-proposed repository.
There are still issues with Skype however, if you're using that.

---

### Post by irondoll on 2011-11-17
This worked for the color issue of guvcview. But soon the picture fade to black. Could it be because of something wrong with autogain?
My device is 046d:08dd Logitech, Inc. QuickCam for Notebooks.

> **ppatalano said:**
> Here's the solution that finally worked for me.

```
sudo add-apt-repository ppa:libv4l
sudo apt-get update
sudo apt-get install libv4l-0 libv4l-dev
```
I hope this works out for everyone experiencing the same thing.

---

