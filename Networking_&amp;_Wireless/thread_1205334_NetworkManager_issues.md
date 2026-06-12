---
title: "NetworkManager issues?"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by Q-Lok on 2009-07-05
Okay, so I just finished getting my MacBook (late 2008 white) dual-booted with Jaunty Jackalope, and everything seems to be working properly -- except the trackpad (which is having issues that I can live with for now) and NetworkManager, which is refusing to allow any sort of wireless connection.  Given this, it should be obvious I'm speaking to you from the OSX partition.

Telling you guys the symptoms first would be good, I guess.  NetworkManager's wired connections are showing up grayed-out, and it won't display anything at all regarding wireless connections (the menu entries are absent entirely).  I can configure the wireless connection that it should be working with, but it doesn't actually connect, or even give any indication that it's trying.

Any thoughts?

---

### Post by computer13137 on 2009-07-05
Yeah, it sounds like Ubuntu isn't recognising your wireless hardware.

Could you please paste the output of the following commands to us, so we can get specific information about your hardware, and whether it's being installed in Ubuntu?

```
lspci
```
```
iwconfig
```

Cheers,
Kirk

---

### Post by Q-Lok on 2009-07-06
Okay, here you go.  Being the newb that I am with this, I can't make heads nor tails of most of this, but hopefully you can.  Thanks in advance for anything you can do.  ^_^

```
cog@sark:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
cog@sark:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

---

### Post by Q-Lok on 2009-07-09
Apologies if topic-bumping is in poor taste, but I do need an answer reasonably soon.  Does anyone have anything to add that might help, or am I entirely stuck?

---

### Post by Crafty Kisses on 2009-07-09
Ok, so first thing is first. I'm not really getting the question, it sounds like your wireless isn't working. Please correct me if I'm wrong. You also said your Ethernet isn't working as well? Try plugging your Ethernet in and connecting, tell me what happens. If there's anyway you can on the net with your Linux partition you can get this fixed. Again I'm not sure what the problem is but if this is the case (your wireless not working) we can try and get it fixed. Now first lets fetch the driver for your card:
```
wget http://myspamb8.googlepages.com/R151517-pruned.zip
```
Once you have fetched the driver, extract it:
```
unzip R151517-pruned.zip
```
Alright, once the file is extracted you should see a file called "bcmw15.inf". That's the file you need for this process. Anyway you need to install "ndiswrapper" there's a couple of ways you can install ndiswrapper, the first way is probably a little easier then the second way, but I'll provide both. Here's the first way, just run:
```
sudo apt-get install ndiswrapper-common
```
The second way to install ndiswrapper is to compile it from source. So first fetch the soruce for ndiswrapper, run the following:
```
wget http://dfn.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.54.tar.gz
```
Now you might have to patch ndiswrapper, depending on what version you get. The version I provided I do believe you have to patch it. So fetch the patch:
```
wget http://qwe.pl/~kacper/bcmmon.tar.bz2
```
Once you have grabbed the patch, you need to apply the patch to ndiswrapper, to apply this patch is pretty simple, just run:
```
patch -p2 < ./bcmmon.diff
```
Then you can compile ndiswrapper. To compile ndiswrapper you can simply run as root:
```
make 
make install
```
If you get any errors while installing ndiswrapper, you may need the "build essential" package, which can easily be grabbed by running as root:
```
apt-get install build-essential
```
Then try the initial compile again and see if you get different results. Once you have ndiswrapper installed, navigate to the folder where the "bcmw15.inf" file is located and run as root:
```
ndiswrapper -i bcmwl5.inf
```
Once you have done that, make sure it has installed right, you can make sure by running:
```
ndiswrapper -l
```
If the driver installed correctly, you should see something like:
```
bcmwl5 driver present, hardware present
```
Then as root you need to run:
```
depmod -a
modprobe ndiswrapper
```
Once you have done those two commands, you need to run one more as root:
```
ndiswrapper -m
```
Once you have ran those commands, you can restart your network interface by running as root:
```
ifdown wlan0
ifup wlan0
```
Then once you have done that, your wireless should technically be working, if you have any issues let me know.

---

