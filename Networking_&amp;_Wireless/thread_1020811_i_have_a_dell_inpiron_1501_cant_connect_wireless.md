---
title: "i have a dell inpiron 1501 cant connect wireless"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by jrranbrody on 2008-12-24
i have a dell inspiron 1501 that i recently install linux. since i installed linux i have not been able to connect my laptop to any type of wireless devise. can somebody help me sort my problem? thank you very much and happy holidays

---

### Post by ieee488 on 2008-12-24
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by jrranbrody on 2008-12-24
> **ieee488 said:**
> [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

i still cant get anything

---

### Post by ieee488 on 2008-12-24
That HOW-TO explains exactly what you need to tell us in your post other than "I can't get anything" which is NOT helpful in the least.

---

### Post by jrranbrody on 2008-12-24
1. Dell Inspiron 1501 Laptop
2. Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
3. wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:
4. Module                  Size  Used by
af_packet              23812  2 
ipv6                  267780  10 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
rfkill_input            5760  0 
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43                   144548  0 
rfkill                  8596  16 rfkill_input,b43
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
led_class               6020  1 b43
snd_hda_intel         344856  3 
input_polldev           5896  1 b43
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
wl                   1073940  0 
ieee80211_crypt         7040  1 wl
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
video                  19856  0 
output                  4736  1 video
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci                  19076  0 
i2c_piix4               9612  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
5. [   21.219529] Total of 2 processors activated (6786.84 BogoMIPS).
[   21.219689] ENABLING IO-APIC IRQs
[   21.219870] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   21.259543] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   21.259583] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   21.259586] ...trying to set up timer as Virtual Wire IRQ... works.
[   21.299414] Brought up 2 CPUs
[   21.299448] CPU0 attaching sched-domain:
[   21.299451]  domain 0: span 03
[   21.299454]   groups: 01 02
[   21.299457] CPU1 attaching sched-domain:
[   21.299459]  domain 0: span 03
[   21.299461]   groups: 02 01
[   21.299705] net_namespace: 64 bytes
[   21.299713] Booting paravirtualized kernel on bare hardware
[   21.300199] Time: 21:19:11  Date: 12/24/08
[   21.300231] NET: Registered protocol family 16
[   21.300436] EISA bus registered
[   21.300441] ACPI: bus type pci registered
[   21.315804] PCI: BIOS BUG #81[49435000] found
[   21.315844] PCI: Using configuration type 1
[   21.315853] Setting up standard PCI resources
[   21.317781] ACPI: EC: Look up EC in DSDT
[   21.320091] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   21.320367] ACPI: Interpreter enabled
[   21.320370] ACPI: (supports S0 S3 S4 S5)
[   21.320383] ACPI: Using IOAPIC for interrupt routing
[   21.321807] ACPI: EC: non-query interrupt received, switching to interrupt mode
6.   *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:26:58:e4:80
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
7. lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan result
8. 	Ubuntu 8.04.1
9. 2.6.24-22-generic i686 32 bit
10. ok


hope this is the info you need

---

### Post by Grazor on 2009-01-06
Try this: [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

---

