---
title: "nVidia driver is not working (offline installation)"
date: 2006-07-30
forum: Multimedia &amp; Video
---

### Post by jakonj on 2006-07-30
Hello everyone! Firest of all i must tell that my english is wrealy bad so try to understand what i'm gonna write 

here:

I have Abit Siluro (i think that the manufacturer is not important!?) GF 4 Ti (64mb). i have ubuntu 6.06 and i added 

next packages into system (from official cd):

- build essential (gcc, make, dpkg handling etc.)
- binutils

I think that is enough to install nvidia driver but there is some error! I have NVIDIA-Linux-X86-1.0-8178_p.run 

(full name) and i tried to install it this way:

```
root@ubuntu: /home/krak/nvidia.run
```

there is no need for sudo because i log in as root (in Grub i choose "Ubuntu ...(kernel version) failsafe)

First driver displays error  withthis content:
```
Skipping the runlevel check (the utility 'runlevel' failed to start)
```

And i hit "ok"
Next therte is installation and after that he asks me to auto config the xorg.conf file and i hit "ok"
Reboot

after that there is error:
```
X server failed to start...
``` or something like that!

and i tried this way (before that i installed ubuntu again (it's fast so it's not that painfull :>)
everythig is same as done before but when he asked me to auto config xorg.conf i hit "no" and i edited manualy 

taht file! Here's what i do:

```
i looged in as user (not root),
enter the terminal and writte:

sudo gedit /....(path to xorg file in etc directory (i dont remeber the full path right now))

saved it

```

reboot

there is same error as before! So what can i do? 

[note] be aware that my internet is not in funkcioning  so i want offline instalatin (no apt-get cr*p) in any case ;)

tnx for support

---

### Post by tseliot on 2006-07-30
**There's no need to reinstall Ubuntu when the Xserver crashes.**

Just follow these steps:

boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine


**About the offline installation**:

I have never tried it and I don't know if it works:
Type:
```
sudo apt-cdrom add
```

then it should ask you to insert Ubuntu's cd.

Then (after the previous process finishes) type:
```
sudo apt-get update
```

```
sudo apt-get install linux-386 nvidia-glx nvidia-xconfig
```

```
sudo nvidia-xconfig
```

Then log out and press CTRL+ALT+Backspace

---

### Post by jakonj on 2006-07-30
nope... it's not working. Look at terminal log (it's not log (i dont now how to create terminal log)):

---

### Post by tseliot on 2006-07-31
Download this package from another computer (in which you have an internet connection):
[http://ftp.port80.se/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/nvidia-glx_1.0.8762%2b2.6.15.11-3_i386.deb](http://ftp.port80.se/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/nvidia-glx_1.0.8762%2b2.6.15.11-3_i386.deb)

Then move the package to your computer with Ubuntu (use a USB pen for example):
Double click on the .deb file and install it.


Then IF AND ONLY IF the installation of the package went fine, set up your xorg.conf:

sudo nano -w /etc/X11/xorg.conf

Get to the Section "Module" and put a "#" before load dri and load glcore so that it looks like this:

```
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    #Load           "dri"
    #Load           "glcore"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
```

Then get to the Section device and set the driver to "nvidia" (instead of "nv" or "vesa"):
```
Driver		"nvidia"
```


If it works I can add the offline installation to my guide.

---

### Post by jakonj on 2006-07-31
It's working :)

After the 2(nd) advice ist' s ok and 3d i fully working ( i tried one 3d game (tribalTroubledemo) and it's working with good picture without blur and all that c**p)!

So, you can put to your guide (but you should say that this metod is working on ubuntu with 2.6.15-23 kernel (witch i have))

tnx for support

---

### Post by tseliot on 2006-07-31
> **jakonj said:**
> It's working :)

After the 2(nd) advice ist' s ok and 3d i fully working ( i tried one 3d game (tribalTroubledemo) and it's working with good picture without blur and all that c**p)!

So, you can put to your guide (but you should say that this metod is working on ubuntu with 2.6.15-23 kernel (witch i have))

tnx for support

Thanks for reporting. :D

---

