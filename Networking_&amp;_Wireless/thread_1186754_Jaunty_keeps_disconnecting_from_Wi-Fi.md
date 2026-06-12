---
title: "Jaunty keeps disconnecting from Wi-Fi"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by Endolith on 2009-06-13
Ugh.  Nothing but problems and more problems with every release.

Since I upgraded to Jaunty my Wi-Fi connection is flaky.  It will work fine for hours, maybe even days, and then suddenly disconnect and refuse to reconnect.  Logging out and logging in doesn't help, turning off wi-fi in hardware doesn't work, killing nm-applet doesn't work.  It repeatedly tries to reconnect and nothing happens.  The only thing I can figure out is to reboot.  

```
Jun 13 19:00:52 inspiron NetworkManager: <info>  eth1: link timed out. 
Jun 13 19:00:52 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating 
Jun 13 19:00:52 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated 
Jun 13 19:00:52 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Activation (eth1/wireless): association took too long. 
Jun 13 19:00:57 inspiron NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 13 19:00:57 inspiron NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 13 19:00:57 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> disconnected 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 13 19:00:57 inspiron NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto dynatron' has security, and secrets exist.  No new secrets needed. 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Config: added 'ssid' value 'dynatron' 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jun 13 19:00:57 inspiron NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 13 19:00:57 inspiron NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 13 19:00:57 inspiron NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 13 19:00:57 inspiron NetworkManager: <info>  Config: set interface ap_scan to 1 
Jun 13 19:00:57 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning 
Jun 13 19:00:57 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected 
Jun 13 19:00:57 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> associating 
Jun 13 19:00:58 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected 
Jun 13 19:01:03 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> associating 
Jun 13 19:01:03 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated 
Jun 13 19:01:03 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake 
Jun 13 19:01:07 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> disconnected 
Jun 13 19:01:07 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning 
Jun 13 19:01:08 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating 
Jun 13 19:01:08 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated 
Jun 13 19:01:08 inspiron NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake 
Jun 13 19:01:12 inspiron NetworkManager: <info>  eth1: link timed out. 
```

---

### Post by xavierp94 on 2009-06-13
I'm having the same problem with my wireless connection too. It hasn't happened lately though.

---

### Post by Amber_Man on 2009-06-14
Has anyone found a fix for this yet, it is really starting to annoy me.

---

### Post by Vostrocity on 2009-06-14
I actually have the same problem in Jaunty, but it hasn't bothered me much since it only happens a couple times a month and a reboot really isn't that bad. But it'd be nice if someone figures out a solution.

---

### Post by majamba on 2009-06-14
yeap sometimes experincing the samething

---

### Post by Scunnered on 2009-06-14
Like you all there are times where my connection fails.  Normally this requires that I re-enter the password to the wireless network.

What I found was that the only way was to enter the password and then when it follows the cycle and calls for it again select cancel. Once that has been done **Shut Down** and re-boot.  This usually works first time.  Please note that if you attempt to restart instead of shut down connection will not be made.

I hope this assists in some way.

---

### Post by Vostrocity on 2009-06-14
Yea I've also noticed that when it drops it tries to connect and and asks for your pass over and over again. But rebooting never failed me.

---

### Post by Endolith on 2009-06-16
Please report bugs about this so we can get to the bottom of it.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/331103](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/331103)

---

### Post by Student Driver on 2009-08-02
> **Endolith said:**
> Please report bugs about this so we can get to the bottom of it.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/331103](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/331103)

I am having the same issue with my Dell Mini 9, and I guess I will post to the bug as well.  If I reboot, it's fine.  I can usually get several days out of it, then it stops detecting WiFi spots and won't connect if you explicitly state which hotspot to connect to.

---

