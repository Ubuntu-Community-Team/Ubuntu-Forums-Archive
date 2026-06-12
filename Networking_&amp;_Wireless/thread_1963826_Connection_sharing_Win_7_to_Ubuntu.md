---
title: "Connection sharing: Win 7 to Ubuntu"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by qianian on 2012-04-23
I have an Acer Aspire 4720Z running Windows 7 that successfully connects to the internet using a Venus USB Broadband modem (CDMA3G 1X-EVDO) that is plugged directly into the machine. 

I have a separate laptop, Lenovo Thinkpad R61i, running Ubuntu 11.10. When I plugged the modem into the Ubuntu laptop, Network Manager and gnome-ppp didn't recognize the modem, so I cannot connect directly on the Ubuntu computer. 

I have a LAN cable but the wired connection didn't work even though LEDs are blinking. I've connected automatically in this way to a Windows Visa laptop plugged into a different model modem before.

What is the best way to connect both computers to the internet using the Venus USB Broadband modem? And how do I achieve that? 

Please be give step-by-step instructions, I'm a relative newbie.

---

### Post by sanderj on 2012-04-23
The "Venus USB Broadband modem (CDMA3G 1X-EVDO)" is a USB-cellular-stick? No ethernet-connection on it?

If so, I can think of the following options:

Put the USB-stick in the Windows computer, setup Internet Connection Sharing on that Windows computer. Then connect both the Windows-computer and the Ubuntu computer to a switch. I expect it to work then. Attention: the Windows computer should be on when the Ubuntu computers needs Internet

Or: buy a router that can use the 3G usb device as gateway. Connect both computers to the router (wired or wireless).

---

### Post by qianian on 2012-04-24
Thanks for the response. Is there a typo in the "to a switch" line? I didn't grock that.

---

### Post by sanderj on 2012-04-24
> **qianian said:**
> Thanks for the response. Is there a typo in the "to a switch" line? I didn't grock that.

Changed that line a bit ...

---

### Post by qianian on 2012-04-25
Ack. Don't know where to look for hardware like that in rural Indonesia. Thanks anyway.

---

### Post by SeijiSensei on 2012-04-25
Maybe you can find what's called a "crossover" Ethernet cable.  You can't use a normal Ethernet cable to network two machines together, because the "transmit" pair of wires on one machine will be connected to the transmit pair on the other machine.  A crossover cable connects the transmit pair on one end to the receive pair on the other and vice versa.

If you're good with your hands, you can try to [build your own]("http://www.makeitsimple.com/modules.php?name=Content&pa=showpage&pid=8&page=1") crossover cable.

---

### Post by qianian on 2012-04-26
Interesting point. The cable I'm using was hand-made specifically for connecting my Linux machine to a Windows one. I successfully used it before switching to this Win7 machine. That is why I don't believe the cable is the problem.

---

### Post by SeijiSensei on 2012-04-26
Maybe it's an issue with the Windows 7 firewall blocking access from the Ubuntu machine since it appears to have happened when you switched from Vista to Win7.  Try browsing Windows support forums to see what problems people have reported with Internet Connection Sharing in Windows 7.

---

