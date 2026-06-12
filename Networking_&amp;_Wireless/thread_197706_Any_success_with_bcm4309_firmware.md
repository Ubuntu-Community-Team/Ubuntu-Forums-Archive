---
title: "Any success with bcm4309 firmware?"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by eindgebruiker on 2006-06-16
Since Dapper I haven't been able to get my wireless connection working. It used to work fine on Breezy with ndiswrapper. On Dapper I tried both ndiswrapper and bcm43xx, without success.

I have a Dell Inspiron 510m, with a Dell TrueMobile 1400 Mini-PCI Card. This is based on a BCM4309:

```
lspci
0000:01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)

lspci -vn
0000:01:03.0 0280: 14e4:4324 (rev 02)
        Subsystem: 1028:0001
        Flags: fast devsel, IRQ 5
        Memory at fcffc000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
```

According to [http://bcm43xx.berlios.de/?go=Devices](http://bcm43xx.berlios.de/?go=Devices) this is supported.

The problem starts here:

```
iwconfig
eth2      IEEE 802.11a/b/  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwlist eth2 scan
eth2      Interface doesn't support scanning : No such device
```

I tried several firmware versions from Dell, e.g.
R63259.EXE, which DriverVer=06/13/2003, 3.20.23.0
and
R102318.EXE, which is DriverVer=05/26/2005, 3.120.27.0

Neither with bcm43xx nor with ndiswrapper do they work.

What I would like to know is:
- What's wrong here?
- Does anyone have success with a bcm4309? Which firmware version do you use?

Thanks,

Gaele

---

### Post by eindgebruiker on 2006-06-19
Well, I finally got it working.

Not with bcm43xx. That keeps telling me the Access Point is "Invalid."

Now I have a working configuration with ndiswrapper, network-manager, and the Broadcom driver from R63259.EXE (DriverVer=06/13/2003, 3.20.23.0).

What may have helped (though I am not sure) is that I stopped and then started Wireless in the BIOS (with a boot into Ubuntu in between).

---

### Post by jakesr on 2007-04-24
Hi,

I am using the same bcm4309 from Dell Inspiron 600 with the latest Ubuntu 7.04. I installed ndiswrapper and when I do the "ndiswrapper -l" command it show my the driver for the bcm43xx is installed. But still I am not able to get the wireless enabled even after several reboots. 

So, Can you please step out in detail ur process in getting a successful installation of bcm4309 driver using ndiswrapper?

Thanks,
Jakes.

---

### Post by mimiko on 2008-05-25
On Hardy Heron I got wireless working on a Dell Latitude D610 with Broadcom BCM4309 (rev 03).

This is all I did:

1) Followed all the steps here: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)  
You will see here that on step to you immediately are redirected to a different documentation page([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851))

2) On this documentation/driver page, I then followed step 2a on that page, so this specifically: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-dfa35a08da26002d337e79d528efb0c4ed5a127f](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-dfa35a08da26002d337e79d528efb0c4ed5a127f)

3) Once I'd finished with step 2a on that documentation page, I returned to the initial walk-through and continued with steps 3 onwards. I rebooted, and it worked.

Note: if this doesn't work for you, trying using the Windows Wifi Driver gui (called Windows Wireless Network Drivers); you can then add the bcmwl5 driver.

Good luck!

What I'd really like to know is an easy way to switch between using the built in driver (with the cutter) and using ndiswrapper, as the speeds suck with the native driver, but with ndiswrapper you're limited in some of the monitoring you can do. If anyone has already figured out or created a script to switch seamlessly between these two driver set ups, I'd love it if you shared! :)

---

