---
title: "Static IP using 3G+ stick"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by Raf3600 on 2011-08-02
Hello i'm using a 3G+ stick, by Sfr in France.

Is it possible to get a static local ip address ?

I wasnt able to find the answer with google. Thank you

---

### Post by CyberPingU on 2011-08-02
If it's a stick it doesn't matter: all you have is a "modem", so you will get on that device the IP that the provider gives you.
All you can do, if (depending on the device) a bridge with a local eth0 or you can use an alias for the device. Doubt you can acheive this with a stick though.

---

### Post by Raf3600 on 2011-08-02
Sorry I was talking about the local ip address.

For apache I would like to have 192.168.1.2 assigned to my server ( ubuntu 04/11 )

---

### Post by spiky001 on 2011-08-02
I use a 3G usb on my server, I have not added a static ip for local but it alawys gets 10.42.43.1. Here is how to set a static ip [LINK]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/")
Hope this helps

---

