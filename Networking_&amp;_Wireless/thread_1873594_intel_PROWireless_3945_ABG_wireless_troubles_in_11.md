---
title: "intel PRO/Wireless 3945 ABG wireless troubles in 11.10"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by timbuktoo on 2011-11-01
hello Ubuntu forum.
I have a HP tc4400 with intel PRO/Wireless 3945 ABG card.  I have had it since 10.04 LST was released and had no problems with the wireless, however when i upgraded to 11.10 the upgrade failed however using the live cd usb disk thing's new upgrade existing system harddrive partition option i saved all my files and programs and it worked. but then the system update ran and got updated packages the wireless ceased working and i need help fixing it.

---

### Post by wildmanne39 on 2011-11-01
Hi, please post the results of:
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod | grep iwl
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan -e wpa -e etwork | tail -n55
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by timbuktoo on 2011-11-01
```
root@tim-tc4400:/home/tim# nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:16:D4:9F:BF:D5

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:13:02:96:BF:D3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    cookies:         Infra, 00:13:F7:0A:52:1E, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    St_John_LM:      Infra, C0:3F:0E:2F:96:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2


```

```
root@tim-tc4400:/home/tim# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

```

```
root@tim-tc4400:/home/tim# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```

root@tim-tc4400:/home/tim# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

```

root@tim-tc4400:/home/tim# lsmod | grep iwl
iwl3945                73329  0 
iwl_legacy             71499  1 iwl3945
mac80211              272785  2 iwl3945,iwl_legacy
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211

```

```
root@tim-tc4400:/home/tim# sudo cat /var/log/syslog | grep -e iwl -e firmware -ewlan -e wpa -e etwork | tail -n55
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) starting connection 'Auto cookies'
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> (wlan0): bringing up device.
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> (wlan0): device state change: config -> failed (reason 'config-failed') [50 120 4]
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <warn> Activation (wlan0) failed for access point (cookies)
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <warn> Activation (wlan0) failed.
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov  1 16:41:59 tim-tc4400 NetworkManager[856]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> Auto-activating connection 'Auto cookies'.
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) starting connection 'Auto cookies'
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> (wlan0): bringing up device.
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> (wlan0): device state change: config -> failed (reason 'config-failed') [50 120 4]
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <warn> Activation (wlan0) failed for access point (cookies)
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <warn> Activation (wlan0) failed.
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov  1 16:42:02 tim-tc4400 NetworkManager[856]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> Auto-activating connection 'Auto cookies'.
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) starting connection 'Auto cookies'
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> (wlan0): bringing up device.
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> (wlan0): device state change: config -> failed (reason 'config-failed') [50 120 4]
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <warn> Activation (wlan0) failed for access point (cookies)
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> Marking connection 'Auto cookies' invalid.
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <warn> Activation (wlan0) failed.
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov  1 16:42:05 tim-tc4400 NetworkManager[856]: <warn> bluez error getting default adapter: No such adapter

```

those are the responses that it gives me.
thank you a lot for helping me.

---

### Post by wildmanne39 on 2011-11-01
Hi, first it looks like you have a hard block try turning your wireless on with the switch or key like fn f5 then post:
```
rfkill list all
``` 
```
sudo iwlist scan
```
again.
Thank you

---

### Post by timbuktoo on 2011-11-01
the dropdown menu at top right of screen is checked that the wireless is on after pressing button however indicator light is dark. after pressing button off and menu saying wireless off it is also dark. it is as if the led there were removed.

anyway with menu saying wireless on but light dark it says
```
root@tim-tc4400:/home/tim# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

and

```
root@tim-tc4400:/home/tim# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


```

---

### Post by wildmanne39 on 2011-11-01
Hi, restart your computer and see if it come to life.
Thank you

---

### Post by timbuktoo on 2011-11-01
it works now. it rebooted 2x. both times connecting to the wireless internet and having the blue wireless light back. thankyou very much. and if i may ask how did you fix it

---

### Post by wildmanne39 on 2011-11-01
Hi, it was the hardware switch being turned off and you turned it on, then just had to reboot.

You welcome! I am glad it is working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

