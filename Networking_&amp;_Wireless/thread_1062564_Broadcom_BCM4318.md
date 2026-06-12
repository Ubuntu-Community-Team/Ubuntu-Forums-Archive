---
title: "Broadcom BCM4318"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by interceptorV8 on 2009-02-07
Broadcom BCM4318 (rev 02)  

my belkin usb wireless receiver decided to stop working so i went to best buy and bought the dynex wireless G destop card (dx-bgdtc).
i dual boot with vista and linux (hardy).  in vista, the card works like a charm.  linux won't detect it therefore i have no internet w/ linux.  the threads i've been reading regarding this situation requires downloading via the terminal or the synaptic package manager...  which means i need internet - which i don't have.  can someone guide me through this or give me a helpful link?

---

### Post by superprash2003 on 2009-02-07
post output of **lshw -C network** from the terminal .. do you see any restricted drivers under sytem->admin->hardware drivers ??

---

### Post by interceptorV8 on 2009-02-07
sorry for the delayed response...  lost internet for the night, but i got it up and running again, but now i'm back to the linux problem again.  i posted in the terminal what you told me and i got:

WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:03:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:22:75:19:65:4d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g



oh...and i checked the restricted drivers... because the card won't detect the internet, it won't install the restricted driver for broadcom b43 wireless driver.  i get the error message:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb)
  Could not resolve 'archive.ubuntu.com'

---

### Post by Ayuthia on 2009-02-07
You first try to see if there is a System->Administration->Hardware Drivers/Restricted Drivers.  If there is, check and see if there is a Broadcom b43 wireless option.  You will need a working connection in Ubuntu to make it work though.  It needs to download some firmware to activate the wireless module.

If it is not there, please try installing b43-fwcutter from Synaptic or:
```
sudo apt-get install b43-fwcutter
```

---

### Post by interceptorV8 on 2009-02-07
all i get is:
______________________________________


Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following packages were automatically installed and are no longer required:

  libstrigiqtdbusclient0 libclucene0ldbl libglitz-glx1 libsensors4 librdf0

  kdebase-runtime-data-common libempathy-common libpulse-mainloop-glib0

  librasqal0 libttf2 libsoprano4 kdelibs5-data libzvbi-common libglitz1

  libqt4-sql ftplib3 libstreamanalyzer0 libphonon4 pulseaudio-module-zeroconf

  libstreams0 libempathy-gtk-common libgconfmm-2.6-1c2 perlmagick

  kdepimlibs-data libglademm-2.4-1c2a

Use 'apt-get autoremove' to remove them.

The following NEW packages will be installed:

  b43-fwcutter

0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.

Need to get 15.8kB of archives.

After this operation, 102kB of additional disk space will be used.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main b43-fwcutter 1:011-1

  Could not resolve 'archive.ubuntu.com'

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb)  Could not resolve 'archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by interceptorV8 on 2009-02-07
i switched to vista and downloaded the deb package "b43-fwcutter_011-1_i386.deb" and switched back to ubuntu to install it.  when i try to install it, it fails citing that it's already installed.

---

### Post by Ayuthia on 2009-02-07
Try running this from the Terminal:
```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

It is the script that b43-fwcutter will call to download the firmware.

---

### Post by interceptorV8 on 2009-02-07
Okay... when i put that into the terminal, i get:

.sh

--14:28:51--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

           => `wl_apsta-3.130.20.0.o'

Resolving downloads.openwrt.org... failed: Name or service not known.

---

### Post by Ayuthia on 2009-02-07
Sorry, I was thinking of a different post and just saw that you don't have  a working connnection.  Try the following:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)
It will tell you what to download.

---

### Post by interceptorV8 on 2009-02-07
thanks... here goes nothin' i guess

---

### Post by interceptorV8 on 2009-02-07
i manned-up and just took my desktop downstairs where it could be wired to the internet...   just enabled the driver and now it's working...   thanks to everyone who helped or tried helping :)

---

