---
title: "Wireless stopped working after wine install"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by Speedwagon on 2010-04-05
And I haven't a clue as to why.  It was working fine before I had WINE on my system, and now it doesn't work.  I've been using the Broadcom STA wireless driver for my Linksys WMP300N with no problems, until now.  I've tried removing the driver, rebooting, and reactivating it, but to no avail.

Any idea how to fix this?

```

06:09.0 Network controller: Broadcom Corporation BCM43XG (rev 01)

```

A 'iwconfig wlan0' returns 'wlan0     No such device' now, whereas my wireless used to be wlan0.

---

### Post by chili555 on 2010-04-05
Let's take a look under the hood. Please open a terminal and do:```
sudo modprobe wl
dmesg | grep -e wl -e wlan
```Thanks.

---

### Post by Speedwagon on 2010-04-05
First one returned nothing.  Second one: 

```
[   10.179000] wl 0000:06:09.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[30818.907875] usbcore: registered new interface driver rndis_wlan

```

---

### Post by chili555 on 2010-04-05
Not much there. Let's see:```
lsmod
```

---

### Post by Speedwagon on 2010-04-05
```
Module                  Size  Used by
isofs                  36424  1 
udf                    88136  0 
crc_itu_t               2336  1 udf
binfmt_misc            10220  1 
ppdev                   8232  0 
rndis_wlan             25896  0 
snd_hda_codec_realtek   277860  1 
cfg80211              109144  1 rndis_wlan
rndis_host              9312  1 rndis_wlan
cdc_ether               6624  1 rndis_host
usbnet                 20936  3 rndis_wlan,rndis_host,cdc_ether
lib80211_crypt_tkip    10016  0 
amd64_edac_mod         26688  0 
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
usblp                  15136  0 
wl                   1277380  0 
lib80211                7812  2 lib80211_crypt_tkip,wl
snd_hda_intel          31880  4 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
usbhid                 43968  0 
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
xhci                   40772  0 
psmouse                57124  0 
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
serio_raw               6596  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
lp                     11908  0 
parport                40528  2 ppdev,lp
edac_core              48876  1 amd64_edac_mod
i2c_piix4              11728  0 
nvidia              10316904  36 
ohci1394               33780  0 
usb_storage            66304  1 
ieee1394              100896  1 ohci1394
r8169                  38884  0 
mii                     6368  2 usbnet,r8169
floppy                 65192  0 

```

---

### Post by chili555 on 2010-04-05
It looks very good. Any news in:```
iwconfig
```If you see no wireless interface, please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```Attach the dmesg.zip file to your reply.

---

### Post by Speedwagon on 2010-04-05
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

usb0      no wireless extensions.

```

Don't know if it makes a difference, but usb0 is how I am currently connecting to the internet(via my cell phone).

---

### Post by chili555 on 2010-04-05
While I gaze upon your dmesg, what do you think eth2 is?> eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


---

### Post by chili555 on 2010-04-05
I think your wireless is working:> $ cat dmesg.txt | grep eth
[    1.858299] eth0: RTL8168d/8111d at 0xffffc90000346000, 6c:f0:49:0d:0b:9f, XID 283000c0 IRQ 30
[   10.549408] [COLOR="Blue"]eth1: Broadcom BCM4329 802.11 Wireless Controller[/COLOR] 5.10.91.9
[   10.552421] [COLOR="Blue"]udev: renamed network interface eth1 to eth2[/COLOR]
[   10.589972] usbcore: registered new interface driver cdc_ether
[   11.580431] r8169: eth0: link down
[   11.580623] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.780009] [COLOR="Blue"]eth2: no IPv6 routers present[/COLOR]Does Network Manager see an eth2?

---

### Post by Speedwagon on 2010-04-06
Network manager shows the 'Wireless Networks' area, but it will not actually see any networks, and fails to connect to anything(if I manually type it in).  And there's at least 10 networks in the area for it to see.  And I'm not sure what eth2 is, as my wireless used to be wlan0 before playing with wine.

---

### Post by chili555 on 2010-04-06
Let's see:```
nm-tool
sudo iwlist eth2 scan
```Thanks.

---

### Post by Speedwagon on 2010-04-06
```
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        6C:F0:49:0D:0B:9F

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:1E:E5:A6:04:3E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


$ sudo iwlist eth2 scan

eth2      No scan results


```

---

### Post by chili555 on 2010-04-06
Network Manager is designed not to allow a wireless connection if wired is available. You have a connection and an IP address with your wired interface. Please detach the ethernet cable, wait a few moments for Network Manager to notice the change of state and do:```
sudo ifconfig eth2 up
sudo iwlist eth2 scan
```Any improvement? If not, please do:```
sudo cat /var/log/syslog | grep -e eth2 -e wl
```I am wondering why this card doesn't spring to life.

---

### Post by Speedwagon on 2010-04-06
Disconnected the wired ethernet, waited a minute or two, and tried what you said.  But the wireless still didn't want to work.

```
-desktop:~$ sudo iwlist eth2 scan
eth2      No scan results

-desktop:~$ sudo ifconfig eth2 up

-desktop:~$ sudo iwlist eth2 scan
eth2      No scan results

-desktop:~$ sudo cat /var/log/syslog | grep -e eth2 -e wl
-desktop:~$ 

```

That's what I got.  I suppose I could attempt to remove the card, boot into Ubuntu, and then shut down and reinstall.  I know that tends to help Winblows out a lot when things break.

---

### Post by chili555 on 2010-04-06
If the reinstall is not too troublesome, it might just fix it. I am frankly out of ideas.

---

### Post by Speedwagon on 2010-04-06
> **chili555 said:**
> If the reinstall is not too troublesome, it might just fix it. I am frankly out of ideas.

I'll do that now then.  Anything to run after I boot up without the card, to see what's what?

---

### Post by chili555 on 2010-04-06
Not that I can think of. Just do:```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
iwconfig
```Post back if it doesn't go perfectly.

---

### Post by Speedwagon on 2010-04-06
eth2 is now gone, as I am in Ubuntu with the wireless card out.

```
-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:0d:0b:9f  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fe0d:b9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:736133 (736.1 KB)  TX bytes:257990 (257.9 KB)
          Interrupt:30 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9609 (9.6 KB)  TX bytes:9609 (9.6 KB)

```

Now to shut down and reinstall.

---

### Post by Speedwagon on 2010-04-06
```
-desktop:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

-desktop:~$ sudo modprobe wl
FATAL: Could not read '/lib/modules/2.6.31-20-generic/updates/dkms/wl.ko': Invalid argument

```

?

---

### Post by Speedwagon on 2010-04-06
Ok, now the STA driver's won't install or uninstall.  During the "activate" stage of the hardware drivers for the STA drivers, the computer froze.  I went into synaptic and it won't completely remove, or reinstall the drivers.  It's somehow in limbo now.

```
E: bcmwl-kernel-source: subprocess installed post-installation script returned error exit status 2

```

---

### Post by chili555 on 2010-04-06
What's in limbo? The whole computer? Or the Hardware Driver installer? Can you reboot?

---

### Post by Speedwagon on 2010-04-06
> **chili555 said:**
> What's in limbo? The whole computer? Or the Hardware Driver installer? Can you reboot?

The hardware driver install.  The computer is fine now, but the driver won't uninstall, or reinstall now.  And it's not completely installed, so it doesn't work.  This is trying it via synaptic package manager.

---

### Post by chili555 on 2010-04-06
Can you close Synaptic?```
sudo killall synaptic
sudo apt-get remove --purge bcmwl-kernel-source
```

---

### Post by Speedwagon on 2010-04-06
> **chili555 said:**
> Can you close Synaptic?```
sudo killall synaptic
sudo apt-get remove --purge bcmwl-kernel-source
```

Yea, synaptic closed fine.

```
Removing bcmwl-kernel-source ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing bcmwl-kernel-source (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by chili555 on 2010-04-07
Try it again without *--purge*.

---

### Post by Speedwagon on 2010-04-07
Well, it's fixed.  But I went ahead and upgraded to 10.04 beta last night, as I was getting tired of trying to get the stupid thing to work.

After the upgrade, it defaulted to the STA drivers.  Just to make sure, I removed them and reinstalled, rebooted, and all is right with the world again.

---

