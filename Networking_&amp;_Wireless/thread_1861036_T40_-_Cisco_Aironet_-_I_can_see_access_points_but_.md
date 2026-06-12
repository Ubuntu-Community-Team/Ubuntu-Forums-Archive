---
title: "T40 - Cisco Aironet - I can see access points but connecting to them times out"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by tryggvib on 2011-10-15
I have a IBM T40 running Ubuntu and after an upgrade to 11.04 the wireless card stopped working. Since then I have been trying to fix it but been unable to. I read somewhere that this would be fixed in 11.10 so I upgraded quickly but again it doesn't work in 11.10.

So now I want to see if I can fix this and start browsing the Internet again on wifi instead of mobile broadband.

The problem is that even though I can see a list of access points in the network manager indicator, I am unable to connect to them. Reading syslog tells me that it just times out.

People have suggested reconfiguring access points to fix the problem but I don't want to do that, since I use the wireless at other locations than my home (e.g. conferences) so I can't go and ask people to reconfigure routers just for me.

I am totally lost on what to do and would greatly appreciate some help. Here is some handy for those who want to help me (let me know if something else is needed).

Here is dmesg. I can't find any errors (except eth0 link not being ready but I have no problems with the wired network so I don't think this is an error)

```
dmesg (grep'd for eth and airo)
```> 
[    1.745775] e1000 0000:02:01.0: eth0: (PCI:33MHz:32-bit) 00:09:6b:bf:47:5f
[    1.745785] e1000 0000:02:01.0: eth0: Intel(R) PRO/1000 Network Connection
[   28.662384] airo(): Probing for PCI adapters
[   28.662447] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   28.662471] airo(): Found an MPI350 card
[   29.241602] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.773774] airo(eth1): Firmware version 5.40.10
[   29.773779] airo(eth1): WPA supported.
[   29.773783] airo(eth1): MAC enabled **************
[   29.775000] airo(): Finished probing for PCI adapters
[   41.352029] eth1: no IPv6 routers present
Here is a list of wireless devices. I can only see the bluetooth device (The wireless symbol on the computer itself shows that it is on).

```
rfkill list all
```> 
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
lshw tells me that it the wireless network is disabled. I have no idea why it is disabled.

```
sudo lshw -C network
```> 
  *-network:0            
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:09:6b:bf:47:5f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8400(size=64) memory:c0240000-c024ffff
  *-network:1 DISABLED
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:02:8a:9e:cf:80
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0210000-c0213fff memory:c0400000-c07fffff memory:c0800000-c09fffff
Now, here comes the weird thing. Running iwconfig shows two wireless interfaces, eth1 and wifi0 with the same configuration. In all of my years running GNU/Linux I have never seen this wifi0 before now. Running ```
dmesg | grep wifi
``` returns nothing. So I have no idea why wifi0 is there and where it comes from.

```
iwconfig
```> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"mywirelessessid" 
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid  
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535 
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-102 dBm  Noise level=-93 dBm
          Rx invalid nwid:1780  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24818   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"mywirelessessid" 
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid  
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535 
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-102 dBm  Noise level=-93 dBm
          Rx invalid nwid:1780  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24818   Missed beacon:0

ppp0      no wireless extensions.
After some reading I tried to see if the airo modules were loaded. I read on some other forum post that I should get a few lines returned but I only got one. I noticed that I don't have airo_cs which should be there according to other forum posts.

```
lsmod | grep airo
```> 
airo                   77500  0
I know about two modules that conflict with the airo module and I've added them to my blacklist.conf file:

```
/etc/modprobe.d/blacklist.conf
```> 
# conflicts with the airo module
blacklist padlock-aes
blacklist geode-aes
I have also tried to blacklist the same with underscore istead of hyphens (e.g. padlock_aes instead of padlock-aes) but that doesn't work. There might be other modules that conflict so here are the results of lsmod to show all of the loaded modules.

```
lsmod
```> 
Module                  Size  Used by
usbhid                 41905  0
hid                    77367  1 usbhid
snd_usb_audio         100880  3
snd_hwdep              13276  1 snd_usb_audio
snd_usbmidi_lib        24558  1 snd_usb_audio
ppp_deflate            12878  0
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0
ppp_async              17307  1
option                 21205  2
usb_wwan               19779  1 option
usbserial              37203  7 option,usb_wwan
usb_storage            44173  0
uas                    17699  0
joydev                 17393  0
pcmcia                 39822  0
ppdev                  12849  0
bnep                   17923  2
snd_intel8x0           33318  2
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
rfcomm                 38408  0
snd_pcm                80468  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec
bluetooth             148839  10 bnep,rfcomm
thinkpad_acpi          73942  0
radeon                925020  2
snd_seq_midi           13132  0
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65224  1 radeon
snd                    55902  20 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 radeon
psmouse                73673  0
drm                   192226  4 radeon,ttm,drm_kms_helper
yenta_socket           27428  0
pcmcia_rsrc            18367  1 yenta_socket
soundcore              12600  1 snd
serio_raw              12990  0
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
airo                   77500  0
nvram                  14029  1 thinkpad_acpi
video                  18908  0
irda                  185428  0
i2c_algo_bit           13199  1 radeon
binfmt_misc            17292  1
parport_pc             32114  1
crc_ccitt              12595  2 ppp_async,irda
shpchp                 32356  0
lp                     17455  0
parport                40930  3 ppdev,parport_pc,lp
e1000                 101773  0
floppy                 60310  0
I can't figure this out but I would love to get some help. It's a bit harsh to be without wireless for about 4 months (I didn't upgrade to 11.04 the moment it was released) so I really want to get this fixed.

Thanks in beforehand.

---

### Post by tryggvib on 2011-10-17
I believe this is the same issue as is being discussed here: [http://ubuntuforums.org/showthread.php?t=1838414](http://ubuntuforums.org/showthread.php?t=1838414) but that hasn't been solved either. I'm keeping this one open until one of these threads has been solved.

---

