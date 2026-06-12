---
title: "Wireless not working anymore - rt73usb"
date: 2013-01-02
forum: Networking &amp; Wireless
---

### Post by rafaelhsn on 2013-01-02
Hi.

I have a USB wilress that was working perfectly. Somehow (maybe after some system upgrade) is not working anymore.

I tried to figure out it but was not able. So if someone could help I would appreciate =)

This is what I got from syslog.

```
Dec 31 22:20:40 hp kernel: [ 1217.464046] usb 1-2: new high-speed USB device number 2 using ehci_hcd
Dec 31 22:20:40 hp udevd[1870]: failed to execute '/lib/udev/mtp-probe' 'mtp-probe /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-2 1 2': No such file or directory
Dec 31 22:20:40 hp kernel: [ 1217.716078] usb 1-2: reset high-speed USB device number 2 using ehci_hcd
Dec 31 22:20:41 hp kernel: [ 1218.112741] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112754] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112762] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112771] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112778] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112787] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112794] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112803] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112809] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112818] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112825] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112834] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112841] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112849] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112856] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112865] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112872] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112881] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112888] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112896] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112903] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112912] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112919] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112928] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112935] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112944] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112951] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112960] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112967] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112975] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112983] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.112991] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.112998] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.113007] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.113014] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.113023] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.113029] cfg80211: Disabling freq 5260 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113034] cfg80211: Disabling freq 5280 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113038] cfg80211: Disabling freq 5300 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113043] cfg80211: Disabling freq 5320 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113048] cfg80211: Disabling freq 5500 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113052] cfg80211: Disabling freq 5520 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113057] cfg80211: Disabling freq 5540 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113061] cfg80211: Disabling freq 5560 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113066] cfg80211: Disabling freq 5580 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113071] cfg80211: Disabling freq 5600 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113075] cfg80211: Disabling freq 5620 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113080] cfg80211: Disabling freq 5640 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113084] cfg80211: Disabling freq 5660 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113089] cfg80211: Disabling freq 5680 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113094] cfg80211: Disabling freq 5700 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113099] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.113108] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.113115] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.113124] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.113131] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.113139] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.113146] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.113155] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.113162] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.113171] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.113177] cfg80211: Disabling freq 5170 MHz
Dec 31 22:20:41 hp kernel: [ 1218.113183] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.113191] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.113198] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.113207] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp kernel: [ 1218.113214] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
Dec 31 22:20:41 hp kernel: [ 1218.113223] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 31 22:20:41 hp NetworkManager[782]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2:1.0/ieee80211/phy0/rfkill0) (driver (unknown))
Dec 31 22:20:41 hp kernel: [ 1218.141027] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Dec 31 22:20:41 hp kernel: [ 1218.148581] Registered led device: rt73usb-phy0::radio
Dec 31 22:20:41 hp kernel: [ 1218.148647] Registered led device: rt73usb-phy0::assoc
Dec 31 22:20:41 hp NetworkManager[782]: <info> (wlan0): using nl80211 for WiFi device control
Dec 31 22:20:41 hp NetworkManager[782]: <warn> (wlan0): driver supports Access Point (AP) mode
Dec 31 22:20:41 hp NetworkManager[782]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt73usb' ifindex: 3)
Dec 31 22:20:41 hp NetworkManager[782]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 31 22:20:41 hp NetworkManager[782]: <info> (wlan0): now managed
Dec 31 22:20:41 hp NetworkManager[782]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 31 22:20:41 hp NetworkManager[782]: <info> (wlan0): bringing up device.
Dec 31 22:20:41 hp NetworkManager[782]: <info> (wlan0): preparing device.
Dec 31 22:20:41 hp NetworkManager[782]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 31 22:20:41 hp kernel: [ 1218.303255] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 31 22:20:41 hp kernel: [ 1218.303997] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 31 22:20:41 hp dbus[583]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Dec 31 22:20:41 hp NetworkManager[782]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2:1.0/net/wlan0, iface: wlan0)
Dec 31 22:20:41 hp NetworkManager[782]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 31 22:20:41 hp dbus[583]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Dec 31 22:20:41 hp NetworkManager[782]: <info> wpa_supplicant started
Dec 31 22:20:41 hp NetworkManager[782]: <info> (wlan0): supplicant interface state: starting -> ready
Dec 31 22:20:41 hp NetworkManager[782]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 31 22:20:41 hp NetworkManager[782]: <info> (wlan0): supplicant interface state: ready -> inactive
Dec 31 22:20:41 hp NetworkManager[782]: <warn> Trying to remove a non-existant call id.
rafael@hp:/var/log$ 
```

---

### Post by Pjotr123 on 2013-01-02
Try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

### Post by rafaelhsn on 2013-01-02
I tried all steps exactly as described.
Not worked.

The strange is that I was using perfectly before.
Seems to be a kind of incompatibility with some update on my opnion.

Any other idea?

The wireless seems to be powerup normally.

iwconfig
```
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```

lshw -C network
 ```
 *-network               
       descrição: Interface sem fio
       physical id: 1
       informações do barramento: usb@1:2
       nome lógico: wlan0
       serial: 00:0c:43:2a:93:d5
       capabilities: ethernet physical wireless
       configuração: broadcast=yes driver=rt73usb driverversion=3.2.0-35-generic-pae firmware=1.7 link=no multicast=yes wireless=IEEE 802.11abg

```

---

### Post by amjjawad on 2013-01-02
Hello and welcome to Ubuntu Forum :)

What system are you using? what release? what update are you referring to?

---

### Post by rafaelhsn on 2013-01-02
> **amjjawad said:**
> Hello and welcome to Ubuntu Forum :)

What system are you using? what release? what update are you referring to?

Hi! I'm was using Lubuntu 12.04 32 bits and just update to 12.10 by update manager to see if solve the problem, but wifi still does not work.

Not sure exactly what update could be responsible for that (if is that the issue as well, my guess, because the system asks for updates everyday almost..)

---

### Post by amjjawad on 2013-01-02
> **rafaelhsn said:**
> Hi! I'm was using Lubuntu 12.04 32 bits and just update to 12.10 by update manager to see if solve the problem, but wifi still does not work.

Not sure exactly what update could be responsible for that (if is that the issue as well, my guess, because the system asks for updates everyday almost..)

Ok, so you had Lubuntu 12.04 and you have upgraded it to 12.10 via Update Manager.
You have done that via Wired Network (LAN), right?

Does
```
sudo lshw -C network
```
still shows: 
```
 driver=rt73usb
```

---

### Post by rafaelhsn on 2013-01-02
> **amjjawad said:**
> Ok, so you had Lubuntu 12.04 and you have upgraded it to 12.10 via Update Manager.
You have done that via Wired Network (LAN), right?

Does
```
sudo lshw -C network
```
still shows: 
```
 driver=rt73usb
```

Hi, yes exactly, via LAN cable.

on lshw still show rt73usb: [http://pastebin.com/m7MrsWYt](http://pastebin.com/m7MrsWYt)

---

### Post by amjjawad on 2013-01-02
> **rafaelhsn said:**
> Hi, yes exactly, via LAN cable.

on lshw still show rt73usb: [http://pastebin.com/m7MrsWYt](http://pastebin.com/m7MrsWYt)

Which basically means your system is still able to detect the driver so there is no problem with that.
The issue as far as I can tell is a connection problem not a driver problem.

Are you using the Network Manager? I had some problems with it recently so I had to use wicd instead.

If you still using the Network Manager, I suggest to remove your Wireless Network from the list, unplug your Wireless USB Adapter, reboot, login and plug your USB again and try to connect to your Wireless Network.

If that failed, we need to go more in depth ;)

---

### Post by rafaelhsn on 2013-01-02
> **amjjawad said:**
> Which basically means your system is still able to detect the driver so there is no problem with that.
The issue as far as I can tell is a connection problem not a driver problem.

Are you using the Network Manager? I had some problems with it recently so I had to use wicd instead.

If you still using the Network Manager, I suggest to remove your Wireless Network from the list, unplug your Wireless USB Adapter, reboot, login and plug your USB again and try to connect to your Wireless Network.

If that failed, we need to go more in depth ;)

Hi, thanks for the reply.

Actually, the network manager is set to false. so not in use..

```
rafael@hp:/etc/NetworkManager$ cat NetworkManager.conf 
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```

I have no idea what I else can do to solve that.

---

### Post by rafaelhsn on 2013-01-02
I just erased thedisk and performed a fresh install but still no success...

Same log / situation.

I tested the USB WIFI on a windows notebook and it worked, so I assume that the problem is not the wifi dongle..

If anyone have any idea please advise.

---

### Post by rafaelhsn on 2013-01-03
Just tried to dpkg a older version of network-manager but no success again...:(

---

### Post by rafaelhsn on 2013-01-03
Installed WICD. stopped network-manager daemon.

No success as well with wicd.

---

### Post by amjjawad on 2013-01-03
> **rafaelhsn said:**
> Installed WICD. stopped network-manager daemon.

No success as well with wicd.

When you are on the LiveCD/LiveUSB, does the USB work?

Does your network manager detect your Wireless Network to begin with? is it listed?

What happens when you try to connect to your Wireless Network? is it secure or not? are you sure you are choosing the correct wireless security?

---

### Post by rafaelhsn on 2013-01-03
@amjjawad
Thanks for you help.

I just purchased another USB dongle with other chip and worked.

Should be a freak incompatibility

---

### Post by amjjawad on 2013-01-05
> **rafaelhsn said:**
> @amjjawad
Thanks for you help.

I just purchased another USB dongle with other chip and worked.

Should be a freak incompatibility

You are welcome but I have done nothing much :)

So, everything is ok at the moment? if yes, could you please mark this thread as Solved? 

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

