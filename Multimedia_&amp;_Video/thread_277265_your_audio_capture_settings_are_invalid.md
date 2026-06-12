---
title: "your audio capture settings are invalid"
date: 2006-10-14
forum: Multimedia &amp; Video
---

### Post by joyolee on 2006-10-14
when i run sound recorder, it says 

Your audio capture settings are invalid. Please correct them in the Multimedia settings

i have no idea how to correct them, could somebody help me ?

---

### Post by joyolee on 2006-10-14
besides, Mplayer gives me an error:

"Could not open/initialize audio device -> no sound"

but beep media player gives no error and continues to operate quite well

here's lsmod: 

Module                  Size  Used by
ipt_limit               2624  8
iptable_mangle          2976  0
ipt_LOG                 7392  8
ipt_MASQUERADE          3840  0
ip_nat                 20652  1 ipt_MASQUERADE
ipt_TOS                 2528  0
ipt_REJECT              6176  1
ip_conntrack_irc        6992  0
ip_conntrack_ftp        8176  0
ipt_state               2016  6
ip_conntrack           54136  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntr ack_ftp,ipt_state
nfnetlink               6808  2 ip_nat,ip_conntrack
iptable_filter          3104  1
ip_tables              23744  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE, ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ppp_generic            33556  0
slhc                    7456  1 ppp_generic
ipv6                  286976  20
dm_mod                 63256  0
af_packet              24520  2
lp                     12356  0
synaptics_usb          15520  0
tsdev                   8032  0
usbhid                 42752  0
snd_mpu401              7016  0
snd_mpu401_uart         8704  1 snd_mpu401
floppy                 64676  0
snd_rawmidi            26976  1 snd_mpu401_uart
irtty_sir               9312  0
snd_seq_device          9452  1 snd_rawmidi
sir_dev                21356  1 irtty_sir
irda                  217980  2 irtty_sir,sir_dev
parport_pc             37988  1
analog                 12800  0
crc_ccitt               2240  1 irda
8139cp                 24032  0
pcspkr                  2244  0
gameport               16776  1 analog
parport                39400  2 lp,parport_pc
8139too                29056  0
mii                     6176  2 8139cp,8139too
nvidia               4552660  0
i2c_core               22848  2 i2c_acpi_ec,nvidia
snd_intel8x0           35708  0
snd_ac97_codec         99520  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            55552  0
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                96804  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
psmouse                40004  0
snd_timer              26980  1 snd_pcm
intel_agp              24700  1
agpgart                36784  2 nvidia,intel_agp
serio_raw               7748  0
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
snd                    61220  10 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_ device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11336  2 snd_intel8x0,snd_pcm
evdev                  10176  2
ext3                  148296  4
jbd                    65876  1 ext3
ide_generic             1504  0
ehci_hcd               36104  0
uhci_hcd               35536  0
usbcore               139172  5 synaptics_usb,usbhid,ehci_hcd,uhci_hcd
ide_cd                 35780  0
cdrom                  41408  1 ide_cd
ide_disk               19136  6
piix                   11652  1
generic                 5124  0
thermal                13768  0
processor              26888  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

---

### Post by joyolee on 2006-10-14
any help appreciated

---

