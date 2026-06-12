---
title: "No AP in NetworkManager with Broadcom BCM4306 (B43)"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by gheaci80 on 2010-04-24
Hi all, 

I have problems with my Broadcom BCM4306 (rev 03) on my HP nx6110 using Karmic. NetworkManager does not list any AP, even if there should be some. It did work for some days without problems, but suddenly stopped working. I made a kernel update with the update manager, but I am not sure if this caused the probem (I also used the wired connection, so I don't exaclty know when wireless stopped working). Reinstalling fwcutter wasn't successful. So I tried as suggested in [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4306](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4306) and added the following lines to /etc/rc.local

modprobe -r b43 b44 ssb
modprobe ieee80211_crypt_tkip
modprobe b44
/etc/init.d/networking restart

But still no success. Any ideas on this problem?

Some output:

> uname -a
before update: Linux heidi-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
after update : Linux heidi-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

> sudo iwlist scanning
wlan0     No scan results

> sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:d0000000-d0001fff

> lsmod | grep "b43"
b43                   122200  0 
mac80211              181140  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
ssb                    35524  2 b43,b44

> iwconfig
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> dmesg | grep "b43"
[    1.925948] b43-pci-bridge 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   27.520100] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   28.768057] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   28.811891] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   28.818687] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   28.826046] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   28.958999] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   29.105074] Registered led device: b43-phy0::tx
[   29.105101] Registered led device: b43-phy0::rx
[   29.105137] Registered led device: b43-phy0::radio


Thanks in advance,
Gerald

---

### Post by nastelroy on 2010-07-07
you have same problem with me, everything works perfect with manual ifup and ifdown command....but the network manager not shown anything


vostro@vostro-laptop:~$ uname -r
2.6.33-02063304-generic


vostro@vostro-laptop:~$ lspci -vv| grep Bro
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

vostro@vostro-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:25:9C:2F:A1:3B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-5 dBm  
                    Encryption key:off
                    ESSID:"DAUNBIRU"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004598f3400
                    Extra: Last beacon: 1032ms ago
                    IE: Unknown: 00084441554E42495255
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020CF4000000

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


whats wrong with my network manager?

---

