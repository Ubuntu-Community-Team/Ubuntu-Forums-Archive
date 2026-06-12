---
title: "Making my broken laptop work"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by audit on 2010-11-06
I have a laptop with a broken battery.

It is only used by my granddaughter and she is 5--still I like the wireless to work.

For the last six months the only way it would work after it was shutdown
was for me to type in the terminal:

```
sudo ifconfig wlan0 down
sudo ifconfig wlan1 down
sudo shutdown -h now
```

When I would restart it I would have wireless.

Today, I upgraded to using the wireless to 10.10.

After the restart the wireless did not work as I expected, but the old work around no longer works.

Any ideas?

I have tried ```
rfkill unblock all
``` but it does not help.

When I click on the wireless icon it tells me that

"Wireless Network (Atheros AR5001 Wireless Network Adapter)
 wireless is disabled"
and
"Wireless Network(Ralink 802.11 bg WLAN)
Wirelss is disabled"

---

### Post by P4man on 2010-11-06
is this ubuntu (gnome) ? I dont quite recognise those strings, are you using the default network manager? If you are, if you right click the network manager icon, does it show wireless networking as enabled ? (if it doesnt, enable it obviously).

If its not as simple as that, can you provide the output of

```
rfkill list
```

as well as

```
lshw -C network
```

---

### Post by audit on 2010-11-06
I can not enable it will not allow me.

here is the output you requested:
```
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: phy4: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:42:6c:c3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:42 ioport:3000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4d:a3:1b:b1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:92600000-9260ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@2:5
       logical name: wlan1
       serial: 00:1f:1f:39:ab:6f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.35-22-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg
```

---

### Post by P4man on 2010-11-06
Does the laptop have a hardware switch to turn wifi on ? And/or an Fn+function key to enable wifi? Have you tried those?

---

### Post by audit on 2010-11-06
> Does the laptop have a hardware switch to turn wifi on ? And/or an Fn+function key to enable wifi? Have you tried those?

Yes it does have a hardware switch-- and I have tried it multiple times.
The only function key that seems relevant does nothing more than return to my homepage. (it obviously does not work now unless the Ethernet cable is attached)

---

### Post by audit on 2010-11-07
alright--now it is working again.
As far as I know I did nothing different. I updated the system through the ethernet cable. After which I noticed that I was it was now letting me "enable wireless". 
Then I typed in the terminal:
```
sudo ifconfig wlan0 down
sudo ifconfig wlan1 down
```

Then I shut the computer down.
When I rebooted I also pushed the wireless button (I doubt that was the reason, but it was really the only thing I did different) and when it came on
I had wireless.

I wish I knew what the problem was--so I understood why it sometimes works.

--good night and thanks for reading even if you could not help.

---

### Post by audit on 2010-11-07
I woke up this morning and restarted my laptop to find much to my surprise that not only do I still have wireless, but I no longer need the external wireless card.
It has been to months since this computer worked, and since it is now working correctly I'll probably go out and replace the battery (which before seemed like a waste of money).
I do not know which combination of external buttons, terminal commands, or if the problem was a bug which was fixed by an update.
I really wish I knew what was wrong and what was corrected. 
I am leaving this here mostly as archive for myself to review if I ever have problems again.

take care and if you have an idea what this nood did right I would appreciate the response.

---

### Post by grahammechanical on 2010-11-07
The listing shows > Soft blocked: Yes and > Hard blocked: Yes. So the wireless hardware was switched off at the keyboard. Sometimes it takes a reboot or two for changes to be accepted by the system and configuration files to be re-written.  I found this recently when I tried to get networking going in Ubuntu Studio. Nothing I did seemed to work. So I gave up and booted into my normal Ubuntu setup. A few days later I accessed Ubuntu Studio again and was surprised when Update manager notified me of some updates.

By the way, did you know that you can set the wireless network connection to connect automatically? Right click on the network manager icon and select Edit Connections. Select your wireless connection and tick the box marked Connect Automatically.

Regards   and watch out - your granddaughter will soon be showing you how to use a computer! Oh, the joys of being a grandparent.

---

