---
title: "GSPCA module not loading for webcam"
date: 2008-12-23
forum: Multimedia Software
---

### Post by gdselzer on 2008-12-23
I am having problems getting my usb webcam to work on recent install of 8.10.  My webcam is listed here ([http://moinejf.free.fr/webcam.html]("http://moinejf.free.fr/webcam.html")) as being supported by the sonixj subdriver of gspca (gspca_sonixj?)  However, when I plug the cam in, all get in dmesg is:
> 
[ 2687.456539] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 2687.674335] usb 3-1: configuration #1 chosen from 1 choice

I tried:
```
$ sudo modprobe gspca_sonixj
```

but that didn't seem to do anything.

Can someone please help to troubleshoot this?

Attached is the results of lsusb -vv

Thanks

---

### Post by gdselzer on 2008-12-23
bump

---

### Post by gdselzer on 2009-05-05
Just realized I should update this.  I was able to resolve this by compiling gspca myself.  See this thread where I document the process.  

[http://ubuntuforums.org/showthread.php?t=1020873]("http://ubuntuforums.org/showthread.php?t=1020873")

---

