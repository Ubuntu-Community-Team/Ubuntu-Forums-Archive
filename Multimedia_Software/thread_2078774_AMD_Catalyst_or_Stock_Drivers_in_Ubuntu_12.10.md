---
title: "AMD Catalyst or Stock Drivers in Ubuntu 12.10"
date: 2012-10-31
forum: Multimedia Software
---

### Post by sikemo on 2012-10-31
Hello,

I just installed Ubuntu 12.10 on an HP dm1z notebook with an AMD E-350 processor. I am not sure what drivers came installed when I installed the OS, fglrx? However, I have downloaded the latest AMD Catalyst 12.10 (same number as OS coincidentally) drivers and was wondering if I should install those instead. Is there a solid answer to this question, and if so, what would the procedure be?

Regards...

---

### Post by Isamu715 on 2012-10-31
If the stock drivers work fine for you there's no reason to replace them. By default Ubuntu uses the open-source AMD or Radeon driver, so it's not fglrx. The procedure for installing the Catalyst driver is described [HERE]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

---

### Post by sikemo on 2012-10-31
Thanks for that. Just what I was looking for. Movie Player seems to work just fine, but VLC is performing very poorly. Wanted to see if I could improve that with the AMD drivers.

---

### Post by Supermouse on 2012-11-01
I have a similar laptop.

Before doing anything with the drivers, please refer to this bug:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1069199](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1069199)


Catalyst driver makes Unity stop working, because of some incompatibility wih xorg.

I'm still waiting for the solution to this problem...

---

### Post by sikemo on 2012-11-04
Thanks. I am having issues with my desktop PC as a result of this. I cannot get HDMI audio working with the open source drivers, but video works fine. When I enable the fglrx drivers, Unity doesn't work, but HDMI audio works fine. !! Very frustrating. Let's hope there is a fix soon.

---

### Post by Yellow Pasque on 2012-11-04
For open-source HDMI audio, you'll need to add radeon.audio=1 (inside the quotes next to "quiet splash") to the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub and then run:
```
sudo update-grub
```

If that doesn't work, and you can try installing Catalyst 12-11 Beta: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

---

### Post by Linuxisfast on 2012-11-05
Catalyst drivers from Ubuntu work fine, in fact they have been specially catered to Ubuntu by ATI, just install it via hardware drivers and install the updates rather than regular. Then install xvba-va and libvpx. In vlc make sure gpu is checked under inputs and codecs. I have a small ASUS netbook with C60 and HDMI is a breeze.

---

### Post by sikemo on 2012-11-05
Excellent, thanks!

---

### Post by osnofla on 2013-01-13
I have an HP m6, and the default AMD driver performance (Radeon) is really poor. Also, my laptop is operating between 60-80°C, whereas with the official AMD driver (fglrx) it stays much cooler, around 40 °C, and the performance gain is quite measurable. The only drawback is that you must use the official tool for changing screen resolution, configuring multiple screens, etc, because it works separately from the default screen configuration utility in ubuntu. Minor detail, from my point of view.

---

### Post by webdesigncompanyla on 2013-03-29
> **Linuxisfast said:**
> Catalyst drivers from Ubuntu work fine, in fact they have been specially catered to Ubuntu by ATI, just install it via hardware drivers and install the updates rather than regular. Then install xvba-va and libvpx. In vlc make sure gpu is checked under inputs and codecs. I have a small ASUS netbook with C60 and HDMI is a breeze.


no they don't... if you have certain popular ATI cards like the ATI Radeon 3600 series then neither sound nor video works through the ATI driver, 12.10 loads the VESA driver but the sound through the HDMI still doesn't work...

it's something about the versions of X system not being compatible...

however it works fine in 12.04...

this is kind of a lame move by Ubuntu once again.

---

### Post by Yellow Pasque on 2013-03-29
> **webdesigncompanyla said:**
> it's something about the versions of X system not being compatible... however it works fine in 12.04...
this is kind of a lame move by Ubuntu once again.

It is not Ubuntu's decision/fault...

---

### Post by Mark Phelps on 2013-03-29
> **webdesigncompanyla said:**
> no they don't... if you have certain popular ATI cards like the ATI Radeon 3600 series then neither sound nor video works through the ATI driver, 12.10 loads the VESA driver but the sound through the HDMI still doesn't work...

it's something about the versions of X system not being compatible...

however it works fine in 12.04...

this is kind of a lame move by Ubuntu once again.
Actually, the "lame move" is by AMD -- who announced last summer that they were stopping Linux driver support for their HD 2x/3x/4x series cards. They decided only to support the HD5x series and newer -- and those are the ones that work with the newer X-server version in Ubuntu 12.10.

---

