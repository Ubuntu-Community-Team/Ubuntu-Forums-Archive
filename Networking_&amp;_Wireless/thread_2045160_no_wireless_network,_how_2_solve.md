---
title: "no wireless network, how 2 solve?"
date: 2012-08-20
forum: Networking &amp; Wireless
---

### Post by schmidtmueller on 2012-08-20
It is a ubuntu10 up2date on a HP8510workstation
there is no driver. 
and i do not know wich one and where i should get it,
and how 2 install,
neither how 2 activate it:(

it would be wonderfull if anyone couls help me out.


i collectet some information tht can help, i hope.

         [FONT=Liberation Serif, Times New Roman, serif]iwconfig->[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]wlan0     IEEE 802.11abg  ESSID:off/any  [/FONT] 
  [FONT=Liberation Serif, Times New Roman, serif]Mode:Managed  Access Point: Not-Associated   Tx-Power=off   [/FONT] 
  [FONT=Liberation Serif, Times New Roman, serif]Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]Encryption key:off[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]Power Management:off[/FONT]
  

*        [FONT=Liberation Serif, Times New Roman, serif]ifconfig->[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]eth0      Link encap:Ethernet  HWaddr 00:1f:29:7d:ad:6c  [/FONT] 
  [FONT=Liberation Serif, Times New Roman, serif]UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]collisions:0 txqueuelen:1000 [/FONT] 
  [FONT=Liberation Serif, Times New Roman, serif]RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]Interrupt:22 Memory:e8000000-e8020000 [/FONT] 
 

   [FONT=Liberation Serif, Times New Roman, serif]lo        Link encap:Local Loopback  [/FONT] 
  [FONT=Liberation Serif, Times New Roman, serif]inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]inet6 addr: ::1/128 Scope:Host[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]RX packets:16 errors:0 dropped:0 overruns:0 frame:0[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]TX packets:16 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]collisions:0 txqueuelen:0 [/FONT] 
  [FONT=Liberation Serif, Times New Roman, serif]RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)[/FONT]

   
[FONT=Liberation Serif, Times New Roman, serif]
lshw -class Network->[/FONT] 

   [FONT=Liberation Serif, Times New Roman, serif]*-network DISABLED[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]description: Wireless interface[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]vendor: Intel Corporation[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]physical id: 0[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]bus info: pci@0000:10:00.0[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]logical name: wlan0[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]version: 61[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]serial: 00:1f:3b:95:60:77[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]width: 64 bits[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]clock: 33MHz[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-15-generic-pae firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abg[/FONT]
  [FONT=Liberation Serif, Times New Roman, serif]resources: irq:46 memory:e4000000-e4001fff[/FONT]


[FONT=Liberation Serif, Times New Roman, serif]
[/FONT]

---

### Post by chili555 on 2012-08-20
> *-network [COLOR="Red"]DISABLED[/COLOR]
description: Wireless interface
product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
vendor: Intel CorporationWe wonder how and why it's disabled. Please run and post:```
dmesg | grep -e wlan -e iwl
rfkill list all
```

---

### Post by schmidtmueller on 2012-08-21
* 	   #dmesg | grep -e wlan -e iwl  
 [   16.939099] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:  
 [   16.939101] iwlagn: Copyright(c) 2003-2010 Intel Corporation  
 [   16.939170] iwlagn 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [   16.939179] iwlagn 0000:10:00.0: setting latency timer to 64  
 [   16.939207] iwlagn 0000:10:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4  
 [   16.977387] iwlagn 0000:10:00.0: device EEPROM VER=0x36, CALIB=0x5  
 [   16.977389] iwlagn 0000:10:00.0: Device SKU: 0Xb  
 [   16.981658] iwlagn 0000:10:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels  
 [   16.981737] iwlagn 0000:10:00.0: irq 46 for MSI/MSI-X  
 [   17.870634] iwlagn 0000:10:00.0: loaded firmware version 228.61.2.24  
 [   17.875545] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'  
 [ 1680.967317] iwlagn 0000:10:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)  
 [ 1680.967352] iwlagn 0000:10:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xe4000004)  
 [ 1680.967360] iwlagn 0000:10:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)  
 [ 1680.967370] iwlagn 0000:10:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006) 
 [ 1681.696426] iwlagn 0000:10:00.0: RF_KILL bit toggled to disable radio.
 

 

 #rfkill list all  
 0: phy0: Wireless LAN  
 	Soft blocked: yes  
 	Hard blocked: yes  
 1: hp-wifi: Wireless LAN  
 	Soft blocked: yes  
 	Hard blocked: no

---

### Post by chili555 on 2012-08-21
> RF_KILL bit toggled to disable radio.Also see:> 0: phy0: Wireless LAN
Soft blocked: yes
[COLOR="Red"]Hard blocked: yes[/COLOR] Please find the wireless switch and turn it on.

---

### Post by schmidtmueller on 2012-08-21
i tryed to scitch it on!
It doesnt respond!

---

### Post by chili555 on 2012-08-21
Please try:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Is the hard block cleared? Does the wireless work? If so, we'll need to blacklist the module *hp-wmi*.

---

### Post by schmidtmueller on 2012-08-22
done

#rfkill list all  
 0: phy0: Wireless LAN  
 	Soft blocked: no
 	Hard blocked: yes  

the wifi switch doesnt respond
networkmanager doesnt let me activate

after reboot

#rfkill list all  
 0: phy0: Wireless LAN  
 	Soft blocked: yes  
 	Hard blocked: yes  
 1: hp-wifi: Wireless LAN  
 	Soft blocked: yes  
 	Hard blocked: no 	

wifi-switchand networkmanager are not working

---

### Post by chili555 on 2012-08-22
> wifi-switchand networkmanager are not workingI assume you mean button #4 in the picture attached. Please run:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Is the wireless still hard blocked? Now press the button #4 *once only* and run:```
rfkill list all
```Please ignore the wireless LED. Is there any change?

---

### Post by schmidtmueller on 2012-08-22
:~$ sudo modprobe -r hp-wmi
:~$ sudo rfkill unblock all
:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

touched the button(#4) once
then->
:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

No change .
The wifi-button Led is blinking once when the system is shutting down.
But not during start up.

---

### Post by chili555 on 2012-08-22
We have seen a few instances where resetting the computer's BIOS to default restored the wireless switch to be able to be controlled. Can you please try?

Aside from that, I have no further ideas.

---

### Post by schmidtmueller on 2012-08-23
Resetting the bios WORKED

big THX for your help chili555

---

### Post by chili555 on 2012-08-23
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

---

