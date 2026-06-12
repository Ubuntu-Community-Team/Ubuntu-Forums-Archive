---
title: "Connecting to Wireless drops Wired connection"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by Lumb on 2009-06-16
Hi all,

I recently installed Ubuntu and am having some troubles with networking. I've gotten to the point where my wireless connection is stable, however whenever I log on on my laptop (the PC which has ubuntu installed on it), the wired connection on my desktop (Windows 7) no longer functions. If I restart my router and modem, I can browse both for maybe 10 minutes until the wired will again go off. I don't think this is a coincidence, as i've tested it quite a bit and without my laptop connected the wired connection stays on without fail. There are 2 other PC's in my house which are on wireless and are fine when I log on to the Ubuntu Laptop - hence why I'm thinking it could be an Ubuntu related problem.

Due to the fact that I'm new to Ubuntu and fairly unfamiliar with Linux as a whole, I don't have all that much information to offer. I have been reading around a bit though and I understand this to be the procedure when asking for networking help

 **Laptop brand and model:**

Sony VAIO NR38ES

 **Wireless Brand, Model and Wireless Chipset:**

06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

**ifconfig:**

```

james@james-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:80:fa:9e:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:540 (540.0 B)  TX bytes:540 (540.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:f7:1b:44  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:fef7:1b44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:116270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:135717905 (135.7 MB)  TX bytes:13174546 (13.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3A-F7-1B-44-62-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```**iwconfig:**

```

james@james-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"home1"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:1F:33:FE:35:58   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=45/100  Signal level:-63 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```**lsmod**:

```

james@james-laptop:~$ lsmod
Module                  Size  Used by
aes_i586               15744  3 
aes_generic            35880  1 aes_i586
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
joydev                 18368  0 
arc4                    9856  2 
ecb                    10752  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
ath5k                 107008  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217208  1 ath5k
pcmcia                 44748  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class              12036  1 ath5k
psmouse                61972  0 
tifm_7xx1              13824  0 
soundcore              15200  1 snd
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_core              15900  1 tifm_7xx1
serio_raw              13316  0 
pcspkr                 10496  0 
cfg80211               38032  2 ath5k,mac80211
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
video                  25360  0 
sony_laptop            40796  0 
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
output                 11008  1 video
usbhid                 42336  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```Sorry if that's too much information, I thought i'd chuck it all in there just to be sure.

Thanks

---

### Post by Lumb on 2009-06-16
Update:

When I run the Windows Network Diagnostics tool, it says that the "Local Area Connection" doesn't have a valid IP configuration, and that the default gateway is not available. Again, as soon as I shut off ubuntu it would work fine.

---

### Post by Iowan on 2009-06-16
**ifconfig** doesn't show an address for eth0? You did mention something about wireless.  So Ubuntu is wireless, and Windows is wired?
What does the Windows setup (run>ipconfig) look like without the Ubuntu machine active?
Are all addresses via DHCP, or are some static?

---

### Post by Nonstop Crunchy on 2009-06-17
I am having a similar situation.  I am on a desktop and when I plug in my external USB WiFi to connect to a LAN it dumps both of my wired connections.  I have one wired with DHCP and one that is static.  I also need a static IP on my wireless.
I have to shut down X to get it back after I unplug the wireless.

---

### Post by sedawk on 2009-06-17
Is it possible you use the same IP on the laptop and on the windows box?
(ipconfig command on the command line if windows 7 still got any.
 Otherwise check the context menu of the LAN icon
 ("status" or "properties")

Another problem is when you have one computer with more then one
network interface (e.g. wlan and wired) and both are connecting
to the same network the same time. Two network interfaces configured
in the same subnet are always a guarantee for lots of confusion.

---

### Post by Nonstop Crunchy on 2009-06-17
> **Nonstop Crunchy said:**
> I am having a similar situation.  I am on a desktop and when I plug in my external USB WiFi to connect to a LAN it dumps both of my wired connections.  I have one wired with DHCP and one that is static.  I also need a static IP on my wireless.
I have to shut down X to get it back after I unplug the wireless.

To clarify mine.  I am on all ubuntu and I have a different subnet for the wireless 192.168.1.x, one of the wired is 192.168.0.x and the other wired is DHCP for my internet from the corporate internet.

---

