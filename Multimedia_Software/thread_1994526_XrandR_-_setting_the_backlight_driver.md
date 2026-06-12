---
title: "XrandR - setting the backlight driver?"
date: 2012-06-02
forum: Multimedia Software
---

### Post by mondschein on 2012-06-02
Hello,

I have two entries in /sys/class/backlight. if I change the value in acpi_video0/brightness nothing happens, but I can dim the monitor by modifying the value in intel_backlight/brightness.

The problem is that XrandR changes the value in acpi_video0/brightness. As a result the xfce4-power-manager (I am using lubuntu), which uses the XrandR function XRRChangeOutputProperty sets the wrong value.

So how can I change the backlight device in XrandR or how can I remove acpi_video0/brightness?

Best regards

mondschein

---

### Post by Balahuop on 2013-05-26
Hello, 

I know this thread is getting old, but since I finally found a solution for this specific problem, I'm posting here.
So I manage to set the driver used by the X server for backlight control by generating a xorg.conf file. 
Then in the section "Device", by uncommenting the "Backlight" line and set it with the name of the driver's folder you intend to use in /sys/class/backlight/ (Not the complete path, juste the name of the folder.).

Best regards, 

Balahuop

---

