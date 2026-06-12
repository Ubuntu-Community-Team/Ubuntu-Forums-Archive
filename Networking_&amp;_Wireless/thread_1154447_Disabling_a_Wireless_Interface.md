---
title: "Disabling a Wireless Interface?"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by kmand on 2009-05-09
I have two wireless nics on a Ubuntu 9.10 laptop. A slow builtin and a fast usb. The network manager keeps trying to bring up both, but I only want it to bring up the external.

Is there a way to disable the internal?

---

### Post by chellrose on 2009-05-09
Look in /etc/udev/rules.d/70-persistent-net.rules (note: the "70" might be different on your machine) and see if you can figure out which is which.

If so, I think commenting out the one you don't want to use would be sufficient -- you might have to do that in /etc/network/interfaces as well, though.

---

### Post by pastalavista on 2009-05-09
You can also right-click the network manager icon in the tray (notifications area) and "Edit Connections" make the one you want to use "connect automatically" and disable that function in the other.

---

### Post by thesavager on 2009-05-09
You can disable the internal wireless network-card in your BIOS settings.

---

### Post by kmand on 2009-05-10
I went with "edit connections" in the network manager. I had missed that I could specifiy the Mac address of the interface. I was expecting to see an interface name and had thought the Mac qualified the access point.

---

### Post by Mortus Pryde on 2009-05-22
I have a similar situation with my T42, however in my case I want to use the wireless hotkey to disable the internal wireless, and past that would like the active/inactive state to persist between sessions and shutdowns. Is either yet possible? I should mention that I am using Intrepid.

I post these questions here as I believe they may be of interest to the OP as well.

---

