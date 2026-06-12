---
title: "Rosewill RNX-N180UBE"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by tylerwagler on 2010-09-21
I am having the hardest time getting this wireless adapter to work on either Ubuntu 10.04 Desktop x64 or Ubuntu 10.04 Server x86.  The device comes with a linux driver provided here:

[http://rosewill.com/Mgnt/Uploads2/AttachmentForProduct/rnx-n180ube_linux_v2.6.x.zip](http://rosewill.com/Mgnt/Uploads2/AttachmentForProduct/rnx-n180ube_linux_v2.6.x.zip)

I downloaded the driver, extracted it, made it, then did a
sudo insmod 8712u.ko
all without problem.  The device still does not work. Any help would be greatly appreciated, and I can answer any questions about my setup.

lsusb returns this and other unrelated crap:
```
 Bus 001 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. 

```

iwconfig returns this:
```
 wlan1     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lsmod returns this(the top one being the module i put in there:
```


Module                  Size  Used by
8712u                 301393  0 
hidp                   11083  0 
hid                    67032  1 hidp
rfcomm                 33421  4 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  17 hidp,rfcomm,bnep
btusb                  10925  2 
bluetooth              49892  10 hidp,rfcomm,sco,bnep,l2cap,btusb
joydev                  8708  0 
binfmt_misc             6587  1 
snd_hda_codec_si3054     3396  1 
snd_hda_codec_realtek   203310  1 
ppdev                   5259  0 
arc4                    1153  2 
iwlagn                105694  0 
snd_hda_intel          21941  3 
iwlcore               105922  1 iwlagn
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
uvcvideo               56990  0 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
r8192s_usb            345975  0 
mac80211              205146  2 iwlagn,iwlcore
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63245  0 
video                  17375  0 
nvidia               9961216  41 
vga16fb                11385  1 
ricoh_mmc               2923  0 
cfg80211              126517  3 iwlagn,iwlcore,mac80211
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  2 iwlcore,sdhci
output                  1871  1 video
intel_agp              24119  0 
vgastate                8961  1 vga16fb
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 nvidia,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ahci                   32200  2 
r8169                  34076  0 
mii                     4381  1 r8169

```

dmesg returns a whole bunch of relevant crap that i don't know what it means: 
```
 [   77.666062]  [<c0440f50>] ? clear_port_feature+0x50/0x60
[   77.666062]  [<c0444465>] hub_events+0x1f5/0x510
[   77.666062]  [<c016797f>] ? finish_wait+0x4f/0x70
[   77.666062]  [<c04447ba>] hub_thread+0x3a/0x140
[   77.666062]  [<c0167810>] ? autoremove_wake_function+0x0/0x50
[   77.666062]  [<c0444780>] ? hub_thread+0x0/0x140
[   77.666062]  [<c0167584>] kthread+0x74/0x80
[   77.666062]  [<c0167510>] ? kthread+0x0/0x80
[   77.666062]  [<c0104087>] kernel_thread_helper+0x7/0x10
[   77.666062] rtl819xU:=============>wlan driver to be removed
[   77.666062] 
[   77.676500] rtl819xU:wlan driver removed
[   77.676501] 
[   82.488235] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   82.623070] usb 1-4: configuration #1 chosen from 1 choice
[   82.623579] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[   82.623581] ==>RtInPipes:3  
[   82.623584] ==>RtOutPipes:4  6  13  
[   82.623588] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[   82.623590] 1  1  0  0  2  2  2  2  2  
[   82.859411] Dot11d_Init()
[   95.140959] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.
[   95.204834] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   95.241178] iwlagn 0000:02:00.0: loaded firmware version 228.61.2.24
[   95.457405] Registered led device: iwl-phy0::radio
[   95.457456] Registered led device: iwl-phy0::assoc
[   95.457503] Registered led device: iwl-phy0::RX
[   95.457547] Registered led device: iwl-phy0::TX
[   95.513507] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   95.527775] rtl819xU: --->FirmwareDownload92S()
[   95.527781] 
[   95.527791] usb 1-4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   95.531850] rtl819xU:request firmware fail!
[   95.531853] 
[   95.532248] rtl819xU:Firmware Download Fail!!a
[   95.532251] 
[   95.544415] rtl819xU: --->FirmwareDownload92S()
[   95.544419] 
[   95.544427] usb 1-4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   95.547938] rtl819xU:request firmware fail!
[   95.547941] 
[   95.548424] rtl819xU:Firmware Download Fail!!a
[   95.548427] 
[   95.548433] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   95.548436] 
[   95.864273] usb 7-2: new full speed USB device using uhci_hcd and address 2
[   96.042197] usb 7-2: configuration #1 chosen from 1 choice
[   96.059149] Bluetooth: Core ver 2.15
[   96.061114] NET: Registered protocol family 31
[   96.061117] Bluetooth: HCI device and connection manager initialized
[   96.061120] Bluetooth: HCI socket layer initialized
[   96.062746] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   96.062877] usbcore: registered new interface driver btusb
[   96.088746] Bluetooth: L2CAP ver 2.14
[   96.088749] Bluetooth: L2CAP socket layer initialized
[   96.094538] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   96.094541] Bluetooth: BNEP filters: protocol multicast
[   96.103131] Bridge firewalling registered
[   96.113505] Bluetooth: SCO (Voice Link) ver 0.6
[   96.113508] Bluetooth: SCO socket layer initialized
[   96.213338] Bluetooth: RFCOMM TTY layer initialized
[   96.213345] Bluetooth: RFCOMM socket layer initialized
[   96.213348] Bluetooth: RFCOMM ver 1.11
[   96.712639] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   96.847056] cfg80211: Found new beacon on frequency: 5745 MHz (Ch 149) on phy0
[  103.787010] wlan0: deauthenticating from 00:18:18:94:18:71 by local choice (reason=3)
[  103.794280] wlan0: direct probe to AP 00:17:5a:8f:1c:b1 (try 1)
[  103.992061] wlan0: direct probe to AP 00:17:5a:8f:1c:b1 (try 2)
[  104.192159] wlan0: direct probe to AP 00:17:5a:8f:1c:b1 (try 3)
[  104.392082] wlan0: direct probe to AP 00:17:5a:8f:1c:b1 timed out
[  123.961161] CE: hpet increasing min_delta_ns to 15000 nsec
[  140.535674] usbcore: registered new interface driver r871x_usb_drv
[  144.922977] usb 1-4: USB disconnect, address 3
[  144.953159] rtl819xU:=============>wlan driver to be removed
[  144.953165] 
[  144.964065] rtl819xU:wlan driver removed
[  144.964067] 
[  147.572180] usb 2-1: new high speed USB device using ehci_hcd and address 5
[  147.711366] usb 2-1: configuration #1 chosen from 1 choice
[  147.728153] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[  147.728155] ==>RtInPipes:3  
[  147.728158] ==>RtOutPipes:4  6  13  
[  147.728162] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[  147.728164] 1  1  0  0  2  2  2  2  2  
[  148.005486] Dot11d_Init()
[  148.008020] ------------[ cut here ]------------
[  148.008039] WARNING: at /build/buildd/linux-2.6.32/fs/proc/generic.c:590 proc_register+0x103/0x1e0()
[  148.008045] Hardware name: HP Pavilion dv6500 Notebook PC    
[  148.008050] proc_dir_entry 'rtl819xU/wlan1' already registered
[  148.008055] Modules linked in: 8712u hidp hid rfcomm sco bridge stp bnep l2cap btusb bluetooth joydev binfmt_misc snd_hda_codec_si3054 snd_hda_codec_realtek ppdev arc4 iwlagn snd_hda_intel iwlcore snd_hda_codec snd_hwdep uvcvideo snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd fbcon tileblit font bitblit softcursor r8192s_usb(C) mac80211 videodev v4l1_compat psmouse video nvidia(P) vga16fb ricoh_mmc cfg80211 sdhci_pci sdhci led_class output intel_agp vgastate serio_raw soundcore snd_page_alloc agpgart lp parport ohci1394 ieee1394 ahci r8169 mii
[  148.008203] Pid: 30, comm: khubd Tainted: P        WC 2.6.32-24-generic #43-Ubuntu
[  148.008208] Call Trace:
[  148.008220]  [<c014c4a2>] warn_slowpath_common+0x72/0xa0
[  148.008231]  [<c02521a3>] ? proc_register+0x103/0x1e0
[  148.008240]  [<c02521a3>] ? proc_register+0x103/0x1e0
[  148.008249]  [<c014c51b>] warn_slowpath_fmt+0x2b/0x30
[  148.008258]  [<c02521a3>] proc_register+0x103/0x1e0
[  148.008267]  [<c0252799>] create_proc_entry+0x59/0xa0
[  148.008299]  [<f83859f5>] rtl8192_proc_init_one+0x25/0x460 [r8192s_usb]
[  148.008312]  [<c04c7cbf>] ? register_netdev+0x3f/0x50
[  148.008337]  [<f839d39e>] rtl8192_usb_probe+0x148/0x191 [r8192s_usb]
[  148.008348]  [<c044b860>] usb_probe_interface+0xc0/0x180
[  148.008358]  [<c0260b87>] ? sysfs_create_link+0x17/0x20
[  148.008371]  [<c03e7cfd>] really_probe+0x4d/0x140
[  148.008381]  [<c03ee60e>] ? pm_runtime_barrier+0x4e/0xc0
[  148.008390]  [<c03e7e2c>] driver_probe_device+0x3c/0x60
[  148.008398]  [<c03e7f29>] __device_attach+0x49/0x60
[  148.008408]  [<c03e7053>] bus_for_each_drv+0x53/0x80
[  148.008416]  [<c03e7ff2>] device_attach+0x72/0x90
[  148.008424]  [<c03e7ee0>] ? __device_attach+0x0/0x60
[  148.008433]  [<c03e6e95>] bus_probe_device+0x25/0x40
[  148.008441]  [<c03e5914>] device_add+0x274/0x430
[  148.008451]  [<c034d3b4>] ? kobject_set_name_vargs+0x64/0x70
[  148.008472]  [<c044a197>] usb_set_configuration+0x417/0x690
[  148.008482]  [<c0452bbe>] generic_probe+0x3e/0xb0
[  148.008491]  [<c0260b87>] ? sysfs_create_link+0x17/0x20
[  148.008499]  [<c044a4c4>] usb_probe_device+0x24/0x30
[  148.008507]  [<c03e7cfd>] really_probe+0x4d/0x140
[  148.008516]  [<c03ee60e>] ? pm_runtime_barrier+0x4e/0xc0
[  148.008524]  [<c03e7e2c>] driver_probe_device+0x3c/0x60
[  148.008531]  [<c03e7f29>] __device_attach+0x49/0x60
[  148.008540]  [<c03e7053>] bus_for_each_drv+0x53/0x80
[  148.008548]  [<c03e7ff2>] device_attach+0x72/0x90
[  148.008555]  [<c03e7ee0>] ? __device_attach+0x0/0x60
[  148.008564]  [<c03e6e95>] bus_probe_device+0x25/0x40
[  148.008573]  [<c03e5914>] device_add+0x274/0x430
[  148.008583]  [<c0442e9d>] usb_new_device+0x5d/0xc0
[  148.008592]  [<c04438cf>] hub_port_connect_change+0x45f/0x850
[  148.008601]  [<c0449145>] ? usb_control_msg+0xd5/0x130
[  148.008610]  [<c0440f50>] ? clear_port_feature+0x50/0x60
[  148.008619]  [<c0444465>] hub_events+0x1f5/0x510
[  148.008629]  [<c016797f>] ? finish_wait+0x4f/0x70
[  148.008638]  [<c04447ba>] hub_thread+0x3a/0x140
[  148.008646]  [<c0167810>] ? autoremove_wake_function+0x0/0x50
[  148.008654]  [<c0444780>] ? hub_thread+0x0/0x140
[  148.008662]  [<c0167584>] kthread+0x74/0x80
[  148.008670]  [<c0167510>] ? kthread+0x0/0x80
[  148.008679]  [<c0104087>] kernel_thread_helper+0x7/0x10
[  148.008685] ---[ end trace e83cd24330bc19b6 ]---
[  148.033441] rtl819xU: --->FirmwareDownload92S()
[  148.033444] 
[  148.033450] usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  148.034978] rtl819xU:request firmware fail!
[  148.034979] 
[  148.035247] rtl819xU:Firmware Download Fail!!a
[  148.035249] 
[  148.042686] rtl819xU: --->FirmwareDownload92S()
[  148.042689] 
[  148.042695] usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  148.046403] rtl819xU:request firmware fail!
[  148.046406] 
[  148.046935] rtl819xU:Firmware Download Fail!!a
[  148.046937] 
[  148.046941] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  148.046943] 
[  148.059431] rtl819xU: --->FirmwareDownload92S()
[  148.059432] 
[  148.059438] usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  148.085053] rtl819xU:request firmware fail!
[  148.085055] 
[  148.085835] rtl819xU:Firmware Download Fail!!a
[  148.085836] 
[  148.093057] rtl819xU: --->FirmwareDownload92S()
[  148.093060] 
[  148.093064] usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  148.110110] rtl819xU:request firmware fail!
[  148.110112] 
[  148.111426] rtl819xU:Firmware Download Fail!!a
[  148.111428] 
[  148.111432] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  148.111433] 
[  154.489907] usb 2-1: USB disconnect, address 5
[  154.521519] rtl819xU:=============>wlan driver to be removed
[  154.521522] 
[  154.532041] rtl819xU:wlan driver removed
[  154.532043] 
[  155.892193] usb 2-2: new high speed USB device using ehci_hcd and address 6
[  156.028111] usb 2-2: configuration #1 chosen from 1 choice
[  156.029471] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[  156.029477] ==>RtInPipes:3  
[  156.029485] ==>RtOutPipes:4  6  13  
[  156.029495] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[  156.029500] 1  1  0  0  2  2  2  2  2  
[  156.286712] Dot11d_Init()
[  156.288863] ------------[ cut here ]------------
[  156.288880] WARNING: at /build/buildd/linux-2.6.32/fs/proc/generic.c:590 proc_register+0x103/0x1e0()
[  156.288887] Hardware name: HP Pavilion dv6500 Notebook PC    
[  156.288892] proc_dir_entry 'rtl819xU/wlan1' already registered
[  156.288897] Modules linked in: 8712u hidp hid rfcomm sco bridge stp bnep l2cap btusb bluetooth joydev binfmt_misc snd_hda_codec_si3054 snd_hda_codec_realtek ppdev arc4 iwlagn snd_hda_intel iwlcore snd_hda_codec snd_hwdep uvcvideo snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd fbcon tileblit font bitblit softcursor r8192s_usb(C) mac80211 videodev v4l1_compat psmouse video nvidia(P) vga16fb ricoh_mmc cfg80211 sdhci_pci sdhci led_class output intel_agp vgastate serio_raw soundcore snd_page_alloc agpgart lp parport ohci1394 ieee1394 ahci r8169 mii
[  156.289049] Pid: 30, comm: khubd Tainted: P        WC 2.6.32-24-generic #43-Ubuntu
[  156.289054] Call Trace:
[  156.289067]  [<c014c4a2>] warn_slowpath_common+0x72/0xa0
[  156.289077]  [<c02521a3>] ? proc_register+0x103/0x1e0
[  156.289086]  [<c02521a3>] ? proc_register+0x103/0x1e0
[  156.289094]  [<c014c51b>] warn_slowpath_fmt+0x2b/0x30
[  156.289103]  [<c02521a3>] proc_register+0x103/0x1e0
[  156.289113]  [<c0252799>] create_proc_entry+0x59/0xa0
[  156.289145]  [<f83859f5>] rtl8192_proc_init_one+0x25/0x460 [r8192s_usb]
[  156.289157]  [<c04c7cbf>] ? register_netdev+0x3f/0x50
[  156.289182]  [<f839d39e>] rtl8192_usb_probe+0x148/0x191 [r8192s_usb]
[  156.289193]  [<c044b860>] usb_probe_interface+0xc0/0x180
[  156.289203]  [<c0260b87>] ? sysfs_create_link+0x17/0x20
[  156.289218]  [<c03e7cfd>] really_probe+0x4d/0x140
[  156.289228]  [<c03ee60e>] ? pm_runtime_barrier+0x4e/0xc0
[  156.289237]  [<c03e7e2c>] driver_probe_device+0x3c/0x60
[  156.289246]  [<c03e7f29>] __device_attach+0x49/0x60
[  156.289256]  [<c03e7053>] bus_for_each_drv+0x53/0x80
[  156.289264]  [<c03e7ff2>] device_attach+0x72/0x90
[  156.289272]  [<c03e7ee0>] ? __device_attach+0x0/0x60
[  156.289281]  [<c03e6e95>] bus_probe_device+0x25/0x40
[  156.289290]  [<c03e5914>] device_add+0x274/0x430
[  156.289298]  [<c044a167>] ? usb_set_configuration+0x3e7/0x690
[  156.289307]  [<c044a197>] usb_set_configuration+0x417/0x690
[  156.289318]  [<c0452bbe>] generic_probe+0x3e/0xb0
[  156.289327]  [<c0260b87>] ? sysfs_create_link+0x17/0x20
[  156.289335]  [<c044a4c4>] usb_probe_device+0x24/0x30
[  156.289343]  [<c03e7cfd>] really_probe+0x4d/0x140
[  156.289351]  [<c03ee60e>] ? pm_runtime_barrier+0x4e/0xc0
[  156.289359]  [<c03e7e2c>] driver_probe_device+0x3c/0x60
[  156.289367]  [<c03e7f29>] __device_attach+0x49/0x60
[  156.289376]  [<c03e7053>] bus_for_each_drv+0x53/0x80
[  156.289384]  [<c03e7ff2>] device_attach+0x72/0x90
[  156.289391]  [<c03e7ee0>] ? __device_attach+0x0/0x60
[  156.289401]  [<c03e6e95>] bus_probe_device+0x25/0x40
[  156.289409]  [<c03e5914>] device_add+0x274/0x430
[  156.289419]  [<c0442e9d>] usb_new_device+0x5d/0xc0
[  156.289428]  [<c04438cf>] hub_port_connect_change+0x45f/0x850
[  156.289437]  [<c0449145>] ? usb_control_msg+0xd5/0x130
[  156.289446]  [<c0440f50>] ? clear_port_feature+0x50/0x60
[  156.289455]  [<c0444465>] hub_events+0x1f5/0x510
[  156.289465]  [<c016797f>] ? finish_wait+0x4f/0x70
[  156.289473]  [<c04447ba>] hub_thread+0x3a/0x140
[  156.289481]  [<c0167810>] ? autoremove_wake_function+0x0/0x50
[  156.289490]  [<c0444780>] ? hub_thread+0x0/0x140
[  156.289498]  [<c0167584>] kthread+0x74/0x80
[  156.289506]  [<c0167510>] ? kthread+0x0/0x80
[  156.289515]  [<c0104087>] kernel_thread_helper+0x7/0x10
[  156.289521] ---[ end trace e83cd24330bc19b7 ]---
[  156.323072] rtl819xU: --->FirmwareDownload92S()
[  156.323077] 
[  156.323084] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  156.325950] rtl819xU:request firmware fail!
[  156.325952] 
[  156.326381] rtl819xU:Firmware Download Fail!!a
[  156.326383] 
[  156.335206] rtl819xU: --->FirmwareDownload92S()
[  156.335208] 
[  156.335218] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  156.340988] rtl819xU:request firmware fail!
[  156.340989] 
[  156.341185] rtl819xU:Firmware Download Fail!!a
[  156.341186] 
[  156.341189] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  156.341190] 
[  156.352683] rtl819xU: --->FirmwareDownload92S()
[  156.352685] 
[  156.352690] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  156.366163] rtl819xU:request firmware fail!
[  156.366165] 
[  156.367419] rtl819xU:Firmware Download Fail!!a
[  156.367421] 
[  156.374308] rtl819xU: --->FirmwareDownload92S()
[  156.374311] 
[  156.374316] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  156.387633] rtl819xU:request firmware fail!
[  156.387635] 
[  156.388474] rtl819xU:Firmware Download Fail!!a
[  156.388476] 
[  156.388479] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  156.388481] 
[  182.632837] Registered led device: iwl-phy0::radio
[  182.632888] Registered led device: iwl-phy0::assoc
[  182.632933] Registered led device: iwl-phy0::RX
[  182.632975] Registered led device: iwl-phy0::TX
[  182.668979] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  182.669411] wlan0: direct probe to AP 00:17:5a:8f:1c:b1 (try 1)
[  182.672423] wlan0: direct probe responded
[  182.672431] wlan0: authenticate with AP 00:17:5a:8f:1c:b1 (try 1)
[  182.675126] wlan0: authenticated
[  182.675168] wlan0: associate with AP 00:17:5a:8f:1c:b1 (try 1)
[  182.680102] wlan0: RX AssocResp from 00:17:5a:8f:1c:b1 (capab=0x431 status=0 aid=103)
[  182.680110] wlan0: associated
[  182.702626] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  182.702743] cfg80211: Calling CRDA for country: US
[  182.709950] cfg80211: Received country IE:
[  182.709957] cfg80211: Regulatory domain: US
[  182.709962] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  182.709969] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[  182.709974] cfg80211: CRDA thinks this should applied:
[  182.709979] cfg80211: Regulatory domain: US
[  182.709982] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  182.709989] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  182.709996] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  182.710002] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  182.710008] 	(5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  182.710015] 	(5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  182.710021] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  182.710026] cfg80211: We intersect both of these and get:
[  182.710030] cfg80211: Regulatory domain: 98
[  182.710034] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  182.710041] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  182.710052] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[  182.710058] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[  182.710064] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[  182.710070] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[  182.710077] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[  182.710082] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[  182.710089] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[  182.710094] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[  182.710101] cfg80211: Leaving channel 5745 MHz intact on phy0 - no rule found in band on Country IE
[  182.710107] cfg80211: Leaving channel 5765 MHz intact on phy0 - no rule found in band on Country IE
[  182.710113] cfg80211: Leaving channel 5785 MHz intact on phy0 - no rule found in band on Country IE
[  182.710119] cfg80211: Leaving channel 5805 MHz intact on phy0 - no rule found in band on Country IE
[  182.710125] cfg80211: Leaving channel 5825 MHz intact on phy0 - no rule found in band on Country IE
[  182.710135] cfg80211: Current regulatory domain updated by AP to: US
[  182.710139] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  182.710146] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  182.712682] wlan0: deauthenticating from 00:17:5a:8f:1c:b1 by local choice (reason=3)
[  185.948974] rtl819xU: --->FirmwareDownload92S()
[  185.948981] 
[  185.948991] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  185.955558] rtl819xU:request firmware fail!
[  185.955561] 
[  185.956522] rtl819xU:Firmware Download Fail!!a
[  185.956525] 
[  185.967942] rtl819xU: --->FirmwareDownload92S()
[  185.967944] 
[  185.967948] usb 2-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  185.972878] rtl819xU:request firmware fail!
[  185.972879] 
[  185.973069] rtl819xU:Firmware Download Fail!!a
[  185.973070] 
[  185.973073] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  185.973074] 
[  193.248044] wlan0: no IPv6 routers present
[  194.215598] lo: Disabled Privacy Extensions
[  199.490093] wlan0: deauthenticating from 00:18:18:94:18:70 by local choice (reason=3)
[  199.529448] wlan0: direct probe to AP 00:17:5a:8f:1c:b0 (try 1)
[  199.536567] wlan0: direct probe responded
[  199.536578] wlan0: authenticate with AP 00:17:5a:8f:1c:b0 (try 1)
[  199.538485] wlan0: authenticated
[  199.538533] wlan0: associate with AP 00:17:5a:8f:1c:b0 (try 1)
[  199.736202] wlan0: associate with AP 00:17:5a:8f:1c:b0 (try 2)
[  199.936074] wlan0: associate with AP 00:17:5a:8f:1c:b0 (try 3)
[  200.136060] wlan0: association with AP 00:17:5a:8f:1c:b0 timed out
[  206.167012] wlan0: direct probe to AP 00:17:5a:8f:1c:b0 (try 1)
[  206.170663] wlan0: direct probe responded
[  206.170666] wlan0: authenticate with AP 00:17:5a:8f:1c:b0 (try 1)
[  206.172492] wlan0: authenticated
[  206.172507] wlan0: associate with AP 00:17:5a:8f:1c:b0 (try 1)
[  206.176622] wlan0: RX AssocResp from 00:17:5a:8f:1c:b0 (capab=0x421 status=0 aid=106)
[  206.176625] wlan0: associated
[  210.556914] usb 2-2: USB disconnect, address 6
[  210.576570] rtl819xU:=============>wlan driver to be removed
[  210.576575] 
[  210.587199] rtl819xU:wlan driver removed
[  210.587202] 
[  327.308097] usb 1-4: new high speed USB device using ehci_hcd and address 4
[  327.443317] usb 1-4: configuration #1 chosen from 1 choice
[  327.444096] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[  327.444102] ==>RtInPipes:3  
[  327.444109] ==>RtOutPipes:4  6  13  
[  327.444119] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[  327.444124] 1  1  0  0  2  2  2  2  2  
[  327.695969] Dot11d_Init()
[  327.698552] ------------[ cut here ]------------
[  327.698570] WARNING: at /build/buildd/linux-2.6.32/fs/proc/generic.c:590 proc_register+0x103/0x1e0()
[  327.698577] Hardware name: HP Pavilion dv6500 Notebook PC    
[  327.698582] proc_dir_entry 'rtl819xU/wlan1' already registered
[  327.698587] Modules linked in: 8712u hidp hid rfcomm sco bridge stp bnep l2cap btusb bluetooth joydev binfmt_misc snd_hda_codec_si3054 snd_hda_codec_realtek ppdev arc4 iwlagn snd_hda_intel iwlcore snd_hda_codec snd_hwdep uvcvideo snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd fbcon tileblit font bitblit softcursor r8192s_usb(C) mac80211 videodev v4l1_compat psmouse video nvidia(P) vga16fb ricoh_mmc cfg80211 sdhci_pci sdhci led_class output intel_agp vgastate serio_raw soundcore snd_page_alloc agpgart lp parport ohci1394 ieee1394 ahci r8169 mii
[  327.698733] Pid: 30, comm: khubd Tainted: P        WC 2.6.32-24-generic #43-Ubuntu
[  327.698739] Call Trace:
[  327.698751]  [<c014c4a2>] warn_slowpath_common+0x72/0xa0
[  327.698761]  [<c02521a3>] ? proc_register+0x103/0x1e0
[  327.698770]  [<c02521a3>] ? proc_register+0x103/0x1e0
[  327.698779]  [<c014c51b>] warn_slowpath_fmt+0x2b/0x30
[  327.698787]  [<c02521a3>] proc_register+0x103/0x1e0
[  327.698797]  [<c0252799>] create_proc_entry+0x59/0xa0
[  327.698828]  [<f83859f5>] rtl8192_proc_init_one+0x25/0x460 [r8192s_usb]
[  327.698839]  [<c04c7cbf>] ? register_netdev+0x3f/0x50
[  327.698864]  [<f839d39e>] rtl8192_usb_probe+0x148/0x191 [r8192s_usb]
[  327.698875]  [<c044b860>] usb_probe_interface+0xc0/0x180
[  327.698884]  [<c0260b87>] ? sysfs_create_link+0x17/0x20
[  327.698898]  [<c03e7cfd>] really_probe+0x4d/0x140
[  327.698907]  [<c03ee60e>] ? pm_runtime_barrier+0x4e/0xc0
[  327.698916]  [<c03e7e2c>] driver_probe_device+0x3c/0x60
[  327.698925]  [<c03e7f29>] __device_attach+0x49/0x60
[  327.698934]  [<c03e7053>] bus_for_each_drv+0x53/0x80
[  327.698942]  [<c03e7ff2>] device_attach+0x72/0x90
[  327.698949]  [<c03e7ee0>] ? __device_attach+0x0/0x60
[  327.698958]  [<c03e6e95>] bus_probe_device+0x25/0x40
[  327.698967]  [<c03e5914>] device_add+0x274/0x430
[  327.698976]  [<c044a167>] ? usb_set_configuration+0x3e7/0x690
[  327.698985]  [<c044a197>] usb_set_configuration+0x417/0x690
[  327.698995]  [<c0452bbe>] generic_probe+0x3e/0xb0
[  327.699004]  [<c0260b87>] ? sysfs_create_link+0x17/0x20
[  327.699012]  [<c044a4c4>] usb_probe_device+0x24/0x30
[  327.699020]  [<c03e7cfd>] really_probe+0x4d/0x140
[  327.699029]  [<c03ee60e>] ? pm_runtime_barrier+0x4e/0xc0
[  327.699036]  [<c03e7e2c>] driver_probe_device+0x3c/0x60
[  327.699044]  [<c03e7f29>] __device_attach+0x49/0x60
[  327.699053]  [<c03e7053>] bus_for_each_drv+0x53/0x80
[  327.699060]  [<c03e7ff2>] device_attach+0x72/0x90
[  327.699067]  [<c03e7ee0>] ? __device_attach+0x0/0x60
[  327.699076]  [<c03e6e95>] bus_probe_device+0x25/0x40
[  327.699085]  [<c03e5914>] device_add+0x274/0x430
[  327.699095]  [<c0442e9d>] usb_new_device+0x5d/0xc0
[  327.699104]  [<c04438cf>] hub_port_connect_change+0x45f/0x850
[  327.699113]  [<c0147e47>] ? dequeue_entity+0x1a7/0x200
[  327.699122]  [<c0441233>] ? hub_port_status+0xb3/0x110
[  327.699131]  [<c0444465>] hub_events+0x1f5/0x510
[  327.699141]  [<c016797f>] ? finish_wait+0x4f/0x70
[  327.699149]  [<c04447ba>] hub_thread+0x3a/0x140
[  327.699157]  [<c0167810>] ? autoremove_wake_function+0x0/0x50
[  327.699166]  [<c0444780>] ? hub_thread+0x0/0x140
[  327.699174]  [<c0167584>] kthread+0x74/0x80
[  327.699182]  [<c0167510>] ? kthread+0x0/0x80
[  327.699191]  [<c0104087>] kernel_thread_helper+0x7/0x10
[  327.699197] ---[ end trace e83cd24330bc19b8 ]---
[  327.733441] rtl819xU: --->FirmwareDownload92S()
[  327.733444] 
[  327.733450] usb 1-4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  327.735230] rtl819xU:request firmware fail!
[  327.735231] 
[  327.735430] rtl819xU:Firmware Download Fail!!a
[  327.735432] 
[  327.743674] rtl819xU: --->FirmwareDownload92S()
[  327.743677] 
[  327.743682] usb 1-4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  327.747815] rtl819xU:request firmware fail!
[  327.747817] 
[  327.748049] rtl819xU:Firmware Download Fail!!a
[  327.748050] 
[  327.748054] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  327.748055] 
[  327.760170] rtl819xU: --->FirmwareDownload92S()
[  327.760171] 
[  327.760176] usb 1-4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  327.772996] rtl819xU:request firmware fail!
[  327.772997] 
[  327.773496] rtl819xU:Firmware Download Fail!!a
[  327.773497] 
[  327.780545] rtl819xU: --->FirmwareDownload92S()
[  327.780547] 
[  327.780552] usb 1-4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  327.794172] rtl819xU:request firmware fail!
[  327.794174] 
[  327.794740] rtl819xU:Firmware Download Fail!!a
[  327.794741] 
[  327.794744] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  327.794745] 
[  477.482317] CE: hpet increasing min_delta_ns to 22500 nsec
[  477.482427] CE: hpet increasing min_delta_ns to 33750 nsec

```

sudo lshw -C network:
```

 *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:1a:ef:11:0f:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

```

---

### Post by ianbrown75 on 2010-09-24
anyluck with this issue? i have rosewill 2t2r verison
RNX-easyN4
ieee 802.11 n 2.0 wireless Router

it worked for about three months, and now it does not.

---

### Post by miyagison on 2011-02-08
[https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455)

I have RNX-N180UBE and it worked perfectly for me. ~ Mark Post As Solved

---

### Post by henrytheindian on 2013-01-21
I have ubuntu 10.10 and the same wireless adapter but with rtl8192sfw.bin in lib/firmware/RTL819SU it still doesn't work. Can someone help me? I'm new to linux and without getting the computer connected to the internet it's a paperweight.

---

### Post by Smallwheels on 2013-06-04
I just bought one of these because someone with Linux said it was just a plug and play installation for him. I have plugged the unit into the machine and the LED lights don't come on. I don't even know if the LEDs are there. I just don't see anything lighting up. There was no new item in the desktop acknowledging that a new piece of hardware was added. I tried restarting the machine with the unit installed and nothing changed. 

What do I need to do to get this thing working? I am typing this from a different computer that is connected to the internet. It is a Mac Book. The Ubuntu 10.04 32 bit machine is in a place where it is impossible to connect to the internet to download things from the repositories. Please let me know how to proceed.

---

