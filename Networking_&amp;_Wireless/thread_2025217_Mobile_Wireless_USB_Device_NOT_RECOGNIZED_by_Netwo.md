---
title: "Mobile Wireless USB Device NOT RECOGNIZED by Network Manager"
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by sgriggly on 2012-07-14
Hello, 

I'm running Natty Narwhal release (11.04)

I have a mobile broadband device here in India (called Tata Photon+, or Photon Plus). 

When I first plugged in the USB device, the Network Manager recognized it correctly, but would not connect. After some search, I followed the advice from [this page]("http://bernaerts.dyndns.org/linux/209-ubuntu-tata-photonplus"), which said to install the latest modeswitch .deb (which I did: 

sudo dpkg -i usb-modeswitch_1.1.9-1ubuntu3_amd64.deb
sudo dpkg -i usb-modeswitch-data_20120120-0ubuntu1_all.deb 

At this point, Network Manager still recognized the device; After installing the modeswitch .debs, I set up the Mobile Broadband Connection (country: India, device: Photon+... Number: #777, Username: internet, PW: internet... etc.) and viola, the device WORKED. 

That is, until I shut my computer... When it came out of hibernation, the device no longer showed up in Network Manager (and hasn't since). I tried all the "dummy" stuff... Restarting, plugging the device in and out, trying all the different USB bays, etc., to no avail. 

The good news is, the device is still recognized by my machine, it just doesn't appear in Network Manager automatically like it should. lsusb shows the device: 

Bus 005 Device 006 ID 12d1:1505 Huawei Technologies Co., Ltd. 

So, I know the device is plugged in and working... How do I get the Network Manager to recognize it again so I can actually USE it???

---

### Post by sgriggly on 2012-07-14
tried going to Synaptic Manager and updated all the USB modeswitch packages... then restarted. No luck... (I guess what trips me up is that Network manager recognized the device BEFORE I updated modeswitch, but no longer does? _wtf_ FYI, device worked perfectly fine, plug-and-play, in 10.10)

---

### Post by sgriggly on 2012-07-15
SOLVED the following way: instead of "reloading" or "updating" the modeswitch debs, i DELETED them, and REINSTALLED (via Synaptic Package Manager). Network Manager now recognizes the device... Fingers crossed that it still does after restart!

---

