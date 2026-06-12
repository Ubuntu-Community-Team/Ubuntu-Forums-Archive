---
title: "Add VPN button inactive in Kubuntu 10.04"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by BlondboyUA on 2010-05-01
Hi guys!
I installed new Kubuntu 10.04 on my laptop and got some problem with
creation of my VPN connection. Actually the problem is that in network manager on VPN tab
button "Add" is inactive. I had the same problem with Ubuntu 9.1, but after installation of
all packages everything was OK. Now I already have installed all required packages, but "Add VPN" button still inactive/
What should I do? Can anybody give me some advise?

---

### Post by alexeix on 2010-05-01
I've noticed the same problem, after doing an upgrade.

Is there another network manager which could be used as a workaround?

---

### Post by alexeix on 2010-05-01
I found the solution to this issue in the Kubuntu Network Manager.

It seems like you need to install the following plug-in:

network-manager-vpnc-kde

The 'Add' button then appears in the VPN tab.

---

### Post by BlondboyUA on 2010-05-02
Thanx a lot! it work's! Only one point - in case if you are using PPTP to connect to VPN, you need to download and install once again vpnc, network-manager-vpnc, and network-manager-vpnc-kde.

---

### Post by karatedog on 2010-05-14
Thanks, this helped me, too.
I had a working Cisco VPN entry in my VPN tab, its data looked very strange without the proper package. After installing, the VPN properties now look fine.

---

