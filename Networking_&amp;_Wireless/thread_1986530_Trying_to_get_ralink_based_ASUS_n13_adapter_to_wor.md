---
title: "Trying to get ralink based ASUS n13 adapter to work"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by lazerbeem on 2012-05-25
Fresh install of 12.04 32bit, and ASUS n13 usb wireless adapter stated to work with linux.  It's detected and working somewhat because my iwconfig output is 
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.

My network manager is not displaying any networks and when I type in my network manually it just keeps trying to connect and nothing happens.   I've spent the whole day looking at forums trying to see if anything works and nothing I've tried has.   ](*,)

---

### Post by kevdog on 2012-05-25
I have the same wireless adapter as you, however I'm running 11.10 which it worked straight out of the box.

The wireless chipset in this device is a realtek which utilized the rt2800usb driver (You can discover all of this from typing lshw -C network).

Make sure first the rt2800usb kernel module is loaded within the kernel userspace (lsmod | grep rt2800): (Mine looks like this:)
rt2800usb              22222  0
rt2800lib              48909  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48114  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              393459  3 rt2800lib,rt2x00usb,rt2x00lib

Make sure there is no kill switches:
~/src/gnupg$ sudo rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

Please also post ifconfig

Thanks

---

### Post by lazerbeem on 2012-05-25
Ok I'm not sure if postng lshw -C network output is nesseccary but here it is:

lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 00:25:22:da:c4:ae
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.115 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:51 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@8:1
       logical name: wlan0
       serial: 54:04:a6:df:31:30
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-24-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

It says driver=rtl8192cu, is that a different one?

Nothing was coming up until for lsmod | grep rt2800 until I typed sudo modeprobe rt2800, then I got this for lsmod | grep rt2800

rt2800usb              22300  0 
rt2800lib              53264  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20061  1 rt2800usb
rt2x00lib              48858  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436455  6 rt2800lib,rt2x00usb,rt2x00lib,rtl8192cu,rtl8192c_common,rtlwifi

rfkill list shows

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

ifconfig shows

eth0      Link encap:Ethernet  HWaddr 00:25:22:da:c4:ae  
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:feda:c4ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1664317 (1.6 MB)  TX bytes:298952 (298.9 KB)
          Interrupt:51 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30324 (30.3 KB)  TX bytes:30324 (30.3 KB)

wlan0     Link encap:Ethernet  HWaddr 54:04:a6:df:31:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Thanks for the help!

---

### Post by kevdog on 2012-05-25
Ok -- just want to make sure we are talking about the same Asus USB wireless stick here -- USB-N13.

Try this (these are temporary solutions):
sudo ifconfig wlan0 down
sudo modprobe -r rtl8192cu
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb
sudo ifconfig wlan0 up

Check lshw -C network to make sure your device is now specifically associated with the rt2800usb driver rather than rtl8192cu.

You might then need to use network manager or whatever utility to connect to your wireless network.

If everything works above (I'd be shocked if it totally worked), you can permanently "blacklist" the rtl8192cu module from loading at boot-time by doing the following:

echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf

Try the above commands prior to blacklisting anything first.

---

### Post by lazerbeem on 2012-05-25
Correct it is ASUS usb n13 wireless adapter.   Removing rtl8192cu from modprobe makes it so the network manager no longer gives the option of wireless like it did before.  It also takes wlan0 out of my iwconfig output.  I tried adding rt2800usb to modprobe and it didn't make a difference in fact lshw -C network doesn't even show the wireless device after removing rt8192cu and adding the other modules to modprobe.  Is there a configuration type file that can be edited to change which driver is associated with the wireless usb?

---

### Post by kevdog on 2012-05-25
Wow -- that's unfortunate.  What version of ubuntu are you on?

modprobe is simple a command to load the driver into user space.  modprobe -r is a way to remove the driver.

You can always modprobe the old driver to reload the original configuration.  Reload the original driver and then post the results of iwlist scan.  Thanks.

---

### Post by lazerbeem on 2012-05-25
I'm on 12.04.  I took rtl8192cu off the blacklist and put it back in back into modprobe.  Here is what iwlist scan says
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

---

### Post by kevdog on 2012-05-25
Can you post a picture of your device -- something is screwy!  Thanks. Also lsusb

My lsusb appears like the following:
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network
Adapter [Ralink RT2870]

---

### Post by lazerbeem on 2012-05-25
I ordered it from newegg, here is the product page lol
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320040](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320040)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 0b05:17ab ASUSTek Computer, Inc. 

Odd that it doesn't show anything other than the manufacturer.

---

### Post by lazerbeem on 2012-05-25
I finally got it to work.  I tried these commands 
sudo modprobe -r rtl8192cu sudo modprobe rtl8192cu swenc=1 I'm not sure what the significance of swenc=1 is but it did the trick.
Thanks for the help.

---

### Post by kevdog on 2012-05-26
Ok -- you have a different chipset than my device so hence the confusion.  


Have you ever compiled a driver from source?  I think that is what you are going to have to do in your case.  The source of the driver is the following:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=2&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772](http://www.realtek.com/downloads/downloadsView.aspx?Langid=2&PNid=21&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true#2772)

Go down and get the zip package -- specifically for your chipset RTL8192CU

You'll need to make sure to compile the package you have the build-essential and linux header packages:
sudo apt-get install build-essential linux-headers-`uname -r`

This will give you the header files for your kernel source and also the gcc compiler and tool chain.

Once you unzip the RTL package, try just running:
sudo ./install.sh

This might work -- I doubt it.  If not we will just compile the driver manually.

---

