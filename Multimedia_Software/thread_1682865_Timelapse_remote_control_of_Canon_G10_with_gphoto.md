---
title: "Timelapse remote control of Canon G10 with gphoto"
date: 2011-02-06
forum: Multimedia Software
---

### Post by T@. on 2011-02-06
I had some trouble making a time lapse video using a canon g10 camera and gphoto in ubuntu 10.10.

Because of that is tried to get a crack/hack of psremote to work under wine and when that failed I actually considered installing xp to my machine.

So this is what can be done to get timelaps recording with a g10 under linux ubuntu.
I hope it is of help to some one and perhaps someone knows a more user friendly program that can to remote control timelapse with a canon g10?

administration>synaptic package manager> search "gphoto" and install all the unmarked packages that show up.

Connect our camera to the machine and unmount the device.

Open a terminal 
and type "man gphoto2", this will give you an idea of the commands available.
exit with Q

Enter "gphoto2 --auto-detect" and you camera should show up.

Then normally you can enter "gphoto2 --list-config" but for the canon g10 you need to enter "gphoto2 --list-config capture=on" to make things happen.
(this is what had me stuck for a while)
enter "gphoto2 --get-config name"
enter "gphoto2 --set-config name=value"

enter "gphoto2 --capture-image-and-download --filename "%Y%m%d%H%M%S.jpg""

If all is well a your camera takes a picture and saves it on your computer, making the file name the time and date .jpg

Now you can start your timelapse recording with "gphoto -I 25 -F 3000 --capture-image-and-download --filename "%Y%m%d%H%M%S.jpg""
where -I 20 is a 25 second interval and -F 3000 is the amount of pictures to be taken.

You can enter more setting in this command line like iso valuwe, flash, shutter lag, etc. These commands can be found in the config list.

I guess it is a lot of work to make a click a button interface (shows what noob, I am) since every model of camera has different options.

Does any one know of a program native to Linux / Ubuntu that works?

---

