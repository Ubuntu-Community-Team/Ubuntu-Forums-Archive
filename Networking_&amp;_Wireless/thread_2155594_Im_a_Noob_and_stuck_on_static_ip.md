---
title: "Im a Noob and stuck on static ip"
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by thopper on 2013-06-18
Im stuck with a static ip problem, I have to use linux and learn it but I have to get this to work due to needing it for my job.
I use moto cambium radios that default to 169.254.1.1
I can use ifconfig to set it static temporary but what i need is this.

a 169.254.1.101 255.255.0.0 169.254.0.0 while im connecting and configuring a wireless radio before i have internet access.
once i have internet access, i need it to just acquire a public DHCP address from our server and still be able to get to the 169.254.1 subnet to continue configuring the radio.

is there any way to do this.
Thanks for any help
thopper

---

### Post by Vitsliputsli on 2013-06-19
169.254.0.0 - 169.254.255.255 is autoconfigure addresses without dhcp. Maybe it's normal for cambium, because it use ptp, I don't know.
Probably you should search answer on [http://forum.cambiumnetworks.com]("http://forum.cambiumnetworks.com/").

---

### Post by redmk2 on 2013-06-19
> **thopper said:**
> Im stuck with a static ip problem, I have to use linux and learn it but I have to get this to work due to needing it for my job.
I use moto cambium radios that default to 169.254.1.1
I can use ifconfig to set it static temporary but what i need is this.

If there is **no DHCP server** on the network the interface should auto configure the interface via Avahi.  This feature is installed by default in Ubuntu.
> 

a 169.254.1.101 255.255.0.0 169.254.0.0 while im connecting and configuring a wireless radio before i have internet access.
once i have internet access, i need it to just acquire a public DHCP address from our server and still be able to get to the 169.254.1 subnet to continue configuring the radio.

is there any way to do this.
Thanks for any help
thopper

I don't think you can do what you want to do.  An IP address in the 169.254.0.0/16 network is not usable outside of the local subnet.  You probably need to have a 2nd NIC that is isolated from the network DHCP server.   With no network services it will auto configure with a 169.254.0.0/16 network address.  If you need a specific address in that network then you will need to manually configure that using ifconfig or directly at the ***/etc/network/interfaces*** file.

---

### Post by thopper on 2013-06-19
ok thanks , i will see what i can do

---

