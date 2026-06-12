---
title: "madwifi and broadcom"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by kr651129 on 2010-07-10
Has anyone successfully installed madwifi drivers for the broadcom chipset?  And if so how.

I'm having speed problems with my bcm43xx on Ubuntu 10.04.

---

### Post by bkratz on 2010-07-10
> **kr651129 said:**
> Has anyone successfully installed madwifi drivers for the broadcom chipset?  And if so how.

I'm having speed problems with my bcm43xx on Ubuntu 10.04.



A bit confused-- from this page

[http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)

It says:

Multiband Atheros Driver for WiFi (MADWIFI): Linux driver [COLOR="Red"]for 802.11a/b/g Cardbus/PCI/MiniPCI cards using Atheros chipsets[/COLOR]. *** Attention: homepage moved to [http://madwifi-project.org](http://madwifi-project.org) - files from sf.net CVS deprecated! ***

Why would you try these with a Broadcom device--they are for Atheros chipsets?

---

### Post by kr651129 on 2010-07-11
I can't find the link but I read a post somewhere that someone got the madwifi working with the broadcom chip.

I installed ndiswrapper -  the gtk version

Then installed the xp driver, black listed everything I needed to and added nidswrapper to the start up and my wifi looks like its not turned on.

Any ideas?

---

