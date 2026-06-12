---
title: "Wireless not connecting after 3.2.0.38 kernel upgrade"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by chemistrydiva on 2013-02-23
Hello all - this is the first time I've had to post here as usually I can fix things that have gone wrong by searching previous posts. This time I'm stumped.

I upgraded the other day to the 3.2.0.38 kernel, and my wireless (controlled by Network manager) promptly stopped working. It saw the wireless network available, prompted multiple times for the password, but failed to connect. 

I rebooted using the old kernel but that didn't make a difference.

The next day I booted in 3.2.0.38, and although network manager was pretty much unresponsive and didn't show me any wireless networks or many menu options, the wireless did work for about 8 hours, then suddenly dropped and no wireless network appeared in the menu (although the entire menu now showed). This is the case now on another reboot. 

Something similar had happened with the upgrade to the 3.2.0.37 kernel but by following the instructions [here]("http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/") I was able to get it to work. 

I've tried all sorts of work-arounds but I haven't been able to get it working again. Now it just seems to have turned itself off. 

I'm using an Edimax EW-7811Un USB adapter. 

Output of lsusb:
Bus 001 Device 005: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]

That's the driver that worked previously (RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622), and the old one (rtl9192cu) I have blacklisted. 

Output of iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

lshw -C network doesn't show the wireless at all

---

### Post by sanderj on 2013-02-23
Which Ubuntu do you use?

How did you do the kernel upgrade?

---

### Post by chemistrydiva on 2013-02-23
Oops, sorry I forgot the Linux distro!

12.04LTS 32 bit and I updated using Update Manager.

---

### Post by sanderj on 2013-02-23
> **chemistrydiva said:**
> Oops, sorry I forgot the Linux distro!

12.04LTS 32 bit and I updated using Update Manager.

OK, I was just checking you did not 'upgrade' to a Linus' stock kernel.

You could have a look at dmesg after you plug in the USB stick.

---

### Post by chili555 on 2013-02-23
> RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622Did you recompile the driver for the newer kernel? Something like:```
cd Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622
sudo su
make clean
make
make install
modprobe 8192cu [COLOR="Red"]<--or whatever it builds[/COLOR]
exit
```

---

### Post by chemistrydiva on 2013-02-23
Fantastic - thanks. I thought I was going to need a new driver but just running:

sudo bash install.sh

in the driver directory and the driver reinstalled itself and the wireless started working perfectly. Many thanks for the prompt!

---

### Post by chili555 on 2013-02-23
Awesome! Glad it's working.

---

