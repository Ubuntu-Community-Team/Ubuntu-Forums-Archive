---
title: "Realtek RTL8188CUS Wireless Adapter"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by Warmijwilf on 2012-04-22
Hey, all.
I've been an Ubuntu user since about 2008, and I've had problems with Ubuntu before that are usually fixed with a google search. However, I have just purchased a new computer where almost everything works fine except one crucial thing - the USB Wifi adapter.

In 32-bit Ubuntu (any version), downloading and installing the wireless driver for the RTL8188CUS USB wifi adapter from Realtek's website (Which I believe is the same driver as the RTL8192CU and is what the module name is) and going into /etc/modprobe.d/blacklist.conf and blacklisting "rtl8192cu" makes it work fine... However, with 64-bit doing this either makes the computer kernel panic at every boot or has absolutely no effect. The default driver included in the kernel just lets me find the network but not actually connect.

Can someone please help? Thanks.

---

### Post by kurt18947 on 2012-04-22
I'm not sure because I'm running an Edimax EW-7811Un on Ubuntu 64 bit no issues.  I just used the install script included with the driver and no problem, didn't even have to blacklist anything in 12.04.  I did have to blacklist in Mint12.  The default driver doesn't work for me either.  The device is recognized but I get recurring "enter your passphrase" or whatever the message is.

---

### Post by Warmijwilf on 2012-04-22
Unfortunately, even 32-bit 12.04 requires a bit of fiddling (blacklisting RTL8192CU) to get the driver working... 64-bit is just having none of it still, every attempt to try and make the driver work (I've even removed the spaces between quotes in certain parts of the install.sh as suggested by a few other sites, nothing different) ends with either the wireless just not connecting or a kernel panic.

Anyone else able to help?!

---

### Post by Warmijwilf on 2012-04-23
Anyone able to help...?

---

### Post by kurt18947 on 2012-04-23
I'm not sure if this matters but it's the only thing that comes to mind.  When I run the shell script included in RealTek's driver I use this command:

```
sudo bash install.sh
```

This works perfectly for me on a Thinkpad running 12.04 64 bit.  I hope you're able to solve your problem, wish I had a better suggestion.

---

### Post by Warmijwilf on 2012-04-24
Nope, that's the command I use...

Oh well. Guess I'll have to stick with 32-bit.

---

### Post by bford16 on 2012-07-17
I just purchased an EDIMAX "EW-7811Un" USB wireless adapter, which uses the RTL8188CUS chipset.  I was having no fun at all until I found the directions at this link.  The directions were exactly what I needed. The link says it is for Ubuntu 11.10, but it worked for my 64-bit Precise Pangolin machine (Ubuntu 12.04).

[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/]("http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/")

---

### Post by finmann on 2012-09-05
Yea, I too used the method at 
[http://www.r-statistics.com/2011/11/...-ubuntu-11-10/]("http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/") on a 64-bit build.
It works, however if I take the dongle out of the USB port I most-times suffer a kernel panic! Now I don't go taking it out all the time but 4 some reason if it's in my USB hub(I have a laptop with 3 USB ports so I need it) and my fridge makes some noise it causes a KP too! I hope this is resolved in a future driver.

Also the drivers for the 8188CUS on the realtek website are outdated, use the ones on 8192CU page.

---

### Post by kurt18947 on 2012-09-05
Has anyone tried just plugging the Edimax  into an updated 12.04 install?  Mine has taken to just working and I can't find any evidence of having installed RealTek's drivers.  Signal strength and speed seem as expected.  The light in on steady rather than blinking but I guess I can't have everything:-).   It appears to be plug 'n' play in12.10 as well but the last time I tried it would lock up after about 90-120 minutes.  Unplug/replug and it'd work again.

---

### Post by odinb on 2012-12-17
> **kurt18947 said:**
> Has anyone tried just plugging the Edimax  into an updated 12.04 install?  Mine has taken to just working and I can't find any evidence of having installed RealTek's drivers.  Signal strength and speed seem as expected.  The light in on steady rather than blinking but I guess I can't have everything:-).   It appears to be plug 'n' play in12.10 as well but the last time I tried it would lock up after about 90-120 minutes.  Unplug/replug and it'd work again.

Is your access point by any chance G-only?

Running this adapter "EDIMAX EW-7811Un" identified as "ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]" using lsusb.

The driver in use is "rtl8192cu" per the connection information.

It seems to work flawless using a G-only access point, but if you try a G/N access point, it keeps asking for the key, and never connects.

Have not found a solution to getting N to work, without having to manually install new drivers, and I do not want to go there, so G-only for me it is.

---

### Post by ahallubuntu on 2012-12-17
Have you tried building the latest driver from Realtek?

[http://ubuntuforums.org/showthread.php?p=12318056#poststop](http://ubuntuforums.org/showthread.php?p=12318056#poststop)

---

