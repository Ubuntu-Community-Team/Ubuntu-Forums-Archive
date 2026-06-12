---
title: "no screens detected after nvidia drivers installed"
date: 2008-12-28
forum: Multimedia Software
---

### Post by Kimbie on 2008-12-28
Just installed 8.10 on my C2D, 8800GTS and 6800, installed the patches and rebooted and works fine.

If I try to install the nVidia drivers, either through restricted drivers or EnvyNG on a reboot X fails to load, complains no screens found.

Now with 8.04 this didnt happen, so I tried installing 8.04 then upgrading to 8.10 and the same thing happens

Any ideas on how to fix this?

Kimbie

---

### Post by easybake on 2008-12-28
> **Kimbie said:**
> Just installed 8.10 on my C2D, 8800GTS and 6800, installed the patches and rebooted and works fine.

If I try to install the nVidia drivers, either through restricted drivers or EnvyNG on a reboot X fails to load, complains no screens found.

Now with 8.04 this didnt happen, so I tried installing 8.04 then upgrading to 8.10 and the same thing happens

Any ideas on how to fix this?

Kimbie

In envy try to load the previous version of the driver and not the latest.

---

### Post by Kimbie on 2008-12-28
Yup tried that both the 172 and 177, but once rebooted, I get a black screen with text login, and if i log in then type startx, I dont get anything just comes back with No screens found

---

### Post by nromanel on 2008-12-29
Hey There, here was my solution to the "No Screens Detected" error after installing the restricted drivers.

The solution for me was to define the BusID in the device section of the xorg.conf file.

**1. Find the BUS ID of your card. In a shell type:**:
```
lspci | grep -i nvidia
```

The Output should look something like this:
```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

```

If you have a motherboard with an nvidia chipset, you will have more entries, look for the VGA entry.

In this case the Bus ID is 01:00.0

**2. Add the BusID to your xorg.conf file**

In your favorite text editor, open up your xorg.conf file and find the "Device" Section. After the last line of the section add
```
BusID      "PCI:1:0:0"
```
[I][COLOR="Red"]
Remember yours may be different![/COLOR][/I]

In my example, the final Device section looks like this:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
EndSection
```

Hope This Helps!

---

### Post by Kimbie on 2008-12-29
> **nromanel said:**
> snip

Thanks for that, I will give that ago.

How do I edit a text file in terminal? Only every used gedit in the gui, and where will I find the config file you speak of?

Kimbie

---

### Post by nromanel on 2008-12-29
The file you are after is **/etc/X11/xorg.conf**

The simplest text editor is **nano**

In a shell type:
```
sudo nano /etc/X11/xorg.conf
```

When you're done editing, save the file using Ctrl+O

Cheers!

---

### Post by Kimbie on 2008-12-30
> **nromanel said:**
> The file you are after is **/etc/X11/xorg.conf**

The simplest text editor is **nano**

In a shell type:
```
sudo nano /etc/X11/xorg.conf
```

When you're done editing, save the file using Ctrl+O

Cheers!

No that didnt work, that file doesnt exist at all.  I was told 8.10 doesnt use xorg.conf anymore?

Kimbie

---

### Post by nromanel on 2008-12-30
I don't see how that's possible. do an ls on the directory /etc/X11/
You should see maybe xorg.conf.failsafe and a few others.

Have you tried downloading the latest drivers from nvidia and doing an install? When the nvidia installer finishes, it creates a new xorg.conf file to use the nvidia drivers.

---

### Post by Kimbie on 2008-12-30
> **nromanel said:**
> I don't see how that's possible. do an ls on the directory /etc/X11/
You should see maybe xorg.conf.failsafe and a few others.

Have you tried downloading the latest drivers from nvidia and doing an install? When the nvidia installer finishes, it creates a new xorg.conf file to use the nvidia drivers.

I will have a look at the folder on my next reboot, in Vista at the moment.

Ive tried installing drivers, through Envy, Restricted Drivers, and by downloading the file from nvidia.  All have the same effect

Kimbie

---

### Post by Kimbie on 2008-12-31
I had to browse to /x11/ and did an ls and there was an xorg.conf file.

I did a sudo nano edit on it, and it had some information in but nothing relating to screens, graphics cards.

What is the way round this? Baring mind I have no gui, not even in recovery mode.

Kimbie

---

