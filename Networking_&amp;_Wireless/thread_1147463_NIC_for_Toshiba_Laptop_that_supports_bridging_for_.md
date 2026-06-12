---
title: "NIC for Toshiba Laptop that supports bridging for VM's?"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by hamannp on 2009-05-03
Can anyone tell me the brand and model of a wired ethernet NIC that I can plug into my Toshiba laptop [with the Intel core-duo] that is well liked by Ubuntu AND with a driver that supports network bridging for my KVM guests?

Thank you,
Paul

---

### Post by DGortze380 on 2009-05-03
> **hamannp said:**
> Can anyone tell me the brand and model of a wired ethernet NIC that I can plug into my Toshiba laptop [with the Intel core-duo] that is well liked by Ubuntu AND with a driver that supports network bridging for my KVM guests?

Thank you,
Paul

I'm a little confused what you're asking.

First, the vast majority of Ethernet NICs are supported, especially if your laptop is new enough to have  Core 2 Duo. What's wrong with the NIC that came with the laptop?

Second, VirtualBox will Bridge your card with the Virtual NIC automatically in host-interface mode.

Last, what do you mean by a KVM Guest?? Typo?

---

### Post by hamannp on 2009-05-04
Thanks for responding. Sorry, I was trying to be brief.

The net of it is I got a pretty muscular laptop and I want to run demos locally on it.  I'm integrating oss business software.  I use vm-builder and virt-manager to build development machines (and blow them up over and over).  I've got a muscular desktop machine where it works flawlessly with a bridge network.  

On my laptop, it's been a LIVING HELL to setup a proper bridge network. We're talking 17 second page loads.  Thats for a clone where I change the appropriate network settings and copy from one machine to the other.   Wireshark didn't see any traffic on the ethernet card. I came to the conclusion that the sky2 driver for the Marvell YUKON wired ethernet card must lack support for bridging.   

I have a long and sad tail of woe. If you really want to rehash the sordid affair........

[http://ubuntuforums.org/showthread.php?t=1140713](http://ubuntuforums.org/showthread.php?t=1140713)

Thanks again for the response.

Cheers! Paul

---

### Post by DGortze380 on 2009-05-04
> **hamannp said:**
> Thanks for responding. Sorry, I was trying to be brief.

The net of it is I got a pretty muscular laptop and I want to run demos locally on it.  I'm integrating oss business software.  I use vm-builder and virt-manager to build development machines (and blow them up over and over).  I've got a muscular desktop machine where it works flawlessly with a bridge network.  

On my laptop, it's been a LIVING HELL to setup a proper bridge network. We're talking 17 second page loads.  Thats for a clone where I change the appropriate network settings and copy from one machine to the other.   Wireshark didn't see any traffic on the ethernet card. I came to the conclusion that the sky2 driver for the Marvell YUKON wired ethernet card must lack support for bridging.   

I have a long and sad tail of woe. If you really want to rehash the sordid affair........

[http://ubuntuforums.org/showthread.php?t=1140713](http://ubuntuforums.org/showthread.php?t=1140713)

Thanks again for the response.

Cheers! Paul

Well, if you're already certain that's the issue, I unfortunately have no advice. Good Luck.

I will suggest maybe you try running the VMs in some different Virtualization Software, if for no other reason than to rule out the software as a problem.

---

### Post by hamannp on 2009-05-04
> **DGortze380 said:**
> Well, if you're already certain that's the issue, I unfortunately have no advice. Good Luck.

I will suggest maybe you try running the VMs in some different Virtualization Software, if for no other reason than to rule out the software as a problem.

Thanks again for the reply.  It's really an economics question at this point.  Time is money.  All else equal, I'm hoping to find someone who has done something similar.  Maybe I got lucky.

[http://www.uluga.ubuntuforums.org/showthread.php?t=1144139](http://www.uluga.ubuntuforums.org/showthread.php?t=1144139)

Regards,
Paul

---

