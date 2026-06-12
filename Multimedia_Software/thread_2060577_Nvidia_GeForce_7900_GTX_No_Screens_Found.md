---
title: "Nvidia GeForce 7900 GTX No Screens Found"
date: 2012-09-20
forum: Multimedia Software
---

### Post by lillypad on 2012-09-20
Hey Guys, I would love to have the 3D effects in compiz but when I install the package nvidia-current when I reboot the computer boots into ttyl1 saying no screens found. I did try installing a package from here that configures the xorg.conf file for nvidia but still no avail. Everything works just fine without the driver installed though since I'm going to be using Kdenlive for video editing it would be great to have a gfx card working properly.

lspci gives:
```
01:00.0 VGA compatible controller: NVIDIA Corporation G71 [GeForce 7900 GTX] (rev a1)
```I did follow this tutorial by another user:
[https://www.youtube.com/watch?v=ReyT56rTWnA](https://www.youtube.com/watch?v=ReyT56rTWnA)

However this did not fix the issue. Is anyone else having the same problem?

---

### Post by BicyclerBoy on 2012-09-20
What ubuntu version ?
What nVidia driver version..

When you install & reboot to your console tty screen:
- login then run
- sudo nvidia-xconfig
(11.10, 12.04)
sudo service lightdm start
(10.04)
sudo service gdm start

if X server/GUI comes up then use:
nvidia-settings
(if necessary)..

If all/any of this fails post this file:
/var/log/Xorg.0.log

---

### Post by lillypad on 2012-09-21
```
The NVIDIA GPU at PCI:1:0:0 does not have the necessary external power cables attached; X cannot use this GPU until the problem is rectified. Please shut down your computer, open it's case, and attach all of the appropriate power connectors. Please see the documentation provided with your NVIDIA GPU for more details.
```

I have not taken this device out of the computer and it's always worked fine with windows before. Why is it looking for a power cable?

---

### Post by lillypad on 2012-09-21
Hello, thank you for getting me on the right track! Here is the solution:

```
sudo apt-get install nvidia-current
sudo reboot
```

reboot..

login to ttyl1

```
sudo nvidia-xconfig
sudo nano /etc/X11/xorg.conf
```
add the following line under screens:
```
Option         "NoPowerConnectorCheck" "True"
```

Then start your lightdm service
(11.10, 12.04)
```
sudo service lightdm start
```
or
(10.04)
```
sudo service gdm start
```

Now you should be able to boot into the GUI!
Thank you for getting me in the right direction very appreciated!

---

### Post by BicyclerBoy on 2012-09-21
7900GTX is prob a power hungry GPU..I guess it has TDP 120W

It would make sense to fit the extra power cable..the warning is not just for fun..
All ATX2 PSUs come with a couple of video card power cables..
A cable is cheaper than a new mobo..

---

### Post by lillypad on 2012-09-22
Yeah, I'll probably stop at future shop here soon to take a peak for some pwr cables i got this second hand so that is probably why it didn't come with one. The funny thing is, is that there were no warnings when running windows on here with it.

---

### Post by BicyclerBoy on 2012-09-22
The std PSU (without detachable wiring harness) has all the required cables/plugs. It should be coiled up inside the PC..

The better PSUs (like seasonic) have detachable harnesses so you get tidy layout.

Possible the windows driver just uses throttling/adaptive clocking to limit the GPU current, the linux driver could be doing this as well.

Running more than 1 screen also increases the GPU load.

---

