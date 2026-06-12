---
title: "Lenovo E520 - 11.04 - WiFi not working"
date: 2011-08-21
forum: Networking &amp; Wireless
---

### Post by CTBuckweed on 2011-08-21
I upgraded to Natty 11.04 from 10.04 on my Lenovo E520. I did the upgrade because 10.04 did not support a 1366x768 resolution which is native on the Lenovo.

My Windows 7 Pro alternate boot reports the adapter as an 'Intel WiFi Link 1000 BGN'.

The WiFi worked without a hitch on 10.04 but I don't even see a 'wlan0' connection under 11.04, either in the installed system or with the live CD. All I see is 'eth0', the wired adapter. Networking works OK on the wired (eth0) connection.

With the 10.04 live CD, it still works....

What am I to do? Help needed....

---

### Post by bkratz on 2011-08-21
Please post the output of

rfkill list all

---

### Post by CTBuckweed on 2011-08-24
> **bkratz said:**
> Please post the output of

rfkill list all

rfkill list all output:

[B]0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no[/B]

I tried 'rfkill unblock 0' and 'rfkill unblock all' with no change in the output.

Thanks in advance for the help....

---

### Post by praseodym on 2011-08-24
Try to blacklist the module **acer_wmi**:

```
echo "blacklist acer_wmi" | sudo tee /etc/modprobe.d/blacklist-acer_wmi.conf
```
and reboot, check "rfkill" again.

If it doesn't work, remove the file and try a module parameter for that module:

```
sudo rm /etc/modprobe.d/blacklist-acer_wmi.conf
echo "options acer_wmi wireless=1" | sudo tee /etc/modprobe.d/acer_wmi.conf
```
and reboot again.

---

### Post by CTBuckweed on 2011-08-24
> **praseodym said:**
> Try to blacklist the module **acer_wmi**:

```
echo "blacklist acer_wmi" | sudo tee /etc/modprobe.d/blacklist-acer_wmi.conf
```and reboot, check "rfkill" again.

If it doesn't work, remove the file and try a module parameter for that module:

```
sudo rm /etc/modprobe.d/blacklist-acer_wmi.conf
echo "options acer_wmi wireless=1" | sudo tee /etc/modprobe.d/acer_wmi.conf
```and reboot again.

[B]Praseudym, You are my hero.

I did the <-- echo "blacklist acer_wmi" | sudo tee /etc/modprobe.d/blacklist-acer_wmi.conf --> and rebooted.

It worked! Thanks a million. Kudos to you. [/B]

---

### Post by khurtsiya on 2011-09-23
worked for me too
THANKS!

---

