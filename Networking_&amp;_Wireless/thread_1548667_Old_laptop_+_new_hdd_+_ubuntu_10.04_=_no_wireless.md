---
title: "Old laptop + new hdd + ubuntu 10.04 = no wireless"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by Newbie Kowboy on 2010-08-08
I have an ACER TRAVELMATE 2420 laptop in which I replaced the defunct HDD and loaded UBUNTU 10.04 LTS. My old HDD is fried and Windows XP had been the OS. 
 
The Ubuntu OS loaded and it looks great. Major problem, so far, is that I cannot connect to the Internet via the Wireless component in the ACER. My laptop has the Broadcom BCM4318MPG internal wireless component.
 
I cannot capture a wireless connection. The 4318 seems to be "disabled". I've researched a number of Forums, FAQ's, etc., followed instructions for various commands, downloads of ndiswrapper/drivers/etc., but no luck and so I'm posting this thread. I'm looking for a clear, step-by-step approach to get the wireless working in order to connect to the Internet.
 
I apologize for the length of the details following, but I hope I've captured all of the correct info for analysis - thanks so much for any help!
 
Information:
 
**[FONT=Calibri]Machine Brand and Model:[/FONT]**
[FONT=Calibri][SIZE=3]Acer Travelmate 2420 Laptop[/SIZE][/FONT]
 
**[FONT=Calibri]Wireless Brand, Model and Wireless Chipset:[/FONT]**
[FONT=Calibri][SIZE=3]$ lspci [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]~$ lspci -nn | grep Broadcom [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]06:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)[/SIZE][/FONT]
 
**[FONT=Calibri]Interface[/FONT]**
[FONT=Calibri][SIZE=3]~$ ifconfig [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]eth0 Link encap:Ethernet HWaddr 00:0a:e4:f9:0c:2b [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]UP BROADCAST MULTICAST MTU:1500 Metric:1 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX packets:0 errors:0 dropped:0 overruns:0 frame:0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]collisions:0 txqueuelen:1000 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Interrupt:20 Base address:0x3000 [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]lo Link encap:Local Loopback [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]inet addr:127.0.0.1 Mask:255.0.0.0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]inet6 addr: ::1/128 Scope:Host [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]UP LOOPBACK RUNNING MTU:16436 Metric:1 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX packets:12 errors:0 dropped:0 overruns:0 frame:0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]collisions:0 txqueuelen:0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX bytes:720 (720.0 B) TX bytes:720 (720.0 B) [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]~$ iwconfig [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]lo no wireless extensions. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]eth0 no wireless extensions. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]wlan0 IEEE 802.11bg ESSID:off/any [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Retry long limit:7 RTS thr:off Fragment thr:off [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Power Management:off [/SIZE][/FONT]
 
**[FONT=Calibri]Modules:[/FONT]**
[FONT=Calibri][SIZE=3]~$ lsmod [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Module Size Used by [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]binfmt_misc 6587 1 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]fbcon 35102 71 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]tileblit 2031 1 fbcon [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]font 7557 1 fbcon [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bitblit 4707 1 fbcon [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]softcursor 1189 1 bitblit [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]vga16fb 11385 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]vgastate 8961 1 vga16fb [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ppdev 5259 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_intel8x0 25588 2 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_ac97_codec 100646 1 snd_intel8x0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ac97_bus 1002 1 snd_ac97_codec [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_pcm_oss 35308 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_mixer_oss 13746 1 snd_pcm_oss [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_pcm 70662 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_seq_dummy 1338 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_seq_oss 26726 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_seq_midi 4557 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_rawmidi 19056 1 snd_seq_midi [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]arc4 1153 2 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]joydev 8708 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]pcmcia 33024 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]b43 157218 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_timer 19098 2 snd_pcm,snd_seq [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]mac80211 204922 1 b43 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]i915 282354 3 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd 54148 14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]yenta_socket 20408 1 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]drm_kms_helper 29297 1 i915 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]rsrc_nonstatic 10015 1 yenta_socket [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]cfg80211 126485 2 b43,mac80211 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]drm 162471 4 i915,drm_kms_helper [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]acer_wmi 13861 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]pcmcia_core 32964 3 pcmcia,yenta_socket,rsrc_nonstatic [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]soundcore 6620 1 snd [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]led_class 2864 2 b43,acer_wmi [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]intel_agp 24177 2 i915 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]agpgart 31724 2 drm,intel_agp [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]i2c_algo_bit 5028 1 i915 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]psmouse 63245 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]serio_raw 3978 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_page_alloc 7076 2 snd_intel8x0,snd_pcm [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]video 17375 1 i915 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]output 1871 1 video [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]lp 7028 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]parport 32635 2 ppdev,lp [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]8139too 18545 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]8139cp 16186 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ssb 37336 1 b43 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]mii 4381 2 8139too,8139cp [/SIZE][/FONT]
 
**[FONT=Calibri]Kernal Boot Messages:[/FONT]**
[FONT=Calibri][SIZE=3][ 11.532286] b43-phy0: Broadcom 4318 WLAN found (core revision 9) [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.541264] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.566648] type=1505 audit(1281299176.525:5): operation="profile_load" pid=612 name="/usr/share/gdm/guest-session/Xsession" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.585233] type=1505 audit(1281299176.545:6): operation="profile_replace" pid=615 name="/sbin/dhclient3" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.586045] type=1505 audit(1281299176.545:7): operation="profile_replace" pid=615 name="/usr/lib/NetworkManager/nm-dhcp-client.action" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.586489] type=1505 audit(1281299176.545:8): operation="profile_replace" pid=615 name="/usr/lib/connman/scripts/dhclient-script" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.596253] type=1505 audit(1281299176.557:9): operation="profile_load" pid=618 name="/usr/bin/evince" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.680941] type=1505 audit(1281299176.641:10): operation="profile_load" pid=618 name="/usr/bin/evince-previewer" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.686753] eth0: link down [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]686881] ADDRCONF(NETDEV_UP): eth0: link is not ready [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.716352] type=1505 audit(1281299176.677:11): operation="profile_load" pid=618 name="/usr/bin/evince-thumbnailer" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.718414] phy0: Selected rate control algorithm 'minstrel' [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.719365] Registered led device: b43-phy0::tx [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.719388] Registered led device: b43-phy0::rx [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.719410] Registered led device: b43-phy0::radio [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.719519] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.810402] b43 ssb0:0: firmware: requesting b43/ucode5.fw [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.817674] [drm] initialized overlay support [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.259878] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.265400] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.265493] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.265580] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.288139] b43 ssb0:0: firmware: requesting b43/ucode5.fw [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.293416] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.303812] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.303904] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.303991] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. [/SIZE][/FONT]
 
**[FONT=Calibri]NETWORK CONFIGURATION[/FONT]**
[FONT=Calibri][SIZE=3]*-network:0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]description: Network controller [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]vendor: Broadcom Corporation [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]physical id: 5 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bus info: pci@0000:06:05.0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]version: 02 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]width: 32 bits [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]clock: 33MHz [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]capabilities: bus_master [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]configuration: driver=b43-pci-bridge latency=32 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]resources: irq:21 memory:b0100000-b0101fff [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*-network:1 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]description: Ethernet interface [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]product: RTL-8139/8139C/8139C+ [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]vendor: Realtek Semiconductor Co., Ltd. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]physical id: 7 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bus info: pci@0000:06:07.0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]logical name: eth0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]version: 10 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]serial: 00:0a:e4:f9:0c:2b [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]size: 10MB/s [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]capacity: 100MB/s [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]width: 32 bits [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]clock: 33MHz [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]resources: irq:20 ioport:3000(size=256) memory:b0102000-b01020ff [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*-network DISABLED [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]description: Wireless interface [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]physical id: 1 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]logical name: wlan0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]serial: 00:16:ce:23:79:b7 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]capabilities: ethernet physical wireless [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg [/SIZE][/FONT]
 
**[FONT=Calibri]NETWORKS[/FONT]**
[FONT=Calibri][SIZE=3]~$ iwlist scan [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]lo Interface doesn't support scanning. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]eth0 Interface doesn't support scanning. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]wlan0 Failed to read scan data : Network is down [/SIZE][/FONT]
 
**[FONT=Calibri]UBUNTU VERSION[/FONT]**
[FONT=Calibri][SIZE=3]Description: Ubuntu 10.04 LTS [/SIZE][/FONT]
 
**[FONT=Calibri]KERNAL/ARCHITECTURE[/FONT]**
[FONT=Calibri][SIZE=3]2.6.32-21-generic i686 [/SIZE][/FONT]
 
**[FONT=Calibri]RESTARTING THE NETWORK[/FONT]**
[FONT=Calibri][SIZE=3]Reconfiguring network interfaces...[/SIZE][/FONT]
 
**[FONT=Calibri]NDISWRAPPER[/FONT]**
[FONT=Calibri][SIZE=3]~$ ndiswrapper -l [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bcmwl5a : driver installed [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]device (14E4:4318) present (alternate driver: ssb) [/SIZE][/FONT]

---

### Post by walterav on 2010-08-08
> **Newbie Kowboy said:**
> I have an ACER TRAVELMATE 2420 laptop in which I replaced the defunct HDD and loaded UBUNTU 10.04 LTS. My old HDD is fried and Windows XP had been the OS. 
 
The Ubuntu OS loaded and it looks great. Major problem, so far, is that I cannot connect to the Internet via the Wireless component in the ACER. My laptop has the Broadcom BCM4318MPG internal wireless component.
 
I cannot capture a wireless connection. The 4318 seems to be "disabled". I've researched a number of Forums, FAQ's, etc., followed instructions for various commands, downloads of ndiswrapper/drivers/etc., but no luck and so I'm posting this thread. I'm looking for a clear, step-by-step approach to get the wireless working in order to connect to the Internet.
 
I apologize for the length of the details following, but I hope I've captured all of the correct info for analysis - thanks so much for any help!
 
Information:
 
**[FONT=Calibri]Machine Brand and Model:[/FONT]**
[FONT=Calibri][SIZE=3]Acer Travelmate 2420 Laptop[/SIZE][/FONT]
 
**[FONT=Calibri]Wireless Brand, Model and Wireless Chipset:[/FONT]**
[FONT=Calibri][SIZE=3]$ lspci [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]~$ lspci -nn | grep Broadcom [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]06:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)[/SIZE][/FONT]
 
**[FONT=Calibri]Interface[/FONT]**
[FONT=Calibri][SIZE=3]~$ ifconfig [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]eth0 Link encap:Ethernet HWaddr 00:0a:e4:f9:0c:2b [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]UP BROADCAST MULTICAST MTU:1500 Metric:1 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX packets:0 errors:0 dropped:0 overruns:0 frame:0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]collisions:0 txqueuelen:1000 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Interrupt:20 Base address:0x3000 [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]lo Link encap:Local Loopback [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]inet addr:127.0.0.1 Mask:255.0.0.0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]inet6 addr: ::1/128 Scope:Host [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]UP LOOPBACK RUNNING MTU:16436 Metric:1 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX packets:12 errors:0 dropped:0 overruns:0 frame:0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]collisions:0 txqueuelen:0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX bytes:720 (720.0 B) TX bytes:720 (720.0 B) [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]~$ iwconfig [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]lo no wireless extensions. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]eth0 no wireless extensions. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]wlan0 IEEE 802.11bg ESSID:off/any [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Retry long limit:7 RTS thr:off Fragment thr:off [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Power Management:off [/SIZE][/FONT]
 
**[FONT=Calibri]Modules:[/FONT]**
[FONT=Calibri][SIZE=3]~$ lsmod [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Module Size Used by [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]binfmt_misc 6587 1 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]fbcon 35102 71 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]tileblit 2031 1 fbcon [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]font 7557 1 fbcon [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bitblit 4707 1 fbcon [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]softcursor 1189 1 bitblit [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]vga16fb 11385 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]vgastate 8961 1 vga16fb [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ppdev 5259 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_intel8x0 25588 2 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_ac97_codec 100646 1 snd_intel8x0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ac97_bus 1002 1 snd_ac97_codec [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_pcm_oss 35308 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_mixer_oss 13746 1 snd_pcm_oss [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_pcm 70662 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_seq_dummy 1338 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_seq_oss 26726 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_seq_midi 4557 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_rawmidi 19056 1 snd_seq_midi [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]arc4 1153 2 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]joydev 8708 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]pcmcia 33024 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]b43 157218 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_timer 19098 2 snd_pcm,snd_seq [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]mac80211 204922 1 b43 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]i915 282354 3 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd 54148 14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]yenta_socket 20408 1 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]drm_kms_helper 29297 1 i915 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]rsrc_nonstatic 10015 1 yenta_socket [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]cfg80211 126485 2 b43,mac80211 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]drm 162471 4 i915,drm_kms_helper [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]acer_wmi 13861 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]pcmcia_core 32964 3 pcmcia,yenta_socket,rsrc_nonstatic [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]soundcore 6620 1 snd [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]led_class 2864 2 b43,acer_wmi [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]intel_agp 24177 2 i915 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]agpgart 31724 2 drm,intel_agp [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]i2c_algo_bit 5028 1 i915 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]psmouse 63245 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]serio_raw 3978 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]snd_page_alloc 7076 2 snd_intel8x0,snd_pcm [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]video 17375 1 i915 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]output 1871 1 video [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]lp 7028 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]parport 32635 2 ppdev,lp [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]8139too 18545 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]8139cp 16186 0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]ssb 37336 1 b43 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]mii 4381 2 8139too,8139cp [/SIZE][/FONT]
 
**[FONT=Calibri]Kernal Boot Messages:[/FONT]**
[FONT=Calibri][SIZE=3][ 11.532286] b43-phy0: Broadcom 4318 WLAN found (core revision 9) [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.541264] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.566648] type=1505 audit(1281299176.525:5): operation="profile_load" pid=612 name="/usr/share/gdm/guest-session/Xsession" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.585233] type=1505 audit(1281299176.545:6): operation="profile_replace" pid=615 name="/sbin/dhclient3" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.586045] type=1505 audit(1281299176.545:7): operation="profile_replace" pid=615 name="/usr/lib/NetworkManager/nm-dhcp-client.action" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.586489] type=1505 audit(1281299176.545:8): operation="profile_replace" pid=615 name="/usr/lib/connman/scripts/dhclient-script" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.596253] type=1505 audit(1281299176.557:9): operation="profile_load" pid=618 name="/usr/bin/evince" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.680941] type=1505 audit(1281299176.641:10): operation="profile_load" pid=618 name="/usr/bin/evince-previewer" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.686753] eth0: link down [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]686881] ADDRCONF(NETDEV_UP): eth0: link is not ready [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.716352] type=1505 audit(1281299176.677:11): operation="profile_load" pid=618 name="/usr/bin/evince-thumbnailer" [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.718414] phy0: Selected rate control algorithm 'minstrel' [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.719365] Registered led device: b43-phy0::tx [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.719388] Registered led device: b43-phy0::rx [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.719410] Registered led device: b43-phy0::radio [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.719519] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.810402] b43 ssb0:0: firmware: requesting b43/ucode5.fw [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 11.817674] [drm] initialized overlay support [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.259878] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.265400] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.265493] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.265580] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.288139] b43 ssb0:0: firmware: requesting b43/ucode5.fw [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.293416] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.303812] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.303904] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][ 12.303991] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. [/SIZE][/FONT]
 
**[FONT=Calibri]NETWORK CONFIGURATION[/FONT]**
[FONT=Calibri][SIZE=3]*-network:0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]description: Network controller [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]vendor: Broadcom Corporation [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]physical id: 5 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bus info: pci@0000:06:05.0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]version: 02 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]width: 32 bits [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]clock: 33MHz [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]capabilities: bus_master [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]configuration: driver=b43-pci-bridge latency=32 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]resources: irq:21 memory:b0100000-b0101fff [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*-network:1 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]description: Ethernet interface [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]product: RTL-8139/8139C/8139C+ [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]vendor: Realtek Semiconductor Co., Ltd. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]physical id: 7 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bus info: pci@0000:06:07.0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]logical name: eth0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]version: 10 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]serial: 00:0a:e4:f9:0c:2b [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]size: 10MB/s [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]capacity: 100MB/s [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]width: 32 bits [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]clock: 33MHz [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]resources: irq:20 ioport:3000(size=256) memory:b0102000-b01020ff [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]*-network DISABLED [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]description: Wireless interface [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]physical id: 1 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]logical name: wlan0 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]serial: 00:16:ce:23:79:b7 [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]capabilities: ethernet physical wireless [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg [/SIZE][/FONT]
 
**[FONT=Calibri]NETWORKS[/FONT]**
[FONT=Calibri][SIZE=3]~$ iwlist scan [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]lo Interface doesn't support scanning. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]eth0 Interface doesn't support scanning. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]wlan0 Failed to read scan data : Network is down [/SIZE][/FONT]
 
**[FONT=Calibri]UBUNTU VERSION[/FONT]**
[FONT=Calibri][SIZE=3]Description: Ubuntu 10.04 LTS [/SIZE][/FONT]
 
**[FONT=Calibri]KERNAL/ARCHITECTURE[/FONT]**
[FONT=Calibri][SIZE=3]2.6.32-21-generic i686 [/SIZE][/FONT]
 
**[FONT=Calibri]RESTARTING THE NETWORK[/FONT]**
[FONT=Calibri][SIZE=3]Reconfiguring network interfaces...[/SIZE][/FONT]
 
**[FONT=Calibri]NDISWRAPPER[/FONT]**
[FONT=Calibri][SIZE=3]~$ ndiswrapper -l [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]bcmwl5a : driver installed [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]device (14E4:4318) present (alternate driver: ssb) [/SIZE][/FONT]

```
sudo apt-get install b43-fwcutter
```

Else try this on a liveCD session, I don't know if ndiswrapper etc will conflict with this firmware.

---

### Post by Newbie Kowboy on 2010-08-08
Thanks.
 
I tried this command, sudo apt-get install b43-fwcutter
 
This is what I got:
 
Reading package lists......Done
Building dependency tree
Reading state information.....Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 
Any other ideas?  Not sure what the LiveCD session is, but I'll look into it too.

---

### Post by Newbie Kowboy on 2010-08-14
[SIZE=6][B]SOLVED!!  :KS:KS:KS
[/B][SIZE=2]
I went back through my log above and realized a number of things:

1) Ubuntu recognized my installed wireless network controller: Broadcom BCM4318.

2) I had properly installed an updated driver for the BCM4318 (BCMwl5a).

3) I had properly installed ndiswrapper and associated it correctly with the driver.

4) I had checked, as suggested above, for b-43-fwcutter and saw that it was already installed.

5) My NetworkManager was clicked correctly to enable networking & wireless.

Still no wireless.  

So I focused on the problems listed above in my log: Network is DISABLED and "network ii is down".  Knew this was odd, since I had a functioning wireless set up at home that my other laptop could access.  So I concluded it could be the network device itself that was disabled.

I did some searches on the Acer Travelmate 2420 itself, looking for forums where people were having trouble with the wireless *sans* Ubuntu.  I discovered that I might be able to enable the wireless network controller by simply resetting the web browser Easy-Launch button.  So I did and, *voila!*, my wireless controller was turned on in the Acer.  

My laptop recognized the various wireless networks available to me, I connected to my home network and, I'm happy to say, I'm replying to my original thread via my Acer with Ubuntu installed!

I have a new computer!!!!!

Hope this will help anyone else.
[/SIZE][/SIZE]

---

### Post by Harshpanchal007 on 2013-01-30
Hi,
Can you please explain me how did you do this?

---

### Post by lisati on 2013-01-30
> **Harshpanchal007 said:**
> Hi,
Can you please explain me how did you do this?

10.04 is an "old" version of Ubuntu, things have changed in the time between the last activity on this thread and now.

Old thread closed.

---

