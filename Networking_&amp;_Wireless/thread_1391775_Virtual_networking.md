---
title: "Virtual networking"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by novice buntu on 2010-01-27
Hi,

There seems to be a lot written about virtual networking but I am not sure what approach to take in my situation.

My local subnet has a public block of 128 addresses. I have a virtual host running on my machine. My machine has a static address and I'd need to assign one to the guest. I have edited the guest's interface file and assigned a public address to it's eth0. However the guest cannot ping out and I can't ping in.

By default the virtual machine manager creates a virtual network (virbr0) and assigned a private address range to it. I have tried to create a new virtual network using a subnet of my public range (/31) but the manager says the range must to a minimum of 16 addresses (/4). It doesn't look possible to achieve my aims using the virtual machine manager.

In the past I have used the procedure laid out here:
[https://help.ubuntu.com/8.04/serverguide/C/libvirt.html]("https://help.ubuntu.com/8.04/serverguide/C/libvirt.html")

which is to manually create a bridge. I am not sure that is relevant for my 9.10. I think I would have to disable the network manager if I were to do that and I am not sure how to do that. 

Can anyone give me some pointer on how I can or should proceed? 
Thanks,
Dp.

---

### Post by novice buntu on 2010-01-27
I think the answer to my problem might be here.

[http://libvirt.org/formatdomain.html#elementsNICSBridge]("http://libvirt.org/formatdomain.html#elementsNICSBridge")

---

