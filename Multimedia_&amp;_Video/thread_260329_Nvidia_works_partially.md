---
title: "Nvidia works partially"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by Final on 2006-09-18
Here is my problem - I've been having this since Breezy 5.10 and now this is at Dapper 6.06 too.

I use nforce4 chipset motherboard (ASUS A8N-SLI) and 2x club 3d's geforce 6600 gt cards on pci-express. As a driver I use "nvidia" from nvidia-glx, which I have installed without any problems. However if I install nvidia-settings and start to use it through nvidia-settings command on terminal I keep getting this:

```


> nvidia-settings
ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.
```
However the program do start, but with just five options to change:
```


ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
```
:/ Yep.. Nothing about for instance SLI settings, anti-aliasing etc.

Then, I tried to install the official nvidia drivers (8774) (I removed the nvidia-glx) and installed them without any problems (removed restricted modules etc. Method 2 install). Though still the same error occurs when I begin to use nvidia-settings.

Also in both cases (nvidia-glx, nvidia's official drivers) when I put:
```


> glxinfo | grep rendering
direct rendering: No
```

:/ Yes, this exact problem has occured on breezy too, the very same bug when I use "nvidia" driver.
Here's my xorg.conf: [http://pastebin.ca/175472](http://pastebin.ca/175472)
And nvidia's bug report log: [http://pastebin.ca/175464](http://pastebin.ca/175464)

Thanks for possible answer.

Edit: Strange matter is that when tried I used Alberto Milone's "envy" script to install the drivers (no nvidia-glx or manually installed nvidia's official drivers installed yet then). I got a message that said that my card is not supported (in both remove and install drivers) and geforce 6600gt should be supported I think.

---

### Post by clarke.rainey on 2006-09-19
I am having the exact same problem with my Geforce 6800 Ultra in my laptop and an external monitor... only mine just gives the no NV-CONTROL extension error...

---

### Post by LetsLinux on 2006-09-19
I don't know if this is of any help. But if you are using the NV driver that comes with Ubuntu (Dapper) - then you might want to check out this link: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) as it helped me out with the issues I had with my GeForce2 MX 440 (nVidia2).

Jonas

---

### Post by Final on 2006-10-02
LetsLinux: It didn't help. Thanks anyway.

I really have no clue what causes this. Well, at Xorg.0.log (at nvidia-bug-report) there is:
```

(II) Module glx: vendor="NVIDIA Corporation"
     compiled for 4.0.2, module version = 1.0.8762
     Module class: X.Org Server Extension
     ABI class: X.Org Server Extension, version 0.1

```
Why it claims that I use 8762 version driver as I have compiled 8774 driver? Yeah, this should not be any error I think, but odd still.

Edit: I must emphasize that I'm not using XGL/Compiz (as of that direct rendering: No thing), but I have tried to install them and the odd thing is that all effects work perfectly but when I try to turn the cube, the screen starts to flicker and flash and I never "enter" to the 3D space, just suddenly transform myself to other desktop (I think that this is the reason of the bug). 
However, I have tried to install just plainly from vanilla Dapper (and Breezy) and still the bug occurs (just from boot-CD-install-update kernel-gotonvidiapage-download driver-install-> bug (no XGL installed)). I think the problem is either something at installion process such that I have done something wrong (however, I've tried to install many times already and this bug occured on breezy too, I've used different methods and different drivers (nvidia-glx or nv for instance) and still the bug occurs) or my hardware (nforce4 chipset pci-e port maybe? or even the club3d's geforce 6600gt 128MB) is not supported in ubuntu (/or on those drivers).

---

### Post by tseliot on 2006-10-02
> **Final said:**
> Edit: Strange matter is that when tried I used Alberto Milone's "envy" script to install the drivers (no nvidia-glx or manually installed nvidia's official drivers installed yet then). I got a message that said that my card is not supported (in both remove and install drivers) and geforce 6600gt should be supported I think.

That means that your card ID is not in the list of the supported cards:
[http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-a.html)

You can check your card ID by typing:
```
lspci -n | grep "0300" | cut -d " " -f3 | sed s/.*://
```

---

### Post by tseliot on 2006-10-02
> **LetsLinux said:**
> I don't know if this is of any help. But if you are using the NV driver that comes with Ubuntu (Dapper) - then you might want to check out this link: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) as it helped me out with the issues I had with my GeForce2 MX 440 (nVidia2).

Jonas

Follow Method 2 of my guide UNLESS you use a wireless card:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2)

In my guide I suggest to remove the restricted modules (which are causing the driver mismatch)

---

### Post by Final on 2006-10-02
Thanks for answer.

```

> lspci -n | grep "0300" | cut -d " " -f3 | sed s/.*://
0140
0140

```

[http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-a.html)

GeForce 6600 GT 	0x0140

- yep, match it is - I use two identical cards in SLI, I have tried to change their order, just to use one at time or two at time or use PCI-e-x16-2 slot instead of PCI-e-x16-1 slot (currently using the slot 1) (and changed the SLI-card other side when using just single card).

---

### Post by tseliot on 2006-10-02
> **Final said:**
> Thanks for answer.

```

> lspci -n | grep "0300" | cut -d " " -f3 | sed s/.*://
0140
0140

```

[http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-a.html)

GeForce 6600 GT 	0x0140

- yep, match it is - I use two identical cards in SLI, I have tried to change their order, just to use one at time or two at time or use PCI-e-x16-2 slot instead of PCI-e-x16-1 slot (currently using the slot 1) (and changed the SLI-card other side when using just single card).

The ID 0140 is included in Envy's list of supported cards as well.

Make sure that you are using Envy's latest version:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Final on 2006-10-02
> **tseliot said:**
> The ID 0140 is included in Envy's list of supported cards as well.

Make sure that you are using Envy's latest version:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I updated envy, but still the same thing happens:

```

...
Please select one of the activities displayed above and press ENTER:

1
Error: your card does not seem to be supported by the Nvidia driver
0140
0140
```

I really think there is something wrong with my hardware (though in windows there are no errors of these kind).

---

