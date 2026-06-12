---
title: "Need help accessing public open wireless network"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by ciaopaulo on 2011-05-05
Hi all,

Using my laptop, I'm trying to get onto the local library's wireless network, with zero results so far.

Basically, I can see the network, but when NetworkManager tries to connect it just spins for a few minutes and then rejects the connection. (Or the connection is rejected by the router)

My wireless connection works fine when connecting to my WPA home network.

Can anyone recommend some diagnostic tools and processes so that I can figure out why this is happening?

Thanks,

Paul

---

### Post by NoBugs! on 2011-05-05
System-Admin-Log File Viewer should show what error occurs when connecting.

---

### Post by ciaopaulo on 2011-05-06
OK Xubuntu doesn't have Log File Viewer as far as I can tell.

Doing a grep under var/logs/ suggests these files might be of interest:

/var/log/auth.log:11
/var/log/daemon.log:975
/var/log/kern.log:4809
/var/log/messages:4809
/var/log/syslog.1:3281

From messages:

```
May  3 16:52:45 paulo-laptop kernel: [  112.258580] Linking with  Cambridgeshire Libraries,channel:1, qos:1, myHT:1, networkHT:0, mode:6

```


From kern.log:

```
May  3 16:52:50 paulo-laptop kernel: [  116.960159] Linking with  Cambridgeshire Libraries,channel:1, qos:1, myHT:1, networkHT:0, mode:6
May  3 16:52:50 paulo-laptop kernel: [  116.960177] ===>ieee80211_associate_procedure_wq(), chan:1
May  3 16:52:50 paulo-laptop kernel: [  117.040652] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
May  3 16:52:50 paulo-laptop kernel: [  117.071639] =================>ieee80211_authentication_req():auth->algorithm is 0

```

This seems to be the most useful message, from daemon.log:

```
May  3 17:16:19 paulo-laptop wpa_supplicant[995]: Trying to associate with 00:0f:61:fb:94:c0 (SSID='Cambridgeshire Libraries' freq=2437 MHz)
May  3 17:16:19 paulo-laptop wpa_supplicant[995]: **Association request to the driver failed**
May  3 17:16:19 paulo-laptop wpa_supplicant[995]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
May  3 17:16:19 paulo-laptop wpa_supplicant[995]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
```

---

### Post by ciaopaulo on 2011-05-09
*bump?*

---

### Post by josephmills on 2011-05-09
hi there lets do some diagnostics ```
lspci -nn
``` then ```
rfkill list 
``` this last one takes some time to load but it will ```
sudo lshw -C network
```please paste all here thanks

---

