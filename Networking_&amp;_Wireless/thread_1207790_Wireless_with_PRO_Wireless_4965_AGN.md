---
title: "Wireless with PRO Wireless 4965 AGN"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by razorboy5 on 2009-07-08
Hi

I'm using a gateway laptop with PRO Wireless 4965 AGN (iwl4965)

when i tried 

sudo lsmod | grep ipw2200

nothing happens

plz help would like wireless working

---

### Post by lswb on 2009-07-08
ipw2200 is the module loaded for the older Intel Pro Wireless 2000 b/g card. Your card uses the iwl4965 module. See if that module is loaded: lsmod |grep iwl4965

Can you describe the problem or any error messages?

---

### Post by wirelessmonkey on 2009-07-08
My 4965 uses the iwlagn module...

---

