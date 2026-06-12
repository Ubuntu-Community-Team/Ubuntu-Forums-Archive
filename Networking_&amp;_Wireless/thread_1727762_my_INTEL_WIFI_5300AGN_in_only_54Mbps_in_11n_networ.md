---
title: "my INTEL WIFI 5300AGN in only 54Mbps in 11n network"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by mdh3666 on 2011-04-12
[SIZE=3]HI, my Intel Wifi 5300agn works well in ubuntu 10.10, but the max speed rate is **only 54Mbps**, in a 11n wireless network. It functions normally in XP and has the max speed rate 300Mbps in the same condition.

I do not know why and can Anyone fix it? THX a lot! [/SIZE] 
```
Linux ***** 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

user@host:~$ lsmod | grep iw
iwlagn                178948  0 
iwlcore               127415  1 iwlagn
mac80211              231541  2 iwlagn,iwlcore
cfg80211              144470  3 iwlagn,iwlcore,mac80211
```
[SIZE=3]Do i need to update the ucode?[/SIZE]

---

### Post by mdh3666 on 2011-04-13
Keep waiting.

---

### Post by leejkennedy on 2011-04-18
Hi

I was having this exact issue recently and fixed it by re-setting the wireless security to use WPA2 and AES. It's strange but my windows 7 Home Premium dual boot could cope with my previous wireless settings which were WPA/WPA2-PSK with TKIP algorithm, but Ubuntu Maverick would just not work at a higher speed than 54Mbps until I reset as described. I'm now getting 150Mbps.

FYI this was with the ath9k driver, I'm not sure if this fix is specific to my network card (an Atheros AR9285 built into a Samsung laptop) and hope this helps..

Lee

---

### Post by jawilljr on 2011-04-18
What is the output of:

```
cat /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf
```

Jerry

---

### Post by deadvirus on 2011-06-26
> **leejkennedy said:**
> Hi

I was having this exact issue recently and fixed it by re-setting the wireless security to use WPA2 and AES. It's strange but my windows 7 Home Premium dual boot could cope with my previous wireless settings which were WPA/WPA2-PSK with TKIP algorithm, but Ubuntu Maverick would just not work at a higher speed than 54Mbps until I reset as described. I'm now getting 150Mbps.

FYI this was with the ath9k driver, I'm not sure if this fix is specific to my network card (an Atheros AR9285 built into a Samsung laptop) and hope this helps..

Lee

Thanks! I had this problem too and changing from TKIP to WPA2 + AES fixed it. Weird bug...

---

