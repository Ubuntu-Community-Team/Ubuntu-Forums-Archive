---
title: "TP-LINK WN821N Driver issue"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by nik_gr on 2009-05-06
Hello,

My TP-LINK WN821N new wirless adapter drives me insane!
ubuntu 9.04 cant identify it.

i have the driver cd meant for win version only and ia hve got the .inf and sys fiel to use along with ndiswrapper so to port the drivers to linux.

When i open the app and select the inf file and hit install ti saysQ
Cannot determine if the device is present!

But the wifi card is present and connected to the usb port as lsusb also says:
nik@dell:~$ lsusb
Bus 001 Device 005: ID 0cf3:9170 Atheros Communications, Inc. 

Also the module is isntalled arusb_lh as 

nik@dell:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
arusb_lh : driver installed
    device (0CF3:9170) present

says as well.

So why on earth ubuntu cant use my card and the netowrk icon when i click i right click it doesnt say anything about wireless scan?

i also tried

nik@dell:~$ sudo ndiswrapper -a 0CF3:9170 arusb_lh
Driver 'arusb_lh' is already used for '0CF3:9170'

device and driver are both present and used but no good:

nik@dell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:e9:88:75  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fee9:8875/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3434215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3274812 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3193762212 (3.1 GB)  TX bytes:1095927515 (1.0 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:327993 errors:0 dropped:0 overruns:0 frame:0
          TX packets:327993 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47805051 (47.8 MB)  TX bytes:47805051 (47.8 MB)

nik@dell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by nik_gr on 2009-05-07
please someone help me out!

---

### Post by excogitation on 2009-05-07
> **nik_gr said:**
> please someone help me out!

[instructions]("http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/") by flash63
It's in German (if you can't manage let me know and I'll translate the instructions).

Also there's [another thread here]("http://ubuntuforums.org/showthread.php?t=1052619&page=2").

---

### Post by nik_gr on 2009-05-07
Sorry ic an only understand greek and english.
Can you tell me in a few words why the wifi card uisnt being detected?

---

### Post by excogitation on 2009-05-07
The supplied driver doesn't work with ndiswrapper.
The only driver I could get "working" (it doesn't work stable) with ndiswrapper is [this one]("http://www.iogear.com/support/driver/GWU623.zip").

I would forget about ndiswrapper
```
sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
```
and try the driver package built by flash63


**Instructions [taken from here]("http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262") and loosely translated**:
Get rid off windows drivers and unload the ndiswrapper module:
```
sudo rm -r /etc/ndiswrapper/*
sudo modprobe -rf ndiswrapper
```

Get the kernel header and build-essential packages
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
```

Dowlnoad the driver
```

wget http://elektronenblitz63.de/download/Compat-Wireless_ar9170_230209.tar.gz
```

md5sum is 8dc6af49103f04fb7589408045ce311a

```
md5sum Compat-Wireless_ar9170_230209.tar.gz
```

unpack the driver
```
tar xvf Compat-Wireless_ar9170_230209.tar.gz
```
change to its dir, compile and install
```
cd compat-wireless-2009-02-22_AR9170_230209
make
sudo make uninstall
sudo make install
```

copy the firmware files (ar9170-1.fw/ar9170-2.fw) to /lib/firmware:

```
sudo cp ar9170-*.fw /lib/firmware
```

reboot

load the ar9170 module
```
sudo modprobe ar9170
```

Network manager should now connect to your wireless network using the TL-WN821N USB stick.

To automatically load the ar9170 module on start you can put it in
/etc/modules.

working with these devices (USB-ID's):

0cf3:9170
0cf3:1001
0cf3:1002
07d1:3c10
0846:9010
0846:9001
0ace:1221
0cde:0023
0cde:0026
083a:f522
2019:5304
04bb:093f
0586:3417

---

### Post by nik_gr on 2009-05-07
thank you very muchfor he detailed info but in htis step

sudo make install at some point ima getting this:

```

[ERROR]    Module is still being detected:
net/ath_pci.ko
Disabling ath_pci (13) ...mv: cannot stat `net/ath_pci.ko': No such file or directory
[ERROR]    Module is still being detected:
net/ath_pci.ko
Disabling ath_pci (14) ...mv: cannot stat `net/ath_pci.ko': No such file or directory
[ERROR]    Module is still being detected:
net/ath_pci.ko
Disabling ath_pci (15) ...mv: cannot stat `net/ath_pci.ko': No such file or directory

and so on.....
^Cmake: *** [install] Interrupt


```

what might causing this? what the error message mean?

---

### Post by excogitation on 2009-05-07
> **nik_gr said:**
> 
what might causing this? what the error message mean?

Sorry, I don't know.

---

### Post by flash63 on 2009-05-08
Hello,
Compat Wireless checks your system for aktivated madwifi (ath_pci/ath_hal) an try to deactivate it.

Take a look at the restricted-manager (jockey) an deaktivate the madwifi driver manually.

Any Modules loaded?
```

lsmod | grep ath

```

---

### Post by nik_gr on 2009-05-08
> **flash63 said:**
> Hello,
Compat Wireless checks your system for aktivated madwifi (ath_pci/ath_hal) an try to deactivate it.

Take a look at the restricted-manager (jockey) an deaktivate the madwifi driver manually.

Any Modules loaded?
```

lsmod | grep ath

```

lsmod | grep ath return empty which means there sint an ath module loades still i tried to do suod make install and iam getting hundrends of the above messages

Disabling ath_pci (23) ...mv: cannot stat `net/ath_pci.ko': No such file or directory
[ERROR]    Module is still being detected:

How can i unload the madwifi frivers if any?

---

### Post by flash63 on 2009-05-08
I need more information:

ubuntu-Version?
```
uname -a
```
Try to find any ath-modules:
```
locate ath_pci
```

The driver is included in the restricted-modules

> Take a look at the restricted-manager (jockey) an deaktivate the madwifi driver manually.
Normally you can find it in the gnome Main-Menü > System > Hardware Driver

If there are no drivers activeted, you can ignore the messages, stop the rolling with **Strg+c** an try to load the new driver
```
sudo modprobe ar9170
iwconfig

```This effect appears sometimes with ubuntu 9.04, because the package was made for ubuntu 8.10.

---

