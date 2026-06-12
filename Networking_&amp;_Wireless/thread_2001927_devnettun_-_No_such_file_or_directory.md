---
title: "/dev/net/tun - No such file or directory"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by Chireru on 2012-06-11
I'm playing around with tinc, but I can't seem to get it to work with the tun device.  I get the same thing on 12.04 LTS and 10.04 LTS:

```
**root@mio:~# ls -lah /dev/net/tun**
crw-rw-rwT 1 root root 10, 200 Jun 11 07:45 /dev/net/tun
**root@mio:~# file /dev/net/tun **
/dev/net/tun: sticky character special
**root@mio:~# mount | grep udev**
udev on /dev type devtmpfs (rw,mode=0755)
**root@mio:~# tincd -d5 -n net**
Jun 11 20:51:33 mio tinc.net[19190]: tincd 1.0.16 (Jul 27 2011 12:56:56) starting, debug level 5
Jun 11 20:51:33 mio tinc.net[19190]: Could not open '/dev/net/tun': No such file or directory
Jun 11 20:51:33 mio tinc.net[19190]: Terminating
```

'modprobe tun' returns nothing; 'lsmod|grep tun' also returns nothing, so I assume it's compiled into the kernel.

Any idea why tinc complains that it can't find a device file that clearly exists?

---

### Post by Chireru on 2012-06-12
Not sure why, but if I just comment out all of the device information, it picks up the device just fine...  :confused:
```
#Device = '/dev/net/tun'
#DeviceType = tun
```

---

### Post by gertvdijk on 2012-07-08
Yeah I got the same on Debian Squeeze. To much more surprise of me see this:
```

Jul  8 12:34:24 router tinc.testvpn[1728]: tincd 1.0.13 (Apr 13 2010 12:07:31) starting, debug level 0
Jul  8 12:34:24 router tinc.vpn6[1733]: tincd 1.0.13 (Apr 13 2010 12:07:31) starting, debug level 0
Jul  8 12:34:24 router tinc.svpn[1735]: tincd 1.0.13 (Apr 13 2010 12:07:31) starting, debug level 0
Jul  8 12:34:24 router tinc.clnt[1740]: tincd 1.0.13 (Apr 13 2010 12:07:31) starting, debug level 0
Jul  8 12:34:24 router tinc.svpn[1735]: Could not open /dev/net/tun: No such device
Jul  8 12:34:24 router tinc.svpn[1735]: Terminating
Jul  8 12:34:24 router tinc.testvpn[1728]: Could not open /dev/net/tun: No such device
Jul  8 12:34:24 router tinc.testvpn[1728]: Terminating
Jul  8 12:34:24 router tinc.clnt[1740]: Could not open /dev/net/tun: No such device
Jul  8 12:34:24 router tinc.clnt[1740]: Terminating
Jul  8 12:34:24 router tinc.vpn6[1733]: /dev/net/tun is a Linux tun/tap device (tap mode)
Jul  8 12:34:24 router tinc.vpn6[1733]: Ready

```
So it failed to find the tun device for 3 out for 4 VPNs, but it worked for one. Hmm.

Then I restarted Tinc, *without changing anything*:
```

Jul  8 12:44:32 router tinc.vpn6[1733]: Got TERM signal
Jul  8 12:44:32 router tinc.testvpn[4586]: tincd 1.0.13 (Apr 13 2010 12:07:31) starting, debug level 0
Jul  8 12:44:32 router tinc.testvpn[4586]: /dev/net/tun is a Linux tun/tap device (tun mode)
Jul  8 12:44:32 router tinc.testvpn[4586]: Ready
Jul  8 12:44:32 router tinc.vpn6[1733]: Terminating
Jul  8 12:44:33 router tinc.vpn6[4610]: tincd 1.0.13 (Apr 13 2010 12:07:31) starting, debug level 0
Jul  8 12:44:33 router tinc.vpn6[4610]: /dev/net/tun is a Linux tun/tap device (tap mode)
Jul  8 12:44:33 router tinc.vpn6[4610]: Ready
Jul  8 12:44:33 router tinc.svpn[4629]: tincd 1.0.13 (Apr 13 2010 12:07:31) starting, debug level 0
Jul  8 12:44:33 router tinc.svpn[4629]: /dev/net/tun is a Linux tun/tap device (tap mode)
Jul  8 12:44:33 router tinc.svpn[4629]: Ready
Jul  8 12:44:34 router tinc.clnt[4666]: tincd 1.0.13 (Apr 13 2010 12:07:31) starting, debug level 0
Jul  8 12:44:34 router tinc.clnt[4666]: /dev/net/tun is a Linux tun/tap device (tap mode)
Jul  8 12:44:34 router tinc.clnt[4666]: Ready

```

So it seems like a race condition somewhere that only rarely occurs. I have never seen Tinc fail to start because of this before.

---

