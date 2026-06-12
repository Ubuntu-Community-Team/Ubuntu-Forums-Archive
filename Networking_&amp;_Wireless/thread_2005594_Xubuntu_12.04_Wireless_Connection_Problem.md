---
title: "Xubuntu 12.04 Wireless Connection Problem"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by prisoner1572 on 2012-06-17
&#65279;I'm having a problem with my wireless connection.
I built my own computer and installed Xubuntu 12.04 and everything pretty much worked fine. I got the wireless card afterwards and plugged it in and had no problem getting connected. It worked right out of the box without having to install anything. After a while I noticed an issue where the connection is interrupted and Xubuntu tries to connect to the router. It will ask me for the password, I will type it in and it will keep trying to connect and keep asking me for the password and never connect. I can get it to work again by rebooting the computer. It then connects without a problem.  I'm not sure what causes this because it may happen within the first few minutes or it might not happen at all. It happened a couple times today already when I was trying to download something through the software center, but I've been connected for a few hours  without trying to downloading anything.  When I went to try it again, within a few minutes it ran into the same problem. All my other wireless devices work during this time, too.


lspci

```
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller
    Flags: bus master, fast devsel, latency 0, IRQ 19
    I/O ports at c000 [size=256]
    Memory at fe400000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl8192se
    Kernel modules: rtl8192se

```iwconfig wlan0

```
wlan0     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:9A:45:CB:0D   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:590   Missed beacon:0

```lsmod

```
rtl8192se              99989  0 
rtlwifi               111202  1 rtl8192se
mac80211              506816  2 rtl8192se,rtlwifi
cfg80211              205544  2 rtlwifi,mac80211

```dmesg

```

[   10.699549] cfg80211: Calling CRDA to update world regulatory domain
[   10.709056] rtl8192se 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.709062] rtl8192se 0000:06:00.0: setting latency timer to 64
[   10.721461] rtl8192se: rtl8192ce: FW Power Save off (module option)
[   10.721537] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   10.721537] Loading firmware rtlwifi/rtl8192sefw.bin
[   10.722702] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.722705] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722714] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.722716] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722717] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.722718] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722719] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.722721] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722722] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.722724] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722725] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.722726] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722728] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.722729] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722730] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.722732] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722733] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.722734] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722736] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.722737] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722738] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.722740] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722741] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.722743] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722744] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.722745] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.722747] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   10.722754] cfg80211: Pending regulatory request, waiting for it to be processed...
[   10.722869] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   10.725683] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.745823] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   10.745825] cfg80211: World regulatory domain updated:
[   10.745826] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.745828] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.745829] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.745831] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.745832] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.745833] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.745841] cfg80211: Calling CRDA for country: EC
[   10.747704] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.747706] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747708] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.747709] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747710] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.747712] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747713] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.747715] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747716] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.747717] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747719] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.747720] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747721] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.747723] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747724] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.747726] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747727] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.747728] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747729] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.747731] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747732] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.747734] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747735] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.747736] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747738] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.747739] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.747740] cfg80211: Disabling freq 2484 MHz
[   10.747742] cfg80211: Regulatory domain changed to country: EC
[   10.747743] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.747744] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   10.747746] cfg80211:     (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[   10.747747] cfg80211:     (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[   10.747749] cfg80211:     (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)

...

[   11.608353] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.650988] ADDRCONF(NETDEV_UP): wlan0: link is not ready

...

[   14.291454] wlan0: authenticate with 00:17:9a:45:cb:0d (try 1)
[   14.293000] wlan0: authenticated
[   14.312865] wlan0: associate with 00:17:9a:45:cb:0d (try 1)
[   14.315656] wlan0: RX AssocResp from 00:17:9a:45:cb:0d (capab=0x431 status=0 aid=2)
[   14.315661] wlan0: associated
[   14.316877] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.464678] wlan0: no IPv6 routers present

```sudo lshw -C network

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 8c:89:a5:30:df:ed
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:49 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 10
       serial: 00:08:54:a2:bf:f4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.2.0-25-generic firmware=N/A ip=192.168.0.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:c000(size=256) memory:fe400000-fe403fff

```iwlist scan

```
wlan0     Scan completed :
          Cell 01 - Address: 00:17:9A:45:CB:0D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000023b6df181
                    Extra: Last beacon: 56800ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```lsb_release -d

```
Description:    Ubuntu 12.04 LTS
```uname -mr

```
3.2.0-25-generic x86_64

```sudo /etc/init.d/networking restart
 
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

```

---

### Post by wildmanne39 on 2012-06-18
Hi, do the second set of commands in post 2,  then what is in post 4.
Thanks

---

### Post by prisoner1572 on 2012-06-18
Is this what you were looking for?

lspci -nn | grep 'Realtek'

```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)

```


not sure about wlan_module_name from #4

---

### Post by wildmanne39 on 2012-06-18
Hi, sorry I forgot to put in the link to the page that I wanted you to go to, then do the second set of commands in post 2, then what is in post 4.
[http://ubuntuforums.org/showthread.php?p=12034950#post12034950](http://ubuntuforums.org/showthread.php?p=12034950#post12034950)
I should not post when I am tired.
Thanks

---

### Post by prisoner1572 on 2012-06-18
Here is the output for nm-tool

```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [dlink] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        00:08:54:A2:BF:F4

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *dlink:          Infra, 00:17:9A:45:CB:0D, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA

  IPv4 Settings:
    Address:         192.168.0.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


```

Is that all you wanted from post #2?
Also made the changes from post #4.

---

### Post by wildmanne39 on 2012-06-18
Hi, do this procedure in post 2.
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```
and follow the rest of the directions on the page and I think you will be able to connect.

I also recommend going into your router settings and changing your encryption to wpa2 only not wpa or wep or wpa2/wpa, you will need to type something like 192.168.0.1 into your web browser with a wired connection to your router to change that setting.

Did you make the changes in post 4 after your ran the nm-tool command because they do not show up in the info you posted.
Thanks

---

### Post by prisoner1572 on 2012-06-18
I made the change on the router to WPA2 and reconnected my wireless connection on the computer, but the output still shows the connection as WPA:

```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [dlink] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        00:08:54:A2:BF:F4

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *dlink:          Infra, 00:17:9A:45:CB:0D, Freq 2437 MHz, Rate 54 Mb/s, Strength 78 WPA

  IPv4 Settings:
    Address:         192.168.0.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4


```

Also ran the code you showed and it only asks for my password and then does nothing.

---

### Post by wildmanne39 on 2012-06-18
Hi, after you enter your password it will open a blank file then you paste the line in it from post 2 to the file and follow the directions in  post 2 for saving and then rebooting the computer.

Also go to the top of the screen and click on the internet icon go to edit connections>wireless then wireless security and set it to wpa/wpa2 in network manager.

When you were in the router settings did you save the settings after you changed it to wpa2?
Thanks

---

### Post by prisoner1572 on 2012-06-18
I rebooted everything again and this time it shows WPA2:

```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [dlink] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        00:08:54:A2:BF:F4

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *dlink:          Infra, 00:17:9A:45:CB:0D, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA2

  IPv4 Settings:
    Address:         192.168.0.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4

```

Also found out I didn't have gedit so thats why I wasn't getting that window. I installed it and ran the command and added the line but I changed rtl8192ce.conf to rtl8192se.conf since ce showed as the other guys driver and se showed up as mine.

Anything else you need to know or that I should do?

---

### Post by wildmanne39 on 2012-06-18
Hi, that should fix your issue try it for a while and see and if it does please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by prisoner1572 on 2012-06-18
It looks like it worked. I got through a whole download without losing the connection. Thanks for your help!

---

### Post by wildmanne39 on 2012-06-18
Your welcome!
Enjoy

---

### Post by prisoner1572 on 2012-06-18
Changing this back to an unsolved mystery. It worked for a few hours but now just did it again.

---

### Post by wildmanne39 on 2012-06-18
Hi, please show the contents of:
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```
and if it is named > /etc/modprobe.d/rtl8192[COLOR="Red"]ce[/COLOR].conf
change it to > /etc/modprobe.d/rtl8192[COLOR="Red"]se[/COLOR].conf
then save and close gedit and reboot.

Also go into your router settings again and make sure your speed is set to b/g not b/g/n because the driver does not handle N speed well and it is unstable.
Thanks

---

### Post by prisoner1572 on 2012-06-19
My router is older and doesn't have N.

I did change ce to se and this is what is in the file:

```
options rtl8192se swenc=1
```

it does seem to be happening less often but still can't download the really big programs through software center because it doesn't last long enough

---

### Post by wildmanne39 on 2012-06-19
Hi, did you set IPV6 to ignore in the network settings?
Thanks

---

### Post by prisoner1572 on 2012-06-19
yes, I did that too.

---

### Post by wildmanne39 on 2012-06-19
Hi, I am doing some research, this does not happen when the system is left unattended for a few minutes where it might be going into suspend, like when it goes back to the login screen?
Thanks

---

### Post by wildmanne39 on 2012-06-19
Hi, I believe this is what you should do and you must do it in this order or you will not have internet to install the package that you need.

```
sudo apt-get install wicd
```
Then:
```
sudo apt-get purge network-manager network-manager-gnome
```
You may have to open dash to set up wicd.
Thanks

---

### Post by prisoner1572 on 2012-06-19
Installed WICD and removed Network Manager.
Are there any settings I should change in it?

Also, the disconnects were happening whether I was using it or had stepped away for a while. I might be able to leave it for an hour and it be fine and sometimes it wouldn't. I don't have automatic suspend currently set up. I only have a screen saver.

---

### Post by wildmanne39 on 2012-06-19
Hi, I would set the dns server to google and disable IPV6 just like in network manager, but I am not sure exactly where to disable IPV6 because I do not have wicd installed.
Thanks

---

### Post by prisoner1572 on 2012-06-20
It looks like it worked this time since I had it on all day and made it through a big download without it disconnecting. Thanks for your help!

---

### Post by wildmanne39 on 2012-06-20
Hi, I am glad it is working!!!
Enjoy

---

### Post by langmarp on 2012-10-14
could you please help me with a similar problem?
[http://ubuntuforums.org/showthread.php?p=12295844#post12295844](http://ubuntuforums.org/showthread.php?p=12295844#post12295844)

---

