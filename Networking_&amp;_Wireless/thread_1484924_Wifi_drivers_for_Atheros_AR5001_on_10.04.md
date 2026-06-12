---
title: "Wifi drivers for Atheros AR5001 on 10.04"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by zabi1001 on 2010-05-16
hi,
i have Atheros card in my laptop HP G60 as it says in 'lspci'


```
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

i am looking for its drivers for Ubuntu 10.04...plz help me get it working
thanks

---

### Post by ____ on 2010-08-16
Try madwifi [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072).
Hope it helps.

---

### Post by DevilMongoose on 2010-08-16
Hey there, zabi1001, I have the same model of laptop.

I can tell you right now that you dont need new drivers. The problem is that the laptop is starting with the wifi default to off.
So, to get it working, (not permanently, but for right now) just open a Terminal, type in ```
iwlist scan
``` Then press the little wireless button next to the power button for about 5 - 10 seconds. Release it, and press enter.
Repeat this process until your scan shows results. It may take a couple of minutes. But once you see results in the scan you can then use the network manager to connect to the AP as normal.
(I read somewhere you may need to hold the button in for 30 or more seconds.
Its not an exact science. Just try various lengths of holding the button down.)

I know this is a very tricky fix, but it works. I have been using this fix for a little while. It is very time consuming to fiddle with the hardware switch at every boot though, because you are not sure when it is going to turn anything on.
But, the fact of the matter is that we need to get the wifi to default to being turned on at boot instead of off.

I have done a fair amount of searching on other forums and this one and tried a lot of different solutions, none of which worked. I will detail what I have done so far, because frankly, I have hit a wall. I am not sure what to do to fix this. I have NOT yet tried the madwifi drivers, but I would rather it work with the native type drivers.
I really need some help on this one.

First, I tried to remove and reload the driver.
```

modprobe -r -f ath5k
modprobe ath5k
```No dice.
####################################

Then I started documenting what happens before and after the switch is pressed.

Before wifi switch is depressed:

```
mongoose@lappy486:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


mongoose@lappy486:~$ tail /sys/class/rfkill/*/state
1
mongoose@lappy486:~$ tail /sys/class/rfkill/*/type
wlan
mongoose@lappy486:~$ tail /sys/class/rfkill/*/name
phy0
mongoose@lappy486:~$ tail /sys/class/rfkill/*/persistent
0
```Results for these are the same after the switch is pressed and wifi starts working.

]########################################

```
mongoose@lappy486:~$ sudo lshw -C Network
[sudo] password for mongoose:
  *-network              
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:d2:e1:1c
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:56:02:57:9a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
```#############################################

Before the switch is pressed:

```
mongoose@lappy486:~$ dmesg | grep -e wlan -e ath
[    0.521885] device-mapper: multipath: version 1.1.0 loaded
[    0.521888] device-mapper: multipath round-robin: version 1.0.0 loaded
[   30.600600] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   30.600613] ath5k 0000:07:00.0: setting latency timer to 64
[   30.600655] ath5k 0000:07:00.0: registered as 'phy0'
[   31.126543] ath: EEPROM regdomain: 0x64
[   31.126546] ath: EEPROM indicates we should expect a direct regpair map
[   31.126551] ath: Country alpha2 being used: 00
[   31.126552] ath: Regpair used: 0x64
[   31.136063] Registered led device: ath5k-phy0::rx
[   31.136079] Registered led device: ath5k-phy0::tx
[   31.136082] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   32.076660] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```After:

```
mongoose@lappy486:~$ dmesg | grep -e wlan -e ath
[    0.521885] device-mapper: multipath: version 1.1.0 loaded
[    0.521888] device-mapper: multipath round-robin: version 1.0.0 loaded
[   30.600600] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   30.600613] ath5k 0000:07:00.0: setting latency timer to 64
[   30.600655] ath5k 0000:07:00.0: registered as 'phy0'
[   31.126543] ath: EEPROM regdomain: 0x64
[   31.126546] ath: EEPROM indicates we should expect a direct regpair map
[   31.126551] ath: Country alpha2 being used: 00
[   31.126552] ath: Regpair used: 0x64
[   31.136063] Registered led device: ath5k-phy0::rx
[   31.136079] Registered led device: ath5k-phy0::tx
[   31.136082] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   32.076660] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  239.223134] wlan0: direct probe to AP   (try 1)
[  239.223177] wlan0: deauthenticating from   by local choice (reason=3)
[  239.253317] wlan0: direct probe to AP  (try 1)
[  239.256974] wlan0: direct probe responded
[  239.256980] wlan0: authenticate with AP    (try 1)
[  239.258060] wlan0: authenticated
[  239.258091] wlan0: associate with AP    (try 1)
[  239.263001] wlan0: RX AssocResp from    (capab=0x421 status=0 aid=90)
[  239.263005] wlan0: associated
[  239.263477] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```After this I can then see networks, and connect.

I have also tried to install the linux-backports-modules-wireless-generic meta-package and this has not worked. Wifi still defaults to off at boot.

I am thinking I will unload both the Ethernet module, and the wifi, and then load just the wifi. I will report back.

---

### Post by DevilMongoose on 2010-08-18
Unloading the wifi, and the ethernet via:

```
sudo modprobe -r -v ath5k && sudo modprobe -r -v forcedeth
```

And then reloading just the ath5k module,

Has no effect on getting the wireless to come on.

If anyone has any suggestions, I would love to hear them.

---

### Post by Madhu Cherukuri on 2010-12-23
I too had the same problem HP G60 laptop with AR5001 wifi card. I tried before installing the ubuntu 10.04 and 10.10 three to four times trying all - MadWifi drivers and NDisWrapper. Nothing worked.  

Yesterday, I went thru this thread and then tried and it worked. I will write down the steps I used. So that others may find this useful.


[LIST=1]
[*]As suggested pressed the wifi button for 30 seconds.
[*]On the top network icon right clicked and then Enabled the wireless.
[*]From the terminal entered the command
[*][B]rfkill list
[/B]
[*]the output was
[*]Soft blocked: **yes**
[*]Hard blocked: no
[/LIST]
Using rfkill killed the id. And from the edit connection added the wifi information. 
Restarted the machine. [COLOR=Red]It did not work. [/COLOR]

Then again using rfkill killed the id 0.  [B]The mystery part begins here.

[/B]I got a phone and so closed the laptop lid and came back after half an hour, opened the lid, to my surprise the WIFI connected to internet.

Restarted the machine twice, every time after login WIFI was connecting to the router.

[B]My reading is, there is some Soft block, other wise the out of box drivers should work from UBUNTU 10.10 or 10.04 should work.

Hope this helps, who struggled for a week like me.
[/B]

---

### Post by Stord on 2010-12-25
I am having the same problems. Im trying to update to ubuntu 10.10. I had previously gotten wifi working in ubuntu 10.04 by installing 
linux-backports-modules-headers-lucid-generic
linux-backports-modules-wireless-lucid-generic

. After that i from then on had to turn on wifi on boot by patiently clicking the wifi enable on/off a couple of times. But now that i see this, it may have been random change that it worked. In any case, the generic backports for meerkat aren't working. 

I have tried rfkill list (output works initially) and rfkill unblock all. However, once i do rfkill unblock all, further rfkill  list never returns . 

Im personally suprised this bug in atheros 5001 is still around - how long has it been known??? I guess no one has been motivated to make a permanent fix because this chipset randomly works forever (for some) after a little playing around.

---

