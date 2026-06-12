---
title: "Ubuntu Studio Jaunty nvidia geforce mx420 driver issue"
date: 2009-06-04
forum: Multimedia Software
---

### Post by MMD1990 on 2009-06-04
I've installed jaunty for the 3rd time and have tried to fix the driver issue myself but I've hit blocks everywhere.
Anyway, I've been using the recommended driver (in the restricred driver menu) for this video card but have came to the conclusion it's not the correct one because after it's installed x server fails to load and I"m stuck with the command line instead of GUI.
I've tried installing it from a driver download from Nvidia's site which I've ran from the line using the sh. command, but the attempt has lead to a problem with the incorrect kernel and an error stating, ""unable to find the kernel source tree for the currently running kernel."

I'm quit an inexperienced user with ubuntu command lines and would appreciate any help I can get.

Thanks to everyone willing to help.

---

### Post by MMD1990 on 2009-06-04
anyone?
thanks

---

### Post by overdrank on 2009-06-04
Hi and welcome, have you tried the xfix option when booting into recovery mode?
Recovery mode is usually the second choice from the grub and choose xfix to correct graphical issues.

---

### Post by saimoncis on 2009-06-04
Hi MMD1990, this is Saimoncis from Italy, I have the same problem with my "Nvidia geforce fx go5700", I've tried all the drivers but with no results, now I'm stuck at low resulution graphics.
With the previous Ubuntu Studio all worked smoothly, maybe it's the kernel rt?
Let me know your progress...
ciao

---

### Post by Bearly Able on 2009-06-04
I'm using Nvidia GeForce 7900 GS, which worked just great under Hardy, but since I upgraded, I've had endless problems with the driver.  Using the "recommended" driver causes repeated freezes and crashes, and then the X Server error message.  I've been looking for two weeks now, but can't find any help on the subject, and am stuck with an incorrect display until I do.

---

### Post by MMD1990 on 2009-06-04
> **overdrank said:**
> Hi and welcome, have you tried the xfix option when booting into recovery mode?
Recovery mode is usually the second choice from the grub and choose xfix to correct graphical issues.

sure have
I think I got some error with a read/write problem
I'll be sure to go back and confirm that in an hour or so

---

### Post by MMD1990 on 2009-06-04
> **saimoncis said:**
> Hi MMD1990, this is Saimoncis from Italy, I have the same problem with my "Nvidia geforce fx go5700", I've tried all the drivers but with no results, now I'm stuck at low resulution graphics.
With the previous Ubuntu Studio all worked smoothly, maybe it's the kernel rt?
Let me know your progress...
ciao

> **Lesley Lutomski said:**
> I'm using Nvidia GeForce 7900 GS, which worked just great under Hardy, but since I upgraded, I've had endless problems with the driver. Using the "recommended" driver causes repeated freezes and crashes, and then the X Server error message. I've been looking for two weeks now, but can't find any help on the subject, and am stuck with an incorrect display until I do.


Guys, I'm going to be recompiling the kernel and using nvidia drivers in about an hour. 
I've found a tutorial on the subject looks like it can take a while for the inexperienced (i.e.-me). I'll be sure to let you know the outcome.  
Might keep this in  ind before the install-http://ubuntuforums.org/showthread.php?t=1036788

In the meantime this may be of some interest-
[http://ubuntuforums.org/showthread.php?t=1177942](http://ubuntuforums.org/showthread.php?t=1177942)

---

### Post by MMD1990 on 2009-06-04
So after about 5 hrs of working and trying to fix the problem I've found a solution, or so i think I have.


As for the big issue of how to get nvidia driver installed in the first place went through the process of compiling a different kernel. Instructions can be found here [http://howtoforge.com/kernel_compilation_debian_etch](http://howtoforge.com/kernel_compilation_debian_etch)

The kernel I used is 2.6.29.4

takes some time to get it done but it seems it's the main issue for the nvidia driver for my particular ancient card.

After the the compile is complete you need to find the driver that supports your card
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Geforce MX420-http://www.nvidia.com/object/linux_display_x86_96.43.11.html

what you need to do is logout and then press "ctrl-Alt-F1"
Login
then ```
sudo -s
``` to login to root
then to stop xserver
```
/etc/init.d/gdm stop
```run the installer its directory (in my case, desktop)
```
cd Desktop
```finally
```
sh NVIDIA-Linux-x86-version here-pkg1.run
```go through the installation and it should build the kernel somewhere

and now to work out the kinks
Effects are working but the title bar with the close/expand/minimize is missing and terminal along with other programs come up as white boxes.
This may be a temporary fix but 
```
metacity --replace & disown
```should correct this issue. I'm thinking it's just a temporary fix but I have read that it may be a compiz issue and in that case you need Advanced Desktop Effects which is found in synaptic as "compizconfig-settings-manager," and with this you check the option "window decoration." This issue is addressed in ubuntuforums.org/archive/index.php/t-795805.html.

I probably when through more than needed but it got the job done.
Not too shabby for a mac os gui dependent user, eh?
I believe they're almost the same build wise but I never though of installing everything through terminal.
1 point for a linux noob
hhaha
good luck
and if anyone has any comments or suggestions, please post.
thanks:D

note:there may be some unknown issues to this kernel that I may not be aware of but I'm not worrying I'm doing this for fun

---

### Post by blakew on 2009-06-05
I've had similar problems with the nvidia-glx-173 driver, for my nvidia geforce 5200FX. i've narrowed it down to the -rt kernel, which seems to be a huge mess (but i need that mess of a kernel for low latency audio). The nvidia kernel module can't be built for the rt kernel for some reason, which has left me with a nice and unusable system.

EDIT: oh and MMD1990, did you compile an -rt kernel? if not, then the solution will have no bearing on the issue (at least for me).

---

