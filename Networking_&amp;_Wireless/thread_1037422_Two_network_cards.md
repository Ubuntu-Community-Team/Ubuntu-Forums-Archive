---
title: "Two network cards"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by schimm1 on 2009-01-11
Got any tips for helping this helping this noob get his onboard network connection working? only the pci card is sending and receiving.

they both work independently, but not together

thanks.

---

### Post by Iowan on 2009-01-11
You may need to manually edit */etc/network/interfaces*.  One card might be set DHCP, but the two cards should be in different subnets.

---

### Post by dmizer on 2009-01-11
For this, I suggest doing the following:

1) Install the gnome network management tool (assuming you have gnome)
```
sudo aptitude install gnome-network-admin
```
2) Disable Network-Manager: [https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)
3) Configure your network devices under System > administration > networking

---

### Post by schimm1 on 2009-01-11
> **dmizer said:**
> 3) Configure your network devices under System > administration > networking

how would one configure network devices?

---

### Post by dmizer on 2009-01-11
> **schimm1 said:**
> how would one configure network devices?

It will largely depend on what you want to do. What is your purpose for using two network cards?

---

### Post by schimm1 on 2009-01-11
> **dmizer said:**
> It will largely depend on what you want to do. What is your purpose for using two network cards?

faster downloading

---

### Post by cabbiinc on 2009-01-12
> **schimm1 said:**
> faster downloading

From the same ISP? Probably not going to help.

---

### Post by dmizer on 2009-01-12
Nope. Not going to work. Your WAN bandwidth probably won't exceed a megabit LAN speed. And even if it does, it's not likely that your modem or router will support it.

To assign the same IP address to multiple interfaces, you will need to use bonding. There is some discussion here about bonding: [http://ubuntuforums.org/showthread.php?t=1037423](http://ubuntuforums.org/showthread.php?t=1037423)

---

### Post by schimm1 on 2009-01-12
dang, thanks anyway

---

