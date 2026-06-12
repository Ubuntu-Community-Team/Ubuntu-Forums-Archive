---
title: "No net connection at or near boot, network card's light not on- but it works in WinXP"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by skztr on 2009-09-23
"every now and then" (perhaps once or twice a week), when I boot up I have no net connection (no internet or LAN, and
the light on the ethernet plug is not on). doing "sudo /etc/init.d/networking restart" has no effect on the
problem, and rebooting rarely has an effect, though I have found that if I repeatedly unplug/replug the ethernet cable,
eventually the light comes back on ("immediately" as I re-plug, when it eventually happens), and once that happens I
have net connection immediately, without needing to say "sudo /etc/init.d/networking restart"- once the light comes
back on, I don't have any problems for the rest of the day. "tail -f /var/log/dmesg" shows no new output while all this
is happening.

I am sometimes (but very very rarely) disconnected after having had a connection when I first boot up (same symptoms-
light in the back goes off, re-plugging eventually makes the light come back on, etc), though usually within 30 minutes
of having booted, and if I don't have the problem "on boot" or "near boot" I don't have any problems for the rest of
the day.

If I boot into Windows, it always works just fine, though booting back into Ubuntu the problem remains.
I have tried multiple network cables, swapped cables with people sitting next to me, tried "jiggling" the cable, etc.
If nothing else, the fact that it always (without any failure, ever) works in Windows tells me that this is not a cable
problem.

Things I have tried:
 - Rebooting (rarely works)
 - Rebooting into Windows (always works, but if I reboot back into Ubuntu the problem remains)
 - sudo /etc/init.d/networking/restart
 - sudo rmmod e100 && sudo modprobe e100
 - Unplugging/replugging the cable ("eventually" works, after about twenty attempts and twenty minutes)
 - Swapping cables with someone else (their net connection continues to work, my net connection continues not to)

```
$ uname -a
Linux office-d4897a 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
```

```
$ lsb_release  -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty
```

```
$ sudo lshw | sed -n '/\*-network/,${/\*-/{/\*-network/!q;};p;};'
           *-network      
                description: Ethernet interface
                product: 82801G (ICH7 Family) LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:03:08.0
                logical name: eth0
                version: 01
                serial: 00:13:72:ce:c9:7e
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A ip=192.168.2.128 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
```

---

