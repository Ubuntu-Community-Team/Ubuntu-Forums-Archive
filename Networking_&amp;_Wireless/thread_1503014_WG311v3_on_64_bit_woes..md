---
title: "WG311v3 on 64 bit woes."
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by shearn89 on 2010-06-06
Hey all,

Long time since i've been on here, but it's the usual wireless troubles that bring me back...

So:
I have just downloaded and installed 10.04, totally fresh, on a partition on my machine. Its 64 bit, and the card I'm using is a Netgear WG311v3. It works great on vista 32-bit, but fails miserably on windows 7 64-bit, as there're no drivers.

I've looked at many many forum posts and googled my *** off.

Procedure I followed:
[LIST]
[*]Download this file: [http://sites.google.com/site/subtlegems/netgear-wg311v3-ndis-driver-for-linux-amd64/wg311v3_ndis_amd64.tar.gz?attredirects=0](http://sites.google.com/site/subtlegems/netgear-wg311v3-ndis-driver-for-linux-amd64/wg311v3_ndis_amd64.tar.gz?attredirects=0)
[*]from this site: [http://sites.google.com/site/subtlegems/netgear-wg311v3-ndis-driver-for-linux-amd64](http://sites.google.com/site/subtlegems/netgear-wg311v3-ndis-driver-for-linux-amd64)
onto usb pen. 
[*]Reboot into ubuntu.
[*]Install ndiswrapper from usb pen (version 1.56).
[*]unzip the tar file.
[*]install driver .inf file using **sudo ndiswrapper -i driver.inf**
[*]confirmed that it shows up under ndiswrapper -l
[*]sudo depmod -a
[*]sudo modprobe ndiswrapper
[*]check dmesg:
```
[   66.060304] ndiswrapper 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 16 (level, low) -> IRQ 16
[   66.060808] ndiswrapper: using IRQ 16
[   66.083838] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   66.083843] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   66.083850] ndiswrapper (mp_halt:262): device ffff8800abb14680 is not initialized - not halting
[   66.083852] ndiswrapper: device eth%d removed
[   66.083863] ndiswrapper 0000:01:06.0: PCI INT A disabled
[   66.083876] ndiswrapper: probe of 0000:01:06.0 failed with error -22
[   66.083939] usbcore: registered new interface driver ndiswrapper
```
[/LIST]
As you can see, i get a "couldn't initialize device" error. This means that the card doesn't show up in ifconfig OR iwconfig.
I've also tried rebooting, then running
```

sudo rmmod ndiswrapper
sudo depmod -a
sudo modprobe ndiswrapper

```
to no avail.

I've also tried building ndiswrapper from source, and before trying the marvell drivers I tried some other netgear XP64bit ones. Didn't work either...


**_Any help or ideas appreciated! _**I know other people have had this problem, so if they have a way around it, please let me know.


Extra info:
```

relevant lspci:
01:06.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
0

shearn89@THOR-DEV:~$ sudo lshw -c net
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:fe9f0000-fe9fffff memory:fe9e0000-fe9effff

```

---

### Post by xatus on 2010-06-16
i'm with the same problem(same result for dmesg and lshw -c net).
Im using thi driver for 64bit xp: [http://skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=](http://skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=)

---

### Post by thundaraptor on 2010-07-05
I have had similar problems with this.  Did either of you get the driver to work once and then it doesn't work anymore?  I have had that happen twice, both times right after I reinstall the entire OS from scratch.  I have also an account for support with canonical and the couldn't solve this for me.  I have done all the same things that are listed above to no avail, this really gets me steemed cause hardline connections are sometimes and issue depending on the location of the router/phone line.

---

### Post by thundaraptor on 2010-07-05
The strangest thing, I have now gotten the driver working, but moments ago it wouldn't.  This is such odd behaviour, I bet if I restart my system it will stop working...

---

### Post by flash63 on 2010-07-06
Hello,
try this driver for 64bit.

[http://forum.ubuntuusers.de/topic/verbindungsprobleme-mit-wlan-marvel-8339-libe/#post-1888522](http://forum.ubuntuusers.de/topic/verbindungsprobleme-mit-wlan-marvel-8339-libe/#post-1888522)

Two inf-Files are included. Test it serparate.

Check:
```
dmesg | grep ndis
```
Look to this message
```
ndiswrapper: probe of 0000:01:06.0 failed with error -22

```
No improvement at all? Ndiswrapper 1.56 with a patch may help.

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://dfn.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.56.tar.gz
tar -xzf ndiswrapper-1.56.tar.gz  

```
Patchfile
```
gedit ndiswrapper-1.56/driver/pelinker.c.patch 
```
Content:
```
--- ndiswrapper-1.56/driver/pe_linker.c	2009-06-29 04:09:26.000000000 +0200
+++ ndiswrapper-1.56/driver/pe_linker.c	2009-09-07 12:19:10.000000000 +0200
@@ -450,6 +450,8 @@
 		      " %d bytes", image_size);
 		return -ENOMEM;
 	}
+// zero out memory
+memset(image, 0, image_size); 
 
 	/* Copy all the headers, ie everything before the first section. */
```
save and patch
```
patch ndiswrapper-1.56/driver/pe_linker.c ndiswrapper-1.56/driver/pelinker.c.patch 
```
build
```
cd ndiswrapper-1.56
make                     
sudo make uninstall      
sudo make install
modinfo ndiswrapper
```

---

### Post by shearn89 on 2010-07-07
> **thundaraptor said:**
> I have had similar problems with this.  Did either of you get the driver to work once and then it doesn't work anymore?  I have had that happen twice, both times right after I reinstall the entire OS from scratch.  I have also an account for support with canonical and the couldn't solve this for me.  I have done all the same things that are listed above to no avail, this really gets me steemed cause hardline connections are sometimes and issue depending on the location of the router/phone line.

I had no luck at all: I gave up and have stuck with a cable out the window to my router. Much faster, and easier to set up...

**@flash63** - I'm gonna keep your post bookmarked, and if I decide to go back to trying the wifi, I'll give it a go!

---

### Post by M0nk3yM4n on 2011-04-10
> **flash63 said:**
> Hello,
try this driver for 64bit.

[http://forum.ubuntuusers.de/topic/verbindungsprobleme-mit-wlan-marvel-8339-libe/#post-1888522](http://forum.ubuntuusers.de/topic/verbindungsprobleme-mit-wlan-marvel-8339-libe/#post-1888522)

Two inf-Files are included. Test it serparate.

Check:
```
dmesg | grep ndis
```
Look to this message
```
ndiswrapper: probe of 0000:01:06.0 failed with error -22

```
No improvement at all? Ndiswrapper 1.56 with a patch may help.

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://dfn.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.56.tar.gz
tar -xzf ndiswrapper-1.56.tar.gz  

```
Patchfile
```
gedit ndiswrapper-1.56/driver/pelinker.c.patch 
```
Content:
```
--- ndiswrapper-1.56/driver/pe_linker.c	2009-06-29 04:09:26.000000000 +0200
+++ ndiswrapper-1.56/driver/pe_linker.c	2009-09-07 12:19:10.000000000 +0200
@@ -450,6 +450,8 @@
 		      " %d bytes", image_size);
 		return -ENOMEM;
 	}
+// zero out memory
+memset(image, 0, image_size); 
 
 	/* Copy all the headers, ie everything before the first section. */
```
save and patch
```
patch ndiswrapper-1.56/driver/pe_linker.c ndiswrapper-1.56/driver/pelinker.c.patch 
```
build
```
cd ndiswrapper-1.56
make                     
sudo make uninstall      
sudo make install
modinfo ndiswrapper
```


Thank you for this! The german Marvell drivers were what I needed!

---

