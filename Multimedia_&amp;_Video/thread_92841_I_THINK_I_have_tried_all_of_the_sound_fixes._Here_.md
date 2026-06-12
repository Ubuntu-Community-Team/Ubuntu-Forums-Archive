---
title: "I THINK I have tried all of the sound fixes. Here is my info."
date: 2005-11-20
forum: Multimedia &amp; Video
---

### Post by jaredwhitehead on 2005-11-20
I have been at this for a week now. Fortunately, I have learned a lot from the issue but I would rellay like to play an mp3 on my laptop. Here is my system info:

root@Porty:~# lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)
0000:06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

root@Porty:~# lsmod | grep snd
snd_nm256              67680  0
snd_ac97_codec         72188  1 snd_nm256
snd_pcm                78344  2 snd_nm256,snd_ac97_codec
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd                    48644  4 snd_nm256,snd_ac97_codec,snd_pcm,snd_timer
soundcore               9184  1 snd

root@Porty:~# lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  4
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
snd_nm256              67680  0
snd_ac97_codec         72188  1 snd_nm256
snd_pcm                78344  2 snd_nm256,snd_ac97_codec
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd                    48644  4 snd_nm256,snd_ac97_codec,snd_pcm,snd_timer
soundcore               9184  1 snd
i2c_piix4               8336  0
i2c_core               19728  2 i2c_acpi_ec,i2c_piix4
ath_pci                69148  0
ath_rate_sample        14344  1 ath_pci
wlan                  120988  3 ath_pci,ath_rate_sample
ath_hal               148432  3 ath_pci,ath_rate_sample
yenta_socket           22540  3
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  1 intel_agp
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  2
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
uhci_hcd               28048  0
usbcore               104188  2 uhci_hcd
ide_disk               16128  4
ide_generic             1664  0
piix                    9476  1
ide_core              125268  3 ide_disk,ide_generic,piix
unix                   24624  574
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

I don't think I'll be giving up on Ubuntu anytime soon, but I did get this old laptop (Omnibook 900) just to run Linux. I would appreciate any help.

---

### Post by jliedeka on 2005-11-20
You may want to check the file ALSA-Configuration.txt in the kernel sources.  They suggest a number of possible workarounds including driver options and alternate drivers to try.  Nothing seemed directly relevant.

I looked for the Omnibook 900 on linux-laptop.net.  The only entry I could find was for installing an older SuSE with a 2.2 kernel and OSS drivers.

The kernel docs were a big help for me getting my intel8x0 chip to work.

---

### Post by jaredwhitehead on 2005-11-23
I'm not sure where to find that file. I Googled it and found several files by that name, but I think you may have meant that it is in my system somewhere.

---

### Post by jliedeka on 2005-11-25
It is on your system if you installed the kernel sources.  If not, you may find it through Google but if you have the space, kernel sources are always good to have.  Plus you will know the docs relate to your kernel version.

Another good resource for sound is the ALSA project web site.  IIRC, they have a lot of user submitted data for various sound cards.

---

