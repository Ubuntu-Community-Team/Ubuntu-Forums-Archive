---
title: "WIFI is working very slow"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by nirjhar17 on 2011-09-10
Hi guys,

I am facing problem while working with my wifi in ubuntu 11.04.
Its working fine in windows 7 and i am getting good speed there.
I m not using usb wifi.

i have tried number of things which are on net but they did n't help me.

**This is my wifi card configuration**     
  resources: irq:43 memory:b6100000-b610ffff
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 4c:0f:6e:5f:69:42
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.0.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:b5100000-b510ffff


**Things which i have already tried.**

 Open a Terminal by going to "Applications," clicking on "Accessories"  and  then "Terminal." Type "sudo su" into the Terminal and press  "Enter." Type "sudo  gedit /etc/modprobe.d/bad_list" into the Terminal.  This opens a text file. Type  "alias net-pf-10 off" into the open text  file and then save and close it. This  shuts off an unnecessary Internet  protocol, IPV6. It often conflicts with IPV4,  a protocol used by most  applications, when accessing the  Web.
 

2Type "sudo gedit  /etc/sysctl.conf" into the Terminal and press "Enter." This  opens a  different text file. Copy and paste the following into the end of the   file, then save and close it:
 net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
 net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
 net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1
This speeds  up your broadband connection by changing the size of the data  packets  that are being exchanged into more manageable sizes so as not to   overload your connection
 

Type "sudo sysctl -p"  into the Terminal followed by "Enter." This resets the  text file  configurations for broadband Internet after adding the information  from  Step 2. Restart your computer after completing these steps to assure  all  changes take hold.


Open your Firefox and type about:config at URL address bar and hit  enter. To make a False into True, select the line to change, and double  click. On the 2nd option change, right click and select Modify
 - network.http.pipelining > Make it True
- network.http.pipelining.maxrequests > Make it 8 or 10
- network.http.proxy.pipelining > Make it True
- network.dns.disableIPv6 > Make it True
any comments from your side would be appreciated.

---

### Post by praseodym on 2011-09-10
Try a module parameter for ath9k:

```
sudo modprobe -rf ath9k
sudo modprobe -v ath9k nohwcrypt=1
sudo service network-manager restart
```

If it works:

```
sudo depmod -a
sudo update-initramfs -u
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

---

### Post by shubham1 on 2011-09-10
i have the smae problem of horrible slow network speed

---

### Post by nirjhar17 on 2011-09-11
Hi 

Thanks for the reply...I have read on some thread that if i upgrade my kernel than my issue will 
resolved but after upgrading my kernel even i am not able to connect the WIFI.
Than i apply the code given by you. After that wifi is working fine but it is dead slow.
I am getting only 4kb/s. Even i tried download manager Uget but nothing help

All these things again pushing me towards Windows, which i don't want.:(

I am giving you all the details again.
**1 ) Machine Brand and Model (PC/Laptop)**:
Acer AS5742G

[B]2 ) Wireless Brand, Model and Wireless Chipset:
[/B][FONT=monospace]**nirjhar17@ubuntu:~$  lspci -nn | grep "Atheros"**

03:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)

[/FONT][B]3 ) check interface:

nirjhar17@ubuntu:~$ iwconfig wlan0
[/B]wlan0     IEEE 802.11bgn  ESSID:"shantanu"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 1C:7E:E5:58:7A:5B   
          Bit Rate=52 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:149  Invalid misc:16   Missed beacon:0
[B]4 ) Check for modules:

[/B]nirjhar17@ubuntu:~$ lsmod | grep "ath[B]"
ath9k                 103633  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath

[/B][B]5 ) Kernel boot messages

 [/B]  4.362764] device-mapper: multipath: version 1.2.0 loaded
[    4.362767] device-mapper: multipath round-robin: version 1.0.0 loaded
[   20.031857] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.031870] ath9k 0000:03:00.0: setting latency timer to 64
[   20.122982] ath: EEPROM regdomain: 0x65
[   20.122984] ath: EEPROM indicates we should expect a direct regpair map
[   20.122987] ath: Country alpha2 being used: 00
[   20.122989] ath: Regpair used: 0x65
[   20.152719] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   20.153269] Registered led device: ath9k-phy0::radio
[   20.153294] Registered led device: ath9k-phy0::assoc
[   20.153321] Registered led device: ath9k-phy0::tx
[   20.153348] Registered led device: ath9k-phy0::rx
[  164.348773] ath9k 0000:03:00.0: PCI INT A disabled
[  164.348812] ath9k: Driver unloaded
[  184.000284] ath9k: `' invalid for parameter `nohwcrypt'
[  192.040865] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  192.040878] ath9k 0000:03:00.0: setting latency timer to 64
[  192.131136] ath: EEPROM regdomain: 0x65
[  192.131140] ath: EEPROM indicates we should expect a direct regpair map
[  192.131143] ath: Country alpha2 being used: 00
[  192.131144] ath: Regpair used: 0x65
[  192.132316] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  192.132953] Registered led device: ath9k-phy0::radio
[  192.132976] Registered led device: ath9k-phy0::assoc
[  192.132998] Registered led device: ath9k-phy0::tx
[  192.133020] Registered led device: ath9k-phy0::rx
[  330.788460] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  330.788497] ath: Failed to stop TX DMA!
[  351.645206] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  351.645246] ath: Failed to stop TX DMA!
[  352.388187] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  352.388224] ath: Failed to stop TX DMA!
[  497.580253] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  497.580293] ath: Failed to stop TX DMA!
[  527.570743] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  527.570783] ath: Failed to stop TX DMA!
[  530.658551] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  530.658590] ath: Failed to stop TX DMA!
[  746.256415] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  770.329952] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  770.329994] ath: Failed to stop TX DMA!
[  895.990219] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  895.990260] ath: Failed to stop TX DMA!
[  920.961165] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  920.961208] ath: Failed to stop TX DMA!
[  940.948696] ath: Failed to stop TX DMA in 100 msec after killing last frame
[  940.948736] ath: Failed to stop TX DMA!
[ 1012.762649] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 1012.762692] ath: Failed to stop TX DMA!
[ 1025.763247] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 1025.763287] ath: Failed to stop TX DMA!
[ 1057.721399] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 1057.721439] ath: Failed to stop TX DMA!
[ 1252.328890] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 1252.328932] ath: Failed to stop TX DMA!
[ 1298.265586] ath: Failed to stop TX DMA in 100 msec after killing last frame
[ 1298.265623] ath: Failed to stop TX DMA[B]!

[/B][B]6 ) Network configuration
[/B]PCI (sysfs)[B]7 ) Scan for networks:
[/B]nirjhar17@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 1C:7E:E5:58:7A:5B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"shantanu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004092fcd193
                    Extra: Last beacon: 27768ms ago
                    IE: Unknown: 00087368616E74616E75
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B080400000000000000000000000000000000000000[B]8 ) Ubuntu Version: 
[/B]nirjhar17@ubuntu:~$ lsb_release -d
Description:    Ubuntu 11.04[B]

9 ) Kernel/architecture (including 32 vs. 64 bit): 
[/B]nirjhar17@ubuntu:~$ uname -mr
2.6.38-11-generic i686

---

### Post by praseodym on 2011-09-11
You are using a mixed WPA/WPA2 encryption, this often causes problems with the network-manager, use WPA2-AES instead if possible.

If it is not possible, give Wicd a try:


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
sudo service network-manager stop
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service wicd start
```
Choose **wlan0** as interface name and **wext** as driver. Deactivate the network-manager in autostart.

Did you try the module parameter?

---

### Post by nirjhar17 on 2011-09-11
Hi,

I tried the steps given by you but i am not able to perform the last step **"sudo service wicd start"**

i got a error "wicd: unrecognized service"

i don't how to change the module parameters?

one more thing which i forgot here is after upgrading  my kernel, laptop is not able to detect the wifi network
 earlier after starting laptop it automatically detects the wifi network.
to resolve this i have to perform these three steps again...

[B]sudo modprobe -rf ath9k 
sudo modprobe -v ath9k nohwcrypt=1 
sudo service network-manager restart[/B]
than it starts working.

---

### Post by praseodym on 2011-09-12
Execute this command:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
This will load the module with this parameter at boot-up.

---

