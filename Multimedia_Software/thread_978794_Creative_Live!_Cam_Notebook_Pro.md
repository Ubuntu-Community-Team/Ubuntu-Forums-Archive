---
title: "Creative Live! Cam Notebook Pro"
date: 2008-11-11
forum: Multimedia Software
---

### Post by lodravah on 2008-11-11
Hey.

As others, I am having issues with my webcam in Skype. I am totally new to using one i Linux, and I need some help. I have googled, and have found info regarding LD_PRELOAD which is a fix that is supposed to work, but I am unable to find out how to actually use this hack. 

The webcam works in Cheese, but not camorama (same issue as another user in this forum, but without fix so far). The issue I am having in Skype is "colourful (mostly green) snow" when testing. So I know that the cam works with Ubuntu, just nor Skype. 

Anyone?

---

### Post by duffrecords on 2008-12-19
Try editing /etc/modprobe.d/options and adding the following line:```
options ov51x-jpeg forceblock=1
```Then reload the ov51x-jpeg module like this:```
sudo modprobe -r ov51x-jpeg
sudo modprobe ov51x-jpeg
```That was how I got my Live! Cam Notebook working with Skype in Hardy Heron.

---

### Post by duffrecords on 2008-12-19
Also, if you upgrade to Intrepid Ibex you may find that ov51x-jpeg-1.5.9 does not work.  Use the latest svn source; there is a small error in the release version.

---

### Post by crazy ivan on 2008-12-20
I've had to work through a lot of incomplete answers before finding that the ubuntu 8.10 section of the [rastageeks wiki]("http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall") lists all the steps that are necessary. Still having some problems with *camorama* and *cheese*, but * XawTV * and * SKYPE * video works.

---

### Post by duffrecords on 2008-12-20
The 8.10 section of the wiki *is* quite complete, but what I'm saying is you should check out the latest code with subversion instead of the 1.5.9 tarball.  There is an edit on line 8377 that impacts the ability of some applications to detect the webcam.  What problems are you having with canorama and cheese?

---

### Post by crazy ivan on 2008-12-25
Guess you're right and my problems
1) cheese detects no video-device
2) grey triple-pictures in camorama
are caused by this line.. But aslong as skype works I'm happy.

---

### Post by crazy ivan on 2009-03-28
Hey fellow "Creative Notebook Pro" users, experienced the following problems after setting it up with the [rastageeks wiki]("http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall"): Webcam stopped working after kernel update. 
More precisely: Programs like "cheese" and "ekiga" started working properly (with ekiga unfortunately only in the sense of displaying my own video though), whereas skype showed nothing but green.. Did nothing about the problem, so the next kernel update changed skype behavior to crashing every time I accessed video.
Now I got down and fixed it:
1. Find out the names of the modules related to webcam
```

lsmod | grep ov
```
2. "Killem all"
```
sudo rmmod ov51x_jpeg gspca_main gspca_ov519
```
3. Reinstall the old one
```
modprobe ov51x-jpeg
```

Now I'm back with the old problems.. Most webcam aps not working but skype running fine. But since there is no good linux alternative to skype to do video chatting yet, I'm o.k. with that.

---

### Post by crazy ivan on 2009-03-28
If you're looking for a solution, where both ekiga and skype work you might want to give the solution by [Alejandro Vargas and Hans de Goede]("http://forum.skype.com/index.php?showtopic=225971") a try, where the default driver is not altered, but instead the skype libraries.

---

### Post by sandy8925 on 2009-04-11
I used to have the same problem too. Did you try the webcam with cheese ? By the way you can run skype like this :

env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Just copy and paste it in a terminal. You can save it in a text file make it executable and then just call the run dialog and type ./filename .

Steps:
1)Copy the command (only that line above)and save it in a file with any name
2)Open a terminal go to the directory where it is saved (best to save it in home directory)
3)Type "chmod +x ./filename" without the quotes. This makes the file executable.
4)Then whenever you want to use Skype open the terminal go to that directory and type ./filename and it should work. Alternatively you can also press Alt + F2 which open the run dialog. Then type ./filename

Phew!! Hope that helps.

---

### Post by aynaval on 2010-03-25
> **sandy8925 said:**
> I used to have the same problem too. Did you try the webcam with cheese ? By the way you can run skype like this :

env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Just copy and paste it in a terminal. You can save it in a text file make it executable and then just call the run dialog and type ./filename .

Steps:
1)Copy the command (only that line above)and save it in a file with any name
2)Open a terminal go to the directory where it is saved (best to save it in home directory)
3)Type "chmod +x ./filename" without the quotes. This makes the file executable.
4)Then whenever you want to use Skype open the terminal go to that directory and type ./filename and it should work. Alternatively you can also press Alt + F2 which open the run dialog. Then type ./filename

Phew!! Hope that helps.
yes that helps....oh my god...i was almost gonna swallow my pride and switch back to windows or worse get a mac...but this instills my faith right back! thank you thank you thank you...
i havent given up yet even after imminent dismissal from my clients who cannot for the life of them read any of my files. but with this kind of network, ubuntu can only get better. I am praying and waiting for April.

---

### Post by no2498 on 2010-03-26
hope you all know v4l1 and v4l2 is all 1 driver now

i just hope they/ubuntu fix the v4l1 colors backwards for me

---

