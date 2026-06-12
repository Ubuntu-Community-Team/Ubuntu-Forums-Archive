---
title: "Issues with wireless + Ubuntu 13.04 + Lenovo W520"
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by euxneks on 2013-07-31
Hello all,

I was having trouble with gnome 3.8 connecting to a WPA2 wireless AP, in my logs, it looked like it was connecting and disconnecting in a never ending loop. It would also ask me frequently for my password in the GUI. I found a solution on my own and thought I would post it here in case anyone else encountered this in the future.

Here is an excerpt of my log:

```
Jul 30 09:37:43 companion kernel: [ 1955.549007] wlan0: authenticate with [WIFI AP MAC ADDRESS]
Jul 30 09:37:43 companion kernel: [ 1955.558424] wlan0: send auth to [WIFI AP MAC ADDRESS] (try 1/3)
Jul 30 09:37:43 companion NetworkManager[6164]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 30 09:37:43 companion kernel: [ 1955.563100] wlan0: authenticated
Jul 30 09:37:43 companion wpa_supplicant[1289]: wlan0: Trying to associate with [WIFI AP MAC ADDRESS] (SSID='[SSID]' freq=2462 MHz)
Jul 30 09:37:43 companion kernel: [ 1955.563463] wlan0: waiting for beacon from [WIFI AP MAC ADDRESS]
Jul 30 09:37:43 companion NetworkManager[6164]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 30 09:37:44 companion NetworkManager[6164]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jul 30 09:37:44 companion NetworkManager[6164]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 30 09:37:47 companion wpa_supplicant[1289]: wlan0: SME: Trying to authenticate with [WIFI AP MAC ADDRESS] (SSID='[AP SSID]' freq=2462 MHz)
Jul 30 09:37:47 companion kernel: [ 1959.076786] wlan0: authenticate with [WIFI AP MAC ADDRESS]
Jul 30 09:37:47 companion kernel: [ 1959.080967] wlan0: send auth to [WIFI AP MAC ADDRESS] (try 1/3)
Jul 30 09:37:47 companion NetworkManager[6164]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 30 09:37:47 companion wpa_supplicant[1289]: wlan0: Trying to associate with [WIFI AP MAC ADDRESS] (SSID='[AP SSID]' freq=2462 MHz)
Jul 30 09:37:47 companion kernel: [ 1959.087012] wlan0: authenticated
Jul 30 09:37:47 companion kernel: [ 1959.087339] wlan0: waiting for beacon from [WIFI AP MAC ADDRESS]
Jul 30 09:37:47 companion NetworkManager[6164]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 30 09:37:47 companion NetworkManager[6164]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jul 30 09:37:47 companion NetworkManager[6164]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 30 09:37:51 companion wpa_supplicant[1289]: wlan0: SME: Trying to authenticate with [WIFI AP MAC ADDRESS] (SSID='[AP SSID]' freq=2462 MHz)
Jul 30 09:37:51 companion kernel: [ 1962.629386] wlan0: authenticate with [WIFI AP MAC ADDRESS]
Jul 30 09:37:51 companion kernel: [ 1962.631900] wlan0: send auth to [WIFI AP MAC ADDRESS] (try 1/3)
Jul 30 09:37:51 companion NetworkManager[6164]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 30 09:37:51 companion wpa_supplicant[1289]: wlan0: Trying to associate with [WIFI AP MAC ADDRESS] (SSID='[AP SSID]' freq=2462 MHz)
Jul 30 09:37:51 companion kernel: [ 1962.634533] wlan0: authenticated
Jul 30 09:37:51 companion kernel: [ 1962.634933] wlan0: waiting for beacon from [WIFI AP MAC ADDRESS]
Jul 30 09:37:51 companion NetworkManager[6164]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 30 09:37:51 companion NetworkManager[6164]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jul 30 09:37:51 companion NetworkManager[6164]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 30 09:37:54 companion wpa_supplicant[1289]: wlan0: SME: Trying to authenticate with [WIFI AP MAC ADDRESS] (SSID='[AP SSID]' freq=5745 MHz)

```

I have a lenovo W520, dual boot with win7 and ubuntu 13.04.  I've installed gnome 3 from the PPA.  Unity could also not connect, though it used to connect on initial install.  I suspect the installation of gnome-3 from the PPAs introduced a regression of some sort.

Here is my network hardware information:
```

euxneks@companion:/var/log$ lspci | grep -i net
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)

```

After much googling around, it appears that it might be something to do with the AP possibly not advertising a specific value over wifi.

This was the solution I found:

```

sudo service network-manager stop
sudo modprobe -r iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo service network-manager start

```

The network manager start and stop may not be needed.

EDIT: To make it permanent, as I was kindly reminded by praseodym:
> **praseodym said:**
> You can make it permanent at boot-up via:
```

echo "options iwl3945 disable_hw_scan=1" | sudo tee -a /etc/modprobe.d/iwl3945.conf
```

(I've already done this, I just forgot that I did :P)

If there is a better solution out there, I'd love to hear it :)

EDIT 2013-11-14: I found out that the wireless network I was having troubles with I think is not assigning IPv6 addresses through dhcp or something, so I've disabled IPv6 (on that specific network) and that seems to have fixed it.  Good luck to others out there!

---

### Post by praseodym on 2013-07-31
You can make it permanent at boot-up via:
```

echo "options iwl3945 disable_hw_scan=1" | sudo tee -a /etc/modprobe.d/iwl3945.conf
```

---

### Post by euxneks on 2013-07-31
Ah, yes, I forgot to mention I did that too!

---

