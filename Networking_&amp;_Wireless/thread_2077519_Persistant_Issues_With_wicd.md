---
title: "Persistant Issues With wicd"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by Destructo47 on 2012-10-28
Title says all. Wicd won't always find the network I'm trying to connect to (or any at all). I have to refresh the list several times to get any networks to show up. When I try connecting, it gets stuck at "Validating Authentication", and gives me the "Bad Password" error. All traces of network manager have been eradicated, so there shouldn't be a conflict there. The security type is WPA2-PSK (personal). I am 100% sure that the passphrase I have entered is correct. All other devices on the network can connect without a hitch.

I have a reserved IP address on my router's DHCP server for my computer, and MAC filtering is off. The result of **sudo iwlist wlan0 scan** yields the following:

```
Interface doesn't support scanning.
```

I have tried using two identical wireless cards. I have _not_ tried switching PCI slots. I wouldn't be totally shocked if that worked, since this Abit IS7 motherboard is old, though I doubt it because **lspci** detects it:

```
02:07.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
```

The wireless card model I was using is a Linksys WMP54G. I have Googled around on the "Wicd bad password" issue, but I can't find a definitive answer. Anyone know of any solutions? Any help would be greatly appreciated.

12.04 Precise Pangolin
Compiz & Unity removed, using Gnome Shell.

---

### Post by Destructo47 on 2012-10-30
Who'da thunk it? I moved the wireless card to the PCI slot above it, and now the issue seems to have vanished. Also, I don't have the last security update to wicd (I did a manual reinstall of wicd while I was stuck offline), but I don't know if that would contribute to the issue or not.

If there is still no problem after the update and several boots, I will mark this as solved, but until I can confirm that switching PCI slots was the fix, I won't change anything here.

---

