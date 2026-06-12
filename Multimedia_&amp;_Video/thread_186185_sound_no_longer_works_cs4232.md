---
title: "sound no longer works cs4232"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by orsonj on 2006-06-01
I was able to get sound working in breezy, but now it doesn't work with dapper.

I added the line
cs4232 io=0x534 irq=5 dma=1 dma2=0
to /etc/modules and sound worked fine in breezy.

With dapper it doesn't work.

---

### Post by Zill on 2006-08-23
Just installed Dapper here with the same results on a Dell Optiplex.
Can anyone help?
Many thanks.

---

### Post by Zill on 2006-08-23
I have found an answer to my problem courtesy of shanenin at [http://www.besttechie.net/forums/index.php?showtopic=2559&st=15](http://www.besttechie.net/forums/index.php?showtopic=2559&st=15)

first load the module with this command
sudo modprobe snd-cs4236

then restart alsa with this command
sudo /etc/init.d/alsa-utils restart

after that, you may want to check to see if your master and pcm volume are unmuted, you can check with the command
sudo alsamixer

Hope this helps someone struggling with these old sound chips!

---

### Post by Zill on 2006-08-25
Note that the above only loads the module until the next reboot.
To load the sound module automatically on boot use sudo gedit to add the following line to /etc/modules
snd-cs4236
Then reboot and ALSA sound should start up OK.

---

### Post by graylion on 2006-08-28
TP600

mine doesn't load "device not found"

OS is xubuntu dapper

bios claims that audio and dsp are working

lsmod
Module                  Size  Used by
ipv6                  265728  6
nvram                   9224  1
uinput                  9088  1
apm                    21228  1
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
af_packet              22920  2
tsdev                   8000  0
xircom_tulip_cb        18864  0
xircom_cb              11520  0
irtty_sir               8576  0
sir_dev                19628  1 irtty_sir
nsc_ircc               23948  0
irda                  187068  3 irtty_sir,sir_dev,nsc_ircc
crc_ccitt               2304  1 irda
pcmcia                 40508  0
analog                 12320  0
ns558                   5636  0
floppy                 62148  0
gameport               15496  3 analog,ns558
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
pcspkr                  2180  0
rtc                    13492  0
psmouse                36100  0
serio_raw               7300  0
i2c_piix4               9104  0
i2c_core               21904  1 i2c_piix4
yenta_socket           28428  3
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               130692  2 uhci_hcd
ide_cd                 33028  1
cdrom                  38560  1 ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
processor              23360  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
0000:00:02.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
0000:00:03.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
0000:05:00.0 Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)

---

### Post by AndrewS on 2006-10-30
I also can't get the cs4232 sound card working on my Thinkpad 770E.  I get the following:

andrew@Home:~$ sudo modprobe snd-cs4236
Password:
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.15-26-386/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device
andrew@Home:~$ sudo modprobe snd-cs4232
FATAL: Error inserting snd_cs4232 (/lib/modules/2.6.15-26-386/kernel/sound/isa/cs423x/snd-cs4232.ko): No such device
andrew@Home:~$ lsmod
Module                  Size  Used by
snd_opl3_lib           10624  0
snd_hwdep               9376  1 snd_opl3_lib
snd_cs4236_lib         16512  0
snd_mpu401_uart         7808  0
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_opl3_lib,snd_rawmidi
snd_cs4231_lib         26752  1 snd_cs4236_lib
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_cs4236_lib,snd_cs4231_lib,snd_pcm_oss
snd_timer              25220  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    55268  11 snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_cs4231_lib,snd_pcm
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
nvram                   9224  1
uinput                  9088  1
apm                    21228  1
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
lp                     11844  0
tsdev                   8000  0
8139cp                 22528  0
8139too                26880  0
mii                     5888  2 8139cp,8139too
analog                 12320  0
ns558                   5636  0
gameport               15496  3 analog,ns558
irtty_sir               8576  0
sir_dev                19628  1 irtty_sir
nsc_ircc               23948  0
irda                  187068  3 irtty_sir,sir_dev,nsc_ircc
crc_ccitt               2304  1 irda
pcmcia                 40508  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
psmouse                36100  0
serio_raw               7300  0
rtc                    13492  0
pcspkr                  2180  0
floppy                 62148  0
i2c_piix4               9104  0
i2c_core               21904  1 i2c_piix4
yenta_socket           28428  3
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               130692  2 uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
processor              23360  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

Any thoughts would be appeciated.

Thanks

Andrew

---

