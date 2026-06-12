---
title: "Atheros driver won't stay installed."
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by dai_vernon on 2008-12-29
I am using Intrepid on my laptop with the Atheros5007 wireless chipset.  I downloaded the latest madwifi drivers and compiled/installed them and everything worked fine.  I restart and it no longer works, but redoing the whole thing does.

How can I get the drivers to stay installed?

Here is what I did just to be clear

Downloaded the latest madwifi modules from [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Installed the necessary dependencies

Untarred and built the driver

Installed the driver

sudo modprobe ath_pci

Then all was good, until I restarted, and now it is completely gone - the wireless network doesn't show up in my network dropdown, just like before the drivers were installed.  I'd like to not have to recompile and reinstall the thing every time I boot.  How do I keep it loaded?

Thanks in advance.

---

### Post by kevdog on 2008-12-29
echo ath_pci | sudo tee -a /etc/modules

This will load the module at boot.

---

### Post by dai_vernon on 2008-12-30
Thanks - that did it.

---

