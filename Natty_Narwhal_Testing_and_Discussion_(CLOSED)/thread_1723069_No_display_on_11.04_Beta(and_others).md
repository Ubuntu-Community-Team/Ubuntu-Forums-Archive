---
title: "No display on 11.04 Beta(and others)"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Stompicus on 2011-04-06
I upgraded to 11.04 today, and when I rebooted, I had no display. When I boot into the previous kernels, it works perfectly. If I select the newer kernel images, however, it doesn't work. Anything past 2.6.35-28 that I've tried has the same problem, on any distro.

I am using an NV78 laptop with integrated Intel graphics.

Please help me fix this, I'll try to tell you anything you need.

---

### Post by uRock on 2011-04-06
Moved to Natty Narwhal Testing & Discussion.

If you didn't upgrade with the purpose of testing for bugs, then you may want to reinstall Lucid or Maverick.

---

### Post by Stompicus on 2011-04-06
Yeah, I installed to do some testing, but I can't do much of it at the moment. I guess I'll reinstall 10.10.

I'll keep the 11.04 install and try to find a solution however. If anyone has any ideas, please post them.

---

### Post by cariboo on 2011-04-06
Can you paste the output of:

```
lspci | grep VGA
```

in your next post?

---

### Post by Stompicus on 2011-04-24
> **cariboo907 said:**
> Can you paste the output of:

```
lspci | grep VGA
```in your next post?


I get:


```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```
Keep in mind I am booting from the old kernel.

---

### Post by dino99 on 2011-04-24
so xserver-xorg-video-intel might be installed
and dkms too

sudo rm /etc/X11/xorg.conf

---

### Post by Stompicus on 2011-04-24
> **dino99 said:**
> so xserver-xorg-video-intel might be installed
and dkms too

sudo rm /etc/X11/xorg.conf

It told me there was no such file or directory.

---

### Post by Stompicus on 2011-04-24
If I suspend, hibernate, or just close the lid and open it, the video turns on. The only problem is that the backlight is off. If i use a flashlight however, I can see color. I've had problems turning my backlight down before, but I don't have any ideas on how to fix this.

I'll try to run a program called gamma panel under WINE to change the brightness and report back to see if it worked.

UPDATE:

Good news and bad news.

Gamma Panel didn't work.

When I boot I can use the fn keys to adjust the brightness before the post. If I do this, then the display shows when I boot.

However, I have to reboot to adjust the brightness, and if I don't adjust the brightness when booting, it defaults to the backlight being off when I choose newer kernels.

I think I will install windows and update my bios to see if that fixes things. I will also try using LILO.

UPDATE 2: neither of those things worked

If anyone has any ideas, please post them

---

### Post by Harry33 on 2011-04-25
This is not a graphics driver problem at all.
There are several laptop backlight bug reports in Launchpad ATM.
I suspect acpi and power management issues with newer kernels.
Here for example:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438)
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/756938](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/756938)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/749899](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/749899)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709994](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709994)

---

