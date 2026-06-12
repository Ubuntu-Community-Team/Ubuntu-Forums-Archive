---
title: "DRI not enabled, and GL version = 1.2"
date: 2008-08-15
forum: Multimedia Software
---

### Post by kerryhall on 2008-08-15
So running glxinfo gives me:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

So I did "export LIBGL_DEBUG=verbose" and ran glxinfo again, same damn thing! Why do programs have such a hard time recognizing environment vars?

And for some reason:
OpenGL version string: 1.2 (2.1.2 NVIDIA 173.14.12)
#&@$(*$&*(#*$!!!! :mad:

So I downloaded the source for Mesa 7.0.3, compiled and installed it, same problem. 

I did make linux-x86, maybe wrong target?

Anyway, anyone know how to get OpenGL 2.1 working, and also enable DRI?

Thanks!!

---

### Post by shak541 on 2008-08-15
check xorg.conf to see if u have option DRI:disabled... i had this in a fresh install just 2 days ago... also do u have nvidia or ati graphics card?

---

### Post by kerryhall on 2008-08-15
Section "Module"
    Load	"dri"
    Load        "glx"
EndSection

I added in the Load "dri" line, but then realized that x.org loads it by default. (right?)

I have an Nvidia card, one that is def capable of OpenGL 2.1

---

### Post by shak541 on 2008-08-15
check your driver section to make sure you are using nvidia.. or nv.... depends on what graphics card you have. also try to see if going into terminal and going to nvidia-settings works....

---

### Post by kerryhall on 2008-08-15
Geforce 6600 GT

driver is "nvidia" should I try "nv" ? 

nvidia-settings:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

I run nvidia-xconfig and restart x, no effect.

I have been doing full reboots, but just for speed, does ctrl-atl-backspace restart x entirely?

---

### Post by shak541 on 2008-08-15
yeah ctrl-atl-backspace shoudl restart x competly/... sometimes it may not... try nv instead... also try going into system-administration-restricted drivers management to see if your driver is there...

---

### Post by kerryhall on 2008-08-15
system-administration-restricted drivers management

Wow, I have no idea how that box got unchecked. I tried downloading and installing the latest nvidia drivers from nvidias web site, was that the problem? Should I not do that in Ubuntu?

---

### Post by shak541 on 2008-08-15
the latest drivers may work as some older cards are supported only by nvidia-glx and newer ones by nvidia-glx-new... check that box and do a full restart... that should work.. :D ... just make sure that box is checked and ubuntu should take card of it for you! :D

---

### Post by kerryhall on 2008-08-15
Ok, so the box wasn't checked. I checked it and restarted X. Now I am in "low graphics mode" but glxinfo says that i'm now running mesa 7.0.3 and opengl version = 2.1! horray! but glxinfo ALSO says that dri is not enabled. What the hell? and nvidia-settings still says that i'm not using an nvidia driver. i run nvidia-xconfig again to generate the config and reboot, still no effect. I am going to try changing "nvidia" to "nv" and seeing what happens. any thoughts? keep in mind im using a version of mesa that i built myself, perhaps i built it wrong?

---

### Post by shak541 on 2008-08-15
sorry for not responding for so long... ummm... make sure that it is actually using nvidia or nv... i remember mine would not change before... try that out... also make sure once more that the box is checked,... sometimes this can get really annoying... ive been through this... and its not fun!! .. :(

---

### Post by kerryhall on 2008-08-16
It's ok! Yeah the box is checked. so far I have not solved this problem.

---

### Post by kerryhall on 2008-08-16
Ok, I changed the driver from "nvidia" to "nv" with no effect.

---

### Post by shak541 on 2008-08-16
umm.. yikes... try to reinstall the driver by checking then unchecking the box. also try to run sudo dpkg-reconfigure xserver-xorg. and let it autodetect just about everything. Im surprised checking the box did not work. I guess after this envyng might be a solution. Unfortuately i have not used envyng enough to help you out but a few minutes of googling around should help you out. :D

---

### Post by kerryhall on 2008-08-16
I have already tried envy-ng to no effect.

Am now trying sudo dpkg-reconfigure xserver-xorg

---

### Post by kerryhall on 2008-08-16
Ok, so envy gets me out of low graphics mode, but it unchecks the box, and now glxgears is going reallyyyy slow.

should i check that box again?

and i have not figured out how to get nvidia-settings to work yet...

---

### Post by kerryhall on 2008-08-16
I seem to have gotten the driver working again, however direct rendering is still not enabled.

I had to follow this:
[http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)

but first i had to do
sudo apt-get remove libgl1-mesa-glx
then
sudo apt-get install libgl1-mesa-glx

which for some reason uninstalled everything that depended upon it! Is there anyway i can uninstall and then reinstall a package without everything that depends upon it getting messed up?

thanks!

---

### Post by shak541 on 2008-08-17
i honestly dont know a way... my computer has an issue with python-common and i can;t reinstall or almost everything gets removed... if you find a way could you point it out to me please? after that all i can say is play around with it. that's what i did when i had this problem. never found a solution but rather playing with it for a day worked. :( sorry about not knowing how to solve the problem.

---

### Post by kerryhall on 2008-08-19
It's all good, I'll figure it out sooner or later!

Hmmm as for python-common, I am sorry, I don't know.

I couldn't seem to find the package python-common in the apt repository.

That seems to be a problem with apt in general. If you want to remove some package, it removes all the packages that depend on it!

Will reply here if I figure it out.

---

