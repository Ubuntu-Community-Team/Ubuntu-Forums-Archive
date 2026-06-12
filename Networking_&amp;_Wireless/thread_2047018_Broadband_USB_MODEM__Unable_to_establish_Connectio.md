---
title: "Broadband USB MODEM : Unable to establish Connection"
date: 2012-08-24
forum: Networking &amp; Wireless
---

### Post by fantab on 2012-08-24
I have a **ZTE-AC2726 Broadband USB MODEM** and I am having a **problem connecting**.

It used to work perfectly well with Previous versions of Ubuntu but not with 12.04, which I am currently using. 

I need help is establishing connection and I don't know where to start looking. _Network-Manager_, _Modemmanager_ and _usb_modeswitch_ are all in place.  Network manager detects my said device as modem... so I really don't know nor have any idea where to look.

I suspected that It could be ufw and tried to connect disabling ufw... it didn't help though.

Any pointers to help me troubleshoot this issue are most welcome.

Thanks...

---

### Post by jorok_tupur on 2012-09-10
Can you describe what you mean with "having a problem connecting"?

Did the connection simply got disconnected randomly, or no connection at all?
Maybe the ModemManager crashed while trying to establish the connection?
Did the modem get switched at all?

How do you know that the problem does not lies in NetworkManager, ModemManager, or usb_modeswitch?

Maybe you can post the portion of /var/log/syslog that describes the problem?

---

