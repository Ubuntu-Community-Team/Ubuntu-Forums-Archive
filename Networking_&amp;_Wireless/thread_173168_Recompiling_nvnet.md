---
title: "Recompiling nvnet"
date: 2006-05-09
forum: Networking &amp; Wireless
---

### Post by fluffington on 2006-05-09
I've got an nForce 430 motherboard, which means I need nVidia's proprietary driver to get networking to work. The problem is that every time the kernel gets upgraded, I have to reinstall the driver, which is irritating (and usually involves several reboots because I need networking to apt-get install the headers for the new kernel, and that means using an earlier kernel).

Why isn't the nvnet driver in the Ubuntu repositories? Or, if it is, where?

---

### Post by Aphorism on 2006-05-09
The provided forcedeth driver should work for ethernet.

---

### Post by fluffington on 2006-05-27
[QUOTE=Aphorism]The provided forcedeth driver should work for ethernet.[/QUOTE]

The forcedeth driver does work, but not at full speed or very reliably. That wasn't my question, though; I wanted to know why Ubuntu packages the nVidia graphics driver but not the nVidia network or audio drivers.

---

