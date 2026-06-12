---
title: "Convoluted eth0 connection"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by S.R on 2011-06-27
Having a total brain lock here. I have recently had a problem away from the house with a wired connection. I am able to replicate this problem by plugging directly to my cable modem. 

With the router receiving from the modem the wired connection works fine. Unplug the router and plug directly to the cable modem I get wired disconnect.

Tried using Win7, 9.04, 10.10 and 11.04 all with the same result. I even did a clean install of 11.04. So a very generic problem that seems to be hardware related but I have run out of ideas. Maybe some back and forth would get the proverbial juices flowing.

And before someone ask .... yes ... a wireless connection works fine and ... yes ... a wired connection through the router works fine.

Thanks for any help in advance...

---

### Post by Dangertux on 2011-06-28
> **S.R said:**
> Having a total brain lock here. I have recently had a problem away from the house with a wired connection. I am able to replicate this problem by plugging directly to my cable modem. 

With the router receiving from the modem the wired connection works fine. Unplug the router and plug directly to the cable modem I get wired disconnect.

Tried using Win7, 9.04, 10.10 and 11.04 all with the same result. I even did a clean install of 11.04. So a very generic problem that seems to be hardware related but I have run out of ideas. Maybe some back and forth would get the proverbial juices flowing.

And before someone ask .... yes ... a wireless connection works fine and ... yes ... a wired connection through the router works fine.

Thanks for any help in advance...

Is your modem expecting to authenticate your router's mac address, as opposed to your pc's?

---

### Post by S.R on 2011-06-28
No the modem is not looking for any specific MAC. Seems like it is unable to resolve the DHCP from what I can tell.

---

### Post by Dangertux on 2011-06-28
Ok -- so you know if you connect the router to the modem it gives it an IP address via DHCP.  If you connect the PC to the modem it does not give it an IP address via DHCP.

We know it is operating system independent (as you have tried multiple OS'es)

The modem doesn't change , so the problem isn't there
The Operating system does change , so the problem isn't there
The only thing I see changing is the MAC address...

I think you should test this, set your router to spoof your eth0 mac address , see if it receives an IP from dhcp, if it does not , you know it was a MAC issue.

Alternatively it could be assigning DHCP addresses based on host name.

Cable ISP's are famous for this.

---

### Post by S.R on 2011-07-14
Problem solved ... ifconfig eth0 down then ifconfig eth0 up

By the way thanks Dangertux you walked me down a good path.

---

