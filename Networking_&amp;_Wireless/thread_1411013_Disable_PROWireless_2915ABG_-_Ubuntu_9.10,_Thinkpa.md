---
title: "Disable PRO/Wireless 2915ABG - Ubuntu 9.10, Thinkpad X41"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by hnmcc on 2010-02-19
I use this Thinkpad mostly for work while traveling, and wireless connectivity is not a big issue for me.  Battery life **is** a big issue, however.

I've just converted from Mandriva. With that, I was able to disable the wireless adapter so that it did nothing at all on boot - and only started on my instruction.

This made a dramatic difference to battery life! :D

Can anyone tell me how to achieve this in Ubuntu?

The file attached gives all the info about my wireless set-up as it stands.

---

### Post by hnmcc on 2010-02-21
Oh dear: looks horribly like I'll have to go back to Mandriva.  Which I really don't want to do: their version of OpenOffice has some serious problems, and the whole experience is less appealing.

This must be possible - and someone must know how to do it.  Please, whoever you are, help!

---

### Post by chili555 on 2010-02-21
You might try:```
sudo rfkill block wifi
```Please post back so the searchers will know the outcome.

---

### Post by hnmcc on 2010-02-21
> **chili555 said:**
> You might try:```
sudo rfkill block wifi
```Please post back so the searchers will know the outcome.

Thanks for the suggestion - no luck.  RFKILL LIST only mentions Bluetooth:

```
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
```

---

### Post by chili555 on 2010-02-21
Here is another idea. ```
sudo su
echo "0" > /sys/bus/pci/devices/0000:04:02.0/enable
```

---

### Post by hnmcc on 2010-02-21
> **chili555 said:**
> Here is another idea. ```
sudo su
echo "0" > /sys/bus/pci/devices/0000:04:02.0/enable
```

Thanks for this!

At first I thought we had a result: estimated battery life nearly doubled - but now (a few moments later) it's back to normal.  CORRECTION - now it's flipped back... and back again... :D

Typing the instruction ended the current wireless connection, whereupon NetworkManager tried to restart it. It asked for the router key (which it already knows) and I cancelled the dialog.  There is no visible activity in NetworkManager, but the wireless LED is now on continuously.

I think we have to assume that it probably hasn't worked.  But I'll try it again in action during the week, and see how it performs.

---

### Post by chili555 on 2010-02-21
You may have to precede the command with:```
/etc/init.d/NetworkManager stop
```Depending on the vintage of your system, it may instead be network-manager.

---

### Post by hnmcc on 2010-02-26
Sorry about the delay in getting back on this: super-busy week!

The NetworkManager command made no difference, unfortunately.

However, buried on the IBM site I found a quick set-up diagram for the Thinkpad which shows that Fn F5 is a WiFi & Bluetooth toggle switch.  The F5 key *should* have a blue wireless icon on it, and mine doesn't: but it **works**, which is what counts.

Anyway, thanks a lot for all your help. :D

---

