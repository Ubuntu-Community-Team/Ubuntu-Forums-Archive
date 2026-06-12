---
title: "Cannot connect to DNS server - Intrepid 8.10"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by Bill Roberts on 2009-02-21
I have been running Intrepid 8.10 on an AMD64 and using a cable modem connected through a Netgear router.

I am switching to DSL and I have setup the DSL modem and the Netgear router.  I connect to a Windows laptop and 2 printers successfully and the Intrepid machine can see the other devices on the router.  The day I set it up, the Intrepid machine connected to the Internet and I used the browser.

The second day I re-booted to connect a usb hard drive and when I restarted, the Intrepid machine no longer sees a DNS server.

I can ping unbuntu.com as 91.189.94.156, but not as ubuntu.com.

On the eth0 connection the default route and primary DNS are the same, 192.168.1.1 (the modem).  Qwest support can't help, but tell me that the DNS servers are 205.171.3.65 and 205.171.2.65.

Any network expertise would be greatly appreciated.

Since posting I connected my wife's Intrepid machine (almost identical) and it connected correctly.  It has exactly the same routing and dns as mine.

---

### Post by Bill Roberts on 2009-02-21
Shut down the machine to work a different problem with external USB devices and that fixed it.  I don't have any idea why.

---

### Post by Iowan on 2009-02-21
Da*ned USB devices... ;)

---

