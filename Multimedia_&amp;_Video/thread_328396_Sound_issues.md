---
title: "Sound issues"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by JParkus on 2006-12-30
Run ulsamixer i get 
parkus@parkus:~$ulsamixer
bash: ulsamixer: command not found
parkus@parkus:~$ sudo ulsamixer
Password:
sudo: ulsamixer: command not found

what i did have work to open ulsamixer was
sudo modprobe snd_es18xx isapnp=0 port=0x220 mpu_port=0x330 dma1=1 dma2=5 irq=5 fm_port=0x388
then it told me to save the changes with
echo options [module-name] [module-options] >> /etc/modprobe.d/[module-name]

i restarted my computer and now if i give the modprobe command it says 

WARNING: /etc/modprobe.d/alsa-base.save line 28: ignoring bad line starting with '^g'
WARNING: /etc/modprobe.d/alsa-base.save line 29: ignoring bad line starting with '^x'
WARNING: /etc/modprobe.d/alsa-base.save line 28: ignoring bad line starting with '^g'
WARNING: /etc/modprobe.d/alsa-base.save line 29: ignoring bad line starting with '^x'
FATAL: Error inserting snd (/lib/modules/2.6.15-27-386/kernel/sound/core/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.15-27-386/kernel/sound/core/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.15-27-386/kernel/sound/core/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.15-27-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.15-27-386/kernel/sound/core/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-27-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_opl3_lib (/lib/modules/2.6.15-27-386/kernel/sound/drivers/opl3/snd-opl3-lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: /etc/modprobe.d/alsa-base.save line 28: ignoring bad line starting with '^g'
WARNING: /etc/modprobe.d/alsa-base.save line 29: ignoring bad line starting with '^x'
WARNING: /etc/modprobe.d/alsa-base.save line 28: ignoring bad line starting with '^g'
WARNING: /etc/modprobe.d/alsa-base.save line 29: ignoring bad line starting with '^x'
FATAL: Error inserting snd (/lib/modules/2.6.15-27-386/kernel/sound/core/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-27-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.15-27-386/kernel/sound/core/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_es18xx (/lib/modules/2.6.15-27-386/kernel/sound/isa/snd-es18xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
parkus@parkus:~$

lspci shows
0000:00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
0000:00:03.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:00:04.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)


i have onboard sound
ESS ES1869A

what do i do now

---

### Post by Stemp on 2006-12-30
ulsamixer ? are you talking about alsamixer ? or about something I don't know ?

---

