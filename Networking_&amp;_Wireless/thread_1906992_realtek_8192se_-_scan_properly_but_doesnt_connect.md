---
title: "realtek 8192se - scan properly but doesnt connect"
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by xurxoham on 2012-01-10
Hi everybody.
I've been searching around trying to solve this issue but I havent been able to get it working.

My problem is that my wireless card on my laptop detects wireless networks but can't connect to them. I think it's a OS problem cause I have a dual boot with Windows 7 x64 and hadnt any trouble like this since i bought it.
it
When i'm trying to connect to my network it asks me for the password with a  'Wireless network authentication required'. I've checked tons of times the password i was writting was the right one, but it keeps me asking like if i put it wrong.

I disabled any kind of wireless security on my router (first it had WPA2-PSK) and tried to connect again. I had to remove the network manager's entry of this network to stop it from asking me the password.
Once it tried to connect without asking from password (because at that point my wireless was open) it kept trying to connect for several minutes until I disconnected.

I suspected there was a problem with DHCP. A couple of months ago, I tried to connect to it by command-line. Everything went right until i had to get the IP address. At that point dhclient hanged requesting the address.

So I then tried to connect to my network using a statc IP address. My network addres is 192.168.2.0 so i put an address which didnt collided with any of the hosts connected to it. Again, it kept connecting while my wireless was open or asking for the password when it wasnt.

It seems very odd to me, cause I could connect to some neighbours' wireless network and I havent any trouble with connecting to my university's.

Here follows some information of my system:

```
1 ) Machine Brand and Model (PC/Laptop):
Toshiba Satellite A500-18Q

2 ) Wireless Brand, Model and Wireless Chipset:
14:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

3 ) check interface:
ifconfig
wlan0     Link encap:Ethernet  direcciónHW xx:xx:xx:xx:xx:xx
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig
wlan0     IEEE 802.11bgn  ESSID:"BCast"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

4 ) Check for modules:
rtl8192se              93999  0 
rtlwifi               118703  1 rtl8192se
mac80211              462092  2 rtl8192se,rtlwifi

5 ) Kernel boot messages
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88013fc00000 s79616 r8192 d22784 u1048576
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u1048576 alloc=1*2097152
[   22.252372] rtl8192se 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   22.252381] rtl8192se 0000:14:00.0: setting latency timer to 64


6 ) Network configuration
 *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wlan0
       version: 10
       serial: 70:1a:04:64:1c:c0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.0.0-14-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:5000(size=256) memory:f6000000-f6003fff

7 ) Scan for networks:
Cell 11 - Address: xx:xx:xx:xx:xx:xx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"BCast"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000244a2304b
                    Extra: Last beacon: 9220ms ago
                    IE: Unknown: 00054243617374
                    IE: Unknown: 01088C9298A4B048606C
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0700E04C01020300

8 ) Ubuntu Version: 
Ubuntu 11.10

9 ) Kernel/architecture (including 32 vs. 64 bit): 
3.0.0-14-generic x86_64

10 ) Restarting the network:
 * Reconfiguring network interfaces...                                               [ OK ] 

```

I'm sorry if I have opened a new thread about an existing topic, but i didnt found any which were posted the last months.
Greetings

---

