---
title: "Crash Due to BlueZ Error - but No Bluetooth in my Laptop"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by kovesz on 2010-01-13
Hi,

I installed Ubuntu 9.10 yesterday on my laptop, and it keeps crashing while I am connected to the Internet, especially when I am downloading large files. It even crashed when I was running Ubuntu from a Live CD, so the fails are definitely not the result of my tinkering.

I searched the logs for errors and found a recurring error message, generated exactly when the crashes happened. It says:

```
NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
```I found that BlueZ is a Bluetooth protocol stack. But my laptop don't even have a Bluetooth in it, and I haven't tried to use external ones since yesterday.

What should I do? Should I disable BlueZ somehow? How could I do that? Is it possible that this BlueZ error is a result, rather than the cause of the crash? Any responses are welcome.

System data:
ASUS F5SR-AP29 notebook
CPU: Intel T5800
VGA: ATI Mobility Radeon HD 3470
WLAN card: Atheros chipset
Bluetooth: none

---

