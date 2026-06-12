---
title: "No build Network problems"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by coolercooler on 2009-03-05
Just recently had a new build from my old pc that was very slow.

Am using latest from Gigabyte GA-MA78-us2h board, the install goes fine, an seems to run everything fine so I guess it's compatible with Linux.  But am having some network problems, my adapters work fine on my other pc, but on this new board have some issues.  if my adapter is plugged in usb, and if I reboot my pc, it hangs up halfway through boot with this message, " could not receive return value from daiemon Process fail".  If I take out the usb wireless card it boots up fine but when I insert the card in again while booted and restart the network I get these errors.

```
/etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
grep: /etc/resolv.conf: No such file or directory
grep: /etc/resolv.conf: No such file or directory
grep: /etc/resolv.conf: No such file or directory
----------------------------------------
                                                                       [ OK ]
/etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
RTNETLINK answers: No such process
grep: /etc/resolv.conf: No such file or directory
RTNETLINK answers: No such process
grep: /etc/resolv.conf: No such file or directory
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.
grep: /etc/resolv.conf: No such file or directory
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan1 ; Invalid argument.
grep: /etc/resolv.conf: No such file or directory
                                                                         [ OK ]
-------------------------------------------
/etc/init.d/networking stop
 * Deconfiguring network interfaces...                                          
grep: /etc/resolv.conf: No such file or directory
RTNETLINK answers: No such process
grep: /etc/resolv.conf: No such file or directory


```
This problem is with both 8.10 and 8.04 and 64 bit ubuntu

Please help.

---

### Post by coolercooler on 2009-03-06
Anyone any thoughts?  Do you guys think it might be hardware related?

---

### Post by puppywhacker on 2009-03-06
you have two errors, non is hardware related, those should show up when you run "dmesg"

1. resolv doesn't exist or it doesn't have the proper file rights
```
/etc/resolv.conf: No such file or directory
```

touch /etc/resolv.conf
chmod 644 /etc/resolv.conf

2. your devices could not be found this could mean the module wasn't loaded or the name of the interface has changed.
```
wlan0 ; No such device
```

post some output for us to chew on

```
lsmod
iwconfig
ifconfig
cat /etc/network/interfaces

```

---

### Post by coolercooler on 2009-03-06
Firstly thanks for trying to help, I was kind of started to think that it might have been my new hardware, and the ubuntu might be confusing my new board ga-ma78gm-us2h with old version ga-ma78gm-s2h :)

After typing these commands: 
touch /etc/resolv.conf
chmod 644 /etc/resolv.conf

When I now reboot, the system hangs on this message, "starting common unix printing system: cupsd" with my wireless adpter in usb port.  I had to take it out and reboot and it boot-up fine then I get this result with it plugged in and set to static address.

```

 lsmod

Module                  Size  Used by
cx88_dvb               23940  0 
ieee80211_rtl          80520  0 
ieee80211_crypt_ccmp_rtl     8064  1 ieee80211_rtl
ieee80211_crypt_tkip_rtl    11648  1 ieee80211_rtl
ieee80211_crypt_wep_rtl     6400  1 ieee80211_rtl
ieee80211_crypt_rtl     6788  4 ieee80211_rtl,ieee80211_crypt_ccmp_rtl,ieee80211_crypt_tkip_rtl,ieee80211_crypt_wep_rtl
arc4                    2944  0 
ecb                     4480  0 
blkcipher               8324  1 ecb
rtl8187                36096  0 
mac80211              165652  1 rtl8187
cfg80211               15112  1 mac80211
eeprom_93cx6            3200  1 rtl8187
af_packet              23812  0 
lirc_dev               15860  0 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
cpufreq_userspace       5284  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
video                  19856  0 
output                  4736  1 video
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
loop                   18948  0 
isl6421                 3200  1 
cx24116                16904  1 
cx88_vp3054_i2c         3968  1 cx88_dvb
videobuf_dvb           10116  1 cx88_dvb
dvb_core               89852  2 cx88_dvb,videobuf_dvb
tuner                  30660  0 
snd_seq_dummy           4868  0 
ipv6                  267908  12 
snd_hda_intel         346136  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_oss            35584  0 
zd1201                 23556  0 
cx8800                 36396  0 
cx8802                 19332  1 cx88_dvb
cx88xx                 76840  3 cx88_dvb,cx8800,cx8802
fglrx                1555468  27 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
ir_common              50180  1 cx88xx
v4l2_common            17280  2 tuner,cx8800
i2c_algo_bit            7300  2 cx88_vp3054_i2c,cx88xx
tveeprom               13572  1 cx88xx
videodev               44576  4 tuner,cx8800,cx88xx,v4l2_common
v4l1_compat            14852  1 videodev
agpgart                34760  1 fglrx
videobuf_dma_sg        15108  4 cx88_dvb,cx8800,cx8802,cx88xx
evdev                  13056  4 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
btcx_risc               5896  3 cx8800,cx8802,cx88xx
videobuf_core          19716  5 videobuf_dvb,cx8800,cx8802,cx88xx,videobuf_dma_sg
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
wmi_acer                9644  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
i2c_piix4               9612  0 
snd                    56996  17 snd_seq_dummy,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               24832  9 isl6421,cx24116,cx88_vp3054_i2c,tuner,cx88xx,v4l2_common,i2c_algo_bit,tveeprom,i2c_piix4
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
pcspkr                  4224  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
ide_cd                 32544  0 
cdrom                  37408  1 ide_cd
sd_mod                 30720  2 
pata_atiixp             8960  0 
ata_generic             8324  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
pata_acpi               8320  0 
floppy                 59588  0 
ehci_hcd               37900  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
atiixp                  5648  0 [permanent]
ide_core              113996  2 ide_cd,atiixp
r8169                  33156  0 
ahci                   28548  1 
libata                159600  4 pata_atiixp,ata_generic,pata_acpi,ahci
scsi_mod              151436  4 sbp2,sg,sd_mod,libata
ohci_hcd               26640  0 
usbcore               146412  6 rtl8187,zd1201,usbhid,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36488  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
---------------------------------------
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11b  ESSID:"net internet"  Nickname:"zd1201"
          Mode:Managed  Channel:6  Access Point: 00:11:50:F9:AB:0C   
          Bit Rate:11 Mb/s   
          Retry   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0/128  Signal level=43/128  Noise level:0/128
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


----------------
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:C5:92:2e  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3165091270 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:222 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19287 (18.8 KB)  TX bytes:19287 (18.8 KB)

wlan1     Link encap:Ethernet  HWaddr 00:0c:2d:00:22:95  
          inet addr:192.168.135.9  Bcast:192.168.135.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:2dff:fe00:2295/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6072 (5.9 KB)

----------------
 cat /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.24


auto wlan1
iface wlan1 inet static
address 192.168.135.9
        netmask 255.255.255.0
        network 192.168.135.0
        broadcast 192.168.135.255
        gateway 192.168.135.1
wireless-key XXXXXXXXXX
wireless-essid net internet

```

For security I just crossed out password and such.

Thanks

---

### Post by puppywhacker on 2009-03-09
these commands show that the wlan1 is up, and an internal ip-address is assigned. But the signal to weak to establish a link. You are transmitting packets, but not receiving any.

```
Link Quality:0/128  Signal level=43/128  Noise level:0/128
```

I think by playing around with "iwconfig" you should be abled to get some signal. Look at the last lines of "dmesg" to check the results.

you have an realtek usb rtl8187. I believe it should be capable of output powermanagement. You can run one of the following commands to increase the power

```
iwconfig wlan1 txpower auto
iwconfig eth0 txpower 25
```

---

