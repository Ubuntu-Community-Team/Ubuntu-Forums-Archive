---
title: "OFFLINE beryl installation guide"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by estebancs on 2007-02-11
I write this guide after founding out how frustrating can it be to install new software for a linux newbie like myself, having no internet connection to download stuff from repositories using synaptic. The OFFLINE term means that you can't connect to the internet from ubuntu, but you can get connected from somewhere else like another computer, your office, your friend's computer... (I downloaded all from my winxp partition) AS far as I know THIS IS NOT THE RECOMMENDED WAY TO INSTALL IT, it worked for me, but I can't say it will work for you, comments and improvements to this guide are welcome as I'm NOT a linux expert, I'm just describing how I got it working.

[COLOR="Red"]Important[/COLOR], I have a nvidia geforce2 mx/mx 400 so this guide can be useful to nvidia card owners, but not for ati's.

This guide assumes you already have 3d acceleration working, you can check with this command:

For nvidida:

```
$ glxinfo | grep direct
```

For ati:

```
$ fglrxinfo
```

If your terminal returns

```
direct rendering: Yes
```

you're ready to go, otherwise you have to install your card drivers to enable hardware acceleration, I followed [_**this guide**_]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy"). (also just for nvidia, but certainly you can find an ati guide to install drivers googling or in this forum).


Next, in another computer you have internet connection head your browser to 

[http://ubuntu.beryl-project.org/dists/edgy/main/](http://ubuntu.beryl-project.org/dists/edgy/main/)

download all .deb packages you find there (I think they're 20 or something like that) EXCEPT FOR AQUAMARINE AND HELIODOR that are optional window managers for KDE and GNOME in that order. I don't know if I used all of them but it's better to be sure...

For the package xserver-xgl there are two more packages you need to download from [http://packages.ubuntu.com](http://packages.ubuntu.com) search for xserver-xgl and download the following packages:

- libglitz1_0.5.6-1_i386.deb
- libglitz-glx1_0.5.6-1_i386.deb

ok now you've downloaded all packages save them somewhere you can use with ubuntu (a CD, a usb flash drive, or a mounted partition you can see from ubuntu)

Install xserver-xgl fisrt, you may have to install the dependencies firts (the two packages you downloaded for xserver-xgl)

Now open the beryl_0.1.9999.1~0beryl1_i386.deb package, it will say that there's a dependence error with some package that isn't installed, search it in your donwloaded packages and install it (usually the second package will give you the same error and you will have to look and install the other package before), keep on doing the same until package beryl_0.1.9999.1~0beryl1_i386.deb stops giving you dependencies errors and you can install it.

Maybe there are some packages wich seem very tricky to install, like if you try to install the beryl package and it says that emerald must be installed first, but when you want to install emerald it says that beryl must be installed first (sounds insane but it do happens), if that happens do the following:

Open your console and install emerald package like this:

```
sudo dpkg -i emerald_0.1.9999.1~0beryl1_i386.deb
```

It will say you the same, that beryl isn't installed, don't listen and now install beryl:

```
sudo dpkg -i beryl_0.1.9999.1~0beryl1_i386.deb
```

Again it will say that emerald is not configured so beryl is left unconfigured or something like that, well don't listen it's already installed!

I found a way to configure both packages after this, if there's a better way LET ME KNOW

Go to synaptic and find some package YOU have installed before that will be easy to reinstall (I picked tuxracer), uninstall it, in the process emerald and compiz are configured, then I just installed tuxracer again.

NOW YOU HAVE BERYL INSTALLED!

To configure and start using it follow the instructions in this guide:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Configuration](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Configuration)

---

### Post by Masterj15 on 2007-03-01
Dude your the best:)

---

### Post by estebancs on 2007-03-01
> **Masterj15 said:**
> Dude your the best:)

Thanks! I'm glad you found this guide useful... you can upload some screenshots to let other ppl know this guide works:lolflag: ... I've been kinda busy so I haven't uploaded mine yet

---

### Post by Masterj15 on 2007-03-02
Sure!:) 

Oh, their is just one thing I need help with. I have a Nvida NV5 [TNT2/TN2 PRO].
I dont know what to do all that well. I am a newbie (OF Course!) at ubuntu and I just want to get those drivers before I install the packages.:)

---

### Post by estebancs on 2007-03-02
You mean you don't have hardware acceleration enabled yet? Well I really haven't heard a lot about your card but if it's a new one you have to install the [[COLOR="Blue"]nvidia-glx[/COLOR]]("http://packages.ubuntu.com/edgy/x11/nvidia-glx") driver, if it's old (like mine hehe) you must install [[COLOR="Blue"]nvidia-glx-legacy[/COLOR]]("http://packages.ubuntu.com/edgy/misc/nvidia-glx-legacy") drivers... this guide was very useful for me

**[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)**

you may also want to check this out

**[http://ubuntuforums.org/showthread.php?t=233241](http://ubuntuforums.org/showthread.php?t=233241)**

---

### Post by Masterj15 on 2007-03-02
Great! Thanks man. That help me out perfectly.

---

### Post by srikanth40 on 2007-09-15
thanks dood..!!! I got beryl installed on my computer. gr8 tutorial...

---

