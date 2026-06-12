---
title: "Can’t enable wireless NIC in BIOS, keeps being reset"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by kaimi&#326;iece on 2010-01-22
I have an Eee PC 701 4G, and some time ago I disabled its wireless NIC in the BIOS to save energy. Now I've come to need it working again, but I can't re-enable it, because it always goes back to being disabled after I boot the eeebuntu installed on the machine. If I just enable it in the BIOS, reboot and go into the BIOS setup again, it's still enabled, but if I let the OS load it'll get disabled. I'm really at a loss here, how do I find out what's wrong? Could it be Ubuntu that does this?

---

### Post by chili555 on 2010-01-22
If it's disabled in Ubuntu, it's probably because no driver has attached to the hardware and created an interface. Please let us see:```
sudo lshw -C network
```Thanks.

---

### Post by kaimi&#326;iece on 2010-01-22
Since it's disabled in BIOS, it doesn't appear in lshw.

---

### Post by chili555 on 2010-01-22
> If I just enable it in the BIOS, reboot and go into the BIOS setup again, it's still enabled, Then I'm not quite sure I understand. Are you saying that you enable it in the BIOS, boot to Ubuntu, don't see the wireless card at all in lshw or lspci and then reboot into the BIOS and it's disabled again?

---

