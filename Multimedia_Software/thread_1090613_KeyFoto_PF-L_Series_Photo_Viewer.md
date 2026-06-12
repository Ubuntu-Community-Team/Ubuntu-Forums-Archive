---
title: "KeyFoto PF-L Series Photo Viewer"
date: 2009-03-08
forum: Multimedia Software
---

### Post by cyrilmethodius on 2009-03-08
I am helping a friend with ubuntu 8.10 = I still have 8.04.   The friend just got a KeyFoto PF-L Series Photo Viewer[1] as a gift and we're having trouble getting to work on either 8.10 or 8.04.  Attaching to USB it charges the battery but there is no way to transfer photos to it.  Has anybody found drivers or anything that will work with this photo viewer?


[1] [http://www.techfresh.net/keyfoto-the-digital-picture-keychain/](http://www.techfresh.net/keyfoto-the-digital-picture-keychain/)

---

### Post by cariboo on 2009-03-08
It should just show up as a usb storage device. Can you post the output of dmesg when the device is plugged in :

```
dmesg | tail -n10
```

The above command will print the last 10 lines of dmesg in a terminal.

Jim

---

### Post by cyrilmethodius on 2009-03-12
> **cariboo907 said:**
> It should just show up as a usb storage device. Can you post the output of dmesg when the device is plugged in :

```
dmesg | tail -n10
```

The above command will print the last 10 lines of dmesg in a terminal.

Jim

Thanks Jim.  Here is what it gives:

[   78.848185] Bluetooth: RFCOMM socket layer initialized
[   78.848201] Bluetooth: RFCOMM TTY layer initialized
[   78.848203] Bluetooth: RFCOMM ver 1.8
[  160.568448] NET: Registered protocol family 17
[  163.471455] NET: Registered protocol family 10
[  163.472110] lo: Disabled Privacy Extensions
[  175.638842] eth0: no IPv6 routers present
[  445.753196] usb 1-3: USB disconnect, address 3
[ 4874.434460] usb 2-4: new full speed USB device using ohci_hcd and address 5
[ 4874.645278] usb 2-4: configuration #1 chosen from 1 choice

---

### Post by compeng on 2009-10-16
I found a similar thread and posted info into it.

[http://ubuntuforums.org/showpost.php?p=8114000&postcount=6](http://ubuntuforums.org/showpost.php?p=8114000&postcount=6)

---

### Post by teledyn on 2010-12-25
having the identical issues here -- the included software photoviewer also will install without incident but will not run under Wine.

---

### Post by teledyn on 2010-12-25
> **cariboo907 said:**
> It should just show up as a usb storage device. 

Jim

I'm curious to know: if this is what you observed, which version of Ubuntu were you using?  I have tried 8.10, 9.10 and 10.04 and on all the systems I get the same behaviour, the usb device is reported and nothing more


[562825.216729] usb 1-2: new full speed USB device using ohci_hcd and address 5
[562825.077780] usb 1-2: configuration #1 chosen from 1 choice

Also, in trying to run the included software under Wine I see that it asks for cximage.dll, which Symantic curiously lists as a Spyware library!! 

err:module:import_dll Library cximage.dll (which is needed by L"C:\\Program Files\\Mars\\MR7910\\mr7910.exe") not found

I did locate the other needed DLL, MFC42.DLL and installed that, and the program then runs but does not detect the KeyFoto device on the USB.

---

### Post by teledyn on 2011-07-30
just to confirm: the device is still unrecognized when the app is run in Wine 1.3.  Perhaps progress, there is nothing of interest reported by either kern.log, syslog or dmesg :(

---

### Post by cyrilmethodius on 2011-09-01
Sorry I did not get back to this sooner.   The Keyfoto device is my sister's and I have not had the chance to try it out again.

Originally, I was using Ubuntu 10.04.   I now have 11.04 on my Inspiron laptop so I will give that a try next time I see her and update the thread with what I find.

---

