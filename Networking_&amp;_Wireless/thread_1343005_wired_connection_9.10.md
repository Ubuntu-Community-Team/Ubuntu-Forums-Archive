---
title: "wired connection 9.10"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by abdo5705 on 2009-12-01
I have an E-Machines computer with a 2.5 celeron processor and dual boot with windows XP w/sp3. My internet connection works fine in windows. My connection in linux works intermittently and is getting me frustrated. My connection on the auto-etho setting. It worked fine for about 3 days after I upgraded to 9.10 from 9.04. I had the same problem in 9.04. Also, this computer is wired but I have a router connected for my laptop which has windows Vista.Does anyone know how to fix the problem ? Any help would be appreciated. My connection failed again so a downgraded to 9.04. This time no connection. I plugged the ethernet cable into a different port but the router fails to light up (only in linux not windows). please help!

---

### Post by linuxonbute on 2009-12-01
> **abdo5705 said:**
> I have an E-Machines computer with a 2.5 celeron processor and dual boot with windows XP w/sp3. My internet connection works fine in windows. My connection in linux works intermittently and is getting me frustrated. My connection on the auto-etho setting. It worked fine for about 3 days after I upgraded to 9.10 from 9.04. I had the same problem in 9.04. Also, this computer is wired but I have a router connected for my laptop which has windows Vista.Does anyone know how to fix the problem ? Any help would be appreciated.

Does it work if you do not have the laptop connected?
Have you changed anything around the time when it stopped working ( e.g updates to any software, installed other software, altered any settings )?
Have you changed the ethernet cable at all?

---

### Post by teward on 2009-12-01
Have you tried plugging the computer into a different port on the router/switch/modem?

---

### Post by abdo5705 on 2009-12-01
I didn't change anything. It just stopped working.

---

### Post by abdo5705 on 2009-12-01
I didn't even think of that because it worked in windows. Right now it's working again but for how long.... could it be the router? It's a linksys model wrt160n.

---

### Post by abdo5705 on 2009-12-06
Please help! problem still exists and I've run out answers.

---

### Post by uncaspi on 2009-12-06
Try to remove all lines except auto lo and iface lo inet looback in /etc/network/interfaces  and then reboot.

---

