---
title: "intel PRO/Wireless 3945 ABG wireless problems since installing  11.10"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by abenco on 2011-11-05
Wireless has been working up until I installed 11.10. First while booting up it says that it's searching for network configuration which it never finds. Then the drop down network menu doesn't show any ssids that are available. Now the drop down menu says Wireless Networks device not managed. Same with wired. No access to a wired network at the moment to see if that works, so I'm just using a second computer, so I can't copy and paste from the terminal on the problem computer. Here's some of the relevant information. Any help would be appreciated. Thank you.

```
lspci -nvn | grep -i net

02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan} Network Connection [8086:4222] (rev 02)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev01)
```

```
nm-tool

NetworkManager Tool

State: asleep

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unmanaged
  Default:           no
  HW Address:        00:1C:BF:3B:6B:C5

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

- Device: eth0 -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        00:1B:24:D0:95:1C

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


```


```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Leonards"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```



```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```


```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed : [COLOR="Red"]does see several networks, but since I'm typing this on a separate computer can't copy and paste at the moment. Please tell me if there's something specific I need to see here.[/COLOR]



```



```
lsmod | grep iwl
iwl3945                73329  0 
iwl_legacy             71499  1 iwl3945
mac80211              272785  2 iwl3945,iwl_legacy
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211

```

---

### Post by abenco on 2011-11-06
Updated the nm-system-settings.conf file in /etc/NetworkManager. Changed managed=false to true

rebooted and problem fixed.

---

