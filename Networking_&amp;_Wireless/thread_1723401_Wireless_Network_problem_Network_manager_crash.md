---
title: "Wireless Network problem/ Network manager crash"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by trendyabinash on 2011-04-07
Sir I have Digisol's PCI Wireless card
Model No. DG-WN1150N

Here is the site: [http://www.digisol.com/product_subdetails.aspx?Dgid=D_solwireless&typeid=D_PRO_2&id=8]("http://www.digisol.com/product_subdetails.aspx?Dgid=D_solwireless&typeid=D_PRO_2&id=8")

When i am booting Ubuntu, the network manager detects the wireless card, so I assume that it has the requisite drivers for my card. But when I am trying to connect to my router, it scans for a while i guess and then the network manager closes.. I am unable to do start it again, plus with it seems the Ubuntu crashes too, so I have to reboot my Ubuntu and same thing happens.

Any solution to this ?
Is there a way i uninstall the Ubuntu provided drivers and then trying using the ndisgtk ( the window driver suppoter) to run my wireless card. Or is there an easier solution ?

Without Internet, I am kind of lost and not able to do anything.
Using my windows system to post this.

---

### Post by trendyabinash on 2011-04-07
here is a list of commands i tried and their outputs

```
sudo lspci :
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
05:01.0 Network controller: RaLink Device 3060
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
____________________________________________________________________________________

sudo lspci | grep wireless

no result
_______________________________________________________________________________
sudo lshw -c network
PCI (sysfs)  
  *-network:0             
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wlan0
       version: 00
       serial: 00:17:7c:0a:a0:50
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic firmware=N/A latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:22 memory:90000000-9000ffff
  *-network:1
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 01
       serial: 00:16:76:c6:64:ae
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:90010000-90010fff ioport:1000(size=64)
______________________________________________________________________________
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off


```

---

### Post by trendyabinash on 2011-04-07
Any thing can be done to my problem please?
I installed ndisgtk package over the default Ubuntu package still same problem.

---

### Post by trendyabinash on 2011-04-08
I googled a bit and found around few things relating to this problem.

My wireless card needs rt2860 driver. Where as Ubuntu installing rt2800 driver.

So what i did was I downlaoded the driver file from the manufacturer's website. It was in .tar.bz2

I extracted it then there was a Makefile
so I used 

sudo make
sudo make install

the output i didn't recorded so i tried it again and here is the output
```
sudo make install
[sudo] password for 
make -C /home/abinash/rt2860/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/abinash/rt2860/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/abinash/rt2860/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.38-7-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2860sta.ko /lib/modules/2.6.38-7-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-7-generic
make[1]: Leaving directory `/home/abinash/rt2860/os/linux'


```

Then as per a site I did this :

Edit /etc/modules in Ubuntu and added this line:


```
rt3652sta.ko
```

And /etc/modprobe.d/blacklist.conf and added


```
blacklist rt2800pci
```

Now this should fix my problem but Now in the network manager there is no wireless network at all, earlier it showed "Wireless Enable - ticked" Now that part is missing.

any help here will be really appreciated


Reference :[http://www.linuxquestions.org/questions/linux-hardware-18/digisol-dg-wn1150n-ralink-3060-chip-pci-wireless-card-on-ubuntu-865140/](http://www.linuxquestions.org/questions/linux-hardware-18/digisol-dg-wn1150n-ralink-3060-chip-pci-wireless-card-on-ubuntu-865140/)
this is the site where a guy was able to solve this issue.

Sorry i am kind a newbie to installing drivers manually.


Also I installed Ubuntu from pendrive, so i am unable to install any package from the software center. I really need the internet connection sir, please please help me here

---

### Post by trendyabinash on 2011-04-08
I made my wireless network

thanks to this thread : [http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716)

Marking this one as solved

---

