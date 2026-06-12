---
title: "Creative Live! Cam Video IM"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by niartv on 2006-11-12
Dear All,

I have been having some trouble to configure this cam on Ubuntu dapper 6.06.1 LTS.  ](*,) 

The cam ID:
```
ID 041e:4053 Creative Technology, Ltd
```

dmesg:
```
[17242261.348000] usb 1-1: new full speed USB device using uhci_hcd and address 7
[17242261.552000] gspca_core.c: USB SPCA5XX camera found.(ZC3XX)
[17242261.552000] gspca_core.c: [spca5xx_probe:3885] Camera type JPEG
[17242261.552000] Vimicro/zc3xx.h: [zc3xx_config:515] Sensor ID:22
[17242262.216000] Vimicro/zc3xx.h: [zc3xx_config:522] Find Sensor Tas5130 (FV0250)
[17242262.220000] gspca_core.c: [spca5xx_getcapability:1163] maxw 640 maxh 480 minw 176 minh 144
[17242262.220000] usbcore: registered new driver gspca
[17242262.220000] gspca_core.c: gspca driver 01.00.04 registered
```

lsmod:
```

gspca                 620560  0
videodev                9856  2 gspca,ov511
usbcore               130820  5 gspca,ov511,ehci_hcd,uhci_hcd

```

ls -lart /dev/video*:
```

crw-rw---- 1 root video 81, 0 2006-11-12 18:24 /dev/video0
lrwxrwxrwx 1 root root      6 2006-11-12 18:24 /dev/video -> video0

```

camorama:
```

Could not connect to video device (/dev/video0).
Please check connection

```

in Ekiga preferences, video devices it says:
"no device found"

Any idea what I could try ? :rolleyes: 

Vtrain

---

### Post by niartv on 2006-11-13
adding the user the video group at /etc/groups made Camorama work and Ekiga shows the video feed 8)  . But Amsn, kopete, mercury aren't able to video chat yet... :???:

---

### Post by resadent on 2008-02-06
> **niartv said:**
> adding the user the video group at /etc/groups made Camorama work and Ekiga shows the video feed 8)  . But Amsn, kopete, mercury aren't able to video chat yet... :???:
Did it work? I am interested to buy this webcam...

---

