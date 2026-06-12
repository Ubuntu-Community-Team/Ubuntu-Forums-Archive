---
title: "Gsmart Mini 3 webcam no /dev/video0"
date: 2010-08-31
forum: Multimedia Software
---

### Post by skywriter on 2010-08-31
Please help with webcam!
I have have learned this thread first: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678) .
After plugging camera i got the following from "dmesg":
> [61670.227091] gspca: probing 055f:c520
[61670.617116] gspca: probe ok
[61670.617195] gspca: probing 055f:c520
[61670.746256] gspca: disconnect complete

I healed this by replacing the module gspca_sunplus with gspca_spca500 this way:
> sudo modprobe -r gspca_sunplus
sudo modprobe -r gspca_main
sudo modprobe gspca_spca500

Now i get the following from dmesg:

> [63545.151603] Linux video capture interface: v2.00
[63545.157233] gspca: main v2.7.0 registered
[63545.159371] usbcore: registered new interface driver spca500
[63545.160261] spca500: registered

Seems OK, but I still have no "/dev/video0". How to get back it to live?

> lsb_release -rd
Description:    Ubuntu 10.04.1 LTS
Release:        10.04

---

