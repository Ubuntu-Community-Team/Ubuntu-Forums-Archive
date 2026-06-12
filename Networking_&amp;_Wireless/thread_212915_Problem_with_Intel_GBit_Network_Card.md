---
title: "Problem with Intel GBit Network Card"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by AtrejuT on 2006-07-10
Hello Folks,


well, I just installed Ubuntu 6.06 a couple of days ago and everything worked fine until yesterday.
Today my Network Cards (LAN and WLAN) both stopped working. The only thing I could find in syslog was

e1000: probe of 0000:02:00.0 failed with error -5
e1000: 0000:02:00.0: e1000_probe: The EEPROM Cheksum Is Not Valid

now I found one comment on the internet suggesting to disable the card in BIOS, reboot, reboot and enable it again and for him it worked. for me it did not - though at least the WLAN worked while LAN was disabled. 

now I am quite at a loss what to do, and don't really know my way around linux yet either... 

so i'd be grateful for any help.

I am running the latest 686 kernel on a Samsung X60 Studentbook (Centrino Duo T2300, 100GB SATA HD, Centrino Wlan etc., ATI X1600, Intel HDA sound (not working either...) ...)

Thanks

Atreju

---

### Post by lawngn0mex on 2006-07-10
you have any available BIOS updates?

---

### Post by AtrejuT on 2006-07-10
The latest I can find on Samsung's web page is what I have...
Also checked for firmware updates of the card but could not find any...

Atreju

---

### Post by imransulehri on 2006-08-17
hello
i have with me samsung x60 you have installed the ubuntu on your system i am tryin to install it it is not working at first it use to stuck on laoding acpi modules then i have to put it off by inserting acpi=off and now it did not detect my graphical interface and on start if then gives me prompt ...do please help me in this regard also it is not detecting my network card also
regards

---

