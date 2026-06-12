---
title: "Wifi doesn't work, Ubuntu 12.10 - RTL8188CUS"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by svargasl on 2013-01-11
I'm new here, and i have been having troubles with the wifi since I started configurating the OS, I have read lots of posts and none of them have worked for me..plz help me ):P

---

### Post by squakie on 2013-01-12
Found this thread on the net.  It says 11.10, but it was linked to from another thread saying it worked in 12.04 (and should therefore work with 12.10):

[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/](http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/)

---

### Post by mikewhatever on 2013-01-12
This is a known problem across all Linux distros. [Bug report]("https://bugs.launchpad.net/linux/+bug/852190").

You'll need to blacklist the original module, and then install the driver downloaded from [Realtek.com]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742").

1. Blacklisting.

Run **gksu gedit /etc/modprobe.d/blacklist.conf**, and add the following to the bottom:
```
blacklist rtl8192cu
```
Reboot, and make sure that no rtl81** modules are loaded with **lsmod | grep 81**

2. Installing.

Place the downloaded file in your home folder, and run 

```

unzip RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip #extracting

sudo bash ./RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/install.sh

```

3. If you have any questions, do not hesitate to ask.

---

### Post by squakie on 2013-01-12
> **mikewhatever said:**
> This is a known problem across all Linux distros. [Bug report]("https://bugs.launchpad.net/linux/+bug/852190").

You'll need to blacklist the original module, and then install the driver downloaded from [Realtek.com]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742").

1. Blacklisting.

Run **gksu gedit /etc/modprobe.d/blacklist.conf**, and add the following to the bottom:
```
blacklist rtl8192cu
```Reboot, and make sure that no rtl81** modules are loaded with **lsmod | grep 81**

2. Installing.

Place the downloaded file in your home folder, and run 

```

unzip RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip #extracting

sudo bash ./RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/install.sh

```3. If you have any questions, do not hesitate to ask.

That's what the thread I posted shows how to do as well.

---

