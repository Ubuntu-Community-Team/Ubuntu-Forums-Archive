---
title: "Asterisk Build, network dies in 9.10"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by mr-nick on 2010-05-10
Hi everyone,

I have looked over existing threads and can't seem to find a solution to this issue.
I've just recently finished a second asterisk + freepbx build on a Revo N330.

This setup (the first one) was working perfect for a few weeks until I plugged it into a Zyxell managed 100mbs switch (into one of the uplink ports)

When the device was originally working it was just plugged straight into a regular switch connected to the router. 

The problem specifically causes all phones on the network to fail at registration.
Internet access stops working also.
The machine was and still has a static IP, dns servers I believe are still setup correctly in resolv.conf.
What I discovered is that if I edit /etc/network/ifconfig and change the static entry to dhcp and then /init.d/network restart, then change back to static and repeat, all phones come back online.  This fixes the phone network but still leaves the internet down!!
I've been pulling my hair out over this and can't figure out what can be causing this.
Again the only difference that I can think is plugging it into this managed switch has some how toggled a setting!
ufw is off, rebooting the machine makes no difference and network devices are unable to connect until I carry out the above process.

Sorry for the lack of information, if I can add anything please let me know.

Thanks in advance.

Nick

---

