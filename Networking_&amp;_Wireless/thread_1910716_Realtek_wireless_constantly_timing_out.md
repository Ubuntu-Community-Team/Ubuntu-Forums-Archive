---
title: "Realtek wireless constantly timing out"
date: 2012-01-17
forum: Networking &amp; Wireless
---

### Post by IndyGunFreak on 2012-01-17
This is driving me crazy.  I've used Linux for a while, and never had a problem like this.  Granted, I've always been very particular about stuff I buy, and usually use Atheros wireless devices.. but this was a good deal, and I thought RealTek had pretty good Linux support... Most of the slow wireless threads seem to revolve around Atheros devices, so I figured I would start a new thread.

Toshiba C655-S5504.  Connection speed is normal under Windows, so it's not hardware.  I've already tried this:  [http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html](http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html)   which rendered my device inoperable, so I had to undo everything.

uname -a
```
3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

lspci -nn
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MYESSID"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:33:B6:55:28   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-12 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:21891   Missed beacon:0

```
(My laptop is sitting 10ft from my router right now, so I'm not sure why it says Link quality is 70/70)

rfkill list all
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsmod
```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
joydev                 17693  0 
parport_pc             36962  0 
ppdev                  17113  0 
arc4                   12529  2 
snd_hda_codec_conexant    62197  1 
snd_hda_intel          33390  1 
snd_hda_codec         104802  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
uvcvideo               72711  0 
snd_rawmidi            30547  1 snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
rtl8192ce             137433  0 
rtlwifi               118703  1 rtl8192ce
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              310872  2 rtl8192ce,rtlwifi
cfg80211              199587  2 rtlwifi,mac80211
snd_timer              29991  2 snd_pcm,snd_seq
sparse_keymap          13890  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  566711  2 
drm_kms_helper         42558  1 i915
snd                    68266  11 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   236330  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
mei                    41480  0 
video                  19412  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
atl1c                  41643  0 
ahci                   26002  3 
libahci                26861  1 ahci

```

Any help would be greatly appreciated.  Any other logs, etc.,, you need, just ask.

---

### Post by chili555 on 2012-01-19
Your iwconfig looks solid. Let's dig a bit deeper. Please post:```
dmesg | grep 819
sudo cat /var/log/syslog | grep wlan | tail -n25
```Thanks.

---

### Post by IndyGunFreak on 2012-01-20
dmesg | grep 819

```
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88014fa00000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[   14.700748] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.700758] rtl8192ce 0000:02:00.0: setting latency timer to 64
[   33.324823] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[   41.919123] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[   48.708264] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin

```

Now this one seeems kinda telling...
```
Jan 20 12:10:19 ken-Satellite-C655 NetworkManager[876]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan 20 12:10:21 ken-Satellite-C655 NetworkManager[876]: <info> Activation (wlan0) starting connection 'HomeNetwork581'
Jan 20 12:10:21 ken-Satellite-C655 NetworkManager[876]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 20 12:10:21 ken-Satellite-C655 NetworkManager[876]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 20 12:10:21 ken-Satellite-C655 NetworkManager[876]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 20 12:10:21 ken-Satellite-C655 NetworkManager[876]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 20 12:10:21 ken-Satellite-C655 NetworkManager[876]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 20 12:10:21 ken-Satellite-C655 NetworkManager[876]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 20 12:10:21 ken-Satellite-C655 NetworkManager[876]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 20 12:10:21 ken-Satellite-C655 NetworkManager[876]: <info> (wlan0): preparing device.
Jan 20 12:10:21 ken-Satellite-C655 NetworkManager[876]: <info> Activation (wlan0/wireless): connection 'HomeNetwork581' has security, and secrets exist.  No new secrets needed.
Jan 20 12:10:21 ken-Satellite-C655 NetworkManager[876]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 20 12:10:21 ken-Satellite-C655 NetworkManager[876]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jan 20 12:10:22 ken-Satellite-C655 NetworkManager[876]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 20 12:10:22 ken-Satellite-C655 kernel: [   36.318268] wlan0: direct probe to 00:1f:33:b6:55:28 (try 1/3)
Jan 20 12:10:22 ken-Satellite-C655 kernel: [   36.515598] wlan0: direct probe to 00:1f:33:b6:55:28 (try 2/3)
Jan 20 12:10:22 ken-Satellite-C655 kernel: [   36.715267] wlan0: direct probe to 00:1f:33:b6:55:28 (try 3/3)
Jan 20 12:10:22 ken-Satellite-C655 kernel: [   36.914933] wlan0: direct probe to 00:1f:33:b6:55:28 timed out
Jan 20 12:10:28 ken-Satellite-C655 kernel: [   43.107602] wlan0: authenticate with 00:1f:33:b6:55:28 (try 1)
Jan 20 12:10:29 ken-Satellite-C655 kernel: [   43.304718] wlan0: authenticate with 00:1f:33:b6:55:28 (try 2)
Jan 20 12:10:29 ken-Satellite-C655 kernel: [   43.504358] wlan0: authenticate with 00:1f:33:b6:55:28 (try 3)
Jan 20 12:10:29 ken-Satellite-C655 kernel: [   43.704039] wlan0: authentication with 00:1f:33:b6:55:28 timed out
Jan 20 12:10:34 ken-Satellite-C655 NetworkManager[876]: <info> (wlan0): device state change: config -> unavailable (reason 'none') [50 20 0]
Jan 20 12:10:34 ken-Satellite-C655 NetworkManager[876]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan 20 12:10:34 ken-Satellite-C655 NetworkManager[876]: <info> (wlan0): taking down device.

```

---

### Post by IndyGunFreak on 2012-01-20
OK, just to make sure the log is current (I think that one was)....

I just did some updates, rebooted, and the Wireless connected fairly quick, but just as usual, it worked for about 20-25sec, then it just times out.
l
Here's the info you wanted, as it's a little different than before.
dmesg | grep 819

```
ken@ken-Satellite-C655:~$ dmesg | grep 819
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88014fa00000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[   15.015006] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.015015] rtl8192ce 0000:02:00.0: setting latency timer to 64
[   28.024457] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[   36.622726] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
[  151.852505] Modules linked in: bnep rfcomm bluetooth parport_pc ppdev snd_hda_codec_conexant snd_hda_intel snd_hda_codec snd_hwdep uvcvideo snd_pcm joydev videodev snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq arc4 v4l2_compat_ioctl32 rtl8192ce i915 rtl8192c_common rtlwifi drm_kms_helper drm snd_timer snd_seq_device psmouse mac80211 cfg80211 snd lp i2c_algo_bit sparse_keymap video serio_raw parport mei(C) soundcore snd_page_alloc usbhid hid ahci libahci atl1c
ken@ken-Satellite-C655:~$ 

```


sudo cat /var/log/syslog | grep wlan | tail -n25

```
Jan 20 12:38:43 ken-Satellite-C655 NetworkManager[847]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Jan 20 12:38:43 ken-Satellite-C655 NetworkManager[847]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 20 12:38:43 ken-Satellite-C655 NetworkManager[847]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 20 12:38:43 ken-Satellite-C655 NetworkManager[847]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan 20 12:38:43 ken-Satellite-C655 avahi-daemon[846]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.4.
Jan 20 12:38:43 ken-Satellite-C655 avahi-daemon[846]: New relevant interface wlan0.IPv4 for mDNS.
Jan 20 12:38:43 ken-Satellite-C655 avahi-daemon[846]: Registering new address record for 192.168.1.4 on wlan0.IPv4.
Jan 20 12:38:44 ken-Satellite-C655 NetworkManager[847]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan 20 12:38:45 ken-Satellite-C655 NetworkManager[847]: <info> Activation (wlan0) successful, device activated.
Jan 20 12:38:45 ken-Satellite-C655 NetworkManager[847]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 20 12:38:45 ken-Satellite-C655 NetworkManager[847]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 20 12:38:45 ken-Satellite-C655 avahi-daemon[846]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::e2ca:94ff:fe9f:3f7.
Jan 20 12:38:45 ken-Satellite-C655 avahi-daemon[846]: New relevant interface wlan0.IPv6 for mDNS.
Jan 20 12:38:45 ken-Satellite-C655 avahi-daemon[846]: Registering new address record for fe80::e2ca:94ff:fe9f:3f7 on wlan0.*.
Jan 20 12:38:54 ken-Satellite-C655 NetworkManager[847]: <info> Policy set 'HomeNetwork581' (wlan0) as default for IPv4 routing and DNS.
Jan 20 12:38:54 ken-Satellite-C655 NetworkManager[847]: <info> Policy set 'HomeNetwork581' (wlan0) as default for IPv4 routing and DNS.
Jan 20 12:38:54 ken-Satellite-C655 kernel: [   53.791988] wlan0: no IPv6 routers present
Jan 20 12:38:56 ken-Satellite-C655 ntpd[1563]: Listen normally on 3 wlan0 192.168.1.4 UDP 123
Jan 20 12:38:56 ken-Satellite-C655 ntpd[1563]: Listen normally on 5 wlan0 fe80::e2ca:94ff:fe9f:3f7 UDP 123
Jan 20 12:39:03 ken-Satellite-C655 NetworkManager[847]: <info> (wlan0): IP6 addrconf timed out or failed.
Jan 20 12:39:03 ken-Satellite-C655 NetworkManager[847]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Jan 20 12:39:03 ken-Satellite-C655 NetworkManager[847]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Jan 20 12:39:03 ken-Satellite-C655 NetworkManager[847]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan 20 12:39:03 ken-Satellite-C655 NetworkManager[847]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 20 12:39:03 ken-Satellite-C655 NetworkManager[847]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.

```

---

### Post by chili555 on 2012-01-20
Please try:```
sudo modprobe -rv rtl8192ce
sudo modprobe rtl8192ce ips=0
```Please tell us if there is improvement.

-----------------
Notes to Chili:

[https://bugzilla.redhat.com/show_bug.cgi?id=729618](https://bugzilla.redhat.com/show_bug.cgi?id=729618)

[http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II#Realtek_Linux_driver](http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II#Realtek_Linux_driver)

> One method that appears to drastically reduce the crashes and connection drops is to comment out "-DENABLE_LPS" from the Makefiles while building the Realtek Linux driver. This also reduces the "noise" in the syslog kernel messages generated by LPS. However, it may reduce the battery life since LPS is an acronym for Low Power State. 

---

### Post by IndyGunFreak on 2012-01-20
Doesn't appear to be.. same problem.  It takes forever trying to connect, *if* it connects, it times out after 20-30sec.  I've tried No Encryption, WEP, WPA, WPA2... all do the same thing.

Edit:  Hold on a second, I might have jumped the gun that it's not working.. gimme a sec.

---

### Post by IndyGunFreak on 2012-01-20
Ok, definitely didn't change anything.

---

### Post by IndyGunFreak on 2012-01-20
The very end looks a little different.

```
ken@ken-Satellite-C655:~$ sudo cat /var/log/syslog | grep wlan | tail -n25
[sudo] password for ken: 
Jan 20 17:10:22 ken-Satellite-C655 dhclient: DHCPREQUEST of 192.168.1.4 on wlan0 to 255.255.255.255 port 67
Jan 20 17:10:22 ken-Satellite-C655 NetworkManager[846]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Jan 20 17:10:22 ken-Satellite-C655 NetworkManager[846]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 20 17:10:22 ken-Satellite-C655 NetworkManager[846]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 20 17:10:22 ken-Satellite-C655 NetworkManager[846]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan 20 17:10:23 ken-Satellite-C655 NetworkManager[846]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan 20 17:10:23 ken-Satellite-C655 NetworkManager[846]: <info> Activation (wlan0) successful, device activated.
Jan 20 17:10:23 ken-Satellite-C655 NetworkManager[846]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 20 17:10:23 ken-Satellite-C655 NetworkManager[846]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 20 17:10:29 ken-Satellite-C655 kernel: [  120.798840] wlan0: no IPv6 routers present
Jan 20 17:10:30 ken-Satellite-C655 NetworkManager[846]: <info> Policy set 'HomeNetwork58' (wlan0) as default for IPv4 routing and DNS.
Jan 20 17:10:30 ken-Satellite-C655 NetworkManager[846]: <info> Policy set 'HomeNetwork58' (wlan0) as default for IPv4 routing and DNS.
Jan 20 17:10:35 ken-Satellite-C655 ntpd[1827]: Listen normally on 3 wlan0 192.168.1.4 UDP 123
Jan 20 17:10:35 ken-Satellite-C655 ntpd[1827]: Listen normally on 5 wlan0 fe80::e2ca:94ff:fe9f:3f7 UDP 123
Jan 20 17:10:39 ken-Satellite-C655 NetworkManager[846]: <info> (wlan0): IP6 addrconf timed out or failed.
Jan 20 17:10:39 ken-Satellite-C655 NetworkManager[846]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Jan 20 17:10:39 ken-Satellite-C655 NetworkManager[846]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Jan 20 17:10:39 ken-Satellite-C655 NetworkManager[846]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan 20 17:10:39 ken-Satellite-C655 NetworkManager[846]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 20 17:10:39 ken-Satellite-C655 NetworkManager[846]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Jan 20 17:11:31 ken-Satellite-C655 NetworkManager[846]: <info> Policy set 'HomeNetwork58' (wlan0) as default for IPv4 routing and DNS.
Jan 20 17:11:42 ken-Satellite-C655 ntpd[2047]: Listen normally on 4 wlan0 192.168.1.4 UDP 123
Jan 20 17:11:42 ken-Satellite-C655 ntpd[2047]: Listen normally on 6 wlan0 fe80::e2ca:94ff:fe9f:3f7 UDP 123
Jan 20 17:12:47 ken-Satellite-C655 NetworkManager[846]: <info> Policy set 'HomeNetwork58' (wlan0) as default for IPv4 routing and DNS.
Jan 20 17:12:47 ken-Satellite-C655 NetworkManager[846]: <info> Policy set 'HomeNetwork58' (wlan0) as default for IPv4 routing and DNS.
ken@ken-Satellite-C655:~$ 

```

---

### Post by IndyGunFreak on 2012-02-24
Just thought I'd update those that might still be having issues with this device.  I'm using a Live USB of 12.04, and it appears my wireless is working fantastic.

Been using it for about 30min, no timeouts at all, including downloading the current Kubuntu 12.04 alpha ISO.  Using WPA2.

If you're a new Ubuntu user, probably best to stay away from Alpha's and Beta's, but just know that it appears a solution is on the horizon.

IGF

---

