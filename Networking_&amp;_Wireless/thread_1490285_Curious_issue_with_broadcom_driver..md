---
title: "Curious issue with broadcom driver."
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by cespinal on 2010-05-22
Hello to all, 

I know there has been countless threads about wireless and broadcom drivers. But I have not seen any that talks about what I am experiencing. 

On one out of, lets say, 10 system boots, the wireless driver just won't load. I easily work around this by reinstalling the dirver after login. but this was obviously not happening in Karmic. 

Any hints at all? 

Cheers and thanks for your patience. :)

---

### Post by chili555 on 2010-05-22
It happens. Drivers failing to load once in a while is not confined to Broadcom. I don't know why. It can be easily fixed. Open a terminal and do:```
sudo su
echo b43 >> /etc/modules
exit
```Substitute your driver if it's not b43. The driver you added to */etc/modules* will load on boot from now on.

---

### Post by cespinal on 2010-05-22
Thanks for the reply man, 

However, applied the commands and I think I accidentally the whole thing lol. 

Dont know what went wrong, but now everytime I reboot I need to reinstall the driver in order to regain wireless support. In other words, the system is not loading the driver on boot, I guess. 

Halp? :(

---

### Post by chili555 on 2010-05-22
> I think I accidentally the whole thing lol.What driver is your Broadcom using?```
sudo lshw -C network
```Here is an example from mine:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       --- snip ---
       configuration: broadcast=yes driver=[COLOR="Red"]iwl3945[/COLOR] Is the driver you found the driver you entered in */etc/modules*? If not, edit and correct:```
sudo gedit /etc/modules
```Add the driver you need and remove the incorrect one, b43, perhaps. Proofread, save and close gedit.

Remember what I said?> Substitute your driver if it's not b43. 

---

### Post by Bucky Ball on 2010-05-22
.

in error ...

---

### Post by cespinal on 2010-05-22
here: 

```
description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 ip=10.
```

So Im updating the file changing b43 for wl1. 

I'll reboot and try it back. 

I dont know, but I was almost sure I was using b43 :S sorry for that... 

brb

---

### Post by cespinal on 2010-05-22
What's that bucky? I didn't understand what you just said.

---

### Post by cespinal on 2010-05-22
> **cespinal said:**
> here: 

```
description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 ip=10.
```

So Im updating the file changing b43 for wl1. 

I'll reboot and try it back. 

I dont know, but I was almost sure I was using b43 :S sorry for that... 

brb

Nothing... had to reinstall the driver upon login. here is a screenshot of the whole thing.

---

### Post by cespinal on 2010-05-22
Solved! :D 

sudo lshw -C network was giving me the wrong driver. Here is what I did. 

1) Erased every input on /etc/modules. Then reboot
2) Wireless loaded as it normally does. 
3) entered sudo lshw -C network on terminal again to see if it gave a different dirver, which did. 
4) updated /etc/modules with it. and viola. 

NOW...on one of these reboots the nvidia drivers also failed to load (which also happens from time to time). So the question is, how to I detectt that driver in order to add it to /etc/modules as well? Does it work the same way it worked with the broadcom driver? 

Thank you very much again for your patience. I know this sort of things can be sorted out with help from you.

---

### Post by chili555 on 2010-05-22
> Does it work the same way it worked with the broadcom driver?
Probably:```
$ sudo lshw -C [COLOR="Red"]display[/COLOR]
[sudo] password for chili: 
    *-display               
       description: VGA compatible controller
       product: NV25 [GeForce4 Ti 4200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list rom
       configuration: [COLOR="Red"]driver=nvidia[/COLOR] latency=248 maxlatency=1 mingnt=5
       resources: irq:16   

```Substitute your driver if it's not nvidia. I know, what an old, obsolete card!

---

### Post by cespinal on 2010-05-22
Great :) I'll give it a try.

---

