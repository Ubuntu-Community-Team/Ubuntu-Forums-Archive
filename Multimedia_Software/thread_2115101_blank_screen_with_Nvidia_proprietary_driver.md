---
title: "blank screen with Nvidia proprietary driver"
date: 2013-02-11
forum: Multimedia Software
---

### Post by ieee488 on 2013-02-11
There is only Ubuntu on this laptop.

I don't even get the Grub screen to try any fixes.

It just boots straight into Ubuntu, and then I hear the drumroll.

How do I fix this problem?

---

### Post by BicyclerBoy on 2013-02-12
I assume that laptop you refer is m6300..with either quadro fx1600m or fx3600m.
Either of them is still supported by 310 but only just..

The grub screen & further text console is hidden by default, you can try to get grub by <shift> key..
The plymouth process hides the OS messages up to greeter login..any key should cause text to be revealed..

Did you install the nVidia driver 304 or 310 from/via the  jockey additional drivers tool?

One way to find the problem is to console screen 1 login:
<ctrl>+<alt>+<F1>   then login..

Try to start X server:
$ sudo service lightdm start
switch back to console screen 1 & then:
$dmesg > dump.txt
$cat /var/log/Xorg.0.log

Make a backup copy of the log somewhere & post the log & dump.txt here..

---

### Post by ieee488 on 2013-02-12
Thanks for the reply.

The install is on an ancient Dell Latitude C840.

Since I had just installed the OS with nothing to lose, I decided to re-install Ubuntu again. The next time it suggests installing the proprietary driver, I will not be doing so.

By the way, how can I tell which version of video driver Ubuntu is running?

---

### Post by Yellow Pasque on 2013-02-12
If my quick Googling is correct, you have a GeForce4 440 Go, which is relatively ancient and only supported by legacy 96.x nvidia proprietary drivers.

Your options
1) just use the default open-source nouveau driver
2) use Ubuntu 12.04.x and this proprietary driver: [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.23-0ubuntu0.1](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.23-0ubuntu0.1)

It may also be possible to use the above proprietary driver on Ubuntu 12.10 if you use the makson PPA ( [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx) ) to downgrade your Xserver. I'm not sure if that nvidia-96 driver supports kernel 3.5, though. It's best not to attempt this unless you're feeling adventurous.

---

### Post by ieee488 on 2013-02-13
Thank you.

Yes, this is an old laptop, so I am going to keep the default video driver.  :)

---

