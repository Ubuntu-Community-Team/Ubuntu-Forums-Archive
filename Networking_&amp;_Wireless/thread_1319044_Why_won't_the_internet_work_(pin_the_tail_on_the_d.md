---
title: "Why won't the internet work? (pin the tail on the donkey)"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by RabbitWho on 2009-11-08
Nice simple title, no?
I realise it's very unlikely anyone can help me because unfortunately I can give you almost no information. It's like pin the tail on the donkey because you can't see anything have no information and i'm hoping you'll be able to guess and magically arrive at an answer. 

I have ethernet cable coming from a flat upstairs. So I  have no access to the modem  or the internet company or anything nice like that that would help me give more information. 
I have dual booted Ubuntu 9.4 and Windows Vista to a Dell 1545 laptop
The internet always connects in Vista
The internet sometimes (rarely) connects in ubutntu and then it will randomly turn off and refuse to turn on again. 

Any common problems it could be?
No suggestion is to obvious or too unlikely a solution

Here are some things it says:
Connection information:

Ethernet (eth0) 
Hardware addres: blah blah blah
Driver: Sky2
Speed 100 Mb/s
Security: none


It's driving me crazy that half my life is in windows and half is in Ubuntu and i'm constantly restarting.. also i hate having to be so careful where I go and what I download because of all the damn viruses. Even open office had a trojan on it (or at least one was detected) and I had to download a Czech version from a Czech server instead, which was clean. And windows genneraly manages to piss me off every day. I almost wish I never got used to Ubuntu, i never knew how easy and good things could be. Save me from Windows. Save me. Please.

---

### Post by idef1x on 2009-11-08
You can try to set your ip-address to a fixed one?
You can take the information (ip,subnetmask,gateway,dns) from your vista settings and configure ubuntu likewise.

It could have something to do with the dhcp server. 

Or is your physical connection dropping in ubuntu?

---

### Post by RabbitWho on 2009-11-08
> **idef1x said:**
> You can try to set your ip-address to a fixed one?
You can take the information (ip,subnetmask,gateway,dns) from your vista settings and configure ubuntu likewise.

It could have something to do with the dhcp server. 

Or is your physical connection dropping in ubuntu?

The IP address appears to be static now I think, i will have  a look at the windows settings next time I restart, i'm afraid to now because it's the first time i've had the net running in ubuntu for ages!

---

### Post by chili555 on 2009-11-08
Please open a terminal and do:```
sudo rmmod -f sky2
sudo modprobe sky2 disable_msi=1
sudo ifconfig eth0 up
```Does it work as expected now? If so, we can make this permanent.

---

