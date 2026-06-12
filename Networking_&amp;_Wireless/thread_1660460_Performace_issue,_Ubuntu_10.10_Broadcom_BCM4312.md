---
title: "Performace issue, Ubuntu 10.10 Broadcom BCM4312"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by merced.se on 2011-01-05
I've recently installed Ubuntu 10.10 on my Dell Inspiron 1525.
It all works quite well except the wireless network card, a Broadcom BCM4312.
I have found and read quite a lot of threads about people having problems with these cards. I have, however, not found anyone having exactly my problem and none of the solutions i found helps me 100%.
My problem is that my connection is extremely slow after reboot. It is so slow a cant load any website. Ping responses from sites like google takes 1-2 seconds.
I can get the network connection to work perfectly by running:
```
sudo rmmod wl
sudo modprobe wl
```
I have to perform that operation after every reboot to get the network connection up to acceptable speeds.

This is from directly after a system start:
```
ola@olatop:~$ ping www.google.com
PING www.l.google.com (66.102.13.106) 56(84) bytes of data.
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=1 ttl=52 time=2061 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=2 ttl=52 time=1057 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=3 ttl=52 time=2111 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=6 ttl=52 time=2130 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=7 ttl=52 time=1132 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=9 ttl=52 time=2065 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=10 ttl=52 time=1063 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=11 ttl=52 time=2113 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=12 ttl=52 time=2065 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=13 ttl=52 time=1067 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=14 ttl=52 time=2130 ms
^C
--- www.l.google.com ping statistics ---
15 packets transmitted, 11 received, 26% packet loss, time 37173ms
rtt min/avg/max/mdev = 1057.329/1727.275/2130.883/490.111 ms, pipe 3
ola@olatop:~$ sudo rmmod wl
[sudo] password for ola: 
ola@olatop:~$ sudo modprobe wl
ola@olatop:~$ ping www.google.com
PING www.l.google.com (66.102.13.147) 56(84) bytes of data.
64 bytes from ez-in-f147.1e100.net (66.102.13.147): icmp_req=1 ttl=52 time=70.9 ms
64 bytes from ez-in-f147.1e100.net (66.102.13.147): icmp_req=2 ttl=52 time=72.3 ms
64 bytes from ez-in-f147.1e100.net (66.102.13.147): icmp_req=3 ttl=52 time=71.9 ms
64 bytes from ez-in-f147.1e100.net (66.102.13.147): icmp_req=4 ttl=52 time=70.8 ms
64 bytes from ez-in-f147.1e100.net (66.102.13.147): icmp_req=5 ttl=52 time=72.0 ms
64 bytes from ez-in-f147.1e100.net (66.102.13.147): icmp_req=6 ttl=52 time=70.8 ms
64 bytes from ez-in-f147.1e100.net (66.102.13.147): icmp_req=7 ttl=52 time=98.4 ms
64 bytes from ez-in-f147.1e100.net (66.102.13.147): icmp_req=8 ttl=52 time=71.9 ms
64 bytes from ez-in-f147.1e100.net (66.102.13.147): icmp_req=9 ttl=52 time=72.7 ms
64 bytes from ez-in-f147.1e100.net (66.102.13.147): icmp_req=10 ttl=52 time=72.1 ms
64 bytes from ez-in-f147.1e100.net (66.102.13.147): icmp_req=11 ttl=52 time=72.3 ms
64 bytes from ez-in-f147.1e100.net (66.102.13.147): icmp_req=12 ttl=52 time=72.0 ms
^C
--- www.l.google.com ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11017ms
rtt min/avg/max/mdev = 70.855/74.046/98.433/7.381 ms
ola@olatop:~$ 
```

Some info (after modprobe wl is performed):
```
This is my network card from lspci -v | less:
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
        Subsystem: Dell Wireless 1395 WLAN Mini-Card
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fe7fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: wl
        Kernel modules: wl, ssb

ola@olatop:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

eth1      Scan completed :
          Cell 01 - Address: 00:19:5B:EE:D0:1A
                    ESSID:"Sldtrp15"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-48 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:23:F8:FD:48:5C
                    ESSID:"TN_private_4EU7YV"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-56 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s

ola@olatop:~$ dmesg | grep -i ath
[    0.563077] device-mapper: multipath: version 1.1.1 loaded
[    0.563080] device-mapper: multipath round-robin: version 1.0.0 loaded

ola@olatop:~$ dmesg | grep wl
[   12.326341] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.432354] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.432369] wl 0000:0b:00.0: setting latency timer to 64
[  168.904716] wl 0000:0b:00.0: PCI INT A disabled
[  178.586811] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  178.586831] wl 0000:0b:00.0: setting latency timer to 64
```

I have added the module wl to /etc/modules, but the connection is still slow after reboot.

I am quite new to Linux so I'm out of ideas.
All help is appreciated!

Thanx.

---

### Post by PatchesTheCaveman on 2011-01-05
Have you installed updates on this computer?  There is a faulty update for Ubuntu 10.10 Maverick Meerkat that causes problems with Broadcom wireless cards.

You can follow the instructions I provided in this post to see if you have the broken update and fix it:
[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)

If not, you can run the following commands to add the unload and reload commands to your /etc/rc.local file so it does it every time your computer starts as a workaround, so you don't have to do it yourself all the time:
```
sudo bash -c "echo modprobe -r wl >> /etc/rc.local"
sudo bash -c "echo modprobe wl >> /etc/rc.local"
```

---

### Post by merced.se on 2011-01-06
I have that faulty update:
```
ola@olatop:~$ uname -r
2.6.35-24-generic

```

I disabled automatic updates directly after I installed Ubuntu because it has happened to be before that some update caused problems with an installations that worked perfectly before the update. I did however update all new packages before I disabled automatic updates because I wanted my system to be up to date initially. Stupid!

In my Grub boot menu I also have 2.6.35-22-generic.
If I use that one I have no wireless network connection at all.
When I boot 2.6.35-24-generic I have two network devices: eth0 (wired) and eth1 (wireless).
When I boot 2.6.35-22-generic I only have eth0 (wired).

One thing that doesn't make sense to me is that your workaround isn't working. I get the same scenario after system startup with that workaround. I still hade to perform those operations manually.

---

### Post by chili555 on 2011-01-06
> 0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
        Subsystem: Dell Wireless 1395 WLAN Mini-Card
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fe7fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: wl
        Kernel modules: wl, [COLOR="Red"]ssb[/COLOR]
I think my colleague patches will be interested in why ssb is loading. Is it conflicting? Is it dragged along by the ethernet driver b44?

---

### Post by PatchesTheCaveman on 2011-01-06
merced.se:  You have to rebuild the STA driver for that kernel, because you  installed it after you updated.  To do that, boot into the 2.6.35-22-generic kernel, open a terminal, and run this command:
```
sudo dpkg-reconfigure bcmwl-kernel-source
```
It should work after that.  Once you get a working connection, you can run the commands in the second half of my post to delete the bad kernel and install the most-recent working 2.6.35-23-generic kernel.

chili555:  It most likely isn't loaded, unless like you said b44 is running too.  That line indicates the driver is a possible candidate, not actually loaded.  I have the exact same chipset with the exact same *lspci* output and *lsmod* tells me *ssb* is not running.

I'd hope *ssb* wouldn't conflict with the *bcmwl* driver, as then you couldn't use your Broadcom Ethernet and wireless (which I imagine are likely to be combined) at the same time! Running *modprobe b44* (which loads *ssb* too) doesn't break my *bcmwl* driver. (But that probably isn't a valid test since I don't actually have *b44* hardware.)

However, if the borked kernel isn't his problem, it's a definite possibility.

---

### Post by merced.se on 2011-01-08
I booted my system with the 2.6.35-22-generic kernel. Same problem:
```
ola@olatop:~$ ping www.google.com
PING www.l.google.com (66.102.13.105) 56(84) bytes of data.
64 bytes from ez-in-f105.1e100.net (66.102.13.105): icmp_req=1 ttl=52 time=1946 ms
64 bytes from ez-in-f105.1e100.net (66.102.13.105): icmp_req=2 ttl=52 time=950 ms
64 bytes from ez-in-f105.1e100.net (66.102.13.105): icmp_req=3 ttl=52 time=2063 ms
64 bytes from ez-in-f105.1e100.net (66.102.13.105): icmp_req=4 ttl=52 time=1063 ms
64 bytes from ez-in-f105.1e100.net (66.102.13.105): icmp_req=5 ttl=52 time=2110 ms
^C
--- www.l.google.com ping statistics ---
6 packets transmitted, 5 received, 16% packet loss, time 16485ms
rtt min/avg/max/mdev = 950.724/1627.004/2110.514/510.010 ms, pipe 3
ola@olatop:~$ sudo rmmod wl
ola@olatop:~$ sudo modprobe wl
ola@olatop:~$ ping www.google.com
PING www.l.google.com (66.102.13.106) 56(84) bytes of data.
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=1 ttl=52 time=70.3 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=2 ttl=52 time=69.9 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=3 ttl=52 time=69.7 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=4 ttl=52 time=69.6 ms
64 bytes from ez-in-f106.1e100.net (66.102.13.106): icmp_req=5 ttl=52 time=69.9 ms
^C
--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 69.653/69.930/70.341/0.331 ms
ola@olatop:~$ uname -r
2.6.35-22-generic
ola@olatop:~$ 

```

This is my lsmod:
```
ola@olatop:~$ lsmod
Module                  Size  Used by
wl                   1959533  0 
michael_mic             1744  4 
arc4                    1165  2 
parport_pc             26058  0 
ppdev                   5556  0 
rfcomm                 33811  4 
sco                     7998  2 
bnep                    9542  2 
binfmt_misc             6599  1 
l2cap                  37008  16 rfcomm,bnep
snd_hda_codec_idt      54887  1 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
i915                  291004  3 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 i915
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  4 i915,drm_kms_helper
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
lib80211_crypt_tkip     7736  0 
btusb                  10969  2 
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
r852                    9536  0 
sm_common               3285  1 r852
intel_agp              26360  2 i915
nand                   34905  2 r852,sm_common
soundcore                880  1 snd
lib80211                5058  2 wl,lib80211_crypt_tkip
dell_laptop             5730  0 
dell_wmi                2852  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
agpgart                32011  2 drm,intel_agp
psmouse                59033  0 
output                  1883  1 video
mtd                    18877  2 sm_common,nand
dcdbas                  5402  1 dell_laptop
serio_raw               4022  0 
joydev                  8735  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
firewire_ohci          21106  0 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
firewire_core          46643  1 firewire_ohci
led_class               2633  1 sdhci
crc_itu_t               1383  1 firewire_core
ahci                   19013  0 
libahci                21667  5 ahci
sky2                   45127  0 

```

There is one more thing that i should mention. I get this message when the system is started:
[IMG]http://web.merced.se/NetworkServiceDiscoveryDisabled.png[/IMG]

---

### Post by PatchesTheCaveman on 2011-01-08
Don't worry about the Avahi error.

I'd love to be able try and see if I can replicate this behavior but I'm away for the holidays until early next week and am presently stuck on dialup, so I'm afraid my ping times will suck regardless.

The only other thing I could suggest is updating to the latest version of the Broadcom STA driver.  You can download it here:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Before you do that, I suggest you update to the latest working version of the kernel.  To do that run:
```
sudo apt-get install linux-image-2.6.35-23-generic
```

That will automatically rebuild the older version of the STA driver included with Ubuntu on the newer kernel so you can give that a shot as well.

---

### Post by merced.se on 2011-01-11
So I tried to reinstall the driver from the instructions for Ubuntu at the end of this file:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

The same problem still occur.

---

### Post by merced.se on 2011-01-11
Hey! It works!
I can't really say why I'm afraid...

I removed the walkaround in the /etc/rc.local file.
In the file /etc/modules the wl-module was specified, I removed that.

After a reboot it seems to work fine. :D

Thanx for all help!

EDIT: Never mind. It worked yesterday. Today it's back to "normal" with slow connection. I have not changed a thing since yesterday. This seems close to impossible to fix...

---

### Post by jorgan1024 on 2011-01-13
I have a card in the same series in my Samsung Netbook, either the BCM4311, 4312, 4321 or 4322.

I'm not sure if we have the same problem but when I turn my computer on / wake from sleep it takes close to 30 seconds (after the desktop appears) before wireless is ready in linux-image-2.6.35-24-generic.

In linux-image-2.6.35-22-generic it seemed faster but I haven't done any benchmarking.

Also I always need to give the default keyring password before wireless can connect, something I don't have to do on other computers, is that due to the proprietary driver?

---

### Post by PatchesTheCaveman on 2011-01-13
There are known problems with kernel version  linux-image-2.6.35-24-generic and Broadcom devices (though usually they just don't work at all).  You might try kernel linux-image-2.6.35-23-generic.

Is that computer configured to automatically log you in?  If so you will be asked for the keyring password for security reasons.

---

### Post by jorgan1024 on 2011-01-13
Yep it logs in automatically, I was trying to save time/hassel on entering a password but this seems to have defeated the purpose of that, thanks for pointing that out caveman.

I've tried 2.6.35-22 a few times now but it seems just as slow to connect (its only a new installation so I don't have any other versions to test atm)

I was originally told by a Samsung rep that the wireless was unsupported in *nix so I was pleasantly surprised when Ubuntu told me a driver was available and it started working, its just really slow to connect (Windows 7 connects almost instantly), but is otherwise fine.  But this seems to be of less concern than what other people are experiencing.

---

### Post by PatchesTheCaveman on 2011-01-14
Does the wireless network not show up at all for awhile, or does it just connect really slowly?

I experience the former behavior with my Broadcom device.  You can get around it by choosing *Connect to hidden network* from the wireless menu and choosing your wireless network from there.

---

### Post by merced.se on 2011-01-14
My connection connects at once directly after startup, it is the connection (bandwidth, ping responses) that is very slow.
When I reload the wl-module it takes about 20-30 seconds before the connection is up and running, but the the performance is as expected.

---

### Post by merced.se on 2011-01-14
My connection connects at once directly after startup, it is the connection (bandwidth, ping responses) that is very slow.
When I reload the wl-module it takes about 20-30 seconds before the connection is up and running, but the the performance is as expected.

---

### Post by merced.se on 2011-01-14
My connection connects at once directly after startup, it is the connection (bandwidth, ping responses) that is very slow.
When I reload the wl-module it takes about 20-30 seconds before the connection is up and running, but the the performance is as expected.

---

### Post by PatchesTheCaveman on 2011-01-14
Have you tried using the b43 driver?

To install and activate it:
```
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe -r wl
sudo modprobe b43
```

If that works better, disable the STA driver:
```
sudo bash -c "echo blacklist wl >> /etc/modprobe.d/blacklist.conf"
```

If it makes it worse, switch back to the STA driver and disable the b43 driver just in case:
```
sudo modprobe -r b43
sudo modprobe wl
sudo bash -c "echo blacklist b43 >> /etc/modprobe.d/blacklist.conf"
```

---

### Post by merced.se on 2011-01-15
That worked for a while. 

I had to add the b43-driver to /etc/modules to get it to autoload. The wl-driver was added to blacklist.
The connection was up and running directly after boot and the network performance was perfect. I tried to reboot a couple of times and the connections worked perfect for about 20min. Suddenly, when I was browsing the web, I was prompted for the network password. Now nothing works.

Other devices that is connected to my wireless network works fine, so it's not the network that is the problem.

Does Ubuntu have something equivalent to the Windows restore points? The wireless connections is down permanently after installing en b43 driver so I'm stuck with the ethernet cable... Uninstalling that driver didn't help. I would like to restore the system to before I installed the b43 driver.

---

### Post by merced.se on 2011-01-15
What is the difference between installing the b43 driver using apt-get as in the instructions above and using the graphical installer in System -> Administration -> Additional drivers? If I try to activate the b43 driver there I get this error message:
"System error: installArchives() failed."
If I install by using apt-get it seems to install fine, my wireless network is automatically detected but I cant connect.

If I try to use the STA driver no wireless networks can be found anymore.

It seems that a lot of people that were happy with 10.04 are having problem with 10.10. Perhaps I should do a clean install and choose 10.04 LTS instead?

---

### Post by merced.se on 2011-01-16
I dont get this... yesterday nothing worked. Today I just started the laptop and the wireless network was detected at once. 

Instable is what it is. :roll:

---

### Post by vilson on 2011-01-30
merced.se
i had the same problem with my HP laptop, i tryed to reinstall the STA driver and then the Bc43, and it was always the same...wireless working until the next reboot or shutdown, and the connection slow slow slow!

this is what i've done:
After trying one and othjer driver i don't know wy, it stoped loading the "wl" module so i edited the file /etc/modules and added "wl" module to the list.

Wireless was ON but slow.

So i followed [PatchesTheCaveman]("http://start.ubuntuforums.org/member.php?u=922660") post ([http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)) and removed kernel 2.6.35.24 and 2.6.35.25 and reinstalled the 2.6.35.23. Now when the computer starts wireless is connected and with great speed. I rebooted a few times and seems fine.

Hope it helps ;-)

---

