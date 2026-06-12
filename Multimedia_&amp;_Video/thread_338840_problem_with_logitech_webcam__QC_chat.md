---
title: "problem with logitech webcam : QC chat"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by andrewtw on 2007-01-15
i have checked lsusb, there is my QC Chat
and spca5xx does support this
```

$> lsusb 

Bus 002 Device 006: ID 046d:092e Logitech, Inc.   <--this 
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

then i download spca5xx-20060501.tar.gz	 
"*make && make install*" the spca5xx
and "*modprobe spca5xx*" , 
```

$> lsmod |grep spca
spca5xx               664720  0
videodev                9856  1 spca5xx
usbcore               130820  6 spca5xx,ndiswrapper,usbhid,ohci_hcd,ehci_hcd

```


then i try camorama, it pop a error message : 
**Could not connect to video device (/dev/video0), please check connection**
**there is no /dev/video***   ( ls /dev/video got nothing! )

and this is dmesg
```

$> dmesg | grep spca
[17180388.280000] usbcore: registered new driver spca5xx
[17180388.280000] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[17183768.264000] usbcore: deregistering driver spca5xx
[17183768.264000] drivers/usb/media/spca5xx/spca5xx-main.c: driver spca5xx deregistered
[17184126.016000] usbcore: registered new driver spca5xx
[17184126.016000] /home/fyodor/packages/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered

```

i'll be much appriciate if anyone give any suggestion :(  thanks !

---

