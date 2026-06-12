---
title: "Nvidia Drivers broke my system"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by LsrLine on 2006-06-04
I can't get my computer to boot up x server.  I ran a script that would install nvidia drivers and it broke my sytem.  I have since uninstalled those drivers using hte same script and tried reinstalling them, but my internet connection doesn't seem to work any longer.  How would I go about just using the old nv drivers?  How can I edit xorg.conf from teh consle? thanks

---

### Post by Sutekh on 2006-06-04
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```
Find the "Device" section, and change the Driver to **nv**, for example
```

Section "Device"
    Identifier     "Device0"
    Driver         "**nv**"
    VendorName     "NVIDIA Corporation"
EndSection

```
Save the file (Ctrl+O) and exit (Ctrl+X), then try to start the GDM again
```
sudo /etc/init.d/gdm restart
```

---

### Post by LsrLine on 2006-06-04
Thanks for your help, but that didn't work.  Is there a way I can get some output so you can get a better idea of whats going on and why it won't start.

---

### Post by tseliot on 2006-06-04
[QUOTE=LsrLine]I can't get my computer to boot up x server.  I ran a script that would install nvidia drivers and it broke my sytem.[/QUOTE]
Can you explain what you mean by "broke"?

[QUOTE=LsrLine]I have since uninstalled those drivers using hte same script and tried reinstalling them, but my internet connection doesn't seem to work any longer.[/QUOTE]
Do you use a wireless card (or a modem that needs the restricted modules) to connect to the Internet?

---

### Post by chrroessner on 2006-06-04
Had the same problem.

cd NVIDIA-Linux-x86-1.0-8762-pkg1/

./nvidia-installer -aqsbN --x-prefix=/usr --x-module-path=/usr/lib/xorg/modules --ui=none --no-runlevel-check

Regards

Christian

---

### Post by LsrLine on 2006-06-04
[QUOTE=chrroessner]Had the same problem.

cd NVIDIA-Linux-x86-1.0-8762-pkg1/

./nvidia-installer -aqsbN --x-prefix=/usr --x-module-path=/usr/lib/xorg/modules --ui=none --no-runlevel-check

Regards

Christian[/QUOTE]

Tried that, but it didn't work.  I get No GLX Module loaded error and when I try to sudo apt-get anything it won't work because I have no internet.

---

### Post by chrroessner on 2006-06-06
Maybe you could remove the -s flag and see, if something went wrong while running the nvidia-installer?

---

### Post by cogadh on 2006-06-06
```
sudo dpkg -reconfigure -phigh xserver-xorg
```

That will rebuild your xorg.conf file from scratch with generic settings that will work. Once it is fixed, try re-running the nVidia configuration, that worked for me.

Same thing happened to me when I updated the nVidia driver. When I checked the corrupted xorg.conf file, it had entries for an ATi card. I haven't owned an ATi product for over 10 years.

---

### Post by LsrLine on 2006-06-10
[QUOTE=cogadh]```
sudo dpkg -reconfigure -phigh xserver-xorg
```

That will rebuild your xorg.conf file from scratch with generic settings that will work. Once it is fixed, try re-running the nVidia configuration, that worked for me.

Same thing happened to me when I updated the nVidia driver. When I checked the corrupted xorg.conf file, it had entries for an ATi card. I haven't owned an ATi product for over 10 years.[/QUOTE]

I tried sudo dpkg -reconfigure xserver-xorg it won't let me do -phigh...in any case it didn't fix anything.  This is wheat I've been getting:

dlopen: /usr/lib/xorg/modules/xgl/libglx.so: cannot open shared object file: No such file or directory

Fatal server error:
No GLX modules loaded
dlopen: /usr/lib/xorg/modules/xgl/libglx.so: cannot open shared object file: No such file or directory

FatalError re=entered, aborting
No GLX modules loaded

---

### Post by blastus on 2006-06-11
Its ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` not ```
sudo dpkg -reconfigure -phigh xserver-xorg
``` but you probably already know that. Have you tried stopping gdm and then running dpkg-reconfigure?
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by sfaoldun on 2006-09-11
I get the same problem (though I have connectivity). Installing the drivers with apt-get (as per the wiki) did nothing so I went and got the latest .run file from nVidia. After I got the development packages for xserver-xorg it seemed to install cleanly, but I still get the error message 

```
dlopen: /usr/lib/xorg/modules/xgl/libxgl.so: cannot open shared object file: No such file or directory

Fatal server error:
No GLX modules loaded
dlopen: /usr/lib/xorg/modules/xgl/libxgl.so: cannot open shared object file: No such file or directory

FatalError re-entered, aborting
No GLX modules loaded
```

It's right too, there are no files with that name in /usr/lib/xorg/modules/xgl/, just the following:

[FONT="Courier New"]libglcore.la
libglcore.so
libxglx.la
libxglx.so[/FONT]

Should it be attempted to load libxglx.so instead of libxgl.so? If so, can I just symlink the two?

---

### Post by petermarkab on 2006-10-11
The same thing happened to me today. I get an error when starting gdm saying no such file as libxgl.so 

i followed sfaoldun's suggestion of symlinking libxgl.so to libxglx.so and when i initiate gdm it doesn't work. however when i startx as normal user the x-server works and i get full-on hardware acceleration!

so its a fix of sorts but i'd appreciate any help fixing the gdm issue

---

### Post by ufalcon on 2006-10-14
Exact same issue here!  I was previously running I am running Edgy though (not sure if this is Dapper or Edgy section of forum).  I was running Xgl previously, perhaps this is a common clue?  I too can get X up and running using startx, so it's most likely a config file issue.  When I do a glxinfo, somewhat expectedly, I get a bunch of lines stating "Xlib: extension "GLX" missing...".

I ran the dpkg-reconfigure script as given earlier, and it looked like it was going to do the trick, but there must be something else in the xorg.conf that's not right!

---

### Post by ufalcon on 2006-10-14
Ok, my problem was stupid.  It was missing a glx lib that was supposed to be in an xgl path, and with the latest Edgy "patches" Xgl exploded - I simply needed to edit /etc/gdm/gdm.conf-custom and get it to stop using Xgl.  Looks like dri's not working though...

That's what I get for using a Beta version of the OS I guess!! :p

---

