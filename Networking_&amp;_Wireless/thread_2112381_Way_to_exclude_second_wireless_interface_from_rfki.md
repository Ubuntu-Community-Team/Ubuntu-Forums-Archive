---
title: "Way to exclude second wireless interface from rfkill list? (12.10 - Quantal Quetzal)"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by m0rd0 on 2013-02-04
I've been working through the various threads on the subject of physical wireless switches disabling wireless interfaces for the last hour, but I've yet to find one that answers my particular issue.

I have an Acer laptop with an inbuilt Intel wireless nic which I use for everyday connections. I also have an Alfa USB nic for pen testing and for problematic wireless links where shouting the loudest often resolves connection drops. 

In previous releases the physical wireless switch has only disabled the inbuilt nic (Which is what I want to do to save some battery life). In the latest builds the functionality has changed to disable all network interfaces. What I'd like to do is bring the former usage scenario back for my laptop and effectively exclude the Alfa interface from the rfkill list.  

Does anyone know if this is possible and / or even if this is the right approach to take with this issue?

---

### Post by chili555 on 2013-02-04
Is one listed as phy0 and the other as phy1?```
rfkill list all
```Something like:> [COLOR="Red"]0: phy0[/COLOR]: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
Assuming the built-in is phy0, please try, instead of the wireless switch:```
sudo rfkill block 0
```Then check:```
rfkill list all
```

---

### Post by m0rd0 on 2013-02-04
Thanks for replying.

> **chili555 said:**
> Assuming the built-in is phy0, please try, instead of the wireless switch:```
sudo rfkill block 0
```

Using rfkill (*sudo rfkill block 5*) in this way causes the exact same result as the physical button. rfkill list outputs the following:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
5: phy4: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```Even if rfkill on the physical interface did work I can't see how that would help accomplishing my end goal of reimplementing the old usage model. Is there a way to specifically tailor rfkill command sets from function key input?

---

### Post by chili555 on 2013-02-04
> Is there a way to specifically tailor rfkill command sets from function key input?None that I am aware of. You might file a bug against rfkill or acer-wmi or both and see if there are better ideas. [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) > Using rfkill ([COLOR="Red"]sudo rfkill block 5[/COLOR]) in this way causes the exact same result as the physical button.I suspect the internal is 0 and the USB is 5. Didn't you want to disable the internal? 

This result suggests the internal is blocked and the USB is working. No?> 0: phy0: Wireless LAN
    Soft blocked: no
    [COLOR="Red"]Hard blocked: yes[/COLOR]
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
5: phy4: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by m0rd0 on 2013-02-05
Reviewing the network manager app it appears that disabling the onboard wifi through the physical switch also disables the wireless from the network manager perspective. So although the USB NIC isn't blocked by rfkill the entirety of wireless connectivity is disabled.

---

### Post by chili555 on 2013-02-05
> **m0rd0 said:**
> Reviewing the network manager app it appears that disabling the onboard wifi through the physical switch also disables the wireless from the network manager perspective. So although the USB NIC isn't blocked by rfkill the entirety of wireless connectivity is disabled.Perhaps I've been misunderstood. I'm suggesting you *NOT* use the switch and use the terminal command instead. While we both hope there is another more elegant solution, the terminal command is the one I'm aware of today and I hope it is helpful.

---

### Post by m0rd0 on 2013-02-05
> **chili555 said:**
> Perhaps I've been misunderstood. I'm suggesting you *NOT* use the switch and use the terminal command instead.

Nope, I'm understanding you. Issuing the terminal command results in the exact same problem where the network manager shows the wireless disabled. Even though the USB nic isn't blocked, wireless as my laptop knows it has ceased to exist.

---

