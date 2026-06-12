---
title: "Wireless problems"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by kotto28 on 2013-04-29
Hello all, This is my first post so be gentle. I have a HP Mini 1104 which has a Ralink rt3592 wifi module. I originally tried 12.04 on the netbook and found that the wifi did not work. After downloading and installing the wifi drivers from the manufacturers website I found that the laptop would connect but would be very slow and would drop connection now and then. When testing the wifi with iperf to a wired server on the same network the results would only be a throughput of around 200kbps. I recently tried the 13.04 release and found the default driver (rt2800pci) to work much better but it is still slow for what it should be. Iperf on 13.04 got me to about 3mbps. I have tested other laptops and usually get over 20mbps.

Are there any settings I need to change to make the wifi work better? I also haven't had any luck on the manufacturer's driver in 13.04 (it was realeased in 2010). Any help would be appreciated if anyone has any experience with the rt2800pci driver. Thanks!

---

### Post by kotto28 on 2013-04-30
**[FONT=Arial]Here is a little more info. I'm no pro but the "Link Quality=39/70", "[/FONT]****[FONT=Arial]Tx excessive retries:299", and "[/FONT]****[FONT=Arial]Invalid misc:340" throw up a red flag to me. I am currently at a school campus where I am within range of multiple access points. I'm not sure that is throwing it off or the driver isn't able to handle it as well as the windows driver does. Thanks![/FONT]**[B][FONT=Arial]

lspci -nnk | grep -iA2 net
[/FONT]
```
[FONT=Arial]01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)[/FONT]
[FONT=Arial]    Subsystem: Hewlett-Packard Company Device [103c:338d][/FONT]
[FONT=Arial]    Kernel driver in use: r8169[/FONT]
[FONT=Arial]02:00.0 Network controller [0280]: Ralink corp. RT3592 Wireless 802.11abgn 2T/2R PCIe [1814:3592][/FONT]
[FONT=Arial]    Subsystem: Hewlett-Packard Company Device [103c:1638][/FONT]
[FONT=Arial]    Kernel driver in use: rt2800pci[/FONT]

```

[FONT=Arial]iwconfig
[/FONT]
```
[FONT=Arial]wlan0     IEEE 802.11abgn  ESSID:"IVLS"  [/FONT]
[FONT=Arial]          Mode:Managed  Frequency:2.437 GHz  Access Point: E8:39:35:FF:1E:90   [/FONT]
[FONT=Arial]          Bit Rate=39 Mb/s   Tx-Power=20 dBm   [/FONT]
[FONT=Arial]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT]
[FONT=Arial]          Power Management:on[/FONT]
[FONT=Arial]          Link Quality=39/70  Signal level=-71 dBm  [/FONT]
[FONT=Arial]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/FONT]
[FONT=Arial]          Tx excessive retries:299  Invalid misc:340   Missed beacon:0
[/FONT]
```[/B]

---

### Post by kotto28 on 2013-04-30
Doing some more poking around and found that if I install the manufacturer provided driver on an older ubuntu system (10.04) it seems to work a lot better. I'm guessing since the wifi driver is from 2010 it functions better on an older kernel. Any thoughts on how to get that to work on 13.04? Again, any help would be appreciated!

Edit: Just when I start to think I'm on to something the wifi cuts out and won't connect again. I'm really thinking the Ralink rt3592 just isn't cut out for ubunutu.

---

