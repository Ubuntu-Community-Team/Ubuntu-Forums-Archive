---
title: "Wireless no more on Acer Aspire One with Ubuntu 8.10 Intrepid"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by sefs on 2009-05-28
Network Manager is not longer detecting wireless on my acer aspire one.

lspci detects the card as: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I know the card is fine because I dualboot with windows and everything is fine there.  

I am not sure if it was an update or what.

What can I do to get back my wireless in ubuntu.

iwconfig does not seem to see the card either

Thanks.

---

### Post by sefs on 2009-05-28
Ok, I forgot I had to reinstall the madwifi drivers.  There was probably a kernel update or something

---

### Post by timcredible on 2009-05-28
i installed 8.10 on an acer one from scratch and just installed linux-backports-<something> from the repos and wireless worked.  there's a nice website with acer one and ubuntu info that has all the info you'd ever need, forget the name though.

---

### Post by beefcurry on 2009-06-02
is the mad wifi drivers alot better then ath5k? By default after a fresh 9.04 install ubuntu uses ath5k and that sometimes randomly drops my card.

---

### Post by sefs on 2009-06-08
I'm on 8.10 at the moment and the help page for the aa1 on ubuntu had directed me towards the madwifi I believe.

---

