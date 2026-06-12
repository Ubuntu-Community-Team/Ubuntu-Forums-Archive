---
title: "Wireless is Disabled by Hardware - Ubuntu 11.10"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by phiri on 2011-12-29
I am running Ubuntu 11.10 on a Lenovo G560 and my wireless was disabled when I hibernated my machine.I have been trying to find a solution to this problem for days now. It seems a number of people have experienced it, but unfortunately, I have been unable to find a viable solution.

**scap@scap-lenovo-g560:~$ rfkill list **
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
scap@scap-lenovo-g560:~$ 

**lspci command**
02:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


I even thought there was a problem with the card and so I went and bought a USB wireless adapter, but it too is disabled. Could someone kindly help me understand why this might be happening and possibly help with a solution as well?

---

### Post by phiri on 2011-12-29
> **phiri said:**
> I am running Ubuntu 11.10 on a Lenovo G560 and my wireless was disabled when I hibernated my machine.I have been trying to find a solution to this problem for days now. It seems a number of people have experienced it, but unfortunately, I have been unable to find a viable solution.

**scap@scap-lenovo-g560:~$ rfkill list **
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
scap@scap-lenovo-g560:~$ 

**lspci command**
02:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


I even thought there was a problem with the card and so I went and bought a USB wireless adapter, but it too is disabled. Could someone kindly help me understand why this might be happening and possibly help with a solution as well?

Well now I feel sheepish :( I just discovered there's a hidden switch somewhere on the bottom of the machine; flipping it solves everything.

---

