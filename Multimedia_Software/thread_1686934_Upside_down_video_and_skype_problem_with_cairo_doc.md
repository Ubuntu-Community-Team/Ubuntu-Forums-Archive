---
title: "Upside down video and skype problem with cairo dock on Asus K52J"
date: 2011-02-13
forum: Multimedia Software
---

### Post by Radhavictory on 2011-02-13
Hello,

I just bought an Asus K52J a couple of days. I of course got down right away to installing Ubuntu 10.10. Everything works fine except for a couple of problems with Skype.

In the past I already had the problem with Skype video not working while Cairo dock was running. I found a solution which consisted in changing the command line and making a custom launcher for Skype alone on my desktop. The command line was


export XLIB_SKIP_ARGB_VISUALS=1 && skype

Now, on this new laptop....I have a new problem.....the webcam image is upside down! For this too I found a custom command line for skype to run properly.

export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

My problem is combining the two commands in one line so that Skype will run properly and this would thus solve my problem. Seeing that I am running Cairo dock as well i need to solve the incompatibility issue and also the inverted video in Skype.

Can anybody help me out in combining the above two commands? I tried just copying and pasting them but it only solves the incompatibility with Cairo dock, the image in the meantime, remains upside down!

Any help will be greatly appreciated!

---

### Post by mr_amit on 2011-02-14
I am having same issue with my newly bought K52J laptop. I have created a launcher on gnome panel with this command line:

```

env LIBV4LCONTROL_FLAGS=3 LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

```

I am also facing few more issues like:

- sound issue (HDMI and Audio Jack)
- unable to disable touchpad
- suspend/hibernate doesn't work

I if close the LID, ubuntu will be suspended to save power but then it never awakes and need to reboot the system using power button. So I have changed this settings from gnome power manager to not suspend on LID close.

---

### Post by Radhavictory on 2011-02-19
@mr amit:

Hi thanks for trying to help out. After a week of struggling with Skype I finally got it to work.
Here's what I did.

1. I first followed the instructions on this page

[http://techieboycdo.blogspot.com/2010/08/fix-upside-down-or-inverted-webcam-on.html](http://techieboycdo.blogspot.com/2010/08/fix-upside-down-or-inverted-webcam-on.html)

then I used this command to get skype started

env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 

and suddenly it all worked fine. I have no idea what I did but this is what worked for me.

2. About your suspend problem, a fix has been found which is very simple. Check out this page/post here

[http://art.ubuntuforums.org/showthread.php?t=1460790](http://art.ubuntuforums.org/showthread.php?t=1460790)

I hope it works out for you.
One last thing, I use Cairo dock and Skype is incompatible with OpenGL. So there is another command line that needed to be added to the one mentioned above to get it working. Here's what I did. I edited the command line by putting this

export XLIB_SKIP_ARGB_VISUALS=1
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

(first line is for it to work along with Cairo dock and the second line is for the webcam issue.)

and bang! everything works! Finally!!!!!

Thanks again, ciao!

---

