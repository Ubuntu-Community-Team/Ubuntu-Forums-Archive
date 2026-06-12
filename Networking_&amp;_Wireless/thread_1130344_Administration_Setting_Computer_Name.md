---
title: "Administration Setting Computer Name"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by UranUtan on 2009-04-19
Hi,

I have two Ubuntu machines with static IP. From Machine2 (U 8.10 x64) I ping Machine1  (U 8.10 x32, computer name = MyUbuComp1) by its name. The name is not recognized. But if i do
```
ping MyUbuComp1.local
```

Then I could see it with the correct IP.

Q1. Where does the .local come from?

Q2. The search results in this forum show in similar post that it is possible to set computer name by  System, Administration, Network. In my machine I don't have this item visible. I went to preference (Main Menu and checked that all items under Administration are enabled to be visible). What should I install to have this Network admin menu item enabled?

Thanks in advance for any help

---

### Post by dmizer on 2009-04-20
> **UranUtan said:**
> Q1. Where does the .local come from?
It is located (and can be edited) in: /etc/hosts

> **UranUtan said:**
> Q2. The search results in this forum show in similar post that it is possible to set computer name by System, Administration, Network. In my machine I don't have this item visible.

You can either edit /etc/hosts, or do the following. Before you do, please be aware that this will remove the nmapplet that allows you to configure your network from the computer icon in your notification tray. Usually there is no problem as long as you are using a wired connection, but if you're running wireless you may want an additional network management applet like wicd.

Install network-manager-gnome:
```
sudo aptitude install network-manager-gnome
```
Remove network-manager:
```
sudo aptitude remove network-manager
```

Now you will have the System > Administration > Network option.

---

