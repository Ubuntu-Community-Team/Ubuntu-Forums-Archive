---
title: "ADSL Router(USB)"
date: 2006-01-05
forum: Networking &amp; Wireless
---

### Post by hanchung on 2006-01-05
I have problems with this ADSL Router(Prolink Hurricane 9000P). Its connected tru a 4 usb head hub(USB extender) and Ubuntu Linux has problem detecting it, even that the box said it supports linux. I tried finding the driver in the CD included(ADSL Router), no luck. Any suggestion and/or help would be appretiated. Thank you.

(Using Ubuntu 5.10 Gnome)

---

### Post by mips on 2006-01-05
Does your router have an ethernet port ?

---

### Post by mips on 2006-01-06
[http://www.fida.com/products/h9000p.htm](http://www.fida.com/products/h9000p.htm)

Who is your ISP and provide a link to their website please ?!

You need to ensure the device is configured for routed mode and NOT bridged mode.

The box says it supports Linux but probably only if you use the ethernet port.

Please connect to it via the ethernet port and try and use it that way. If you get stuck connect to it via ethernet on your windows machine and try to get it to work from windows via the ethernet port. If you get stuck call your ISp and ask then to assist with the ethernet/windose config.

Once you have it working open a command prompt (dos window) from windows and type **ipconfig /all** and paste the entire output here. the we can do the ubuntu config after that.

---

