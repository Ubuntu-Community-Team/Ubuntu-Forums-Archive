---
title: "Can't connect to home network after upgrade to 12.04"
date: 2012-10-13
forum: Networking &amp; Wireless
---

### Post by jolindbe on 2012-10-13
Hi,

I've just upgraded my 10.04 LTS to 12.04 LTS, but after this I cannot connect to my home wireless network. When selecting it, a minute or so passes, it prompts me for the password, I enter it, wait another minute, and I am again prompted for the password.

I can connect to the Wifi of my smartphone, and other computers can connect to my home wifi. I have checked the password carefully.


Output of lspci:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [NVS 3100M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
0d:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
0d:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```


The output of cat /var/log/syslog | grep NetworkManager just after I've failed to connect (the network that is not working is called Hogwarts):
```

Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> (wlan0): device state change: config -> disconnected (reason 'none') [50 30 0]
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> (wlan0): deactivating device (reason 'none') [0]
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Activation (wlan0) starting connection 'Hogwarts'
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 13 20:56:46 bilbo NetworkManager[1134]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Activation (wlan0/wireless): connection 'Hogwarts' has security, and secrets exist.  No new secrets needed.
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Config: added 'ssid' value 'Hogwarts'
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Config: added 'scan_ssid' value '1'
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Config: added 'auth_alg' value 'OPEN'
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Config: added 'psk' value '<omitted>'
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 13 20:56:46 bilbo NetworkManager[1134]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Oct 13 20:56:46 bilbo NetworkManager[1134]: <info> Config: set interface ap_scan to 1
Oct 13 20:56:47 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:56:47 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:56:47 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:56:47 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:56:49 bilbo NetworkManager[1134]: <info> wpa_supplicant die count reset
Oct 13 20:56:51 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:56:51 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:56:51 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:56:51 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:56:54 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:56:55 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:56:55 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:56:55 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:56:58 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:56:58 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:56:58 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:02 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Oct 13 20:57:02 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:02 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:02 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:57:05 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:57:06 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:06 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:06 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:57:09 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:57:09 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:09 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:10 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:57:13 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:57:13 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:13 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:13 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:57:17 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:57:17 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:17 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:17 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:57:20 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:57:20 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:20 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:21 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:57:24 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:57:24 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:24 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:24 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:57:28 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:57:28 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:28 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:28 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:57:31 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:57:31 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:32 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:32 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:57:35 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:57:35 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:35 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:35 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:57:39 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:57:39 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:39 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:39 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:57:42 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:57:42 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:43 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:43 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 13 20:57:46 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 13 20:57:46 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 13 20:57:46 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: associating -> disconnected
Oct 13 20:57:46 bilbo NetworkManager[1134]: <warn> Activation (wlan0/wireless): association took too long.
Oct 13 20:57:46 bilbo NetworkManager[1134]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Oct 13 20:57:46 bilbo NetworkManager[1134]: <warn> Activation (wlan0/wireless): asking for new secrets
Oct 13 20:57:46 bilbo NetworkManager[1134]: <info> (wlan0): supplicant interface state: disconnected -> inactive
```

The computer is a Lenovo Thinkpad T410.

I'd be very thankful for any suggestions - let me know if you need any more info.

---

### Post by jolindbe on 2012-10-14
Using wicd instead of Network Manager it apparently works. Any theories? If not, what is the easiest way to make wicd default and not use Network Manager?

---

### Post by eigersa on 2012-10-14
I have the exact same problem, though it's on my Compaq 610. I've posted for help in the beginners guide (since I am a beginner) as well as on the Ubuntu facebook page. Will be watching this thread to see if any useful advice comes about.

---

### Post by Finnicella on 2012-10-14
Hi, it can be a problem in "interfaces" file.
Please give this command:
```
cat /etc/network/interfaces
```
and write what it says.
Bye

---

### Post by jolindbe on 2012-10-14
> **Finnicella said:**
> Hi, it can be a problem in "interfaces" file.
Please give this command:
```
cat /etc/network/interfaces
```
and write what it says.
Bye

Thanks! The result is:
```
auto lo
iface lo inet loopback


```

By the way, using wicd is not problem-free either, every time I start the computer, I have to toggle the setting "Automatically connect to this network" (first to off, then to on again) for wicd to be able to connect properly.

---

### Post by Finnicella on 2012-10-14
The output is ok.

Do you have both Network Manager and Wicd installed on your pc?

---

### Post by jolindbe on 2012-10-14
> **Finnicella said:**
> The output is ok.

Do you have both Network Manager and Wicd installed on your pc?

Yes - I installed wicd when it didn't work, since I found some suggestions that it might work better - optimally I'd like to use Network Manager, though.

By the way, the output above was printed when I was connected to the WiFi with wicd - do you need the output when Network Manager is failing to connect, or is the output the same?

---

### Post by Finnicella on 2012-10-14
No thanks.
I know that the two cannot coexist, I think this is the problem, you can try to leave only wicd.
Bye

---

### Post by jolindbe on 2012-10-14
> **Finnicella said:**
> No thanks.
I know that the two cannot coexist, I think this is the problem, you can try to leave only wicd.
Bye

Uninstalled Network Manager, still same problem with wicd (have to toggle the "Automatically connect..." back and forth to get it to connect). And no system tray icon for wicd, so if there is a way of getting it to work in Network Manager, that would be preferrable.

---

### Post by jolindbe on 2012-10-15
Please, can anybody help me?!?

wicd does not work properly (I have to connect several times, toggling  "Automatically connect" back and forth; furthermore it does not work at my job wifi), Network Manager does not work at all with my home network, but flawlessly with the job network.

I'll give you any output you need, just let me know what...

---

### Post by jolindbe on 2012-10-15
Never mind, problem was solved through changing the router security settings from WPA-PSK [TKIP] to WPA2-PSK [AES]. But I have no clue on why not WPA-PSK [TKIP] wouldn't work in Ubuntu 12.04. Anyway, now works perfectly in Network Manager, and wicd is uninstalled.

---

