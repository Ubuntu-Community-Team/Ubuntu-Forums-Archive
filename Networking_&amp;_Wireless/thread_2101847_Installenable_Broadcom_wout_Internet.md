---
title: "Install/enable Broadcom w/out Internet"
date: 2013-01-05
forum: Networking &amp; Wireless
---

### Post by putz3000 on 2013-01-05
I have not yet found an answer that seems to work. I could be wrong, but I assume my problem is no Internet connection otherwise I assume I could actually get around this.

Here is a brief background:

I installed Ubuntu 12.10 64-Bit on my Dell XPS M1550 and had things working properly. I was given a Dell Vostro 1500 and decided I wanted to install the hard drive from the XPS with the installed Ubuntu into the Vostro unit. I really didn't/don't want to reinstall if I can help it due to some of the data/configuration that I really don't want to have to redo.

After install the system boots up just fine and for the most part everything seems to work fine...except the wireless driver. I had ordered my XPS specifically with an Intel wireless driver but the previous owner of the Vostro went with the Broadcom. Worse yet, the ethernet adapter/port does not work so I currently have no Internet access at all.

If I launch "software sources" & "Additional Drivers", it identifies an option for Broadcom 802.11 Linux STA Wireless driver Source for the BCM4311. But directly under the option it says "This device is not working". I had assumed that was because I simply needed to install the proprietary drivers (still mostly think that). However after I try to enable it, I get a progress bar for installing it that stops part way through and then the "Do not use the device" option is reselected.

So, is there a way I can get this driver installed without having internet access? I feel my technical knowledge/comprehension is above "noob", but below proficient - so I like detailed steps when possible. I have the install media but have been unable to figure out how to get the system to extract the driver from it (assuming internet only install?). The only thing I have not yet tried was purchasing a USB style connecter & attempting hook into ISP modem/router via USB based connection. I would rather not deal with it if there is an easier method using a few commands and/or file I can download form another machine.

Thank you for any help you may be able to offer.

---

### Post by Hadaka on 2013-01-05
Hi, if you have a usb stick you can use the machine you are posting on
to load the included zip file to the usb then plug into your ubuntu machine.
by default it will probably download to /Downloads so be sure to drag it
to the desktop before loading it. This link contains a how to with no internet
for the B43 driver,

[http://ubuntuforums.org/showthread.php?t=1920981&highlight=b43](http://ubuntuforums.org/showthread.php?t=1920981&highlight=b43)

---

### Post by putz3000 on 2013-01-05
In my case, I got lucky in that I stumbled upon a Linksys USB200M laying around which Ubuntu 12.10 auto detected & started using. I used that to get the proprietary driver installed. However, wireless was still not operational. It was like the adapter was just not working or not powered.

After doing some more poking around I stumbled onto a post on the Ask Ubuntu website which resolved the real issue (outside of no initial network access). Apparently the STA driver that Ubuntu 12.10 wants to use is the incorrect driver. Based on this <a href="http://askubuntu.com/questions/228821/bcm4311-wireless-not-working-with-drivers-installed">Ask Ubuntu post</a>, the following 3 commands fixed my problem:

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

As a side note, my laptop's wireless light next to the on/off switch does not work. Thats fine as the adapter itself is working. I only point this out in case future frustrated users are using the LED light as an indicator of the adapter working.

---

### Post by Hadaka on 2013-01-05
Great! glad you got it working.
please use thread tools and mark this SOLVED

---

