---
title: "(sound card) vxpocket firmware does not load"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by ibanez88 on 2006-06-11
I'm working with a fresh install of Kubuntu Dapper on a Toshiba Satellite S105-5701 laptop, and I'd like to configure my Digigram VX Pocket V2 sound card.  I'm using the 686 kernel package (vxpocket support is built into kernel by default).    

I installed alsa-utils and alsa-firmware-loaders packages from the repos, and compiled the alsa-firmware (1.0.10) itself from alsa-project.org.  Ubuntu ships with the firmware loader but not the firmware itself.

When I insert the card into my pcmcia slot I get the following dmesg output:

------------
[4297123.195000] pccard: PCMCIA card inserted into slot 1
[4297123.195000] pcmcia: registering new device pcmcia1.0
[4297123.243000] vx: can't load firmware vx/bx_1_vxp.b56
-------------

The file referred to in the last line exists in /usr/lib/hotplug/firmware/vx and also in /usr/share/alsa/firmware/vxloader.  These are files created during firmware compilation.

Typing vxloader gives the following:
vxloader: no VX-compatible cards found

I copy-and-pasted the file /etc/modutils/alsa from the alsa-project.org site:

-------------
#ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-vxpocket
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
--------------

Also copied into /etc/pcmcia/vxpocket.conf:

------------
#
# PCMCIA device driver definitions for Digigram VXpocket card
#
# put this file under /etc/pcmcia
#

device "snd-vxpocket"
  class "audio" module "snd-vxpocket"

#
# card definitions
#

card "Digigram VX-POCKET"
  manfid 0x01f1, 0x0100
  bind "snd-vxpocket"
-------------


And here is my lsmod output:


--------------
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
ppdev                   9668  0
speedstep_ich           6188  0
speedstep_lib           4580  1 speedstep_ich
cpufreq_userspace       6496  1
cpufreq_stats           6688  0
freq_table              4928  2 speedstep_ich,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
toshiba_acpi           11076  0
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
ipv6                  286912  20
nls_utf8                2240  1
ntfs                  111728  1
dm_mod                 63256  1
md_mod                 76052  0
af_packet              24520  4
parport_pc             37988  0
lp                     12356  0
parport                39400  3 ppdev,parport_pc,lp
hostap_cs              68792  0
hostap                127844  1 hostap_cs
ieee80211_crypt         6528  1 hostap
snd_vxpocket           16552  1
orinoco_cs             18344  1
snd_vx_lib             38176  1 snd_vxpocket
orinoco                45940  1 orinoco_cs
hermes                  8352  2 orinoco_cs,orinoco
joydev                 10432  0
pcmcia                 41948  3 hostap_cs,snd_vxpocket,orinoco_cs
tsdev                   8032  0
sd_mod                 20448  2
usblp                  13920  0
synaptics_usb          15520  0
psmouse                40036  0
yenta_socket           30124  7
rsrc_nonstatic         14624  1 yenta_socket
pcmcia_core            45272  3 pcmcia,yenta_socket,rsrc_nonstatic
usbhid                 40992  0
serio_raw               7748  0
sg                     40096  0
sr_mod                 17988  0
snd_intel8x0           35740  1
snd_ac97_codec         99808  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
e100                   40964  0
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
mii                     6176  1 e100
snd_pcm                96676  4 snd_vx_lib,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
pcspkr                  2244  0
snd                    60004  10 snd_vxpocket,snd_vx_lib,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
nvidia               4552692  0
i2c_core               22848  2 i2c_acpi_ec,nvidia
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
intel_agp              24700  1
agpgart                36784  2 nvidia,intel_agp
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
evdev                  10176  3
sbp2                   24996  2
scsi_mod              145960  4 sd_mod,sg,sr_mod,sbp2
ext3                  148104  2
jbd                    65876  1 ext3
ide_generic             1504  0
ohci1394               37524  2
ieee1394              306520  2 sbp2,ohci1394
uhci_hcd               35408  0
usbcore               137700  5 usblp,synaptics_usb,usbhid,uhci_hcd
ide_cd                 35780  0
cdrom                  41408  2 sr_mod,ide_cd
ide_disk               19200  4
piix                   11652  1
generic                 5124  0
thermal                13768  0
processor              26344  1 thermal
fan                     4836  0
fbcon                  43904  0
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit
capability              4968  0
commoncap               7328  1 capability
-------------

Does anyone know why the firmware isn't loading?  Do I need to compile alsa-driver from alsa-project.org or is that already built into the kernel or other packages that I have?  

I should note that I have ALSA working perfectly using my built-in sound card.

Many thanks for reading this!

---

### Post by ibanez88 on 2006-07-30
Ok its been a while since I played with this but now after keeping my system updated - the card still doesn't work - it appears that I have a new clue from dmesg:

[17179925.712000] pcmcia: Detected deprecated PCMCIA ioctl usage.
[17179925.712000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[17179925.712000] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.


After following the link I updated my kernel boot line in /boot/grub/menu.lst to include:
pci=assign-busses

... with no change in behavior.  I still get the same dmesg output after reboot.


Also I've discovered that cardctl ident gives me:

Socket 0:
  product info: "TOSHIBA", "Wireless LAN Card", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)
Socket 1:
  product info: "Digigram", "VX-POCKET", "V1.0", "R1.0"
  manfid: 0x01f1, 0x0100
  function: 254 ((null))
Socket 2:
  no product info available

... so it looks like the FUNCID should maybe not be set to 254?  Not sure how to change this or if it is a symptom of some other misconfiguration.


Here is my lspci

0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)
0000:02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
0000:02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:02:0c.0 System peripheral: Toshiba America Info Systems TC6371AF SmartMedia Controller (rev 03)
0000:02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)


I've also discovered from here:
[http://www.kernel.org/pub/linux/utils/kernel/pcmcia/cardmgr-to-pcmciautils.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/cardmgr-to-pcmciautils.html)

"Kernels since 2.6.13-rc1 do not require the cardmgr daemon anymore. In those newer kernel the pcmcia bus acts almost as any other bus with full /sbin/hotplug support. Old style cardmgr setups should still work if the kernel is configured correctly. But be aware that the ioctl for PCMCIA will be removed in the near future.

The change to be /sbin/hotplug capable means that the normal /etc/init.d/pcmcia script is not required any more and in fact only hurts as it starts cardmgr. To use the new pcmciautils it is a requirement that cardmgr is not started."


Is there a problem with the way Ubuntu handles pcmcia cards or is the "couldn't load firmware" issue a misconfiguration on my part?


If anyone has any suggestions I would be forever grateful...... (I would also consider buying a different pro-quality audio card that configures more easily in Ubuntu!  But for the moment I'd like to exhaust all possibilities here.)

---

