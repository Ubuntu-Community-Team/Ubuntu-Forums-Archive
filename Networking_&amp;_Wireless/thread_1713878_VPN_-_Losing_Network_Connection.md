---
title: "VPN - Losing Network Connection"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by BarataPT on 2011-03-24
Hi,

I have to use VPN to connect to the college network. When i connect to the VPN after some time it seems that it "shutdowns" my wireless connection. I have to disconnect to the VPN and connect again. This can happen after 5minutes or 1hour after connecting to VPN. The stranger thing is that there is no info saying "Connection Lost" or other.

I'm using Ubuntu 10.10 and my wireless card is a Realtek 8192-SE

I tried to disable IPv6 but the problem remains.

When the problem occurs here are the messages:
```
Mar 24 20:52:41 RuiLaptop pppd[2274]: Protocol-Reject for unsupported protocol 0x50e6
Mar 24 20:52:41 RuiLaptop pppd[2274]: Protocol-Reject for unsupported protocol 0xccb1
Mar 24 20:52:41 RuiLaptop pppd[2274]: Protocol-Reject for unsupported protocol 0xd0e1
Mar 24 20:52:41 RuiLaptop pppd[2274]: Protocol-Reject for unsupported protocol 0x64ed
Mar 24 20:52:41 RuiLaptop pppd[2274]: Protocol-Reject for unsupported protocol 0x36ec
Mar 24 20:52:41 RuiLaptop pppd[2274]: Protocol-Reject for unsupported protocol 0xd26d
Mar 24 20:52:41 RuiLaptop pppd[2274]: Protocol-Reject for unsupported protocol 0x95
Mar 24 20:52:41 RuiLaptop pppd[2274]: Protocol-Reject for unsupported protocol 'NTCITS IPI' (0xc1)
Mar 24 20:52:41 RuiLaptop pppd[2274]: Protocol-Reject for unsupported protocol 'Stampede Bridging' (0x6f)
Mar 24 20:52:42 RuiLaptop pppd[2274]: Protocol-Reject for unsupported protocol 0x6d
Mar 24 20:52:42 RuiLaptop pppd[2274]: Protocol-Reject for unsupported protocol 0x7ecc
```

And this continues until i disconnect from the VPN.

Also, i get a lot of this messages (connected or not to VPN):
```
Mar 24 20:24:41 RuiLaptop kernel: [ 1790.526183] ===>rtl8192se_link_change():ieee->iw_mode is 2
Mar 24 20:24:41 RuiLaptop kernel: [ 1790.526189] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
Mar 24 20:24:49 RuiLaptop kernel: [ 1797.997204] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Mar 24 20:25:23 RuiLaptop kernel: [ 1832.504934] rtl8192_hw_sleep_down(): RF Change in progress!
Mar 24 20:26:07 RuiLaptop kernel: [ 1876.643162] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Mar 24 20:26:40 RuiLaptop kernel: [ 1909.007104] ===>rtl8192se_link_change():ieee->iw_mode is 2
Mar 24 20:26:40 RuiLaptop kernel: [ 1909.060106] =====>rtl8192_set_chan()====ch:1
Mar 24 20:26:40 RuiLaptop kernel: [ 1909.172037] =====>rtl8192_set_chan()====ch:2
Mar 24 20:26:40 RuiLaptop kernel: [ 1909.284074] =====>rtl8192_set_chan()====ch:3
Mar 24 20:26:40 RuiLaptop kernel: [ 1909.396074] =====>rtl8192_set_chan()====ch:4
Mar 24 20:26:40 RuiLaptop kernel: [ 1909.508072] =====>rtl8192_set_chan()====ch:5
Mar 24 20:26:40 RuiLaptop kernel: [ 1909.620096] =====>rtl8192_set_chan()====ch:6
Mar 24 20:26:40 RuiLaptop kernel: [ 1909.732104] =====>rtl8192_set_chan()====ch:7
Mar 24 20:26:40 RuiLaptop kernel: [ 1909.844105] =====>rtl8192_set_chan()====ch:8
Mar 24 20:26:40 RuiLaptop kernel: [ 1909.956103] =====>rtl8192_set_chan()====ch:9
Mar 24 20:26:41 RuiLaptop kernel: [ 1910.068112] =====>rtl8192_set_chan()====ch:10
Mar 24 20:26:41 RuiLaptop kernel: [ 1910.180086] =====>rtl8192_set_chan()====ch:11
Mar 24 20:26:41 RuiLaptop kernel: [ 1910.293066] =====>rtl8192_set_chan()====ch:12
Mar 24 20:26:41 RuiLaptop kernel: [ 1910.404104] =====>rtl8192_set_chan()====ch:13
Mar 24 20:26:41 RuiLaptop kernel: [ 1910.517068] =====>rtl8192_set_chan()====ch:1
```

---

