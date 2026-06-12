---
title: "Not connecting to network"
date: 2006-04-17
forum: Networking &amp; Wireless
---

### Post by delta32 on 2006-04-17
I've been trying to get my wireless card working on Kubuntu but it doesn't want to connect to the network at all. Whenever I put my ESSID in it never saves the setting and goes back to off/any. I've tried putting in my WEP key first then my ESSID, but that didn't work either. Does anyone know what is wrong and how I can fix it? Thanks.

```
delta32@jigoku:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:30:BD:F7:BE:F0
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fef7:bef0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:fe1fe000-fe1fffff
```
```
delta32@jigoku:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33   Missed beacon:0
```
```
delta32@jigoku:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:D1:64:F7
                    ESSID:"nullpo"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-64 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
```
```
delta32@jigoku:~$ dmesg |grep ndis
[4294703.779000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294703.851000] ndiswrapper: driver bcmwl5 (Broadcom,06/25/2004, 3.40.73.0) loaded
[4294703.858000] ndiswrapper: using irq 16
[4294704.499000] wlan0: ndiswrapper ethernet device 00:30:bd:f7:be:f0 using driver bcmwl5, configuration file 14E4:4320.5.conf

```

---

### Post by bscbrit on 2006-04-17
Perhaps the easiest way to fix it would be to edit the /etc/networks/interfaces file in an editor?  But that doesn't actually fix the problem that you are having, it just gets you a working system.  I don't use Kubuntu and I don't know enough about the configuration tools to offer any useful advice regarding them.

---

### Post by jml on 2006-04-17
I agree with bscbrit.  I've read on these forums that the gui frontend to the networking administration tool will not always reliably work.  Other have suggested that manually editing the file he mentions often leads to more reliable results.

Joe

---

### Post by delta32 on 2006-04-17
I just tried editing the interfaces file like suggested and it still doesn't work. :( 

```
iface wlan0 inet static
address 192.168.1.47
netmask 255.255.255.0
network 192.168.1.1
broadcast 192.168.1.255
gateway 192.168.1.1
wireless-key1 s:xxx
wireless-defaultkey 1
wireless-essid nullpo
wireless-mode Managed
wireless-channel 6
```

Any other ideas?

---

### Post by bscbrit on 2006-04-17
Here is a copy of my setup (encryption changed - obviously)

iface wlan0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid bscbritnet
wireless-nick spare
wireless-channel 6
wireless-mode managed
wireless-ap 00:13:46:9E:FF:FF
wireless-key1 aa11bb22cc33dd44ee55ff6600
wireless-defaultkey 1
wireless-keymode open

The last 3 lines are missing from your file but I find that on my computer if I miss them out it does not work.  You may wish to try your equivalent values.

---

### Post by delta32 on 2006-04-17
Thank you so much! :D I'm typing from Kubuntu now. Looks like the things I was missing were important.

---

### Post by bscbrit on 2006-04-18
Did it work? Or did you decide that you had had enough for one day and went to bed?!

---

### Post by delta32 on 2006-04-18
Yes, it's working now and it works great now. :D

---

