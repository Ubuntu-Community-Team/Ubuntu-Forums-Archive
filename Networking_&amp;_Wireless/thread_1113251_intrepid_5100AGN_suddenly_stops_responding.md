---
title: "intrepid 5100AGN suddenly stops responding"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by GoldWing on 2009-04-01
I have to reboot my laptop several times a day.
Symptom: wireless just stops responding and I cannot connect to any network anymore.
I can connect with other laptops no problem.

output of dmesg:

[  196.600281] wlan0: No ProbeResp from current AP 00:0d:54:9e:18:07 - assume out of range
[  197.208071] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
[  197.708095] iwlagn: Error sending REPLY_SCAN_ABORT_CMD: time out after 500ms.
[  198.208144] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[  198.208160] iwlagn: Error setting new RXON (-110)
[  198.208174] wlan0: authenticate with AP 00:0d:54:9e:18:07
[  198.408281] wlan0: authenticate with AP 00:0d:54:9e:18:07
[  198.608280] wlan0: authenticate with AP 00:0d:54:9e:18:07
[  198.808097] wlan0: authentication with AP 00:0d:54:9e:18:07 timed out
[  212.312073] iwlagn: Error sending REPLY_SCAN_ABORT_CMD: time out after 500ms.
[  212.312124] iwlagn: Aborted scan still in progress after 100ms
[  212.312134] wlan0: Failed to config new SSID to the low-level driver

oliver@oliware-elite:~$ lspci |grep -i wifi
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
oliver@oliware-elite:~$ 

laptop = HP elitebook 8530p

I browsed several workarrounds, but they all tell me that the current kernel should solve all of these problems:

oliver@oliware-elite:~$ uname -a
Linux oliware-elite 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

---

### Post by GoldWing on 2009-04-28
still the same.
Upgrade to jaunty is not a solution, my video card is not supported, I get a blank screen.

wifi:
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

vga:
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

---

### Post by GoldWing on 2009-05-02
tried the 32 bit version now

vga: so only the restricted driver does not work, this means no compiz

wifi: still the same problem, but I have a workaround (instead of rebootin)

```
sudo rmmod iwlagn
sudo modprobe iwlagn
```

Can anybody script this ?

---

