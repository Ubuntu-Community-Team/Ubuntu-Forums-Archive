---
title: "ATI/Radeon Problems"
date: 2011-04-28
forum: Multimedia Software
---

### Post by chkneater on 2011-04-28
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

I was having troubles installing a new ATi RadeonHD 4830 after having an nVidia card installed. I tried the proprietary drivers and restricted drivers with no luck.  I followed this guide starting with the section on removing all the old drivers and configs.  I followed the guide and everthing was going perfect and I realized that nVidia drivers were still installed and that was causing part of the problem.

Anyway, there is a section about unpacking the .deb files, be careful if you paste this line and you're NOT using maverick.  Notice the end of the command?  Just change "maverick" to your distro name (lucid, natty) and it will work great.  IF however you accidentally ran that line, guess what? You gotta start over with removing your files and then starting from the beginning using the right .deb command this time.


My question to the ATI gods, after doing all this, I'm getting OpenGL rendering, fgl_glxgears runs perfect even if I move it all over the screen, Flight Sim runs great, BUT when I run " atiode -P60 -H localhost:0; echo $? " I get an error 2 which is fail for rendering errors.  Is this an actually error that needs fixing or just an annoying bug?

Also this command:

aticonfig --initial --input=/etc/X11/xorg.conf

yields this:

sudo] password for notsure: 
Found fglrx primary device section
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-2
notsure@notsure-desktop:~$ 

I know that libglx.so is where it should be, I noted as I installed Catalyst.

using 64bit AMD btw

---

### Post by cottfcfan on 2011-04-29
I'm having the same problem on Ubuntu 64bit & kubuntu 32bit.
It's the line:
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
thats worrying and I think causing the problem.
I've started a different thread, will let you know if I get anywhere.

---

### Post by chkneater on 2011-04-29
Thank you good sir (tip of the hat).  I'll keep an eye on your thread as well.

---

### Post by Marco309 on 2011-04-29
Same problem here. Using 64Bit Ubuntu 11.04

Found some errors in dmesg
[   28.686103] unity_support_t[1590]: segfault at 4 ip 00007f74fce37dce sp 00007fff15b0afa0 error 4 in libGL.so.1.2[7f74fcdd5000+c0000]
[   28.698509] unity_support_t[1592]: segfault at 4 ip 00007f06d3337dce sp 00007fff76b59e90 error 4 in libGL.so.1.2[7f06d32d5000+c0000]

...

[  402.864787] fglrxinfo[2586]: segfault at 4 ip 00007fcbd30a4dce sp 00007fffbc7ef370 error 4 in libGL.so.1.2[7fcbd3042000+c0000]

---

### Post by cottfcfan on 2011-04-30
Think ive managed to solve this problem.
Did a fresh install, then went here to the ATI Website and downloaded the 11.4 Driver to my Desktop:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
Then opened a terminal:
```
sudo su
```
enter password
```
cd Desktop
```
```
sh ./ati-driver-installer*
```
Answer all the questions then:
```
aticonfig --initial -f
```
Then Reboot.
Seems to have worked.

ps. the only problem with this method is you'll need to repeat it for every kernel upgrade.

---

### Post by chkneater on 2011-05-04
Out of purriosity tigerman above me, what does your fglrxinfo output, I'm just curious if it's using mesa, because it doesn't seem like you've installed any fglrx modules.  Under System>Adm>Hardwire drivers what is listed?



excuse me, cottcfcan, couldn't recall your name

---

### Post by cottfcfan on 2011-05-04
Hi chkneater,
I don't think you have to install anything else using the above method. My fglrxinfo is this:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 3.3.10665 Compatibility Profile Context

```
Which tells me its installed correctly.

---

### Post by chkneater on 2011-05-04
My fglxrinfo is identical but check " atiode -P60 -H localhost:0; echo $? " without the quotes obviously.  It will print a number 0-4.  thanks for your help.  I'm d/l the ATI file right now and I'm in between leaving it as is or trying your method.  I tried the ATI site a few weeks ago and had no luck with their driver at the time, but I noticed it is a new one since then.

---

### Post by cottfcfan on 2011-05-04
The number I get is "2".
What does that mean??

---

### Post by chkneater on 2011-05-04
That's what is worrying me, the code 2 is for 3d rendering errors.  I think it may be nothing since 3d is run through OpenGL and Catalyst works just fine, but I can't get an answer if the 3d rendering is there or not.

I submitted to launchpad.net so those geniuses should have an answer by now, if not I'm going to try the ATI installer again after purgin every damn driver and config file.

What driver is listed in your Hardware drivers btw?

---

### Post by cottfcfan on 2011-05-04
it should be fine.
I still have Lucid on my system the code is "2" there as well, and I know that driver is installed and working just fine.
The driver listed in hardware drivers is just "ATI/AMD proprietary FGLRX Graphics driver".
Please post back if you find out anything new.

---

### Post by Yellow Pasque on 2011-05-04
> Anyway, there is a section about unpacking the .deb files, be careful if you paste this line and you're NOT using maverick. Notice the end of the command? Just change "maverick" to your distro name (lucid, natty) and it will work great. IF however you accidentally ran that line, guess what? You gotta start over with removing your files and then starting from the beginning using the right .deb command this time.

You can avoid this issue by using the correct guide ;) [http://wiki.cchtml.com/index.php/Ubuntu#Installation](http://wiki.cchtml.com/index.php/Ubuntu#Installation)

As for libglx thing, let me look at my laptop and see what the deal is.

---

### Post by Yellow Pasque on 2011-05-04
I also get 2 for the atiode command on my laptop, but my 3D is fine.. so *shrug*. Look at fglrxinfo and test out fgl_glxgears.

---

### Post by chkneater on 2011-05-04
LOL Temuljin, the quote from two posts up was a quote from me from a different thread.  Yeah, I realized my error after installing Maverick drivers because I was following so many diff. threads and I had to go back and undo the Mav configs.  Then I installed the "correct" lucid files from that same guide and everything works, but many ppl are getting error two when checking 3d with aticonfig and aticonfig --initial -f says "error linking to libsomething.so" and permission denied while writing to xorg.conf (yes I sudo'd).

HOWEVER, Catalyst works fine and graphics are great, but I'm worried I won't be able to overclock or do other things with aticonfig since i can't even initialize it.

Oh yeah, and fglrxinfo and fglx_glxgears both are working fine also, so I'm thinking aticonfig isn't realizing OpenGL is doing the 3d.

---

### Post by Yellow Pasque on 2011-05-04
From changelog of ubuntu's fglrx:
> Rename fglrx-libGL.so and fglrx-libglx.so
-- [https://launchpad.net/ubuntu/natty/+source/fglrx-installer/2:8.840-0ubuntu1](https://launchpad.net/ubuntu/natty/+source/fglrx-installer/2:8.840-0ubuntu1)
So I'm not sure why aticonfig is still looking for them, unless you have an old version of aticonfig.

EDIT: Look at your /var/log/Xorg.0.log to make sure libglx is proper version and loading correctly.

---

### Post by chkneater on 2011-08-12
I wish I could definitively say which thing fixed it for me while I was mucking around with this issue, but it is now seemingly perfect.  It's using the FireGL driver and the correct lib is listed in the log, so maybe one of the kernel updates fixed it?!? I bet it was an old version of aticonfig and then a kernel update added the newer version when I reinstalled maybe, just like Temujin said.

---

