---
title: "Duel booted Windows Vista and Ubuntu 12.04"
date: 2012-09-04
forum: Networking &amp; Wireless
---

### Post by SUPERFITTER on 2012-09-04
I duel booted Windows Vista and Ubuntu 12.04. It checks for wireless but cannot connect. I have tried chilis555 method:

[http://ubuntuforums.org/showthread.php?t=1785620](http://ubuntuforums.org/showthread.php?t=1785620)

This is the information I got:

dennis@dennis:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G94 [GeForce 9700M GTS] [10de:062a] (rev a1)
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
14:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
20:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380]
20:00.1 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
20:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
20:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
20:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]

dennis@dennis:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"SUPERFITTER1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:B6:B6:53:35   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

dennis@dennis:~$ 

Then this:
dennis@dennis:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

dennis@dennis:~$ dmesg | grep b43
dennis@dennis:~$ 

Any ideas?   Thank You in advance.

---

### Post by chili555 on 2012-09-04
The chili555 method you linked won't work for you; you don't have a Broadcom card. You have:> 14:00.0 Network controller [0280]: [COLOR="Red"]Intel[/COLOR] Corporation WiFi Link 5100 [8086:4232]Please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, we'll write one quick file and make it persistent.

---

### Post by SUPERFITTER on 2012-09-04
Thank You for the help chili555

dennis@dennis:~$ sudo modprobe -r iwlwifi
[sudo] password for dennis: 
dennis@dennis:~$ sudo modprobe iwlwifi 11n_disable=1
dennis@dennis:~$

Not much here.  What is the next step?

---

### Post by chili555 on 2012-09-05
> Not much here.Meaning what? Did you expect some confirmation from the terminal? What you got, this:> dennis@dennis:~$ sudo modprobe iwlwifi 11n_disable=1
[email]dennis@dennis:~$...means[/email], roughly, command accepted and executed and there are no errors or warnings to report. As far as I know, that's exactly what you wanted.

Or does 'not much here' mean there was no change in your ability to connect? When you say 'it checks for wireless but cannot connect,' does that mean you are challenged for an encryption key and it's never accepted or what?

If you'd like some help. we'd appreciate more descriptive responses. 

If you have rebooted, you'll need to repeat what I suggested. You might also try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N
```

---

### Post by SUPERFITTER on 2012-09-05
I guess I was looking for more text to appear. 

A pop up asks to enter  my wireless password which I type in and then it's connecting.  It then has another pop up that says   activation of network connection  failed and wireless network disconnected.


dennis@dennis:~$ sudo modprobe -r iwlwifi
[sudo] password for dennis: 
dennis@dennis:~$ sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N
dennis@dennis:~$

---

### Post by SUPERFITTER on 2012-09-05
I rebooted no change.  

The wireless says   activation of network connection  failed and wireless network: disconnected . It then brings up my neighbors wireless and asks to put in his password for his wireless network.

It only asked for my password once, which I inserted and has never asked again.

I entered all four codes that you posted and rebooted.  Nothing changed, still trying to connect.  Activation of network connection  failed and wireless network: disconnected.

---

### Post by chili555 on 2012-09-05
> A pop up asks to enter my wireless password which I type in and then it's connecting. It then has another pop up that says activation of network connection failed and wireless network disconnected.
I see now. Thank you.> I entered all four codes that you posted and rebooted.Every time you reboot, these temporary changes go away. Please do not reboot. If they help, we can write a file and make them permanent. 

Is your router set to WPA2 only or the tricky mixed mode WPA and WPA2? WPA2 only is preferred.

---

### Post by SUPERFITTER on 2012-09-05
> **chili555 said:**
> 

Is your router set to WPA2 only or the tricky mixed mode WPA and WPA2? WPA2 only is preferred.

I'm not sure, how do I check?

---

### Post by chili555 on 2012-09-05
Run:```
nm-tool
```Does your network show as WPA WPA2? If so, I'd go into the administration pages of the router and change it. Please see attached.

---

### Post by SUPERFITTER on 2012-09-06
Hi chili555
I ran nm - tool:

dennis@dennis:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        00:21:5D:53:6B:BE

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1E:EC:3F:A9:5E

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.10.10.105
    Prefix:          24 (255.255.255.0)
    Gateway:         10.10.10.1

    DNS:             75.75.76.76
    DNS:             75.75.75.75


dennis@dennis:~$ 

I have an other laptop that you helped me with last year. 

[http://ubuntuforums.org/showthread.php?t=1785620](http://ubuntuforums.org/showthread.php?t=1785620)

I have it updated to Ubuntu 12.04 and it runs great on this wireless network.  It has a different wireless card that you pointed out to me.  I was wondering if there is something else that I have to do to this laptop that would configure it to any wireless network?

Thank You

---

### Post by chili555 on 2012-09-06
> - Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: iwlwifi
[COLOR="Red"]State: unavailable[/COLOR]
Default: no
HW Address: 00:21:5D:53:6B:BE

Capabilities:

Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points
[COLOR="Red"]None??[/COLOR]
We wonder why it's unavailable and see no access points. It may be unavailable because Network Manager will disallow wireless if you have wired ethernet available and you do. Please detach the ethernet cable, wait a few moments and try again:```
nm-tool
```Is it still unavailable?

It may be unavailable because the wireless switch is off. You checked previously, but let's double-check:```
rfkill list all
```It may be unavailable for some reason we haven't yet discovered. Let's check the message logs:```
dmesg | grep iwl
```

---

### Post by SUPERFITTER on 2012-09-06
Hi chili555
I disconnected the cable and ran the codes.

dennis@dennis:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: wlan0  [Auto SUPERFITTER1] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        00:21:5D:53:6B:BE

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Bonkowski-N:     Infra, 00:23:69:15:B1:AC, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WEP
    SUPERFITTER1:    Infra, 00:16:B6:B6:53:35, Freq 2462 MHz, Rate 54 Mb/s, Strength 82 WEP


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:1E:EC:3F:A9:5E

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


dennis@dennis:~$ 
dennis@dennis:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
dennis@dennis:~$ dmesg | grep iwl
[   14.195260] iwlwifi 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.195270] iwlwifi 0000:14:00.0: setting latency timer to 64
[   14.195295] iwlwifi 0000:14:00.0: pci_resource_len = 0x00002000
[   14.195298] iwlwifi 0000:14:00.0: pci_resource_base = f8720000
[   14.195300] iwlwifi 0000:14:00.0: HW Revision ID = 0x0
[   14.195387] iwlwifi 0000:14:00.0: irq 47 for MSI/MSI-X
[   14.195423] iwlwifi 0000:14:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   14.195483] iwlwifi 0000:14:00.0: L1 Disabled; Enabling L0S
[   14.217245] iwlwifi 0000:14:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   14.217249] iwlwifi 0000:14:00.0: Device SKU: 0Xf0
[   14.218787] iwlwifi 0000:14:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.766892] iwlwifi 0000:14:00.0: loaded firmware version 8.83.5.1 build 33692
[   14.786790] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.802814] iwlwifi 0000:14:00.0: L1 Disabled; Enabling L0S
[   14.805782] iwlwifi 0000:14:00.0: Radio type=0x1-0x2-0x0
[   14.925121] iwlwifi 0000:14:00.0: L1 Disabled; Enabling L0S
[   14.928163] iwlwifi 0000:14:00.0: Radio type=0x1-0x2-0x0
dennis@dennis:~$

---

### Post by chili555 on 2012-09-06
> dennis@dennis:~$ dmesg | grep iwl
[ 14.195260] iwlwifi 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 14.195270] iwlwifi 0000:14:00.0: setting latency timer to 64
[ 14.195295] iwlwifi 0000:14:00.0: pci_resource_len = 0x00002000
[ 14.195298] iwlwifi 0000:14:00.0: pci_resource_base = f8720000
[ 14.195300] iwlwifi 0000:14:00.0: HW Revision ID = 0x0
[ 14.195387] iwlwifi 0000:14:00.0: irq 47 for MSI/MSI-X
<snip>Looks perfect!> Wireless Access Points
Bonkowski-N: Infra, 00:23:69:15:B1:AC, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WEP
[COLOR="Red"]SUPERFITTER1: Infra, 00:16:B6:B6:53:35, Freq 2462 MHz, Rate 54 Mb/s, Strength 82 WEP[/COLOR]Also perfect; now we see that the card sees your network. When it's trying to connect, I assume you are asked for your WEP key. How many characters is it? Have you put any settings in Network Manager? Usually, none are needed and I recommend you delete them.

WEP encryption is quite insecure; I recommend you change the router to WPA2.

---

### Post by SUPERFITTER on 2012-09-06
I assume you are asked for your WEP key. 
It does not ask for my WEP key?

How many characters is it?  
Ten

Have you put any settings in Network Manager?  
No  

In network connections, what should wireless, IPv4Settings, IPv6Settings and Wireless Security have in them?   Nothing?

I have a linksys router, I tried for hours to get WPA2 to work with tech support help, but could not make it work.  So I have to use WEP.  

I'm not that concerned with WEP because I'm a long way from other houses and the signal gets weak fast outside because my router is in the basement.

Thank You

---

### Post by chili555 on 2012-09-06
> It does not ask for my WEP key?No? When you click the Network manager icon and see your network SUPERFITTER1 and click on it, doesn't it ask for your key?> How many characters is it?
TenGood!> In network connections, what should wireless, IPv4Settings, IPv6Settings and Wireless Security have in them? Nothing?Please see attached. Be sure it says Infrastructure and, under IPv6, Ignore.

---

### Post by SUPERFITTER on 2012-09-06
When I go to network connections> wireless and edit my name> wireless.  
If I delete:
 SSID: SUPERFITTER1 and Device MAC address

I cannot save that setting.

Mode: infrastructure is OK

In IPv6
Method: Ignore, I can save that.

Network manager icon, is that the same as Network Connection, if not where is it located?

---

### Post by chili555 on 2012-09-06
> Network manager icon, is that the same as Network Connection, if not where is it located?It is located in the panel at the top right. Please see attached. If you don't have it and the Network Manager applet is not running, that may be the real problem!!

Let's try to work with what we have first:> When I go to network connections> wireless and edit my name> wireless. Leave the network name and MAC address in place. See if you can add your encryption type, probably 40/128-bit WEP and your 10 character WEP key. Select 'connect automatically' and save. See what the logs say after you save:```
sudo tail -f /var/log/syslog
```You will see activity as it is logged and will see if you connect. Stop with Ctrl+c.

Very interesting!

---

### Post by SUPERFITTER on 2012-09-07
I found the Network Manager applet and it is running. I see the beacon being sent. 

 In Wireless Security 40/128-bit WEP and your 10 character WEP key are already there.
I see no where else to add 40/128-bit WEP and your 10 character WEP key?  I ran a log so you can see what is happening at this point.

dennis@dennis:~$ sudo tail -f /var/log/syslog
[sudo] password for dennis: 
Sep  7 00:18:04 dennis dhclient: Sending on   Socket/fallback
Sep  7 00:18:04 dennis dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Sep  7 00:18:05 dennis avahi-daemon[957]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::221:5dff:fe53:6bbe.
Sep  7 00:18:05 dennis avahi-daemon[957]: New relevant interface wlan0.IPv6 for mDNS.
Sep  7 00:18:05 dennis avahi-daemon[957]: Registering new address record for fe80::221:5dff:fe53:6bbe on wlan0.*.
Sep  7 00:18:07 dennis dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Sep  7 00:18:10 dennis dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Sep  7 00:18:14 dennis dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Sep  7 00:18:14 dennis kernel: [ 2012.144036] wlan0: no IPv6 routers present
Sep  7 00:18:23 dennis dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Sep  7 00:18:24 dennis NetworkManager[951]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep  7 00:18:24 dennis NetworkManager[951]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep  7 00:18:24 dennis NetworkManager[951]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep  7 00:18:24 dennis NetworkManager[951]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

---

### Post by chili555 on 2012-09-07
> Sep 7 00:18:05 dennis avahi-daemon[957]: Joining mDNS multicast group on interface [COLOR="Red"]wlan0.IPv6[/COLOR] with address fe80::221:5dff:fe53:6bbe.
Sep 7 00:18:05 dennis avahi-daemon[957]: New relevant interface [COLOR="Red"]wlan0.IPv6[/COLOR] for mDNS.
Sep 7 00:18:05 dennis avahi-daemon[957]: Registering new address record for fe80::221:5dff:fe53:6bbe on wlan0.*.Is IPv6 set to Ignore? 

Have you double-checked the WEP key? It is case-sensitive. The key 12345abcde is not the same as 12345abCde.

Let's have a look at:```
sudo cat /var/log/syslog | grep etwork | tail -n20
ifconfig
iwconfig
```

---

### Post by SUPERFITTER on 2012-09-07
Is IPv6 set to Ignore? 
Yes

Have you double-checked the WEP key?
Yes

dennis@dennis:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for dennis: 
Sep  7 11:36:54 dennis NetworkManager[932]: <info> Activation (wlan0/wireless): connection 'Auto SUPERFITTER1' has security, and secrets exist.  No new secrets needed.
Sep  7 11:36:54 dennis NetworkManager[932]: <info> Config: added 'ssid' value 'SUPERFITTER1'
Sep  7 11:36:54 dennis NetworkManager[932]: <info> Config: added 'scan_ssid' value '1'
Sep  7 11:36:54 dennis NetworkManager[932]: <info> Config: added 'key_mgmt' value 'NONE'
Sep  7 11:36:54 dennis NetworkManager[932]: <info> Config: added 'auth_alg' value 'OPEN'
Sep  7 11:36:54 dennis NetworkManager[932]: <info> Config: added 'wep_key0' value '<omitted>'
Sep  7 11:36:54 dennis NetworkManager[932]: <info> Config: added 'wep_tx_keyidx' value '0'
Sep  7 11:36:54 dennis NetworkManager[932]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep  7 11:36:54 dennis NetworkManager[932]: <info> Config: set interface ap_scan to 1
Sep  7 11:36:54 dennis NetworkManager[932]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep  7 11:36:57 dennis NetworkManager[932]: <info> (wlan0): supplicant interface state: scanning -> associating
Sep  7 11:36:57 dennis NetworkManager[932]: <info> (wlan0): supplicant interface state: associating -> completed
Sep  7 11:36:57 dennis NetworkManager[932]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'SUPERFITTER1'.
Sep  7 11:36:57 dennis NetworkManager[932]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep  7 11:36:57 dennis NetworkManager[932]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep  7 11:36:57 dennis NetworkManager[932]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep  7 11:36:57 dennis NetworkManager[932]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep  7 11:36:57 dennis NetworkManager[932]: <info> dhclient started with pid 2198
Sep  7 11:36:57 dennis NetworkManager[932]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep  7 11:36:57 dennis NetworkManager[932]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
dennis@dennis:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:3f:a9:5e  
          inet6 addr: fe80::21e:ecff:fe3f:a95e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:486006 (486.0 KB)  TX bytes:78900 (78.9 KB)
          Interrupt:46 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7505 (7.5 KB)  TX bytes:7505 (7.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:53:6b:be  
          inet6 addr: fe80::221:5dff:fe53:6bbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:20120 (20.1 KB)

dennis@dennis:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"SUPERFITTER1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:B6:B6:53:35   
          Bit Rate=2 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

dennis@dennis:~$ 

The wireless beacon is on a loop, it tries my network for awhile and then times out. Next it goes to my neighbors network and you can see the beacon going trying to connect to his network and then it times out again. It tries to connect to my neighbors network  a second time and then times out.  After a few minutes it starts with my network and repeats over and over again.

It never asks for a wireless network password, my network or my neighbors anymore?

Even when I'm connected to a wired connection the wireless is still looking for a wireless network?

---

### Post by chili555 on 2012-09-07
Arrgh! This is a tough one! Let's try it the other way around. Delete everything you can from the Network Manager windows. Save and detach the ethernet cable and try to connect again. Ideally, NM ought to look for networks, allow you to click on one, ask for the network key and connect. Yours seems to do some but not all of this.

This is mysterious:> Sep 7 11:36:57 dennis NetworkManager[932]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful. Connected to wireless network 'SUPERFITTER1'....and this looks like you are connected:> wlan0 IEEE 802.11abgn ESSID:"SUPERFITTER1"
Mode:Managed Frequency:2.462 GHz Access Point: 00:16:B6:B6:53:35
Bit Rate=2 Mb/s Tx-Power=15 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=69/70 Signal level=-41 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0But you are not.

We don't even see any messages that suggest NM stopped the established connection for any reason.

---

### Post by SUPERFITTER on 2012-09-07
chili555

I did as you asked. I even rebooted laptop and my router. Nothing changed either way.

I'm now wired to my router, but the beacon is still trying to connect to my network wireless and then my neighbors wireless.  

Could I need a driver for my laptop that is different than the one I have installed?  Could I be missing something in Ubuntu 12.04?

---

### Post by SUPERFITTER on 2012-09-08
Hi chili555

I found the problem.  I went over all the posts and when I went to: 

Network manager> Edit Connections> Wireless> My name> Edit> Wireless Security> Key> 

I put a check mark in show key and found I had one number wrong, I was off by one number.  For some reason I never paid attention to that box because I just typed the number in with the little stars showing ***********.  I feel like an idiot for not checking that box.

I am so sorry for using so much of your time, but hope others will learn from my mistake. 

Thank You Very Much

I will us the laptop for a few days and see if there are any other problems, if not then I will post problem solved.

---

### Post by chili555 on 2012-09-08
Whew! I am glad it was as simple as that and there were no more serious issues! I'm glad it's working by whatever means. 

I will always be happy to help you any way I can. Have fun!

---

