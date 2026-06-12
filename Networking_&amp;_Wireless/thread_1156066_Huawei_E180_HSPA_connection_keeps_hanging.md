---
title: "Huawei E180 HSPA connection keeps hanging"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by Arador Aristata on 2009-05-11
Hi everyone

I have been scouring around for other people that have this same problem,if only to find some way to diagnose the issue.

I am running Jaunty 32 bit and have a HUAWEI E180 USB modem that I use on MTN South Africa for connectivity.

The modem was automatically picked up and installed when i plugged it in and setting up the connection was simple enough. I can connect with it and achive the speeds I expect from it but I do have one issue.

Every now and the, some days more often than other, the connection becomes dormant. It doesnt say disconnected but no traffic flows through and the only way to get it to work again is be reconnecting. I should also note that when I disconnect, it takes about 3 attempts before it will reconnect again.

Weak signal is not the issue as I hover between strong 3G and weak HSPA signal. I thought it may be the Provider but it runs fine under Windows XP when controlled by their software.

Can anyone give me an idea of how to address this or even how to just pinpoint the problem, please?

I had one hunch that it might be the switching between 3G and HSPA that confuses Ubuntu or the modem under Ubuntu but I have no idea how I would establish this.

---

### Post by Arador Aristata on 2009-05-12
Good morning again. Anyone know what this could be? Please even just an idea to put me on the right track would be appreciated.

Thank you Kindly

---

### Post by Arador Aristata on 2009-05-13
I have been looking through Syslog to see if I can find any indication fo what happens but nothing. From the connection working to going dormant, no logs are updated, nothing that I can find actually happens.

I am pretty sure it has to do with the switching between 3G and HSPA. Is there any way in Ubuntu to force it to stick to one level?

---

### Post by Arador Aristata on 2009-05-13
Hi again

I am truly sorry if I am a bother but I am truly stuck here with no luck :(

I have been looking at the MTU settings and tried forcing it to other values like 1292 but this does not seem to solve the problem. I can see in Windows using Huawei software that the signal jumps between WCDMA and HSPA.

I have updated the firmware to the newest version and looked at logs to see anything but all I see is the successful connection establishment.

I have browsed the net with about half my cap, reconnecting all the time but I can not track down a way to limit it to WCDMA in Linux.

Please, please is there anyone that can help me. I dont want to switch to Windows again. :cry:

---

### Post by GeorgeVita on 2009-05-13
Hi **Arador Aristata**,
can you do some basic tests to get more technical info:

- From terminal: **lsusb** (to see the productID)
- boot without modem, wait for the system to stabilize, attach the modem, after some seconds from terminal: **dmesg** (to see the drivers/ports that used/created)
> when I disconnect, it takes about 3 attempts before it will reconnect again.
How the above is happening? (Network manager icon spins with grey circles instead of green?)

Have you tried other version of Ubuntu (like 8.10)?

At this time, do not fear about the 3G/HSPA switching or the firmware as it works with windows.

EDIT: another question: this modem works with windows on the same PC (same h/w)?

Regards,
George

---

### Post by Arador Aristata on 2009-05-14
Hi GeorgeVita

Thank you very much for the assistance.

I have tried lsusb and it picks it up fine. Dmesg shows the port creation and that all seems to be in order.

That reconnection problem does exactly as you say. It spins with grey dots instead of lights and in the syslog I can see two failures (will post them when I am back at my PC)

I have not tried it with 8.10, no.

The Windows instance is on the same PC with dualboot yes.

---

### Post by userid on 2009-09-08
Not sure if you're sitll onto this, installing the packages from [https://forge.betavine.net/frs/?group_id=12&release_id=9](https://forge.betavine.net/frs/?group_id=12&release_id=9) helped..

---

