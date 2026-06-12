---
title: "Laptop as server"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by bobosity on 2010-03-01
Can I run a laptop as a wireless server?

My friend runs his laptop off of his cable box and does not have a multi-port router. How can I have his laptop wireless act as an access point?

If I can't be wireless, how do I have his laptop act as a server through a usb cable to my laptop?

Thanks...

---

### Post by cjhabs on 2010-03-01
Does this help?
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

### Post by bobosity on 2010-03-01
I think I could follow that on my machine but I need to get my friend to do this on his machine for when I visit.

I'm hoping for a package that needs minimal configuration to start. It's only going to run when I visit. If I could hook to his laptop through usb that would be cool but wireless would be better.

Anyone...?

---

### Post by bobosity on 2010-03-03
Bump bump bump BUMPETYBUMPBUMP

Well, let's recap.

My friend has no router and runs straight off his cable modem. I need a simple way to either turn his wireless into an access point or run a cable (ethernet or usb) from his laptop to mine.

A tag search for "access point" showed a number of people with the same question but no real resolution. 

The problem is ease of installation. If this was at my place I could experiment all day. To make this happen at my friends place I need to present him with a fairly simple package that he can just install and run. 

While security is always important, this program will only run when I'm there so I can use a lightweight solution that perhaps would not be suitable in another environment.

Has anybody done something similar?

---

### Post by cjhabs on 2010-03-03
> **bobosity said:**
> Bump bump bump BUMPETYBUMPBUMP

Well, let's recap.

My friend has no router and runs straight off his cable modem. I need a simple way to either turn his wireless into an access point or run a cable (ethernet or usb) from his laptop to mine.

A tag search for "access point" showed a number of people with the same question but no real resolution. 

The problem is ease of installation. If this was at my place I could experiment all day. To make this happen at my friends place I need to present him with a fairly simple package that he can just install and run. 

While security is always important, this program will only run when I'm there so I can use a lightweight solution that perhaps would not be suitable in another environment.

Has anybody done something similar?

If you want to connect the 2 machines together directly via a network cable, firstly one of the machines will need 2 network interfaces to allow internet access and local access simultaneously - secondly you'll need a crossover cable, rather than a standard network cable and finally you'll have to configure your machine with an ip address on his subnet and make sure he routes you to the cable modem.

---

### Post by bobosity on 2010-03-03
Thanks cjhabs. 

An ethernet cable connects the modem and his laptop and that is eth0. I guess I would want to connect through usb. How would I set up that?

---

### Post by spiky001 on 2010-03-03
If you are using the ethonet cable to the modem on laptop, you would need 2 ethonet connections on laptop i,m sure there is only1

---

### Post by Poltergiest on 2010-03-03
I have a laptop that has a wireless modem and desktop computer with a ethernet cable (CAT 5)  the wireless router in no where near my desktop I would like to connect my desktop to my Laptop so it can connect to the Internet. I think my problem is the same as the one your talking about. thanks for listing.

---

### Post by spiky001 on 2010-03-03
hi so you have the modem in the laptop so that is your internet connection, you then want to connect desktop to that?

---

### Post by cjhabs on 2010-03-03
> **bobosity said:**
> Thanks cjhabs. 

An ethernet cable connects the modem and his laptop and that is eth0. I guess I would want to connect through usb. How would I set up that?

Sorry - no idea if that is possible - hopefully someone else will chime in.

I would consider buying your friend a cheap router for their birthday :)

---

### Post by spiky001 on 2010-03-03
thats what i was going to suggest but wanted to know how it was all connected up

---

