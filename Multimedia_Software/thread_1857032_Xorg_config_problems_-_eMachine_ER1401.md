---
title: "Xorg config problems - eMachine ER1401"
date: 2011-10-09
forum: Multimedia Software
---

### Post by markturnip on 2011-10-09
Hey I've bought an eMachine ER1401 Desktop to use as an HTPC, but having difficulty displaying an X window through HDMI.

I'm running minimal Ubuntu: Ubuntu 10.04.3 LTS.

The computer specifications suggests that I have a "Nvidia Geforce 9200" however, my lspci suggests otherwise: 

02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200] (rev a2)


I downloaded the 9200 drivers from NVidia: "NVIDIA-Linux-x86_64-285.05.09.run" & installed. 

Upon deleting my "xorg.conf" I can run a X window over HDMI. After running nvidia-xconfig I can no longer create a window and get the following when running xinit:

(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Here's my Xorg log: [http://pastebin.com/VEncqQzu](http://pastebin.com/VEncqQzu)



Perhaps I've installed the incorrect drivers? 

Any advice offered will be much appreciated!

Thanks, 

MT

---

### Post by markturnip on 2011-10-11
Is anyone able to offer any troubleshooting or advice?

This issue may not be specific to the computer model I have.

Thanks, 

Mark

---

### Post by lkjoel on 2011-10-11
Try following this tutorial: [http://lkubuntu.wordpress.com/2011/08/30/quick-and-easy-way-to-fix-x11-issues/](http://lkubuntu.wordpress.com/2011/08/30/quick-and-easy-way-to-fix-x11-issues/)
If it works, then try using the Additional Drivers tool to install the nVidia drivers.

---

### Post by markturnip on 2011-11-12
Thanks lkjoel, unfortunately that hadn't sorted it. 

I'm still having trouble, is anyone else able to offer any advice?

Thanks.

---

### Post by markturnip on 2011-11-12
I have no problem with using VGA. However whenever I do & set the resolution to what should be native (1440x900) the whole image is shifted to the right by about 300 pixels.

Perhaps someone can offer some advice as to why that's happening with VGA?

Re the above, I tested using a higher resolution screen & it works fine over HDMI. So must be my display, but despite what resolution I set it to - I still end up getting "Mode not supported".

---

### Post by BicyclerBoy on 2011-11-12
You should re-post your /var/log/Xorg.0.log..

If you post (2) versions, with the problem TV connected by VGA & HDMI, it may point to the problem..

Your previous Xorg.0.log shows you did not install correctly.
The nVidia installer method is not recomended..just use synaptic package manager to install nvidia-current.

For 10.04.3 You can get nvidia280 & modaliases, vdpauinfo & libvdpau from:
```
https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=lucid

```

---

### Post by markturnip on 2011-11-13
Thanks, I will post my logs shortly. 

But I will note that when booting using VGA my bios screen is all shifted to the right. This gives me reason to believe it may not be the driver? 
When selecting 1024x768 with nvidia-settings, the screen does fill entirely (not shifting to the right)

> **BicyclerBoy said:**
> You should re-post your /var/log/Xorg.0.log..

If you post (2) versions, with the problem TV connected by VGA & HDMI, it may point to the problem..

Your previous Xorg.0.log shows you did not install correctly.
The nVidia installer method is not recomended..just use synaptic package manager to install nvidia-current.

For 10.04.3 You can get nvidia280 & modaliases, vdpauinfo & libvdpau from:
```
https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=lucid

```

---

### Post by BicyclerBoy on 2011-11-14
The nVidia driver is an X server driver only..it plays no part in the boot plymouth greeter screens. It is only active if an X screen is..

All video cards must provide low level text & VGA compatible interfaces, some other kernel framebuffer driver is at work during boot..

There are many supported boot/grub video modes..

---

### Post by markturnip on 2011-11-14
Thanks for this info. 

Should I be trying to get the video card working for the bios first then?
Or is the mismatch irrelevant once the driver is loaded?

> **BicyclerBoy said:**
> The nVidia driver is an X server driver only..it plays no part in the boot plymouth greeter screens. It is only active if an X screen is..

All video cards must provide low level text & VGA compatible interfaces, some other kernel framebuffer driver is at work during boot..

There are many supported boot/grub video modes..

---

### Post by BicyclerBoy on 2011-11-14
Forget about boot screen video mode until you have fixed the other problems.
It is relevant.

Are you using HDMI or VGA into external display.?

TVs have very different VGA capabilities to HDMI (HDCP).
 Xorg.0.log ?

---

### Post by markturnip on 2011-11-17
For the sake of trying I installed Ubuntu Desktop.

For now I'm forgetting about HDMI. But am still having the same issue with VGA. 

Here's my lastest Xorg log: 

[http://pastebin.com/edzwuLRS](http://pastebin.com/edzwuLRS)

Just to repeat, that the screen is filled entirely when I select any other resolution. But once I select the native resolution the screen shifts to the right. 

Thanks again.

---

### Post by gordintoronto on 2011-11-17
This might be something you can fix from the TV's menus.

---

