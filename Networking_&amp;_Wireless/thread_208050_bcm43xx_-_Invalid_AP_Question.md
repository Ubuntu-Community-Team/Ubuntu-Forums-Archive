---
title: "bcm43xx - Invalid AP Question"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by munsell on 2006-07-02
Hello,

I have the following broadcom card:
```

0000:01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
        Subsystem: Hewlett-Packard Company: Unknown device 1360
        Flags: bus master, fast devsel, latency 0, IRQ 233
        Memory at c3000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

```
Now, I got it working using this [ post]("http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx") and this [ guide.]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")

When I boot my laptop and type iwconfig at the command prompt I get the following:
```

eth1   IEEE 802.11b/g  ESSID:"xxxxx"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
As you can see, the "Access Point" is "Invalid".  To fix this I must issue the following command at the command prompt and restart eth1:
```

$ sudo iwconfig eth1 ap any

```

Now, I have tried to automate this by putting the following in my /etc/network/interfaces file:

```

iface eth1 inet dhcp
wireless-essid xxxxx
        pre-up iwconfig eth1 ap any
auto eth1

```

I also tried this:

```

iface eth1 inet dhcp
wireless-essid xxxxx
wireless-ap any
auto eth1

```


Neither approach seems to work.  I still must manually set the access point every time I boot the device.  Does anyone have any suggestions on how to automate this process during the boot sequence?  Thanks for any help in advance :)

---

### Post by spd106 on 2006-07-03
The current best solution seems to be to install network-manager. It will take care of setting up the connection when you log on. Though you still have to enter the keyring password, but the next version will solve this.

Unfortunately this doesn't help much on a gui-less machine. If anyone has a better solution I'd much appreciate it.

---

