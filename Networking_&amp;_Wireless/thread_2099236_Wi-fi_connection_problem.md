---
title: "Wi-fi connection problem"
date: 2012-12-29
forum: Networking &amp; Wireless
---

### Post by ZelAlex on 2012-12-29
My wi-fi is working in Windows 7 but ubuntu 12.04 LTS isn't able to connect to the same wi-fi.

It happens many times. The problem solves itself many times but I want to know if it can be solved manually.

Any information required for help?

[http://ubuntuforums.org/showthread.php?t=2037340](http://ubuntuforums.org/showthread.php?t=2037340)
This thread is of the same laptop. It contains information about the laptop.

---

### Post by praseodym on 2012-12-29
If

```
lspci -nnk | grep -iA2 net
```
shows an Intel-device, and

```
lsmod
```

shows the driver "iwlwifi", deactivate the N-mode of the driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by kleenex on 2012-12-29
Hi **ZelAlex**. In addition to what **praseodym** wrote, You could try to enable wireless device by using [COLOR=SeaGreen]rfkill(1)[/COLOR] command. This tool is designed for enabling and disabling wireless devices. An example
```
[COLOR=Red]$[/COLOR] [COLOR=SeaGreen]rfkill list wlan[/COLOR]
## or even
[COLOR=Red]$[/COLOR] [COLOR=SeaGreen]rfkill list all[/COLOR]
```If you see that the device is blocked (e.g. **Soft blocked: yes **etc.) You can try to unblock it with 
```
[COLOR=Red]$[/COLOR] [COLOR=SeaGreen]rfkill unblock wlan[/COLOR]
## or even
[COLOR=Red]$[/COLOR] [COLOR=SeaGreen]rfkill unblock all[/COLOR]
```Of course You have to restart network-manager, for example, by using [COLOR=SeaGreen]service[/COLOR] command: [COLOR=Blue]sudo service network-manager restart[/COLOR].

---

### Post by cottfcfan on 2012-12-29
Not sure your problem is the same as mine, but I find that after I boot into Windows 7, I then have to shutdown my computer before logging back into Ubuntu. Just rebooting into Ubuntu leaves me with no Wireless.

---

