---
title: "Wifi Hard and soft blocked"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by danbrownlow on 2012-08-13
Hi there, yesterday a problem with friends Wifi, today a problem with mine.

I booted up into Ubuntu today and wireless wouldn't work, no matter how many times I switched the hardware switch on or off, Ubuntu wouldn't see the Wireless card as on.

I remembered a command I used yesterday which was:

```

dan@inn0min4t3:~$ rfkill list all
0: sony-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes


```

I looked a bit more and noticed in my Network Settings, Ubuntu was reporting "Aeroplane Mode" was enabled, and Wireless as being Disabled. I couldn't toggle the switches either.

Next I found the command:

```

dan@inn0min4t3:~$ sudo rfkill unblock all
[sudo] password for dan: 
dan@inn0min4t3:~$ rfkill list all
0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


```

Which enabled wireless and I was able to connect (Wireless is now showing enabled and Aeroplane Mode is showing as disabled).

Any reason Ubuntu would do this? And what can I do to make this change permanent?

Thanks.

---

