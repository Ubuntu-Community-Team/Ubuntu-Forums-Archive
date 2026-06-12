---
title: "How to connect automatically to hidden ssid?"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by lduperval on 2009-08-08
I have a Broadcom wireless card on an AMD64 system. Everything works fine except that whenever I reboot or unsuspend my system, I have to connect manually using the Network Manager and selecting a hidden network (identified as "auto my network"). How can I configure it so it picks up thhat one automatically, amongt the many that are listed? I.e. I don't want to have to do an extra manual step to connect.

Thanks,

L

---

### Post by Metaljaz on 2009-08-09
For me I had to turn off auto login. I have to type name and password whenever I turn on the computer or reboot but i connect automatically without having to re-enter any wireless info.
System > Administration > Login Window > Security and check to make sure that enable automatic login is not checked

I hope thats what you were looking for

---

### Post by Metaljaz on 2009-08-11
You can also try right clicking on the network icon in the top right hand corner. Select edit connections. Select the wireless tab and then select the wireless network you are trying to connect to. Select edit and then click connect automatically at the top. 
I think this is more of what you were looking for.

---

### Post by gub1 on 2009-08-12
same problem here, broadcom nic using ndiswrapper connects fine 

but after selecting automatically connect, (currently using wicd, but tried with network manager too), after every login, whether autologin is selected or not, I have to manually enter hidden ssid and connect

---

