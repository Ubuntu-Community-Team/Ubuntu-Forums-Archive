---
title: "HP dv7 1245dx - Wireless Network No Workie"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by loaba on 2010-03-04
What is it with Linux and wireless networking? :(

OS: Ubuntu 9.10 64b (new install)
Platform: Laptop, HP dv7 1245dx

Issue: onboard wireless network adapter not working properly. I can see my SSID (and halfway connect), but I cannot fully connect and access the network or internet.

Is there a tool that I can use to troubleshoot the device in Terminal?

As always, any help would be much appreciated.

Thanks, Jon

Edit: wired network adapter does function properly

---

### Post by loaba on 2010-03-04
lspci results

```
loaba@HAL:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
**09:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)**
**0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)**
```

---

### Post by chili555 on 2010-03-04
> Is there a tool that I can use to troubleshoot the device in Terminal?When you are connected, halfway, please let us see:```
iwconfig
ping -c3 www.google.com
ping -c3 74.125.45.147
```Thanks.

---

### Post by loaba on 2010-03-04
Wireless
```
loaba@HAL:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

loaba@HAL:~$ ping -c3 www.google.com
ping: unknown host www.google.com
loaba@HAL:~$ ping -c3 74.125.45.147
```

Wired
```
loaba@HAL:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

loaba@HAL:~$ ping -c3 www.google.com
PING www.l.google.com (74.125.127.103) 56(84) bytes of data.
64 bytes from pz-in-f103.1e100.net (74.125.127.103): icmp_seq=1 ttl=53 time=86.9 ms
64 bytes from pz-in-f103.1e100.net (74.125.127.103): icmp_seq=2 ttl=53 time=86.3 ms
64 bytes from pz-in-f103.1e100.net (74.125.127.103): icmp_seq=3 ttl=53 time=86.1 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2008ms
rtt min/avg/max/mdev = 86.129/86.482/86.946/0.418 ms
loaba@HAL:~$ ping -c3 74.125.45.147
```

Now I'm not even getting past authentication with the wireless card.

---

### Post by chili555 on 2010-03-04
Is the ethernet cable attached? We can't test if it is.

---

### Post by loaba on 2010-03-04
First output is minus the Ethernet cable. I will try again to verify.

Cable disconnected
```
loaba@HAL:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

loaba@HAL:~$ ping -c3 www.google.com
ping: unknown host www.google.com
loaba@HAL:~$ ping -c3 74.125.45.147
[enter]
connect: Network is unreachable
```


So, now I can't even tease myself with the illusion of connectivity, the wireless is completely dead.

---

### Post by chili555 on 2010-03-04
It's not dead, it's working fine and waiting for an order to connect. When you click the Network Manager icon and see your network and ask it to connect, what happens, or doesn't? Any encryption in use: WEP, WPA or otherwise?

---

### Post by loaba on 2010-03-04
Initially, I would get a password box (I use WPA2 encryption), after entering the password, it would act like it was connected but I wouldn't be able to load internet pages.

With the ethernet cable connected; 
click network manager; 
Wired Network; etho

I can interact with it (meaning I can select "disconnect")

With the ethernet cable unplugged (wireless activity light showing active)
click network manager;
Wired Network; disconnected

I cannot interact with it (meaning I can't select it and choose from a list of detected WLAN's in the area)

---

### Post by chili555 on 2010-03-04
How about showing us:```
rfkill list
sudo iwlist wlan0 scan
```Thanks.

---

### Post by loaba on 2010-03-04
```
loaba@HAL:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
loaba@HAL:~$ sudo iwlist wlan0 scan
```

Is that "hard" as in hardware?

---

### Post by chili555 on 2010-03-04
> Is that "hard" as in hardware?Correct. Try pressing the wireless switch at the upper right and try *rfkill list* again. I am not at all sure that the Acer module *acer-wmi* doesn't have the button versus light reversed. The way to find out is to press the button and ignore the light, but check the terminal output and, more importantly, see if, with the wire detached, Network Manager wakes up.

---

### Post by loaba on 2010-03-04
Interesting... I pressed the button (light-key) and things started working for a few seconds. While typing this post, the light has flickered on and off.

---

### Post by loaba on 2010-03-04
```
loaba@HAL:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
loaba@HAL:~$ sudo iwlist wlan0 scan
```

Dare I press the freak'n button again?

---

### Post by chili555 on 2010-03-04
> rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
I think you keep your finger well away from whirling objects, detach the wire and make your next reply wirelessly!

---

### Post by loaba on 2010-03-04
Yup - we are wireless indeed. Thanks again and I need to start reading up on sudo commands etc.

---

### Post by chili555 on 2010-03-04
You made my night! Glad it's working. Enjoy!

---

