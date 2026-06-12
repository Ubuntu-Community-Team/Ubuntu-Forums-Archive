---
title: "USB Video Class (UVC) Kernel Problems"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by nswint on 2007-09-23
I'm having problems using my Pansonic PV-GS19 as a webcam using USB as I previously did on other linux distros.  I plug it in and it is immediately recognized.

[21504.331810] usb 2-3: new full speed USB device using ohci_hcd and address 4
[21504.551929] usb 2-3: configuration #1 chosen from 1 choice
[21505.243706] uvcvideo: Found UVC 1.00 device DVC (04da:2318)
[21505.247750] usbcore: registered new interface driver uvcvideo
[21505.247756] USB Video Class driver (v0.1.0)


It was added as /dev/video2


ls -latr /dev/video?
crw-rw---- 1 root video 81, 0 2007-09-23 15:40 /dev/video0
crw-rw---- 1 root video 81, 1 2007-09-23 15:40 /dev/video1
crw-rw---- 1 root video 81, 2 2007-09-23 21:37 /dev/video2


When I start up camorama to use the device I get a nasty beep and a syslog wall to the console
It also happens using gyachi and ekiga.  Any suggestions?  Do I need to submit this to ubuntu developers?

Message from syslogd@hashem at Sun Sep 23 21:41:38 2007 ...
hashem kernel: [21738.239305] CR2: 0000000000000090


Sep 23 21:41:38 hashem kernel: [21555.691903]  <1>Unable to handle kernel NULL pointer dereference at 0000000000000090 RIP: 
Sep 23 21:41:38 hashem kernel: [21738.238653] PGD 12ff8067 PUD 12ff9067 PMD 0 
Sep 23 21:41:38 hashem kernel: [21738.238660] CPU 0 
Sep 23 21:41:38 hashem kernel: [21738.238662] Modules linked in: uvcvideo jfs xfs reiserfs ext2 hfs hfsplus ntfs isofs udf snd_bt_sco hci_usb nfs lockd sunrpc nls_iso8859_1 nls_cp437 vfat fat binfmt_misc rfcomm l2cap bluetooth ppdev fglrx(P) dev_acpi pcc_acpi tc1100_wmi sony_acpi ac video asus_acpi backlight battery container dock button sbs i2c_ec af_packet it87 hwmon_vid i2c_isa eeprom lp fuse bt878 snd_bt87x snd_atiixp snd_ac97_codec joydev xpad tuner snd_seq_dummy ac97_bus snd_pcm_oss snd_mixer_oss tvaudio snd_seq_oss bttv x10_cm19a snd_usb_audio snd_usb_lib gspca video_buf ir_common usbhid usblp snd_hwdep hid snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_seq_device compat_ioctl32 i2c_algo_bit snd_pcm snd_timer snd btcx_risc soundcore i2c_piix4 parport_pc parport tveeprom videodev v4l2_common v4l1_compat serio_raw snd_page_alloc k8temp pcspkr i2c_core psmouse shpchp pci_hotplug tsdev evdev ext3 jbd mbcache sg sd_mod ide_cd cdrom usb_storage 8139too ata_generic libusual floppy 8139cp mii ehci_hcd s
Sep 23 21:41:38 hashem kernel: ta_sil atiixp ohci_hcd usbcore libata scsi_mod generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb cfbcopyarea cfbimgblt cfbfillrect capability commoncap
Sep 23 21:41:38 hashem kernel: [21738.238734] Pid: 1415, comm: camorama Tainted: P      2.6.20-16-generic #2
Sep 23 21:41:38 hashem kernel: [21738.238737] RIP: 0010:[_end+135347728/2130485360]  [_end+135347728/2130485360] :uvcvideo:__uvc_find_control+0x0/0x70
Sep 23 21:41:38 hashem kernel: [21738.238745] RSP: 0018:ffff810027cdf630  EFLAGS: 00010292
Sep 23 21:41:38 hashem kernel: [21738.238749] RAX: ffff8100061e8800 RBX: 00000000c0445624 RCX: ffff810027cdf768
Sep 23 21:41:38 hashem kernel: [21738.238752] RDX: ffff810027cdf680 RSI: 0000000000980900 RDI: 0000000000000000
Sep 23 21:41:38 hashem kernel: [21738.238756] RBP: ffff810027cdf680 R08: ffffffff88747ef0 R09: 00000000000000ff
Sep 23 21:41:38 hashem kernel: [21738.238759] R10: 0000000000000000 R11: 0000000000000206 R12: ffff810075542048
Sep 23 21:41:38 hashem kernel: [21738.238763] R13: 0000000000980900 R14: ffff810075542048 R15: ffff81000b7aa158
Sep 23 21:41:38 hashem kernel: [21738.238767] FS:  00002b5231fc46e0(0000) GS:ffffffff8054e000(0000) knlGS:00000000f0bfdb90
Sep 23 21:41:38 hashem kernel: [21738.238770] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Sep 23 21:41:38 hashem kernel: [21738.238772] CR2: 0000000000000090 CR3: 00000000350ca000 CR4: 00000000000006e0
Sep 23 21:41:38 hashem kernel: [21738.238776] Process camorama (pid: 1415, threadinfo ffff810027cde000, task ffff8100064dd180)
Sep 23 21:41:38 hashem kernel: [21738.238778] Stack:  ffffffff88749e3e 00000000c0445624 ffff810027cdf768 ffff810075542048
Sep 23 21:41:38 hashem kernel: [21738.238786]  ffff810027cdf768 ffff810075542048 ffffffff8874a80a 0000001a01010000
Sep 23 21:41:38 hashem kernel: [21738.238791]  000000000000001a 0000000000000000 0000000000000001 ffff810027cdf708
Sep 23 21:41:38 hashem kernel: [21738.238795] Call Trace:
Sep 23 21:41:38 hashem kernel: [21738.238800]  [_end+135347886/2130485360] :uvcvideo:uvc_find_control+0x2e/0xc0
Sep 23 21:41:38 hashem kernel: [21738.238815]  [_end+135350394/2130485360] :uvcvideo:uvc_query_v4l2_ctrl+0x2a/0x1f0
Sep 23 21:41:38 hashem kernel: [21738.238834]  [_end+135340814/2130485360] :uvcvideo:uvc_v4l2_do_ioctl+0x3ae/0xe40
Sep 23 21:41:38 hashem kernel: [21738.238845]  [_end+135346579/2130485360] :uvcvideo:uvc_set_video_ctrl+0x103/0x110
Sep 23 21:41:38 hashem kernel: [21738.238860]  [_end+135339872/2130485360] :uvcvideo:uvc_v4l2_do_ioctl+0x0/0xe40
Sep 23 21:41:38 hashem kernel: [21738.238871]  [_end+129556969/2130485360] :v4l1_compat:get_v4l_control+0x29/0xe0
Sep 23 21:41:38 hashem kernel: [21738.238895]  [_end+129560192/2130485360] :v4l1_compat:v4l_compat_translate_ioctl+0xbe0/0x1d60
Sep 23 21:41:38 hashem kernel: [21738.238901]  [_end+135339872/2130485360] :uvcvideo:uvc_v4l2_do_ioctl+0x0/0xe40
Sep 23 21:41:38 hashem kernel: [21738.238941]  [get_page_from_freelist+936/1392] get_page_from_freelist+0x3a8/0x570
Sep 23 21:41:38 hashem kernel: [21738.238968]  [__alloc_pages+99/784] __alloc_pages+0x63/0x310
Sep 23 21:41:38 hashem kernel: [21738.238987]  [__handle_mm_fault+1462/2736] __handle_mm_fault+0x5b6/0xab0
Sep 23 21:41:38 hashem kernel: [21738.239010]  [thread_return+0/245] thread_return+0x0/0xf5
Sep 23 21:41:38 hashem kernel: [21738.239017]  [find_get_page+41/96] find_get_page+0x29/0x60
Sep 23 21:41:38 hashem kernel: [21738.239023]  [task_rq_lock+76/144] task_rq_lock+0x4c/0x90
Sep 23 21:41:38 hashem kernel: [21738.239028]  [task_rq_lock+76/144] task_rq_lock+0x4c/0x90
Sep 23 21:41:38 hashem kernel: [21738.239047]  [remove_wait_queue+25/96] remove_wait_queue+0x19/0x60
Sep 23 21:41:38 hashem kernel: [21738.239059]  [__wake_up_common+68/128] __wake_up_common+0x44/0x80
Sep 23 21:41:38 hashem kernel: [21738.239072]  [__wake_up+67/112] __wake_up+0x43/0x70
Sep 23 21:41:38 hashem kernel: [21738.239077]  [__d_lookup+133/288] __d_lookup+0x85/0x120
Sep 23 21:41:38 hashem kernel: [21738.239091]  [do_lookup+116/528] do_lookup+0x74/0x210
Sep 23 21:41:38 hashem kernel: [21738.239100]  [dput+47/368] dput+0x2f/0x170
Sep 23 21:41:38 hashem kernel: [21738.239107]  [__link_path_walk+3179/3520] __link_path_walk+0xc6b/0xdc0
Sep 23 21:41:38 hashem kernel: [21738.239112]  [zone_statistics+52/128] zone_statistics+0x34/0x80
Sep 23 21:41:38 hashem kernel: [21738.239118]  [get_page_from_freelist+936/1392] get_page_from_freelist+0x3a8/0x570
Sep 23 21:41:38 hashem kernel: [21738.239137]  [link_path_walk+208/240] link_path_walk+0xd0/0xf0
Sep 23 21:41:38 hashem kernel: [21738.239157]  [_end+135343338/2130485360] :uvcvideo:uvc_v4l2_do_ioctl+0xd8a/0xe40
Sep 23 21:41:38 hashem kernel: [21738.239172]  [kmem_cache_zalloc+216/256] kmem_cache_zalloc+0xd8/0x100
Sep 23 21:41:38 hashem kernel: [21738.239190]  [_end+129627639/2130485360] :videodev:video_usercopy+0x177/0x240
Sep 23 21:41:38 hashem kernel: [21738.239196]  [_end+135339872/2130485360] :uvcvideo:uvc_v4l2_do_ioctl+0x0/0xe40
Sep 23 21:41:38 hashem kernel: [21738.239223]  [do_filp_open+45/64] do_filp_open+0x2d/0x40
Sep 23 21:41:38 hashem kernel: [21738.239235]  [do_ioctl+105/160] do_ioctl+0x69/0xa0
Sep 23 21:41:38 hashem kernel: [21738.239242]  [vfs_ioctl+674/736] vfs_ioctl+0x2a2/0x2e0
Sep 23 21:41:38 hashem kernel: [21738.239255]  [sys_ioctl+108/176] sys_ioctl+0x6c/0xb0
Sep 23 21:41:38 hashem kernel: [21738.239267]  [system_call+126/131] system_call+0x7e/0x83
Sep 23 21:41:38 hashem kernel: [21738.239286] 
Sep 23 21:41:38 hashem kernel: [21738.239288] 
Sep 23 21:41:38 hashem kernel: [21738.239288] Code: 44 8b 9f 90 00 00 00 45 85 db 74 5d 48 8b bf 98 00 00 00 45 
Sep 23 21:41:38 hashem kernel: [21738.239303]  RSP <ffff810027cdf630>


lsusb -v

Bus 002 Device 004: ID 04da:2318 Panasonic (Matsushita) 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 Common Class
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x04da Panasonic (Matsushita)
  idProduct          0x2318 
  bcdDevice            1.00
  iManufacturer           1 Panasonic
  iProduct                2 DVC
  iSerial                 3 d148a050
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          258
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               4 Web-Camera
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              4 Web-Camera
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength           39
        dwClockFrequency       13.500000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          2
        iTerminal               6 Camera
        wObjectiveFocalLengthMin    100
        wObjectiveFocalLengthMax   1000
        wOcularFocalLength          100
        bControlSize                  2
        bmControls           0x00000200
          Zoom (Absolute)
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          1
        bSourceID               1
        iTerminal               7 USB
    Interface Descriptor:
      bLength                 9
bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              8 VideoStreamingInterface
      VideoStreaming Interface Descriptor:
        bLength                            14
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormarts                        1
        wTotalLength                    34560
        bEndPointAddress                    0
        bmInfo                              2
        bTerminalLink                       0
        bStillCaptureMethod                 0
        bTriggerSupport                     0
        bTriggerUsage                       1
        bControlSize                        1
        bmaControls( 0)                    11
      VideoStreaming Interface Descriptor:
        bLength                            11
        bDescriptorType                    36
        bDescriptorSubtype                  6 (FORMAT_MJPEG)
        bFormatIndex                        1
        bNumFrameDescriptors                1
        bFlags                              0
          Fixed-size samples: No
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x02
          Interlaced stream or variable: No
          Fields per frame: 2 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                   786432
        dwMaxBitRate                  3932160
        dwMaxVideoFrameBufferSize       32768
        dwDefaultFrameInterval         666667
        bFrameIntervalType                  0
dwMinFrameInterval             666667
        dwMaxFrameInterval             666667
        dwFrameIntervalStep                 0
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     0 (Unspecified)
        bTransferCharacteristics            0 (Unspecified)
        bMatrixCoefficients                 0 (Unspecified)
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              8 VideoStreamingInterface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         2
      bInterfaceCount         2
      bFunctionClass          1 Audio
      bFunctionSubClass       1 Control Device
      bFunctionProtocol       0 
      iFunction               2 DVC
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
 bcdADC               1.00
        wTotalLength           30
        bInCollection           1
        baInterfaceNr( 0)       3
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               1
        iTerminal               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           2
        bDelay                  2 frames
        wFormatTag              1 PCM
 AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        16000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
Device Status:     0x0001
  Self Powered

---

