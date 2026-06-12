---
title: "Mythbuntu wake on lan"
date: 2016-05-02
forum: Mythbuntu
---

### Post by philip7 on 2016-05-02
Has anyone got any advice on setting up wake on lan with mythbuntu?

I've followed the advice here [https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

As far as I can tell everything has been setup correctly, I've recently fresh installed to 16 and had wol working without any issues before.

---

### Post by Lester_Burnham on 2016-05-03
Hi,

Run ifconfig in a terminal and check the interfaces.
On my machine eth0 changed to something like this enp8s0

Lester

---

### Post by philip7 on 2016-05-03
That change has happened to me as well, but had a quick Google and it sounds like a new naming convention so don't think it will cause a problem.

Not sure if I should disable network manager and configure myself, seem to think I did that (somehow) last time.

---

### Post by Lester_Burnham on 2016-05-03
Hi,
So don't you need to substitute the old eth0 with enp8s0 in: sudo ethtool -s <NIC> wol g
Eg. sudo ethtool -s enp8s0 wol g (use the interface you see in if config)
Then add it to rc.local or your interfaces file.
I prefer rc.local
Lester

---

### Post by philip7 on 2016-05-04
That's not a problem for me, magic packet is enabled automatically so no need to add to the script.

---

### Post by philip7 on 2016-05-09
Looks like network-manager was the problem, I uninstalled network-manager and then followed the same steps in the Wake On Lan guide. When testing with Ethtool WOL wasn't enabled so I included the necessary script in /etc/network/interfaces and it worked

---

