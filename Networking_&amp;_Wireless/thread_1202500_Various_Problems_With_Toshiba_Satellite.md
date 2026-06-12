---
title: "Various Problems With Toshiba Satellite"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by rossmc92 on 2009-07-02
Various Problems With Toshiba Satellite

So I finally managed to navigate my friend away from Vista. He'd borrowed my spare laptop while his was being repaired and loved it. So we went ahead and installed Jaunty on his Toshiba Satellite L300D based on it working well on the live CD. However, a short while after install we noticed the wireless disconnects shorty after connecting. The only way I can see that fixes this is if I disable the wireless and re-enable it several times and then restarting.

I really, really don't want him to go back to Windows but this hasn't exactly given the best impression on Ubuntu. Help would be great but if there appears to be no way for it to work, could you advise any other known distro that works with it well?

Thanks in advance.

---

### Post by The Toxic Mite on 2009-07-02
Hmm. Tell your friend to do the following:

[indent]
Go to Applications > Accessories > Terminal, and type in the following command:

```
lshw -c network
```

Also, can you post the output of this other command please?

```
iwconfig
```
[/indent]

Thanks! :)

---

### Post by rossmc92 on 2009-07-02
lshw -c network;

andrew@andrew-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:7d:83:63
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:21:63:97:a7:04
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.11.6 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:60:68:15:32:b9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

iwconfig;

andrew@andrew-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"001D7374A8F8"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:1D:73:74:A8:F8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=56/100  Signal level:-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by superprash2003 on 2009-07-02
take a look [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by The Toxic Mite on 2009-07-02
That's strange - the "product" and "vendor" strings aren't there.

Would you mind running lshw -c network again please? Thanks :-k

---

### Post by rossmc92 on 2009-07-02
> **The Toxic Mite said:**
> That's strange - the "product" and "vendor" strings aren't there.

Would you mind running lshw -c network again please? Thanks :-k

I would but the laptops not with me now, he took it back and is putting XP on it.

---

### Post by The Toxic Mite on 2009-07-02
> **rossmc92 said:**
> I would but the laptops not with me now, he took it back and is putting XP on it.

Damnit!

Well, I wish him luck, but he might regret putting XP on it later... ;)

---

