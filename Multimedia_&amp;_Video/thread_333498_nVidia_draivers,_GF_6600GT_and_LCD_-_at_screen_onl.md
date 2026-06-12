---
title: "nVidia draivers, GF 6600GT and LCD - at screen only stripes"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by spottraining on 2007-01-07
Hi

I have big problem with latest nVidia drivers and my LCD display. After enabling nvidia drivers I see only stripes at my screen. Nothing can be do.

I am usuing Ubuntu Edgi, kernel is 2.6.17-10-386, nVidia drivers are the latest. i am using script ([http://albertomilone.com/nvidia_scripts1.html)](http://albertomilone.com/nvidia_scripts1.html)).

System is upgraded from Dapper.  Before that evrything works fine and I have even XGL and 3D desktop installed.  Problem started, when I updated to latest kernel. Why system takes the 386 I dont know - before was 386. Then I get yust errors about wrong modules. But when I have make nvidia driver update also - then system starts. I see like behind stripes, that even Gnome starts (startup sound, at the place splash screen is also something) - but screen is so messed with vertical stripes that I cant see nothing.

I have try with diffrent xorg.conf files. Make new config with nvidia tool and also dpkg-reconfigure. Result is allvays the same. When I change back to open source nv drivers - evrything works.

Can someone give me some instructions - what else to look. I cannot change back to nvidia drivers from Ubuntu repos, beckuase I getting then errors about missing and wrong modules. X server is compiled to other module and so on.

But I need also 3D support.


Bellow are my Xorg.log, xorg.conf files (two what I have try).
Here is my Xorg.log file:
[http://spottraining.org/failid/Xorg.log.old.veaga.txt](http://spottraining.org/failid/Xorg.log.old.veaga.txt)


My first xorg.conf file (there is nvidia changed right now to nv - this works:
[http://spottraining.org/failid/xorg.conf.txt](http://spottraining.org/failid/xorg.conf.txt)
	
This is xorg.conf what is genereted with nvidia tool:
[http://spottraining.org/failid/xorg.conf.nvidia.txt](http://spottraining.org/failid/xorg.conf.nvidia.txt)

Any help and tip is welcome.

---

### Post by tseliot on 2007-01-07
Try the "uninstall" function of Envy and then the "install" function

---

### Post by spottraining on 2007-01-07
its done - result is the same. But envy installing also 9631 (or something 96xx) draivers. But its also now on newer set...

EDIT: my fault with driver version. I hava old envy script.

Now I getting GLX module error (failed to load module "glx", libglx.so - something about invalid ELF header at libGLcore.so.a) and also invalid nvidia.ko module format.

---

### Post by tseliot on 2007-01-07
```
sudo aptitude purge envy
```

then install the latest version of envy.

Use the "uninstall" function of Envy and then the "install" function

---

### Post by spottraining on 2007-01-08
> **tseliot said:**
> ```
sudo aptitude purge envy
```

then install the latest version of envy.

Use the "uninstall" function of Envy and then the "install" function
Its done and now its problem with this modules.

I uninstall the old drivers, then make reboot, then I install new drivers and X dont start. Errors are at previous post.

---

### Post by tseliot on 2007-01-08
Ok, let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by spottraining on 2007-01-08
About wrong nvidia.ko file - I removed again nvidia drivers. Then I discover, that nvidia.ko file is still at modules and other files. I remove manualy these. And then I install again nvidia drivers. Now - my monitor shows, that no signal.



I get new log file now also (terminal works in other tty-s). There is lot of errors.

New log file is here:
[http://spottraining.org/failid/Xorg.0.log.2.txt](http://spottraining.org/failid/Xorg.0.log.2.txt)

---

