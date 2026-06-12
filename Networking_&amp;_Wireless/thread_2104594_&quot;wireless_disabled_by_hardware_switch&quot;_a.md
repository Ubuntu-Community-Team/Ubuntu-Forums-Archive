---
title: "&quot;wireless disabled by hardware switch&quot; after suspend"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by fahadayaz on 2013-01-13
Hi all! :)

I have recently purchased a Novatech nFinity N1410 laptop and am having problems with the wireless, which *sudo lshw -C network* tells me is Centrino Wireless-N 2230 and using the *iwlwifi* driver.

The problem is that after the device has been suspended, I am not able to get the wireless working again without a restart. The network indicator states that the *wireless disabled by hardware switch*.

Though Fn +F2 is meant to be the wireless switch, xev tells me that the system doesn't see it as anything at all when I press this hardware combination. Also, though the brightness up/down buttons work fine, the volume up/down buttons do not work either.

What can I do to fix this? I am running Ubuntu 12.10 with all available updates installed.

---

### Post by bronkeydain on 2013-01-14
I remember on my Samsung netbook I could download some utilities to control Bluetooth and wifi settings from command line... Did you check if your machine's manufacturer has similar tools on their website?

Does your wireless come back after restarting the network service?
```
sudo service networking restart
```

---

### Post by fahadayaz on 2013-01-14
There's no utilities that they offer, that I'm aware of.

Alas, that command just makes Unity crash and a single press of the power button makes the machine shut down or restart (can't remember which one, now).

Any other ideas?

---

### Post by tgalati4 on 2013-01-14
Check the BIOS.  On my Dell laptop, I have the choice of FN-FN2 or "Application" or Both for control of wireless.  Also make sure that the default setting for wireless is "ON".

It could also be a bug in the ACPI implementation, which would require flashing a newer version of the BIOS to your notebook.  Check the manufacturer's helpful website.

---

