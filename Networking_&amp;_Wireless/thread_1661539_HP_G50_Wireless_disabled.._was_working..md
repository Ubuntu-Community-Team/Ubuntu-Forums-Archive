---
title: "HP G50 Wireless disabled.. was working."
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by truz on 2011-01-06
I'm running Ubuntu 11.04 latest updates on a HP G50 laptop. It was working fine but would never auto connect to wireless.

I would have to select the wireless from the top menu and connect to a network. However I disabled it once and tried to re-enable but ran into a problem. The Enable Wireless was grey and would not allow me to enable.

Have searched google and tried lots of solutions and none worked. I even reinstalled and still have the problem. Any ideas?

Thanks!

---

### Post by PatchesTheCaveman on 2011-01-07
Plug into a wired Ethernet connection and download the rfkill package.  To do that, go to Applications > Accessories > Terminal, type the following into the black box that appears, and press Enter:
```
sudo apt-get install rfkill
```

Then, run it:
```
sudo rfkill list
```

Does it report your wireless card as hard or soft-blocked?

If it's hard-blocked, flip the wireless switch on your laptop.  This might be a physical switch, a discrete button, or a Fn key combination.

If it's soft-blocked, run this command to unblock it:
```
sudo rfkill unblock 0
```
Note that you'll need to replace 0 with the number reported by the list command above for your wireless card, if it's different.

After that, you should be able to right-click and re-enable wireless, if it doesn't do that automatically.

---

### Post by truz on 2011-01-08
I show the following..

0: hp-wifi: Wireless LAN
soft block: yes
hard block: yes

1: phy0: Wireless LAN
soft block: no
hard block: no

Wireless is still showing disabled and will not allow me to enable. I tried doing sudo rfkill unblock 0 twice and it still won't unblock.

---

### Post by PatchesTheCaveman on 2011-01-08
Try:
```
sudo modprobe rfkill
sudo rfkill unblock 0
```

---

### Post by truz on 2011-01-09
That managed to work. However every time I reboot the system they are blocked again.

---

### Post by PatchesTheCaveman on 2011-01-10
Run this command:
```
sudo bash -c "echo rfkill >> /etc/modules"
```

Then run this command to edit */etc/rc.local*:
```
sudo gedit /etc/rc.local
```

Above the line that says *exit 0* add this line:
```
rfkill unblock 0
```
Save and exit.  Now it should work on reboot.

---

### Post by Interruptor on 2011-01-15
> **PatchesTheCaveman said:**
> If it's hard-blocked, flip the wireless switch on your laptop.  This might be a physical switch, a discrete button, or a Fn key combination.
Also it could be sensor in the Ethernet socket.
On Compaq nx6310 I had to pull out the wire, otherwise WiFi was hard-blocked.

---

