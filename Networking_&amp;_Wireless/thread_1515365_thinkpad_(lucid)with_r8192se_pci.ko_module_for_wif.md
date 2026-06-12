---
title: "thinkpad (lucid)with r8192se_pci.ko module for wifi always grayed in Network Manager"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by tjose on 2010-06-22
Hi all

I have a thinkpad (T410i) and the Wireless driver from RealTek called rt8192se_pci.ko.

"iwconfig" returns the following results.
>>>>>>>>>>>>>>>>>>>>>
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

tun0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.467 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

However the network manager menu is remain in 'disconnected' state for "Wireless Networks". dmesg shows  the following..

[27090.437732] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[27090.551636] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[27090.551651] ===>rtllib_start_scan()
[27090.551700] =====>rtl8192_set_chan()====ch:2
[27090.552191] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27090.661160] =====>rtl8192_set_chan()====ch:3
[27090.759858] =====>rtl8192_set_chan()====ch:4
[27090.869816] =====>rtl8192_set_chan()====ch:5
[27090.969781] =====>rtl8192_set_chan()====ch:6
[27091.069730] =====>rtl8192_set_chan()====ch:7
[27091.169685] =====>rtl8192_set_chan()====ch:8
[27091.269641] =====>rtl8192_set_chan()====ch:9
[27091.369543] =====>rtl8192_set_chan()====ch:10
[27091.470799] =====>rtl8192_set_chan()====ch:11
[27091.579508] =====>rtl8192_set_chan()====ch:12
[27091.629875] GPIOChangeRF  - HW Radio OFF
[27892.208256] ================>r8192_wx_set_scan(): hwradio off
[27912.386872] ================>r8192_wx_set_scan(): hwradio off
[27942.374866] ================>r8192_wx_set_scan(): hwradio off
[27982.357633] ================>r8192_wx_set_scan(): hwradio off
[28032.336143] ================>r8192_wx_set_scan(): hwradio off
[28092.310277] ================>r8192_wx_set_scan(): hwradio off
[28152.284556] ================>r8192_wx_set_scan(): hwradio off
[28212.258831] ================>r8192_wx_set_scan(): hwradio off
[28272.232187] ================>r8192_wx_set_scan(): hwradio off
[28332.206075] ================>r8192_wx_set_scan(): hwradio off
[28392.179848] ================>r8192_wx_set_scan(): hwradio off
[28452.153941] ================>r8192_wx_set_scan(): hwradio off
[28512.128331] ================>r8192_wx_set_scan(): hwradio off
[28572.101624] ================>r8192_wx_set_scan(): hwradio off
[28632.075333] ================>r8192_wx_set_scan(): hwradio off



#lsmod | grep 8192 returns

r8192se_pci           504287  0

and "top" give the following related to r8192se_pci as

.........
 5976 root      20   0     0    0    0 S    1  0.0   0:41.72 rtl819xSE/1  
.........

Kindly help me to find a solution.

Thankyou for your time.
jos

---

