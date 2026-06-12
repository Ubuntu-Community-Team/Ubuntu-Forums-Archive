---
title: "after start nm-applet always has wifi not startet"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by Torero on 2011-01-02
Hi @ all,


sorry if some options are not really described but i use the german Version.

I am new with Ubuntu and Network Manager. Everything ist working fine, but when i start my Netbook i always have to switch on my wifi by my self. 
Now my question: is there any way to give nm-applet the information with some start option to start with wifi swiched on? 
Inside the connection Options i already switched on "connect automatically" and "all users can use this connection" 

also i found the option inside /etc/NetworkManager/nm-system-setings.conf 

no-auto-default=<MAC:Adress>

great thanks for your help

Torero

Ubuntu (MavericMeerkat) i386 / Netbook Lenovo S10-3s / 
0.8.1+git.20100809t190028.290dc70-0ubuntu3 (network-manager-gnome)

---

### Post by PatchesTheCaveman on 2011-01-02
The wireless option in NetworkManager or the wireless switch on your laptop?

Try downloading the rfkill package:
```
sudo apt-get install rfkill
```

Then reboot and run:
```
sudo rfkill list
```
before and after you turn wireless on.

If the output differs we might be able to add something to your startup scripts that switches it on.

---

### Post by DieseL1988 on 2011-01-11
I have this same problem, same device as well: Lenovo S10-3s.

Output from rfkill list
```

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

```

If I do a rfkill unblock all then wireless is disabled in network manager. Re-enable it and all works fine, but then the rfkill output returns to as above. It's almost as if rfkill is seeing things backwards. It's got 'blocked/yes' for when the wifi is actually unblocked and it's got 'unblocked/no' for when the wifi is actually blocked.

Does it have anything to do with the fact rfkill outputs acer-wireless on a lenovo laptop?

---

### Post by DieseL1988 on 2011-01-11
I've found a fix, see this thread: [http://ubuntuforums.org/showthread.php?p=10344446](http://ubuntuforums.org/showthread.php?p=10344446)

---

