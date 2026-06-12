---
title: "Wired Network not getting detected on Lenovo Y480"
date: 2012-09-01
forum: Networking &amp; Wireless
---

### Post by 5prasad on 2012-09-01
Hi,
I recently bought Lenovo Y480 and have installed Ubuntu 12.04 on it. However, it is not detecting ethernet connection. It is getting detected on Windows though on the same laptop. I tried to follow these steps [http://www.zyxware.com/articles/2680/solved-wired-connection-eth0-not-detected-in-ubuntu-12-04](http://www.zyxware.com/articles/2680/solved-wired-connection-eth0-not-detected-in-ubuntu-12-04)
But,it shows this error at the end: 

sushant@sushant-Lenovo-IdeaPad-Y480:~/Downloads/compat-wireless-2012-05-10-p$ make install
FATAL: Could not open /lib/modules/3.2.0-29-generic/modules.dep.temp for writing: Permission denied
make: *** [uninstall] Error 1
sushant@sushant-Lenovo-IdeaPad-Y480:~/Downloads/compat-wireless-2012-05-10-p$ modeprobe alx
No command 'modeprobe' found, did you mean:
 Command 'modprobe' from package 'module-init-tools' (main)
modeprobe: command not found

Any help would be appreciated.

---

### Post by chili555 on 2012-09-01
> $ make install
FATAL: Could not open /lib/modules/3.2.0-29-generic/modules.dep.temp for writing: Permission deniedPlease try:```
[COLOR="Red"]sudo[/COLOR] make install
```> $ modeprobe alxPlease try:```
[COLOR="Red"]sudo modprobe[/COLOR] alx
```I will be fascinated to hear your report.

---

### Post by 5prasad on 2012-09-01
Yahooooooooo! It worked!!Thank you chili555!!!!!!!!

---

