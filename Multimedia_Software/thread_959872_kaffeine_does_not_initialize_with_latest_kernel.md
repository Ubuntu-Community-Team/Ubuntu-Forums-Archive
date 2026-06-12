---
title: "kaffeine does not initialize with latest kernel"
date: 2008-10-26
forum: Multimedia Software
---

### Post by aprete on 2008-10-26
I just upgraded my kernel under Hardy Heron from 2.6.24-19 to 2.6.24-21.  Now kaffeine doesn't initialize.  System monitor shows two instances of kaffeine, both are "sleeping" and I have to kill the processes to get them out.  I'm trying to use a Pinnacle PCTV HD Pro Stick 801e.  Using the old kernel, kaffeine initializes but doesn't show me the digital TV option.  I realize that support for this device is new and I figured I needed the latest kernel to use it.  kaffeine is at the highest level supported by Synaptic Package Manager.

Thanks for your help.

---

### Post by kostkon on 2008-10-26
> **aprete said:**
> I just upgraded my kernel under Hardy Heron from 2.6.24-19 to 2.6.24-21.  Now kaffeine doesn't initialize.  System monitor shows two instances of kaffeine, both are "sleeping" and I have to kill the processes to get them out.  I'm trying to use a Pinnacle PCTV HD Pro Stick 801e.  Using the old kernel, kaffeine initializes but doesn't show me the digital TV option.  I realize that support for this device is new and I figured I needed the latest kernel to use it.  kaffeine is at the highest level supported by Synaptic Package Manager.

Thanks for your help.
Try running *Kaffeine* from the command line and see what error messages you get. You can then post them here.

---

### Post by aprete on 2008-10-28
> **kostkon said:**
> Try running *Kaffeine* from the command line and see what error messages you get. You can then post them here.
Not much to see in the terminal:

kbuildsycoca running...
DCOP Cleaning up dead connections.

But, lots of stuff ends up in dmesg after I start kaffeine.  Looks like something program-checked.  I'm not an Intel programmer so I'm not sure what it all means.  I hope I got the important messages:

[   93.093047] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   93.113282] xc5000: firmware read 12332 bytes.
[   93.113285] xc5000: firmware upload
[   93.113302] BUG: unable to handle kernel paging request at virtual address 00030000
[   93.113306] printing eip: 00030000 *pde = 00000000 
[   93.113311] Oops: 0000 [#1] SMP 
[   93.113314] Modules linked in: ipv6 binfmt_misc af_packet rfcomm l2cap bluetooth ppdev acpi_cpufreq cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video output sbs sbshc dock container battery iptable_filter ip_tables x_tables ac joydev analog sbp2 lp xc5000 s5h1411 snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm dvb_usb_dib0700 dib7000p snd_page_alloc dib7000m snd_util_mem dvb_usb snd_hwdep dvb_core dib3000mc dibx000_common dib0070 snd_seq_dummy snd_seq_oss dv1394 raw1394 snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd emu10k1_gp gameport nvidia(P) soundcore i2c_core intel_agp button agpgart iTCO_wdt iTCO_vendor_support shpchp pci_hotplug evdev parport_pc parport pcspkr ext2 mbcache sr_mod cdrom sg sd_mod usbhid hid usb_storage libusual pata_jmicron ata_piix pata_acpi floppy ohci1394 ieee1394 ata_generic ahci libata scsi_mod r8169 ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   93.113393] 
[   93.113396] Pid: 6478, comm: kdvb-ad-0-fe-0 Tainted: P        (2.6.24-21-generic #1)
[   93.113399] EIP: 0060:[<00030000>] EFLAGS: 00010246 CPU: 1
[   93.113404] EIP is at 0x30000
[   93.113406] EAX: f8b1cc97 EBX: 00030000 ECX: 00000000 EDX: 00000000
[   93.113409] ESI: 00000000 EDI: f8e1a000 EBP: f7fb5340 ESP: f61d9ef0
[   93.113411]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[   93.113414] Process kdvb-ad-0-fe-0 (pid: 6478, ti=f61d8000 task=f61da5c0 task.ti=f61d8000)
[   93.113416] Stack: f8d5accb f8d5b561 0000302c 00000019 df8df808 f7fb5340 f8b354da df8df808 
[   93.113423]        f7fb5340 f8e1a001 000000be df8df808 f8b354da 00000019 df8d0003 f61d9f31 
[   93.113430]        0000f503 00000000 df8df800 df8df800 f8b3558c 00000000 f8b35827 00000001 
[   93.113436] Call Trace:
[   93.113439]  [<f8d5accb>] xc_load_fw_and_init_tuner+0x19b/0x2b0 [xc5000]
[   93.113453]  [<f8b354da>] s5h1411_writereg+0x5a/0xb0 [s5h1411]
[   93.113465]  [<f8b354da>] s5h1411_writereg+0x5a/0xb0 [s5h1411]
[   93.113477]  [<f8b3558c>] s5h1411_i2c_gate_ctrl+0x5c/0x90 [s5h1411]
[   93.113484]  [<f8b35827>] s5h1411_softreset+0x57/0x60 [s5h1411]
[   93.113497]  [<f8d5ae1f>] xc5000_init+0x3f/0x80 [xc5000]
[   93.113504]  [<f8ade0ef>] dvb_usb_fe_wakeup+0x2f/0x40 [dvb_usb]
[   93.113515]  [<f8af2c4b>] dvb_frontend_init+0x2b/0x70 [dvb_core]
[   93.113537]  [<f8af477f>] dvb_frontend_thread+0x5f/0x300 [dvb_core]
[   93.113558]  [<c0123f70>] complete+0x40/0x60
[   93.113568]  [<f8af4720>] dvb_frontend_thread+0x0/0x300 [dvb_core]
[   93.113583]  [<c0140842>] kthread+0x42/0x70
[   93.113587]  [<c0140800>] kthread+0x0/0x70
[   93.113594]  [<c0105667>] kernel_thread_helper+0x7/0x10
[   93.113605]  =======================
[   93.113606] Code:  Bad EIP value.
[   93.113609] EIP: [<00030000>] 0x30000 SS:ESP 0068:f61d9ef0
[   93.113615] ---[ end trace 5914581914bf19c0 ]---

---

### Post by aprete on 2008-10-29
I'm narrowing the problem down, but I still don't have a solution.  The problem is in the firmware file, dvb-fe-xc5000-1.1.fw.  When I delete it, kaffeine comes up, but the tuner stick doesn't receive any video because the above file is needed (dmesg shows "upload failed" message).  I guess I need a newer version of the firmware file.  I'll keep digging.

---

### Post by aprete on 2008-11-01
Upgraded to Ubuntu 8.10, it's a step backwards.  Now kaffeine doesn't show the digital TV option any more.

---

### Post by xc3RnbFO8P on 2008-11-01
> Upgraded to Ubuntu 8.10, it's a step backwards. Now kaffeine doesn't show the digital TV option any more.
I would make a fresh install of 8.10.
This card is supported now in kernel 2.6.27:
[http://www.heise-online.co.uk/open/Kernel-Log-Linux-2-6-27-Released--/features/111671/8]("http://www.heise-online.co.uk/open/Kernel-Log-Linux-2-6-27-Released--/features/111671/8")

---

### Post by AlanR8 on 2008-11-01
Try VLC instead......

---

### Post by aprete on 2008-11-01
> **Ringi said:**
> I would make a fresh install of 8.10.
This card is supported now in kernel 2.6.27:
[http://www.heise-online.co.uk/open/Kernel-Log-Linux-2-6-27-Released--/features/111671/8]("http://www.heise-online.co.uk/open/Kernel-Log-Linux-2-6-27-Released--/features/111671/8")Did a fresh install today to get to that level kernel.

---

### Post by aprete on 2008-11-01
I re-booted, went into the v4l-dvb directory and did a sudo make load.  The little green light on the stick went on (good sign).  I checked dmesg and all looked good, no program check this time.  Kaffeine comes up with the digital TV option now.  But still no audio and no video.  DVB --> Channels shows no channels in the list, and when I press "Start Scan" the button just stays down and nothing happens.  I can press the button again to make it pop back up.

BTW the stick is connected to cable TV with unscrambled NTSC, ATSC, and QAM channels.

---

### Post by SylvainGuiriec on 2008-11-02
Hi there,

I am french and my english remained very poor, sorry. As poor as my Linux skills ;)

Could you write all the steps needed to run "Pinnacle PCTV pro stick 801e" under unbuntu with all the dependencies needed (i.e. kernel, packages, ...) ?

I will be very helpful.

Thank you very much all,

Sylvain

---

### Post by aprete on 2008-11-03
> **AlanR8 said:**
> Try VLC instead......VLC is a great program, but I don't know (yet) how to use it with a tuner.

---

### Post by aprete on 2008-11-08
Installed dvbscan and created a channels.conf file.  The scan facility in Kaffeine doesn't work for me.  Now I'm wondering where to put channels.conf so that kaffeine sees it.

---

### Post by aprete on 2009-01-05
> **SylvainGuiriec said:**
> Hi there,

I am french and my english remained very poor, sorry. As poor as my Linux skills ;)

Could you write all the steps needed to run "Pinnacle PCTV pro stick 801e" under unbuntu with all the dependencies needed (i.e. kernel, packages, ...) ?

I will be very helpful.

Thank you very much all,

SylvainBonjour Sylvain, votre anglais est beau, mon français est mauvais :D

I finally got this working with kaffeine.  Instead of repeating all I did, I will refer you to here:  [http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_(801e)#Making_it_Work](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_(801e)#Making_it_Work)

If it still doesn't work, be sure to upgrade to the latest kernel and the latest version of v4l-dvb.

Bonne Chance

---

