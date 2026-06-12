---
title: "Keyboard stops working when Rythmbox is running"
date: 2010-05-17
forum: Multimedia Software
---

### Post by pjaikins on 2010-05-17
I have 10.04 (kernel 2.6.32-22) and have noticed that whenever i have Rhythmbox running; the keyboard stops working in any apps. As soon as I close Rhythmbox, they work again!

Regards,
     Peter

---

### Post by vaxius on 2010-05-17
Could you run it from a terminal and relay the output?

---

### Post by pjaikins on 2010-05-17
> **vaxius said:**
> Could you run it from a terminal and relay the output?

Attached is the redirected output when run from the command line and attempting to use the keyboard both in rhythymbox and firefox.

---

### Post by pjaikins on 2010-05-17
> **pjaikins said:**
> Attached is the redirected output when run from the command line and attempting to use the keyboard both in rhythymbox and firefox.

Disabling LIRC plugin resolves the issue, but I want to use LIRC with my firefly remote in the future. What can be done to resolve the problem?

---

### Post by vaxius on 2010-05-18
> **pjaikins said:**
> Disabling LIRC plugin resolves the issue, but I want to use LIRC with my firefly remote in the future. What can be done to resolve the problem?

Your log shows Rhythmbox having trouble finding LIRC config files. I don't know why that would interfere with the keyboard, but maybe the problem will go away once LIRC is configured with your remote.

---

