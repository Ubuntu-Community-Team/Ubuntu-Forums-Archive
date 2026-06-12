---
title: "Unable to install compat-wireless -ath5k"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by bwallum on 2011-02-12
I can't get an ath5k driver to work properly on Maverick 32bit. ```
uname -r
```returns> 2.6.35-26-generic```
sudo  apt-get install  linux-backports-modules-compat-wireless-2.6.36-maverick-generic
```returns
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 linux-backports-modules-compat-wireless-2.6.36-maverick-generic :  Depends:  linux-backports-modules-compat-wireless-2.6.36-2.6.35-26-generic but it  is not installable
E: Broken packagesI got the install info  from [http://wireless.kernel.org/en/users/Download?highlight=%28ath5k%29](http://wireless.kernel.org/en/users/Download?highlight=%28ath5k%29). Can  anybody spot why I'm not able to install compat-wireless?...."not  installable"??

---

### Post by chili555 on 2011-02-12
Please try:> sudo  apt-get install  linux-backports-modules-compat-wireless-2.6.3[COLOR="Red"]**7**[/COLOR]-maverick-generic

---

### Post by bwallum on 2011-02-12
```
sudo  apt-get install  linux-backports-modules-compat-wireless-2.6.3[COLOR=Red]**7**[/COLOR]-maverick-generic                      
```returns> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 linux-backports-modules-compat-wireless-2.6.37-maverick-generic : Depends: linux-backports-modules-compat-wireless-2.6.37-2.6.35-26-generic but it is not installable
E: Broken packages


---

### Post by chili555 on 2011-02-12
According to this, the package is in the *Security* section: [http://packages.ubuntu.com/search?keywords=linux-backports-modules-compat-wireless-2.6.37-maverick-generic&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=linux-backports-modules-compat-wireless-2.6.37-maverick-generic&suite=default&section=all&arch=any&searchon=names)

Please open System > Administration > Synaptic > Settings > Repositories and be sure that under Updates, Security is checked, as attached.

Press Reload and then search for linux-backports-modules-compat-wireless-2.6.37-maverick-generic and see if you can install it.

---

### Post by bwallum on 2011-02-12
Repos ok and I have just got```
sudo apt-get install linux-backports-modules-compat-wireless-2.6.37-2.6.35-25-generic
```installed ok.

The ath5k driver still does not work though. I get very low bandwidth to the point of not being useable.

---

### Post by chili555 on 2011-02-12
Let's have a look at:```
lsmod | grep ath
iwconfig
dmesg | grep ath
```Thanks.

---

### Post by bwallum on 2011-02-13
Some returns:-

```
lsmod | grep ath
```ath5k                 130083  0 
mac80211              231959  1 ath5k
ath                     8153  1 ath5k
cfg80211              144694  3 ath5k,mac80211,ath
led_class               2633  2 ath5k,sdhci
------------------------

```
uname -a
```Linux katy-AMILO-Pa-1510 2.6.35-26-generic #46-Ubuntu SMP Sun Jan 30 08:10:51 UTC 2011 i686 GNU/Linux
-----------------------

```
lspci -v
```(part) 

05:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
    Subsystem: Atheros Communications Inc. Compex Wireless 802.11 b/g  MiniPCI Adapter, Rev A1 [WLM54G]
    Flags: bus master, medium devsel, latency 168, IRQ 23
    Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k
----------------------

```
iwconfig 
```(part) 

wlan0     IEEE 802.11bg  ESSID:"LangbankCottage"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
-----------------------

```
sudo lshw -c network 
```(part)

*-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:05:03.0
       logical name: wlan0
       version: 01
       serial: 00:c0:a8:b9:4c:c7
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-26-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c0200000-c020fff
---------------------------

```
sudo iwlist scan
```(part)

wlan0     Scan completed :
          Cell 01 - Address: 00:22:A4:85:01:21
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"LangbankCottage"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000dc69181
                    Extra: Last beacon: 324ms ago
                    IE: Unknown: 000F4C616E6762616E6B436F7474616765
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
                    IE: Unknown: 0706474220010D14
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
----------------------

```
dmesg | grep ath
```[    0.689628] device-mapper: multipath: version 1.1.1 loaded
[    0.689631] device-mapper: multipath round-robin: version 1.0.0 loaded
[   19.031252] ath5k 0000:05:03.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   19.031325] ath5k 0000:05:03.0: registered as 'phy0'
[   19.647957] ath: EEPROM regdomain: 0x30
[   19.647962] ath: EEPROM indicates we should expect a direct regpair map
[   19.647966] ath: Country alpha2 being used: AM
[   19.647968] ath: Regpair used: 0x30
[   19.682651] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
----------------------

---

### Post by chili555 on 2011-02-13
> [COLOR="Red"]IE: IEEE 802.11i/WPA2 Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
[COLOR="Red"]IE: WPA Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 2A0100
IE: Unknown: 32043048606CI don't know whether it's the driver, Network Manager or wpa_supplicant, but often there is trouble with mixed WPA and WPA2 mode. Are you able to change the router's encryption scheme to WPA2 only?

You might also try:```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
```If that fixes it, we can write one file and make it permanent.

---

### Post by bwallum on 2011-02-13
> **chili555 said:**
> I don't know whether it's the driver, Network Manager or wpa_supplicant, but often there is trouble with mixed WPA and WPA2 mode. Are you able to change the router's encryption scheme to WPA2 only?

You might also try:```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
```If that fixes it, we can write one file and make it permanent.

I went straight for the modprobe change above and it worked a treat! A number of people appear to be hung up with non performance of the ath5k driver.  Can you change the driver?

---

### Post by chili555 on 2011-02-13
> Can you change the driver?I'm not a driver developer, but we can make the change persistent in your system, or any searcher, for that matter. Let's create a file:```
sudo gedit /etc/modprobe.d/ath5k.conf
```Add a single line:```
options ath5k nohwcrypt=1
```Proofread, save and close gedit. Now, on boot, the parameter should be applied automatically. Post back if you need further assistance and be sure to mark the thread solved using Thread Tools at the top.

---

### Post by bwallum on 2011-02-13
Just for completeness I've attached the corresponding returns now that ath5k is working. (In use now!)
```
lsmod | grep ath
```ath5k                 130083  0 
mac80211              231959  1 ath5k
ath                     8153  1 ath5k
cfg80211              144694  3 ath5k,mac80211,ath
led_class               2633  2 ath5k,sdhci
--------------------
```
uname -a
```Linux katy-AMILO-Pa-1510 2.6.35-26-generic #46-Ubuntu SMP Sun Jan 30 08:10:51 UTC 2011 i686 GNU/Linux
--------------------
```
lspci -v 
```(part)

05:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
    Subsystem: Atheros Communications Inc. Compex Wireless 802.11 b/g  MiniPCI Adapter, Rev A1 [WLM54G]
    Flags: bus master, medium devsel, latency 168, IRQ 23
    Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k
--------------------
```
iwconfig
```wlan0     IEEE 802.11bg  ESSID:"LangbankCottage"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:22:A4:85:01:21   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
-------------------
```
sudo lshw -c network
```(part)

*-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:05:03.0
       logical name: wlan0
       version: 01
       serial: 00:c0:a8:b9:4c:c7
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-26-generic firmware=N/A ip=192.168.1.13 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c0200000-c020ffff
-------------------
```
sudo iwlist scan
```wlan0     Scan completed :
          Cell 01 - Address: 00:22:A4:85:01:21
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"LangbankCottage"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000dd8dc20a
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000F4C616E6762616E6B436F7474616765
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
                    IE: Unknown: 0706474220010D14
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
---------------------------
```
dmesg | grep ath
```[    0.689628] device-mapper: multipath: version 1.1.1 loaded
[    0.689631] device-mapper: multipath round-robin: version 1.0.0 loaded
[   19.031252] ath5k 0000:05:03.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   19.031325] ath5k 0000:05:03.0: registered as 'phy0'
[   19.647957] ath: EEPROM regdomain: 0x30
[   19.647962] ath: EEPROM indicates we should expect a direct regpair map
[   19.647966] ath: Country alpha2 being used: AM
[   19.647968] ath: Regpair used: 0x30
[   19.682651] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[ 4424.103911] ath5k 0000:05:03.0: PCI INT A disabled
[ 4472.087555] ath5k 0000:05:03.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 4472.087688] ath5k 0000:05:03.0: registered as 'phy1'
[ 4472.687315] ath: EEPROM regdomain: 0x30
[ 4472.687320] ath: EEPROM indicates we should expect a direct regpair map
[ 4472.687324] ath: Country alpha2 being used: AM
[ 4472.687326] ath: Regpair used: 0x30
[ 4472.690459] ath5k phy1: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
-------------------------

---

### Post by bwallum on 2011-02-13
THIS WORKED FOR ME!

> **chili555 said:**
> I'm not a driver developer, but we can make the change persistent in your system, or any searcher, for that matter. Let's create a file:```
sudo gedit /etc/modprobe.d/ath5k.conf
```Add a single line:```
options ath5k nohwcrypt=1
```Proofread, save and close gedit. Now, on boot, the parameter should be applied automatically. ....

Thanks Chili555, you're a star!

---

### Post by harpinder on 2011-06-28
how to install ath5k driver on natty.please help i am a newbie.
thanks

---

### Post by chili555 on 2011-06-28
> **harpinder said:**
> how to install ath5k driver on natty.please help i am a newbie.
thanksath5k is installed by default in Natty. If it isn't working, something else is wrong. Please open Applications > Terminal and run and post:> lspci -nn | grep Atheros
rfkill list all
dmesg | grep athThe pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by harpinder on 2011-06-28
harpinder@ubuntu:~$ lspci -nn | grep Atheros
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
harpinder@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
harpinder@ubuntu:~$ dmesg | grep ath 
[    0.991776] device-mapper: multipath: version 1.2.0 loaded
[    0.991780] device-mapper: multipath round-robin: version 1.0.0 loaded
[    9.143287] ath5k 0000:07:00.0: PCI INT A -> Link[LK3E] -> GSI 19 (level, low) -> IRQ 19
[    9.143297] ath5k 0000:07:00.0: setting latency timer to 64
[    9.143364] ath5k 0000:07:00.0: registered as 'phy0'
[    9.638708] ath: EEPROM regdomain: 0x65
[    9.638713] ath: EEPROM indicates we should expect a direct regpair map
[    9.638718] ath: Country alpha2 being used: 00
[    9.638720] ath: Regpair used: 0x65
[    9.882890] Registered led device: ath5k-phy0::rx
[    9.882927] Registered led device: ath5k-phy0::tx
[    9.882937] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
harpinder@ubuntu:~$ 
as i have not tested with any wifi modem so i have no idea about it.is it installed or not.please tell me is it installed and will work correctly.i am going to use aircrack ng.
thanks

---

### Post by chili555 on 2011-06-28
> please tell me is it installed and will work correctlyIt clearly is installed. I see nothing here that is troublesome or an error.> [ 9.143287] [COLOR="Red"]ath5k[/COLOR] 0000:07:00.0: PCI INT A -> Link[LK3E] -> GSI 19 (level, low) -> IRQ 19
[ 9.143297] [COLOR="Red"]ath5k[/COLOR] 0000:07:00.0: setting latency timer to 64
[ 9.143364] [COLOR="Red"]ath5k[/COLOR] 0000:07:00.0: registered as 'phy0'
[ 9.638708] ath: EEPROM regdomain: 0x65
[ 9.638713] ath: EEPROM indicates we should expect a direct regpair map
[ 9.638718] ath: Country alpha2 being used: 00
[ 9.638720] ath: Regpair used: 0x65
[ 9.882890] Registered led device: ath5k-phy0::rx
[ 9.882927] Registered led device: ath5k-phy0::tx
[ 9.882937] [COLOR="Red"]ath5k[/COLOR] phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)The timestamps in dmesg indicate that your driver and device are matching up and loading pretty early in the boot process, as would be expected if everything is working normally.> i am going to use aircrack I know nothing about Aircrack; I don't know if ath5k works well, poorly or not at all with Aircrack.

---

