---
title: "Connection broken after upgrading to 8.10"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by xX-Felipao-Xx on 2009-02-09
After the upgrade ended successfully, the PC restarted itself and when I logged into my session, internet was not working.

I used pppoeconf, it found my eth0 modem, I did everything, entered my username, password, the terminal told me that the connection was launched, but it wasn't.

The icon with the 2 screens in the top bar shows a cross (which is not good, I guess :P) and I have Active the network (ticked).

Before the upgrade everything worked fine.

What can I do?

Thanks in advance !

---

### Post by xX-Felipao-Xx on 2009-02-09
Weird... I turned off and on again my modem and did pppoeconf after that and worked, but only for this time, the next time after a reboot, I have to do it again :P

And mean the internet works,... the cross in the Network manager's icon is still there... any idea?

---

### Post by radtek on 2009-02-09
I've been running Intrepid 64bit flawlessly until the latest kernel came out. Now I'll drop my network connection after a few hours. Says I'm connected but there's no throughput. Reboot and its back. Until it decides to quit...

---

### Post by xX-Felipao-Xx on 2009-02-11
BUMP!

Update: Everytime I turn on the PC, I need to turn off the modem, then turn it on, and then do a pppoeconf... is then when I have internet.

Any idea??????????

---

### Post by Genghis Prawn on 2009-02-11
I have the same problem. 8.04 works fine. 8.10 won't access the internet. It recognizes the ethernet (eth 0, and eth 1) and gives me a network connected icon .. but wont go to the internet. If I refresh the connection it tells me that the network is gone.

---

### Post by xX-Felipao-Xx on 2009-02-11
I have uninstalled Network-Manager and replaced it for wicd... no success at all.

It's still happening the same... I changed some things in dsl-provider file and pap-secret, let see what happens (when I reboot)

---

