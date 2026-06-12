---
title: "wireless does not work on HP 630"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by barna on 2012-12-27
Hi
I have recently installed kubuntu 12.10 on a HP 630. I can not make the wireless card (Atheros AR9285). 

```

lspci:
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

The hardware switch button is Fn+F12, by pressing this the indicator led does not change status, however KNetworkManager changes the wireless status: "Wireless disabled in software" or "Wireless disabled by hardware". Unfortunately even in the "Wireless disabled in software" I am unable to enable the wifi: if I click on "Enable wireless", it gets selected for a very short time, then it goes back to disabled, and dmesg outputs this:

```

[  241.890058] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[  241.890077] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node f7429c18), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[  241.890104] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f742a168), AE_AML_BUFFER_LIMIT (20120320/psparse-536)

```

Any help?
Thank you

---

### Post by barna on 2012-12-27
This was the solution:

```

echo "options hp_wmi wireless=1" | sudo tee -a /etc/modprobe.d/hp_wmi.conf

```

Credit goes to:

[http://forum.ubuntuusers.de/topic/wireless-funktioniert-nach-neuinstallation-von/#post-5042037](http://forum.ubuntuusers.de/topic/wireless-funktioniert-nach-neuinstallation-von/#post-5042037)

---

### Post by barna on 2013-06-06
****, I upgraded to 13.04. It did not work again, and I was happy I discovered the solution I described above. I issued that command, and the wireless card disappeared 
```

rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```
(previously there were two more cards, hp-wifi and something else. hp-wifi was reported to be soft blocked, but not hard blocked)
Previously, while hp-wifi was still there, I had the same symptom as I discribed earlier: I could click (in kde network manager) on the wifi card, but it got disabled again. Now it is not there at all. This is an infinite story...

---

### Post by barna on 2013-06-06
I removed /etc/modprobe.d/hp_wmi.conf, and restarted. Now rfkill list all gives this:
```

rfkill list all
0: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: hp-bluetooth: Bluetooth
        Soft blocked: yes
        Hard blocked: no
2: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```
Enable wireless is now not disabled in the kde network manager, but as I described, if I enable it, it gets disabled immediately. Any ideas?

---

### Post by barna on 2013-06-06
I removed hp_wmi (sudo rmmod hp_wmi)
did this echo "options hp_wmi wireless=1" | sudo tee -a /etc/modprobe.d/hp_wmi.conf trick, and then loaded hp_wmi again
sudo modprobe hp_wmi
```

ERROR: could not insert 'hp_wmi': Invalid argument

```

---

