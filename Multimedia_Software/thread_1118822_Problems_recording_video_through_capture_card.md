---
title: "Problems recording video through capture card"
date: 2009-04-07
forum: Multimedia Software
---

### Post by horde on 2009-04-07
I have an Hauppauge ImpactVCB (BT878 chip using bttv driver) that I've been trying to use to capture video. As all the forums suggest, I've tried to set it up in xawtv first. Using xawtv 3.95, the display screen goes blue in "grabdisplay" capture mode.  Only in "overlay" mode have I've managed to get a picture displayed.  I've read, though, that you can't capture in that mode; trying to record I get "grabbing: not supported [try -noxv switch?]".

Running "xawtv -noxv -nodga" (I've seen others with ATI and NVidia vid cards complain of needing to use both switches) and trying to record in "overlay" mode gives the following error:
> ioctl: VIDIOC_REQBUFS(count=16;type=VIDEO_CAPTURE;memory=MMAP): Resource temporarily unavailable
ioctl: VIDIOC_QBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): Device or resource busy
ioctl: VIDIOC_STREAMON(int=1): Device or resource busy
ioctl VIDIOC_STREAMOFF: Invalid argument

Switching to "grabdisplay" mode gives the same output as above.

Trying record in "grabdisplay" mode gives the following:
> "v4l2: read: Device or resource busy" 
and then output as above. 

Switching back to "overlay" mode gives no errors.

Additionally, TVTime only displays a blue screen and outputs:
> videoinput: Can't read frame. Error was: Invalid argument (0).
videoinput: Driver refuses to stop streaming: Invalid argument.
videoinput: Can't free frame 0: Device or resource busy
videoinput: Can't free frame 1: Device or resource busy
videoinput: Can't free frame 2: Device or resource busy
videoinput: Can't free frame 3: Device or resource busy
videoinput: Driver refuses to start streaming: Device or resource busy.

So I'm wondering if it has to do with the "Device or resource busy" message. "lsof" says no other apps are using /dev/video0, but then again I don't know what else that error could point to.  Or maybe this is a v4l problem?

Incidentally, I'm running Kubuntu Hardy (2.6.24-22-generic kernel) on an old Athlon XP 2400+ CPU with an ATI Radeon 9200 GPU.  I had to add modprobe option "options bttv card=82 tuner=4" to get the capture card detected as an Osprey 100 (as recommended in the Zoneminder wiki: [http://www.zoneminder.com/wiki/index.php/Hauppauge_ImpactVCB](http://www.zoneminder.com/wiki/index.php/Hauppauge_ImpactVCB)).

I'm pretty sure the capture card's being detected correctly as, with certain settings, I'm getting a picture, "dmesg|grep bttv" gives:
```
[   55.017137] bttv: driver version 0.9.17 loaded                                        
[   55.017145] bttv: using 8 buffers with 2080k (520 pages) each for capture             
[   55.017443] bttv: Bt8xx card found (0).                                               
[   55.017503] bttv0: Bt878 (rev 17) at 0000:01:0a.0, irq: 19, latency: 32, mmio: 0xe4000000
[   55.017530] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb    
[   55.017535] bttv0: using: Osprey 100/150 (878) [card=82,insmod option]                   
[   55.017573] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]                    
[   55.046903] bttv0: tuner absent                                                          
[   55.209164] bttv0: registered device video0                                              
[   55.209222] bttv0: registered device vbi0                                                
[   55.209253] bttv0: PLL: 28636363 => 35468950 .. ok                                       
[11288.284018] bttv0: PLL can sleep, using XTAL (28636363).                                 
[11422.631684] bttv0: PLL: 28636363 => 35468950 .. ok                                       
[11529.324015] bttv0: PLL can sleep, using XTAL (28636363).                                 
[12084.410216] bttv0: PLL: 28636363 => 35468950 .. ok                                       
[12084.443483] kernel BUG at /build/buildd/linux-2.6.24/drivers/media/video/bt8xx/bttv-driver.c:2501!
[12084.443492] Modules linked in: radeon drm af_packet binfmt_misc rfcomm l2cap bluetooth nfsd auth_rpcgss exportfs ppdev ipv6 cpufreq_ondemand cpufreq_powersave cpufreq_conservative cpufreq_userspace cpufreq_stats freq_table video output dock container sbs sbshc battery nfs lockd nfs_acl sunrpc iptable_filter ip_tables x_tables aes_i586 dm_crypt dm_mod ac sbp2 lp snd_mpu401 snd_mpu401_uart evdev analog gameport snd_intel8x0 snd_ac97_codec ac97_bus snd_bt87x snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy bt878 parport_pc parport bttv ir_common compat_ioctl32 i2c_algo_bit videobuf_dma_sg videobuf_core btcx_risc tveeprom videodev v4l2_common v4l1_compat snd_seq_oss snd_seq_midi snd_rawmidi serio_raw snd_seq_midi_event psmouse snd_seq snd_timer snd_seq_device button snd i2c_nforce2 soundcore snd_page_alloc shpchp pcspkr i2c_core nvidia_agp pci_hotplug agpgart ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_acpi ata_generic usbhid hid floppy pata_amd ohci1394 ieee1394 libata scsi_mod ehci_hcd ohci_hcd forcedeth usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse                                              
[12084.443616] EIP is at verify_window+0xa2/0x120 [bttv]                                                          
[12084.443700]  [<f8ae821c>] bttv_try_fmt+0x13c/0x170 [bttv]                                                      
[12084.443731]  [<f8aea41c>] bttv_do_ioctl+0x13bc/0x22c0 [bttv]                                                   
[12084.443872]  [<f8ae7e23>] bttv_ioctl+0x23/0x80 [bttv]                                                          
[12084.443890]  [<f8ae9060>] bttv_do_ioctl+0x0/0x22c0 [bttv]                                                      
[12084.444011] EIP: [<f8ae6ca2>] verify_window+0xa2/0x120 [bttv] SS:ESP 0068:e9fe1dc4                             
[12093.932580] kernel BUG at /build/buildd/linux-2.6.24/drivers/media/video/bt8xx/bttv-driver.c:2501!             
[12093.932589] Modules linked in: radeon drm af_packet binfmt_misc rfcomm l2cap bluetooth nfsd auth_rpcgss exportfs ppdev ipv6 cpufreq_ondemand cpufreq_powersave cpufreq_conservative cpufreq_userspace cpufreq_stats freq_table video output dock container sbs sbshc battery nfs lockd nfs_acl sunrpc iptable_filter ip_tables x_tables aes_i586 dm_crypt dm_mod ac sbp2 lp snd_mpu401 snd_mpu401_uart evdev analog gameport snd_intel8x0 snd_ac97_codec ac97_bus snd_bt87x snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy bt878 parport_pc parport bttv ir_common compat_ioctl32 i2c_algo_bit videobuf_dma_sg videobuf_core btcx_risc tveeprom videodev v4l2_common v4l1_compat snd_seq_oss snd_seq_midi snd_rawmidi serio_raw snd_seq_midi_event psmouse snd_seq snd_timer snd_seq_device button snd i2c_nforce2 soundcore snd_page_alloc shpchp pcspkr i2c_core nvidia_agp pci_hotplug agpgart ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_acpi ata_generic usbhid hid floppy pata_amd ohci1394 ieee1394 libata scsi_mod ehci_hcd ohci_hcd forcedeth usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse                                              
[12093.932713] EIP is at verify_window+0xa2/0x120 [bttv]                                                          
[12093.932797]  [<f8ae821c>] bttv_try_fmt+0x13c/0x170 [bttv]                                                      
[12093.932828]  [<f8aea41c>] bttv_do_ioctl+0x13bc/0x22c0 [bttv]                                                   
[12093.932965]  [<f8ae7e23>] bttv_ioctl+0x23/0x80 [bttv]                                                          
[12093.932982]  [<f8ae9060>] bttv_do_ioctl+0x0/0x22c0 [bttv]                                                      
[12093.933101] EIP: [<f8ae6ca2>] verify_window+0xa2/0x120 [bttv] SS:ESP 0068:dfb4bdc4                             
[13195.647893] bttv0: PLL can sleep, using XTAL (28636363).                                                       
[13305.468970] bttv0: PLL: 28636363 => 35468950 .. ok                                                             
[13342.618667] bttv0: SCERR @ 3505e014,bits: HSYNC SCERR*                                                         
[13342.658652] bttv0: SCERR @ 3505e014,bits: HSYNC SCERR*                                                         
[13342.698635] bttv0: SCERR @ 3505e014,bits: HSYNC SCERR*                                                         
[13342.738621] bttv0: SCERR @ 3505e014,bits: HSYNC SCERR*                                                         
[13342.778605] bttv0: SCERR @ 3505e014,bits: HSYNC SCERR*
[13342.818591] bttv0: SCERR @ 3505e014,bits: HSYNC SCERR*
[13342.858576] bttv0: SCERR @ 3505e014,bits: HSYNC SCERR*
[13342.898557] bttv0: SCERR @ 3505e014,bits: HSYNC SCERR*
[13342.938541] bttv0: SCERR @ 3505e014,bits: HSYNC SCERR*
[13342.978527] bttv0: SCERR @ 3505e014,bits: HSYNC SCERR*
[13343.018512] bttv0: SCERR @ 3505e014,bits: HSYNC SCERR*
[13343.058496] bttv0: SCERR @ 3505e014,bits: HSYNC SCERR*
[13343.088243] bttv0: timeout: drop=3186 irq=723032/723032, risc=3505e03c, bits: HSYNC
[13343.088526] bttv0: reset, reinitialize
[13343.088564] bttv0: PLL: 28636363 => 35468950 . ok
[13343.677219] bttv0: PLL can sleep, using XTAL (28636363).
[13343.915317] bttv0: PLL: 28636363 => 35468950 .. ok
[13446.425995] bttv0: PLL can sleep, using XTAL (28636363).
[13446.799492] bttv0: PLL: 28636363 => 35468950 .. ok
[13515.348950] bttv0: PLL can sleep, using XTAL (28636363).
[13515.677631] bttv0: PLL: 28636363 => 35468950 .. ok
[13603.123126] bttv0: PLL can sleep, using XTAL (28636363).
[13603.329495] bttv0: PLL: 28636363 => 35468950 .. ok
[13629.710086] bttv0: PLL can sleep, using XTAL (28636363).
[13629.875642] bttv0: PLL: 28636363 => 35468950 .. ok
```

and "lspci |grep -i bt878" gives:
> 01:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

I tested the card in WindowsXP and it worked as advertised, but I'd rather not have to boot into Windows...ever if possible!  After working on this for a week, though, I've completely exhausted my Linux expertise, so any ideas would be greatly appreciated!!

---

