---
title: "ENCORE 54G wireless PCI"
date: 2006-02-21
forum: Networking &amp; Wireless
---

### Post by AirborneDude on 2006-02-21
Hello,
   I am new to Ubuntu.  I just installed it on my system.  Every went very good.  Now I have to setup my wireless card.

   My card is a Encore 54g wiresless card.  I read that it's chip set is RT2500.

But Ubuntu see's it as ACX 111 54g mbps Wireless Interfacecard by Texas Instruments. 

Is this right?  I can't ping out, I can't do anything.  CAn someone point me to the right direction?  I was told that the Encores are RT2500 but  Ubuntu see's it as something else.

Thanks...

---

### Post by AirborneDude on 2006-02-21
I am using version 5.10 Ubuntu..

---

### Post by Lambert on 2006-02-21
Same cards can have different chipsets in them. Usually the version separates this but not always. v1 maybe ralink v2 maybe TI v3 maybe broadcom... It's possible new version, same chipset and just some upgrade to the device.

See this link for the acx chipset. note the breezy section.

[http://doc.gwos.org/index.php/ACXDriver]("http://doc.gwos.org/index.php/ACXDriver")

You can verify it's a acx chipset with this command

lspci -v | grep -A 4 Eth

---

### Post by AirborneDude on 2006-02-21
Thanks Lambert.   I will read the article and hopefully it will point my in the right direction.

Hopefully get this thing working...

I will repost on this when I try it and let you and others know if this worked, thanks again.

---

