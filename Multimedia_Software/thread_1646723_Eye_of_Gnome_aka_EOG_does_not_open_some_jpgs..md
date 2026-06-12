---
title: "Eye of Gnome aka EOG does not open some jpgs."
date: 2010-12-16
forum: Multimedia Software
---

### Post by gencon on 2010-12-16
Using Ubuntu Lucid & Eye of GNOME 2.30.

Eye of Gnome aka EOG does not open some jpgs, here's what happens.

With some jpgs only, most work fine!!

If you open one of the problematic jpg files by clicking on the jpg in Nautilus, EOG never fully opens, the process starts but the application's window does not get displayed - I then kill the process with kill -9 PID.

The same jpg opens in other viewers, EG. FSpot and OO Draw on Linux, and IrfanView on Windows.

If you start EOG from the App menu or the command line and drag a problematic jpg to it, the jpg is also not displayed, nothing happens. BUT if you start EOG with a working jpg and, once that is being shown, drag a problematic jpg from Nautilus to EOG's window then now the problematic jpg is displayed.

Any ideas?

Thanks.

PS. Anyone know if there is an Eye of GNOME 2.32 (latest stable) deb package which I can download or if I can install EOG 2.32 from some other repositories? Aptitude and Synaptic have only v. 2.30.

---

### Post by mandarke on 2011-01-11
Have you checked those problematic files with the file command?

I have this problem also, but it seems to be with all image types.

---

### Post by gencon on 2011-01-11
> **mandarke said:**
> Have you checked those problematic files with the file command?
I hadn't but I have now, here's the output of the file command:

01-test.jpg: JPEG image data, JFIF standard 1.01

Does this help at all?

Cheers.

---

### Post by danemaslen on 2013-04-27
> **gencon said:**
> Using Ubuntu Lucid & Eye of GNOME 2.30.

Eye of Gnome aka EOG does not open some jpgs, here's what happens.

With some jpgs only, most work fine!!

If you open one of the problematic jpg files by clicking on the jpg in Nautilus, EOG never fully opens, the process starts but the application's window does not get displayed - I then kill the process with kill -9 PID.

The same jpg opens in other viewers, EG. FSpot and OO Draw on Linux, and IrfanView on Windows.

If you start EOG from the App menu or the command line and drag a problematic jpg to it, the jpg is also not displayed, nothing happens. BUT if you start EOG with a working jpg and, once that is being shown, drag a problematic jpg from Nautilus to EOG's window then now the problematic jpg is displayed.

Any ideas?

This is a problem I've also experienced, but I don't think it's specific to certain files.  I'll try to explain why I say that.  For the last four years I've intermittently experienced this scenario:
 * Double-click on JPG (or PNG) file.
 * Item appears on panel claiming that the file is being opened.
 * After a few seconds the item disappears.
 * Double-click on the file again.
 * EOG window opens successfully but is blank.
 * Close window.
 * Double-click on the file again.
 * EOG opens file successfully.
Whenever the initial failure occurred, the resultant sequence of events was so repeatable that I came to live with the minor hassle of occasionally having to try three times to get an image to display.  Just recently, however, I've started to experience the same sort of scenario that you describe, namely persistent failure to open an image, but the ability to display it by first opening another image in the same directory and then using the arrows to step forward or backward to the desired image.

I've just tried the experiment of repeatedly issuing the command
```
eog /home/dane/test/basket.png
```
from a terminal window.  About 75% of the time it failed to display the image and hung, forcing me to interrupt it with CTRL/C.  But the rest of the time it opened the image perfectly.  That's why I don't think that the failure is caused by the image!

Dane Maslen

---

### Post by sudodus on 2013-04-27
Ubuntu desktop 10.04 LTS end of life is this month. I suggest that you start looking for an alternative. I upgraded my production environment (my workhorse) to 12.04 LTS half a year ago, and my current eog version is 3.4.2, and I don't have that problem you are describing. I am also running Lubuntu, which is very nice on middle-aged and old computers.

Before upgrading you can download the iso file 12.04.2 and try it live (booting from CD/DVD/USB) and check if it is what you want. If you have old hardware, you can try Xubuntu or Lubuntu instead of Ubuntu. Unity in 12.04.2 is quite nice, although a different experience than old gnome2, so if you have a lot of horsepower, but don't like Unity, you can try Kubuntu or gnome shell.

My alternative was to upgrade Ubuntu from 10.04 to 12.04 and then install Lubuntu Desktop
```
 sudo apt-get install lubuntu-desktop
```
to get a very fast and responsive desktop environment on a once powerful workstation but now an aging computer. Obvious alternatives are to install **lxde** or **xubuntu-desktop** or **xfce4**. Different amounts of packages are installed, and afterwards you can select which desktop to run at the login screen (select 'session').

---

### Post by wildmanne39 on 2013-04-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

