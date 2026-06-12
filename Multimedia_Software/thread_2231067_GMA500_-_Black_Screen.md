---
title: "GMA500 - Black Screen"
date: 2014-06-23
forum: Multimedia Software
---

### Post by sam83 on 2014-06-23
Hi all,
I have an Intel N2600 Board with the GMA3600 video hardware.
The board has a 7" LCD Display (800x480 resolution) attached on the LVDS connector.

I installed Ubuntu 14.04 64-bit successfully, but when the OS boots, after loading the drm and gma500_gfx module the display goes completely black (with no backlight).
If I blacklist the modules, the display works with a resolution of 640x480 (which is not its native resolution and the graphics is a little weird).

I tried to modprobe the drm module with debug=6 and this is the result:
```

[   44.359499] [drm] Initialized drm 1.1.0 20060810
[  107.386640] [drm:psb_intel_opregion_setup], Public ACPI methods supported
[  107.386649] [drm:psb_intel_opregion_setup], ASLE supported
[  107.386698] gma500 0000:00:02.0: irq 45 for MSI/MSI-X
[  107.386725] [drm:psb_intel_init_bios], Using VBT from OpRegion: $VBT CEDARVIEW      d
[  107.386736] [drm:drm_mode_debug_printmodeline], Modeline 0:"800x480" 0 32000 800 840 968 1056 480 490 493 505 0x8 0xa
[  107.386748] [drm:parse_sdvo_device_mapping], No SDVO device info is found in VBT
[  107.386755] [drm:parse_edp], EDP timing in vbt t1_t3 2000 t8 10 t9 2000 t10 500 t11_t12 5000
[  107.386761] [drm:parse_edp], VBT reports EDP: Lane_count 1, Lane_rate 6, Bpp 18
[  107.386766] [drm:parse_edp], VBT reports EDP: VSwing  0, Preemph 0
[  107.404467] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[  107.405107] acpi device:26: registered as cooling_device5
[  107.405309] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input14
[  107.405783] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[  107.405791] [drm] No driver support for vblank timestamp query.
[  107.406472] [drm:cdv_intel_lvds_init], LVDS is not present in VBT
[  107.407295] [drm:cdv_intel_dp_i2c_init], i2c_init DPDDC-B
[  107.407861] [drm:cdv_intel_dp_aux_ch], dp_aux_ch timeout status 0x51440064
[  107.407871] [drm:cdv_intel_dp_i2c_aux_ch], aux_ch failed -110
[  107.408381] [drm:cdv_intel_dp_aux_ch], dp_aux_ch timeout status 0x51440064
[  107.408389] [drm:cdv_intel_dp_i2c_aux_ch], aux_ch failed -110
[  107.409347] [drm:cdv_intel_dp_i2c_init], i2c_init DPDDC-C
[  107.409356] [drm:cdv_intel_edp_panel_vdd_on], 
[  107.412076] [drm:cdv_intel_dp_i2c_aux_ch], aux_i2c nack
[  107.412444] [drm:cdv_intel_edp_panel_vdd_off], 
[  107.412460] [drm:cdv_intel_dp_init], cur t1_t3 2000 t8 10 t9 2000 t10 500 t11_t12 6
[  107.412470] [drm:cdv_intel_dp_init], panel power up delay 200, power down delay 50, power cycle delay 500
[  107.412478] [drm:cdv_intel_dp_init], backlight on delay 1, off delay 200
[  107.412485] [drm:cdv_intel_edp_panel_vdd_on], 
[  107.615926] [drm:cdv_intel_edp_panel_vdd_off], 
[  107.615936] [drm:cdv_intel_dp_init], DPCD: Rev=10 LN_Rate=a LN_CNT=82 LN_DOWNSP=40
[  107.615966] [drm:cdv_intel_edp_backlight_off], 
[  107.835617] [drm:cdv_intel_edp_panel_vdd_on], 
[  108.039617] [drm:cdv_intel_dp_link_down], 
[  108.063614] [drm:cdv_intel_edp_panel_vdd_off], 
[  108.063622] [drm:cdv_intel_edp_panel_off], 
[  108.063627] [drm:cdv_intel_edp_panel_off], PP_STATUS c0000008
[  108.823614] [drm:cdv_intel_edp_panel_off], Over
[  108.823635] gma500 0000:00:02.0: trying to get vblank count for disabled pipe 0
[  108.823996] gma500 0000:00:02.0: trying to get vblank count for disabled pipe 0
[  108.864331] [drm:cdv_intel_single_pipe_active], pipe enabled 0
[  108.924177] [drm:cdv_intel_single_pipe_active], pipe enabled 0
[  108.944040] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:7:VGA-1]
[  108.975610] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:7:VGA-1] disconnected
[  108.975621] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:9:DVI-D-1]
[  108.980080] [drm:drm_do_probe_ddc_edid], drm: skipping non-existent adapter intel drm HDMIB
[  108.980089] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:9:DVI-D-1] disconnected
[  108.980096] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:11:DP-1]
[  108.980602] [drm:cdv_intel_dp_aux_ch], dp_aux_ch timeout status 0x51440064
[  108.980607] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:11:DP-1] disconnected
[  108.980612] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:15:DVI-D-2]
[  108.985073] [drm:drm_do_probe_ddc_edid], drm: skipping non-existent adapter intel drm HDMIC
[  108.985082] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:15:DVI-D-2] disconnected
[  108.985088] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:17:eDP-1]
[  108.985093] [drm:cdv_intel_edp_panel_vdd_on], 
[  109.187918] [drm:cdv_dp_detect], DPCD: Rev=10 LN_Rate=a LN_CNT=82 LN_DOWNSP=40
[  109.189032] [drm:i2c_algo_dp_aux_xfer], dp_aux_xfer return 2
[  109.215606] [drm:i2c_algo_dp_aux_xfer], dp_aux_xfer return 2
[  109.215617] [drm:cdv_intel_edp_panel_vdd_off], 
[  109.216727] [drm:i2c_algo_dp_aux_xfer], dp_aux_xfer return 2
[  109.243304] [drm:i2c_algo_dp_aux_xfer], dp_aux_xfer return 2
[  109.243332] [drm:cdv_intel_edp_panel_vdd_off], 
[  109.243343] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:17:eDP-1] probed modes :
[  109.243349] [drm:drm_mode_debug_printmodeline], Modeline 20:"800x480" 60 32000 800 840 968 1056 480 490 493 505 0x48 0x9
[  109.243358] [drm:drm_mode_debug_printmodeline], Modeline 21:"800x480" 50 26660 800 840 968 1056 480 490 493 505 0x40 0x9
[  109.243366] [drm:drm_mode_debug_printmodeline], Modeline 22:"800x480" 40 21330 800 840 968 1056 480 490 493 505 0x40 0x9
[  109.243375] [drm:drm_setup_crtcs], 
[  109.243381] [drm:drm_enable_connectors], connector 7 enabled? no
[  109.243385] [drm:drm_enable_connectors], connector 9 enabled? no
[  109.243390] [drm:drm_enable_connectors], connector 11 enabled? no
[  109.243394] [drm:drm_enable_connectors], connector 15 enabled? no
[  109.243398] [drm:drm_enable_connectors], connector 17 enabled? yes
[  109.243403] [drm:drm_target_preferred], looking for cmdline mode on connector 17
[  109.243408] [drm:drm_target_preferred], looking for preferred mode on connector 17
[  109.243412] [drm:drm_target_preferred], found mode 800x480
[  109.243416] [drm:drm_setup_crtcs], picking CRTCs for 4096x4096 config
[  109.243423] [drm:drm_setup_crtcs], desired mode 800x480 set on crtc 4
[  109.251051] checking generic (7f800000 130000) vs hw (7f800000 7bf000)
[  109.251059] fb: conflicting fb hw usage psbdrmfb vs VESA VGA - removing generic driver
[  109.251134] Console: switching to colour dummy device 80x25
[  109.252060] fbcon: psbdrmfb (fb0) is primary device
[  109.252208] [drm:drm_crtc_helper_set_config], 
[  109.252213] [drm:drm_crtc_helper_set_config], [CRTC:3] [NOFB]
[  109.252228] [drm:cdv_intel_edp_backlight_off], 
[  109.471617] [drm:cdv_intel_edp_panel_vdd_on], 
[  109.675612] [drm:cdv_intel_edp_panel_vdd_off], 
[  109.675615] [drm:cdv_intel_edp_panel_off], 
[  109.675623] [drm:cdv_intel_single_pipe_active], pipe enabled 0
[  109.695478] [drm:cdv_intel_single_pipe_active], pipe enabled 0
[  109.715325] [drm:drm_crtc_helper_set_config], 
[  109.715331] [drm:drm_crtc_helper_set_config], [CRTC:4] [FB:25] #connectors=1 (x y) (0 0)
[  109.715340] [drm:drm_crtc_helper_set_config], crtc has no fb, full mode set
[  109.715343] [drm:drm_crtc_helper_set_config], modes are different, full mode set
[  109.715349] [drm:drm_mode_debug_printmodeline], Modeline 0:"" 0 0 0 0 0 0 0 0 0 0 0x0 0x0
[  109.715356] [drm:drm_mode_debug_printmodeline], Modeline 24:"800x480" 60 32000 800 840 968 1056 480 490 493 505 0x48 0x9
[  109.715359] [drm:drm_crtc_helper_set_config], encoder changed, full mode switch
[  109.715362] [drm:drm_crtc_helper_set_config], crtc changed, full mode switch
[  109.715366] [drm:drm_crtc_helper_set_config], [CONNECTOR:17:eDP-1] to [CRTC:4]
[  109.715369] [drm:drm_crtc_helper_set_config], attempting to set mode from userspace
[  109.715375] [drm:drm_mode_debug_printmodeline], Modeline 24:"800x480" 60 32000 800 840 968 1056 480 490 493 505 0x48 0x9
[  109.715385] [drm:cdv_intel_dp_mode_fixup], Display port link bw 0a lane count 1 clock 270000
[  109.715387] [drm:drm_crtc_helper_set_mode], [CRTC:4]
[  109.715390] [drm:cdv_intel_edp_backlight_off], 
[  109.931618] [drm:cdv_intel_edp_panel_off], 
[  109.931622] [drm:cdv_intel_edp_panel_vdd_on], 
[  110.135609] [drm:cdv_intel_edp_panel_vdd_off], 
[  110.135619] [drm:cdv_intel_single_pipe_active], pipe enabled 0
[  110.155481] [drm:drm_mode_debug_printmodeline], Modeline 26:"800x480" 60 270000 800 840 968 1056 480 490 493 505 0x48 0x9
[  110.159606] [drm:cdv_sb_write], 0x00008038: 0x0068a701 (before)
[  110.159609] [drm:cdv_sb_write], 0x00008038: 0x0068a701
[  110.175607] [drm:cdv_sb_write], 0x00008038: 0x0068a701 (after)
[  110.183607] [drm:cdv_dpll_set_clock_cdv], use their DPLL for pipe A/B
[  110.191607] [drm:cdv_sb_write], 0x00008030: 0x7e40421c (before)
[  110.191610] [drm:cdv_sb_write], 0x00008030: 0x7e40221c
[  110.207607] [drm:cdv_sb_write], 0x00008030: 0x7e40221c (after)
[  110.223607] [drm:cdv_sb_write], 0x00008028: 0x6200217f (before)
[  110.223610] [drm:cdv_sb_write], 0x00008028: 0x8500217f
[  110.239607] [drm:cdv_sb_write], 0x00008028: 0x8500217f (after)
[  110.255608] [drm:cdv_sb_write], 0x00008034: 0xc4080157 (before)
[  110.255611] [drm:cdv_sb_write], 0x00008034: 0x55000157
[  110.271611] [drm:cdv_sb_write], 0x00008034: 0x55000157 (after)
[  110.287611] [drm:cdv_sb_write], 0x0000803c: 0x45552000 (before)
[  110.287614] [drm:cdv_sb_write], 0x0000803c: 0x05551000
[  110.303612] [drm:cdv_sb_write], 0x0000803c: 0x05551000 (after)
[  110.319611] [drm:cdv_sb_write], 0x00002320: 0x001000c4 (before)
[  110.319614] [drm:cdv_sb_write], 0x00002320: 0x003000c4
[  110.335611] [drm:cdv_sb_write], 0x00002320: 0x003000c4 (after)
[  110.351611] [drm:cdv_sb_write], 0x00002420: 0x001000c4 (before)
[  110.351614] [drm:cdv_sb_write], 0x00002420: 0x003000c4
[  110.367611] [drm:cdv_sb_write], 0x00002420: 0x003000c4 (after)
[  110.367763] [drm:cdv_intel_crtc_mode_set], Mode for pipe B:
[  110.367770] [drm:drm_mode_debug_printmodeline], Modeline 24:"800x480" 60 32000 800 840 968 1056 480 490 493 505 0x48 0x9
[  110.407616] [drm:drm_crtc_helper_set_mode], [ENCODER:18:TMDS-18] set [MODE:24:800x480]
[  110.407620] [drm:cdv_intel_dp_mode_set], DP expected reg is 70000008
[  110.407622] [drm:cdv_intel_edp_panel_on], 
[  110.619805] [drm:cdv_intel_single_pipe_active], pipe enabled 2
[  110.679343] [drm:cdv_intel_dp_start_link_train], Link config
[  110.679547] [drm:cdv_intel_dp_start_link_train], Start train
[  110.679550] [drm:cdv_intel_dp_start_link_train], DP Link Train Set 0, Link_config a, 1
[  110.680456] [drm:cdv_intel_dp_start_link_train], DP Link status 0, 0, 80, 0, 1, 0
[  110.680460] [drm:cdv_intel_dp_start_link_train], DP Link Train Set 1, Link_config a, 1
[  110.681364] [drm:cdv_intel_dp_start_link_train], DP Link status 1, 0, 80, 0, 1, 0
[  110.681366] [drm:cdv_intel_dp_start_link_train], PT1 train is done
[  110.681368] [drm:cdv_intel_dp_complete_link_train], 
[  110.681371] [drm:cdv_intel_dp_complete_link_train], DP Link Train Set 1, Link_config a, 1
[  110.683069] [drm:cdv_intel_dp_complete_link_train], DP Link status 1, 0, 81, 0, 5, 0
[  110.683072] [drm:cdv_intel_dp_complete_link_train], DP Link Train Set 9, Link_config a, 1
[  110.684770] [drm:cdv_intel_dp_complete_link_train], DP Link status 1, 0, 81, 0, 9, 0
[  110.684774] [drm:cdv_intel_dp_complete_link_train], DP Link Train Set 11, Link_config a, 1
[  110.686471] [drm:cdv_intel_dp_complete_link_train], DP Link status 7, 0, 81, 1, 9, 0
[  110.686473] [drm:cdv_intel_dp_complete_link_train], PT2 train is done
[  110.686677] [drm:cdv_intel_edp_backlight_on], 
[  110.987619] [drm:drm_crtc_helper_set_config], Setting connector DPMS state to on
[  110.987625] [drm:drm_crtc_helper_set_config], 	[CONNECTOR:17:eDP-1] set DPMS on
[  111.027320] [drm:cdv_intel_single_pipe_active], pipe enabled 2
[  111.067091] Console: switching to colour frame buffer device 100x30
[  111.079346] gma500 0000:00:02.0: fb0: psbdrmfb frame buffer device
[  111.079352] gma500 0000:00:02.0: registered panic notifier
[  111.079370] [drm] Initialized gma500 1.0.0 2011-06-06 for 0000:00:02.0 on minor 0

```

It seems that the video hardware is detected correctly, however when I load the module the screen seems to power off, it goes completely black with backlight off.

Other informations that could be useful:
```

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/drm/card0/card0-eDP-1/status 
connected

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/drm/card0/card0-eDP-1/enabled 
enabled

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/drm/card0/card0-eDP-1/modes 
800x480
800x480
800x480

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/drm/card0/card0-eDP-1/dpms 
On

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/drm/card0/card0-eDP-1/power/runtime_enabled 
disabled

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/drm/card0/card0-eDP-1/power/control 
auto

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/drm/card0/card0-eDP-1/power/runtime_usage 
0

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/drm/card0/card0-eDP-1/power/runtime_active_time 
0

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/drm/card0/card0-eDP-1/power/runtime_suspended_time 
0

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/drm/card0/card0-eDP-1/power/async 
disabled

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/backlight/acpi_video0/actual_brightness 
10

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/backlight/acpi_video0/bl_power 
0

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/backlight/acpi_video0/brightness 
10

$ cat /sys/devices/pci0000\:00/0000\:00\:02.0/backlight/acpi_video0/max_brightness 
10

```

Do you have any suggestions on how could I make the display work? 
I don't need hw acceleration, I would only like to make the display work at its native resolution of 800x480...

Thanks for any help/support.


Samuele.

---

### Post by Rob Sayer on 2014-06-28
Are you sure you loaded the gma500_gfx driver and not the gma500?  I believe they're different.  gma500_gfx is for the Poulsbo card and gma500 is for the cedarview one.

My netbook has the 2600/3600 cpu/gpu and the driver is gma500:

```
~$ lspci -nnk | grep -i vga -A3 | grep 'in use'
	Kernel driver in use: gma500
```

Also, I believe the drivers for poulsbo/cedarview only work properly in 32 bit.  I've always had 32 bit on my cedarview netbook but I tried 64 bit xubuntu 14.04 recently.

It mostly worked OK but I got a system error message sometimes on boot having to do with xorg.  I decided it'd just be easier and quicker to reinstall 32 bit than to diagnose it properly.  But it seems like quite a coincidence that xorg was involved, and I haven't got any error messages since I installed 32 bit.

Hopefully this helps .... I dunno though ....

---

### Post by darksid3r on 2014-08-07
I had the same issue with an embedded PC (Atom CPU) with a Poulsbo videocard. It seems to be an ACPI issue. Disabling ACPI functionality in BIOS fixes the problem.
I'm still investigating the exact cause.

---

