---
title: "Ati glxgears: XIO:  fatal IO error 104"
date: 2008-11-30
forum: Multimedia Software
---

### Post by Apfilian on 2008-11-30
Hi there,

I installed Ubuntu 8.10 a few days ago and almost everything runs. 

However, there are still a few problems with my ATI-Card (X800). The ATI drivers are installed and when I type "fglrxinfo" I get the following text:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 Series
OpenGL version string: 2.1.8087 Release

A test with "glxgears" seems to run, but when I close the window, I get the following message:

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 49 requests (48 known processed) with 0 events remaining.

If I let glxgears run for a longer period of time, the desktop freezes and I have to reboot. There are also a lot of other applications which make my desktop freeze. For example, while I was writing this article, my desktop froze and I had to reboot. 
Using the open source driver, my desktop works however very well but as you probably know, it has a quite small performance. 

Is there any solution how I could get the Ati-driver work, or do I have to use the open-source driver?

thanks for your Help...

---

### Post by JupiterV2 on 2008-12-28
I have the exact same issue on my wife's computer using a Radeon 9600.

---

### Post by markbuntu on 2008-12-28
The fglrx driver has issues with glxgears so don't use it and you can avoid those problems. You might have noticed that ati is aware of this if you read the driver release notes.

---

### Post by lavinog on 2008-12-29
Also the driver that ships with ubuntu 8.10 is a beta driver of Catalyst 8-11.
You might find that upgrading to the full 8-11 or even the current 8-12 will improve your issue.
I can't say for sure thought that it will fix the issue, but 8-12 is working much better than the 8-11 and 8-11 beta on my system.

---

### Post by Apfilian on 2009-01-06
Hi,
thanks for your replies. As lavinog proposed I installed Catalyst 8-12. However, this did not solve the problem at once. Then I tested a view options with "aticonfig". By chance I found a few options which solved my problem. 

```
sudo aticonfig --acpi-services=off
```

and/or

```
sudo aticonfig --od-disable
```

I hope that maybe one of this commands may help JupiterV2 or someone else, as well!

---

### Post by Apfilian on 2009-02-06
Hi there,
since the new Version 9.1 of ATI Catalyst has been released, there are no desktop-freezes anymore. I recommend to download it, if you have the problems I had.

[http://ati.amd.com/support/drivers/de/linux/linux-radeon.html]("http://ati.amd.com/support/drivers/de/linux/linux-radeon.html")

---

