---
title: "Novatel ovation MC679 (Mobile broadband) + Ubuntu 12.10"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by mibarrios on 2013-05-21
Insert the device (MC679), and then:

```
xxxxxx@xxxxxxx:~$ sudo modprobe usbserial vendor=0x1410 product=0x7031 
```

```
xxxxxx@xxxxxxx:~$ lsusb   
```


Terminal output (in my laptop: Samsung S9):

[I]Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 0fca:8004 Research In Motion, Ltd. Blackberry Handheld
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
**Bus 001 Device 008: ID 1410:7031 Novatel Wireless **
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 004: ID 2232:1024[/I]

Driver:
Download ([here]("https://www.dropbox.com/s/74g1w339bg49kpp/Novatel_MC679_V1.0.5.001.7z")), unzipp and install (in my case: .deb):

```
xxxxxx@xxxxxxx:~$ sudo dpkg -i LinuxDrivers_v1.0.5.001.deb 
```

the device will be auto-mounted as USB (please, unmount it).

Then, create a "New  mobile broadband connection":
GUI approach: edit connections>Mobile Broadband>Add

the required information must be supplied by your internet provider (in my case: [http://support.sasktel.com/app/answers/detail/a_id/15921/~/connecting-to-the-internet-with-a-novatel-wireless-device](http://support.sasktel.com/app/answers/detail/a_id/15921/~/connecting-to-the-internet-with-a-novatel-wireless-device))

After that, you are ready to use the configured network!

---

