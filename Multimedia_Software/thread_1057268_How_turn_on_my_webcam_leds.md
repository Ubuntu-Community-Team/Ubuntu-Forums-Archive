---
title: "How turn on my webcam leds"
date: 2009-02-01
forum: Multimedia Software
---

### Post by mimis_dim on 2009-02-01
I am newbie in linux , and my english are not very good (sorry)

I use ubuntu 8.4 .and have a digitus usb 6 leds webcam

[http://www.digitus.info/en/products/multimedia/?c=1161&p=4971](http://www.digitus.info/en/products/multimedia/?c=1161&p=4971)

In windows works ok using manufacture drivers (even with low room  light , video signal its ok)

ubuntu recognizes the webcam automatically :-) but every program i tried gives me very dark video signal (comorama , camstream ,cheese ,came )

as i said webcam gives signal but its very dark , even if i increase full brightness and color (for example with camstream)

In windows on the webcams option menu pane, i can turn on and off webcams 6 leds (for dark rooms)

how can i do the same (turn on / off my webcam leds) in ubuntu.

i searched a lot but nothing. :-(

lsusb gives
```

Bus 002 Device 002: ID 093a:2600 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse

```

lsmod gives
```

Module                  Size  Used by
via                    43648  2 
drm                    82580  3 via
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
lp                     12324  0 
powernow_k7             9000  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 powernow_k7,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
pcmcia                 40876  0 
joydev                 13120  0 
snd_via82xx            29464  3 
gameport               16008  1 snd_via82xx
snd_via82xx_modem      16264  0 
snd_ac97_codec        101028  2 snd_via82xx,snd_via82xx_modem
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         9728  1 snd_via82xx
cdc_ether               7168  0 
gspca                 643920  0 
videodev               29440  1 gspca
usbnet                 20232  1 cdc_ether
v4l2_common            18304  1 videodev
v4l1_compat            15492  1 videodev
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
video                  19856  0 
output                  4736  1 video
i2c_viapro              9876  0 
i2c_core               24832  1 i2c_viapro
container               5632  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0 
via_ircc               27796  0 
yenta_socket           27276  1 
battery                14212  0 
snd                    56996  19 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rsrc_nonstatic         13696  1 yenta_socket
ac                      6916  0 
button                  9232  0 
via_agp                11136  1 
shpchp                 34452  0 
parport_pc             36260  1 
irda                  203068  1 via_ircc
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
agpgart                34760  2 drm,via_agp
pci_hotplug            30880  1 shpchp
evdev                  13056  7 
parport                37832  3 ppdev,lp,parport_pc
crc_ccitt               3072  1 irda
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
led_class               6020  0 
wmi_acer                9644  0 
pcspkr                  4224  0 
psmouse                40336  0 
squashfs               49160  1 
loop                   18948  2 
unionfs                76752  1 
nls_cp437               6656  1 
isofs                  36388  1 
usbhid                 31872  0 
hid                    38784  1 usbhid
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  0 
floppy                 59588  0 
pata_via               13316  1 
ata_generic             8324  0 
pata_acpi               8320  0 
via_rhine              26632  0 
mii                     6400  2 usbnet,via_rhine
libata                159344  3 pata_via,ata_generic,pata_acpi
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  7 cdc_ether,gspca,usbnet,usbhid,ehci_hcd,uhci_hcd
ohci1394               33584  0 
ieee1394               93752  1 ohci1394
thermal                16796  0 
processor              36872  3 powernow_k7,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 


```



ps:why in linux i don't get as good video signal as in windows ? (as i said in windows the signal is very good even if room light is very low)

thanx :-)

---

### Post by mimis_dim on 2009-02-04
any ideas how to turn on/off webcam leds.?

---

### Post by astef on 2009-05-26
bump

---

