---
title: "Hard blocked"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by shafi on 2013-01-08
Hi,
I'm using ubuntu 12.10 AMD/64 bit. the wireless was working fine. 
I installed linux-header-generics-... and after that I can not see any wireless signal, and there is no interface any more

```
iwconfig 
eth0      no wireless extensions.

lo        no wireless extensions.

```
```
rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
```

I tried all these combinations:
```
sudo rfkill unblock all
sudo rfkill unblock wlan
sudo rfkill unblock 0
```
none of them worked for me still I'm getting:
```
rfkill list 0
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

any idea? I'm having a hp proBook 5320m
I also powered off/on the wifi via wireless button, but got no result.
thanks.

---

### Post by John.Klockenkemper on 2013-01-08
Hello.

Please provide the output of the following commands:

lspci

ifconfig

cat /etc/network/interfaces

---

### Post by praseodym on 2013-01-08
Plus:

```
lsmod

```
please. Try to reset the BIOS to default settings.

---

### Post by tgalati4 on 2013-01-08
Hardlock ON means that the BIOS has turned wireless off for some reason.  This could be a small switch on the machine.  It could be a FN-F2 key combination, or it could be a safety shutdown due to static electricity.

Find the switch and change it. Or shutdown, boot into BIOS and turn wireless back on.

---

### Post by shafi on 2013-01-09
> **tgalati4 said:**
> Hardlock ON means that the BIOS has turned wireless off for some reason.  This could be a small switch on the machine.  It could be a FN-F2 key combination, or it could be a safety shutdown due to static electricity.

Find the switch and change it. Or shutdown, boot into BIOS and turn wireless back on.
Thank you tgalati4.
booting into BIOS and turning on the wireless worked for me.

---

### Post by tgalati4 on 2013-01-09
Now, remove your Ugg boots.  That static electricity will shut down your wireless without you knowing it.

---

### Post by rajenthakur on 2013-02-06
Hi,
I have same problem. On using ubuntu 10.04 on thinkpad edge(E430 lenovo).
When I used rfkill list it show only bluetooth no wireless device found.

[HTML]sudo rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no[/HTML]

Any one can help me out. thanks in advance.

---

