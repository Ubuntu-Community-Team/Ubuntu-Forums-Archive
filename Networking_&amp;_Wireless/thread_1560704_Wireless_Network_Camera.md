---
title: "Wireless Network Camera"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by zeee on 2010-08-25
Hi,

I'm new to Ubuntu and I would like to know if my wireless network camera (Encore ENVCWI-G1) can be connected to it. I know that Ubuntu is not listed on the supported O.S. but still, I would like to try to give it a try..

 I tried to connect it, but it gets stuck in "Requesting Network Address" before a pop-up message appears saying that the wireless network is disconnected. I'm using Ubuntu 10.04 and I tried connected to Wifi networks without problems..

When using xp, I can access the camera by connecting to it wireless-ly. It takes a few seconds while acquiring network address before connected. After a successful connection, I can view it by entering the IP address (169.254.1.240) using a browser.


Hope that someone can help regarding this matter and Thank you in advance! :)

---

### Post by grahammechanical on 2010-08-25
I do not know the answer. I am not that clever but I can ask questions that might help someone else find the answer.

Please describe how you try to connect to this camera. What steps do you take? Left click on the network manager icon? Then select a network to connect to? This will tell us if the camera's wireless is being detected by the computer's operating system? Can the camera be connected by USB cable? Have you tried setting up a new wireless network? Left click - create new wireless network.

This is just a silly thought, but is the camera switched on? Are the batteries discharged? Do you have to do anything to the camera to allow wireless access. I should think that, like a laptop, having wireless on all the time would (a) allow anyone to access the camera wirelessly, (b) use up battery power.

These are just some thoughts to let you know that you are not alone.  Regards.

---

### Post by zeee on 2010-08-25
Hi grahammechanical,

thank you for your post. :D

I think the OS can recognize the camera because when I click on the network manager icon, I can see the assigned name for the IP camera (Encore IP Camera). I can try to connect to it by clicking on it, but as I have said before, it gets stuck while requesting network address..

I also tried your suggestion to create a new wireless connection but it was unsuccessful..

The camera is connected to the wall outlet and it can connect to a computer on xp/vista just fine. The camera also has a blinking green light if it is ready for a connection. It can be connected locally using an ethernet cable, but I do not have one at the moment so that will have to wait.

I hope there are work arounds because this seems to be just a software problem. Thanks again. :)

---

### Post by dineshs on 2010-08-25
A guess
just try this command```
sudo dhclient
```
If it doesnt work post the results of
```
sudo lshw -C network
```

---

### Post by zeee on 2010-08-26
Hi dineshs,

these were the results for:

sudo dhclient

```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:25:d3:dd:cd:69
Sending on   LPF/wlan0/00:25:d3:dd:cd:69
Listening on LPF/eth0/90:e6:ba:f1:ba:16
Sending on   LPF/eth0/90:e6:ba:f1:ba:16
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

sudo lshw -C network

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 90:e6:ba:f1:ba:16
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:e800(size=256) memory:feaff000-feafffff memory:feac0000-feadffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:dd:cd:69
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:febf0000-febfffff
```


Sorry, I'm clueless about the 1st result so I just did both.

Thanks for the help by the way. ;)

---

### Post by dineshs on 2010-08-26
> When using xp, I can access the camera by connecting to it wireless-ly. It takes a few seconds while acquiring network address before connected. After a successful connection, I can view it by entering the IP address (169.254.1.240) using a browser.
Do you have some software like DVR installed in windows?
While accessing the camera via windows go through the camera menu to see if you can configure an IP for it

---

### Post by zeee on 2010-08-26
I do have a DVR software but the IP address configuration is done using an explorer (I.E., Mozilla, Etc.). Do I need to change the IP address to connect to Ubuntu through WLAN?

I'm still researching for ways to connect it to Ubuntu.. I hope this can be done in a week or so. I'm planning to migrate my computer vision program here in Ubuntu for the presentation of my final design project. :p

---

### Post by dineshs on 2010-08-26
Can you set an IP to camera (say 192.168.1.1 )via windows.I mean is there any provision in the camera menu for that?

---

### Post by zeee on 2010-08-26
The default IP address before is 192.168.0.30 and I can't connect to it my Windows PC.

There is an option to change the IP address to DHCP, but it reverts back to IP address 192.168.0.30 and I can't access it again.

But when I change it to static IP Address 168.254.1.240 (Submask 255.255.0.0), I can now access the camera.

I suppose it is because of this ( from the advanced installation guide of cam):

```
3.3 Configuring the IP Address of the PC
If you are failed to access to the camera, please check the IP
address of your computer. When you connect the camera to your
computer directly to proceed with configuration of the camera, you
need to set up the IP addresses to be in the same segment for the
two devices to communicate.

6. To configure a fixed IP address that is within the segment of the
camera, select the Use the following IP address option. Then,
enter an IP address into the empty field. The suggested IP
address is 192.168.0.x (x is 0~254 except 30), and the
suggested Subnet mask is 255.255.255.0. 
```


Again, thanks dineshs. :D

---

### Post by dineshs on 2010-08-26
> The default IP address before is 192.168.0.30 and I can't connect to it my Windows PC.Set it as 192.168.0.30
Now boot to ubuntu
Right-click on the NM icon Edit Connections. 
Select the tab, wireless
select the camera device-edit 
select ipv4 
method-manual 
address 192.168.0.250
mask 255.255.255.0 
gateway 192.168.0.30
then hit enter 
apply
Now try 192.168.0.30 via firefox

---

### Post by zeee on 2010-08-27
Haha.. Thanks man! The connection was successful. :D
I can see the connection is established.

Now, I do have problems accessing the video stream using the mozilla/chrome..

192.168.0.30 was not found

192.168.0.250 returned OK, but no video stream was shown.

I tried the same cgi scripts for viewing the camera in xp (cgi/jpg/image.cgi -OR- cgi/mpg/mpeg.cgi)

Later I'll try to use zone-minder, etc. to view it.

---

### Post by dineshs on 2010-08-27
While setting up IP ie 192.168.0.30 did you change the port?Default is 80

---

### Post by zeee on 2010-09-07
@dineshs - Sorry for the late reply! But the good news is I'm able to access the camera now! :p

Thanks for the help! I really appreciate it. I'm beginning to love Ubuntu now. :D

---

