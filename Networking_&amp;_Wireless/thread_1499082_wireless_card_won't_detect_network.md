---
title: "wireless card won't detect network"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by CelticFiddle on 2010-06-01
Hello everyone :)
I've just installed Kubuntu 10.04 on my laptop and I have issues with WiFi.
My card seems to be detected and driver/firmware installed. 
(I installed firmware through:
```
sudo apt-get install b43-fwcutter
```)
However, the card doesn't detect my local wireless network.
 
 
So, I've been following [this]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") troubleshoot guide. Here's what i get:
 
**[COLOR=red]nm-tool[/COLOR]**
```

** (process:2771): WARNING **: <WARN>  get_one_connection(): error: invalid connection: 'NMSettingWireless' / 'bssid' invalid: 1                                                                
 
- Device: wlan0 ----------------------------------------------------------------                                                                                                                
  Type:              802.11 WiFi                                                                                                                                                                
  Driver:            b43                                                                                                                                                                        
  State:             disconnected                                                                                                                                                               
  Default:           no                                                                                                                                                                         
  HW Address:        90:4C:E5:91:7B:AE                                                                                                                                                          
 
  Capabilities:                                                                                                                                                                                 
 
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
 
  Wireless Access Points 
```
 
**[COLOR=red]lshw -C network[/COLOR]**
```

 *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0500000-f0503fff
 
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 90:4c:e5:91:7b:ae
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
 

```
 
So, seems like the driver is Ok!
Now, here's what [COLOR=red]**rfkill list **[/COLOR]gives:
```
0: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: dell-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```
 
 
Now, a [COLOR=red]**dmesg**[/COLOR] command shows a loop on:
```
[ 4363.112276] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 4368.629256] b43-phy0: Controller restarted
[ 4368.629293] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000

```
 
Here's what **[COLOR=red]sudo iwlist scan[/COLOR]** returns:
```
wlan0     Interface doesn't support scanning : Device or resource busy
```
 
Does anyone have an idea on what my problem may be?
Thank you so much :D

---

### Post by CelticFiddle on 2010-06-01
I'm sorry this seems similar to recurrent questions.. but I've gone through mannnny old threads with no results.

Ideas, Anyone?

Thank you!

---

### Post by pdc on 2010-06-02
I can only suggest this diagnostic script

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English)

download it; run it; see if it gives you helpful answers

---

### Post by krippa on 2010-06-02
Did you try turning wireless switch off, rebooting and not reactivating it again until you are already logged in. It´s a workaround to an annoying bug I reported [here]("https://bugs.launchpad.net/ubuntu/+bug/588366").

---

### Post by krippa on 2010-06-06
If anyone's having a problem with the wireless switch, I found a workaround.. [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9421500#post9421500]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9421500#post9421500")

---

### Post by northd_tech on 2010-06-06
> **CelticFiddle said:**
> 
  Wireless Access Points [/CODE]**[COLOR=red]lshw -C network[/COLOR]**
```

 *-network               
       description: Network controller
       product: BCM4312 802.11b/g

```

You have apparently got a Broadcom 4312 wireless chipset- mine is a Broadcom 4321AG that will use your drivers (or the newer 802.11n higher speed ones too).

You probably want to run the proprietary "Broadcom STA" driver- that has worked very well for me.

Also, can you post the output of the following terminal commands:

```
lsmod

ifconfig

iwconfig

```I might be busy for a couple of days, but a search of this forum for "Broadcom STA 4312" should find some helpful threads- yours is one of the "easy" ones IMHO.

Good luck.

eta: Try these threads tagged with "broadcom 4312" first:

[http://ubuntuforums.org/tags.php?tag=broadcom+4312](http://ubuntuforums.org/tags.php?tag=broadcom+4312)

---

### Post by CelticFiddle on 2010-06-13
Hi all!
I followed [these]("http://ubuntuforums.org/showpost.php?p=9102439&postcount=34") instructions (removed driver, firmware..)
And installed the STA driver -- worked fine!

Thank you very much :D

---

