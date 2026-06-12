---
title: "nVidia Driver Detects Wrong Resolution"
date: 2010-10-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by karmila on 2010-10-04
Hi!

I have nVidia GeForce 6100 nForce 405 graphic card now running Ubuntu Maverick RC. Everything just fine before I installed current driver (256.53) from repository. After installed the driver my graphic card display 1280x768 resolution instead of 1360x768 (Samsung SyncMaster 943 native resolution).

Then I tried to install latest driver from X Updates ppa but nothing changes. My graphic card still display wrong resolution.

The weird thing was nvidia-settings told the right resolution 1368x768 but not in my monitor.:(

Now, after purge X Updates ppa and remove nVidia driver my monitor resolution backs to normal. Anyone have/had this problem too? Any solution or alternative to enable 3d because some application need that...

---

### Post by dino99 on 2010-10-04
remove xorg.conf

sudo rm -f /etc/X11/xorg.conf

then reboot

---

### Post by karmila on 2010-10-04
@dino99: When should i do that, before or after install the driver?

---

### Post by realzippy on 2010-10-04
@dino

sorry,but is this your standard solution for everything?
[#2]("http://ubuntuforums.org/showpost.php?p=9922781&postcount=2")
may I again ask why OP should do this????

@karmila

You need the nvidia-driver for 3D acceleration.
Reinstall the driver,set the resolution you need in nvidia-settings.
If it still shoud not work,create
the nvidia-bug-report file and post it here please:
```
sudo nvidia-bug-report.sh
```
..file will be in your user's directory.

---

### Post by karmila on 2010-10-04
@realzippy: Sorry my ISP got error last night :(

This is my nvidia-settings screen shoot and nvidia-bug-report. They tell different driver.. :confused:

---

### Post by karmila on 2010-10-04
Oh yes, the problem still exist.

---

### Post by cariboo on 2010-10-04
Did the latest Nvidia driver 260.19.06 do anything for you?

---

### Post by tormod on 2010-10-05
There were some resolution issues with a recent gnome-settings-daemon update. This was fixed in gnome-settings-daemon 2.32.0-0ubuntu2 so please retest once you have this version installed.

---

### Post by karmila on 2010-10-05
> **cariboo907 said:**
> Did the latest Nvidia driver 260.19.06 do anything for you?

I install them again from X Updates ppa but they do nothing :(

---

### Post by karmila on 2010-10-05
> **tormod said:**
> There were some resolution issues with a recent gnome-settings-daemon update. This was fixed in gnome-settings-daemon 2.32.0-0ubuntu2 so please retest once you have this version installed.

I just finished download current daily-build image and going to install it now. I'll back for report.

---

### Post by karmila on 2010-10-05
I installed today daily-build and still got the same problem. :confused:

---

### Post by tormod on 2010-10-05
> **karmila said:**
> I installed today daily-build and still got the same problem. :confused:
Have you updated gnome-settings-daemon to 2.32.0-0ubuntu2? If so, it is another bug.

---

### Post by karmila on 2010-10-05
> **tormod said:**
> Have you updated gnome-settings-daemon to 2.32.0-0ubuntu2? If so, it is another bug.

I went to synaptic and saw that i had 2.32.0-0ubuntu1 instead of the latest package. It is weird because i have daily-build install and because of that I don't have any updates from my local repo.

So, i just went to packages.ubuntu.com. Downloaded & installed it manually, reinstalled current nvidia driver, rebooted. Voila, now I get my monitor full screen and 3D enabled. 

Thanks, and I mark this thread as solved :P

---

### Post by tormod on 2010-10-06
> **karmila said:**
> I went to synaptic and saw that i had 2.32.0-0ubuntu1 instead of the latest package. It is weird because i have daily-build install and because of that I don't have any updates from my local repo.
It it because this package was released after your daily build was made.

---

### Post by karmila on 2010-10-06
> **tormod said:**
> It it because this package was released after your daily build was made.

:)

Thanks for your help. :guitar:

---

