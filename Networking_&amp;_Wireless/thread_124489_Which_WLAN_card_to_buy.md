---
title: "Which WLAN card to buy"
date: 2006-02-01
forum: Networking &amp; Wireless
---

### Post by ubuntuuser on 2006-02-01
Hi all, I am looking for advice on which WLAN adapter to buy. I want to play around in my home net and bought an old laptop for that. It doesn't have WLAN, so I need to buy an adapter. I want to use for example Wellenreiter, and I know that this app only supports certain chipsets (Prism2, Lucent, and Cisco based cards).
Does anybody here know of other limitations of that kind? I believe that I read somewhere that airsnort also supports just some chips, but I am not sure.

What do you think, are the chipsets supported by Wellenreiter generally recommendable? What adapter do you use?

Thanks in advance.

---

### Post by hajk on 2006-02-02
Well, I'm writing this on an old laptop right now, connected to my WLAN with a NetGear WG511T PC-Card (PCMCIA) card. This card is based on the Atheros chip, requiring the madwifi driver, which is in the linux-restricted-modules package for the kernel version used. So, if you're reading this then you'll know that this card works, out-of-the-box as it were. I recommend it.

---

### Post by devipl on 2006-02-02
3 com with ATmel chipset

regards

---

### Post by tomcoussement on 2006-02-02
does there exist a list somewhere with hardware that is supported out of the box for (k)ubuntu?

---

### Post by tomcoussement on 2006-02-02
ok, i found it already

[http://www.ubuntuforums.org/showthread.php?t=88639](http://www.ubuntuforums.org/showthread.php?t=88639)

seems like I need stronger glases :rolleyes:

---

### Post by dresnu on 2006-02-02
I too have a NetGear WG511T (PCMCIA) which did work out of the box just by plugging it in ;)

---

### Post by ubuntuuser on 2006-02-09
Just in case anyone needs this info somewhen in the future:
I got myself a Proxim ORiNOCO 8470-WD with the Atheros chipset. Doesn't work with wellenreiter, but with kismet, and the madwifi driver is able to go into monitor mode. 
Recommended.

---

