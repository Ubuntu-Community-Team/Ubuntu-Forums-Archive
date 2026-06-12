---
title: "realtek rtl8192cu can NOT work in ubuntu 12.04."
date: 2012-12-24
forum: Networking &amp; Wireless
---

### Post by waterloo2005 on 2012-12-24
I have downloaded driver from realtek site and do like the post: [http://ubuntuforums.org/showthread.php?t=1949810](http://ubuntuforums.org/showthread.php?t=1949810) .
But everytime I plug the card, system dies.

How to do with it ?
I use 12.04 amd64.

I also try 12.10. When I boot with livecd of 12.10, the card can work. But after I install 12.10, I find the driver of 12.10 is still NOT stable, sometimes works and sometimes not.

Thanks

---

### Post by ahallubuntu on 2012-12-24
This is how I did it - worked in both 12.04 and 12.10:

[http://ubuntuforums.org/showthread.php?p=12318056#poststop](http://ubuntuforums.org/showthread.php?p=12318056#poststop)

Perhaps you could post some more information about your system if these instructions are not working?  Can you look in your syslog to see what happened when you plugged the card in?

---

### Post by waterloo2005 on 2012-12-27
After I plug the card until the system dies, I find below in /var/log/syslog file :
```
Dec 27 22:13:15 ubuntu1204-tf kernel: [  777.297768] usb 2-1.3: new high-speed USB device number 5 using ehci_hcd
Dec 27 22:13:15 ubuntu1204-tf mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3"
Dec 27 22:13:15 ubuntu1204-tf mtp-probe: bus: 2, device: 5 was not an MTP device
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207844] rtw driver version=v3.4.4_4749.20121105 
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207847] Build at: Dec 21 2012 10:00:29
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207878] register rtw_netdev_ops to netdev_ops
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207880] CHIP TYPE: RTL8188C_8192C
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207883] 
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207883] usb_endpoint_descriptor(0):
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207885] bLength=7
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207886] bDescriptorType=5
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207887] bEndpointAddress=81
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207888] wMaxPacketSize=200
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207889] bInterval=0
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207890] RT_usb_endpoint_is_bulk_in = 1
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207892] 
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207892] usb_endpoint_descriptor(1):
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207893] bLength=7
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207894] bDescriptorType=5
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207896] bEndpointAddress=2
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207897] wMaxPacketSize=200
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207898] bInterval=0
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207899] RT_usb_endpoint_is_bulk_out = 2
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207900] 
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207900] usb_endpoint_descriptor(2):
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207902] bLength=7
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207903] bDescriptorType=5
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207904] bEndpointAddress=3
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207905] wMaxPacketSize=200
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207906] bInterval=0
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207907] RT_usb_endpoint_is_bulk_out = 3
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207908] 
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207909] usb_endpoint_descriptor(3):
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207910] bLength=7
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207910] bDescriptorType=5
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207911] bEndpointAddress=84
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207912] wMaxPacketSize=40
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207913] bInterval=1
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207914] RT_usb_endpoint_is_int_in = 4, Interval = 1
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207915] nr_endpoint=4, in_num=2, out_num=2
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207915] 
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.207916] USB_SPEED_HIGH
Dec 27 22:14:28 ubuntu1204-tf kernel: [  850.208181] Chip Version ID: VERSION_NORMAL_UMC_CHIP_88C_B_CUT.
```

---

