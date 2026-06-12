---
title: "Atmel at76c50x connectivity issues"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by linuxwebguy on 2006-06-19
Hello all,

I'm a recent [k]ubuntu user, but have been using linux (debian, older mandrake) for a long time.

I've come across an older Compaq TC1000 tablet PC, and decided try kubuntu.  It's taken a lot of work to get running.  Eventually I'll get everything going on it, but the next step is wireless.

lspci tells me:
0000:00:0a.0 Ethernet controller: Atmel Corporation at76c506 802.11b Wireless Network Adaptor (rev 11)

From what I've read (on these forums and via google), I need to load the atmel_pci driver (I'm running 2.6.15-25-686 from ubuntu dapper), and I seem to have the atmel firmware installed under /lib/firmware.  I load the firmware with:

/usr/sbin/atmel_fwl eth1 /lib/firmware/2.6.15-25-686/atmel_at76c506.bin

I setup /etc/network/interfaces to run this command as a pre-up when loading the interface, but I don't know if this is the preferred method or not.  hotplug is not installed (not sure exactly why).

Here's the output from iwconfig eth1:

eth1      IEEE 802.11-DS  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:10:18:xx:xx:xx
          Bit Rate:11 Mb/s
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:382  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

What really confuses me is the "Rx invalid nwid:382".  Why so high?  I tried to run: 
$ sudo iwconfig eth1 nwid off
Error for wireless request "Set NWID" (8B02) :
    SET failed on device eth1 ; Operation not supported.

Hmmm ok.  Here's the output of ifconfig eth1:

eth1      Link encap:Ethernet  HWaddr 00:08:02:D2:69:E0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:96 errors:2300 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13090 (12.7 KiB)  TX bytes:0 (0.0 b)
          Interrupt:15 Base address:0x1c00

That's a lot of errors.  I've been spoiled in the past with orinoco and Cisco wireless cards, and haven't had to deal with firmware cards.  They seem pretty complicated.

Can anyone shed some light on my wireless issue?  Or point me in the right direction?

---

### Post by linuxwebguy on 2006-06-20
*bump*

Anybody?

---

### Post by nodows on 2006-10-15
you ever figure anything out?  I'm havin the same problem...

---

