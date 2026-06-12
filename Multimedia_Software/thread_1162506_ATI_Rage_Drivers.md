---
title: "ATI Rage Drivers?"
date: 2009-05-17
forum: Multimedia Software
---

### Post by mrd489 on 2009-05-17
I recently acquired a few ATI RAGE PRO but can't find any drivers for xubuntu. Any help?

Here's the [[COLOR="Blue"]Wikipedia page[/COLOR]]("http://en.wikipedia.org/wiki/ATI_Rage") if it helps anyone...

---

### Post by RedSingularity on 2009-05-17
You check in the system>admin>hardware drivers?

---

### Post by chicken_Combo on 2009-05-17
nothing in the drivers list.... its so old ati is denying its existence... i called them up they say it doesent exist even though i can clearly see that its working, just no drivers....



(i asked mrd to post the question since i didnt have an accnt)

---

### Post by nolliecrooked on 2009-05-17
have you tried to enable desktop effects? a card that old should be pretty well supported by the open source drivers.

---

### Post by Melcar on 2009-05-17
The open source drivers support the card (and are the only drivers you can use anyways).  Ubuntu should load them by default, otherwise you can edit your xorg.conf to load them; just open up xorg.conf for editing and add the following line to the "Device" section:

```
Driver  "radeon"
```

Save the file and reboot.

---

