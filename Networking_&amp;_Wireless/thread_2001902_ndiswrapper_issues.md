---
title: "ndiswrapper issues"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by SlasherIT on 2012-06-11
Hi guys,

I'm trying to use ndiswrapper (got if off synaptic) to install the Broadcom BCM4306 Windows driver. I am running Ubuntu 12.04. After I select the .inf file so it can install, I get this error: 

Module could not be loaded. Error was:

*FATAL: Module ndiswrapper not found.*

Is the ndiswrapper module installed?


Help would be appreciated, thanks.

---

### Post by chili555 on 2012-06-11
The native driver for your Broadcom should work perfectly without ndiswrapper. Please run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by Bucky Ball on 2012-06-11
> **chili555 said:**
> The native driver for your Broadcom should work perfectly without ndiswrapper. Please run and post:```
lspci -nn | grep 0280
```Thanks.


+1. Avoid ndiswrapper, it is superceded for the majority of Broadcom cards now.

Do an update, check 'Additional Drivers' and see if your B43 or STA driver is there. If not, you can try installing:

b43-fwcutter

... and I think the other one you need is:

firmware-b43-installer

Someone else may be able to confirm that.

---

### Post by chili555 on 2012-06-11
> Someone else may be able to confirm that.Indeed. Ideally, by reading the exact pci.id.

---

### Post by UltimateCat on 2012-06-11
The only way I was able to install Ndiswrapper was  to install it along with the " inf" file and than blacklist the Rt8169 as I have the Rt8168.

---

### Post by Bucky Ball on 2012-06-11
> **UltimateCat said:**
> The only way I was able to install Ndiswrapper was  to install it along with the " inf" file and than blacklist the Rt8169 as I have the Rt8168.

You are running a Realtek card (and wondering why you are using ndiswrapper) and the OP is using Broadcom. ndiswrapper is no longer relevant for most Broadcom cards. B43 drivers took care of that. ;)

Please go here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168<br>RTL8111C/RTL8111CP/RTL8111D(L)<br>RTL8168C/RTL8111DP/RTL8111E<br>RTL8168E/RTL8111F](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168<br>RTL8111C/RTL8111CP/RTL8111D(L)<br>RTL8168C/RTL8111DP/RTL8111E<br>RTL8168E/RTL8111F)

The drivers for your device are there. There is a rtl8168E and B. You'll need to find out which one yours is.

```
sudo lshw -C network
```

(PS: It is the rt**l**8168, incidentally. You forgot the 'L'.)

---

### Post by SlasherIT on 2012-06-12
Hi guys,

Are you sure its going to work? Because before, on ubuntu 11.10, I tried the same thing (i think), its on another thread here. [http://ubuntuforums.org/showthread.php?t=1897468](http://ubuntuforums.org/showthread.php?t=1897468)
It never worked, so Wi-Fi hasn't been working since. So I'm not sure if it will work without ndiswrapper or not...

---

### Post by chili555 on 2012-06-12
> **SlasherIT said:**
> Hi guys,

Are you sure its going to work? Because before, on ubuntu 11.10, I tried the same thing (i think), its on another thread here. [http://ubuntuforums.org/showthread.php?t=1897468](http://ubuntuforums.org/showthread.php?t=1897468)
It never worked, so Wi-Fi hasn't been working since. So I'm not sure if it will work without ndiswrapper or not...No, we're not sure. We are constantly amazed at what works that shouldn't and what doesn't work that should. It takes about as much effort to try as it would take to fix the ndiswrapper glitch; which is very little. Why not try? 

Please walk over to the router and get a wired ethernet connection, open a terminal and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```Detach the ethernet. Is it working?

I'm not even confident that ndiswrapper will work perfectly!

----------

Note to Chili; from linked thread: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [[COLOR="Red"]14e4:4320[/COLOR]]

---

### Post by SlasherIT on 2012-06-12
I'm currently on ethernet. So I follow your first reply or this latest one? Soz.

---

### Post by chili555 on 2012-06-12
> **SlasherIT said:**
> I'm currently on ethernet. So I follow your first reply or this latest one? Soz.Please follow number 8.

---

### Post by Bucky Ball on 2012-06-12
Think you need to completely remove ndiswrapper for the b43 stuff to work? It is a dim memory so I could be wrong ...

ndiswrapper has the Win driver installed so has the device. If you try install the b43 there's problems. I had a Broadcom card in my dead laptop and seem to remember something like this.

---

### Post by chili555 on 2012-06-12
> **Bucky Ball said:**
> Think you need to completely remove ndiswrapper for the b43 stuff to work? It is a dim memory so I could be wrong ...Probably not yet, because it's not really loading anything:> Module could not be loaded. Error was:

FATAL: Module ndiswrapper not found.If we get b43 to work, we'll do some housekeeping and remove whatever ndiswrapper stuff is there.

---

