---
title: "gspca wont detect Creative"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by DESiBELi on 2007-01-15
I have Creative Live! Cam Vista, apt-get installed spca5xx, compiled and installed from source, gspca also installed from source.

Now modprobe gspca works fine... (?)

[I]# lsmod | grep gspca
gspca                 649936  0 
videodev                9728  1 gspca
usbcore               130304  7 gspca,usblp,hci_usb,usbhid,ehci_hcd,uhci_hcd[/I]

But when I reconnect my cam, it wont detect it nor add /dev/video*
[I]
# dmesg
[17179900.696000] /root/gspcav1-20070110/gspca_core.c: gspca driver 01.00.12 registered
[17179916.604000] usb 2-1: USB disconnect, address 4
[17179923.704000] usb 2-1: new full speed USB device using uhci_hcd and address 5
[17179923.932000] usb 2-1: configuration #1 chosen from 1 choice[/I]

Now the same thing happens if I rmmod gspca and modprobe spca5xx...
And if I load them both. What am I doing wrong here?

[I]# lsusb
Bus 002 Device 005: ID 041e:4052 Creative Technology, Ltd **[Reported to work]("http://www.ubuntu-es.org/index.php?q=node/33630")**[/I]

[I]# uname -r
2.6.17-10-386
[/I]

---

