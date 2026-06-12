---
title: "UFW settings for home network"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by delboy1 on 2009-02-23
Being used to firewalls that autoconfigure for home networks I am struggling a bit with ufw (I thought the "u" stood for uncomplicated :D). I've never really understood all these port things.

I have managed to get my ubuntu Dell mini to see my windows network now and all is Ok until I turn on the firewall. What settings do I need to enter into the firewall (using gufw interface) to allow network traffic.

Cheers

---

### Post by delboy1 on 2009-03-01
Can anyone help me with this? I still can't find how to set the firewall to allow network traffic. As soon as I turn it on it blocks the network but as I use the netbook in wifi spots / 3G etc I would feel safer with a firewall on.

My network IP addresses are all between 192.168.2.1 and 192.168.2.255 so I tried allowing 192.168.2.1/255 to 192.168.2.1/255 but that just reports an error

---

### Post by ibutho on 2009-03-01
> I have managed to get my ubuntu Dell mini to see my windows network now and all is Ok until I turn on the firewall. What settings do I need to enter into the firewall (using gufw interface) to allow network traffic.
It depends what the network traffic is. Are you using SAMBA to share files with Windows? If so, you need to open UDP ports 137 and 138 as well as TCP ports 139 and 445.

---

### Post by delboy1 on 2009-03-01
Thanks for that.

I really don't understand ports etc and firewall settings. All the firewalls I have used before in windows auto detect the home network.

---

