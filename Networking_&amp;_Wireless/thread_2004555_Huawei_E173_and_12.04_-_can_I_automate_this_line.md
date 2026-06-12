---
title: "Huawei E173 and 12.04 - can I automate this line?"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by tpprynn on 2012-06-16
In order to get my Mobile Broadband dongle working I have to type this into the terminal for each online session, i.e. each boot:

sudo modprobe usbserial vendor=0x12d1 product=0x1c10

This has been necessary since 12.04. Other solutions including what worked prior to 12.04 haven't worked.

Can I automate this line, and without having to type in my password? What would be the procedure? I've not really got the hang of scripting so idiot-proof instructions would be necessary.

If this line _was_ in a script and the dongle wasn't plugged in, would some kind of bug/crash occur? If so could the script be amended to take this into account?

Thanks!

---

### Post by tpprynn on 2012-06-18
After needlessly trying a simple script that didn't work, all it needs is this:

Open the file /etc/rc.local (by using sudo gedit /etc/rc.local in the terminal). Add the line

sudo modprobe usbserial vendor=0x12d1 product=0x1c10

before the line beginning 'exit'. Then reboot.

---

