---
title: "weird wireless"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by jjakspaw6 on 2010-09-15
Hi All,


first, I'm a noob. I Just switched my laptop back to Linux after 2 years. I set the system up as a dual boot with XP (I plan on removing XP all together is things go well enough) 
The first night, right after the install finished, wirless was not available... I hard wired the system and ran the updates .. and the BCM4legacy driver installed... I was up and going wireless just like that... 
after I rebooted the system, the wireless stopped working. The card was being seen and my network was being seen except it wouldnt except my wep key.

After a while and trying everything that I could I discovered that if I turn the security off the wireless works great. that is not good though.... 

here are wireless settings and such.....

jason@jason-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:10 memory:d0004000-d0005fff
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:80:f0:bf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=90 maxlatency=52 mingnt=11 multicast=yes
       resources: irq:11 ioport:8c00(size=256) memory:d000a000-d000afff memory:34000000-3400ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:44:fd:ea
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.5 multicast=yes wireless=IEEE 802.11bg
jason@jason-laptop:~$ lspci | grep Broadcom
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
jason@jason-laptop:~$ 
jason@jason-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_ali5451            15799  2 
snd_ac97_codec        100646  1 snd_ali5451
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
arc4                    1153  2 
radeon                675160  2 
snd_rawmidi            19056  1 snd_seq_midi
ttm                    49943  1 radeon
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
drm_kms_helper         29297  1 radeon
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm                   162409  4 radeon,ttm,drm_kms_helper
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 30784  0 
b43legacy             115152  0 
i2c_algo_bit            5028  1 radeon
snd                    54148  14 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           20408  1 
mac80211              205402  1 b43legacy
ati_agp                 5094  1 
rsrc_nonstatic         10015  1 yenta_socket
soundcore               6620  1 snd
i2c_ali15x3             5050  0 
video                  17375  0 
joydev                  8708  0 
agpgart                31724  3 ttm,drm,ati_agp
ppdev                   5259  0 
lp                      7060  0 
i2c_ali1535             4725  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 28820  0 
snd_page_alloc          7076  1 snd_pcm
output                  1871  1 video
cfg80211              126496  2 b43legacy,mac80211
parport_pc             25962  1 
psmouse                63245  0 
serio_raw               3978  0 
parport                32635  3 ppdev,lp,parport_pc
led_class               2864  1 b43legacy
ohci1394               26950  0 
floppy                 53016  0 
ssb                    38902  1 b43legacy
ieee1394               81181  1 ohci1394
pata_ali                7932  2 
natsemi                23934  0 
jason@jason-laptop:~$ sudo iwlist scan
[sudo] password for jason: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:63:2C:FC:F4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:off
                    ESSID:"898PM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001083c2c9c
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 0005383938504D
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

jason@jason-laptop:~$ iwonfig
No command 'iwonfig' found, did you mean:
 Command 'iwconfig' from package 'wireless-tools' (main)
iwonfig: command not found
jason@jason-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"898PM"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:63:2C:FC:F4   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


My router is the verizon fios Westell wireless router...if that is any help.

Any thoughts?

I also noticed that on reboot, networking is disbled. How do I fix that?

Thanks,

Jason

---

### Post by dumb_question on 2010-09-15
I have had a similar problem. Never figured it out, but after a lot of messing around and more or less randomly hitting buttons (I like to think of it as a "genetic algorithm" for fixing things), I found if I hit connect on the NetworkManager Applet, wait about one second, then hit connect on Wicd (which you need to have open in advance & ready for this), and then almost immediately, just after Wicd starts to say "putting up interface", hit the Wicd "Cancel" button, about 5 seconds after that, NM manages to connect to my WiFi. This now works consistently for me (as in, every time).

I came here specifically to look for someone having this problem (I think it's common, from my forum searches when it first happened to me) so that I could post this in the hopes that A) someone else will test it out and see if it works for them; and B) that someone who has a better idea than I do about how the insides of NM and Wicd work can use this information to figure out where the problem is.

Also I have no idea how to post bug reports :)

---

### Post by jjakspaw6 on 2010-09-26
Ok... Sort of solved I guess... I gave up on 10.4 and tried 9.10 seems to all be working now... a bit slow on wireless but working..

I may try 10.10 when it is released but for now all seems good with 9.10

---

