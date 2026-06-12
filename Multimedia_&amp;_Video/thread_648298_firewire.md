---
title: "firewire"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by brandon333 on 2007-12-23
how do i enable the firewire module? in kino when i hook up my dv camcorder, nothing happens but an error saying module not loaded.

---

### Post by macabro22 on 2007-12-24
```
sudo modprobe ohci1394
```

---

### Post by LCDR_Kahuna on 2007-12-25
I have done that but still its as if there is no device plugged in at all

---

### Post by macabro22 on 2007-12-25
actually, you have to remove the module first and then reload it:

```
sudo rmmod ohci1394
sudo modprobe ohci1394
```

Now the device should be recognized.

---

### Post by brandon333 on 2008-01-01
I am still dealing with this issue, anyone?  I have done everything suggested, II34 Module error, could it be my dv camcorder goes into my external hard drive versus straight on? it works in macosx so dont think that would be it

---

### Post by macabro22 on 2008-01-03
> **brandon333 said:**
> I am still dealing with this issue, anyone?  I have done everything suggested, II34 Module error, could it be my dv camcorder goes into my external hard drive versus straight on? it works in macosx so dont think that would be it

Brandon333, Try turning the device on only after you removed and reloaded the ohci1394 module. That usually works for me.

---

