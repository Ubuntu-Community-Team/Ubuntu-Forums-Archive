---
title: "Wirless works, wired does not"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by GUZZLR on 2013-05-19
Ubuntu 13.04 install, got the wireless to work, but still can not get the wired to work. 
Dell Latitude D630
full install over XP Pro
BCM 4311
Thanks

---

### Post by GUZZLR on 2013-05-19
Also wanted to say it does pick up directly off the modem, so I thought it was my router, so I tied my old router, and it does not work off of that one either, or my next door neighbors. router, so I think I'm missing some drivers for the ethernet cable part...wireless works ok. The wired LAN card is a Broadcom Netextreme 57xx. 
Thanks

---

### Post by GUZZLR on 2013-05-21
anybody got any suggestions, or where I can get LAN drivers for Dell Latitude D630.  I searched on Dell's website, but I did not see any drivers for Linux
Thanks

---

### Post by Hadaka on 2013-05-21
Hi, lets take a look at those cards...
please COPY  and paste the following...
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
post the output.
thanks.

---

### Post by GUZZLR on 2013-05-21
Here's what I got...Thanks for the help

```
charles@Raspberry:~$ lspci -nn | egrep '0200|0280'
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
charles@Raspberry:~$ lsmod
Module Size Used by
parport_pc 27504 0 
ppdev 12817 0 
rfcomm 37420 12 
bnep 17669 2 
binfmt_misc 17260 1 
snd_hda_codec_idt 63896 1 
ext2 63166 1 
joydev 17097 0 
arc4 12543 2 
coretemp 13131 0 
kvm 376505 0 
snd_hda_intel 38307 3 
snd_hda_codec 117580 2 snd_hda_codec_idt,snd_hda_intel
dell_wmi 12601 0 
sparse_keymap 13658 1 dell_wmi
snd_hwdep 13272 1 snd_hda_codec
gpio_ich 13236 0 
snd_pcm 80890 2 snd_hda_codec,snd_hda_intel
pcmcia 39544 0 
b43 351918 0 
i915 535507 3 
snd_page_alloc 14230 2 snd_pcm,snd_hda_intel
snd_seq_midi 13132 0 
snd_seq_midi_event 14475 1 snd_seq_midi
snd_rawmidi 25114 1 snd_seq_midi
bcma 39645 1 b43
snd_seq 51280 2 snd_seq_midi_event,snd_seq_midi
mac_hid 13037 0 
snd_seq_device 14137 3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer 24411 2 snd_pcm,snd_seq
yenta_socket 27095 0 
pcmcia_rsrc 18191 1 yenta_socket
pcmcia_core 21505 3 pcmcia,pcmcia_rsrc,yenta_socket
drm_kms_helper 47545 1 i915
mac80211 526519 1 b43
snd 56485 15 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
wmi 18590 1 dell_wmi
drm 228750 4 i915,drm_kms_helper
video 18894 1 i915
lpc_ich 16925 0 
dell_laptop 17161 0 
dm_multipath 22402 0 
psmouse 81038 0 
ssb_hcd 12749 0 
cfg80211 436177 2 b43,mac80211
dcdbas 14021 1 dell_laptop
microcode 18286 0 
scsi_dh 14427 1 dm_multipath
serio_raw 13031 0 
i2c_algo_bit 13197 1 i915
soundcore 12600 1 snd
lp 13299 0 
parport 40753 3 lp,ppdev,parport_pc
btusb 17986 0 
bluetooth 202069 22 bnep,btusb,rfcomm
hid_generic 12484 0 
usbhid 41805 0 
hid 82666 2 hid_generic,usbhid
firewire_ohci 35292 0 
tg3 143666 0 
firewire_core 61718 1 firewire_ohci
ptp 18189 1 tg3
ssb 50628 2 b43,ssb_hcd
pps_core 13736 1 ptp
crc_itu_t 12627 1 firewire_core
dm_raid45 75357 0 
xor 26062 1 dm_raid45
dm_mirror 21621 0 
dm_region_hash 16012 1 dm_mirror
dm_log 18137 3 dm_region_hash,dm_mirror,dm_raid45
charles@Raspberry:~$ rfkill list all
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
charles@Raspberry:~$
```

---

### Post by Hadaka on 2013-05-21
thanks, lets try this...
```
sudo modprobe -rfv tg3
modprobe tg3
```
then post the output of...
```
dmesg | grep tg3
nm-tool
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
```
thanks
please enclose your output in code tags

---

### Post by GUZZLR on 2013-05-22
> **Hadaka said:**
> 
please enclose your output in code tags

How do I utilize the "Tag" Boxes?

Never Mind, I figured it out...I'll send updated data later
Thanks

---

### Post by GUZZLR on 2013-05-22
Here's what I got...
Thanks for the help

```
charles@Raspberry:~$ sudo modprobe -rfv tg3
[sudo] password for charles: 
rmmod tg3
rmmod ptp
rmmod pps_core
charles@Raspberry:~$ modprobe tg3
ERROR: could not insert 'tg3': Operation not permitted
charles@Raspberry:~$ modprobe tg3
ERROR: could not insert 'tg3': Operation not permitted
charles@Raspberry:~$ dmesg | grep tg3
[    2.502794] tg3.c:v3.128 (December 03, 2012)
[    2.534107] tg3 0000:09:00.0 eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address 00:1c:23:38:fc:08
[    2.534113] tg3 0000:09:00.0 eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.534116] tg3 0000:09:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.534120] tg3 0000:09:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   21.708625] tg3 0000:09:00.0: irq 45 for MSI/MSI-X
charles@Raspberry:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Saluki] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        00:1F:3A:31:08:3A

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    kmlacci:         Infra, 68:7F:74:14:67:26, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    schmitzhome2012: Infra, E0:46:9A:70:D8:19, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WEP
    HOME-DCF2:       Infra, 00:1D:D5:9A:DC:F0, Freq 2462 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    *Saluki:         Infra, 14:35:8B:0A:D0:B4, Freq 2437 MHz, Rate 54 Mb/s, Strength 78 WPA
    justin:          Infra, 00:13:10:6D:7A:9B, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    FJSE21:          Infra, 60:A4:4C:8C:CD:58, Freq 2457 MHz, Rate 54 Mb/s, Strength 59 WPA2
    ICUggs:          Infra, B8:9B:C9:26:D2:38, Freq 2447 MHz, Rate 54 Mb/s, Strength 47 WPA
    IEI:             Infra, C0:3F:0E:F1:52:18, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA

  IPv4 Settings:
    Address:         192.168.8.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.8.1

    DNS:             198.88.216.2
    DNS:             198.88.216.3


charles@Raspberry:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
charles@Raspberry:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
charles@Raspberry:~$ cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
charles@Raspberry:~$ 


```

---

### Post by Hadaka on 2013-05-22
Hi, try..

```
sudo modprobe tg3
```
thanks.

---

### Post by GUZZLR on 2013-05-22
Umm...I don't thank anything happened? 

```
charles@Raspberry:~$ sudo modprobe tg3
[sudo] password for charles: 
charles@Raspberry:~$ 

```

---

### Post by Hadaka on 2013-05-22
It means it accepted the command and liked it.
please do that again and we'll see if there are any
moans. Please do..
```
sudo modprobe -rfv tg3
sudo modprobe tg3
dmesg | grep eth
```
thanks

---

### Post by GUZZLR on 2013-05-22
This is fun!
But I'm going to bed.  I'll get with you tomorrow.  Thanks for all your help

```
charles@Raspberry:~$ sudo modprobe -rfv tg3
[sudo] password for charles: 
rmmod tg3
rmmod ptp
rmmod pps_core
charles@Raspberry:~$ sudo modprobe tg3
charles@Raspberry:~$ dmesg | grep eth
[    2.489845] tg3 0000:09:00.0 eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address 00:1c:23:38:fc:08
[    2.489852] tg3 0000:09:00.0 eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.489855] tg3 0000:09:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.489858] tg3 0000:09:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   15.397732] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.785173] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.785770] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  284.794236] tg3 0000:09:00.0 eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address 00:1c:23:38:fc:08
[  284.794252] tg3 0000:09:00.0 eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[  284.794261] tg3 0000:09:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[  284.794269] tg3 0000:09:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[  284.845177] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  284.845884] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
charles@Raspberry:~$ 


```

---

### Post by Hadaka on 2013-05-22
Hi, check your ethernet cable, try a different router port
or different cable...different router port.
then do ..
```
dmesg | grep eth
```
see if there are any changes
thanks.

---

### Post by varunendra on 2013-05-23
Please also check -
```
nm-tool
ifconfig -a
```
..after successfully doing the modprobe command (sudo modprobe -v tg3)

---

### Post by GUZZLR on 2013-05-23
```
charles@Raspberry:~$ dmesg | grep eth
[    2.533992] tg3 0000:09:00.0 eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address 00:1c:23:38:fc:08
[    2.533998] tg3 0000:09:00.0 eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.534002] tg3 0000:09:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.534005] tg3 0000:09:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   15.270788] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.543944] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.544843] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
charles@Raspberry:~$ 

```

Tried a different cable, in a different port.  Also, tried a different router (my backup router). Still no wired connection on either router, wireless works fine on both routers.
Main router: Medialink
Backup router: D-Link

---

### Post by GUZZLR on 2013-05-23
```
charles@Raspberry:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:1C:23:38:FC:08

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Saluki] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        00:1F:3A:31:08:3A

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    kmlacci:         Infra, 68:7F:74:14:67:26, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    HOME-DCF2:       Infra, 00:1D:D5:9A:DC:F0, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    airportthru:     Ad-Hoc, 7E:78:07:3C:3C:E0, Freq 2457 MHz, Rate 11 Mb/s, Strength 42
    ICUggs:          Infra, B8:9B:C9:26:D2:38, Freq 2447 MHz, Rate 54 Mb/s, Strength 57 WPA
    APARKER:         Infra, 30:46:9A:82:6F:10, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA2
    schmitzhome2012: Infra, E0:46:9A:70:D8:19, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WEP
    *Saluki:         Infra, 14:35:8B:0A:D0:B4, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA
    HOME-8B42:       Infra, 00:1D:D5:70:8B:40, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    kmlacci:         Infra, 68:7F:74:14:67:26, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    BUS2246:         Infra, 00:3A:9A:BF:D5:40, Freq 2462 MHz, Rate 54 Mb/s, Strength 44

  IPv4 Settings:
    Address:         192.168.8.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.8.1

    DNS:             198.88.216.2
    DNS:             198.88.216.3


charles@Raspberry:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:23:38:fc:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:965 errors:0 dropped:0 overruns:0 frame:0
          TX packets:965 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:109162 (109.1 KB)  TX bytes:109162 (109.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:31:08:3a  
          inet addr:192.168.8.101  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:fe31:83a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23617555 (23.6 MB)  TX bytes:1895546 (1.8 MB)

charles@Raspberry:~$ 

```

More stuff...Thanks for the help

---

### Post by Hadaka on 2013-05-23
Hi, lets try this..
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo modprobe -v tg3
```
lets see if anything pops up here
```

sudo cat /var/log/syslog | grep -e tg3 -e etwork | tail -n25 
```
thanks.

---

### Post by Hadaka on 2013-05-23
Let's also check some of the simple things that sometimes get overlooked.

click the wireless icon...next to the envelope...upper right corner...then
click Edit Connections
click Wired...and click YOUR ssid
click Edit
check Connect automatically and Available to all users
click IPv4...see attached
click IPv6...see attached
click Save and then close...see below
[ATTACH=CONFIG]242951[/ATTACH][ATTACH=CONFIG]242952[/ATTACH][ATTACH=CONFIG]242953[/ATTACH][ATTACH=CONFIG]242954[/ATTACH]

---

### Post by varunendra on 2013-05-23
> **Hadaka said:**
> Hi, lets try this..
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo modprobe -v tg3
```
I think the above needs a slight correction, the last command (sudo modprobe -v tg3) should be the first.

If that does not help, try a temporary static IP on ethernet interface -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.8.**[COLOR="#0000CD"]110[/COLOR]**
```
..assuming the IP ...**110** is not already taken by another device on the network. If it is, try an available one instead.
(Note: 'ifconfig eth0 up' is implied when you assign an IP to eth0, so it is not needed separately)

Wait about 10-20 seconds, then try pinging the gateway -
```
ping -c4 192.168.8.1
```
Does it get a response ?

If not, and if nm-tool still shows "carrier : off" under 'Wired Properties', then try resetting your BIOS to its defaults. (see : [https://answers.launchpad.net/ubuntu/+question/163932](https://answers.launchpad.net/ubuntu/+question/163932))

---

### Post by GUZZLR on 2013-05-23
umm...I got a little problem here.  I have no terminal to type into?  It is just a black square with a header, there is no place to type the command.  How do I get my terminal back?
[ATTACH=CONFIG]242955[/ATTACH]

---

### Post by Hadaka on 2013-05-23
Try booting the machine...or power down.
then click the "dash" the button upper left in the launcher
then type in..terminal...that should give you a terminal choice.

---

### Post by CharlesA on 2013-05-23
> **GUZZLR said:**
> umm...I got a little problem here.  I have no terminal to type into?  It is just a black square with a header, there is no place to type the command.  How do I get my terminal back?

I removed the base64 image that was dragged into the Browser window. If you need to post a screenshot, you can click on the "manage attachments" button and upload the image from there.

---

### Post by GUZZLR on 2013-05-23
```
charles@Raspberry:~$ sudo ifconfig eth0 down
[sudo] password for charles: 
charles@Raspberry:~$ sudo ifconfig eth0 up
charles@Raspberry:~$ sudo modprobe -v tg3
charles@Raspberry:~$ sudo cat /var/log/syslog | grep -e tg3 -e etwork | tail -n25
May 23 22:00:18 Raspberry NetworkManager[1211]: <info>   address 192.168.8.101
May 23 22:00:18 Raspberry NetworkManager[1211]: <info>   prefix 24 (255.255.255.0)
May 23 22:00:18 Raspberry NetworkManager[1211]: <info>   gateway 192.168.8.1
May 23 22:00:18 Raspberry NetworkManager[1211]: <info>   nameserver '198.88.216.2'
May 23 22:00:18 Raspberry NetworkManager[1211]: <info>   nameserver '198.88.216.3'
May 23 22:00:18 Raspberry NetworkManager[1211]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 23 22:00:18 Raspberry NetworkManager[1211]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
May 23 22:00:19 Raspberry NetworkManager[1211]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
May 23 22:00:19 Raspberry NetworkManager[1211]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
May 23 22:00:19 Raspberry NetworkManager[1211]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May 23 22:00:19 Raspberry NetworkManager[1211]: <info> Policy set 'Saluki' (wlan0) as default for IPv4 routing and DNS.
May 23 22:00:19 Raspberry NetworkManager[1211]: <info> DNS: starting dnsmasq...
May 23 22:00:19 Raspberry NetworkManager[1211]: <warn> dnsmasq not available on the bus, can't update servers.
May 23 22:00:19 Raspberry NetworkManager[1211]: <error> [1369364419.935950] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
May 23 22:00:19 Raspberry NetworkManager[1211]: <warn> DNS: plugin dnsmasq update failed
May 23 22:00:19 Raspberry NetworkManager[1211]: <info> Writing DNS information to /sbin/resolvconf
May 23 22:00:20 Raspberry NetworkManager[1211]: <info> Activation (wlan0) successful, device activated.
May 23 22:00:20 Raspberry NetworkManager[1211]: <warn> dnsmasq appeared on DBus: :1.51
May 23 22:00:20 Raspberry NetworkManager[1211]: <info> Writing DNS information to /sbin/resolvconf
May 23 22:00:39 Raspberry NetworkManager[1211]: <info> (wlan0): IP6 addrconf timed out or failed.
May 23 22:00:39 Raspberry NetworkManager[1211]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 23 22:00:39 Raspberry NetworkManager[1211]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 23 22:00:39 Raspberry NetworkManager[1211]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 23 22:04:29 Raspberry NetworkManager[1211]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
May 23 22:11:28 Raspberry kernel: [  726.736209] tg3 0000:09:00.0: irq 45 for MSI/MSI-X
charles@Raspberry:~$ 

```

Got my terminal back, I switched to another theme, and uninstalled the theme I was using

---

### Post by GUZZLR on 2013-05-23
[ATTACH=CONFIG]242957[/ATTACH]This is odd, I used to have a "wired network 1" listed here...now I don't anymore.  Do you think that is the problem?

---

### Post by varunendra on 2013-05-23
> **GUZZLR said:**
> How do I get my terminal back?
I downloaded the messed-up code for your 'base-64' image before CharlesA removed it. I fixed the code, and what I see WAS a terminal (see attachment). It could have been stuck. Wondering what theme it was :)


**PS:**
**[COLOR="#FF0000"]For Mods :[/COLOR]** copy code after 'base64,' as text > cat inputfile | base64 --decode > outputfile ; reference : [http://ubuntuforums.org/showthread.php?t=2097846](http://ubuntuforums.org/showthread.php?t=2097846)

Although what CharlesA did was a better solution - teaching users the correct use to avoid such bugs :)

---

### Post by GUZZLR on 2013-05-23
```
charles@Raspberry:~$ sudo modprobe -v tg3
[sudo] password for charles: 
charles@Raspberry:~$ sudo ifconfig eth0 down
charles@Raspberry:~$ sudo ifconfig eth0 up
charles@Raspberry:~$ sudo ifconfig eth0 down
charles@Raspberry:~$ sudo ifconfig eth0 192.168.8.110
charles@Raspberry:~$ ping -c4 192.168.8.1
PING 192.168.8.1 (192.168.8.1) 56(84) bytes of data.
From 192.168.8.110 icmp_seq=1 Destination Host Unreachable
From 192.168.8.110 icmp_seq=2 Destination Host Unreachable
From 192.168.8.110 icmp_seq=3 Destination Host Unreachable

--- 192.168.8.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms
pipe 4
charles@Raspberry:~$ ping -c4 192.168.8.1
PING 192.168.8.1 (192.168.8.1) 56(84) bytes of data.
From 192.168.8.110 icmp_seq=1 Destination Host Unreachable
From 192.168.8.110 icmp_seq=2 Destination Host Unreachable
From 192.168.8.110 icmp_seq=3 Destination Host Unreachable
From 192.168.8.110 icmp_seq=4 Destination Host Unreachable

--- 192.168.8.1 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3016ms
pipe 3
charles@Raspberry:~$ 

```

Nothing still,
Reseting the BIOS scares me...I had the problem of the machine not shutting down for the longest time because it would freeze on the Ubuntu splash screen. I finially got it working by using my "Boot Repair" .iso image.  Can we try something else before I mess around with the BIOS?

---

### Post by GUZZLR on 2013-05-23
```
[COLOR=#333333][FONT=arial]sudo add-apt-repository ppa:noobslab/themes[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]sudo apt-get install zoncolor-themes[/FONT][/COLOR]
[COLOR=#333333][FONT=arial][/FONT][/COLOR][COLOR=#333333][FONT=arial][/FONT][/COLOR][COLOR=#333333][FONT=arial][/FONT][/COLOR][COLOR=#333333][FONT=arial][/FONT][/COLOR]
```
Here's the theme pack which my machine did not like

---

### Post by Hadaka on 2013-05-23
are you using network mgr...or wcid?
*If you are using network mrg, then do.

```
sudo service network-manager restart
```
thanks

---

### Post by varunendra on 2013-05-24
> **GUZZLR said:**
> Can we try something else before I mess around with the BIOS?

Like mentioned in the launchpad answer page I linked to, see if the IRQ (Interrupts) are set to be "Set by the system" (or "Auto" or something similar) in your BIOS.

**Something important** - if your system is UEFI based and this is an EFI based installation, it may not be a good idea to reset the BIOS. I should have mentioned that earlier, I forgot, sorry. Besides, this is only one of a few possibilities, not necessarily the actual reason for the problem. So too much risk may not be worth unless everything else is ruled out.

Just see if there is an "auto" or "set by system" type setting for IRQs or not in the BIOS. Let us know if all the settings are manual.

Also, please install ethtool -
```
sudo apt-get install ethtool
```
..then run it and post back its output -
```
sudo ethtool eth0
```
It may give us more hints about what is going on.

---

### Post by GUZZLR on 2013-05-24
```
charles@Raspberry:~$ sudo service network-manager restart
[sudo] password for charles: 
network-manager stop/waiting
network-manager start/running, process 3369
charles@Raspberry:~$ 

```

I tried this, and I still had no network manager.  So I then Added "Ethernet Connection 1" and made sure the tabs were correct in your earlier reply (4 attachments) and I do have wired connection by hooking up directly to the modem, this is what was always available to me.  So I do have that...just not a wired connection through the router[ATTACH=CONFIG]242989[/ATTACH]

---

### Post by GUZZLR on 2013-05-24
```
charles@Raspberry:~$ sudo apt-get install ethtool
[sudo] password for charles: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms kde-l10n-engb libkprintutils4 libokularcore2abi1 libqimageblitz4
  linux-headers-generic linux-image-extra-3.8.0-19-generic linux-image-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ethtool
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 98.3 kB of archives.
After this operation, 305 kB of additional disk space will be used.
Get:1 http://mirror.anl.gov/pub/ubuntu/ raring/main ethtool i386 1:3.4.2-1 [98.3 kB]
Fetched 98.3 kB in 0s (725 kB/s) 
Selecting previously unselected package ethtool.
(Reading database ... 269342 files and directories currently installed.)
Unpacking ethtool (from .../ethtool_1%3a3.4.2-1_i386.deb) ...
Processing triggers for man-db ...
Setting up ethtool (1:3.4.2-1) ...
charles@Raspberry:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric
    Advertised auto-negotiation: Yes
    Speed: Unknown!
    Duplex: Unknown! (255)
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: g
    Wake-on: g
    Current message level: 0x000000ff (255)
                   drv probe link timer ifdown ifup rx_err tx_err
    Link detected: no
charles@Raspberry:~$ 

```

I do believe this machine is ERI boot because I have the purple Ubuntu screen with the "accesibility and keyboard" showing at the bottom, so it's booting in bios.

---

### Post by GUZZLR on 2013-05-24
```

Just see if there is an "auto" or "set by system" type setting for IRQs  or not in the BIOS. Let us know if all the settings are manual.
```

Sort of lost me on this one. Could you send me instructions about how to do this please

---

### Post by GUZZLR on 2013-05-24
[ATTACH=CONFIG]242990[/ATTACH]This is what it has always told me, a cable is unplugged, even when I unplug and plug back in.  If I hook direcly to the modem, the unplug cable goes away, and hooks up to the internet through the cable.  So this is when I thought it had to do something with the routher.  I then tried different routers and still no luck, so I dont think it is a router problem.  It is odd that it hooks up through the modem, but not through a router.  I am using Fiberoptic internet, not DSL or Cable...if that has anything to do with it.
Thanks for everybody's help

---

### Post by Hadaka on 2013-05-24
Are you using vz fios?

---

### Post by GUZZLR on 2013-05-24
> **Hadaka said:**
> Are you using vz fios?

I dont know what vz fios is?

---

### Post by Hadaka on 2013-05-24
its verizon fiber optic service, They usually supply
a modem/router combo one unit deal. Have you played
around with the router settings? with just modem, you have
a totally open connection, as an experiment, try setting your
router fully open as well, just to see if it will attach, then go
from there.

---

### Post by GUZZLR on 2013-05-24
oh yea...been messing with both routers, main and backup.  I also have a converted Chromebook I'm running 12.10 on, this little computer hooks up with no problems with a wired connection, on both my routers.  I can just plug the cable in, and the wireless automatically turns off and the wired connection begins.  So, it's definately something with the Dell running XP.  I have also been contacting Dell forum's, and have been told the computer is missing the LAN driver.  I have the LAN drivers which Dell has given me, but they are an executible file for windows I suppose, and do not want to work on Linux.  I have been unsuccessful getting Dell forum to get me drivers for the Linux OS, which is strange because Dell now offers computers loaded with Linux Ubuntu to the general public.

---

### Post by Hadaka on 2013-05-24
ok, give this a try..
click on the wireless icon...network mgr.
then..uncheck "Enable Wireless"
then..uncheck "Enable Networking"
wait 20 seconds
then..re-check "Enable Networking"
leave wireless unchecked..
watch for the up/down arrows where the wireless icon was
if after a few seconds..it doesnt show...do a re-boot;;restart
and of course..if it still doesnt work..check "Enable wireless"
post back.

---

### Post by GUZZLR on 2013-05-24
No, I'm very sorry, but still no wired connection.  All  it says is Ethernet connection disconnected, and it's grayed out

---

### Post by sgcsg1313 on 2013-05-24
Have your tried typing this by any chance?

"ifconfig eth0 up" without quotes

I've had this work sometimes in the past with older versions of Ubuntu for me

---

### Post by GUZZLR on 2013-05-24
```
charles@Raspberry:~$ ifconfig eth0 up
SIOCSIFFLAGS: Operation not permitted
charles@Raspberry:~$ 

```

Got this

---

### Post by Hadaka on 2013-05-25
hi the command is...
```
sudo ifconfig eth0 up
```

ok you have proven all cables .modem. router to be good.
also..the linux driver tg3 is correct, or it wouldnt work on a direct connect to the modem
and..there are hundreds of dells with your same card running tg3 and ubuntu
so everything is good with the exception that for some reason, your card and the router 
never do what is known as a handshake. as in....here i am...ok...and here i am....its ok to transfer data
the big questions is...Does the windows side...the xp..in the same computer connect WIRED...if YES
lets do this drastic move. For some reason..xp is shutting down the card and it wont awake unless xp
wakes it. Try this..power down the computer...remove the battery...then use the a/c adapter to power it
back up...boot into....windows xp...establish a WIRED connection.....then....yank the the power plug...power
crash it. This should leave the card enabled...now...replace the battery,plug back in, boot to Ubuntu and try
to establish a wired connection.

---

### Post by sgcsg1313 on 2013-05-25
Ah yes, thank you for correcting me with the sudo. I forgot about that, usually when Im in terminal i tend to be in root so i dont have to type my freakishly long password every time i need to install or configure something.

---

### Post by varunendra on 2013-05-25
> **GUZZLR said:**
> Sort of lost me on this one. Could you send me instructions about how to do this please
Never mind that, because of this -
> **GUZZLR said:**
> ...If I hook direcly to the modem, the unplug cable goes away, and hooks up to the internet through the cable.
....which means everything in BIOS is okay, nothing to suspect. You did mention in post #2 that you are able to connect directly, I just somehow missed it earlier.

Did you try using the same cable/router-port that you use with the Chromebook you mentioned?

Also, can you provide us a link to the router's user manual?

Did you, by any chance, fiddle with "DHCP pool" or "MAC binding" type things in the router? Although it doesn't explain why the other routers were unable to connect, but just in case..

Lastly, sorry if I missed you mentioning it earlier, is XP on the same Dell computer working fine with the same router/port/cable combination? If yes, then it 'may be' what Hadaka suggested. I have seen a couple of cases where the router firmware/firewall had a bug that didn't allow two different OSes connecting to it using the same Ethernet interface. But they were really old cases with some particular router models of D-Link, shouldn't exist in newer models but who knows !

---

### Post by GUZZLR on 2013-05-25
```
charles@Raspberry:~$ sudo ifconfig eth0 up
[sudo] password for charles: 
charles@Raspberry:~$ 

```

You wanted me to boot into windows, but I dont know how to do this because I did a full install of Linux, How do I get back to Windows?  I do know that before I installed Ubuntu on this machine, it was hooking up to the internet both wired and wirelessly.

---

### Post by GUZZLR on 2013-05-25
```

Did you try using the same cable/router-port that you use with the Chromebook you mentioned?

Also, can you provide us a link to the router's user manual?

Did you, by any chance, fiddle with "DHCP pool" or "MAC binding" type  things in the router? Although it doesn't explain why the other routers  were unable to connect, but just in case..

Lastly, sorry if I missed you mentioning it earlier, is XP on the same  Dell computer working fine with the same router/port/cable combination?  If yes, then it 'may be' what Hadaka suggested. I have seen a couple of  cases where the router firmware/firewall had a bug that didn't allow two  different OSes connecting to it using the same Ethernet interface. But  they were really old cases with some particular router models of D-Link,  shouldn't exist in newer models but who knows !
```


[LIST=1]
[*]Just used the same cable/router on the Chromebook, everything works good
[*][http://www.medialinkproducts.com/docs/12-2012/MWN-WAPR300N_User_Guide.pdf](http://www.medialinkproducts.com/docs/12-2012/MWN-WAPR300N_User_Guide.pdf)
[*]Did not mess with this stuff...it's above my paygrade.  All I did with both routers was turn off the routers internal firewall, which now that I think about it, would not do anything as the firewall is for wireless I believe.
[*]I don't think XP OS is on this computer, I dont see it on any of the partitions.  When I turn the computer on, it boots directly to Ubuntu
[/LIST]

Thanks for all the help

---

### Post by Hadaka on 2013-05-25
Hi , here are instructions on how to reset the bios
[http://www.ehow.com/how_6861224_replace-cmos-battery-dell-latitude.html](http://www.ehow.com/how_6861224_replace-cmos-battery-dell-latitude.html)
this should clear any bits that are preventing the card from turning on.
take your time..follow the instructions.

---

### Post by GUZZLR on 2013-05-25
Hello Hadaka,
The link for resetting the bios is about changing the internal battery, will pulling the battery out, and reinstalling it reset the bios?
Thanks

---

### Post by Hadaka on 2013-05-25
yes, pulling the cmos battery causes the bios to default to factory settings
mind you, one side of the battery is + positive and the other - negitive, be 
sure to keep track and replace exactly how you took it out.
good luck.

edit: dont forget to remove the big battery.

---

### Post by GUZZLR on 2013-05-25
So I believe the link for battery replacement is for a newer Dell Latitude laptop; mine is a little bit more difficult.  I did find the battery, to get to it:
[LIST=1]
[*]take the main battery off and discharge any remaining voltage by pressing and holding the power button
[*]carefully lift/pry off the surrounding plastic trim around the keyboard3
[*]remove the 3 small screws which hold the keyboard in place
[*]gently lift/pry the keyboard side clips from the perimeter of the keyboard
[*]lift - rotate - flip keyboard upside down and rest on palm pad
[*]the battery (3 volt) is now partially visible underneath a black plastic surround.  This battery is not a typical battery in that you can simply take out and replace. Instead, the battery is a battery module, which connects to the mother board via two wires, which I assume are power and ground.  I can not physically take the battery out with out separating the screen from the computer.
[*]I tried to disconnect the battery connector from the motherboard with some very small needle nose pliers (making sure not to pull the wires).  This I tried several times but was unsuccessful as the connector either has a hidden latch, or is connected very tight.
[*]I resembled the computer with out disconnecting the CMOS battery.
[/LIST]

[http://www.ehow.com/how_7521689_reset-cmos-latitude-d630.html](http://www.ehow.com/how_7521689_reset-cmos-latitude-d630.html)

Is there another way to reset the bios?
Thanks

---

### Post by Hadaka on 2013-05-25
whoa !...needle nose pliers is a bad thing,shorting the cmos
would not be good. anyway, depending on how new your computer
"some" dells allow BIOS reset by holding down the "F10" key...i think.
do a restart..or boot,,hold down the F2 key when it's booting up...that
should bring up the BIOS settings. you may have to do it a couple times
to get into bios...once there..it "should" say what key combo resets the
bios. my dell laptop is a 2005...it does not have that function..google yours
and see if it has the "F10" bios reset ability. On the cmos battery, use a tooth
pick..insulated..pry up then slide out from the U shaped battery holder.
good luck !

---

### Post by GUZZLR on 2013-05-25
So, I'm guessing using vise-grips when the needle-noses pliers didn't work may be worse :)
At any rate, the computer is back together and it still works.
One thing I probably should have mentioned, when I boot the laptop, in the top left corner of the screen, I get the words:

*xxxxxx kvm disabled by bios*

I use the x's because this number changes with each boot...I don't know if that helps any.

I'll try the boot instructions you write of and report back. Thanks

---

### Post by GUZZLR on 2013-05-25
I did several F keys while booting, and they got me to the boot menu, but I never found anything that allows me to reset bios.  I think we may have to realize the only way this computer will hookup with a wire is to simply go directly to the modem.
I  do have the "Boot Repair" disk, if that is of any use.
Thanks

---

### Post by varunendra on 2013-05-25
> **GUZZLR said:**
> I did several F keys while booting, and they got me to the boot menu, but I never found anything that allows me to reset bios.

All the BIOS menus I remember include an "Exit" tab in the last. Here, besides a couple of "exit" options, there are settings to "Load defaults" or "Load Optimized Defaults". This is similar to "Reset to Factory Settings". If your BIOS has this menu item (or similar), try it.

A few more things to experiment -

[LIST]
[*]When you are directly connected to the modem via cable, please run ifconfig and post back its output -
[/LIST]
```
ifconfig -a
```

[LIST]
[*]While being connected via router again, boot your laptop with Ubuntu Live CD/USB (that you installed from) or the Boot-Repair CD you have (close the boot-repair program and use it as a regular live OS). Can it connect via cable?
[/LIST]

If yes, post back the output of **ifconfig** from it.

If not, can it connect when directly hooked to the modem?

Also, if you are comfortable with it, save a backup of your router settings *(refer to topic "10.3 Backup/Restore", page 51 of the manual you linked to)*, then do a factory reset of the router and reconfigure it - only the most basic settings that are absolutely necessary to start the network. Then see if it can break the ice between the router and the ethernet. If anything goes wrong, you may just restore the settings from the backup file you saved.

---

### Post by GUZZLR on 2013-05-25
```
charles@Raspberry:~$ sudo ifconfig -a
[sudo] password for charles: 
eth0      Link encap:Ethernet  HWaddr 00:1c:23:38:fc:08  
          inet addr:66.94.205.167  Bcast:66.94.205.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe38:fc08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2669081 (2.6 MB)  TX bytes:288405 (288.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70774 (70.7 KB)  TX bytes:70774 (70.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:31:08:3a  
          inet6 addr: fe80::21f:3aff:fe31:83a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45249 (45.2 KB)  TX bytes:32748 (32.7 KB)


```

This is with the computer hooked directly to the modem.  I'll post back with it hooked to the router in a moment

---

### Post by GUZZLR on 2013-05-25
```
   

 [COLOR=#ff0000]Running on the Live CD:[/COLOR]
 [COLOR=#ff0000]This is Wired Connection to the router, no connectivity using the router[/COLOR]
 

 ubuntu@ubuntu:~$ sudo ifconfig -a  
 eth0      Link encap:Ethernet  HWaddr 00:1c:23:38:fc:08   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:17  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:65536  Metric:1  
           RX packets:189 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:189 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:16176 (16.1 KB)  TX bytes:16176 (16.1 KB)  
 

 

 [COLOR=#ff0000]This is wired connection directly to the modem, with out the router.  I do get connectivity[/COLOR]
 

 ubuntu@ubuntu:~$ sudo ifconfig -a
 eth0      Link encap:Ethernet  HWaddr 00:1c:23:38:fc:08   
           inet addr:66.94.204.248  Bcast:66.94.204.255  Mask:255.255.255.0
           inet6 addr: fe80::21c:23ff:fe38:fc08/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:31 errors:0 dropped:0 overruns:0 frame:0
           TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:5058 (5.0 KB)  TX bytes:14349 (14.3 KB)
           Interrupt:17  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:349 errors:0 dropped:0 overruns:0 frame:0
           TX packets:349 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0  
           RX bytes:29553 (29.5 KB)  TX bytes:29553 (29.5 KB)


```

So here are the two ifconfig's while using the live CD.  Basically the same thing...I can connect while using the modem directly, can not connect using the router.  I have reset the router too, and still can not connect...Thanks for the help

---

### Post by varunendra on 2013-05-25
> **GUZZLR said:**
> ```
charles@Raspberry:~$ sudo ifconfig -a
[sudo] password for charles: 
eth0      Link encap:Ethernet  HWaddr 00:1c:23:38:fc:08  
         **[COLOR="#FF0000"] inet addr:66.94.205.167[/COLOR]**  Bcast:66.94.205.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe38:fc08/64 Scope:Link

```
This is with the computer hooked directly to the modem.  I'll post back with it hooked to the router in a moment

Hmm.. makes sense, looks like we are reaching somewhere.

Now since you are able to connect the chromebook to the same router, could you please post the same ifconfig output from it? While being connected via ethernet of course.

---

### Post by GUZZLR on 2013-05-25
```
user@ChrUbuntu:~$ sudo ifconfig -a
[sudo] password for user: 
eth1      Link encap:Ethernet  HWaddr b8:88:e3:d2:b4:15  
          inet addr:192.168.8.102  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::ba88:e3ff:fed2:b415/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1489051 (1.4 MB)  TX bytes:128477 (128.4 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41935 (41.9 KB)  TX bytes:41935 (41.9 KB)

wlan0     Link encap:Ethernet  HWaddr 20:68:9d:b7:9c:4a  
          inet6 addr: fe80::2268:9dff:feb7:9c4a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50863 (50.8 KB)  TX bytes:30848 (30.8 KB)

user@ChrUbuntu:~$ 


```

Here is what I got.  This is from the Chromebook, connected to the router, wireless off, ethernet cable connected and working
Also, the Chromebook is running 12.10, while the Dell is on 13.04...Thanks

---

### Post by GUZZLR on 2013-05-25
Oh...you're right, I think I see a difference between the two on inet addr?

---

### Post by Hadaka on 2013-05-25
Hi, see if this will get rid of cyour kvm message
```

sudo apt-get purge qemu-kvm
```
boot and see if it went away.
thanks.

---

### Post by varunendra on 2013-05-25
> **GUZZLR said:**
> Oh...you're right, I think I see a difference between the two on inet addr?

Right. I'll be busy for a couple of hours, meanwhile here a quick one to try-

Turn off your wireless interface using hardware switch (a physical switch or a key combination, whatever you have on your Dell to toggle it on/off). Wait about 10-20 seconds, THEN connect the cable to the router. Make sure wired connection is enabled in Network manager and is set to pick up IP automatically (DHCP).

Any difference?

---

### Post by Hadaka on 2013-05-25
Dell= Fn/F2  wireless toggle on/off

---

### Post by GUZZLR on 2013-05-25
Switched it off phically, plugged the cable in and did not change anything.

---

### Post by Hadaka on 2013-05-25
fun stuff... did you run.
```

sudo apt-get purge qemu-kvm
```
and have you done updates/upgrades?
while connected to the internet..
```
sudo apt-get update
sudo apt-get upgrade
```
and have you tried setting  up an ssid with
no encryption..open/none?

---

### Post by varunendra on 2013-05-26
Funny indeed! And interesting, and frustrating, and mysterious.... what a recipe! :P

Let's crosscheck a few things. Please post the outputs of the following -
```
cat /etc/network/interfaces
sudo grep -iRl ethernet /etc/NetworkManager/system-connections/ | while read line; do echo -e "\n\n$line" && sudo cat "$line"; done
```
The second command (sudo grep.....) is a tiny script that has to be typed (or copy-pasted) as a single line in the terminal.

**[COLOR="#FF0000"]CAUTION ! :[/COLOR]** Before posting, make sure the output of the second command does not contain any sensitive data like saved id/passwords for wireless, DSL etc. Although I've made sure such files are not covered, but just to be sure :)

After running on the Dell lappy, also run the same commands on the Chromebook (whether it is connected to the router or not, is not important for these commands). Post back both sets of outputs for comparison.

Hopefully, these may help pin-pointing the source of the problem, or at least simplify the puzzle.

---

### Post by GUZZLR on 2013-05-26
```
charles@Raspberry:~$ sudo apt-get purge qemu-kvm
[sudo] password for charles: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'qemu-kvm' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dkms kde-l10n-engb libkprintutils4 libokularcore2abi1 libqimageblitz4
  linux-headers-generic linux-image-extra-3.8.0-19-generic linux-image-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
charles@Raspberry:~$ sudo apt-get update
Hit http://mirror.anl.gov raring Release.gpg
Hit http://mirror.anl.gov raring-updates Release.gpg
Hit http://mirror.anl.gov raring-backports Release.gpg
Hit http://mirror.anl.gov raring-security Release.gpg
Hit http://mirror.anl.gov raring Release
Hit http://mirror.anl.gov raring-updates Release
Hit http://mirror.anl.gov raring-backports Release
Hit http://mirror.anl.gov raring-security Release
Hit http://mirror.anl.gov raring/main Sources   
Hit http://mirror.anl.gov raring/restricted Sources
Hit http://mirror.anl.gov raring/universe Sources
Hit http://mirror.anl.gov raring/multiverse Sources
Hit http://mirror.anl.gov raring/main i386 Packages
Hit http://mirror.anl.gov raring/restricted i386 Packages
Hit http://mirror.anl.gov raring/universe i386 Packages
Hit http://mirror.anl.gov raring/multiverse i386 Packages
Hit http://mirror.anl.gov raring/main Translation-en
Hit http://mirror.anl.gov raring/multiverse Translation-en
Hit http://mirror.anl.gov raring/restricted Translation-en
Hit http://mirror.anl.gov raring/universe Translation-en
Hit http://mirror.anl.gov raring-updates/main Sources
Hit http://mirror.anl.gov raring-updates/restricted Sources
Hit http://mirror.anl.gov raring-updates/universe Sources
Hit http://mirror.anl.gov raring-updates/multiverse Sources
Hit http://mirror.anl.gov raring-updates/main i386 Packages
Hit http://mirror.anl.gov raring-updates/restricted i386 Packages
Hit http://mirror.anl.gov raring-updates/universe i386 Packages
Hit http://mirror.anl.gov raring-updates/multiverse i386 Packages
Hit http://mirror.anl.gov raring-updates/main Translation-en
Hit http://mirror.anl.gov raring-updates/multiverse Translation-en
Hit http://mirror.anl.gov raring-updates/restricted Translation-en
Hit http://mirror.anl.gov raring-updates/universe Translation-en
Hit http://mirror.anl.gov raring-backports/main Sources
Hit http://mirror.anl.gov raring-backports/restricted Sources
Hit http://mirror.anl.gov raring-backports/universe Sources
Hit http://mirror.anl.gov raring-backports/multiverse Sources
Hit http://mirror.anl.gov raring-backports/main i386 Packages
Hit http://mirror.anl.gov raring-backports/restricted i386 Packages
Hit http://mirror.anl.gov raring-backports/universe i386 Packages
Hit http://mirror.anl.gov raring-backports/multiverse i386 Packages
Hit http://mirror.anl.gov raring-backports/main Translation-en
Hit http://mirror.anl.gov raring-backports/multiverse Translation-en
Hit http://mirror.anl.gov raring-backports/restricted Translation-en
Hit http://mirror.anl.gov raring-backports/universe Translation-en
Hit http://mirror.anl.gov raring-security/main Sources
Hit http://mirror.anl.gov raring-security/restricted Sources
Hit http://mirror.anl.gov raring-security/universe Sources
Hit http://mirror.anl.gov raring-security/multiverse Sources
Hit http://mirror.anl.gov raring-security/main i386 Packages
Hit http://mirror.anl.gov raring-security/restricted i386 Packages
Hit http://mirror.anl.gov raring-security/universe i386 Packages
Hit http://mirror.anl.gov raring-security/multiverse i386 Packages
Hit http://mirror.anl.gov raring-security/main Translation-en
Hit http://mirror.anl.gov raring-security/multiverse Translation-en
Hit http://mirror.anl.gov raring-security/restricted Translation-en
Hit http://mirror.anl.gov raring-security/universe Translation-en
Ign http://mirror.anl.gov raring/main Translation-en_US
Ign http://mirror.anl.gov raring/multiverse Translation-en_US
Ign http://mirror.anl.gov raring/restricted Translation-en_US
Ign http://mirror.anl.gov raring/universe Translation-en_US
Ign http://mirror.anl.gov raring-updates/main Translation-en_US
Ign http://mirror.anl.gov raring-updates/multiverse Translation-en_US
Ign http://mirror.anl.gov raring-updates/restricted Translation-en_US
Ign http://mirror.anl.gov raring-updates/universe Translation-en_US
Ign http://mirror.anl.gov raring-backports/main Translation-en_US
Ign http://mirror.anl.gov raring-backports/multiverse Translation-en_US
Ign http://mirror.anl.gov raring-backports/restricted Translation-en_US
Ign http://mirror.anl.gov raring-backports/universe Translation-en_US
Ign http://mirror.anl.gov raring-security/main Translation-en_US
Ign http://mirror.anl.gov raring-security/multiverse Translation-en_US
Ign http://mirror.anl.gov raring-security/restricted Translation-en_US
Ign http://mirror.anl.gov raring-security/universe Translation-en_US
Reading package lists... Done
charles@Raspberry:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
charles@Raspberry:~$ 


```

AS far as setting up router with a new SSID, not sure how to do that, I have reset both routers and taken away any passwords and firewalls.  Also, the D-Link router offers a Guest area which I have tried, but that didnt work either

---

### Post by GUZZLR on 2013-05-26
I don't know if this will help.  Here are the two lines of code I originally used to get my wireless running, when I originally installed Ubuntu.  These two lines I also used originally to get 12.10 to work, when I went from 12.10 to 13.04, I had to use them again.  However, this was just  to get wireless working, my wired connection has never worked on his machine running either Ubuntu 12.10 or 13.04.  The wired connection did work with Windows XP, just  not Ubuntu.
Now here's the odd part about this, if you look at the attached screen shot, you'sll notice that I have the Broadcom drivers unchecked in "Software & Updates > Additional Drivers"  If I use the drivers, I loose my wireless...so I have to go back and check the "do not use the device".  So this is odd to me because wireless does not work unless I use the two lines of code to get the drivers, but then I have to not use them to get wireless to work...seems backwards to me.
```
   sudo apt-get purge b43-fwcutter firmware-b43-installer firmware-b43-lpphy-installer firmware-b43legacy-installer bcmwl*
 sudo apt-get install b43-fwcutter firmware-b43-installer bcmwl*


```

[ATTACH=CONFIG]243070[/ATTACH]

---

### Post by GUZZLR on 2013-05-26
[SIZE=3]
Here's what I get:[/SIZE]

```
   [COLOR=#ff0000]Input using Dell [/COLOR][COLOR=#ff0000]on wireless:[/COLOR]
 [COLOR=#000000]charles@Raspberry:~$ cat /etc/network/interfaces [/COLOR] 
 [COLOR=#000000]# interfaces(5) file used by ifup(8) and ifdown(8) [/COLOR] 
 [COLOR=#000000]auto lo [/COLOR] 
 [COLOR=#000000]iface lo inet loopback [/COLOR] 
 [COLOR=#000000]charles@Raspberry:~$ sudo grep -iRl ethernet /etc/NetworkManager/system-connections/ | while read line; do echo -e "\n\n$line" && sudo cat "$line"; done [/COLOR] 
 [COLOR=#000000][sudo] password for charles: [/COLOR] 
 

 

 [COLOR=#000000]/etc/NetworkManager/system-connections/Auto Ethernet [/COLOR] 
 [COLOR=#000000][802-3-ethernet] [/COLOR] 
 [COLOR=#000000]duplex=full [/COLOR] 
 [COLOR=#000000]mac-address=00:1C:23:38:FC:08 [/COLOR] 
 

 [COLOR=#000000][connection] [/COLOR] 
 [COLOR=#000000]id=Auto Ethernet [/COLOR] 
 [COLOR=#000000]uuid=56b84ee9-a71c-45d8-b94a-e5197612fa09 [/COLOR] 
 [COLOR=#000000]type=802-3-ethernet [/COLOR] 
 [COLOR=#000000]timestamp=1369526519 [/COLOR] 
 

 [COLOR=#000000][ipv6] [/COLOR] 
 [COLOR=#000000]method=ignore [/COLOR] 
 

 [COLOR=#000000][ipv4] [/COLOR] 
 [COLOR=#000000]method=auto [/COLOR] 
 [COLOR=#000000]charles@Raspberry:~$ [/COLOR] 
 

 [COLOR=#ff0000]Input using Chromebook on wireless:[/COLOR]
 [COLOR=#000000]user@ChrUbuntu:~$ cat /etc/network/interfaces [/COLOR]
 [COLOR=#000000]auto lo [/COLOR]
 [COLOR=#000000]iface lo inet loopback [/COLOR]
 
 [COLOR=#000000]user@ChrUbuntu:~$ sudo grep -iRl ethernet /etc/NetworkManager/system-connections/ | while read line; do echo -e "\n\n$line" && sudo cat "$line"; done [/COLOR]
 [COLOR=#000000][sudo] password for user:  [/COLOR]
 [COLOR=#000000]user@ChrUbuntu:~$  [/COLOR]


```

---

### Post by Hadaka on 2013-05-26
The wireless driver you have loaded is basically correct..b43
The bcm 4311 card uses the ssb module and b43 driver.
the Sta Broadcom-kernel-source driver "wl" ,blackists the ssb
module by default and design. Why the sta driver always shows
up in proprietary drivers is beyond me, it is a constant source of
trouble. what you have check is correct. The 4311 card really runs
best on the linux-firmware-nonfree dirver. But, since you have no
wired connection,you cannot load it at this time.

---

### Post by Hadaka on 2013-05-26
Hi, I noticed in the output from the last command
varunendra had you try there was no IPv4 listed.
please click your wireless icon..
click Edit connections..
click Wired
click your ssid name
click Edit
click IPv4 settings
and post a screen shot of that..
thanks.

---

### Post by GUZZLR on 2013-05-26
using the Dell or the Chromebook?
Thanks

---

### Post by GUZZLR on 2013-05-26
This is from the Chromebook:

[ATTACH=CONFIG]243080[/ATTACH]

---

### Post by Hadaka on 2013-05-26
The Dell

---

### Post by GUZZLR on 2013-05-26
This is from the Dell...Thanks
[ATTACH=CONFIG]243082[/ATTACH]

---

### Post by Hadaka on 2013-05-26
ok, thats the wireless side, I wanted to see
the wired side...this one..

[COLOR=#000000]Auto Ethernet

which should not have the space in the name.
just use a single ssid setting...call it wired
or some other simple name...at least while testing.
please post of screen shot of the IPv4 setting
for the wired side.
thanks.
[/COLOR]

---

### Post by varunendra on 2013-05-26
> **GUZZLR said:**
> [SIZE=3]
Here's what I get:[/SIZE]

```
   [COLOR=#ff0000]Input using Dell [/COLOR][COLOR=#ff0000]on wireless:[/COLOR]
....
 [COLOR=#000000]charles@Raspberry:~$ sudo grep -iRl ethernet /etc/NetworkManager/system-connections/ | while read line; do echo -e "\n\n$line" && sudo cat "$line"; done [/COLOR] 
 [sudo] password for charles: 

 /etc/NetworkManager/system-connections/Auto Ethernet  
 [802-3-ethernet]  
 duplex=full  
**[COLOR="#FF0000"] mac-address=00:1C:23:38:FC:08 [/COLOR]**
....
....

```

Aha.... what do we have here..

Edit your "Auto Ethernet" connection, and make sure the "**Device MAC address :**" field is empty (delete whatever there is in it). Save > close.

Retry and give us some good news.

---

### Post by Hadaka on 2013-05-26
also..this is not correct

```

 sudo apt-get install b43-fwcutter firmware-b43-installer bcmwl*
those are 2 totally different drivers...im surprised the wireless is working.

```
it should only be..
```

 sudo apt-get install b43-fwcutter firmware-b43-installer
```
please do
```
sudo apt-get purge bcmwl*
```
then..
```
sudo apt-get autoremove
```
thanks.

---

### Post by GUZZLR on 2013-05-26
Did it, powered down and still have the issue.  It always tells me the cable is unplugged, going directly to the modem, the unplugged cable warning goes away and the computer connects

[ATTACH=CONFIG]243094[/ATTACH][ATTACH=CONFIG]243093[/ATTACH]

---

### Post by GUZZLR on 2013-05-26
OK, tried this, I'll reboot and see if anything different happens and report back

```
charles@Raspberry:~$ sudo apt-get purge bcmwl*
[sudo] password for charles: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'bcmwl-kernel-source' for regex 'bcmwl*'
Note, selecting 'bcmwl-modaliases' for regex 'bcmwl*'
Package 'bcmwl-modaliases' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dkms kde-l10n-engb libkprintutils4 libokularcore2abi1 libqimageblitz4
  linux-headers-generic linux-image-extra-3.8.0-19-generic linux-image-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 272565 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-22-generic
charles@Raspberry:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dkms kde-l10n-engb libkprintutils4 libokularcore2abi1 libqimageblitz4
  linux-headers-generic linux-image-extra-3.8.0-19-generic linux-image-generic
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
After this operation, 108 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 272565 files and directories currently installed.)
Removing dkms ...
Removing kde-l10n-engb ...
Removing libkprintutils4 ...
Removing libokularcore2abi1 ...
Removing libqimageblitz4 ...
Removing linux-headers-generic ...
Removing linux-image-extra-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found initrd image: /boot/initrd.img-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found initrd image: /boot/initrd.img-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
done
Removing linux-image-generic ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


```

No change, This is a screen shot of the Dell wired directly to the modem...wireless is still working, wired to router is not, only works directly to modem. 
[ATTACH=CONFIG]243097[/ATTACH]

---

### Post by Hadaka on 2013-05-26
ok, PLEASE show  the **IPv4** setting screenshot of the AUTO ETHERNET
the one you just blanked out for varunendra.
Thanks.

---

### Post by GUZZLR on 2013-05-26
Oh yea...forgot about that

---

### Post by GUZZLR on 2013-05-26
This is wired directly to the modem, using the Dell...Thanks

[ATTACH=CONFIG]243098[/ATTACH][ATTACH=CONFIG]243100[/ATTACH][ATTACH=CONFIG]243101[/ATTACH][ATTACH=CONFIG]243102[/ATTACH][ATTACH=CONFIG]243099[/ATTACH][ATTACH=CONFIG]243103[/ATTACH]

I forgot you wanted a single line created...these are a single line ssid hooked directly to the modem using the Dell

---

### Post by Hadaka on 2013-05-26
ok, everything now looks like it should, so give this a try.
click network mgr. uncheck "enable wireless"...boot with
the ethernet cable attached. * if, it still does not connect
to the router, i would suggest,removing the keyboard again
takeing it to a computer repair place and have them remove
and replace your cmos battery since you were unable to remove
it. you have proven all hardware good, all cables, modem,router,
the ethernet card works when it gets a direct injection of data from
the modem. But, when the card alone to the router it never sends a
"here i am" signal" which is why i suspect a bios issue. I am really
surprised when you cleard out that one field that varunendra requested
that it didnt spring to life. so the battery/bios reset is my final suggestion.
good luck.

---

### Post by GUZZLR on 2013-05-26
Thanks so much for the help Hadaka.  I'll report back

---

### Post by GUZZLR on 2013-05-26
So I've noticed some new developments which were not happening before.  The screen shot with the warning is new, I used to be able to just hit options and it would take me directly to where I can edit wire or wireless.  Also, while in network manager, when I turn off wireless, with the cable attached, the wired "cable unplugged" goes away and the Computer actually tries to connect, but then it dies and goes back to "cable unplugged".  It is trying to connect to the wired router momentarily before it stops. 
[ATTACH=CONFIG]243104[/ATTACH]

---

### Post by Hadaka on 2013-05-26
This may be a good thing, please do the command varunendra sent 
again, i did notice you didnt have the uuid before..yet it shows on mine,
but, im runnng 12.04. so please do..
```
sudo grep -iRl ethernet /etc/NetworkManager/system-connections/ | while read line; do echo -e "\n\n$line" && sudo cat "$line"; done
 
```
this time..before you do the command. uncheck wireless, then shutdown,power down
then..power down the router.
power back up the router, then the computer..
then do the above command.
thanks.

---

### Post by GUZZLR on 2013-05-26
> **Hadaka said:**
> 
this time..before you do the command. uncheck wireless, then shutdown,power down
then..power down the router.
power back up the router, then the computer..
then do the above command.
thanks.

When I power the router and computer back on, the wireless should still be unchecked...correct?

---

### Post by Hadaka on 2013-05-26
It "should" and yes..leave it unchecked when you power back up.
if it fails to connect wired..then of course re-enable it.

---

### Post by GUZZLR on 2013-05-26
Getting Closer!  What it is doing now has never happened.  Before, it would try and connect and immediately close down.  Now, it is trying to connect and stays trying, instead of immediately closing down, and going back to "cable unplugged".  Now, it tries and tries to connect, does not connect, turns the switch to off, and then turns the wired switch back to on, and continues to try and connect...I've never seen it do that.  But still can not connect.

[ATTACH=CONFIG]243105[/ATTACH]

---

### Post by Hadaka on 2013-05-26
indeed !..so now..you need to match the settings in the router to
the settings of networkmgr, you might also consider hooking up the
old dlink router as the newer one is N speed, and your internal ethernet
most likely is not....however..the n speed router will adjust for that.
so,,,,match the settings ...security ssid..in network mgr to the router...
first n router,..if it fails...try the d-link and set its security options.
it is indeed getting close.
post back.

Edit : last you posted settings you had the ssid = EthernetTest
        so set the router ssid to that as well..

---

### Post by GUZZLR on 2013-05-26
> **Hadaka said:**
> 
Edit : last you posted settings you had the ssid = EthernetTest
        so set the router ssid to that as well..

Yep, found that out, and corrected, but still can't connect...it is trying though.

---

### Post by GUZZLR on 2013-05-26
> **Hadaka said:**
> indeed !..so now..you need to match the settings in the router to
the settings of networkmgr, you might also consider hooking up the
old dlink router as the newer one is N speed

Actually, the D-Link is N-Draft too, but I'll mess with it too.

---

### Post by Hadaka on 2013-05-26
I trust you are still able to use the wireless side.
also..i noticed the wireless "connnection name is Saluki
just set the connection name to the wired side to that as 
well...as the names should match anyway...as far as the
N part, i had wireless on the brain..so ignore that.
so set the connection name the same for both wired and wireless
you might also try disableing wireless again and doing the power
cycle routine as all the messing about...things may be a bit confused
and the power cycle gives them a chance to reset to whatever changes
you have made...your close.

---

### Post by varunendra on 2013-05-26
I thought you guys will be having party and I came here to take my share of candies. But I see we still have no candies to share :(

I am thinking about disabling Network Manager and trying the old-school method (trying dhcp first). But for now, keep going with the leads. Meanwhile -
> **GUZZLR said:**
> Now, it tries and tries to connect, does not connect, turns the switch to off, and then turns the wired switch back to on, and continues to try and connect...
..while it is doing so, take a look at -
```
dmesg | tail -40
cat /var/log/syslog | tail -40
```
Any messages regarding ethernet (eth0), DHCP, tg3, net, NetworkManager, etc. ? If anything looks suspicious or relevant, post back here. In fact keep these two commands handy. Everytime there is a state change, they *should* contain relevant log messages.

---

### Post by GUZZLR on 2013-05-27
```
sudo grep -iRl ethernet /etc/NetworkManager/system-connections/ | while read line; do echo -e "\n\n$line" && sudo cat "$line"; done
 
```

So everytime I mess with the wired name, I must reinsert this code, or I get absoulutely nothing.  I'm wondering if there is a purge command I should be entering first, to clean stuff up?  Also, I noticed the word ethernet is lower case, but my ID name is uppercase: Ethernet. Will that mess things up?
Also, when I run this line of code, do I need to be connected to the internet?

Thanks

---

### Post by Hadaka on 2013-05-27
Hi, that line of code has noting to dowith makeing an attempt to connect,
it is simply saying "give me information about the ethernet card in relation
to network mgr. settings". the reason "ethernet" is in lower case...is because
that is its proper name. You chose to call it Ethernet as a connection name.
sooo..question is..does it still connect wireless?...if yes...simply set the ethernet
end...wired..with the same settings as the wireless. this way it uses, as it should
the same "connection name"..same security settings. its suppose to do that.
connection name wireless= saluki  router ssid=saluki wired=saluki
wireless security=none  router security=none wired security=none <- or whatever value you currently can connect on using wireless.
once you have all the settings the same..and have SAVED those setttings...power cycle once again the router and the computer.

any questions..post back.

---

### Post by varunendra on 2013-05-27
**[COLOR="#FF0000"]NOTE : No - help post![/COLOR] Only for educational purpose, nothing to do with troubleshooting.**

> **GUZZLR said:**
> ```
sudo grep -iRl ethernet /etc/NetworkManager/system-connections/ | while read line; do echo -e "\n\n$line" && sudo cat "$line"; done
 
```....Also, I noticed the word ethernet is lower case, but my ID name is uppercase: Ethernet. Will that mess things up?.....

I love explaining things, where I can :P

**grep = g/re/p = Global Regular-Expression Print :** It searches for a given pattern (or regular expression), and prints it as per given instructions.

Anything after a command that is prefixed (without spaces) with a hyphen, is a parameter or option to it. Here, **-iRl** means -
-i = Ignore the case (so "ethernet" will be treated the same as "Ethernet")
-R = Do a recursive search. Tells grep to search 'all' files within the given location, including its subdirectories.
-l = Tells grep to print 'only' the name of the file(s) in which the given pattern is found, instead of the lines themselves in which the match is found (which is its normal behaviour)

ethernet = the pattern that we want to search. Without the '-i' option, grep would not include "Ethernet", but with '-i' (ignore case), it would not care for the cases and will cover it too.

So, **grep -iRl ethernet /etc/NetworkManager/system-connections/** means - look for the pattern "ethernet" (ignoring the case) in all the files located within /etc/NetworkManager/system-conncetions/ directory (including subdirectories if there are any), and report back 'only' their names. The result is a list of file names that have this word - "ethernet" (or Ethernet or any variation of letter-cases) in their contents. Each line in this list will contain exactly one file name. Next part, the 'pipe symbol (|) -

**| (the pipe symbol)** = It converts the output of the command on its left hand side into the 'input' for the command on its right hand side. So here the list of filenames becomes the input for the following 'script' (the combination of commands to get a particular result).

**while read line; do....; done** = tells the command interpreter (the terminal in our case) to '**read**' an input, and store it in a variable that we prefer to call - '**line**'. Then it will '**do**' something until 'done' is met. Goes back to doing the same thing again '**while**' there is an input to read (each line in the input list is counted as one input. It will repeat the 'do' things as many times as there are lines in the input list).

**echo -e "\n\n$line"** = echoes (prints) the value of variable '**line**' that we just read above ($ sing means the word is a variable, and its value has to be considered instead of the word itself). The parameter '**-e**' just enables interpretation of regular expressions, which is the term '**\n**' (new line) here. So now it also prints two empty new lines (\n\n) before printing the variable $line. It did it to create gap between printed file contents, to make it easy to read :).

**&&** = '**And** also do'. By adding this, we can just tell the terminal to also do the command following it. We could do it separately, it's just how I preferred :)

**sudo cat "$line"** = '**cat**' concatenates (or just reads and prints, if there is just a single file to read) the contents of the input files. '**$line**' is a variable- '**line**' - which, during execution, will be replaced by the input that has been read and stored in it (which was a file-name returned by 'grep'). So if, for example, the list of filenames contained the file-name "Auto Ethernet" which has just been read and stored in this variable, then '**cat "$line"**' will be read as '**cat "Auto Ethernet**" by the terminal. The prefix 'sudo' is there to run the command with root privileges (normal user does not have permission to read those files). So **'sudo cat <some file>'** will just print the whole content of the file - <some file>.

Of course you could simply navigate to the directory > open the files with root privileges, and post their contents here. It is just a quicker way to do that, and it is easier to post a line of command than to post a whole bunch of sentences explaining what you have to do. Plus, the command way makes sure nothing is missed that is covered by the given criteria.

Obviously, a no-help post, but it is always a good idea to understand what a piece of code is going to do with your computer before running it. :)

---

### Post by GUZZLR on 2013-05-27
Geeze...

---

### Post by Hadaka on 2013-05-27
ok..:D...lets take a look where we are...does the wireless
still connect and work on the dell??

---

### Post by GUZZLR on 2013-05-27
I'm going backwards now...wireless still works, but when I run this code, It is showing no entry/directory exist.  I delete and create new ones, then powerdown everything, but still not showing any directory exist...Can I throw it out the window now?

```
sudo grep -iRl ethernet /etc/NetworkManager/system-connections/ | while read line; do echo -e "\n\n$line" && sudo cat "$line"; done
```

---

### Post by Hadaka on 2013-05-27
It would probably just bounce,seems to be a tough machine:P
ok..do this..post #82..screen shots..show me the screen shots(just an example)
for wireless..connected to the router
and WIRED connected to the router....not modem...router
i need to see how everything is set.
take your time..we will fix this.
thanks.

---

### Post by GUZZLR on 2013-05-27
It's working!  Sort of.  I now have control of the on/off switch for wired connection...I can turn wired off and on, and it "sticks".  It will connect with my two browsers: Firefox and Chrome, and it connects very quickly.  However, it will not pull in a web site, except once.  I actually saw it hook up to Amazon, but it took a very very long time.  On the back of the computer, where the cable attaches, I do see the normal two lights working now, one solid, and the other flashing for data transfer.  I think we are really close, it did connect to Amazon, and it always connects to the browsers, even when I power down to clear cash.  
I'll send the screen shots tomorrow, I have a dinner date I need to get to.  Lets let it rest for awhile.
Again, thanks for all the help.

---

### Post by GUZZLR on 2013-05-27
```
charles@Raspberry:~$ dmesg | tail -40
[  139.237103] tg3 0000:09:00.0 eth0: Flow control is on for TX and on for RX
[  139.237143] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  142.312256] tg3 0000:09:00.0 eth0: Link is down
[  154.466175] dell_wmi: Unknown key e044 pressed
[  155.204290] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  156.496332] dell_wmi: Unknown key e043 pressed
[  167.464162] dell_wmi: Unknown key e044 pressed
[  192.681145] dell_wmi: Unknown key e043 pressed
[  192.860254] tg3 0000:09:00.0 eth0: Link is up at 100 Mbps, full duplex
[  192.860267] tg3 0000:09:00.0 eth0: Flow control is on for TX and on for RX
[  192.860307] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  312.328262] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  312.413018] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  338.370156] wlan0: authenticate with 14:35:8b:0a:d0:b4
[  338.392287] wlan0: send auth to 14:35:8b:0a:d0:b4 (try 1/3)
[  338.405074] wlan0: authenticated
[  338.408071] wlan0: associate with 14:35:8b:0a:d0:b4 (try 1/3)
[  338.411404] wlan0: RX AssocResp from 14:35:8b:0a:d0:b4 (capab=0x411 status=0 aid=1)
[  338.411837] wlan0: associated
[  338.411870] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1028.363794] composite sync not supported
[ 9706.867672] wlan0: deauthenticating from 14:35:8b:0a:d0:b4 by local choice (reason=3)
[ 9706.885569] cfg80211: Calling CRDA to update world regulatory domain
[ 9706.898270] cfg80211: World regulatory domain updated:
[ 9706.898275] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 9706.898279] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 9706.898281] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 9706.898284] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 9706.898286] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 9706.898288] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 9915.624138] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 9915.724870] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9941.446754] wlan0: authenticate with 14:35:8b:0a:d0:b4
[ 9941.464282] wlan0: send auth to 14:35:8b:0a:d0:b4 (try 1/3)
[ 9941.465906] wlan0: authenticated
[ 9941.468202] wlan0: associate with 14:35:8b:0a:d0:b4 (try 1/3)
[ 9941.470496] wlan0: RX AssocResp from 14:35:8b:0a:d0:b4 (capab=0x411 status=0 aid=1)
[ 9941.470938] wlan0: associated
[ 9941.470970] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10849.826010] systemd-hostnamed[3752]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
charles@Raspberry:~$ cat /var/log/syslog | tail -40
May 27 20:09:37 Raspberry dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 27 20:09:37 Raspberry dhclient: 
May 27 20:09:37 Raspberry NetworkManager[1055]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May 27 20:09:37 Raspberry dhclient: Listening on LPF/eth0/00:1c:23:38:fc:08
May 27 20:09:37 Raspberry dhclient: Sending on   LPF/eth0/00:1c:23:38:fc:08
May 27 20:09:37 Raspberry dhclient: Sending on   Socket/fallback
May 27 20:09:37 Raspberry dhclient: DHCPREQUEST of 192.168.8.102 on eth0 to 255.255.255.255 port 67 (xid=0x45bba566)
May 27 20:09:38 Raspberry avahi-daemon[1028]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::21c:23ff:fe38:fc08.
May 27 20:09:38 Raspberry avahi-daemon[1028]: New relevant interface eth0.IPv6 for mDNS.
May 27 20:09:38 Raspberry avahi-daemon[1028]: Registering new address record for fe80::21c:23ff:fe38:fc08 on eth0.*.
May 27 20:09:40 Raspberry dhclient: DHCPREQUEST of 192.168.8.102 on eth0 to 255.255.255.255 port 67 (xid=0x45bba566)
May 27 20:09:40 Raspberry dhclient: DHCPACK of 192.168.8.102 from 192.168.8.1
May 27 20:09:40 Raspberry dhclient: bound to 192.168.8.102 -- renewal in 34561 seconds.
May 27 20:09:40 Raspberry NetworkManager[1055]: <info> (eth0): DHCPv4 state changed preinit -> reboot
May 27 20:09:40 Raspberry NetworkManager[1055]: <info>   address 192.168.8.102
May 27 20:09:40 Raspberry NetworkManager[1055]: <info>   prefix 24 (255.255.255.0)
May 27 20:09:40 Raspberry NetworkManager[1055]: <info>   gateway 192.168.8.1
May 27 20:09:40 Raspberry NetworkManager[1055]: <info>   nameserver '198.88.216.2'
May 27 20:09:40 Raspberry NetworkManager[1055]: <info>   nameserver '198.88.216.3'
May 27 20:09:40 Raspberry NetworkManager[1055]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 27 20:09:40 Raspberry NetworkManager[1055]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
May 27 20:09:40 Raspberry avahi-daemon[1028]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.8.102.
May 27 20:09:40 Raspberry avahi-daemon[1028]: New relevant interface eth0.IPv4 for mDNS.
May 27 20:09:40 Raspberry avahi-daemon[1028]: Registering new address record for 192.168.8.102 on eth0.IPv4.
May 27 20:09:41 Raspberry NetworkManager[1055]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
May 27 20:09:41 Raspberry NetworkManager[1055]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
May 27 20:09:41 Raspberry NetworkManager[1055]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May 27 20:09:41 Raspberry NetworkManager[1055]: <info> Policy set 'Ethernet connection 1' (eth0) as default for IPv4 routing and DNS.
May 27 20:09:41 Raspberry NetworkManager[1055]: <info> Writing DNS information to /sbin/resolvconf
May 27 20:09:41 Raspberry dnsmasq[2288]: setting upstream servers from DBus
May 27 20:09:41 Raspberry dnsmasq[2288]: using nameserver 198.88.216.3#53
May 27 20:09:41 Raspberry dnsmasq[2288]: using nameserver 198.88.216.2#53
May 27 20:09:41 Raspberry dnsmasq[2288]: using nameserver 198.88.216.2#53
May 27 20:09:41 Raspberry dnsmasq[2288]: using nameserver 198.88.216.3#53
May 27 20:09:41 Raspberry NetworkManager[1055]: <info> Activation (eth0) successful, device activated.
May 27 20:09:41 Raspberry dbus[971]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 27 20:09:41 Raspberry dbus[971]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 27 20:09:44 Raspberry nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' took too long; killing it.
May 27 20:09:44 Raspberry NetworkManager[1055]: <warn> Dispatcher script timed out: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' timed out.
May 27 20:10:06 Raspberry NetworkManager[1055]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
charles@Raspberry:~$ 


```

I have no clue what on Earth I'm looking at here...sure seems to be a lot of errors and dumps and things of that nature. Thanks

---

### Post by Hadaka on 2013-05-27
I would still like to see the screen shots of the network mgr cofiguration for both wired and wireless 
after you post that. then uncheck "connect automatically" for the WIRELESS
check "connect automatically" for the wired..
boot ,,,,,,,,
then do..
```
dmesg | tail -40
```
thanks

---

### Post by Hadaka on 2013-05-28
This is what your WIRED network mgr. settings should look like.

Wired --connect automatically checked   available to others checked
Security...as shown
Ipv4 -- DHCP Automatic
IPv6 -- Ignore
*see attached...

---

### Post by GUZZLR on 2013-05-28
> **Hadaka said:**
> I would still like to see the screen shots of the network mgr cofiguration for both wired and wireless 


I guess there's a size limit,  I'll need to think of something else

---

### Post by Hadaka on 2013-05-28
ok, just make your WIRED connection  look like the ones i just posted...
then,,,uncheck "enable WIRELESS" click save ... boot and see that it 
connects.
thanks.

---

### Post by GUZZLR on 2013-05-28
This is wired:[ATTACH=CONFIG]243182[/ATTACH][ATTACH=CONFIG]243183[/ATTACH][ATTACH=CONFIG]243184[/ATTACH][ATTACH=CONFIG]243185[/ATTACH][ATTACH=CONFIG]243186[/ATTACH][ATTACH=CONFIG]243187[/ATTACH][ATTACH=CONFIG]243188[/ATTACH]


Wireless
[ATTACH=CONFIG]243190[/ATTACH][ATTACH=CONFIG]243191[/ATTACH][ATTACH=CONFIG]243192[/ATTACH][ATTACH=CONFIG]243193[/ATTACH][ATTACH=CONFIG]243194[/ATTACH]

---

### Post by Hadaka on 2013-05-28
the wired screen shots did not come through...didnt attach.
the wireless is fine...i would suggest on the wireless to set
your IPv6 to Ignore....other than that...its fine..
please resend the wired screen shots
thanks.

---

### Post by GUZZLR on 2013-05-28
This is wired:

[ATTACH=CONFIG]243197[/ATTACH][ATTACH=CONFIG]243196[/ATTACH][ATTACH=CONFIG]243198[/ATTACH][ATTACH=CONFIG]243199[/ATTACH][ATTACH=CONFIG]243200[/ATTACH]

I'm wondering if for some reason not inputting the MAC address is messing with it.  Everytime I click on the tab where that is, there is always a flashing cursur there as if it is telling me to input a number. Also, on the wired, I'm using the default name it gives me.  I'm having a lot more success with it that way

---

### Post by GUZZLR on 2013-05-28
> **Hadaka said:**
> I would still like to see the screen shots of the network mgr cofiguration for both wired and wireless 
after you post that. then uncheck "connect automatically" for the WIRELESS
check "connect automatically" for the wired..
boot ,,,,,,,,
then do..
```
dmesg | tail -40
```
thanks

```
charles@Raspberry:~$ dmesg | tail -40
[  533.024253] wlan0: send auth to 14:35:8b:0a:d0:b4 (try 1/3)
[  533.027684] wlan0: authenticated
[  533.028157] wlan0: associate with 14:35:8b:0a:d0:b4 (try 1/3)
[  533.043454] wlan0: RX AssocResp from 14:35:8b:0a:d0:b4 (capab=0x411 status=0 aid=1)
[  533.043905] wlan0: associated
[  533.043917] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  536.504873] dell_wmi: Unknown key e043 pressed
[  544.505785] dell_wmi: Unknown key e044 pressed
[  551.479508] dell_wmi: Unknown key e043 pressed
[  567.223445] dell_wmi: Unknown key e044 pressed
[  569.289363] dell_wmi: Unknown key e043 pressed
[  570.181421] wlan0: deauthenticating from 14:35:8b:0a:d0:b4 by local choice (reason=3)
[  570.186646] cfg80211: Calling CRDA to update world regulatory domain
[  570.194569] cfg80211: World regulatory domain updated:
[  570.194574] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  570.194577] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  570.194580] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  570.194582] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  570.194585] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  570.194587] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  576.267546] dell_wmi: Unknown key e044 pressed
[  580.804279] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  580.904983] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  580.924269] tg3 0000:09:00.0: irq 45 for MSI/MSI-X
[  580.959482] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  583.441070] wlan0: authenticate with 14:35:8b:0a:d0:b4
[  583.460303] wlan0: send auth to 14:35:8b:0a:d0:b4 (try 1/3)
[  583.467502] wlan0: authenticated
[  583.468064] wlan0: associate with 14:35:8b:0a:d0:b4 (try 1/3)
[  583.470354] wlan0: RX AssocResp from 14:35:8b:0a:d0:b4 (capab=0x411 status=0 aid=1)
[  583.470817] wlan0: associated
[  583.470843] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  583.837337] dell_wmi: Unknown key e043 pressed
[  586.135019] tg3 0000:09:00.0 eth0: Link is up at 100 Mbps, full duplex
[  586.135031] tg3 0000:09:00.0 eth0: Flow control is on for TX and on for RX
[  586.135066] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  726.630946] systemd-hostnamed[3955]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 1139.821243] systemd-hostnamed[4210]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 2894.804180] systemd-hostnamed[4659]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 3296.135036] systemd-hostnamed[4815]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!


```

---

### Post by GUZZLR on 2013-05-28
Forget about the last dmesg | tail -40, I forgot to reboot.  This one is with wireless set to not connect automatically and rebooting.  What is nss my host name?

```
charles@Raspberry:~$ dmesg | tail -40
[   21.264866] type=1400 audit(1369786621.758:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1062 comm="apparmor_parser"
[   21.265476] type=1400 audit(1369786621.758:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1062 comm="apparmor_parser"
[   23.188081] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   23.268974] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.269314] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.373706] tg3 0000:09:00.0: irq 45 for MSI/MSI-X
[   23.408892] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.409448] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.447575] type=1400 audit(1369786624.938:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1162 comm="apparmor_parser"
[   24.447602] type=1400 audit(1369786624.938:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1163 comm="apparmor_parser"
[   24.447973] type=1400 audit(1369786624.938:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1162 comm="apparmor_parser"
[   24.448030] type=1400 audit(1369786624.938:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1163 comm="apparmor_parser"
[   24.451967] type=1400 audit(1369786624.942:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1164 comm="apparmor_parser"
[   24.452402] type=1400 audit(1369786624.946:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1164 comm="apparmor_parser"
[   24.454969] type=1400 audit(1369786624.946:16): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1165 comm="apparmor_parser"
[   24.455502] type=1400 audit(1369786624.946:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1165 comm="apparmor_parser"
[   25.555168] composite sync not supported
[   25.897223] composite sync not supported
[   28.613898] composite sync not supported
[   30.097920] composite sync not supported
[   31.152786] composite sync not supported
[   32.064624] composite sync not supported
[   35.796114] composite sync not supported
[   51.232866] composite sync not supported
[   77.079987] dell_wmi: Unknown key e043 pressed
[   82.950198] dell_wmi: Unknown key e044 pressed
[   83.466802] dell_wmi: Unknown key e043 pressed
[   91.125269] dell_wmi: Unknown key e044 pressed
[   99.032788] dell_wmi: Unknown key e043 pressed
[  101.854254] dell_wmi: Unknown key e044 pressed
[  101.945918] systemd-hostnamed[2370]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  106.956874] dell_wmi: Unknown key e043 pressed
[  116.657005] dell_wmi: Unknown key e044 pressed
[  117.173760] dell_wmi: Unknown key e043 pressed
[  121.757061] dell_wmi: Unknown key e044 pressed
[  125.591515] dell_wmi: Unknown key e043 pressed
[  131.464260] dell_wmi: Unknown key e044 pressed
[  141.678001] dell_wmi: Unknown key e043 pressed
[  151.379702] dell_wmi: Unknown key e044 pressed
[  158.030121] dell_wmi: Unknown key e043 pressed


```

---

### Post by Hadaka on 2013-05-28
probably the name you chose...Ethernet connection
change it back to 
Wired connection 1
see it that helps
also please do..
```
echo "blacklist dell_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by GUZZLR on 2013-05-28
```
charles@Raspberry:~$ 
charles@Raspberry:~$ echo "blacklist dell_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for charles: 
blacklist dell_wmi
charles@Raspberry:~$ 


```

Still the same, it says it's connected, I can get my browsers, but nothing more.  There are two lights at the connector, 1 is a flashing yellow light, and the other is a steady orange light. When I can connect with wire (directly to the modem) the two lights are: yellow flashing, and steady green.  So the steady orange is obvioulsly a fault code of somekind?
I also tried the backup router just to make sure...no difference.

---

### Post by GUZZLR on 2013-05-28
I'm going to call it a day with this thing...If you don't hear from me, it's because I though it out the window...

---

### Post by varunendra on 2013-05-28
> **GUZZLR said:**
> There are two lights at the connector, 1 is a flashing yellow light, and the other is a steady orange light. When I can connect with wire (directly to the modem) the two lights are: yellow flashing, and steady green.  So the steady orange is obvioulsly a fault code of somekind?
No, orange or green are just indications of the 'negotiated speed' at which the connection has been established. One shows it is 10Mbps, the other 100Mbps.

> **GUZZLR said:**
> I'm going to call it a day with this thing...If you don't hear from me, it's because I though it out the window...
Doing a fresh re-install of the LTS (that is 12.04) does look like a more sensible option at this stage. :)

Your recent posts show some additional problems (like that nss-myhostname error, which although does affect networking, is a result of something entirely different we haven't addressed yet). 13.04 isn't worth the efforts we have already gone through since it will only be supported for 9 months, which ends in January next year. After that, you'll have to do a fresh install of the next release (or the LTS) anyway unless you don't want updates. 12.04, on the other hand, is much more stable in terms of performance, and will be supported till April 2017.

If you concur with me and go for 12.04, I'd suggest to download via torrent to ensure integrity of the downloaded ISO (plus it downloads faster) : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads) ([64 bit]("http://releases.ubuntu.com/12.04/ubuntu-12.04.2-desktop-amd64.iso.torrent") is recommended)

---

### Post by GUZZLR on 2013-05-29
If I load 12.04, will it overwright 13.04 automatically?  I am leaning towards this just to see if 13.10 is the problem.  And, I have downloaded 12.04 32bit (because this is a 32 bit machine) how can I verify the integrity of the burned .iso disk before I install?
Thanks

---

### Post by varunendra on 2013-05-29
> **GUZZLR said:**
> how can I verify the integrity of the burned .iso disk before I install?
Thanks

While the system is booting from the cd (the purple screen with accessibility and keyboard option at the bottom), press any key to bring up "Advanced Boot menu". There you'll get an option to "Check disc for defects". Run it and see if it returns any errors.

Here's the detailed info about Advanced Boot Menu : [https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)


As an additional measure (and to check the source ISO you have downloaded) : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


**PS:**
It would be a good idea to keep the cable plugged in while you are booting or installing.
Also, your wireless card (BCM4311) will need proprietary firmware on all versions of Ubuntu. Easiest way to install it is to download the "linux-firmware-nonfree" package from [here]("http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download") and double-click to install.
*(Thanks to Hadaka for reminding me these)*

---

### Post by GUZZLR on 2013-05-30
what exactly does the Linux non-free firware do?  and do I have to install the aptitude or synoptic package?  Is the Synoptic program similar to Add/Remove in Windows Control Panel?

---

### Post by varunendra on 2013-05-30
> **GUZZLR said:**
> what exactly does the Linux non-free firware do?  and do I have to install the aptitude or synoptic package?
It is a collection of non-free firmwares that are required by certain devices to work. They are free to download for personal use, but can not be distributed along with the Ubuntu CD due to licencing issues.

All this package does is to just copy the included firmware files to their correct location (/lib/firmware, or a subdirectory in it) automatically. It does not need any specific package manager like synaptic or aptitude. Any one that is already present in the system (dpkg, USC, synaptic, aptitude,.... whatever) will automatically open and install it when double-clicked.

It is a standalone package that does not have any dependencies, so you don't need to worry about that. Just think of it like a zip file, that contains a bunch of files that need to be simply copied to a specific location.

```
Is the Synoptic program similar to Add/Remove in Windows Control Panel?
```
Yes, and no.
It is similar in that it does the job of adding or removing applications.
Different in that it also shows you packages that are not installed yet, but are available for installation.

Plus it has many more functionalities that make it a single point of all kind of general software management. Ubuntu Software Center (that is already present in default Ubuntu installation) also does the same thing, but is much more heavier (thus slow) and not as much transparent. It is made default just because it looks more familiar to new users (looks and behaves like a software download site). Hardcore users still prefer Synaptic or apt-get (command line) due to their speed, more controls and transparency.

---

### Post by GUZZLR on 2013-05-30
Thank you for the explanation...I was hoping it would keep a record of all the apps I have, so If/when I re-install Ubuntu, or upgrade to the latest version, I would know which apps I already have, and not have to keep track of them by entering manually on a spread sheet

---

### Post by varunendra on 2013-05-30
> **GUZZLR said:**
> Thank you for the explanation...I was hoping it would keep a record of all the apps I have, so If/when I re-install Ubuntu, or upgrade to the latest version, I would know which apps I already have, and not have to keep track of them by entering manually on a spread sheet
You're welcome ! :)

What you were hoping can be done with 'dpkg --get-selections' command -
```
dpkg --get-selections > installed.list
```
This will create a file named "installed.list" in your Home directory that will contain all the packages currently installed on the system.

You may then copy this list to the fresh installation, then -
```
sudo dpkg --set-selections < installed.list
```
..assuming you have copied the file in your 'Home' in the fresh installation, else also include the path to the file.

However, this list contains 'All' the installed packages, most of which you didn't actually install, but they were installed already or got installed as 'dependencies' of the few packages that you actually did install. Also, I haven't tried this personally (I use aptoncd instead), so there may be caveats.

Some good reference about these :
[http://askubuntu.com/questions/17823/how-to-list-all-installed-packages](http://askubuntu.com/questions/17823/how-to-list-all-installed-packages)
[http://ubuntuforums.org/showthread.php?t=261366&page=12](http://ubuntuforums.org/showthread.php?t=261366&page=12) (apparently more comprehensive)


**PS:**
As an additional tip, all the packages that you have manually installed (the .deb packages, using any package manager) are downloaded to '**/var/cache/apt/packages/**' directory. And remain there in case you need to reinstall them. Unless you manually removed them (simple deletion, or using 'apt-get clean' command), they would still be there. If so, you can use **AptOnCD** software to create an installation source cd from these packages. You can then use this cd as a software source on a fresh installation of the same version of Ubuntu (or a version that uses the same version of software packages).

Please note that, this cd/dvd will only work on the same version of Ubuntu from which you created it (because different version may require different version of software packages as well). But still, it is a quite handy utility to have.

To install aptoncd, simply run 'sudo apt-get install aptoncd' while you are connected to internet. Once installed, you can find its GUI in the applications menu.

---

### Post by GUZZLR on 2013-06-02
Still no luck, I ran the live disk of 12.04 on the Dell and still could not get wired through the router.  I have run 13.04 Live disk on my normal computer (HP Pavilion, Windows 7 Pro) and works fine with wireless and wired directly to the router, this is also true running Mint14; Mint14 works on the HP, but does not work on the older Dell.  So, I believe it's not the version of Ubuntu, or which distro. is used, it's simply something wrong with the old Dell which I believe both of you know anyway.  
At this point, I say we call it quits.  The Dell will work on wired directly to the modem, and this will suffice if I require it as a backup plan.  Quite frankly, if I did have to go to this backup plan, we could assume I don't have a router anyway.
My only regret, other than not getting the Dell to work, is having you two spend so much time helping.
At any rate, thank you for your time and help...

---

### Post by Hadaka on 2013-06-02
Giving up? In the spirit of Nikola Tesla...i say...one more try ! :)

--ISP--[MODEM]===[DELL] <-This works
--ISP--[MODEM]===[ROUTER]===[DELL] <- This does NOT
--ISP--[MODEM]===[ROUTER]===[-HP-] <- This works
*If you are using the EXACT same cables with modem/router for the dell and the hp...then this proves all connections are 
good. (i.e HP works..)
try this..
connect the Dell to the modem..--ISP--[MODEM]===[DELL]
then..insert your 12.04 disc. boot to it...and when it asks what to do..
tell it to do a complete overwrite everything install...INCLUDING..ALL the updates.
This will take some time...*If it hangs with the 4 dots blinking...post back..I have
an easy work around for that..been there..done that..many times.
*Note..the mars rover wouldnt be there if the Wright brothers had given up :P

---

### Post by GUZZLR on 2013-06-02
You're killing me here...hold on

---

### Post by GUZZLR on 2013-06-02
One thing I just realized, when I originally downloaded and burned 12.04, I never verified it...simply because I've never done it and don't know how

---

### Post by Hadaka on 2013-06-02
You can verify its ok by stuffing it into the "you know it works"
HP machine...then just mash the "Try Ubuntu" button.
That should let you know if its a clean burn...the os doesnt
care what the computer brand is on the "Try Ubuntu" mode.

---

### Post by GUZZLR on 2013-06-02
Well it's a clean burn then, because I just stuffed it into the HP and everything works...including wired and wireless.

---

### Post by Hadaka on 2013-06-02
ok..so tell me EXACTLY what you did...every step
to get the HP to boot up to your freshly burned 12.04
thanks.

---

### Post by GUZZLR on 2013-06-02
[LIST=1]
[*]Turn the HP machine off (with the disk tray open) 
[*]Put the 12.04 disk in the trey and close 
[*]Turn on the machine 
[*]Hit ESC key while machine is booting, to get into boot menu (F2 key on my Dell) 
[*]Booted from CD/DVD trey into Live Disk 
[*]Push the "Try Ubuntu" button 
[*]Found my wireless SSID and input password key 
[*]It immediately connected wirelessly 
[*]Disconnected from wireless 
[*]Plugged in Ethernet cable (cable is hooked to router) 
[*]Immediately connected to internet via ethernet cable to router 
[*]Shut down Ubuntu live disk and machine stop 
[/LIST]

---

### Post by GUZZLR on 2013-06-02
So I've installed 12.04 now and here's what I've done:  
[LIST=1]
[*]I have done updated (211 updates)
[*]Installed Ubuntu Restriced Extras
[*]Checked the additional drivers section; none are showing
[/LIST]

I have no wireless (I know when I do have wireless because the WiFi light is lit...which it isn't now), and wired connection works with the modem directly, but not with the router.  
To get my wireless working previouysly, I used:
  	 	 	 	
[LIST=1]
[*]sudo apt-get purge b43-fwcutter firmware-b43-installer firmware-b43-lpphy-installer firmware-b43legacy-installer bcmwl*
[*]sudo apt-get install b43-fwcutter firmware-b43-installer bcmwl*
[/LIST]
   
However, you did not like that, and told me to use another code.
I'd like to get my wireless working so I can use my other devices.  Currently, I can not use my router as the ethernet cable is hooked directly to the modem going to the Dell, instead of going to my router.
Do you want me to use the two lines above, or use something eles?

Thanks

---

### Post by Hadaka on 2013-06-02
Excellent !
ok, and read carefuly....this time...with the Dell
connect the ethernet cable to the modem...dont even think about messing with wireless.
then fire up the dell...F2...set to boot on CD
with the ethernect cable connected to the modem (no router) let it
boot to the CD....*if it boots ok..go to INSTALL...bypass the try routine..
install it...again..*IF it hangs on the install...STOP.. post back and we will
get past that. also...do not do any other commands..or try anything other than
simply connecting the ethernet cable to the modem...booting to cd and install.
Im keepin an eye on you this time ! ;)

---

### Post by GUZZLR on 2013-06-02
Oops, I just installed GParted to look at my drive[ATTACH=CONFIG]243455[/ATTACH]

---

### Post by GUZZLR on 2013-06-02
What about checking the update and 3rd party boxes on the re-installation?

---

### Post by Hadaka on 2013-06-02
Hi,, yes on updates...NO on 3rd party.
It also looks like you isnstalled a screen saver / background pic...
hmmm

---

### Post by GUZZLR on 2013-06-02
I don't like the orange, it hurts my eyes...

---

### Post by Hadaka on 2013-06-02
ok..so lets look at a couple things before we try the wireless
which by the way..your commands are not correct...we will
do the correct command shortly.
please post the output of..
```
uname -a
```
the correct command for your wireless card...is..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
but i have a feeling you tried the other one already...
let me know
thanks.

---

### Post by GUZZLR on 2013-06-02
```
guzzlr@LATITUDE:~$ uname -a
Linux LATITUDE 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux
guzzlr@LATITUDE:~$ 

```

OK, so I reinstalled (with update checked, and 3rd party unchecked) and everything went OK.  The update manager is showing 213 updates, which I have not updated and I have not installed any other apps...which you have no idea how hard it was to reframe myself from doing.
I have wired connection to the modem, I have not tried connecting ethernet with the router.  Do you want me to run the wireless code you suggested?
Thanks

[ATTACH=CONFIG]243456[/ATTACH]By the way, this is showing on my additioal drivers, I didn't do anything with it
And what about the 213 updates?

---

### Post by Hadaka on 2013-06-02
Good, because that driver is not correct for your card..
please do the 212 or whatever updates first
then issue this command..
```
sudo apt-get upgrade
```
then once again post the output of
```
uname -a
```
then..if you want the wireless do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

---

### Post by GUZZLR on 2013-06-02
```
guzzlr@LATITUDE:~$ sudo apt-get upgrade
[sudo] password for guzzlr: 
Sorry, try again.
[sudo] password for guzzlr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
guzzlr@LATITUDE:~$ uname -a
Linux LATITUDE 3.5.0-32-generic #53~precise1-Ubuntu SMP Wed May 29 20:35:31 UTC 2013 i686 i686 i386 GNU/Linux
guzzlr@LATITUDE:~$ 

```

OK, updates are done
Thanks

---

### Post by GUZZLR on 2013-06-02
```
guzzlr@LATITUDE:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for guzzlr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,952 kB of archives.
After this operation, 8,980 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu2 [3,952 kB]
Fetched 3,952 kB in 3s (1,100 kB/s)                 
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 169769 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.11ubuntu2_all.deb) ...
Setting up linux-firmware-nonfree (1.11ubuntu2) ...
guzzlr@LATITUDE:~$ sudo modprobe b43
guzzlr@LATITUDE:~$ 

```

Here is the output for wireless, I'll let you know in a minute if wireless works.

Wow, my wireless is working!...Maybe I really should listen to what you're saying :)

---

### Post by Hadaka on 2013-06-02
ok,,so next, power down the router,power down the computer.
then power up the router..connected to the modem...let it sync up
to the modem, connect the computer to the router...fire up the computer.
got wired connection?

---

### Post by GUZZLR on 2013-06-02
[ATTACH=CONFIG]243459[/ATTACH]Nope, same thing.  It says it is connected, and it appears to be connected, but it will not pull in any websites.  One thing interesting, when it says it is connected to the router, it reads at 100mb/sec, and the connection lights are solid orange and flashing yellow.
When it actually is connected via the modem, the network mangager is reading 10mb/sec and the lights are solid green and flashing yellow. 
So maybe there is something screwy going on there, because this computer is only capable of a BG draft, no N Draft, and there's no way something this old can get to 100mb/sec.
Just my thoughts

---

### Post by Hadaka on 2013-06-02
Mine says the same thing..
[ATTACH=CONFIG]243460[/ATTACH]
on a 2005 dell with a ity bity 40 gig drive.
difference is...my wired and wireless work.
cant imagine why ;)
sooo...in conclusion, *if you used the exact same cables
for the hp and it worked with the router wired...then there
is probably something amiss with the circuit on your ethernet card
with send/rcv to a router....or...you have a faulty cable,but the hp
may put out more power and over ride the fault...or  operator error.
I would suggest  a different cable to start, test with the hp then the dell
then..consider getting a different ethernet card...after of course exhausting
any possibility of user error configuration. Beyond that I am out of ideas or
suggestions.

---

### Post by varunendra on 2013-06-03
> **GUZZLR said:**
> I believe it's not the version of Ubuntu, or which distro. is used, it's simply something wrong with the old Dell which I believe both of you know anyway. 
....
My only regret, other than not getting the Dell to work, is having you two spend so much time helping.
At any rate, thank you for your time and help...
You're most welcome, especially because of your patience and persistence. For us, it's just hobby, so no problem with the time. The best part of an 'honest attempt to help' is that even if we fail, we get the benefit of gaining experience.

As for the problem itself, yes, I have been suspecting from the beginning that there is probably some 'cold war' going on between your Dell's BIOS and the router's firmware (can't say what Hadaka thinks). That's why I suggested the BIOS reset. But then again, it is just another guess and we don't have much clue to support that guess (other than everything else being ruled out).

> **GUZZLR said:**
> [ATTACH=CONFIG]243459[/ATTACH]One thing interesting, when it says it is connected to the router, it reads at 100mb/sec, and the connection lights are solid orange and flashing yellow.
When it actually is connected via the modem, the network mangager is reading 10mb/sec and the lights are solid green and flashing yellow. 

Like I mentioned in post #116, the solid light colours are just indicators of the 'shake-hand' speed. But you are misunderstanding this part -
> So maybe there is something screwy going on there, because this computer is only capable of a BG draft, no N Draft, and there's no way something this old can get to 100mb/sec.
Like Hadaka mentioned many posts ago (I don't have the courage to dig it up ;)), B,G,N are relevant to the wireless only. They have nothing to do with ethernet.

And....
100mb/s = 100/8 mB/s = **12.5 mB/s** (b=bit, B=Byte).

This is a speed that the oldest available ethernet card in today's market can happily provide. So you don't need to doubt the capability of your card :P

However, if you think forcing a slow speed 'may' help, we may try mii-tool to force the 10mb/s (full duplex) speed. Check if mii-tool is installed and is supported by your card -
```
sudo mii-tool eth0

```
Running the above command when you are connected directly to the modem should give something like -
> eth0: 10 Mbit, full duplex,.....

If so, connect to the router, and force the same speed -
```
sudo mii-tool -F 10baseT-FD eth0
```
Your ethernet lights should immediately turn solid green and the speed 10mb/s.

To reset the speed to defaults -
```
sudo mii-tool -r eth0
```

Oh, and if mii-tool is not installed at all (I'm not sure if it's installed by default or not), then ofcourse -
```
sudo apt-get install mii-tool
``` to install it.

If, like everything else, this one fails too. I won't be surprised (what may surprise me is if it worked :P). Only my doubt on the BIOS/firmware would be reaffirmed.

---

### Post by GUZZLR on 2013-06-03
Fortunately, the Wright Brothers did not build this computer

---

### Post by GUZZLR on 2013-06-03
```
guzzlr@LATITUDE:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for guzzlr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,952 kB of archives.
After this operation, 8,980 kB of additional disk space will be used.
Get:1 http://mirror.anl.gov/pub/ubuntu/ precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu2 [3,952 kB]
Fetched 3,952 kB in 3s (1,090 kB/s)                 
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 170865 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.11ubuntu2_all.deb) ...
Setting up linux-firmware-nonfree (1.11ubuntu2) ...
guzzlr@LATITUDE:~$ sudo modprobe b43

```

Umm...I think I broke my computer again.  I reloaded 12.04, after reloading 13.04 again, and now I can't get my wireless backIt gets stuck on the modprobe b43 command
Can you fix my computer for me again?
Thanks

---

### Post by GUZZLR on 2013-06-03
I'm back on 13.04, but I'm afraid to insert any wireless codes because you'll probably get mad at me again...

---

### Post by varunendra on 2013-06-04
> **GUZZLR said:**
> I'm back on 13.04, but I'm afraid to insert any wireless codes because you'll probably get mad at me again...

I didn't see any notion of that ;)

Making your wireless work is really easy and a sure-shot thing. You just have to do/remember two things to make it work on a fresh install -

[INDENT]1) DO NOT install the driver that Ubuntu automatically suggests [COLOR="#0000CD"](remove it completely if you already have, see the part coloured in blue below)[/COLOR], and

2) Install the 'linux-firmware-nonfree' any possible way you like > reboot > Done ![/INDENT]

To elaborate on these, the automatically suggested driver is not good enough for your card. The better one is already included in the kernel, but it needs broadcom's proprietary 'firmware' to work. This firmware can not be distributed with the installation CD/DVD due to licencing issues (hence the term 'nonfree'). The 'linux-firmware-nonfree' package is actually just a collection of many such 'nonfree' firmwares that are required by certain devices to work. You wireless card's firmware is just a tiny part of that collection. We recommend it because it is easier to download and install.

If you have a working internet connection, just run the following command to install it -
```
sudo apt-get install linux-firmware-nonfree
```
(note that if it is an absolutely fresh installation, you may have to run "sudo apt-get update" before above command)

If you don't have a working internet connection, just download the package from here : [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download)
Copy the downloaded file over to the Ubuntu machine and double click to install.

[COLOR="#0000CD"]If you have already installed the wrong driver suggested by "Additional Drivers" program, you will have to completely remove it -
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```[/COLOR]

Do a reboot after removing above (and installing the 'linux-firmware-nonfree' package), and your wireless should be up.

Feel free to ask if the above steps look confusing or if you have any problems while or after following them.

**PS:**
We are already mad enough to be on these forums and pulling out our hair on others' problems when our own systems are working fine. So don't worry, problems like yours can't make us any madder ;)

---

### Post by GUZZLR on 2013-06-04
OK thanks.  I still am showing the bad driver which is reccomended.  I have learned my lesson abut not using this driver.  With my machine, running 13.04, If I use this driver, in addition to not working, it will completely lock up the machine when I try to shut down; basically, I can't turn the machine off.  I had to do another fresh install of 13.04 to get the machine to turn off again, this has happened to me twice now, so I definately do not mess with that bad duggested driver.  My question, is how do I keep 13.04 from showing the driver for additional drivers recommended in the upadate manager?  I would like to get ric of that message/suggestion.  With the last fresh instal, too my knowledge, I do not believe it is in the machine as it is still showing to be installled in the update manager.
Thanks

---

### Post by GUZZLR on 2013-06-04
```

sudo apt-get update
sudo apt-get install linux-firmware-nonfree


```

OK, ran the two commands, and everything is working fine, including shut-down, which has always been a problem with this machine and 13.04.  12.04 never had an issue with shut-down, but 13.04 did not like to...it would always freeze and I would have to do a hard shut-down.

Also, I originally had problems with previous wireless codes because my terminal window would lock-up and I was stuck.  In the future, if that happens again, is there a command to free the terminal/computer so I can use it.  The only way I knew how was to do another fresh install...which I feel confident is definately the hard way to get a working terminal.
Thanks

---

### Post by varunendra on 2013-06-04
> **GUZZLR said:**
> how do I keep 13.04 from showing the driver for additional drivers recommended in the upadate manager?  I would like to get ric of that message/suggestion
I'm not sure, but this *should* work -
Open **Software Center > Edit > Software Sources**. In the first tab (Ubuntu Software), **clear** the checkbox that says "**Proprietary drivers for devices (restricted)**". Close it, then in terminal, do-
```
sudo apt-get update
```
Hopefully, this will get rid of the message. If not, then I'm afraid you'll have to learn how to power on the lappy with some extra dose of ignorance :D

> **GUZZLR said:**
> Also, I originally had problems with previous wireless codes because my terminal window would lock-up and I was stuck.  In the future, if that happens again, is there a command to free the terminal/computer so I can use it.
The number of reasons why a terminal (or the whole desktop) may get stuck are quite so many. Generally, whenever only terminal gets stuck, you can simply close it (using the close button on top) > then reopen to get it working again. If not, or if the whole desktop gets stuck, you can go to virtual terminals to run commands there, including some that restart a gui session.

To get to a virtual terminal, press **Ctrl+Alt+F1** (F1 through F6 give you 6 different virtual terminals). You'll get login prompt. Enter your login id, then password to login. Run the commands you need, then '**exit**' to logout (or leave it logged in). To get back to GUI desktop, press **Ctrl+Alt+F7**.

Three common commands I know of that restart a GUI session are (try any one at a time) -
```
Unity
Unity --reset
restart lightdm
```
The first command tries to start a fresh session of Unity. I often have to run it more than once to get back a working desktop (yeah, sometimes I mess up my desktop session too ;)). The downside is, the working desktop runs as a process through the virtual terminal, so it gets permanently busy as long as the desktop is running. To be able to run another command, you'll have to 'stop' the process 'unity', which will kill the working GUI session (the GUI will be back to its stuck state). Not a problem for me as there are still 5 other virtual terminals available ;)

The second command resets Unity to its defaults and is more recommended way. Downside is - it resets all the settings and desktop configurations. So you lose any customization like wallpaper, launcher buttons etc. I haven't yet tried it, so can't say this is permanent or just for the running session.

The third command just restarts a fresh GUI session, killing the previous one. I have tested it only once, and it took me back to login screen. When I logged in, all my open programs were closed, which wasn't desirable. Can't say if it was just me or something it is meant to do. Also, the customization were back to default, but back again after a reboot.

Lastly, if everything is stuck but the virtual terminals work, you can also enter "sudo reboot" or "sudo poweroff" commands to just do a proper reboot or shutdown.

---

### Post by GUZZLR on 2013-06-04
```
Open **Software Center > Edit > Software Sources**. In the first tab (Ubuntu Software), **clear** the checkbox that says "**Proprietary drivers for devices (restricted)**".
```

That worked, thanks!

---

### Post by varunendra on 2013-06-04
> **GUZZLR said:**
> That worked, thanks!

Glad I could help that :)

---

### Post by GUZZLR on 2013-06-23
```
sudo apt-get install linux-firmware-nonfree
```

Hello Varunendra...
So I've installed 13.04 on a newer laptop: HP Pavilion, Win7 Pro. Wireless and Wired is working correctly, I've installed several things including restricted  extras.  
Question:  Because this is a newer computer, with a newer operting system from the old XP computer we were having a hard time with, should I still install the linux firmware nonfree package?

Thanks for the help!

---

### Post by Hadaka on 2013-06-23
Hi, if your current driver is allowing the wireless to work
no need to load another driver...that would be like having
an automobile with a working engine...then attempting to
bolt another engine on top if it.

---

### Post by GUZZLR on 2013-06-23
But it's twice the Horsepower!!

---

### Post by varunendra on 2013-06-23
> **GUZZLR said:**
> Wireless and Wired is working correctly...... should I still install the linux firmware nonfree package?

Like Hadaka already explained, "don't fix it if it ain't broken !". :D

The linux-firmware-nonfree package is just a collection of some proprietary firmwares which is only needed if the system has such a hardware that requires any of those firmware. If everything is working fine, you don't need it.

And congrats for the "double horse-power" !! :P

---

### Post by GUZZLR on 2013-06-23
Actually, everything is not working fine anymore...I just lost my background...nothing, just a black screen.  Everything else works, just no background.
I'll make a new post.

---

