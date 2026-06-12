---
title: "nVidia 2 GeForce, Compaq Presario 6000 series, Compaq 7550 monitor"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by jasex on 2008-03-01
I am having terrible times trying to learn about setting up xorg.conf for nvidia cards, mainly cause I am only accustomed to my former Intel cards: my 815 and 945, dell desktop, and toshiba laptop respectively. I moved into this Compaq box cause I thought the graphics would be a step up from the dell box, so I moved my sound blaster card, and my modems, and NIC over, and actually I did try to plug in my AGP NVidia card as well originally when I had windows on this box temporarily due to an extended visit from a linux incompetent guest (stubborn as a mule at that) but it caused the startup of the bios to lock up =( no multi monitor mode for me... anyways, if you guys could tell me what info you need about my machine, I'd love to attain a nice 1280x1024 display as I know it is capable of displaying it. Any help is furthermore forehandedly greatly appreciated. I believe it can actually sucessfully display 1600x1200 on this but I cannot recall if those tests were sucessful.

I am running Ubuntu 7.10, and running the updates now. I did try the restricted driver but that froze up my X server. I am pretty comfortable with the command line, so if it involves me playing with the restricted driver and going into recovery mode to tweak it, that is fine, don't newb it up for me :)

(EDIT: For iteration the built in card is also a nvidia geforce 2)

---

### Post by justsomedude on 2008-03-01
I'd start with finding out which exact driver you need, take a look at this list: [http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.11/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.11/README/appendix-a.html)

Download the appropriate driver and backup your xorg.conf:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then, uninstall the old driver and install the downloaded one. The procedure is a bit tricky, if you need help with that let me know.

Run

```
nvidia-xconfig
```

to configure your xorg.conf auttomatically. If you cannot set your desired resolution then, we can have a look at your xorg.conf. 

Keep in mind that every kernel upgrade will break your graphics and you will have to repeat this procedure. You can always use the vesa driver to get a graphical environment, if you edit the section "device" in your xorg.conf like this:

Section "Device"
    Identifier     "Card0"
    Driver          "vesa"
    VendorName     "nVidia Corporation"
    BoardName      "MCP51 PCI-X GeForce Go 6100"
    BusID          "PCI:0:5:0"
EndSection

Everything besides Identifier, Driver, VendorName, BoardName and BusID has to be uncommented with a "#". Of course, your xorg.conf will look a little different...

---

### Post by jasex on 2008-03-02
01:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)


that's what I get from LSPCI

And this...

thursday@Azumi:~$ lspci -n | grep 0300
01:00.0 0300: 10de:01a0 (rev b1)
thursday@Azumi:~$ 

How do I know which matches my card?

I know it's an nForce board I believe. From what I had to do to get it all working 100% properly under windows

---

### Post by justsomedude on 2008-03-02
Ok, I think you need the legacy driver. You can get it here:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

You need this one:

Latest Legacy GPU version (1.0-96xx series): 96.43.05, if you have Ubuntu 32bit installed. 


Uninstall your current nvidia driver and make sure you have:

gcc
linux-headers-<for your kernel>
pkg-config
xserver-xorg-dev
libc6 

installed. You can find out your exact kernel version by 

```
uname -r
```

Make sure nvidia-glx is **not** installed.

Open Nautilus as root and remove:

/etc/init.d/nvidia-glx
/etc/init.d/nvidia-kernel
/lib/linux-restricted-modules/.nvidia_new_installed

if they are there. You can make backups of these files if you wish, of course.


Open linux-restricted-modules:

```
sudo gedit /etc/default/linux-restricted-modules
```

or

```
sudo gedit /etc/default/linux-restricted-modules-common
```

and disable nv and nvidia, like this:

```
DISABLED_MODULES="nv nvidia_new"
```


Leave your graphical environment with [Ctrl] + [Alt] + [F1] and login.


Stop gdm:

```
sudo /etc/init.d/gdm stop
```


Navigate to the folder you have downloaded your driver to:

```
cd ~/home/usename/Desktop #or wherever it is
```


...and start the installation:

```
sudo sh NVIDIA*.run
```

Answer everything with "yes". After you're done, reboot. Now the driver should run and we can take care about your xorg.conf. Remember every kernel update will break your graphics and you will have to reinstall.

---

