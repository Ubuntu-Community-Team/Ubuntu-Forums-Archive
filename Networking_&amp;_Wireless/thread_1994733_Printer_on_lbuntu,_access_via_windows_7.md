---
title: "Printer on lbuntu, access via windows 7"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by runtman on 2012-06-03
Hello there, to make things less confusing I have listed PC names see below
lbuntu = 192.168.1.10
Windows 1 = 192.168.1.2
Windows 2 = 192.168.1.5
Windows 3 = 192.168.1.7

Currently, I have a USB samsung CLP310 plugged into my lbuntu machine, which I added via CUPS [http://localhost:631](http://localhost:631), Windows 1 is able to find the printer and print to it, but any other machine is not including the ubuntu machine. Looking at the error log, it says this;
```
W [03/Jun/2012:14:00:09 +0100] failed to CreateDevice: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
``````
E [03/Jun/2012:10:19:08 +0100] Returning IPP client-error-not-authorized for Print-Job (ipp://localhost:631/printers/SamsungCLP310) from localhost
```The reason I have it on the ubuntu machine is because my dad refuses to move the printer, and the PC is so low spec I had to stick lbuntu on it. I think the issue is somewhat to do with CUPS/SAMBA but as I am such a noob, I have no idea how to resolve it.

Can anyone help?

-- EDIT.

Sorry all machines can see the printer, but when a print job is sent to the printer it says "completed" but does not print. Only Windows 1 can successfully print anything.

---

### Post by runtman on 2012-06-03
Can anyone help?

---

### Post by runtman on 2012-06-04
Is anyone able to help with this at all?

---

