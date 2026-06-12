---
title: "Lenovo IdeaPad Z570-1024D9U - Laptop (Wireless Help)"
date: 2012-04-15
forum: Networking &amp; Wireless
---

### Post by zdeuyo on 2012-04-15
Hello Forum,


The problem I am having is with my Lenovo IdeaPad Z570-1024D9U - Laptop. I just recieved it after ordering from Lenovo and Windows 7 works fine. Ubuntu 11.10 flawless except wireless wont work. Here are the specs.


Description:	

IdeaPad Z570 Laptop - 1024D9U - Gunmetal Grey: Weekly Deal	

Processor:	2nd generation Intel Core i7-2670QM Processor( 
2.2GHz 1333MHz 6MB)	

Operating system:	Genuine Windows 7 Home Premium 64	

Graphics:	Intel Integrated HD Graphics 3000	

Memory:	8.0GB PC3-10600 DDR3 SDRAM 1333 MHz	

Display:	15.6" HD Glare with integrated camera 1366x768	

Pointing device:	Industry Standard Touchpad	

Hard Drive:	500GB 7200	

Optical Drive:	DVD Recordable	

Battery:	6 Cell Lithium-Ion	

Network Card:	Intel 1000 BGN Wireless	

Bluetooth:	Bluetooth Version 2.1 + EDR	

Warranty:	One Year	

Camera:	Integrated 2.0MP Camera	

HDMI:	HDMI (Out)



Please help.

---

### Post by chili555 on 2012-04-15
Please open a terminal and run and post:```
dmesg | grep iwl
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by zdeuyo on 2012-04-16
Thank you for your speedy reply. Here is the output you requested.

"zdeuyour@zdeuyour-Ideapad-Z570:~$ dmesg | grep iwl
[   10.723612] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   10.723615] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   10.723674] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.723684] iwlagn 0000:02:00.0: setting latency timer to 64
[   10.723718] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   10.743527] iwlagn 0000:02:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   10.743530] iwlagn 0000:02:00.0: Device SKU: 0X9
[   10.743532] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   10.744017] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   10.744184] iwlagn 0000:02:00.0: irq 43 for MSI/MSI-X
[   10.820626] iwlagn 0000:02:00.0: loaded firmware version 39.31.5.1 build 35138
[   10.822473] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
zdeuyour@zdeuyour-Ideapad-Z570:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
"

---

### Post by chili555 on 2012-04-16
> 3: [COLOR="Red"]acer-wireless[/COLOR]: Wireless LAN
Soft blocked: yes
Hard blocked: noacer-wireless on an Ideapad, eh? Please run:```
lsmod | grep acer
```Is the module *acer-wmi* loaded? If so, that's our offender. Let's remove it:```
sudo modprobe -r acer-wmi
sudo rfkill unblock all
```Now does your wireless work? If so,let's blacklist it so it doesn't come back again:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Post back your result so the searchers will learn.

---

### Post by zdeuyo on 2012-04-16
OMG it worked :) ...this disabled the offending driver which I believe is the default for ubuntu. This allowed the process to connect and allow me to connect to the router. Did full restart and system automatically reconnected with router. :)

Thank you so much :)

Where can I learn more about ubuntu and coding so I can help users in the future?

---

### Post by chili555 on 2012-04-16
> **zdeuyo said:**
> OMG it worked :) ...this disabled the offending driver which I believe is the default for ubuntu. This allowed the process to connect and allow me to connect to the router. Did full restart and system automatically reconnected with router. :)

Thank you so much :)

Where can I learn more about ubuntu and coding so I can help users in the future?I'm glad it's working! Have fun!

I am sure there are books but I just read the forums and examine my test system, an older laptop with nothing too crucial on it. If I make a mistake, I can reinstall or otherwise without losing my essential files.

Broward County?? I hearda that place. I spent quite a few years in Boca before I moved to SC.

Would you please use thread tools at the top to Mark Solved?

---

### Post by zdeuyo on 2012-04-16
Its a very nice place...just hot :) ...SOLVED.

---

### Post by hossub on 2012-04-28
i have same problem,please help me

```
dmesg | grep iwl
rfkill list all

```
this is result:
```
[   18.893038] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.893070] iwlwifi 0000:03:00.0: setting latency timer to 64
[   18.893107] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   18.893108] iwlwifi 0000:03:00.0: pci_resource_base = f8458000
[   18.893110] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[   18.893242] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   18.893317] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   18.893422] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   18.902398] iwlwifi 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   18.902399] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[   18.902401] iwlwifi 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   18.902422] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   19.226352] iwlwifi 0000:03:00.0: loaded firmware version 17.168.5.3 build 42301
[   19.629493] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   25.325608] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   25.325783] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   25.611526] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   25.611717] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  104.726154] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = c8:6c:87:8c:44:dc tid = 0

```
and
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

now what i am must to do?

---

### Post by zdeuyo on 2012-04-28
Hello, Please send a message to chilli, he is good with wirelesss

---

### Post by chili555 on 2012-04-28
> **hossub said:**
> i have same problem,please help me



now what i am must to do?I don't see anything wrong! Let's dig deeper:```
sudo iwlist wlan0 scan
iwconfig
```Thanks.

---

### Post by divamvak on 2012-05-31
i have sthe same problem with almost the same labtop


dmesg | grep iwl
[    9.542256] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.542286] iwlwifi 0000:03:00.0: setting latency timer to 64
[    9.542324] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[    9.542325] iwlwifi 0000:03:00.0: pci_resource_base = f847c000
[    9.542327] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[    9.542451] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[    9.542554] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    9.542657] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    9.562113] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[    9.562116] iwlwifi 0000:03:00.0: Device SKU: 0X50
[    9.562118] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[    9.562127] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   10.141178] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[   10.412750] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.498878] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   16.568478] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   55.603613] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 00:26:44:3c:4c:b8 tid = 0
[   62.617925] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 00:26:44:3c:4c:b8 tid = 6

---

### Post by divamvak on 2012-05-31
i have the same problem

dmesg | grep iwl
[    9.542256] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.542286] iwlwifi 0000:03:00.0: setting latency timer to 64
[    9.542324] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[    9.542325] iwlwifi 0000:03:00.0: pci_resource_base = f847c000
[    9.542327] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[    9.542451] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[    9.542554] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    9.542657] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    9.562113] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[    9.562116] iwlwifi 0000:03:00.0: Device SKU: 0X50
[    9.562118] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[    9.562127] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   10.141178] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[   10.412750] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.498878] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   16.568478] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   55.603613] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 00:26:44:3c:4c:b8 tid = 0
[   62.617925] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 00:26:44:3c:4c:b8 tid = 6

---

### Post by chili555 on 2012-05-31
I suggest you run and post the same diagnostics I requested above.

---

### Post by divamvak on 2012-06-02
> **chili555 said:**
> I suggest you run and post the same diagnostics I requested above.
bou
that's right it was me mistake. i am newbie :).i am a new ubuntu user and i just  bought a new labtop and i am very upset because of this problem.

---

### Post by chili555 on 2012-06-02
> **divamvak said:**
> bou
that's right it was me mistake. i am newbie :).i am a new ubuntu user and i just  bought a new labtop and i am very upset because of this problem.Please tell us more. What does your wireless do or not do? When you click the Network Manager icon, do you see networks? Can you click on yours and try to connect? Please open a terminal and run and post:```
rfkill list all
iwconfig
```Thanks.

You have every right to be upset if your new laptop doesn't work properly. I would be, too. Let's work together and fix it.

---

### Post by hrvooje on 2012-06-06
chili could you help me? firstly, sorry for my bad english.

i have also, lenovo Z570. rfkill list all gives

```

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

when i turn off the hardware switch on the front side of the laptop

```

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

when i press Fn+F5 it shows

```

0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

sudo rfkill ubblock all gives

```

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```



i wonder what does this phy0 mean? it is always blocked.

i have read about acer_wmi module and i see it, it is loaded but it shuoldnt be. 

```

acer_wmi               23612  0 
sparse_keymap          13658  2 ideapad_laptop,acer_wmi
wmi                    18744  2 acer_wmi,mxm_wmi

```

another problem is that in my network settings i cant turn off the airplane mode. 

i have found on the internet that someone had to install windows to activate the wifi card?! another say that the driver iwlwifi should be downgraded? 

*i am now on mint, but it's the same problem i had on ubuntu. please help me!

---

### Post by divamvak on 2012-06-06
> **chili555 said:**
> Please tell us more. What does your wireless do or not do? When you click the Network Manager icon, do you see networks? Can you click on yours and try to connect? Please open a terminal and run and post:```
rfkill list all
iwconfig
```Thanks.

You have every right to be upset if your new laptop doesn't work properly. I would be, too. Let's work together and fix it.

my wifi seems works fine. but the speed is very slow. when i connect to ethernet the speed is normal.


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by chili555 on 2012-06-06
> i have read about acer_wmi module and i see it, it is loaded but it shuoldnt be.

Code:

acer_wmi               23612  0 
sparse_keymap          13658  2 ideapad_laptop,acer_wmi
wmi                    18744  2 acer_wmi,mxm_wmi

another problem is that in my network settings i cant turn off the airplane mode.
Please try this:```
sudo modprobe -r acer-wmi
sudo rfkill unblock all
rfkill list all
```Any improvement? If so,we'll tweak one file to make it permanent.

---

### Post by chili555 on 2012-06-06
> **divamvak said:**
> my wifi seems works fine. but the speed is very slow. when i connect to ethernet the speed is normal.Please run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by divamvak on 2012-06-06
> **chili555 said:**
> please run and post:```
lspci -nn | grep 0280
```thanks.
Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree

Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's

Other options:
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file

---

### Post by divamvak on 2012-06-06
> **divamvak said:**
> basic display modes:
-mm		produce machine-readable output (single -m for an obsolete format)
-t		show bus tree

display options:
-v		be verbose (-vv for very verbose)
-k		show kernel drivers handling each device
-x		show hex-dump of the standard part of the config space
-xxx		show hex-dump of the whole config space (dangerous; root only)
-xxxx		show hex-dump of the 4096-byte extended config space (root only)
-b		bus-centric view (addresses and irq's as seen by the bus)
-d		always show domain numbers

resolving of device id's to names:
-n		show numeric id's
-nn		show both textual and numeric id's (names & numbers)
-q		query the pci id database for unknown id's via dns
-qq		as above, but re-query locally cached entries
-q		query the pci id database for all id's via dns

selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	show only devices in selected slots
-d [<vendor>]:[<device>]			show only devices with specified id's

other options:
-i <file>	use specified id database instead of /usr/share/misc/pci.ids.gz
-p <file>	look up kernel modules in a given file instead of default modules.pcimap
-m		enable `bus mapping' mode (dangerous; root only)

pci access options:
-a <method>	use the specified pci access method (see `-a help' for a list)
-o <par>=<val>	set pci access parameter (see `-o help' for a list)
-g		enable pci access debugging
-h <mode>	use direct hardware access (<mode> = 1 or 2)
-f <file>	read pci configuration dump from a given file

i also understood that i have this probem only in wep wifi

---

### Post by chili555 on 2012-06-06
You've made a typing error. Please try again:```
lspci -nn | grep 0280
```That's lower-case for LSPCI and then a space -NN then the pipe symbol | which is on the right side of my US keyboard on the same key with \; followed by 0280. It should give a description of your exact wireless device, like this:```
chili@LAPTOP60:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
```Of course, your device is probably different.

Please try again.

---

### Post by divamvak on 2012-06-07
> **chili555 said:**
> You've made a typing error. Please try again:```
lspci -nn | grep 0280
```That's lower-case for LSPCI and then a space -NN then the pipe symbol | which is on the right side of my US keyboard on the same key with \; followed by 0280. It should give a description of your exact wireless device, like this:```
chili@LAPTOP60:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
```Of course, your device is probably different.

Please try again.

sorry i thought that | was /.
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]

---

### Post by chili555 on 2012-06-07
Please try this:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Is it a bit faster now? If so, we'll write one quick file and make it permanent.

---

### Post by hrvooje on 2012-06-08
> **chili555 said:**
> Please try this:```
sudo modprobe -r acer-wmi
sudo rfkill unblock all
rfkill list all
```Any improvement? If so,we'll tweak one file to make it permanent.

after those commands phy0 is still hard blocked:

```

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

the switch on the front side of the laptop is on. after i pressed Fn+F5, only wlan and phy0 is soft blocked.

```

0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```

then i pressed it once more and only phy0 hard blocked stays

```

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

my card is:
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]

---

### Post by divamvak on 2012-06-09
> **chili555 said:**
> Please try this:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Is it a bit faster now? If so, we'll write one quick file and make it permanent.
yes it seems to be a bit faster

---

### Post by chili555 on 2012-06-09
> **divamvak said:**
> yes it seems to be a bit fasterLet's make it permanent. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```A new empty file will open. Add just one line:```
options iwlwifi 11n_disable=1 
```Proofread, save and close gedit. Now unload and reload the driver:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```Is the wireless now working as expected?

---

### Post by divamvak on 2012-06-14
> **chili555 said:**
> Let's make it permanent. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```A new empty file will open. Add just one line:```
options iwlwifi 11n_disable=1 
```Proofread, save and close gedit. Now unload and reload the driver:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```Is the wireless now working as expected?

i turned the wifi from wep to wpa and now everything works fine.thanx a lot

---

### Post by pacchiee on 2012-06-20
I have problems in connecting wireless using Ubuntu 12.04 on my Lenovo Laptop.

Read this thread and here are my outputs:

dmesg | grep wlan
```
[   34.756425] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

route -n
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:9c:2e:1d  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe9c:2e1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6483567 (6.4 MB)  TX bytes:830440 (830.4 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:137555 (137.5 KB)  TX bytes:137555 (137.5 KB)
```

rfkill list all
```
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

Please help me.

---

### Post by chili555 on 2012-06-21
> **pacchiee said:**
> I have problems in connecting wireless using Ubuntu 12.04 on my Lenovo Laptop.

Read this thread and here are my outputs:

Please help me.Please post:```
lspci -nn | grep 0280

```Thanks.

---

### Post by pacchiee on 2012-06-21
lspci -nn | grep 0280

```
03:00.0 Network controller [0280] : Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```

---

### Post by chili555 on 2012-06-21
> I have problems in connecting wireless using Ubuntu 12.04 on my Lenovo Laptop.Does it see your network? Does it try to connect? Are you asked for the encryption key?

Now may we have a look at:```
dmesg | grep b43
sudo cat /var/log/syslog | grep wlan
```Thanks.

---

### Post by pacchiee on 2012-06-21
> **chili555 said:**
> Does it see your network? Does it try to connect? Are you asked for the encryption key?

No! It fails to see my wireless network. So it cannot connect and hence doesn't ask for encryption key for authentication.

> 
Now may we have a look at:
dmesg | grep b43
sudo cat /var/log/syslog | grep wlan


dmesg | grep b43 => returned nothing.

cat /var/log/syslog | grep wlan
```
root@lappie:/home/me# cat /var/log/syslog | grep wlan
Jun 19 20:32:06 lappie NetworkManager[765]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jun 19 20:32:06 lappie NetworkManager[765]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 19 20:32:06 lappie NetworkManager[765]: <info> (wlan0): using nl80211 for WiFi device control
Jun 19 20:32:06 lappie NetworkManager[765]: <warn> (wlan0): driver supports Access Point (AP) mode
Jun 19 20:32:06 lappie NetworkManager[765]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jun 19 20:32:06 lappie NetworkManager[765]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 19 20:32:06 lappie NetworkManager[765]: <info> (wlan0): now managed
Jun 19 20:32:06 lappie NetworkManager[765]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 19 20:32:06 lappie NetworkManager[765]: <info> (wlan0): bringing up device.
Jun 19 20:32:06 lappie kernel: [   14.667992] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 20:32:06 lappie NetworkManager[765]: <warn> (wlan0): firmware may be missing.
Jun 19 20:32:06 lappie NetworkManager[765]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 20 20:46:02 lappie NetworkManager[715]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jun 20 20:46:02 lappie NetworkManager[715]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 20 20:46:02 lappie NetworkManager[715]: <info> (wlan0): using nl80211 for WiFi device control
Jun 20 20:46:02 lappie NetworkManager[715]: <warn> (wlan0): driver supports Access Point (AP) mode
Jun 20 20:46:02 lappie NetworkManager[715]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jun 20 20:46:02 lappie NetworkManager[715]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 20 20:46:02 lappie NetworkManager[715]: <info> (wlan0): now managed
Jun 20 20:46:02 lappie NetworkManager[715]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 20 20:46:02 lappie NetworkManager[715]: <info> (wlan0): bringing up device.
Jun 20 20:46:02 lappie NetworkManager[715]: <warn> (wlan0): firmware may be missing.
Jun 20 20:46:02 lappie NetworkManager[715]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 20 20:46:02 lappie kernel: [   13.898635] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 21 07:46:26 lappie NetworkManager[726]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jun 21 07:46:26 lappie NetworkManager[726]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 21 07:46:26 lappie NetworkManager[726]: <info> (wlan0): using nl80211 for WiFi device control
Jun 21 07:46:26 lappie NetworkManager[726]: <warn> (wlan0): driver supports Access Point (AP) mode
Jun 21 07:46:26 lappie NetworkManager[726]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jun 21 07:46:26 lappie NetworkManager[726]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 21 07:46:26 lappie NetworkManager[726]: <info> (wlan0): now managed
Jun 21 07:46:26 lappie NetworkManager[726]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 21 07:46:26 lappie NetworkManager[726]: <info> (wlan0): bringing up device.
Jun 21 07:46:26 lappie kernel: [   13.931238] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 21 07:46:26 lappie NetworkManager[726]: <warn> (wlan0): firmware may be missing.
Jun 21 07:46:26 lappie NetworkManager[726]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 21 07:52:25 lappie NetworkManager[731]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jun 21 07:52:25 lappie NetworkManager[731]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 21 07:52:25 lappie NetworkManager[731]: <info> (wlan0): using nl80211 for WiFi device control
Jun 21 07:52:25 lappie NetworkManager[731]: <warn> (wlan0): driver supports Access Point (AP) mode
Jun 21 07:52:25 lappie NetworkManager[731]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jun 21 07:52:25 lappie NetworkManager[731]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 21 07:52:25 lappie NetworkManager[731]: <info> (wlan0): now managed
Jun 21 07:52:25 lappie NetworkManager[731]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 21 07:52:25 lappie NetworkManager[731]: <info> (wlan0): bringing up device.
Jun 21 07:52:25 lappie NetworkManager[731]: <warn> (wlan0): firmware may be missing.
Jun 21 07:52:25 lappie NetworkManager[731]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 21 07:52:25 lappie kernel: [   13.985969] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 21 18:43:20 lappie NetworkManager[714]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jun 21 18:43:20 lappie NetworkManager[714]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 21 18:43:20 lappie NetworkManager[714]: <info> (wlan0): using nl80211 for WiFi device control
Jun 21 18:43:20 lappie NetworkManager[714]: <warn> (wlan0): driver supports Access Point (AP) mode
Jun 21 18:43:20 lappie NetworkManager[714]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jun 21 18:43:20 lappie NetworkManager[714]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 21 18:43:20 lappie NetworkManager[714]: <info> (wlan0): now managed
Jun 21 18:43:20 lappie NetworkManager[714]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 21 18:43:20 lappie NetworkManager[714]: <info> (wlan0): bringing up device.
Jun 21 18:43:21 lappie NetworkManager[714]: <warn> (wlan0): firmware may be missing.
Jun 21 18:43:21 lappie NetworkManager[714]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 21 18:43:21 lappie kernel: [   14.119628] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 21 18:44:05 lappie NetworkManager[714]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jun 21 18:44:05 lappie NetworkManager[714]: <info> (wlan0): now unmanaged
Jun 21 18:44:05 lappie NetworkManager[714]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]

```

---

### Post by chili555 on 2012-06-21
> <warn> (wlan0): firmware may be missing.Interesting. Please let us see:```
ls /lib/firmware/b43
```If there is no such directory, then the firmware is indeed missing. Let's install it with:```
sudo apt-get install linux-firmware-nonfree
```Then do:```
sudo modprobe b43
dmesg | grep b43
```Thanks.

---

### Post by pacchiee on 2012-06-21
ls /lib/firmware/b43
```
root@lappie:/home/me# ls /lib/firmware/b43
ls: cannot access /lib/firmware/b43: No such file or directory
```

apt-get install linux-firmware-nonfree
```
root@lappie:/home/me# apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 3,947 kB of archives.
After this operation, 8,962 kB of additional disk space will be used.
Get:1 http://in.archive.ubuntu.com/ubuntu/ precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu1 [3,947 kB]
Fetched 3,947 kB in 19s (204 kB/s)                                                                                                                          
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 158258 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.11ubuntu1_all.deb) ...
Setting up linux-firmware-nonfree (1.11ubuntu1) ...
```

modprobe b43
dmesg | grep b43
```
root@lappie:/home/me# modprobe b43
root@lappie:/home/me# dmesg | grep b43
[ 2535.745152] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[ 2536.075878] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[ 2536.267939] Registered led device: b43-phy0::tx
[ 2536.268052] Registered led device: b43-phy0::rx
[ 2536.268129] Registered led device: b43-phy0::radio
[ 2536.720226] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
```

WOW.. Great, it works!!!

Ubuntu now detects my wireless network, asks for encryption key and successfully connects.

Now, am replying through my wireless network!

Thanks so much chili555. You are the real "MASTER" :)

---

### Post by chili555 on 2012-06-21
> Now, am replying through my wireless network!I was happy to have helped and I'm glad it's working. Have fun!

---

### Post by phantomxter on 2012-06-21
Hello, I also have a Lenovo IdeaPad and having wireless issues. 
Got the AMD 64 bit with Windows7 doing dual boot option. 
Just installed Ubuntu Studio and wired network works just fine. 
I made sure to select wlan0 at set up for default, but no matter what I try it doesn't want to work. I have also beed reading through the forums all day with no luck. 

dmesg | grep iwl

returns nothing

~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)                  

~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



Thanks for any input

---

### Post by chili555 on 2012-06-21
> dmesg | grep iwl

returns nothingSince you don't have an Intel wireless card, let's try this:```
sudo modprobe ath9k
dmesg | grep ath
```Thanks.

---

### Post by phantomxter on 2012-06-21
> **chili555 said:**
> Since you don't have an Intel wireless card, let's try this:```
sudo modprobe ath9k
dmesg | grep ath
```Thanks.
Thanks for the fast reply. 

sudo modprobe ath9k
returns nothing

~$ dmesg | grep ath
[    9.199795] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.199821] ath9k 0000:03:00.0: setting latency timer to 64
[    9.250737] ath: EEPROM regdomain: 0x65
[    9.250744] ath: EEPROM indicates we should expect a direct regpair map
[    9.250754] ath: Country alpha2 being used: 00
[    9.250758] ath: Regpair used: 0x65
[    9.576509] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    9.578125] Registered led device: ath9k-phy0
[ 1839.824276] Modules linked in: fglrx(P) b43 ssb bnep rfcomm bluetooth parport_pc ppdev snd_hda_codec_conexant snd_hda_intel snd_hda_codec snd_hwdep sp5100_tco snd_pcm snd_seq_midi joydev snd_rawmidi snd_seq_midi_event snd_seq arc4 snd_timer snd_seq_device uvcvideo videodev ath9k mac80211 ath9k_common ath9k_hw ath v4l2_compat_ioctl32 cfg80211 snd psmouse serio_raw soundcore snd_page_alloc k10temp i2c_piix4 radeon ideapad_laptop sparse_keymap ttm drm_kms_helper drm video i2c_algo_bit lp parport atl1c ahci libahci
[ 1839.824409]  <IRQ>  [<ffffffff8105e83f>] warn_slowpath_common+0x7f/0xc0
[ 1839.824445]  [<ffffffff8105e936>] warn_slowpath_fmt+0x46/0x50

---

### Post by chili555 on 2012-06-21
> Modules linked in: fglrx(P) [COLOR="Red"]b43 ssb[/COLOR] bnep rfcomm <snip>Whaaaa...?? Let's see: ```
cat /etc/modules
```I have no idea why b43 and ssb, drivers for Broadcom cards, would load for your Atheros. Did you or do you have another card?

---

### Post by phantomxter on 2012-06-21
> **chili555 said:**
> Whaaaa...?? Let's see: ```
cat /etc/modules
```I have no idea why b43 and ssb, drivers for Broadcom cards, would load for your Atheros. Did you or do you have another card?

I bought this laptop second hand. I haven't installed or changed anything other than installing Ubuntu Studio. 
At setup, there were only two options in networking.  etho1, which I figured was RJ45 and the wlan0-wireless.  I selected wireless as default. 

~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc

---

### Post by chili555 on 2012-06-21
Let's dig a bit deeper before we take further steps:```
dmesg | grep -e b43 -e ssb
lspci -nn | grep 0200
```Thanks.

---

### Post by phantomxter on 2012-06-21
> **chili555 said:**
> Let's dig a bit deeper before we take further steps:```
dmesg | grep -e b43 -e ssb
lspci -nn | grep 0200
```Thanks.

~$ dmesg | grep -e b43 -e ssb
[ 1839.824276] Modules linked in: fglrx(P) b43 ssb bnep rfcomm bluetooth parport_pc ppdev snd_hda_codec_conexant snd_hda_intel snd_hda_codec snd_hwdep sp5100_tco snd_pcm snd_seq_midi joydev snd_rawmidi snd_seq_midi_event snd_seq arc4 snd_timer snd_seq_device uvcvideo videodev ath9k mac80211 ath9k_common ath9k_hw ath v4l2_compat_ioctl32 cfg80211 snd psmouse serio_raw soundcore snd_page_alloc k10temp i2c_piix4 radeon ideapad_laptop sparse_keymap ttm drm_kms_helper drm video i2c_algo_bit lp parport atl1c ahci libahci


~$ lspci -nn | grep 0200
02:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)

---

### Post by chili555 on 2012-06-21
Nothing startling there; let's assume it is an anomaly for now. Your readings look pretty solid. Now let us see:```
sudo iwlist wlan0 scan
dmesg | grep wlan
```Thanks.

---

### Post by phantomxter on 2012-06-21
> **chili555 said:**
> Nothing startling there; let's assume it is an anomaly for now. Your readings look pretty solid. Now let us see:```
sudo iwlist wlan0 scan
dmesg | grep wlan
```Thanks.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:1E:98:BD
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:off
                    ESSID:"ubuntu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000020d12c18a
                    Extra: Last beacon: 536ms ago
                    IE: Unknown: 00067562756E7475
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010000


~$ dmesg | grep wlan
[   15.821953] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.812244] wlan0: authenticate with 00:13:10:1e:98:bd (try 1)
[   16.814361] wlan0: authenticated
[   16.814453] wlan0: associate with 00:13:10:1e:98:bd (try 1)
[   16.816955] wlan0: RX AssocResp from 00:13:10:1e:98:bd (capab=0x401 status=0 aid=3)
[   16.816966] wlan0: associated
[   16.817931] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.040039] wlan0: no IPv6 routers present

---

### Post by chili555 on 2012-06-21
> [ 16.814361] wlan0: authenticated
[ 16.814453] wlan0: associate with 00:13:10:1e:98:bd (try 1)
[ 16.816955] wlan0: RX AssocResp from 00:13:10:1e:98:bd (capab=0x401 status=0 aid=3)
[ 16.816966] [COLOR="Red"]wlan0: associated[/COLOR]Looks to me like you are or at least were connected. With the ethernet cable detached, what happens or doesn't happen as expected?

---

### Post by phantomxter on 2012-06-21
> **chili555 said:**
> Looks to me like you are or at least were connected. With the ethernet cable detached, what happens or doesn't happen as expected?

This is a fresh install done today.  I installed with no ethernet cable attached. 
When Ubuntu boots, it hangs waiting on network, then waits another up to 60 secs.
Then once running, wireless doesn't auto start and when I added wireless in network connections it still doesn't connect and is showing last used, never. 
So when i connect ethernet cable it almost instantly connects and that's how I'm online now.  If/when I remove ethernet cable I lose connection and wireless doesn't start. Even when I restart machine.  
Bottom line is, no wireless. But ethernet to same router works fine. 
I have no security enabled at router side.  
If I boot into Windows 7, same machine, wireless works fine.

---

### Post by chili555 on 2012-06-21
Please reboot with the ethernet detached so we have a clean slate and can see the behavior. Open a terminal and run:```
dmesg > phantom.txt
```Find the file phantom.txt in yor user directory and paste it here and give us the link in your reply. We'll try to see what's going wrong.

I will be off for the evening, so I'll check in tomorrow.

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by phantomxter on 2012-06-21
> **chili555 said:**
> Please reboot with the ethernet detached so we have a clean slate and can see the behavior. Open a terminal and run:```
dmesg > phantom.txt
```Find the file phantom.txt in yor user directory and paste it here and give us the link in your reply. We'll try to see what's going wrong.

I will be off for the evening, so I'll check in tomorrow.

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Ok, will do.  Just to update, I checked router local network and I do see where my wireless card's MAC did obtain an IP.  But either way, programs such as skype and firefox are not working.  I will continue to try and locate the problem.  Thanks for your help so far.

---

### Post by chili555 on 2012-06-22
> **phantomxter said:**
> Ok, will do.  Just to update, I checked router local network and I do see where my wireless card's MAC did obtain an IP.  But either way, programs such as skype and firefox are not working.  I will continue to try and locate the problem.  Thanks for your help so far.So, did you? What is the link?

---

### Post by phantomxter on 2012-06-22
No, sorry. I got the file but deleted the partition before I pasted it.  
I removed ethernet cable and restart and the wireless worked.  But then after another restart it didn't. 
By then I figured it had to be a Ubuntu Studio 12.04 LTS issue so I booted from a USB drive where I have easypeasy installed. Wireless worked just fine.  So I found XBMCbuntu and thought I'd try it. 
Was easy and fast install and wireless worked well.  Not sure why but must have been something with Studio.  Thank you very much for your help & input.

---

### Post by hrvooje on 2012-07-25
I found the solution! it is called ZorinOS. On ZorinOS 6 wifi on this lenovo works out of box. ZorinOS is based on Ubuntu.

Me happy :)

---

### Post by Lupajz on 2012-07-26
I don't know but wifi worked for me with 12.04 out of the box :)

I have z570 also :) But only with i5 processor :P 

Also i got this dkms for fan controll button, but havent tried it yet on my z570 as I am on vacation.

Anybody willing to do so ? 

```
http://kernel.ubuntu.com/~ikepanhc/ideapad/ideapad-laptop-dkms_3.6_all.deb
```

---

### Post by chili555 on 2012-07-26
> **Lupajz said:**
> I don't know but wifi worked for me with 12.04 out of the box :)

I have z570 also :) But only with i5 processor :P 

Also i got this dkms for fan controll button, but havent tried it yet on my z570 as I am on vacation.

Anybody willing to do so ? 

```
http://kernel.ubuntu.com/~ikepanhc/ideapad/ideapad-laptop-dkms_3.6_all.deb
```I think your question belongs in General Help, not Networking since it involves fan control.

---

### Post by gongdiddle on 2012-08-03
Worked for me!
It's been a while since I've had any problems with an Ubuntu install, basically none since 8.04. I think my older laptop's ('optima' with Intel Core 2 Duo CPU P7370) wireless card might be becoming a weak link. 
 ```
lspci -nn | grep 0280
```
listed: Intel Corporation WiFi Link 5100 [8086:4232]. FWIW, the card worked fine with the 11.10 install, and the fresh (no upgrade) 12.04 install wouldn't even complete until I opted for no updates or network connectivity, I imagine due to this. After installed, I noticed I could see my wireless network, selected it, entered my credentials, and though it indicated it was connected, no sites would load, nor updates complete. When I tried a wired connection there was no problem so I updated the system and enabled some proprietary modem driver in hopes that the subsequent restart would fix the wireless connectivity. I found that though it again showed a successful connection there was none.

I looked at quite a few threads till I found this one, which seemed to focus on Intel hardware as opposed to the more commonly found Broadcom issues. I also found the depth of Chili's knowledge reassuring. After the solutions for the anomalous Acer driver I found someone (divamvak) listed their hardware as "Intel Corporation Centrino Wireless-N 1000 [8086:0084]", and noted Chili's proposed solution in comment 27.
After running:
```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```
the wireless was operational! So I added "options iwlwifi 11n_disable=1" to the newly created /etc/modprobe.d/iwlwifi.conf file as suggested, and entered:
```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```
I've tested the persistence of this solution with a couple boots and so far so good. Can't say I know entirely what I did though; perhaps disabled wireless n and stepped back to g? Either way my connection is great, thanks Chili, I'm so glad there are experts out there.

---

### Post by feynman forever on 2012-08-03
Hi, I'm just after upgrading from 11.10 to 12.04 on a Lenovo Z570 and my wireless isn't working, can anyone help me? I have a Broadcom BCM4313 wireless card.

Thanks a million.

---

### Post by chili555 on 2012-08-03
> **feynman forever said:**
> Hi, I'm just after upgrading from 11.10 to 12.04 on a Lenovo Z570 and my wireless isn't working, can anyone help me? I have a Broadcom BCM4313 wireless card.

Thanks a million.Please post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by feynman forever on 2012-08-04
> **chili555 said:**
> Please post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

Hi, I got

```

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

0: ideapad_wlan: Wireless LAN
      Soft blocked: no
      Hard blocked: no

```

Thanks for your quick reply! :)

---

### Post by chili555 on 2012-08-04
> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]]There is plenty of controversy about the tricky 4727. There are at least two ways to get it going and it's tough to figure out which is best. Let's try the most likely first. Please run:```
lsmod | grep -e brcmsmac -e wl
```Ideally, only brcmsmac is loaded. If wl is loaded, remove it:```
sudo modprobe -r wl
```Let's see if you have a wireless interface:```
iwconfig
```Does it scan and connect?```
sudo iwlist wlan0 scan
```

---

### Post by feynman forever on 2012-08-05
There was no output from this:
```
lsmod | grep -e brcmsmac -e wl
```
I don't think wl is there at all.

For the other commands, I got
```

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```
and
```

~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.


```

---

### Post by chili555 on 2012-08-05
Let's load the most likely driver and see if we kick this thing to life:```
sudo modprobe brcmsmac
iwconfig
```Now do we have a wireless interface? Does it scan?```
sudo iwlist wlan0 scan
```If you do not, let's see if there are informative messages here:```
dmesg | grep brcm
```

---

### Post by feynman forever on 2012-08-05
> **chili555 said:**
> Let's load the most likely driver and see if we kick this thing to life:```
sudo modprobe brcmsmac
iwconfig
```Now do we have a wireless interface? Does it scan?```
sudo iwlist wlan0 scan
```If you do not, let's see if there are informative messages here:```
dmesg | grep brcm
```
Thanks a million chili555, the wireless is now working after the modprobe  and iwconfig commands! I really appreciate this. I'd love to be able to help people on the forums, any advice on how to get better with Linux?

---

### Post by feynman forever on 2012-08-05
> **feynman forever said:**
> Thanks a million chili555, the wireless is now working after the modprobe  and iwconfig commands! I really appreciate this. I'd love to be able to help people on the forums, any advice on how to get better with Linux?

One more thing, upon restarting my machine I had to reenter these commands to get the wireless to work again. Is there a config file I can edit to make the changes permanent? Thanks for your help.

---

### Post by chili555 on 2012-08-05
First, we ought to be sure brcmsmac loads automatically:```
sudo su
echo brcmsmac >> /etc/modules
exit
```I suggest you read threads and look for problems you think you can solve. Wait before you post and see how some of the frequent thread answerers handle it. Learn from their experience.

Google the pci.id or the usb.id; for example:> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]] Google it with 'solved' and 'Ubuntu.' Copy the solution. 

Most of all, when you make a mistake, and you will if you try hard enough, admit it and apologize.

Subscribe to the threads you answer so you get an email when there is a reply. If you take on a case, carry it to completion. Feel free to PM me if you get stuck.

Have fun!

---

### Post by feynman forever on 2012-08-06
Thanks chili555, best of luck!

---

### Post by silverkitsune27 on 2012-11-06
Hi, I am also having wireless problems with my HP Pavilion DV6.  I had the same problem in Ubuntu 12.04, so I thought it was a distribution problem, so I uninstalled it and put in 12.10, which is showing the exact same behavior.

Upon system start, my wifi shows it's trying to connect, then it sees my network and asks for the key, after which it tries to connect for about 30 seconds, then asks for the key again, and keeps repeating this. Wired works perfectly fine though. Can someone (maybe chili555?) help me?


The output of the required codes are below:

ye@ubuntu:~$ lspci -nn | grep 0280
0d:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]

ye@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes

---

### Post by chili555 on 2012-11-06
> **silverkitsune27 said:**
> Hi, I am also having wireless problems with my HP Pavilion DV6.  I had the same problem in Ubuntu 12.04, so I thought it was a distribution problem, so I uninstalled it and put in 12.10, which is showing the exact same behavior.

Upon system start, my wifi shows it's trying to connect, then it sees my network and asks for the key, after which it tries to connect for about 30 seconds, then asks for the key again, and keeps repeating this. Wired works perfectly fine though. Can someone (maybe chili555?) help me?


The output of the required codes are below:

ye@ubuntu:~$ lspci -nn | grep 0280
0d:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]

ye@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yesI'll be happy to help. Please start a new thread an PM me the link.

I wonder how it even tries to connect if it's hard blocked. :confused: :confused:

---

### Post by KISLAYRAKESH on 2012-12-13
[B]Hii I am new to Ubuntu
My wireless connection worked very well on Windows and Ubuntu 9.04
But it is not working now.
Tried the codes given on the forum. [/B]

rakesh@rakesh-C-Notebook-XXXX:~$** lspci -nn | grep 0280**
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
rakesh@rakesh-C-Notebook-XXXX:~$ **rfkill list all**
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
rakesh@rakesh-C-Notebook-XXXX:~$ **lsmod | grep -e brcmsmac -e wl**
wl                   2646601  0 
lib80211               14040  1 wl
rakesh@rakesh-C-Notebook-XXXX:~$ **sudo modprobe -r wl**
[sudo] password for rakesh: 
rakesh@rakesh-C-Notebook-XXXX:~$** lsmod | grep -e brcmsmac -e wl**
**(showed nothing)**
rakesh@rakesh-C-Notebook-XXXX:~$** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

rakesh@rakesh-C-Notebook-XXXX:~$ **sudo iwlist wlan0 scan**
wlan0     Interface doesn't support scanning.

rakesh@rakesh-C-Notebook-XXXX:~$[B] sudo modprobe brcmsmac
(showed nothing)
[/B]rakesh@rakesh-C-Notebook-XXXX:~$ 

[B]I can only connect through ethernet cable. 
Please help me so that I dont have to shift back to Windows.[/B]

---

### Post by KISLAYRAKESH on 2012-12-13
I am using **Ubuntu 12.04 LTE **now.

---

### Post by chili555 on 2012-12-14
> **KISLAYRAKESH said:**
> I am using **Ubuntu 12.04 LTE **now.Please refer to your own thread where I answered.

---

### Post by KISLAYRAKESH on 2012-12-14
> **chili555 said:**
> Please refer to your own thread where I answered.
Thanks for quick response. It did not work. 
I tried the codes that you recommended.
sudo apt-get remove --purge bcmwl-kernel-source sudo apt-get install linux-firmware-nonfree sudo modprobe b43 
this is what I got.
rakesh@rakesh-C-Notebook-XXXX:~$ [B]sudo apt-get remove --purge bcmwl-kernel-source
[/B][sudo] password for rakesh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,252 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 170903 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic-pae

rakesh@rakesh-C-Notebook-XXXX:~$** sudo apt-get install linux-firmware-nonfree**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

rakesh@rakesh-C-Notebook-XXXX:~$ **sudo modprobe b43**
**(showed nothing)**
rakesh@rakesh-C-Notebook-XXXX:~$ 

Please Help.

---

### Post by chili555 on 2012-12-14
> Please Help.Sir or madam: I am answering in your own thread and not here. I am not going to answer every question twice and you needn't ask twice.

---

### Post by bingtian on 2013-02-18
Hi, chili555,

I have a very strange problem with my acer aspire 3750G. I have two routers at home, it can connect to one router (belkin), but not the other (huawei), could you please help me see if there's anything wrong with my wireless?

```

bingtian@aspire3750G:~$ dmesg | grep iwl
bingtian@aspire3750G:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```Does the sequence matter? original order was 1,2,0,3, but i did some modprobe, and but acer-wsi in blacklist once.

```

bingtian@aspire3750G:~$ lsmod | grep acer
acer_wmi               28418  0
sparse_keymap          13890  1 acer_wmi
wmi                    19256  2 acer_wmi,mxm_wmi
bingtian@aspire3750G:~$ dmesg | grep ath
[   57.880056] ath9k 0000:0d:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   57.880071] ath9k 0000:0d:00.0: setting latency timer to 64
[   57.969810] ath: EEPROM regdomain: 0x65
[   57.969812] ath: EEPROM indicates we should expect a direct regpair map
[   57.969814] ath: Country alpha2 being used: 00
[   57.969816] ath: Regpair used: 0x65
[   57.973062] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   57.973458] Registered led device: ath9k-phy0
[   58.126080] usbcore: registered new interface driver ath3k

```Is there any problem? Thank you. I can provide more info on how the two routers are configured. Thanks.

> **chili555 said:**
> Please open a terminal and run and post:```
dmesg | grep iwl
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by chili555 on 2013-02-19
>  I can provide more info on how the two routers are configured.Please do. You might try a temporary driver parameter:```
sudo modprobe -r ath9k
sudo modprobe ath9k btcoex_enable=1
```If it helps, we can write one quick file to make it persistent.

Please post:```
nm-tool
```Tell us which two access points you are trying to connect to.

---

### Post by bingtian on 2013-02-21
Hi, chili,

Thank you so much for your reply, and sorry for the late reply as now both networks do not work for my ubuntu, so I come up online from the other computer.

The two networks are configured like this: one network is a subnet of the other. I name the larger one CO and the subnet ES, they are connected through home plug: ES's uplink is from CO LAN port. CO is configured with 192.168.64.* (gateway at 192.168.64.1, mask 255.255.240.0), ES is configured with 192.168.66.* (gateway at 192.168.66.1, mask 255.255.255.0). So the gateway for ES router is set at 192.168.64.1. This configuration works, as my notebook connect to ES in the bedroom and connects to CO at the living room.

So I paste the outcome after doing "modprobe -r ath9k" and "modprobe ath9k btcoex_enable=1", for CO first, then ES.

```

bingtian@aspire3750G:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e0:69:95:2a:04:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:50 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:153869 (153.8 KB)  TX bytes:153869 (153.8 KB)

wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:a2:ac:b1  
          inet addr:192.168.64.31  Bcast:192.168.79.255  Mask:255.255.240.0
          inet6 addr: fe80::8a9f:faff:fea2:acb1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16353 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29281747 (29.2 MB)  TX bytes:1778517 (1.7 MB)

bingtian@aspire3750G:~$ ping 192.168.64.1
PING 192.168.64.1 (192.168.64.1) 56(84) bytes of data.
^C
--- 192.168.64.1 ping statistics ---
19 packets transmitted, 0 received, 100% packet loss, time 18143ms

bingtian@aspire3750G:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [CO] -----------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        88:9F:FA:A2:AC:B1

  Capabilities:
    Speed:           13 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  IPv4 Settings:
    Address:         192.168.64.31
    Prefix:          20 (255.255.240.0)
    Gateway:         192.168.64.1

    DNS:             192.168.64.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        E0:69:95:2A:04:68

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

I have IP but cannot even ping the gateway, which is very strange. Now I disconnect CO and connect to ES

```

bingtian@aspire3750G:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e0:69:95:2a:04:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:50 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:260111 (260.1 KB)  TX bytes:260111 (260.1 KB)

wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:a2:ac:b1  
          inet addr:192.168.66.84  Bcast:192.168.66.255  Mask:255.255.255.0
          inet6 addr: 2002:c0a8:4002:1234:8a9f:faff:fea2:acb1/64 Scope:Global
          inet6 addr: fe80::8a9f:faff:fea2:acb1/64 Scope:Link
          inet6 addr: 2002:c0a8:4002:1234:5df7:a9a4:e7f9:6781/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5120 (5.1 KB)  TX bytes:17861 (17.8 KB)

bingtian@aspire3750G:~$ ping 192.168.66.1
PING 192.168.66.1 (192.168.66.1) 56(84) bytes of data.
64 bytes from 192.168.66.1: icmp_req=1 ttl=64 time=126 ms
64 bytes from 192.168.66.1: icmp_req=2 ttl=64 time=26.9 ms
^C
--- 192.168.66.1 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2002ms
rtt min/avg/max/mdev = 26.975/76.915/126.856/49.941 ms
bingtian@aspire3750G:~$ nm-tool 

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ES] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        88:9F:FA:A2:AC:B1

  Capabilities:
    Speed:           243 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  IPv4 Settings:
    Address:         192.168.66.84
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.66.1

    DNS:             192.168.66.1
    DNS:             192.168.64.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        E0:69:95:2A:04:68

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

Please advise, thank you!

---

### Post by chili555 on 2013-02-21
I don't think you have a wireless card problem at all. I think you have a gateway, subnet, too-many-routers problem. I don't know how to fix this:> wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:a2:ac:b1  
          inet addr:192.168.[COLOR="Red"]64[/COLOR].31  Bcast:192.168.[COLOR="Red"]79[/COLOR].255  Mask:255.255.[COLOR="Red"]240[/COLOR].0
          inet6 addr: fe80::8a9f:faff:fea2:acb1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          It may be solvable and it may be fine but I just am inexperienced in such complications. I suggest you start your own new thread and refer to your setup in detail and ask for an answer. I don't have it.

I wish I could be of more help.

---

### Post by bingtian on 2013-02-21
Hi, chili, thank you for your answer, I suspect it's the router problem too, but windows and androids are fine with the setting since Bcast:192.168.[COLOR=Red]79[/COLOR].255 (11000000.10101000.01001111.11111111) & Mask:255.255.[COLOR=Red]240[/COLOR].0 (11111111.11111111.11110000.00000000) = subnet:192.168.[COLOR=Red]64[/COLOR].0 (11000000.10101000.01000000.0)

---

### Post by ViliX64 on 2013-03-09
Hi, I have problem with my wifi connection too. When I try to connect to  my wifi, it writes: "Wireless connection established", but when I try  to load a page in default browser, it says: "Server not found".
I'm using Xubuntu 12.10 and before i had installed Windows 8 and the wifi worked fine.
(I have Asus-X201E-kx006h)
I've run some diagnostic:
```

vilix@vilix-X201EP:~$ sudo ufw status
[sudo] password for vilix: 
Status: inactive

```

```

vilix@vilix-X201EP:~$ dmesg | grep iwl
vilix@vilix-X201EP:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```

vilix@vilix-X201EP:~$ iwconfig
lo        no wireless extensions.
wlan0   IEEE 802.11bgn  ESSID:"Wifinka"
          Mode:Managed  Frequency:2.462 GHz  Access Point: C8:6C:87:F3:D2:E0
          Bit Rate=13.5 Mb/s   Tx-Power=16 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

vilix@vilix-X201EP:~$ lsmod | grep asus 
asus_nb_wmi        12710      0
asus_wmi             24088      1  asus_nb_wmi
sparse_keymap      13890      1  asus_wmi   
wmi                     19070      1  asus_wmi

```

Thank you for every help..

---

### Post by chili555 on 2013-03-09
> **ViliX64 said:**
> Hi, I have problem with my wifi connection too. When I try to connect to  my wifi, it writes: "Wireless connection established", but when I try  to load a page in default browser, it says: "Server not found".
I'm using Xubuntu 12.10 and before i had installed Windows 8 and the wifi worked fine.
(I have Asus-X201E-kx006h)
.We would also love to see:```
iwconfig
lspci -nn | grep 0280
```Thanks.

---

### Post by ViliX64 on 2013-03-09
Here it is:

```

vilix@vilix-X201EP:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Wifinka"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: C8:6C:87:F3:D2:E0   
          Bit Rate=108 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vilix@vilix-X201EP:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)

```

---

### Post by chili555 on 2013-03-09
> wlan0     IEEE 802.11bgn  ESSID:"Wifinka"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: C8:6C:87:F3:D2:E0   
          Bit Rate=[COLOR="#FF0000"]108 Mb/s [/COLOR]  Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:offWoo hoo!

I fear this is an N speed issue. I know N is the future but I also know realistically that many Linux drivers are troubled with N. Can you experimentally turn off N in the router and let us have your report? Please see attached. In this example, I'd set 802.11-n-mode to OFF.

---

### Post by ViliX64 on 2013-03-09
Thank you! It works.. I have switched from 802.11b+g+n to 802.11b+g.
Thank you very much again!

---

### Post by chili555 on 2013-03-09
> **ViliX64 said:**
> Thank you! It works.. I have switched from 802.11b+g+n to 802.11b+g.
Thank you very much again!Awesome! I'm glad it's working. I am sorry, however, that my N fears are confirmed in the case of ath9k.

---

### Post by samyakd on 2013-07-07
Hi chili,
Hp laptop. 12.04 UEFI. No wireless. 
dmesg | grep iwl doesnt show anything.
rfkill list all shows : 
0: hp-wifi: Wireless LAN
             Soft Blocked: no
             Hard Blocked: no
1: hp-bluetooth: Bluetooth
             Soft Blocked: no
             Hard Blocked: no


I dont know why but I think its because of a bug in the way UEFI works with ubuntu. But i know i'm just being skeptical here. Thanks in advance.! 
            
dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-23-generic (buildd@komainu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 (Ubuntu 3.5.0-23.35~precise1-generic 3.5.7.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=c7b593da-4cd1-404e-af34-04a70c23847a ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000087fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000088000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000a9dbefff] usable
[    0.000000] BIOS-e820: [mem 0x00000000a9dbf000-0x00000000aaebefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000aaebf000-0x00000000aafbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000aafbf000-0x00000000aaffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000aafff000-0x00000000aaffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ab000000-0x00000000af9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffd80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000024f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by INSYDE Corp.
[    0.000000] efi:  ACPI=0xaaffe000  ACPI 2.0=0xaaffe014  SMBIOS=0xaaebef98 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x000000000006f000) (0MB)
[    0.000000] efi: mem02: type=4, attr=0xf, range=[0x000000000006f000-0x0000000000070000) (0MB)
[    0.000000] efi: mem03: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000088000) (0MB)
[    0.000000] efi: mem04: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem05: type=2, attr=0xf, range=[0x0000000000100000-0x00000000005ef000) (4MB)
[    0.000000] efi: mem06: type=7, attr=0xf, range=[0x00000000005ef000-0x0000000020000000) (506MB)
[    0.000000] efi: mem07: type=0, attr=0xf, range=[0x0000000020000000-0x0000000020200000) (2MB)
[    0.000000] efi: mem08: type=7, attr=0xf, range=[0x0000000020200000-0x0000000036246000) (352MB)
[    0.000000] efi: mem09: type=2, attr=0xf, range=[0x0000000036246000-0x0000000036248000) (0MB)
[    0.000000] efi: mem10: type=7, attr=0xf, range=[0x0000000036248000-0x000000003624a000) (0MB)
[    0.000000] efi: mem11: type=2, attr=0xf, range=[0x000000003624a000-0x000000003711d000) (14MB)
[    0.000000] efi: mem12: type=7, attr=0xf, range=[0x000000003711d000-0x0000000040004000) (142MB)
[    0.000000] efi: mem13: type=0, attr=0xf, range=[0x0000000040004000-0x0000000040005000) (0MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000040005000-0x00000000749b0000) (841MB)
[    0.000000] efi: mem15: type=2, attr=0xf, range=[0x00000000749b0000-0x000000009e3c0000) (666MB)
[    0.000000] efi: mem16: type=4, attr=0xf, range=[0x000000009e3c0000-0x000000009e3e0000) (0MB)
[    0.000000] efi: mem17: type=7, attr=0xf, range=[0x000000009e3e0000-0x00000000a09a7000) (37MB)
[    0.000000] efi: mem18: type=4, attr=0xf, range=[0x00000000a09a7000-0x00000000a13b0000) (10MB)
[    0.000000] efi: mem19: type=7, attr=0xf, range=[0x00000000a13b0000-0x00000000a15a1000) (1MB)
[    0.000000] efi: mem20: type=1, attr=0xf, range=[0x00000000a15a1000-0x00000000a15bf000) (0MB)
[    0.000000] efi: mem21: type=7, attr=0xf, range=[0x00000000a15bf000-0x00000000a6df3000) (88MB)
[    0.000000] efi: mem22: type=4, attr=0xf, range=[0x00000000a6df3000-0x00000000a7675000) (8MB)
[    0.000000] efi: mem23: type=7, attr=0xf, range=[0x00000000a7675000-0x00000000a7965000) (2MB)
[    0.000000] efi: mem24: type=4, attr=0xf, range=[0x00000000a7965000-0x00000000a79bc000) (0MB)
[    0.000000] efi: mem25: type=7, attr=0xf, range=[0x00000000a79bc000-0x00000000a79be000) (0MB)
[    0.000000] efi: mem26: type=4, attr=0xf, range=[0x00000000a79be000-0x00000000a7a0a000) (0MB)
[    0.000000] efi: mem27: type=7, attr=0xf, range=[0x00000000a7a0a000-0x00000000a7a0f000) (0MB)
[    0.000000] efi: mem28: type=4, attr=0xf, range=[0x00000000a7a0f000-0x00000000a7a16000) (0MB)
[    0.000000] efi: mem29: type=7, attr=0xf, range=[0x00000000a7a16000-0x00000000a7a17000) (0MB)
[    0.000000] efi: mem30: type=4, attr=0xf, range=[0x00000000a7a17000-0x00000000a7a41000) (0MB)
[    0.000000] efi: mem31: type=7, attr=0xf, range=[0x00000000a7a41000-0x00000000a7a42000) (0MB)
[    0.000000] efi: mem32: type=4, attr=0xf, range=[0x00000000a7a42000-0x00000000a7b83000) (1MB)
[    0.000000] efi: mem33: type=7, attr=0xf, range=[0x00000000a7b83000-0x00000000a7b86000) (0MB)
[    0.000000] efi: mem34: type=4, attr=0xf, range=[0x00000000a7b86000-0x00000000a7b8a000) (0MB)
[    0.000000] efi: mem35: type=7, attr=0xf, range=[0x00000000a7b8a000-0x00000000a7b8d000) (0MB)
[    0.000000] efi: mem36: type=4, attr=0xf, range=[0x00000000a7b8d000-0x00000000a7bd6000) (0MB)
[    0.000000] efi: mem37: type=7, attr=0xf, range=[0x00000000a7bd6000-0x00000000a7bdf000) (0MB)
[    0.000000] efi: mem38: type=4, attr=0xf, range=[0x00000000a7bdf000-0x00000000a7bff000) (0MB)
[    0.000000] efi: mem39: type=7, attr=0xf, range=[0x00000000a7bff000-0x00000000a7c0a000) (0MB)
[    0.000000] efi: mem40: type=4, attr=0xf, range=[0x00000000a7c0a000-0x00000000a7fce000) (3MB)
[    0.000000] efi: mem41: type=7, attr=0xf, range=[0x00000000a7fce000-0x00000000a7fd5000) (0MB)
[    0.000000] efi: mem42: type=4, attr=0xf, range=[0x00000000a7fd5000-0x00000000a7fee000) (0MB)
[    0.000000] efi: mem43: type=7, attr=0xf, range=[0x00000000a7fee000-0x00000000a7ff0000) (0MB)
[    0.000000] efi: mem44: type=4, attr=0xf, range=[0x00000000a7ff0000-0x00000000a7ff1000) (0MB)
[    0.000000] efi: mem45: type=7, attr=0xf, range=[0x00000000a7ff1000-0x00000000a7ff3000) (0MB)
[    0.000000] efi: mem46: type=4, attr=0xf, range=[0x00000000a7ff3000-0x00000000a95bf000) (21MB)
[    0.000000] efi: mem47: type=7, attr=0xf, range=[0x00000000a95bf000-0x00000000a9a3a000) (4MB)
[    0.000000] efi: mem48: type=2, attr=0xf, range=[0x00000000a9a3a000-0x00000000a9a3e000) (0MB)
[    0.000000] efi: mem49: type=3, attr=0xf, range=[0x00000000a9a3e000-0x00000000a9dbf000) (3MB)
[    0.000000] efi: mem50: type=5, attr=0x800000000000000f, range=[0x00000000a9dbf000-0x00000000aa1bf000) (4MB)
[    0.000000] efi: mem51: type=6, attr=0x800000000000000f, range=[0x00000000aa1bf000-0x00000000aa3bf000) (2MB)
[    0.000000] efi: mem52: type=0, attr=0xf, range=[0x00000000aa3bf000-0x00000000aaebf000) (11MB)
[    0.000000] efi: mem53: type=10, attr=0xf, range=[0x00000000aaebf000-0x00000000aafbf000) (1MB)
[    0.000000] efi: mem54: type=9, attr=0xf, range=[0x00000000aafbf000-0x00000000aafff000) (0MB)
[    0.000000] efi: mem55: type=4, attr=0xf, range=[0x00000000aafff000-0x00000000ab000000) (0MB)
[    0.000000] efi: mem56: type=7, attr=0xf, range=[0x0000000100000000-0x000000024f600000) (5366MB)
[    0.000000] efi: mem57: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem58: type=0, attr=0x0, range=[0x00000000ab000000-0x00000000afa00000) (74MB)
[    0.000000] efi: mem59: type=11, attr=0x8000000000000001, range=[0x00000000e0000000-0x00000000f0000000) (256MB)
[    0.000000] efi: mem60: type=11, attr=0x8000000000000001, range=[0x00000000feb00000-0x00000000feb04000) (0MB)
[    0.000000] efi: mem61: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem62: type=11, attr=0x8000000000000001, range=[0x00000000fed10000-0x00000000fed1a000) (0MB)
[    0.000000] efi: mem63: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem64: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem65: type=11, attr=0x8000000000000000, range=[0x00000000ffd80000-0x0000000100000000) (2MB)
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: Hewlett-Packard HP 2000 Notebook PC/1858, BIOS F.36 02/19/2013
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x24f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF8000000 write-back
[    0.000000]   3 base 0A8000000 mask FFE000000 write-back
[    0.000000]   4 base 0AA000000 mask FFF000000 write-back
[    0.000000]   5 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   6 base 100000000 mask F00000000 write-back
[    0.000000]   7 base 200000000 mask F80000000 write-back
[    0.000000]   8 base 24F600000 mask FFFE00000 uncachable
[    0.000000]   9 base 24F800000 mask FFF800000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xab000 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000082000] 82000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xaaffffff]
[    0.000000]  [mem 0x00000000-0xaaffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xaaffffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x24f5fffff]
[    0.000000]  [mem 0x100000000-0x24f5fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x24f5fffff @ [mem 0xa9a37000-0xa9a3dfff]
[    0.000000] RAMDISK: [mem 0x3624a000-0x3711cfff]
[    0.000000] ACPI: RSDP 00000000aaffe014 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000aaffe210 000B4 (v01 HPQOEM SLIC-MPC 00000001 HP   01000013)
[    0.000000] ACPI: FACP 00000000aaffb000 0010C (v05 HPQOEM SLIC-MPC 00000001 HP   00040000)
[    0.000000] ACPI: DSDT 00000000aafe7000 103B9 (v01 HPQOEM INSYDE   00000000 ACPI 00040000)
[    0.000000] ACPI: FACS 00000000aafb9000 00040
[    0.000000] ACPI: UEFI 00000000aaffd000 00236 (v01 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: ASF! 00000000aaffc000 000A5 (v32 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: HPET 00000000aaffa000 00038 (v01 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: APIC 00000000aaff9000 0008C (v03 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: MCFG 00000000aaff8000 0003C (v01 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: WDAT 00000000aafe6000 00224 (v01 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: SSDT 00000000aafe5000 00166 (v01 HPQOEM INSYDE   00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000aafe3000 00028 (v01 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: ASPT 00000000aafe1000 00034 (v07 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: DBGP 00000000aafe0000 00034 (v01 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: FPDT 00000000aafde000 00044 (v01 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: MSDM 00000000aafdd000 00055 (v03 HPQOEM SLIC-MPC 00000001 HP   00040000)
[    0.000000] ACPI: SSDT 00000000aafdc000 009AA (v01 HPQOEM INSYDE   00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000aafdb000 00B22 (v01 HPQOEM INSYDE   00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000aafda000 002D7 (v01 HPQOEM INSYDE   00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000aafd9000 00348 (v01 HPQOEM INSYDE   00003000 ACPI 00040000)
[    0.000000] ACPI: BGRT 00000000aafd8000 00038 (v01 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000024f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x24f5fffff]
[    0.000000]   NODE_DATA [mem 0x24f5fc000-0x24f5fffff]
[    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880246c00000-ffff88024ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x24f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x00087fff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xa9dbefff]
[    0.000000]   node   0: [mem 0xaafff000-0xaaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x24f5fffff]
[    0.000000] On node 0 totalpages: 2068791
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 7 pages reserved
[    0.000000]   DMA zone: 3889 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 674815 pages, LIFO batch:31
[    0.000000]   Normal zone: 21464 pages used for memmap
[    0.000000]   Normal zone: 1352232 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000088000 - 00000000000c0000
[    0.000000] PM: Registered nosave memory: 00000000000c0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 00000000a9dbf000 - 00000000aaebf000
[    0.000000] PM: Registered nosave memory: 00000000aaebf000 - 00000000aafbf000
[    0.000000] PM: Registered nosave memory: 00000000aafbf000 - 00000000aafff000
[    0.000000] PM: Registered nosave memory: 00000000ab000000 - 00000000afa00000
[    0.000000] PM: Registered nosave memory: 00000000afa00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffd80000
[    0.000000] PM: Registered nosave memory: 00000000ffd80000 - 0000000100000000
[    0.000000] e820: [mem 0xafa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88024f200000 s83584 r8192 d22912 u262144
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2030936
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=c7b593da-4cd1-404e-af34-04a70c23847a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7994508k/9689088k available (6828k kernel code, 1413924k absent, 280656k reserved, 6342k data, 948k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2594.138 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5188.27 BogoMIPS (lpj=10376552)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.036836] Security Framework initialized
[    0.036850] AppArmor: AppArmor initialized
[    0.036851] Yama: becoming mindful.
[    0.037307] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.039176] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.040001] Mount-cache hash table entries: 256
[    0.040139] Initializing cgroup subsys cpuacct
[    0.040141] Initializing cgroup subsys memory
[    0.040147] Initializing cgroup subsys devices
[    0.040148] Initializing cgroup subsys freezer
[    0.040149] Initializing cgroup subsys blkio
[    0.040150] Initializing cgroup subsys perf_event
[    0.040173] CPU: Physical Processor ID: 0
[    0.040173] CPU: Processor Core ID: 0
[    0.040177] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.040177] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.040517] mce: CPU supports 7 MCE banks
[    0.040527] CPU0: Thermal monitoring enabled (TM1)
[    0.040532] using mwait in idle threads.
[    0.042410] ACPI: Core revision 20120320
[    0.079652] ftrace: allocating 27653 entries in 109 pages
[    0.091829] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.131440] CPU0: Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz stepping 09
[    0.236566] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
[    0.236571] ... version:                3
[    0.236572] ... bit width:              48
[    0.236573] ... generic registers:      4
[    0.236574] ... value mask:             0000ffffffffffff
[    0.236575] ... max period:             000000007fffffff
[    0.236575] ... fixed-purpose events:   3
[    0.236576] ... event mask:             000000070000000f
[    0.236701] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.236771] Booting Node   0, Processors  #1 #2 #3
[    0.277166] Brought up 4 CPUs
[    0.277169] Total of 4 processors activated (20753.10 BogoMIPS).
[    0.280414] devtmpfs: initialized
[    0.281345] EVM: security.selinux
[    0.281346] EVM: security.SMACK64
[    0.281347] EVM: security.capability
[    0.281380] PM: Registering ACPI NVS region [mem 0xaaebf000-0xaafbefff] (1048576 bytes)
[    0.282001] dummy: 
[    0.282030] RTC time: 20:56:43, date: 07/07/13
[    0.282056] NET: Registered protocol family 16
[    0.282127] Trying to unpack rootfs image as initramfs...
[    0.282184] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.282186] ACPI: bus type pci registered
[    0.282240] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.282241] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.303913] PCI: Using configuration type 1 for base access
[    0.304694] bio: create slab <bio-0> at 0
[    0.304762] ACPI: Added _OSI(Module Device)
[    0.304763] ACPI: Added _OSI(Processor Device)
[    0.304764] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.304765] ACPI: Added _OSI(Processor Aggregator Device)
[    0.306112] ACPI: EC: Look up EC in DSDT
[    0.307427] ACPI: Executed 1 blocks of module-level executable AML code
[    0.336854] ACPI: SSDT 00000000aae19018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20121220)
[    0.337199] ACPI: Dynamic OEM Table Load:
[    0.337201] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20121220)
[    0.356564] ACPI: SSDT 00000000aae5ba98 00303 (v01  PmRef    ApIst 00003000 INTL 20121220)
[    0.356932] ACPI: Dynamic OEM Table Load:
[    0.356934] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20121220)
[    0.392384] ACPI: SSDT 00000000aae18d98 00119 (v01  PmRef    ApCst 00003000 INTL 20121220)
[    0.392726] ACPI: Dynamic OEM Table Load:
[    0.392727] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20121220)
[    0.490639] Freeing initrd memory: 15180k freed
[    1.326882] ACPI: Interpreter enabled
[    1.326886] ACPI: (supports S0 S3 S4 S5)
[    1.326911] ACPI: Using IOAPIC for interrupt routing
[    1.365816] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.366112] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    1.366115] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.366304] \_SB_.PCI0:_OSC invalid UUID
[    1.366305] _OSC request data:1 8 1f 
[    1.366308] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.366584] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.366586] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.366588] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.366589] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    1.366591] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    1.366592] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    1.366593] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    1.366595] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    1.366596] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    1.366597] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    1.366599] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    1.366600] pci_root PNP0A08:00: host bridge window [mem 0xafa00000-0xfeafffff]
[    1.366623] PCI host bridge to bus 0000:00
[    1.366625] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    1.366626] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.366628] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.366629] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    1.366630] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    1.366632] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    1.366633] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    1.366634] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    1.366636] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    1.366637] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    1.366638] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    1.366640] pci_bus 0000:00: root bus resource [mem 0xafa00000-0xfeafffff]
[    1.366647] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    1.366681] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    1.366690] pci 0000:00:02.0: reg 10: [mem 0xc2000000-0xc23fffff 64bit]
[    1.366697] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.366701] pci 0000:00:02.0: reg 20: [io  0x4000-0x403f]
[    1.366754] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    1.366777] pci 0000:00:16.0: reg 10: [mem 0xc2604000-0xc260400f 64bit]
[    1.366852] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.366886] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    1.366907] pci 0000:00:1a.0: reg 10: [mem 0xc2609000-0xc26093ff]
[    1.366997] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.367023] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    1.367038] pci 0000:00:1b.0: reg 10: [mem 0xc2600000-0xc2603fff 64bit]
[    1.367105] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.367128] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    1.367207] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.367232] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    1.367310] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.367335] pci 0000:00:1c.3: [8086:1e16] type 01 class 0x060400
[    1.367413] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.367447] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    1.367467] pci 0000:00:1d.0: reg 10: [mem 0xc2608000-0xc26083ff]
[    1.367557] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.367583] pci 0000:00:1f.0: [8086:1e5d] type 00 class 0x060100
[    1.367706] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    1.367724] pci 0000:00:1f.2: reg 10: [io  0x4088-0x408f]
[    1.367732] pci 0000:00:1f.2: reg 14: [io  0x4094-0x4097]
[    1.367740] pci 0000:00:1f.2: reg 18: [io  0x4080-0x4087]
[    1.367748] pci 0000:00:1f.2: reg 1c: [io  0x4090-0x4093]
[    1.367755] pci 0000:00:1f.2: reg 20: [io  0x4060-0x407f]
[    1.367763] pci 0000:00:1f.2: reg 24: [mem 0xc2607000-0xc26077ff]
[    1.367808] pci 0000:00:1f.2: PME# supported from D3hot
[    1.367827] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    1.367842] pci 0000:00:1f.3: reg 10: [mem 0xc2605000-0xc26050ff 64bit]
[    1.367862] pci 0000:00:1f.3: reg 20: [io  0x4040-0x405f]
[    1.368012] pci 0000:01:00.0: [10ec:8136] type 00 class 0x020000
[    1.368084] pci 0000:01:00.0: reg 10: [io  0x3000-0x30ff]
[    1.368199] pci 0000:01:00.0: reg 18: [mem 0xc2404000-0xc2404fff 64bit pref]
[    1.368274] pci 0000:01:00.0: reg 20: [mem 0xc2400000-0xc2403fff 64bit pref]
[    1.368611] pci 0000:01:00.0: supports D1 D2
[    1.368612] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.376074] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.376078] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    1.376086] pci 0000:00:1c.0:   bridge window [mem 0xc2400000-0xc24fffff 64bit pref]
[    1.376169] pci 0000:02:00.0: [1814:3290] type 00 class 0x028000
[    1.376188] pci 0000:02:00.0: reg 10: [mem 0xc2510000-0xc251ffff]
[    1.376327] pci 0000:02:00.0: PME# supported from D0 D3hot
[    1.376376] pci 0000:02:00.1: [1814:3298] type 00 class 0x0d1100
[    1.376395] pci 0000:02:00.1: reg 10: [mem 0xc2500000-0xc250ffff]
[    1.376533] pci 0000:02:00.1: supports D1
[    1.376535] pci 0000:02:00.1: PME# supported from D0 D1 D3hot
[    1.384049] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    1.384055] pci 0000:00:1c.2:   bridge window [mem 0xc2500000-0xc25fffff]
[    1.384195] pci 0000:03:00.0: [10ec:5229] type 00 class 0xff0000
[    1.384258] pci 0000:03:00.0: reg 10: [mem 0xc1000000-0xc1000fff]
[    1.384743] pci 0000:03:00.0: supports D1 D2
[    1.384745] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    1.392043] pci 0000:00:1c.3: PCI bridge to [bus 03-08]
[    1.392047] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    1.392051] pci 0000:00:1c.3:   bridge window [mem 0xc1000000-0xc1ffffff]
[    1.392057] pci 0000:00:1c.3:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
[    1.392073] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.392193] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.392225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.392248] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.392326] \_SB_.PCI0:_OSC invalid UUID
[    1.392327] _OSC request data:1 1f 1f 
[    1.392330]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.392363] \_SB_.PCI0:_OSC invalid UUID
[    1.392364] _OSC request data:1 0 1d 
[    1.392366]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.392367] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.394607] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.394644] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.394679] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.394714] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.394748] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.394782] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.394816] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.394850] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.394922] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.394926] vgaarb: loaded
[    1.394927] vgaarb: bridge control possible 0000:00:02.0
[    1.395040] SCSI subsystem initialized
[    1.395079] libata version 3.00 loaded.
[    1.395094] ACPI: bus type usb registered
[    1.395107] usbcore: registered new interface driver usbfs
[    1.395114] usbcore: registered new interface driver hub
[    1.395130] usbcore: registered new device driver usb
[    1.395183] PCI: Using ACPI for IRQ routing
[    1.402463] PCI: pci_cache_line_size set to 64 bytes
[    1.402561] e820: reserve RAM buffer [mem 0x00088000-0x0008ffff]
[    1.402563] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    1.402564] e820: reserve RAM buffer [mem 0xa9dbf000-0xabffffff]
[    1.402565] e820: reserve RAM buffer [mem 0xab000000-0xabffffff]
[    1.402566] e820: reserve RAM buffer [mem 0x24f600000-0x24fffffff]
[    1.402637] NetLabel: Initializing
[    1.402639] NetLabel:  domain hash size = 128
[    1.402639] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.402646] NetLabel:  unlabeled traffic allowed by default
[    1.402694] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.402700] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.404708] Switching to clocksource hpet
[    1.409075] AppArmor: AppArmor Filesystem Enabled
[    1.409092] pnp: PnP ACPI init
[    1.409102] ACPI: bus type pnp registered
[    1.409282] pnp 00:00: [bus 00-fe]
[    1.409284] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.409286] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.409287] pnp 00:00: [io  0x0d00-0xffff window]
[    1.409289] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.409290] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.409291] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.409293] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.409294] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.409296] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.409297] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.409299] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.409300] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.409301] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.409303] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.409304] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.409305] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.409306] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.409308] pnp 00:00: [mem 0xafa00000-0xfeafffff window]
[    1.409311] pnp 00:00: [mem 0x00010000-0x0001ffff window]
[    1.409360] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.409370] pnp 00:01: [io  0x0000-0x001f]
[    1.409371] pnp 00:01: [io  0x0081-0x0091]
[    1.409372] pnp 00:01: [io  0x0093-0x009f]
[    1.409374] pnp 00:01: [io  0x00c0-0x00df]
[    1.409375] pnp 00:01: [dma 4]
[    1.409389] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.409394] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.409408] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.409472] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.409485] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.409492] pnp 00:04: [io  0x00f0]
[    1.409500] pnp 00:04: [irq 13]
[    1.409515] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.409522] pnp 00:05: [io  0x002e-0x002f]
[    1.409524] pnp 00:05: [io  0x004e-0x004f]
[    1.409525] pnp 00:05: [io  0x0061]
[    1.409526] pnp 00:05: [io  0x0063]
[    1.409527] pnp 00:05: [io  0x0065]
[    1.409528] pnp 00:05: [io  0x0067]
[    1.409529] pnp 00:05: [io  0x0070]
[    1.409530] pnp 00:05: [io  0x0080]
[    1.409531] pnp 00:05: [io  0x0092]
[    1.409533] pnp 00:05: [io  0x00b2-0x00b3]
[    1.409534] pnp 00:05: [io  0x0680-0x069f]
[    1.409535] pnp 00:05: [io  0x1000-0x100f]
[    1.409536] pnp 00:05: [io  0xffff]
[    1.409537] pnp 00:05: [io  0xffff]
[    1.409538] pnp 00:05: [io  0x0400-0x0453]
[    1.409540] pnp 00:05: [io  0x0458-0x047f]
[    1.409541] pnp 00:05: [io  0x0500-0x057f]
[    1.409542] pnp 00:05: [io  0x164e-0x164f]
[    1.409571] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.409573] system 00:05: [io  0x1000-0x100f] has been reserved
[    1.409575] system 00:05: [io  0xffff] has been reserved
[    1.409576] system 00:05: [io  0xffff] has been reserved
[    1.409577] system 00:05: [io  0x0400-0x0453] has been reserved
[    1.409579] system 00:05: [io  0x0458-0x047f] has been reserved
[    1.409580] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.409582] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.409584] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.409590] pnp 00:06: [io  0x0070-0x0077]
[    1.409594] pnp 00:06: [irq 8]
[    1.409607] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.409625] pnp 00:07: [io  0x0454-0x0457]
[    1.409648] system 00:07: [io  0x0454-0x0457] has been reserved
[    1.409650] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.425185] pnp 00:08: [io  0x0060]
[    1.425186] pnp 00:08: [io  0x0064]
[    1.425192] pnp 00:08: [irq 1]
[    1.425214] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.425223] pnp 00:09: [irq 12]
[    1.425240] pnp 00:09: Plug and Play ACPI device, IDs SYN1e68 SYN1e00 SYN0002 PNP0f13 (active)
[    1.425320] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    1.425322] pnp 00:0a: [mem 0xfed10000-0xfed17fff]
[    1.425323] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    1.425324] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    1.425326] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    1.425327] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    1.425328] pnp 00:0a: [mem 0xfed90000-0xfed93fff]
[    1.425329] pnp 00:0a: [mem 0xff000000-0xffffffff]
[    1.425330] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    1.425332] pnp 00:0a: [mem 0xafa00000-0xafa00fff]
[    1.425359] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.425361] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.425363] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.425364] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.425366] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    1.425367] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.425369] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.425370] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    1.425372] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.425373] system 00:0a: [mem 0xafa00000-0xafa00fff] has been reserved
[    1.425376] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.425568] pnp 00:0b: [mem 0x20000000-0x201fffff]
[    1.425569] pnp 00:0b: [mem 0x40004000-0x40004fff]
[    1.425608] system 00:0b: [mem 0x20000000-0x201fffff] has been reserved
[    1.425610] system 00:0b: [mem 0x40004000-0x40004fff] has been reserved
[    1.425612] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.425622] pnp: PnP ACPI: found 12 devices
[    1.425623] ACPI: ACPI bus type pnp unregistered
[    1.431722] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.431726] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    1.431734] pci 0000:00:1c.0:   bridge window [mem 0xc2400000-0xc24fffff 64bit pref]
[    1.431741] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    1.431746] pci 0000:00:1c.2:   bridge window [mem 0xc2500000-0xc25fffff]
[    1.431754] pci 0000:00:1c.3: PCI bridge to [bus 03-08]
[    1.431757] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    1.431762] pci 0000:00:1c.3:   bridge window [mem 0xc1000000-0xc1ffffff]
[    1.431766] pci 0000:00:1c.3:   bridge window [mem 0xc0000000-0xc0ffffff 64bit pref]
[    1.431799] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.431801] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.431802] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.431804] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    1.431805] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    1.431807] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    1.431808] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    1.431809] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    1.431811] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    1.431812] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    1.431814] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    1.431815] pci_bus 0000:00: resource 15 [mem 0xafa00000-0xfeafffff]
[    1.431817] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    1.431818] pci_bus 0000:01: resource 2 [mem 0xc2400000-0xc24fffff 64bit pref]
[    1.431820] pci_bus 0000:02: resource 1 [mem 0xc2500000-0xc25fffff]
[    1.431821] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    1.431823] pci_bus 0000:03: resource 1 [mem 0xc1000000-0xc1ffffff]
[    1.431824] pci_bus 0000:03: resource 2 [mem 0xc0000000-0xc0ffffff 64bit pref]
[    1.431847] NET: Registered protocol family 2
[    1.431980] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.432528] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.433509] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.433618] TCP: Hash tables configured (established 524288 bind 65536)
[    1.433619] TCP: reno registered
[    1.433630] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.433656] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.433720] NET: Registered protocol family 1
[    1.433730] pci 0000:00:02.0: Boot video device
[    1.464615] PCI: CLS 64 bytes, default 64
[    1.464617] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.464619] software IO TLB [mem 0xa2df3000-0xa6df2fff] (64MB) mapped at [ffff8800a2df3000-ffff8800a6df2fff]
[    1.464647] Simple Boot Flag at 0x44 set to 0x1
[    1.465008] audit: initializing netlink socket (disabled)
[    1.465015] type=2000 audit(1373230603.328:1): initialized
[    1.486069] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.487374] VFS: Disk quotas dquot_6.5.2
[    1.487402] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.487717] fuse init (API version 7.19)
[    1.487769] msgmni has been set to 15744
[    1.488041] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.488065] io scheduler noop registered
[    1.488066] io scheduler deadline registered (default)
[    1.488084] io scheduler cfq registered
[    1.488269] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.488281] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.488325] efifb: probing for efifb
[    1.488758] efifb: framebuffer at 0xb0000000, mapped to 0xffffc90021b80000, using 4160k, total 4160k
[    1.488759] efifb: mode is 1366x768x32, linelength=5504, pages=1
[    1.488760] efifb: scrolling: redraw
[    1.488761] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.488846] Console: switching to colour frame buffer device 170x48
[    1.488862] fb0: EFI VGA frame buffer device
[    1.488867] intel_idle: MWAIT substates: 0x21120
[    1.488868] intel_idle: v0.4 model 0x3A
[    1.488868] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.493762] ACPI: AC Adapter [AC] (on-line)
[    1.493826] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.494248] ACPI: Lid Switch [LID]
[    1.494276] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.494278] ACPI: Power Button [PWRB]
[    1.494304] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.494306] ACPI: Power Button [PWRF]
[    1.494369] ACPI: Requesting acpi_cpufreq
[    1.530624] thermal LNXTHERM:00: registered as thermal_zone0
[    1.530626] ACPI: Thermal Zone [TSZ0] (50 C)
[    1.530639] ACPI: Battery Slot [BAT0] (battery present)
[    1.530660] GHES: HEST is not enabled!
[    1.530712] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.531748] Linux agpgart interface v0.103
[    1.532683] brd: module loaded
[    1.533171] loop: module loaded
[    1.533235] ahci 0000:00:1f.2: version 3.0
[    1.533288] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    1.533313] ahci: SSS flag set, parallel bus scan disabled
[    1.548399] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.548404] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems apst 
[    1.548412] ahci 0000:00:1f.2: setting latency timer to 64
[    1.556677] scsi0 : ahci
[    1.556735] scsi1 : ahci
[    1.556779] scsi2 : ahci
[    1.556821] scsi3 : ahci
[    1.556867] scsi4 : ahci
[    1.556907] scsi5 : ahci
[    1.556964] ata1: SATA max UDMA/133 abar m2048@0xc2607000 port 0xc2607100 irq 40
[    1.556966] ata2: DUMMY
[    1.556968] ata3: SATA max UDMA/133 abar m2048@0xc2607000 port 0xc2607200 irq 40
[    1.556969] ata4: DUMMY
[    1.556970] ata5: DUMMY
[    1.556971] ata6: DUMMY
[    1.557154] Fixed MDIO Bus: probed
[    1.557179] tun: Universal TUN/TAP device driver, 1.6
[    1.557180] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.557212] PPP generic driver version 2.4.2
[    1.557244] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.557273] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.557276] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.557280] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.557304] ehci_hcd 0000:00:1a.0: debug port 2
[    1.561197] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.561211] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc2609000
[    1.565206] ACPI: Battery Slot [BAT0] (battery present)
[    1.572344] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.572383] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.572385] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.572386] usb usb1: Product: EHCI Host Controller
[    1.572388] usb usb1: Manufacturer: Linux 3.5.0-23-generic ehci_hcd
[    1.572389] usb usb1: SerialNumber: 0000:00:1a.0
[    1.572466] hub 1-0:1.0: USB hub found
[    1.572470] hub 1-0:1.0: 2 ports detected
[    1.572522] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.572525] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.572528] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.572547] ehci_hcd 0000:00:1d.0: debug port 2
[    1.576426] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.576439] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xc2608000
[    1.588313] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.588332] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.588335] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.588351] usb usb2: Product: EHCI Host Controller
[    1.588352] usb usb2: Manufacturer: Linux 3.5.0-23-generic ehci_hcd
[    1.588354] usb usb2: SerialNumber: 0000:00:1d.0
[    1.588421] hub 2-0:1.0: USB hub found
[    1.588426] hub 2-0:1.0: 2 ports detected
[    1.588462] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.588472] uhci_hcd: USB Universal Host Controller Interface driver
[    1.588502] usbcore: registered new interface driver libusual
[    1.588526] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.597781] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.597785] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.597853] mousedev: PS/2 mouse device common for all mice
[    1.597971] rtc_cmos 00:06: RTC can wake from S4
[    1.598081] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.598108] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.598154] device-mapper: uevent: version 1.0.3
[    1.598194] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    1.598249] cpuidle: using governor ladder
[    1.598323] cpuidle: using governor menu
[    1.598325] EFI Variables Facility v0.08 2004-May-17
[    1.605775] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.875869] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.876566] ata1.00: ATA-8: ST500LT012-9WS142, 0001YAM1, max UDMA/133
[    1.876568] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.877332] ata1.00: configured for UDMA/133
[    1.877460] scsi 0:0:0:0: Direct-Access     ATA      ST500LT012-9WS14 0001 PQ: 0 ANSI: 5
[    1.877600] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.877603] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.877607] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.877675] sd 0:0:0:0: [sda] Write Protect is off
[    1.877678] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.877701] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.883787] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.953414]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9
[    1.954745] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.015916] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.015918] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.016195] hub 1-1:1.0: USB hub found
[    2.016291] hub 1-1:1.0: 6 ports detected
[    2.127337] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.195257] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.210552] ata3.00: ATAPI: hp      DVD-RAM UJ8D1, H.01, max UDMA/100
[    2.223692] ata3.00: configured for UDMA/100
[    2.230230] scsi 2:0:0:0: CD-ROM            hp       DVD-RAM UJ8D1    H.01 PQ: 0 ANSI: 5
[    2.233371] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.233373] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.233537] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.233664] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.259463] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    2.259466] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.259737] hub 2-1:1.0: USB hub found
[    2.259845] hub 2-1:1.0: 6 ports detected
[    2.462710] Refined TSC clocksource calibration: 2594.109 MHz.
[    2.462713] Switching to clocksource tsc
[    2.562633] usb 2-1.3: new high-speed USB device number 3 using ehci_hcd
[    2.733562] usb 2-1.3: New USB device found, idVendor=064e, idProduct=e263
[    2.733564] usb 2-1.3: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.733566] usb 2-1.3: Product: HP TrueVision HD
[    2.733569] usb 2-1.3: Manufacturer: SuYin
[    2.733571] usb 2-1.3: SerialNumber: HF1016-T821-SE01-VH-R01.00.05
[    3.097276] ashmem: initialized
[    3.097361] TCP: cubic registered
[    3.097428] NET: Registered protocol family 10
[    3.097566] NET: Registered protocol family 17
[    3.097572] Key type dns_resolver registered
[    3.097664] PM: Hibernation image not present or could not be loaded.
[    3.097676] registered taskstats version 1
[    3.099826] Key type trusted registered
[    3.101301] Key type encrypted registered
[    3.103073]   Magic number: 5:544:952
[    3.103100] tty tty9: hash matches
[    3.103127] memory memory5: hash matches
[    3.103170] rtc_cmos 00:06: setting system clock to 2013-07-07 20:56:46 UTC (1373230606)
[    3.103751] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.103752] EDD information not available.
[    3.104757] Freeing unused kernel memory: 948k freed
[    3.104844] Write protecting the kernel read-only data: 12288k
[    3.107422] Freeing unused kernel memory: 1352k freed
[    3.109431] Freeing unused kernel memory: 1048k freed
[    3.119602] udevd[111]: starting version 175
[    3.148055] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.148168] r8169 0000:01:00.0: irq 41 for MSI/MSI-X
[    3.148326] r8169 0000:01:00.0: eth0: RTL8105e at 0xffffc900100c8000, d8:9d:67:cc:95:e8, XID 00c00000 IRQ 41
[    4.175953] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    8.665121] Adding 3195900k swap on /dev/sda6.  Priority:-1 extents:1 across:3195900k 
[    8.782063] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[    8.832411] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.998457] udevd[476]: starting version 175
[    9.428738] lp: driver loaded but no devices found
[    9.603967] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x15
[    9.676216] wmi: Mapper loaded
[    9.761433] input: HP WMI hotkeys as /devices/virtual/input/input4
[    9.767439] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[    9.767444] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff8802438db258), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[    9.767450] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff8802438dbaf0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[    9.767654] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[    9.767659] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff8802438db258), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[    9.767667] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff8802438dbaf0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[    9.803458] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    9.803464] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.803465] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    9.803468] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    9.803470] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.803473] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[    9.803475] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.803475] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    9.833189] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x15
[    9.834012] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x15
[    9.834802] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x15
[    9.835649] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.892928] mei 0000:00:16.0: setting latency timer to 64
[    9.892981] mei 0000:00:16.0: irq 42 for MSI/MSI-X
[    9.898906] mei 0000:00:16.0: wd: failed to find the client
[   10.349646] [drm] Initialized drm 1.1.0 20060810
[   10.606227] kvm: disabled by bios
[   10.730141] checking generic (b0000000 410000) vs hw (0 0)
[   10.730146] i915 0000:00:02.0: setting latency timer to 64
[   10.730498] pci 0000:00:00.0: Intel Ivybridge Chipset
[   10.730548] pci 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[   10.731294] pci 0000:00:00.0: detected 65536K stolen memory
[   10.736396] Linux video capture interface: v2.00
[   10.754846] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   10.754854] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.754855] [drm] Driver supports precise vblank timestamp query.
[   10.755421] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.765698] uvcvideo: Found UVC 1.00 device HP TrueVision HD (064e:e263)
[   10.769651] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xf00173/0x240000/0xa2400
[   10.771688] input: HP TrueVision HD as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input5
[   10.771764] usbcore: registered new interface driver uvcvideo
[   10.771766] USB Video Class driver (1.1.1)
[   10.816727] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   10.913717] type=1400 audit(1373210814.320:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=691 comm="apparmor_parser"
[   10.913724] type=1400 audit(1373210814.320:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=685 comm="apparmor_parser"
[   10.913976] type=1400 audit(1373210814.320:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=691 comm="apparmor_parser"
[   10.913983] type=1400 audit(1373210814.320:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=685 comm="apparmor_parser"
[   10.914122] type=1400 audit(1373210814.320:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=691 comm="apparmor_parser"
[   10.914130] type=1400 audit(1373210814.320:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=685 comm="apparmor_parser"
[   11.271880] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   11.456349] checking generic (b0000000 410000) vs hw (b0000000 10000000)
[   11.456352] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[   11.456378] Console: switching to colour dummy device 80x25
[   11.456524] fbcon: inteldrmfb (fb0) is primary device
[   11.456570] Console: switching to colour frame buffer device 170x48
[   11.456584] fb0: inteldrmfb frame buffer device
[   11.456584] drm: registered panic notifier
[   11.459404] ACPI Warning: _BQC returned an invalid level (20120320/video-480)
[   11.459432] acpi device:40: registered as cooling_device4
[   11.459535] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.459567] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   11.459620] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.459753] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   12.077065] init: failsafe main process (816) killed by TERM signal
[   12.090887] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.090956] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.091015] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   13.598694] ppdev: user-space parallel port driver
[   13.711801] type=1400 audit(1373210817.124:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=886 comm="apparmor_parser"
[   13.712090] type=1400 audit(1373210817.124:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=886 comm="apparmor_parser"
[   13.957616] Bluetooth: Core ver 2.16
[   13.957631] NET: Registered protocol family 31
[   13.957632] Bluetooth: HCI device and connection manager initialized
[   13.957633] Bluetooth: HCI socket layer initialized
[   13.957634] Bluetooth: L2CAP socket layer initialized
[   13.957636] Bluetooth: SCO socket layer initialized
[   14.356227] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.356229] Bluetooth: BNEP filters: protocol multicast
[   14.458022] Bluetooth: RFCOMM TTY layer initialized
[   14.458027] Bluetooth: RFCOMM socket layer initialized
[   14.458028] Bluetooth: RFCOMM ver 1.11
[   16.467372] r8169 0000:01:00.0: eth0: link down
[   16.467390] r8169 0000:01:00.0: eth0: link down
[   16.467804] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.468033] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.105030] r8169 0000:01:00.0: eth0: link up
[   18.105488] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.069936] type=1400 audit(1373210823.496:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=979 comm="apparmor_parser"
[   20.070195] type=1400 audit(1373210823.496:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=979 comm="apparmor_parser"
[   20.070335] type=1400 audit(1373210823.496:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=979 comm="apparmor_parser"
[   20.072229] type=1400 audit(1373210823.496:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=983 comm="apparmor_parser"
[   20.072517] type=1400 audit(1373210823.496:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=983 comm="apparmor_parser"
[   20.098847] type=1400 audit(1373210823.524:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=978 comm="apparmor_parser"
[   20.106266] type=1400 audit(1373210823.532:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=985 comm="apparmor_parser"
[   20.132824] type=1400 audit(1373210823.556:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=982 comm="apparmor_parser"
[   20.133138] type=1400 audit(1373210823.556:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=982 comm="apparmor_parser"
[   20.154196] type=1400 audit(1373210823.580:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=980 comm="apparmor_parser"
[   20.424503] init: alsa-restore main process (1018) terminated with status 99
[   28.195442] audit_printk_skb: 21 callbacks suppressed
[   28.195444] type=1400 audit(1373210831.636:27): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=891 comm="cupsd" pid=891 comm="cupsd" capability=36  capname="block_suspend"
[   54.583500] type=1400 audit(1373210858.062:28): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1893 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  332.442587] type=1400 audit(1373211136.307:29): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=891 comm="cupsd" pid=891 comm="cupsd" capability=36  capname="block_suspend"
[  455.076241] init: anacron main process (1047) killed by TERM signal
[ 1032.115496] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[ 1032.115510] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff8802438db258), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1032.115525] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff8802438dbaf0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1033.439769] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[ 1033.439782] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff8802438db258), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1033.439798] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff8802438dbaf0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1034.181935] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[ 1034.181947] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff8802438db258), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1034.181962] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff8802438dbaf0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1039.436935] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[ 1039.436953] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff8802438db258), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1039.436975] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff8802438dbaf0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1044.226718] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[ 1044.226726] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff8802438db258), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1044.226737] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff8802438dbaf0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1051.205430] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[ 1051.205443] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff8802438db258), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1051.205458] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff8802438dbaf0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1051.450514] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[ 1051.450527] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff8802438db258), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1051.450543] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff8802438dbaf0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1051.643202] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[ 1051.643215] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff8802438db258), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1051.643231] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff8802438dbaf0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[ 1184.231701] type=1400 audit(1373211989.363:30): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=891 comm="cupsd" pid=891 comm="cupsd" capability=36  capname="block_suspend"


> **chili555 said:**
> I'm glad it's working! Have fun!

I am sure there are books but I just read the forums and examine my test system, an older laptop with nothing too crucial on it. If I make a mistake, I can reinstall or otherwise without losing my essential files.

Broward County?? I hearda that place. I spent quite a few years in Boca before I moved to SC.

Would you please use thread tools at the top to Mark Solved?

---

### Post by chili555 on 2013-07-07
> Hp laptop. 12.04 UEFI. No wireless. What does this tell us?```
lspci -nn | grep 0280
```

---

### Post by samyakd on 2013-07-07
02:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]

> **chili555 said:**
> What does this tell us?```
lspci -nn | grep 0280
```

---

### Post by chili555 on 2013-07-07
> dmesg | grep iwl doesnt show anything.Yes, because you don't have an Intel wireless card, you have a Ralink.

Your device is supported by default in Ubuntu 13.04. Would you rather upgrade or would you rather go through the tricky process of compiling the driver from scratch? Post #13 here gives the compile procedure. [http://ubuntuforums.org/showthread.php?t=2159334&page=2&highlight=rt3290sta](http://ubuntuforums.org/showthread.php?t=2159334&page=2&highlight=rt3290sta) You will also need to install build-essential and linux-headers-generic.

---

### Post by samyakd on 2013-07-07
Damn.! Installing this 12.04 version was itself a headache for me with this new UEFI system and pre-installed windows 8. Upgrade would require the whole process to be repeated. Compiling is the way to go.! I might learn something on my way.! By the way, how do you guys know of all these things, man? Kudos.!

---

### Post by chili555 on 2013-07-07
> **samyakd said:**
> Damn.! Installing this 12.04 version was itself a headache for me with this new UEFI system and pre-installed windows 8. Upgrade would require the whole process to be repeated. Compiling is the way to go.! I might learn something on my way.! By the way, how do you guys know of all these things, man? Kudos.!I know all these things because I love what I do and, having done it for quite a few years, by now I can almost smell the solution! The pci.id, in your case 1814:3290, and Google will tell you more than you ever wanted to know. [https://www.google.com/search?source=ig&rlz=&q=1814%3A3290+ubuntu&oq=1814%3A3290+ubuntu&gs_l=igoogle.3...221724.232230.0.233132.18.6.0.12.0.0.370.1140.0j5j0j1.6.0...0.0...1ac.1.12.igoogle.cRGM9j4Phhg](https://www.google.com/search?source=ig&rlz=&q=1814%3A3290+ubuntu&oq=1814%3A3290+ubuntu&gs_l=igoogle.3...221724.232230.0.233132.18.6.0.12.0.0.370.1140.0j5j0j1.6.0...0.0...1ac.1.12.igoogle.cRGM9j4Phhg)

Do you need a step-by-step or can you proceed based on the linked instructions?

---

### Post by samyakd on 2013-07-08
I did what was told in that post. But now, when I log in to the system and use my laptop for sometime (with wireless on and connected) I get a black screen showing kernel panic - not syncing : Fatal exception in interrupt. I ran a google search but couldn't get any substance out of them. Its been reported as a bug but the place where its solved, its just for that particular user. I wonder if this panic is in any way related to my new wireless driver.

---

### Post by chili555 on 2013-07-08
> **samyakd said:**
> I did what was told in that post. But now, when I log in to the system and use my laptop for sometime (with wireless on and connected) I get a black screen showing kernel panic - not syncing : Fatal exception in interrupt. I ran a google search but couldn't get any substance out of them. Its been reported as a bug but the place where its solved, its just for that particular user. I wonder if this panic is in any way related to my new wireless driver.Let's examine the log file from your last session, which I assume ended in a kernel panic. First, we will copy it to a text file:```
cat /var/log/dmesg.0 > samy.txt
```Now find the text file samy.txt in your user directory and paste it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

We'll examine it and see if we can tell what's going wrong.

---

### Post by samyakd on 2013-07-08
The system finally crashed again in panic.! Here is the dmesg you  required.! Also, the screen had freezed showing a lot of lines and that  error and i had to restart my system by pressing the power button for a  long time! I do hope however that this information is relevant.!  [URL="http://paste.ubuntu.com/5855604/"]http://paste.ubuntu.com/5855604/
[/URL]

---

### Post by samyakd on 2013-07-08
And again.! Although now, there were a few more lines after the panic message, something about the system calls. This is the dmesg of the latest such crash : [http://paste.ubuntu.com/5855647/](http://paste.ubuntu.com/5855647/)[ ]("http://paste.ubuntu.com/5855604/")

---

### Post by chili555 on 2013-07-08
I don't see anything alarming related to wireless. I do see quite a few of these:> ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff8802438db258), AE_AML_BUFFER_LIMIT (20120320/psparse-536)You might Google that or ask in General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331) You can refer them to the same paste.

Perhaps you have some special settings in the BIOS related to ACPI or IRQs. I have the best luck on both of my Lenovos with the BIOS set to Default. Your mileage may vary. 

I would also be concerned here:> [    0.903531] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.903568] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.903604] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.903639] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.903673] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.903707] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.903741] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.903775] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.I have the best luck with the IRQs set in the BIOS to Autoselect, not disabled.

---

### Post by samyakd on 2013-07-08
Here is also a bug post on this out of which I couldnt make our anything. The user claims to have solved it in post #5. Please look at this and see if this makes sense to you. Thanks a lot.! [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1181392](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1181392)

---

### Post by chili555 on 2013-07-09
> **samyakd said:**
> Here is also a bug post on this out of which I couldnt make our anything. The user claims to have solved it in post #5. Please look at this and see if this makes sense to you. Thanks a lot.! [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1181392](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1181392)The bug you linked has to do with Broadcom wireless drivers. You have a Ralink. That won't help us at all.

---

### Post by samyakd on 2013-07-11
Ok. Now, the last crash I experienced was different. A few messages had the location of the driver which I had manually downloaded (Downloads/RT....) and the messages it showed were :
1. Incorrect desired TSSI
2. QIDx(0) Insufficient space in MgmtRing : MgmtRingFullCount = n! (Many such messages)

However, I dont have a dmesg of that session because kernel panic occured in the next session before i could cat the relevant information. 

I am growing really tense now. Please help.
And one more thing, in the post you told me (manually installing the driver), the downloaded file was moved to the Desktop. However, I did the process in my Downloads directory only. I dont know if it was essential or not.

---

### Post by chili555 on 2013-07-11
> in the post you told me (manually installing the driver), the downloaded file was moved to the Desktop. However, I did the process in my Downloads directory only. I dont know if it was essential or not. Not a problem. I only suggest Desktop because it is easier for me to explain to new users. You could do the install from anywhere, as long as you and I can communicate and understand.

Are there any alarming (read: diagnostic) messages in dmesg ordinarily?```
dmesg | grep -e rt2 -e rt3
```Have you made any changes in the BIOS?

---

### Post by samyakd on 2013-07-12
> **chili555 said:**
> 

Are there any alarming (read: diagnostic) messages in dmesg ordinarily?```
dmesg | grep -e rt2 -e rt3
``` 
The output reads : 
```

[   16.318312] rt3290sta: module license 'unspecified' taints kernel.
[   16.320253] register rt2860
[   20.260411] <==== rt28xx_init, Status=0
[   20.260473] RTMPrt3xSetPCIePowerLinkCtrl.===> 1e
[   20.345372] <==== rt28xx_init, Status=0
[   20.345433] RTMPrt3xSetPCIePowerLinkCtrl.===> 1e

```

> Have you made any changes in the BIOS?
Not explicitly, no. I have a new laptop wherein the traditional BIOS is replaced with UEFI, which is much less user-changeable thing, and when I go to the BIOS setup options, I can't see anything realted to IRQs or ACPIs which you were saying in one of earlier posts.

---

### Post by chili555 on 2013-07-13
I don't see anything that looks the least troublesome or that would make me believe that the wireless driver is about to cause a freeze-up. I am still suspicious of the IRQ and ACPI issues and I recommend you research those to be sure there is nothing that needs to be fixed there.

---

### Post by jay.hall199 on 2013-11-12
Ready to hear my bonehead move.  Just bought this toshiba yesterday and went to load Ubuntu on it so it can duel boot Win 8 and Linux.  Well, yea, when creating the partition I formatted Win 8 off the comp.  Even though that kinda sucks I still am running Ubuntu on it.  This is the first time using Ubuntu and stumbled across this thread because my wireless is not working and need some help.  Second problem is, I found the terminal but cannot write the code that you want me to write so we can troubleshoot the problem.  Can anyone help?

---

### Post by chili555 on 2013-11-12
Why can't you write the code?```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Jot down the result and post it here.

---

### Post by jay.hall199 on 2013-11-12
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)

I suppose I was able to do that one.  I tried from the beginning of this thread and it came up with nothing.

---

### Post by chili555 on 2013-11-12
Oh, goody! A device with a bit of challenge! Are you able to get a temporary wired ethernet connection so we can download the driver? Here is the process: [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281)

---

### Post by jay.hall199 on 2013-11-12
I am wired on the device needing service as we speak.

---

### Post by chili555 on 2013-11-12
> **jay.hall199 said:**
> I am wired on the device needing service as we speak.Awesome! Rock on with the process I linked. You can simply copy and paste the commands and sit back and watch! I will be around another 30-45 minutes tonight but you should be done in ten!

---

### Post by jay.hall199 on 2013-11-12
so at the step where it said my wireless should be working... it doesn't.  I went ahead and rebooted anyways and recompiled.  In the process of that now but it doesn't look good.  Also, the item that I was supposed to put on my desktop, what is that used for?

---

### Post by chili555 on 2013-11-12
The item you put on your desktop is the compressed (tar.bz2) file containing the items you needed to compile. Let's see what clues the message logs hold. Please run and post:```
sudo modprobe rtl8188ee
dmesg | grep rtl
iwconfig
```I think we're close!!

EDIT: Did you read and follow this part?> If the message logs say you need firmware:

```
dmesg | grep rtl
```

Download and install it with:

```
wget http://mirror.pnl.gov/ubuntu//pool/main/l/linux-firmware/linux-firmware_1.106_all.deb
sudo dpkg -i linux*.deb 
sudo modprobe -r rtl8188ee && sudo modprobe rtl8188ee
```


---

### Post by jay.hall199 on 2013-11-12
eth0      no wireless extensions.

lo        no wireless extensions.

---

### Post by chili555 on 2013-11-12
> **jay.hall199 said:**
> eth0      no wireless extensions.

lo        no wireless extensions.I need all three results in order that I gave them, please.> sudo modprobe rtl8188ee
dmesg | grep rtl
iwconfig

---

### Post by jay.hall199 on 2013-11-12
Is this what your looking for?  I am so freaking new at this it isn't funny

[    9.152353] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[    9.354138] rtlwifi: Firmware rtlwifi/rtl8188efw.bin not available

eth0      no wireless extensions.

lo        no wireless extensions.

---

### Post by chili555 on 2013-11-12
> rtlwifi: Firmware rtlwifi/rtl8188efw.bin not availableAs expected, you need to download and install the firmware file. Copy and paste.>  I am so freaking new at this it isn't funnyNo worries. You are doing fine. We were all new at one time, even me and even Linus: [http://en.wikipedia.org/wiki/Linus_Torvalds](http://en.wikipedia.org/wiki/Linus_Torvalds)

---

### Post by jay.hall199 on 2013-11-12
I would like to say, Thank you sir!

So that worked.  And ummmm, was a very new experience for me and quite strange.  I bought this laptop to learn programming hence why I wanted Ubuntu.  So, by deleting Windows I am locked in now.  Are all driver processes that difficult?  Also, I am spinning in circles on the net trying to figure out where to start programming from the very begginging.  Everything I found seems to be extremly bias.  Any suggestions on where to get started?

---

### Post by jay.hall199 on 2013-11-12
Last question before I am off... Do I need that zip file anymore?

---

### Post by chili555 on 2013-11-12
This driver process was actually pretty easy! Most device drivers are included in the kernel by default. As newer devices are introduced and drivers are written, they are included in kernel versions from there forward. For newer device drivers, it is sometimes necessary to backport the driver from a later kernel to the Ubuntu version you are running now. Think about putting a new Corvette motor in an older car. We have backported the motor.

As for programming, I bought and read a book. It is not my area of expertise. You might ask more here: [http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

I am glad your wireless is working!

---

### Post by chili555 on 2013-11-12
> **jay.hall199 said:**
> Last question before I am off... Do I need that zip file anymore?No, but you DO need the folder that was extracted from it, because of this:>  You will have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after reboot, re-compile:

```
cd Desktop/backports-3.11-rc3-1/
make clean
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8188ee
```


---

### Post by billy11 on 2014-08-06
Sorry to bother, where does one find the [COLOR=#000000]rtlwifi/rtl8188efw.bin [/COLOR]file? redownloaded the linux-firmware package and looked through all of the "rlt" folders and none of them had any differences than what i had in my file system. and is there a way i can just push the file into the folder and reboot and get the wifi card to work?

I stumbled into this problem by deleting it THINKING i could place an aircrack-ng patch file in the same location and that didnt turn out so well...

---

### Post by chili555 on 2014-08-07
> where does one find the rtlwifi/rtl8188efw.binIt is here: [http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb)

There is nothing about this file that differs particularly from 14.04, 13.10 or whatever. Rather that try to mess with it manually, I suggest you download the deb to your desktop and, in a terminal:```
sudo dpkg -i ~/Desktop/linux-firmware_1.127.4_all.deb
```You should be all set.

DISCLAIMER: I know nothing, nor do I intend to learn, anything about aircrack, aircrack-ng or airgoofy, etc.. Please don't ask.

---

### Post by billy11 on 2014-08-14
> **chili555 said:**
> It is here: [http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.127.4_all.deb)

There is nothing about this file that differs particularly from 14.04, 13.10 or whatever. Rather that try to mess with it manually, I suggest you download the deb to your desktop and, in a terminal:```
sudo dpkg -i ~/Desktop/linux-firmware_1.127.4_all.deb
```You should be all set.

DISCLAIMER: I know nothing, nor do I intend to learn, anything about aircrack, aircrack-ng or airgoofy, etc.. Please don't ask.
THANK YOU SO MUCH i thought i was a gonner! Chili your the best!

---

