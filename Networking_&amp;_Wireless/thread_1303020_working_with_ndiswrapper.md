---
title: "working with ndiswrapper"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by sk8trf on 2009-10-27
ok so i got everything installed for the ndiswrapper, i put in my drivers disk that came with my usb adapter and installed the driver, when it finished installing it said hardware not found, but in the window after i click ok it says the hardware is present and when i type lsusb -l it gives me my chipset says that hardware is present and drivers are installed but for some reason it still wont detect any networks. can someone please help me please, im loving this new 9.10 and i just need some internet so my weather will work and stuff. cant wait till the actual release comes out

---

### Post by arepaking on 2009-10-31
Did you execute this?

```
sudo modbprobe ndiswrapper
```

---

