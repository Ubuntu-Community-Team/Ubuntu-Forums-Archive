---
title: "d-link-140 and ubuntu 10.04 wireless problem"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by Jimali on 2010-05-07
Hi,

I'm running Ubuntu 10.04 on my computer and  I have had headache for days  trying to fix my wireless network without success. 
Here's some info and hope  that somebody will help me with this. I'm new to ubuntu. 


iwconfig 
lo        no wireless extensions.  
eth0      no wireless extensions.   

lsmod | grep rt  
rt2870sta             525366  0   
parport                37160  2 ppdev,lp 

lshw -C network    
*-network                        
    description: Ethernet interface         
    product: RTL8111/8168B PCI Express Gigabit Ethernet controller             
    vendor: Realtek Semiconductor Co., Ltd.             
    physical id: 0             
    bus info: pci@0000:02:00.0             
    logical name: eth0         
    version: 03             
    serial: 90:e6:ba:3c:83:31         
    size: 100MB/s         
    capacity: 1GB/s         
    width: 64 bits         
    clock: 33MHz         
    capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation          
    configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.115 latency=0 link=yes multicast=yes port=MII speed=100MB/s              resources: irq:35 ioport:c800(size=256) memory:f6fff000-f6ffffff(prefetchable) memory:f6ff8000-f6ffbfff(prefetchable) memory:fbcf0000-fbcfffff(prefetchable)

Thanks in advance
/Jimali

---

### Post by labinnsw on 2010-05-08
[Here's a little something I stitched up on the subject]("http://www.youtube.com/watch?v=DZLEZRgWIOc")

[See also my response here]("http://ubuntuforums.org/showpost.php?p=9192517&postcount=2")

---

### Post by Jimali on 2010-05-08
> **labinnsw said:**
> [Here's a little something I stitched up on the subject]("http://www.youtube.com/watch?v=DZLEZRgWIOc")

[See also my response here]("http://ubuntuforums.org/showpost.php?p=9192517&postcount=2")

Thank you for info. That was very difficult to understand and see the text. I use ubuntu 10.04 not 8.04. Any way I used the code as follows and get error on that which I don't understand.

dmesg | grep rt2
[   17.709755] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   17.712112] usbcore: registered new interface driver rt2870
[ 1952.998490] phy0 -> rt2800usb_init_eeprom: Error - Invalid RT chipset detected.
[ 1952.998493] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[ 1952.998507] usbcore: registered new interface driver rt2800usb

/jimali

---

### Post by labinnsw on 2010-05-09
Did you also read the second link I provided. It is a summary of what I did in the video. It will help you to understand the video. It works on any Linux OS. I just happened to be using Ubuntu 8.04 at the time when I recorded the video. I am also now using 10.04.

I can't help you with that grep thing. I don't understand it. If you decide to go that route, I can only wish you luck. If you want to get the modem working though, the video explains the simplest method I know to do so. 

Sorry, I don't know how to make the video any clearer. If you download it, you can watch it in full screen mode and HD.

This will actually work for any wireless device on any Linux system, with some minor adaptations. e.g. The driver might not be on a CD or the system might not use synaptic.

---

