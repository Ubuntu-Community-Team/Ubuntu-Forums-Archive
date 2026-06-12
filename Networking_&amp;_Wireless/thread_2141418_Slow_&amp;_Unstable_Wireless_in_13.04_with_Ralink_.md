---
title: "Slow &amp; Unstable Wireless in 13.04 with Ralink RT3592 &amp; RT2800PCI Driver"
date: 2013-05-02
forum: Networking &amp; Wireless
---

### Post by kotto28 on 2013-05-02
Hello all, I have a HP Mini 1104 which has a Ralink rt3592 wifi module. I originally tried 12.04 on the netbook and found that the wifi did not work. After downloading and installing the wifi drivers from the manufacturers website I found that the laptop would connect but would be very slow and would drop connection frequently. When testing the wifi with iperf to a wired server on the same network the results would only be a throughput of around 200kbps. I recently tried the 13.04 release and found the default driver (rt2800pci) to work much better but it is still slow for what it should be. Iperf on 13.04 got me to about 3mbps and the signal strength seems lower than what it should be. I have tested other laptops and usually get over 20mbps. Are there any settings I need to change to make the wifi work better? I also haven't had any luck on the manufacturer's driver in 13.04 (it was realeased in 2010).

lspci -nnk | grep -iA2 net
```

     01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
     Subsystem: Hewlett-Packard Company Device [103c:338d]
     Kernel driver in use: r8169
     02:00.0 Network controller [0280]: Ralink corp. RT3592 Wireless 802.11abgn 2T/2R PCIe [1814:3592]
     Subsystem: Hewlett-Packard Company Device [103c:1638]
     Kernel driver in use: rt2800pci

```

iwconfig
```

    wlan0     IEEE 802.11abgn  ESSID:"IVLS"  
              Mode:Managed  Frequency:2.437 GHz  Access Point: E8:39:35:FF:1E:90   
              Bit Rate=39 Mb/s   Tx-Power=20 dBm   
              Retry  long limit:7   RTS thr:off   Fragment thr:off
              Power Management:on
              Link Quality=39/70  Signal level=-71 dBm  
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:299  Invalid misc:340   Missed beacon:0

```

I'm no pro but the "Link Quality=39/70", "Tx excessive retries:299", and "Invalid misc:340" throw up a red flag to me. I am currently at a school campus where I am within range of multiple access points. I'm not sure if that is throwing it off or the driver isn't able to handle it as well as the windows driver does. Any help would be appreciated if anyone has any experience with the rt2800pci driver. Thanks!

---

