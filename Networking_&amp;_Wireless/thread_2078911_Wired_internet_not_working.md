---
title: "Wired internet not working"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by HBurd on 2012-10-31
I built a computer for the first time yesterday, and installed Xubuntu. Everything is working fine so far except for the fact that I cannot connect to the internet. When I plug in the ethernet cable, nothing happens. Under Network Connections, there are no connections for me to join. Is there something I need to do to set it up?

---

### Post by 2F4U on 2012-11-01
Is your network card recognized, do you see the card when you enter lspci? There are usually lights on the card. Are they blinking?

---

### Post by HBurd on 2012-11-01
My network card is integrated with my motherboard. Yes, it does seem to be recognized in lspci.

---

### Post by Yumi on 2012-11-02
Have a look in Network Manager and see if "Airplane Mode" on top is enabled. This would disable all connections.

Michael

---

### Post by HBurd on 2012-11-02
What do you mean by network manager? If you mean the network connections page in settings, there is no airplane mode option.

---

### Post by Yumi on 2012-11-02
Yes. Main Menu - System Tools - System Settings - Networking

The top line is Airplane Mode. It was enabled at default in my install.

Michael

---

### Post by Hadaka on 2012-11-02
Hi, please post the output of...

```
rfkill list all 
```

```
lspci -nn | grep -E 'Ethernet|Wireless' 
```

thanks.

---

### Post by HBurd on 2012-11-02
[FONT=Courier New]rfkill list all[FONT=Arial] has no output

[FONT=Courier New]lspci -nn | grep -E 'Ethernet|Wireless' [FONT=Arial]outputs:
[FONT=Courier New]05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)[/FONT]
[/FONT][/FONT][/FONT][/FONT]

---

### Post by HBurd on 2012-11-02
More information:
I ran [FONT=Courier New]sudo lshw -class network[/FONT] which outputed [FONT=Courier New]*-network UNCLAIMED [FONT=Arial]and a bunch of information about my ethernet controller. I saw on another thread that this is associated with a missing driver[/FONT][/FONT].

---

### Post by steeldriver on 2012-11-02
what version of Xubuntu? you may be able to use the alx driver from the compat-wireless backport

> Ubuntu now provides a package for this driver.

To install the driver:

sudo apt-get install linux-backports-modules-cw-3.4-precise-generic 
sudo modprobe alx


see [http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

---

### Post by chili555 on 2012-11-02
> **steeldriver said:**
> what version of Xubuntu? you may be able to use the alx driver from the compat-wireless backport



see [http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)With**out** ethernet??

---

### Post by HBurd on 2012-11-02
> **chili555 said:**
> With**out** ethernet??
Is it possible to do this without it?
**Edit:** I mean work around it, like downloading the driver on a different computer?

---

### Post by chili555 on 2012-11-02
> **HBurd said:**
> Is it possible to do this without it?
**Edit:** I mean work around it, like downloading the driver on a different computer.Certainly. But you can't just open a terminal and ask apt to install a driver it downloads from the internet ... without any internet!

Please see here: [http://ubuntuforums.org/showthread.php?t=2050126&highlight=alx](http://ubuntuforums.org/showthread.php?t=2050126&highlight=alx)

The procedure is outlined at post #4 and the no-internet gotcha starts at post #6 and following.

If you've installed Ubuntu 12.10, I'd try compat-wireless-3.5.4-1-snpc. I compiled it without any warnings or errors myself as a test.

Post back if you get stuck.

---

### Post by HBurd on 2012-11-02
I've downloaded the packages that build essential is dependent on, and the usb key I used to install xubuntu is being formatted now, which could take a while. Just like the guy in the other thread, I will call it quits for the night and finish this in the morning.

---

### Post by chili555 on 2012-11-03
We'll look forward to your report. Don't forget linux-headers-generic.

---

### Post by HBurd on 2012-11-03
Thank you! It worked perfectly! I was worried for a while that I wouldn't find a solution to this, but you were a tremendous help.

---

### Post by chili555 on 2012-11-03
> **HBurd said:**
> Thank you! It worked perfectly! I was worried for a while that I wouldn't find a solution to this, but you were a tremendous help.Awesome! When you compile a package from a tar.gz or similar, it is compiled against your running kernel version only. When Update manager installs a later kernel version, also known as linux-image, you will need to re-compile against the new version:```
cd Desktop/compat-wireless-3.5.1-1-snpc  [COLOR="Red"]<--or wherever you extracted the package[/COLOR]
./scripts/driver-select restore
./scripts/driver-select alx
make clean
make
sudo make install
sudo modprobe alx
```Please retain your file and these instructions for that time.

---

