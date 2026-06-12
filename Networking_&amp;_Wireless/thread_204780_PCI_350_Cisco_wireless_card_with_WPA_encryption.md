---
title: "PCI 350 Cisco wireless card with WPA encryption?"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by cogitordi on 2006-06-27
I have spent days researching and trying to get the PCI 350 Cisco wireless card in my ThinkPad T40 working with WPA encryption. This is not necessarily an Ubuntu-specific problem... it's just that I like Ubuntu and I want it to work in Ubuntu. :^)

I've read all the posts that I could find. I've Googled until I can Google no more. I've tried downgrading the firmware in the card to 4.25.30 but the firmware won't "take". (I see a "bad firmware" message from the Cisco ACU in M-Windows.)

Has anyone in the history of humanity ever got the PCI 350 Cisco wireless card working in a Linux distribution with WPA encryption? ](*,)

---

### Post by cogitordi on 2006-06-27
By the way, the PCI 350 works fine in M-Windows.

---

### Post by cogitordi on 2006-08-08
After trying NDISWrapper and the Linuxant driver without success ("hours of frustration"), I replaced the Cisco Mini PCI 35O with the Intel 2100 3B. I installed Network-Manager-Gnome, rebooted, and... had SUCCESS. The WPA encrypted connection is working. :D 

If you own a ThinkPad with the Cisco Mini PCI 350, I recommend this solution.

---

### Post by prasannakm on 2006-12-16
> **cogitordi said:**
> I have spent days researching and trying to get the PCI 350 Cisco wireless card in my ThinkPad T40 working with WPA encryption. This is not necessarily an Ubuntu-specific problem... it's just that I like Ubuntu and I want it to work in Ubuntu. :^)

I've read all the posts that I could find. I've Googled until I can Google no more. I've tried downgrading the firmware in the card to 4.25.30 but the firmware won't "take". (I see a "bad firmware" message from the Cisco ACU in M-Windows.)

Has anyone in the history of humanity ever got the PCI 350 Cisco wireless card working in a Linux distribution with WPA encryption? ](*,)

>>
Hi,
Did you get this working? 
I want to get WPA working with my cisco 350 series card which makes use of aironet driver code on linux.

Thanks & regards 
Prasanna

---

### Post by wieman01 on 2006-12-16
Please try [this]("http://www.ubuntuforums.org/showthread.php?t=202834"). WPA should definitely work. Try WPA1 first.

---

### Post by cogitordi on 2006-12-19
> **prasannakm said:**
> >>
Hi,
Did you get this working?

I never did get it working. I ended up yanking the card and installing an Intel card.

---

