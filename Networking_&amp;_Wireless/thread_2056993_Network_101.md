---
title: "Network 101"
date: 2012-09-12
forum: Networking &amp; Wireless
---

### Post by mayagrafix on 2012-09-12
I just installed Ubuntu 12.04 on a laptop, the internet works fine thank you, but although it says in the top bar Network indicator menu that it is conected to the network via cable nothing shows up in the Network window when browsing with Nautilus (except for an empty folder named "Windows Network"). Ditto for the other computer on the network.

There are 2 stations on the network, the afore-mentioned laptop and a desktop; Both stations have Ubuntu 12.04 installed. Both conected to the same router via cable for Internet conection. 

How should I proceed?

Thanks for any and all help the network gurus may provide:KS

---

### Post by geeksmith on 2012-09-12
The network would show computers that are sharing files, e.g. via smb.  If there's nobody in the subnet doing so, then it's blank.

--
@@ron

---

### Post by mayagrafix on 2012-09-12
OK, so what should I do? share a file? how do u do dat?

---

### Post by DrBueler on 2012-09-13
Your best bet is to use Samba. Once installed you choose what you want shared and assign users to have access.

---

### Post by Rezliw on 2012-10-27
Similar problem. Can see all windows network folders in smbtree (in terminal) but can't find with network browse in file or in locate.

Making me crazy   Arrrrrgh!

---

