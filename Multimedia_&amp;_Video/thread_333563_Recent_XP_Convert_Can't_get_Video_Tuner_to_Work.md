---
title: "Recent XP Convert Can't get Video Tuner to Work"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by moviemavem on 2007-01-07
I'm a recent convert to Ubuntu from Windows XP. I have an HP Media Center PC m7160n with a dual boot for Ubuntu Edgy and Windows XP. I have just about everything working, except the tuner card that came with the PC. It works in XP using Windows Media Center (i.e. I can watch live TV); however, it doesn't work in Ubuntu. I tried installing the latest firmware and troubleshooting tips at ivtv.org, but all I get with in try to view the output in TVtime or MPlayer is a black screen. 

When I run the Hal Device Manager application, it tells me that I have a "iTVC16 (CX23416) MPEG-2 Encoder". From what I can see, the initialization cannot identify the card, so it defaults to Hauppauge WinTV PVR-150. It also seems to detect a  "Corrupt or not a Hauppauge eeprom." The following is the output from a diagnostic:

jlynn@jlynn-desktop:~$ dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac
[17179594.004000] ivtv:  ==================== START INIT IVTV ====================
[17179594.004000] ivtv:  version 0.7.0 (tagged release) loading
[17179594.004000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[17179594.004000] ivtv:  In case of problems please include the debug info between
[17179594.004000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179594.004000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179594.028000] Initializing USB Mass Storage driver...
[17179594.028000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179594.028000] usbcore: registered new driver usb-storage
[17179594.028000] USB Mass Storage support registered.
[17179594.028000] usb-storage: device found at 2
[17179594.028000] usb-storage: waiting for device to settle before scanning
[17179594.252000] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[17179594.500000] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 201
[17179594.516000] e100: eth0: e100_probe: addr 0xfdefd000, irq 201, MAC addr 00:13:D4:2F:7A:65
[17179594.516000] ivtv0: Unknown card: vendor/device: 4444/0016
[17179594.516000] ivtv0:               subsystem vendor/device: 1043/4b2e
[17179594.516000] ivtv0:               cx23416 based
[17179594.516000] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[17179594.516000] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[17179594.516000] ivtv0: card you have to the ivtv-devel mailinglist ([www.ivtvdriver.org](www.ivtvdriver.org))
[17179594.516000] ivtv0: Prefix your subject line with [UNKNOWN CARD].
[17179594.516000] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179594.516000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179594.552000] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[17179594.552000] tveeprom 0-0050: Encountered bad packet header [68]. Corrupt or not a Hauppauge eeprom.
[17179594.552000] ivtv0: No tuner detected, default to NTSC
[17179594.620000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179594.648000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179594.648000] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[17179594.860000] tda9887 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17179594.904000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179595.684000] NET: Registered protocol family 17
[17179598.876000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[17179599.032000] usb-storage: device scan complete
[17179599.032000]   Vendor: Generic   Model: USB SD Reader     Rev: 1.00
[17179599.032000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179599.036000]   Vendor: Generic   Model: USB CF Reader     Rev: 1.01
[17179599.036000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179599.040000]   Vendor: Generic   Model: USB SM Reader     Rev: 1.02
[17179599.040000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179599.044000]   Vendor: Generic   Model: USB MS Reader     Rev: 1.03
[17179599.044000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179599.056000] sd 2:0:0:0: Attached scsi removable disk sdb
[17179599.056000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[17179599.072000] sd 2:0:0:1: Attached scsi removable disk sdc
[17179599.072000] sd 2:0:0:1: Attached scsi generic sg2 type 0
[17179599.088000] sd 2:0:0:2: Attached scsi removable disk sdd
[17179599.088000] sd 2:0:0:2: Attached scsi generic sg3 type 0
[17179599.104000] sd 2:0:0:3: Attached scsi removable disk sde
[17179599.104000] sd 2:0:0:3: Attached scsi generic sg4 type 0
[17179599.660000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179599.876000] ivtv0: Encoder revision: 0x02050032
[17179599.876000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179599.876000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179599.876000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179599.880000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179599.880000] tuner 0-0060: type set to 0 (Temic PAL (4002 FH5))
[17179599.924000] ivtv0: i2c hardware 0x00000020 not found for command 0x4008646d!
[17179600.012000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[17179600.012000] ivtv:  ====================  END INIT IVTV  ====================

Any suggestions would be appreciated.

Jim

---

### Post by amoore on 2007-01-07
Try this for your IVTV drivers.
[URL="https://help.ubuntu.com/community/Install_IVTV_Edgy"]
https://help.ubuntu.com/community/Install_IVTV_Edgy[/URL]

you may also want to chech out MythTV for Ubuntu.

[https://help.ubuntu.com/community/MythTV ]("https://help.ubuntu.com/community/MythTV")

---

### Post by moviemavem on 2007-01-07
Thanks for the reply. I had already tried following the instructins on the Install_IVTV_Edgy page, but the OS still doesn't seem to ID my card properly.

I'm wondering if HP/Microsoft did something proprietary with my card for Windows Media Center.

Jim

---

### Post by superm1 on 2007-01-10
> **moviemavem said:**
> Thanks for the reply. I had already tried following the instructins on the Install_IVTV_Edgy page, but the OS still doesn't seem to ID my card properly.

I'm wondering if HP/Microsoft did something proprietary with my card for Windows Media Center.

Jim
Well if this is a specially branded card, it may or may not be supported.  Your other option (before reporting this to the the ivtv devs to help get your card supported) is to try the newer ivtv version.  

I've added a section to the wiki page outlining how to do this:
[https://help.ubuntu.com/community/Install_IVTV_Edgy#head-d6d00f1ee4698dd621edff3405efd3e8fb422643](https://help.ubuntu.com/community/Install_IVTV_Edgy#head-d6d00f1ee4698dd621edff3405efd3e8fb422643)

---

