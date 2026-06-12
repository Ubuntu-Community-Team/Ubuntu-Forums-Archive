---
title: "Wireless RT73 will not connect"
date: 2012-01-19
forum: Networking &amp; Wireless
---

### Post by silvergoat on 2012-01-19
Hello,

I have a USB rt73 generic wifi adapter installed, but this last time I turned it on it refused to connect to the router.  I am not sure if I used the wrong drivers or if there is some conflict after some updates.

It is connected via a USB PCI card, but it has worked.  I am not sure where to look now since I have tried reinstalling the drivers several times with no luck.  It just searches and searches but never connects even though the available networks are visible and the security information is entered correctly.

I did configure my router to use MAC address filtering, and I believe I have the right address entered in my WNDR3300, but I don't know how to verify.  This is the driver I downloaded and installed: RTL8188CE-VAU

lsusb returns:

```
Bus 006 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod returns:

```
Module                  Size  Used by
dm_crypt               22463  0 
vesafb                 13449  1 
snd_intel8x0           33213  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
8192cu                488045  0 
ppdev                  12849  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
nvidia               7098106  24 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
joydev                 17322  0 
serio_raw              12990  0 
parport_pc             32111  1 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
hid_logitech           17421  0 
ff_memless             12945  1 hid_logitech
usbhid                 41704  1 hid_logitech
hid                    77084  2 hid_logitech,usbhid
tg3                   131476  0 
floppy                 60032  0 

```

iwconfig returns:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

What am I doing wrong?

---

### Post by chili555 on 2012-01-19
> I did configure my router to use MAC address filtering, and I believe I have the right address entered in my WNDR3300, but I don't know how to verify. Let's start at the easy steps and go on from there. Open a terminal and run:```
ifconfig
```Here is an example:```
$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1569 (1.5 KB)  TX bytes:1569 (1.5 KB)

wlan0     Link encap:Ethernet  HWaddr [COLOR="Red"]99:19:d2:22:1b:88[/COLOR]  
          inet addr:192.168.1.108  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fec2:1b8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1727383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1124587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2167115813 (2.1 GB)  TX bytes:142759544 (142.7 MB)
```The part I highlighted is the MAC address. Check yours in the router. Does it connect with MAC filtering temporarily turned off?

Are there any clues here?```
sudo cat /var/log/syslog | grep wlan | tail -n20
```

---

### Post by silvergoat on 2012-01-19
This is what I got when I typed in that last command- MAC address is correct.

```
Jan 19 13:53:24 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <warn> (wlan0): link timed out.
Jan 19 13:53:29 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 19 13:53:30 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 19 13:53:31 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 19 13:53:40 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 19 13:53:42 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 19 13:53:43 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 19 13:53:46 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <warn> (wlan0): link timed out.
Jan 19 13:53:52 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 19 13:53:53 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 19 13:53:54 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 19 13:54:03 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 19 13:54:04 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 19 13:54:05 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 19 13:54:06 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <warn> Activation (wlan0/wireless): association took too long.
Jan 19 13:54:06 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): device state change: 5 -> 9 (reason 7)
Jan 19 13:54:06 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <warn> Activation (wlan0) failed for access point (SimplyPC-G)
Jan 19 13:54:06 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <warn> Activation (wlan0) failed.
Jan 19 13:54:06 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jan 19 13:54:06 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): deactivating device (reason: 0).

```

---

### Post by chili555 on 2012-01-19
And if you temporarily turn off MAC filtering, what does it look like?

---

### Post by silvergoat on 2012-01-19
This is what it looks like with MAC filtering off:

```
Jan 19 17:22:16 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <warn> (wlan0): link timed out.
Jan 19 17:22:21 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 19 17:22:22 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 19 17:22:23 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 19 17:22:32 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 19 17:22:34 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 19 17:22:35 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 19 17:22:38 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <warn> (wlan0): link timed out.
Jan 19 17:22:44 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 19 17:22:45 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 19 17:22:46 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 19 17:22:55 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 19 17:22:56 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 19 17:22:57 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 19 17:22:58 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <warn> Activation (wlan0/wireless): association took too long.
Jan 19 17:22:58 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): device state change: 5 -> 9 (reason 7)
Jan 19 17:22:58 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <warn> Activation (wlan0) failed for access point (SimplyPC-G)
Jan 19 17:22:58 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <warn> Activation (wlan0) failed.
Jan 19 17:22:58 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jan 19 17:22:58 simplypc-HP-d530-CMT-DS061AR NetworkManager[495]: <info> (wlan0): deactivating device (reason: 0).

```

---

### Post by silvergoat on 2012-01-25
Does anyone have any other suggestions?

---

