---
title: "go back to open source driver after activating proprietary one?"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by sovietdoughnut on 2009-03-15
I installed the prop. driver for my wireless card through the restricted drivers manager and I wasn't pleased with its functionality. Now I want to go back to the open source driver. I deactivated the prop. one through the restricted drivers manager, but ubuntu did not automatically load the other module. Help please. Thanks.

my wireless card is a broadcom BCM4312

---

### Post by kevdog on 2009-03-15
Can you be specific in what driver you want to use by name, and by giving lshw -C network along with lspci -nnm?

---

### Post by sovietdoughnut on 2009-03-15
I figured it out. I booted the live cd to see what module it loaded for my hardware. It loaded the module "wl". So I just added that to my /etc/modules file ;)

---

