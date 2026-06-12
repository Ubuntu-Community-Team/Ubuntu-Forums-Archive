---
title: "WiFi disconnects after AC Power is unpluged from Laptop"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by TimBo170887 on 2011-05-11
About 20 seconds after I unplug my Laptop from the AC adapter my WiFi connection disconnects. The only way to get a connection again is to shut down my laptop and remove the battery and the AC adapter (WiFi-adapter reset) and reboot my laptop. I'm running 10.10 32-bit.
lspci shows me these information about my WiFi-Adapter

02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
        Subsystem: Device 1a3b:1026
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [60] Express Legacy Endpoint, MSI 00
        Capabilities: [90] MSI-X: Enable- Count=1 Masked-
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Kernel driver in use: ath5k
        Kernel modules: ath5k

Thanks!

---

### Post by Paddy Landau on 2011-05-11
This is a bit of a guess, but I've seen it work before.

Close down your computer. Disconnect everything (USB sticks, power cord, external monitor -- everything).

Remove your battery.

Press and hold your power button for 30 seconds. Release.

Connect everything again and see what happens. Sorry if it doesn't help.

---

### Post by TimBo170887 on 2011-05-12
thx for the reply but it didn't help at all... still the same problem

---

### Post by chili555 on 2011-05-12
I believe this has to do with the wireless drivers power management mode. Laptops strive to save power in order to extend battery life. One way is to shut down the wireless radio after an idle period. In some cases, it's well implemented; in others, not so much.

Please run:```
iwconfig wlan0
```Does it say *Power Management:on*? If so, you might try:```
sudo iwconfig wlan0 power off
```Does it help? If so, we can amend rc.local to make it permanent.

---

### Post by hybridxdawn on 2011-06-12
> **chili555 said:**
> I believe this has to do with the wireless drivers power management mode. Laptops strive to save power in order to extend battery life. One way is to shut down the wireless radio after an idle period. In some cases, it's well implemented; in others, not so much.

Please run:```
iwconfig wlan0
```Does it say *Power Management:on*? If so, you might try:```
sudo iwconfig wlan0 power off
```Does it help? If so, we can amend rc.local to make it permanent.
thanks chili555, i had the same problem and using "sudo iwconfig eth1 power off" worked perfectly for me. How do I make this permanent?

---

### Post by Toz on 2011-06-12
You can add it to /etc/rc.local. Place the command before the **exit 0** line in that file so that it looks like:```
iwconfig wlan0 power off
exit 0
```

---

### Post by hybridxdawn on 2011-06-12
> **Toz said:**
> You can add it to /etc/rc.local. Place the command before the **exit 0** line in that file so that it looks like:```
iwconfig wlan0 power off
exit 0
```
thank you!

---

### Post by TimBo170887 on 2011-06-27
when i try that it gives me 

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

---

### Post by chili555 on 2011-06-27
> **TimBo170887 said:**
> when i try that it gives me 

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.Did you run the command with sudo? Does your driver support power management? Not all do. Here is the hint.```
$ sudo iwconfig wlan0
[sudo] password for chili: 
wlan0     IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:24:66:2A:77:99   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          [COLOR="Red"]Power Management:[/COLOR]off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:44   Missed beacon:0
```

---

### Post by TimBo170887 on 2011-06-28
i did run it with sudo.
iwconfig wlan0 gives me almost the same result like you got:

```
wlan0     IEEE 802.11bg  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:24:97:F1:78:30   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```i don't know if my driver supports power management.
is there a way to check this?

---

### Post by chili555 on 2011-06-28
> **TimBo170887 said:**
> i did run it with sudo.
iwconfig wlan0 gives me almost the same result like you got:

```
wlan0     IEEE 802.11bg  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:24:97:F1:78:30   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```i don't know if my driver supports power management.
is there a way to check this?Sure:```
sudo iwlist wlan0 event
```Here is an example from one of my laptops; notice power management is not listed. I will try another computer later today and post the result.> $ sudo iwlist wlan0 event
wlan0     Wireless Events supported :
          0x8B04 : Set Frequency/Channel (kernel generated)
          0x8B06 : Set Mode (kernel generated)
          0x8B15 : New Access Point/Cell address - roaming
          0x8B19 : Scan request completed
          0x8B1A : Set ESSID (kernel generated)
          0x8B2A : Set Encoding (kernel generated)

wlan0     Scanning capabilities :
		- ESSID


---

### Post by TimBo170887 on 2011-07-03
iwlist wlan0 event gives this:

```
wlan0     Wireless Events supported :
          0x8B04 : Set Frequency/Channel (kernel generated)
          0x8B06 : Set Mode (kernel generated)
          0x8B15 : New Access Point/Cell address - roaming
          0x8B19 : Scan request completed
          0x8B1A : Set ESSID (kernel generated)
          0x8B2A : Set Encoding (kernel generated)

wlan0     Scanning capabilities :
        - ESSID

```power management is also not listed here.

---

### Post by tajunta on 2011-08-21
My driver didn't support the power management option, or at least it was not listed on the events. 

My problem got fixed with this: [http://uselessuseofcat.com/?p=67]("http://uselessuseofcat.com/?p=67") (I did also the updated section, because the blank file alone did not work). 

Now wireless is working even if I unplug the AC cord. Before it got disconnected always on the same second I unplugged, and I couldn't revoke it at all except by connecting the AC cord back.

---

### Post by mfaroukg on 2012-08-10
this is the post i did which solved my problem:

[https://plus.google.com/u/0/101265081646386136300/posts/cF7rwrvvrUx](https://plus.google.com/u/0/101265081646386136300/posts/cF7rwrvvrUx)

---

### Post by Toz on 2012-08-10
Old thread. Thread closed.

---

