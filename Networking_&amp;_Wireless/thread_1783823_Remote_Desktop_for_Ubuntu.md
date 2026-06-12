---
title: "Remote Desktop for Ubuntu"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by HokeyFry on 2011-06-16
Is there anything like Remote Desktop in Windows for Ubuntu? VNC is only screen sharing, I am looking for something that allows you to log in remotely and use your desktop (remote session) rather than just sharing your current screen.

---

### Post by collisionystm on 2011-06-16
> **HokeyFry said:**
> Is there anything like Remote Desktop in Windows for Ubuntu? VNC is only screen sharing, I am looking for something that allows you to log in remotely and use your desktop (remote session) rather than just sharing your current screen.

yes there is an rdp program that you can use. However, be aware that it doesnt work the same as windows. It lets you in, but it starts another session. There isnt a way ( that I am aware of ) to rdp to your session that you left running on it. 

I.E. in windows you can mstsc /admin or mstsc /console to rdp directly to the computer on terminal 0. RDP on ubuntu doesnt let you rdp to terminal 0. It will be as if you just logged in after a reboot.

```
sudo apt-get install xrdp
```

---

### Post by ninostar on 2011-11-30
Hello,
 
I also tried to install xrdp, but it isn't recognized as a package when I try installing using "apt-get install xrdp" (I get an error, unknown package). 
 
Here's info about Ubuntu from my hosting account:
 
Distribution: Ubuntu (Maverick) - 64-bit
Kernel: vmlinuz-2.6.32-5-xen-amd64
Initrd: initrd.img-2.6.32-5-xen-amd64

Regards

---

