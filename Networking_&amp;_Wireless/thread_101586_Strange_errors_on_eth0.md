---
title: "Strange errors on eth0"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by ProN00b on 2005-12-10
Since two days i am getting those errors, not all the time but quite alot, it has never happened bevore, i don't know what i could have changed to have caused this, because the only thing i did to my computer was a "apt-get update:apt-get upgrade" and i didn't change any equipment.
I am connected to the internet with pppoe over eth0.
Does anyone know what they mean, and maybe how i can fix it ?
(asking here is really my last resort, i have googled for the errors and failed to use the forum search here :( )

```
Dec 10 07:12:02 localhost kernel: [4319467.035000] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x13e7ba status 1fa541a0!
Dec 10 07:12:17 localhost kernel: [4319481.825000] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x13e7bb status a00e6a9!
Dec 10 07:12:17 localhost kernel: [4319481.825000] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x13e7bc status 0000!
Dec 10 07:12:17 localhost kernel: [4319481.825000] eth0: Oversized Ethernet frame spanned multiple buffers, entry 0x13e7bd status 0000!
Dec 10 07:14:17 localhost pppd[7544]: No response to 4 echo-requests
Dec 10 07:14:17 localhost pppd[7544]: Serial link appears to be disconnected.
Dec 10 07:14:17 localhost pppd[7544]: Connect time 413.6 minutes.
Dec 10 07:14:17 localhost pppd[7544]: Sent 42188676 bytes, received 1577485682 bytes.
Dec 10 07:14:17 localhost pppd[7544]: Couldn't increase MTU to 1500
Dec 10 07:14:17 localhost pppd[7544]: Couldn't increase MRU to 1500
Dec 10 07:14:23 localhost pppd[7544]: Connection terminated.
Dec 10 07:14:23 localhost pppd[7544]: Modem hangup
Dec 10 07:15:28 localhost pppd[7544]: Timeout waiting for PADO packets
Dec 10 07:16:33 localhost pppd[7544]: Timeout waiting for PADO packets
Dec 10 07:17:38 localhost pppd[7544]: Timeout waiting for PADO packets
Dec 10 07:18:43 localhost pppd[7544]: Timeout waiting for PADO packets
Dec 10 07:19:48 localhost pppd[7544]: Timeout waiting for PADO packets
Dec 10 07:20:53 localhost pppd[7544]: Timeout waiting for PADO packets
Dec 10 07:21:23 localhost kernel: [4320028.520000] eth0: Too much work at interrupt, status=0x3c48080.
Dec 10 07:21:23 localhost kernel: [4320028.521000] eth0: Too much work at interrupt, status=0x3c48080.
Dec 10 07:21:23 localhost kernel: [4320028.521000] eth0: Too much work at interrupt, status=0x3c48080.
[...Alot of those Messages...]
Dec 10 07:21:23 localhost kernel: [4320028.581000] eth0: Too much work at interrupt, status=0x3c48080.
Dec 10 07:21:23 localhost last message repeated 2 times
Dec 10 07:21:23 localhost kernel: [4320028.582000] eth0: Too much work at interrupt, status=0x3c48080.
[...Alot of those Messages...]
Dec 10 07:21:23 localhost kernel: [4320028.584000] eth0: Too much work at interrupt, status=0x3c48080.
[...Alot of those Messages...]
Dec 10 07:21:23 localhost kernel: [4320028.727000] eth0: Too much work at interrupt, status=0x3c48080.
Dec 10 07:21:23 localhost last message repeated 2 times
Dec 10 07:21:23 localhost kernel: [4320028.728000] eth0: Too much work at interrupt, status=0x3c48080.
[...Alot of those Messages...]
Dec 10 07:21:24 localhost kernel: [4320028.792000] eth0: Too much work at interrupt, status=0x3c48080.
Dec 10 07:21:58 localhost pppd[7544]: Timeout waiting for PADO packets
Dec 10 07:23:03 localhost pppd[7544]: Timeout waiting for PADO packets
Dec 10 07:24:08 localhost pppd[7544]: Timeout waiting for PADO packets
Dec 10 07:24:56 localhost kernel: [4320241.015000] NETDEV WATCHDOG: eth0: transmit timed out
Dec 10 07:24:56 localhost kernel: [4320241.015000] eth0: Transmit timed out, status 03ca0084, resetting...
Dec 10 07:24:56 localhost kernel: [4320241.015000] eth0: Setting 100MBit-full-duplex based on MII#1
Dec 10 07:25:13 localhost pppd[7544]: Timeout waiting for PADO packets
Dec 10 07:25:13 localhost pppd[7544]: Exit.
```

---

### Post by mips on 2005-12-10
You have an ethernet connection, why not rather let your router handle the PPPoE stuff ?

Giant frames are not uncommon. I dont know about the rest of the errors though.

---

### Post by ProN00b on 2005-12-10
its not a router, its an adsl modem, i got a ethernet connection to it and can dial up to my provider over that ethernet connection, thats why its called pppoe (ppp over ethernet), its not a router, and i don't want a router because it doesn't give you the Direct Connection (tm) to the internet feeling, this setup gives me.

---

