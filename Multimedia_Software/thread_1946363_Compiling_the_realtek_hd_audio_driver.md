---
title: "Compiling the realtek hd audio driver"
date: 2012-03-24
forum: Multimedia Software
---

### Post by Brizlitman on 2012-03-24
After compiling the driver, I tried to run make install and this was the result:

brizlinux@Vishnu:~/Realtek/alsa-driver-1.0.25$ make install
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/brizlinux/Realtek/alsa-driver-1.0.25/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
rm: cannot remove `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound/ac97_codec.h': Permission denied
install: cannot create regular file `/usr/include/sound/aci.h': Permission denied
install: cannot create regular file `/usr/include/sound/ad1816a.h': Permission denied
install: cannot create regular file `/usr/include/sound/ad1843.h': Permission denied
install: cannot create regular file `/usr/include/sound/adau1373.h': Permission denied
install: cannot create regular file `/usr/include/sound/ak4113.h': Permission denied
install: cannot create regular file `/usr/include/sound/ak4114.h': Permission denied
install: cannot create regular file `/usr/include/sound/ak4117.h': Permission denied
install: cannot create regular file `/usr/include/sound/ak4531_codec.h': Permission denied
install: cannot create regular file `/usr/include/sound/ak4641.h': Permission denied
install: cannot create regular file `/usr/include/sound/ak4xxx-adda.h': Permission denied
install: cannot create regular file `/usr/include/sound/alc5623.h': Permission denied
install: cannot create regular file `/usr/include/sound/asequencer.h': Permission denied
install: cannot create regular file `/usr/include/sound/asound.h': Permission denied
install: cannot create regular file `/usr/include/sound/asound_fm.h': Permission denied
install: cannot create regular file `/usr/include/sound/asoundef.h': Permission denied
install: cannot create regular file `/usr/include/sound/atmel-abdac.h': Permission denied
install: cannot create regular file `/usr/include/sound/atmel-ac97c.h': Permission denied
install: cannot create regular file `/usr/include/sound/compress_driver.h': Permission denied
install: cannot create regular file `/usr/include/sound/compress_offload.h': Permission denied
install: cannot create regular file `/usr/include/sound/compress_params.h': Permission denied
install: cannot create regular file `/usr/include/sound/control.h': Permission denied
install: cannot create regular file `/usr/include/sound/core.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs4231-regs.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs4271.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs46xx.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs46xx_dsp_scb_types.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs46xx_dsp_spos.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs46xx_dsp_task_types.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs8403.h': Permission denied
install: cannot create regular file `/usr/include/sound/cs8427.h': Permission denied
install: cannot create regular file `/usr/include/sound/emu10k1.h': Permission denied
install: cannot create regular file `/usr/include/sound/emu10k1_synth.h': Permission denied
install: cannot create regular file `/usr/include/sound/emu8000.h': Permission denied
install: cannot create regular file `/usr/include/sound/emu8000_reg.h': Permission denied
install: cannot create regular file `/usr/include/sound/emux_legacy.h': Permission denied
install: cannot create regular file `/usr/include/sound/emux_synth.h': Permission denied
install: cannot create regular file `/usr/include/sound/es1688.h': Permission denied
install: cannot create regular file `/usr/include/sound/gus.h': Permission denied
install: cannot create regular file `/usr/include/sound/hda_hwdep.h': Permission denied
install: cannot create regular file `/usr/include/sound/hdsp.h': Permission denied
install: cannot create regular file `/usr/include/sound/hdspm.h': Permission denied
install: cannot create regular file `/usr/include/sound/hwdep.h': Permission denied
install: cannot create regular file `/usr/include/sound/i2c.h': Permission denied
install: cannot create regular file `/usr/include/sound/info.h': Permission denied
install: cannot create regular file `/usr/include/sound/initval.h': Permission denied
install: cannot create regular file `/usr/include/sound/jack.h': Permission denied
install: cannot create regular file `/usr/include/sound/l3.h': Permission denied
install: cannot create regular file `/usr/include/sound/max98088.h': Permission denied
install: cannot create regular file `/usr/include/sound/max98095.h': Permission denied
install: cannot create regular file `/usr/include/sound/memalloc.h': Permission denied
install: cannot create regular file `/usr/include/sound/minors.h': Permission denied
install: cannot create regular file `/usr/include/sound/mixer_oss.h': Permission denied
install: cannot create regular file `/usr/include/sound/mpu401.h': Permission denied
install: cannot create regular file `/usr/include/sound/opl3.h': Permission denied
install: cannot create regular file `/usr/include/sound/opl4.h': Permission denied
install: cannot create regular file `/usr/include/sound/pcm-indirect.h': Permission denied
install: cannot create regular file `/usr/include/sound/pcm.h': Permission denied
install: cannot create regular file `/usr/include/sound/pcm_oss.h': Permission denied
install: cannot create regular file `/usr/include/sound/pcm_params.h': Permission denied
install: cannot create regular file `/usr/include/sound/pt2258.h': Permission denied
install: cannot create regular file `/usr/include/sound/pxa2xx-lib.h': Permission denied
install: cannot create regular file `/usr/include/sound/rawmidi.h': Permission denied
install: cannot create regular file `/usr/include/sound/s3c24xx_uda134x.h': Permission denied
install: cannot create regular file `/usr/include/sound/saif.h': Permission denied
install: cannot create regular file `/usr/include/sound/sb.h': Permission denied
install: cannot create regular file `/usr/include/sound/sb16_csp.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_device.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_kernel.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_midi_emul.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_midi_event.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_oss.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_oss_legacy.h': Permission denied
install: cannot create regular file `/usr/include/sound/seq_virmidi.h': Permission denied
install: cannot create regular file `/usr/include/sound/sfnt_info.h': Permission denied
install: cannot create regular file `/usr/include/sound/sh_dac_audio.h': Permission denied
install: cannot create regular file `/usr/include/sound/sh_fsi.h': Permission denied
install: cannot create regular file `/usr/include/sound/snd_wavefront.h': Permission denied
install: cannot create regular file `/usr/include/sound/soc-dai.h': Permission denied
install: cannot create regular file `/usr/include/sound/soc-dapm.h': Permission denied
install: cannot create regular file `/usr/include/sound/soc.h': Permission denied
install: cannot create regular file `/usr/include/sound/soundfont.h': Permission denied
install: cannot create regular file `/usr/include/sound/sta32x.h': Permission denied
install: cannot create regular file `/usr/include/sound/tea575x-tuner.h': Permission denied
install: cannot create regular file `/usr/include/sound/tea6330t.h': Permission denied
install: cannot create regular file `/usr/include/sound/timer.h': Permission denied
install: cannot create regular file `/usr/include/sound/tlv.h': Permission denied
install: cannot create regular file `/usr/include/sound/tlv320aic32x4.h': Permission denied
install: cannot create regular file `/usr/include/sound/tlv320aic3x.h': Permission denied
install: cannot create regular file `/usr/include/sound/tlv320dac33-plat.h': Permission denied
install: cannot create regular file `/usr/include/sound/tpa6130a2-plat.h': Permission denied
install: cannot create regular file `/usr/include/sound/trident.h': Permission denied
install: cannot create regular file `/usr/include/sound/uda134x.h': Permission denied
install: cannot create regular file `/usr/include/sound/uda1380.h': Permission denied
install: cannot create regular file `/usr/include/sound/util_mem.h': Permission denied
install: cannot create regular file `/usr/include/sound/version.h': Permission denied
install: cannot create regular file `/usr/include/sound/vx_core.h': Permission denied
install: cannot create regular file `/usr/include/sound/wavefront.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm1250-ev1.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm2000.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm5100.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm8903.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm8904.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm8955.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm8960.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm8962.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm8993.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm8996.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm9081.h': Permission denied
install: cannot create regular file `/usr/include/sound/wm9090.h': Permission denied
install: cannot create regular file `/usr/include/sound/wss.h': Permission denied
install: cannot create regular file `/usr/include/sound/ymfpci.h': Permission denied
make: *** [install-headers] Error 1

---

### Post by Pand5461 on 2012-03-24
By default, your user doesn't have the rights to write anywhere but their home folder. So, in order to install something system-wide you should run 'make install' with administrator privileges, that is

sudo make install.

---

### Post by Brizlitman on 2012-03-25
Of course! Why didn't I think of that. I've done that but i'm now trying to access the alsamixer:

brizlinux@Vishnu:~/Realtek/alsa-driver-1.0.25$ alsamixer
cannot open mixer: No such file or directory
I realise that this is the wrong command, so what would be the correct one?

---

### Post by Pand5461 on 2012-03-25
This is the right command. Can you see your sound card in lspci output? Do you have alsa-base.conf in your /etc/modprobe.d?

---

### Post by Brizlitman on 2012-03-25
Yes, alsa-base.conf is in /etc/modprobe.d
Here is the output of lspci:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 5f)
15:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
15:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
15:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
15:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

---

### Post by Pand5461 on 2012-03-25
Try
```
 gpasswd -a <your_username> audio
```
(maybe needs sudo)

---

