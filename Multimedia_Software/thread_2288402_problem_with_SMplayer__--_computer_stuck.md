---
title: "problem with SMplayer  -- computer stuck"
date: 2015-07-27
forum: Multimedia Software
---

### Post by offir on 2015-07-27
I am using SMplayer to Watch movies and series

I have a problem with it

Whenever episode or movie reaches the last second
The player gets stuck
And sticking the computer
The computer is stuck with the last frame displayed

The only way out is to shut down the computer from the button on the chassis




i have ubuntu 15.04 with cairo dock

---

### Post by dino99 on 2015-07-27
maybe your logs will help to know what is going on (some missing codec(s) or bug somewhere)

---

### Post by Bucky Ball on 2015-07-27
Can't help with your problem but when the computer gets stuck, type control+alt+F1> login, then:

```
dmesg
```

See anything at the end of that output that might give a clue? To reboot without a hard shutdown:

```
sudo reboot -h now
```

That will restart the machine without a hard shutdown which could potentially damage hardware.

Another thing to try is to launch smplayer from a terminal. When it crashes, check the terminal for the error.

---

### Post by offir on 2015-07-27
> maybe your logs will help to know what is going on

How can I see the logs ? (More accurate Where)


> Can't help with your problem but when the computer gets stuck, type control+alt+F1> login, then:

The computer does not respond to anything
No Keyboard
No mouse

---

### Post by SeijiSensei on 2015-07-27
In SMPlayer, use Options > View Logs.  That will show the logs for smplayer and for mplayer/mpv.  If that doesn't provide any help, try looking at /var/log/syslog.

---

### Post by mc4man on 2015-07-27
You could try , (remove in order listed  below - 
remove ~/.config/smplayer/file_settings (the whole folder
remove ~/.config/smplayer/player_info.ini

Then see if anything changes in this regard.

If not then repeat the above but before testing again open smplayer > Options > Preferences > uncheck 'Remember settings for all files ...' & retest.

---

### Post by monkeybrain20122 on 2015-07-27
Perhaps upgrading Smplayer would help (if it is a Smplayer problem) [https://launchpad.net/~rvm/+archive/ubuntu/ppa](https://launchpad.net/~rvm/+archive/ubuntu/ppa)
If it doesn't fix it ask here [http://forum.smplayer.info/](http://forum.smplayer.info/)

---

### Post by offir on 2015-07-27
Here is the log 
Log begins hour and a half ago
Like what happened from the problem and back does not exist

```
[18:47:55:811] global_init
[18:47:55:811] global_init: config file: '/home/offir/.config/smplayer/smplayer.ini'
[18:47:55:812] Preferences::load
[18:47:55:812] AssStyles::load
[18:47:55:813] Preferences::load: config_version: 4, CURRENT_CONFIG_VERSION: 4
[18:47:55:813] Translator::loadCatalog: can't load qt_en_US from /usr/share/smplayer/translations
[18:47:55:813] Translator::loadCatalog: can't load qt_en_US from /usr/share/qt4/translations
[18:47:55:813] Translator::loadCatalog: successfully loaded smplayer_en_US from /usr/share/smplayer/translations
[18:47:55:813] This is SMPlayer v. 14.9.0 running on Linux
[18:47:55:813] Compiled with Qt v. 4.8.6, using 4.8.6
[18:47:55:813]  * application path: '/usr/bin'
[18:47:55:813]  * data path: '/usr/share/smplayer'
[18:47:55:813]  * translation path: '/usr/share/smplayer/translations'
[18:47:55:813]  * doc path: '/usr/share/doc/smplayer'
[18:47:55:813]  * themes path: '/usr/share/smplayer/themes'
[18:47:55:813]  * shortcuts path: '/usr/share/smplayer/shortcuts'
[18:47:55:813]  * config path: '/home/offir/.config/smplayer'
[18:47:55:813]  * ini path: '/home/offir/.config/smplayer'
[18:47:55:813]  * file for subtitles' styles: '/home/offir/.config/smplayer/styles.ass'
[18:47:55:813]  * current path: '/home/offir'
[18:47:55:813] SMPlayer::processArgs: arguments: 1
[18:47:55:813] SMPlayer::processArgs: 0 = smplayer
[18:47:55:813] SMPlayer::processArgs: files_to_play: count: 0
[18:47:55:813] SMPlayer::gui: changed working directory to app path
[18:47:55:813] SMPlayer::gui: current directory: /usr/bin
[18:47:55:814] Screen::setAutoHideCursor: 0
[18:47:55:814] Screen::setAutoHideCursor: 0
[18:47:55:821] Core::changeFileSettingsMethod: hash
[18:47:55:821] MplayerLayer::setRepaintBackground: 0
[18:47:55:821] Preferences::monitor_aspect_double
[18:47:55:821]  warning: monitor_aspect couldn't be parsed!
[18:47:55:821]  monitor_aspect set to 0
[18:47:55:851] Playlist::setModified: 0
[18:47:55:855] Playlist::loadSettings
[18:47:55:855] Playlist::addItem: '/media/offir/tv show/tv show/Falling Skies/3/Falling Skies 3x10 Brazil.mp4'
[18:47:55:855] Playlist::setModified: 0
[18:47:55:855] Playlist::updateView
[18:47:55:856] Playlist::updateView: name: 'Falling Skies 3x10 Brazil.mp4'
[18:47:55:865] Style name: 'gtk+'
[18:47:55:865] Style class name: 'QGtkStyle'
[18:47:55:874] Favorites::load
[18:47:55:875] Favorites::load
[18:47:55:875] TVList::parse_channels_conf
[18:47:55:875] VList::parse_channels_conf: /home/offir/.mplayer/channels.conf.ter doesn't exist
[18:47:55:875] TVList::parse_channels_conf: can't open /home/offir/.mplayer/channels.conf
[18:47:55:875] Favorites::load
[18:47:55:875] TVList::parse_channels_conf
[18:47:55:875] VList::parse_channels_conf: /home/offir/.mplayer/channels.conf.ter doesn't exist
[18:47:55:875] TVList::parse_channels_conf: can't open /home/offir/.mplayer/channels.conf
[18:47:55:895] BaseGui::initializeMenus
[18:47:55:926] BaseGui::initializeMenus
[18:47:55:926] BaseGui::updateRecents
[18:47:55:927] BaseGui::updateWidgets
[18:47:55:927] Core::changeUseAss: 1
[18:47:55:927] Core::changeSubVisilibity: 1
[18:47:55:927] Core::tellmp: 'sub_visibility 1'
[18:47:55:927] WARNING:  tellmp: no process running: sub_visibility 1
[18:47:55:927] Core::displayMessage
[18:47:55:928] BaseGui::setStayOnTop: 0
[18:47:55:928] BaseGui::setStayOnTop: nothing to do
[18:47:55:928] BaseGui::updateWidgets
[18:47:55:928] BaseGui::updateRecents
[18:47:55:939] BaseGui::initializeMenus
[18:47:55:939] BaseGui::updateRecents
[18:47:55:939] BaseGui::updateWidgets
[18:47:55:940] BaseGuiPlus::loadConfig
[18:47:55:940] DefaultGui::createStatusBar
[18:47:55:944] DefaultGui::createActions
[18:47:55:945] DefaultGui::createControlWidget
[18:47:55:945] DefaultGui::createControlWidgetMini
[18:47:55:946] AutohideWidget::installFilter: child name: "mplayerwindow" 
[18:47:55:946] AutohideWidget::installFilter: child name: "mplayerlayer" 
[18:47:55:946] AutohideWidget::installFilter: child name: "mplayerwindow logo" 
[18:47:55:946] AutohideWidget::installFilter: child name: "" 
[18:47:55:954] BaseGui::initializeMenus
[18:47:55:954] BaseGui::updateRecents
[18:47:55:954] DefaultGui::updateWidgets
[18:47:55:954] BaseGui::updateWidgets
[18:47:55:955] DefaultGui::loadConfig
[18:47:55:955] DesktopInfo::isInsideScreen: geometry of screen: x:0 y:0 w:1280 h:960
[18:47:55:956] ToolbarEditor::load: 'toolbar1'
[18:47:55:956] ToolbarEditor::load: loading action play_prev
[18:47:55:956] ToolbarEditor::load: loading action play
[18:47:55:956] ToolbarEditor::load: loading action pause
[18:47:55:956] ToolbarEditor::load: loading action pl_next
[18:47:55:957] ToolbarEditor::load: loading action screenshot
[18:47:55:957] ToolbarEditor::load: loading action mute
[18:47:55:957] ToolbarEditor::load: loading action mirror
[18:47:55:961] ToolbarEditor::load: loading action flip
[18:47:55:961] ToolbarEditor::load: loading action fullscreen
[18:47:55:961] ToolbarEditor::load: loading action repeat
[18:47:55:961] ToolbarEditor::load: loading action clear_ab_markers
[18:47:55:961] ToolbarEditor::load: loading action set_b_marker
[18:47:55:961] ToolbarEditor::load: loading action set_a_marker
[18:47:55:962] ToolbarEditor::load: 'controlwidget'
[18:47:55:962] ToolbarEditor::load: loading action play_prev
[18:47:55:962] ToolbarEditor::load: loading action play
[18:47:55:962] ToolbarEditor::load: loading action pause_and_frame_step
[18:47:55:962] ToolbarEditor::load: loading action stop
[18:47:55:962] ToolbarEditor::load: loading action play_next
[18:47:55:962] ToolbarEditor::load: loading action timeslider_action
[18:47:55:962] TimeSlider::setDragDelay: 100
[18:47:55:963] ToolbarEditor::load: loading action separator
[18:47:55:963] ToolbarEditor::load: adding separator
[18:47:55:963] ToolbarEditor::load: loading action rotate_menu
[18:47:55:963] ToolbarEditor::load: loading action mirror
[18:47:55:963] ToolbarEditor::load: loading action flip
[18:47:55:963] ToolbarEditor::load: loading action screenshot
[18:47:55:963] ToolbarEditor::load: loading action repeat
[18:47:55:963] ToolbarEditor::load: loading action clear_ab_markers
[18:47:55:963] ToolbarEditor::load: loading action set_b_marker
[18:47:55:963] ToolbarEditor::load: loading action set_a_marker
[18:47:55:964] ToolbarEditor::load: loading action fullscreen
[18:47:55:964] ToolbarEditor::load: loading action mute
[18:47:55:964] ToolbarEditor::load: loading action volumeslider_action
[18:47:55:964] ToolbarEditor::load: 'controlwidget_mini'
[18:47:55:964] ToolbarEditor::load: loading action play_or_pause
[18:47:55:964] ToolbarEditor::load: loading action stop
[18:47:55:964] ToolbarEditor::load: loading action separator
[18:47:55:964] ToolbarEditor::load: adding separator
[18:47:55:965] ToolbarEditor::load: loading action rewind1
[18:47:55:965] ToolbarEditor::load: loading action timeslider_action
[18:47:55:965] TimeSlider::setDragDelay: 100
[18:47:55:965] ToolbarEditor::load: loading action forward1
[18:47:55:965] ToolbarEditor::load: loading action separator
[18:47:55:965] ToolbarEditor::load: adding separator
[18:47:55:965] ToolbarEditor::load: loading action mute
[18:47:55:965] ToolbarEditor::load: loading action volumeslider_action
[18:47:55:966] ToolbarEditor::load: 'floating_control'
[18:47:55:966] ToolbarEditor::load: loading action play
[18:47:55:966] ToolbarEditor::load: loading action pause
[18:47:55:966] ToolbarEditor::load: loading action stop
[18:47:55:966] ToolbarEditor::load: loading action separator
[18:47:55:966] ToolbarEditor::load: adding separator
[18:47:55:966] ToolbarEditor::load: loading action rewindbutton_action
[18:47:55:966] ToolbarEditor::load: loading action timeslider_action
[18:47:55:967] TimeSlider::setDragDelay: 100
[18:47:55:967] ToolbarEditor::load: loading action forwardbutton_action
[18:47:55:967] ToolbarEditor::load: loading action separator
[18:47:55:967] ToolbarEditor::load: adding separator
[18:47:55:967] ToolbarEditor::load: loading action fullscreen
[18:47:55:967] ToolbarEditor::load: loading action mute
[18:47:55:967] ToolbarEditor::load: loading action volumeslider_action
[18:47:55:968] ToolbarEditor::load: loading action separator
[18:47:55:968] ToolbarEditor::load: adding separator
[18:47:55:968] ToolbarEditor::load: loading action timelabel_action
[18:47:55:969] Helper::qtVersion: 4806
[18:47:55:970] DefaultGui::loadConfig: playlist visible: 0
[18:47:55:970] DefaultGui::loadConfig: playlist position: 0, 0
[18:47:55:970] DefaultGui::loadConfig: playlist size: 100 x 30
[18:47:55:970] DefaultGui::updateWidgets
[18:47:55:980] BaseGui::updateWidgets
[18:47:55:988] BaseGui::showEvent
[18:47:55:998] BaseGui::loadActions
[18:47:55:998] ActionsEditor::loadFromConfig
[18:47:56:045] BaseGui::initializeMenus
[18:47:56:045] BaseGui::updateRecents
[18:47:56:046] DefaultGui::updateWidgets
[18:47:56:046] BaseGui::updateWidgets
[18:47:56:929] BaseGui::checkReminder
[18:47:57:929] BaseGui::checkIfUpgraded
[18:47:59:330] BaseGui::showLog

```

---

### Post by offir on 2015-07-29
It stuck again

This time I did what that [COLOR="#0000FF"]Bucky Ball[/COLOR] Said
> type control+alt+F1> login, then:
```
dmesg
```



```
[    0.000000] CPU0 microcode updated early to revision 0xa4, date = 2010-10-02
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-25-generic (buildd@lgw01-07) (gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) ) #26-Ubuntu SMP Fri Jul 24 21:17:31 UTC 2015 (Ubuntu 3.19.0-25.26-generic 3.19.8-ckt2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-25-generic root=UUID=5a00a585-68dc-45e4-bb79-25f55cb011ba ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000dffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfe7ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfe80000-0x00000000bfe8ffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bfe90000-0x00000000bfefffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bff00000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: LENOVO 9637VEY/LENOVO, BIOS 2OKT47AUS 01/17/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 3GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 4GB, type WB
[    0.000000] reg 2, base: 4GB, range: 1GB, type WB
[    0.000000] reg 3, base: 3071MB, range: 1MB, type UC
[    0.000000] total RAM covered: 4095M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0xbff00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbfe80 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f7070-0x000f707f] mapped at [ffff8800000f7070]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] BRK [0x01fe7000, 0x01fe7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x13fe00000-0x13fffffff]
[    0.000000]  [mem 0x13fe00000-0x13fffffff] page 2M
[    0.000000] BRK [0x01fe8000, 0x01fe8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x120000000-0x13fdfffff]
[    0.000000]  [mem 0x120000000-0x13fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbfe7ffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbfdfffff] page 2M
[    0.000000]  [mem 0xbfe00000-0xbfe7ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11fffffff]
[    0.000000]  [mem 0x100000000-0x11fffffff] page 2M
[    0.000000] RAMDISK: [mem 0x3583a000-0x36c14fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F6EC0 000014 (v00 LENOVO)
[    0.000000] ACPI: RSDT 0x00000000BFE8863F 000040 (v01 LENOVO TC-2O    00000047  LTP 00000000)
[    0.000000] ACPI: FACP 0x00000000BFE8FD18 000074 (v01 LENOVO TC-2O    00000047 PTL  00000003)
[    0.000000] ACPI: DSDT 0x00000000BFE89EB1 005E67 (v01 INTEL  BR_2OTER 00000047 MSFT 0100000E)
[    0.000000] ACPI: FACS 0x00000000BFE92FC0 000040
[    0.000000] ACPI: TCPA 0x00000000BFE8FD8C 000032 (v02 LENOVO THI2OCEN 00000047 PTL  00000001)
[    0.000000] ACPI: SLIC 0x00000000BFE8FDBE 000176 (v01 LENOVO TC-2O    00000047  LTP 00000000)
[    0.000000] ACPI: MCFG 0x00000000BFE8FF34 00003C (v01 PTLTD    M2OG   00000047  LTP 00000000)
[    0.000000] ACPI: APIC 0x00000000BFE8FF70 000068 (v01 PTLTD  ? A2OC   00000047  LTP 00000000)
[    0.000000] ACPI: BOOT 0x00000000BFE8FFD8 000028 (v01 PTLTD  $SB2OBL$ 00000047  LTP 00000001)
[    0.000000] ACPI: SSDT 0x00000000BFE8867F 0013EC (v01 PmRef  CpuPm    00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000013fffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x13fff8000-0x13fffcfff]
[    0.000000]  [ffffea0000000000-ffffea0004ffffff] PMD -> [ffff88013b600000-ffff88013f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x13fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0xbfe7ffff]
[    0.000000]   node   0: [mem 0x100000000-0x13fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x13fffffff]
[    0.000000] On node 0 totalpages: 1048093
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12218 pages used for memmap
[    0.000000]   DMA32 zone: 781952 pages, LIFO batch:31
[    0.000000]   Normal zone: 4096 pages used for memmap
[    0.000000]   Normal zone: 262144 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
[    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfe80000-0xbfe8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfe90000-0xbfefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbff00000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xc0000000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88013fc00000 s87104 r8192 d31680 u1048576
[    0.000000] pcpu-alloc: s87104 r8192 d31680 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031694
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-25-generic root=UUID=5a00a585-68dc-45e4-bb79-25f55cb011ba ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4023536K/4192372K available (8002K kernel code, 1232K rwdata, 3760K rodata, 1408K init, 1300K bss, 168836K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=2
[    0.000000] NR_IRQS:16640 nr_irqs:440 16
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-1.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1795.425 MHz processor
[    0.008014] Calibrating delay loop (skipped), value calculated using timer frequency.. 3590.85 BogoMIPS (lpj=7181700)
[    0.008018] pid_max: default: 32768 minimum: 301
[    0.008029] ACPI: Core revision 20141107
[    0.012746] ACPI: All ACPI Tables successfully acquired
[    0.015304] Security Framework initialized
[    0.015330] AppArmor: AppArmor initialized
[    0.015332] Yama: becoming mindful.
[    0.015839] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.018009] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.019058] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.019074] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.019464] Initializing cgroup subsys memory
[    0.019477] Initializing cgroup subsys devices
[    0.019482] Initializing cgroup subsys freezer
[    0.019486] Initializing cgroup subsys net_cls
[    0.019490] Initializing cgroup subsys blkio
[    0.019494] Initializing cgroup subsys perf_event
[    0.019498] Initializing cgroup subsys net_prio
[    0.019502] Initializing cgroup subsys hugetlb
[    0.019536] CPU: Physical Processor ID: 0
[    0.019538] CPU: Processor Core ID: 0
[    0.019540] mce: CPU supports 6 MCE banks
[    0.019549] CPU0: Thermal monitoring handled by SMI
[    0.019553] process: using mwait in idle threads
[    0.019559] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.019680] Freeing SMP alternatives memory: 32K (ffffffff81e96000 - ffffffff81e9e000)
[    0.021450] ftrace: allocating 30087 entries in 118 pages
[    0.032504] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072711] smpboot: CPU0: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz (fam: 06, model: 0f, stepping: 0d)
[    0.076000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.076000] perf_event_intel: PEBS disabled due to CPU errata
[    0.076000] ... version:                2
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   3
[    0.076000] ... event mask:             0000000700000003
[    0.076000] x86: Booting SMP configuration:
[    0.076000] .... node  #0, CPUs:      #1
[    0.012000] CPU1 microcode updated early to revision 0xa4, date = 2010-10-02
[    0.012000] CPU1: Thermal monitoring handled by SMI
[    0.086832] x86: Booted up 1 node, 2 CPUs
[    0.086838] smpboot: Total of 2 processors activated (7181.70 BogoMIPS)
[    0.086889] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.088042] devtmpfs: initialized
[    0.090887] evm: security.selinux
[    0.090890] evm: security.SMACK64
[    0.090892] evm: security.SMACK64EXEC
[    0.090894] evm: security.SMACK64TRANSMUTE
[    0.090895] evm: security.SMACK64MMAP
[    0.090897] evm: security.ima
[    0.090898] evm: security.capability
[    0.092014] PM: Registering ACPI NVS region [mem 0xbfe90000-0xbfefffff] (458752 bytes)
[    0.092039] pinctrl core: initialized pinctrl subsystem
[    0.092212] RTC time:  4:21:52, date: 07/29/15
[    0.092361] NET: Registered protocol family 16
[    0.096012] cpuidle: using governor ladder
[    0.100011] cpuidle: using governor menu
[    0.100105] ACPI: bus type PCI registered
[    0.100110] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.100234] PCI: MMCONFIG for domain 0000 [bus 00-09] at [mem 0xe0000000-0xe09fffff] (base 0xe0000000)
[    0.100237] PCI: not using MMCONFIG
[    0.100239] PCI: Using configuration type 1 for base access
[    0.108161] ACPI: Added _OSI(Module Device)
[    0.108165] ACPI: Added _OSI(Processor Device)
[    0.108167] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.108170] ACPI: Added _OSI(Processor Aggregator Device)
[    0.115226] ACPI: Dynamic OEM Table Load:
[    0.115237] ACPI: SSDT 0xFFFF88013A550C00 00017C (v01 PmRef  Cpu0Ist  00003000 INTL 20050228)
[    0.115786] ACPI: Dynamic OEM Table Load:
[    0.115792] ACPI: SSDT 0xFFFF88013AB18C80 000066 (v01 PmRef  Cpu1Ist  00003000 INTL 20050228)
[    0.116459] ACPI: Interpreter enabled
[    0.116471] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.116488] ACPI: (supports S0 S1 S3 S4 S5)
[    0.116491] ACPI: Using IOAPIC for interrupt routing
[    0.116511] PCI: MMCONFIG for domain 0000 [bus 00-09] at [mem 0xe0000000-0xe09fffff] (base 0xe0000000)
[    0.117323] PCI: MMCONFIG at [mem 0xe0000000-0xe09fffff] reserved in ACPI motherboard resources
[    0.117379] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.123815] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.123824] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.123831] ACPI BIOS Error (bug): \_SB_.PCI0._OSC: Excess arguments - ASL declared 5, ACPI requires 4 (20141107/nsarguments-189)
[    0.123899] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.123901] _OSC request data:1 1f 0 
[    0.123907] acpi PNP0A03:00: _OSC failed (AE_TYPE); disabling ASPM
[    0.125113] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-09] only partially covers this bridge
[    0.125301] PCI host bridge to bus 0000:00
[    0.125306] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.125309] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.125312] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.125315] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.125318] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.125321] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.125323] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.125326] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xdfffffff]
[    0.125329] pci_bus 0000:00: root bus resource [io  0x0d00-0xfdff]
[    0.125341] pci 0000:00:00.0: [8086:2970] type 00 class 0x060000
[    0.125477] pci 0000:00:01.0: [8086:2971] type 01 class 0x060400
[    0.125534] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.125670] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
[    0.125690] pci 0000:00:1b.0: reg 0x10: [mem 0xd3300000-0xd3303fff 64bit]
[    0.125772] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.125876] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.125955] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.126006] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.126074] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
[    0.126158] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.126211] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.126279] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.126323] pci 0000:00:1d.0: reg 0x20: [io  0x1800-0x181f]
[    0.126407] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.126473] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.126516] pci 0000:00:1d.1: reg 0x20: [io  0x1820-0x183f]
[    0.126600] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.126666] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.126709] pci 0000:00:1d.2: reg 0x20: [io  0x1840-0x185f]
[    0.126791] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.126862] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.126905] pci 0000:00:1d.3: reg 0x20: [io  0x1860-0x187f]
[    0.126986] pci 0000:00:1d.3: System wakeup disabled by ACPI
[    0.127059] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.127080] pci 0000:00:1d.7: reg 0x10: [mem 0xd3304000-0xd33043ff]
[    0.127171] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.127219] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.127286] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.127382] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.127449] pci 0000:00:1f.0: [8086:27b8] type 00 class 0x060100
[    0.127541] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.127550] pci 0000:00:1f.0: can't claim BAR 13 [io  0x1000-0x107f]: address conflict with ACPI PM1a_EVT_BLK [io  0x1000-0x1003]
[    0.127557] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.127562] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0290 (mask 003f)
[    0.127691] pci 0000:00:1f.2: [8086:27c0] type 00 class 0x01018a
[    0.127707] pci 0000:00:1f.2: reg 0x10: [io  0x0000-0x0007]
[    0.127717] pci 0000:00:1f.2: reg 0x14: [io  0x0000-0x0003]
[    0.127727] pci 0000:00:1f.2: reg 0x18: [io  0x0000-0x0007]
[    0.127736] pci 0000:00:1f.2: reg 0x1c: [io  0x0000-0x0003]
[    0.127746] pci 0000:00:1f.2: reg 0x20: [io  0x18b0-0x18bf]
[    0.127764] pci 0000:00:1f.2: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.127767] pci 0000:00:1f.2: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.127770] pci 0000:00:1f.2: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.127773] pci 0000:00:1f.2: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.127799] pci 0000:00:1f.2: PME# supported from D3hot
[    0.127900] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.127954] pci 0000:00:1f.3: reg 0x20: [io  0x1880-0x189f]
[    0.128153] pci 0000:01:00.0: [10de:0641] type 00 class 0x030000
[    0.128168] pci 0000:01:00.0: reg 0x10: [mem 0xd2000000-0xd2ffffff]
[    0.128181] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.128194] pci 0000:01:00.0: reg 0x1c: [mem 0xd0000000-0xd1ffffff 64bit]
[    0.128203] pci 0000:01:00.0: reg 0x24: [io  0x2000-0x207f]
[    0.128213] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0007ffff pref]
[    0.128336] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.128340] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.128345] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd2ffffff]
[    0.128350] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.128420] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.128425] pci 0000:00:1c.0:   bridge window [io  0x0000-0x0fff]
[    0.128430] pci 0000:00:1c.0:   bridge window [mem 0x00000000-0x000fffff]
[    0.128437] pci 0000:00:1c.0:   bridge window [mem 0x00000000-0x000fffff 64bit pref]
[    0.128533] pci 0000:04:00.0: [14e4:169a] type 00 class 0x020000
[    0.128562] pci 0000:04:00.0: reg 0x10: [mem 0xd3000000-0xd300ffff 64bit]
[    0.128721] pci 0000:04:00.0: PME# supported from D3hot D3cold
[    0.136029] pci 0000:00:1c.1: PCI bridge to [bus 04]
[    0.136040] pci 0000:00:1c.1:   bridge window [mem 0xd3000000-0xd30fffff]
[    0.136173] pci 0000:00:1e.0: PCI bridge to [bus 0a] (subtractive decode)
[    0.136184] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.136187] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.136190] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.136194] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.136197] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.136200] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.136203] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.136206] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xfdff] (subtractive decode)
[    0.136533] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 10 *11 14 15)
[    0.136602] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 10 11 14 15)
[    0.136668] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 10 11 14 15) *5
[    0.136732] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *10 11 14 15)
[    0.136801] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 10 11 14 15) *0, disabled.
[    0.136870] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 10 11 14 15) *0, disabled.
[    0.136939] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 10 *11 14 15)
[    0.137006] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *10 11 14 15)
[    0.137655] ACPI: Enabled 2 GPEs in block 00 to 1F
[    0.137804] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.137804] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.137804] vgaarb: loaded
[    0.137804] vgaarb: bridge control possible 0000:01:00.0
[    0.137804] SCSI subsystem initialized
[    0.137804] libata version 3.00 loaded.
[    0.137804] ACPI: bus type USB registered
[    0.137804] usbcore: registered new interface driver usbfs
[    0.137804] usbcore: registered new interface driver hub
[    0.137804] usbcore: registered new device driver usb
[    0.137804] PCI: Using ACPI for IRQ routing
[    0.137804] PCI: pci_cache_line_size set to 64 bytes
[    0.137804] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.137804] e820: reserve RAM buffer [mem 0xbfe80000-0xbfffffff]
[    0.137804] NetLabel: Initializing
[    0.137804] NetLabel:  domain hash size = 128
[    0.137804] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.137804] NetLabel:  unlabeled traffic allowed by default
[    0.137804] hpet clockevent registered
[    0.137804] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.137804] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.137804] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.141025] Switched to clocksource hpet
[    0.151283] AppArmor: AppArmor Filesystem Enabled
[    0.151408] pnp: PnP ACPI init
[    0.151692] system 00:00: [io  0x04d0-0x04d1] has been reserved
[    0.151696] system 00:00: [io  0x0290-0x029f] has been reserved
[    0.151700] system 00:00: [io  0x0800-0x087f] has been reserved
[    0.151703] system 00:00: [io  0x0880-0x088f] has been reserved
[    0.151707] system 00:00: [io  0x0400-0x04bf] has been reserved
[    0.151710] system 00:00: [io  0x0600-0x063f] has been reserved
[    0.151714] system 00:00: [io  0x0900-0x090f] has been reserved
[    0.151717] system 00:00: [io  0x1000-0x107f] could not be reserved
[    0.151721] system 00:00: [io  0x1180-0x11bf] has been reserved
[    0.151724] system 00:00: [io  0x04d0-0x04d1] has been reserved
[    0.151728] system 00:00: [io  0xfe00] has been reserved
[    0.151732] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.151735] system 00:00: [mem 0xfed13000-0xfed13fff] has been reserved
[    0.151738] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.151742] system 00:00: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.151745] system 00:00: [mem 0xfef00000-0xfeffffff] has been reserved
[    0.151751] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.151833] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.152427] pnp 00:02: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.153028] pnp 00:03: [dma 3]
[    0.153182] pnp 00:03: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.153572] pnp 00:04: [dma 2]
[    0.153632] pnp 00:04: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.153698] pnp: PnP ACPI: found 5 devices
[    0.161313] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.161319] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.161324] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.161334] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
[    0.161338] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000
[    0.161352] pci 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[    0.161356] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.161360] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.161363] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.161367] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.161370] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.161379] pci 0000:00:1c.0: BAR 14: assigned [mem 0xd3100000-0xd32fffff]
[    0.161388] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd3400000-0xd35fffff 64bit pref]
[    0.161395] pci 0000:00:1c.1: BAR 15: assigned [mem 0xd3600000-0xd37fffff 64bit pref]
[    0.161401] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.161406] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.161411] pci 0000:01:00.0: BAR 6: no space for [mem size 0x00080000 pref]
[    0.161415] pci 0000:01:00.0: BAR 6: failed to assign [mem size 0x00080000 pref]
[    0.161419] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.161422] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.161427] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd2ffffff]
[    0.161432] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.161437] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.161441] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.161447] pci 0000:00:1c.0:   bridge window [mem 0xd3100000-0xd32fffff]
[    0.161452] pci 0000:00:1c.0:   bridge window [mem 0xd3400000-0xd35fffff 64bit pref]
[    0.161459] pci 0000:00:1c.1: PCI bridge to [bus 04]
[    0.161462] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.161468] pci 0000:00:1c.1:   bridge window [mem 0xd3000000-0xd30fffff]
[    0.161473] pci 0000:00:1c.1:   bridge window [mem 0xd3600000-0xd37fffff 64bit pref]
[    0.161480] pci 0000:00:1e.0: PCI bridge to [bus 0a]
[    0.161492] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.161495] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.161498] pci_bus 0000:00: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.161501] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.161504] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.161507] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.161510] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xdfffffff]
[    0.161512] pci_bus 0000:00: resource 11 [io  0x0d00-0xfdff]
[    0.161515] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.161518] pci_bus 0000:01: resource 1 [mem 0xd0000000-0xd2ffffff]
[    0.161521] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.161524] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.161527] pci_bus 0000:02: resource 1 [mem 0xd3100000-0xd32fffff]
[    0.161530] pci_bus 0000:02: resource 2 [mem 0xd3400000-0xd35fffff 64bit pref]
[    0.161533] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.161536] pci_bus 0000:04: resource 1 [mem 0xd3000000-0xd30fffff]
[    0.161539] pci_bus 0000:04: resource 2 [mem 0xd3600000-0xd37fffff 64bit pref]
[    0.161542] pci_bus 0000:0a: resource 4 [io  0x0000-0x0cf7]
[    0.161545] pci_bus 0000:0a: resource 5 [mem 0x000a0000-0x000bffff]
[    0.161548] pci_bus 0000:0a: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.161551] pci_bus 0000:0a: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.161554] pci_bus 0000:0a: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.161556] pci_bus 0000:0a: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.161559] pci_bus 0000:0a: resource 10 [mem 0xc0000000-0xdfffffff]
[    0.161562] pci_bus 0000:0a: resource 11 [io  0x0d00-0xfdff]
[    0.161600] NET: Registered protocol family 2
[    0.161866] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.162012] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.162186] TCP: Hash tables configured (established 32768 bind 32768)
[    0.162254] TCP: reno registered
[    0.162266] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.162300] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.162424] NET: Registered protocol family 1
[    0.163617] pci 0000:01:00.0: Video device with shadowed ROM
[    0.163625] PCI: CLS 32 bytes, default 64
[    0.163730] Trying to unpack rootfs image as initramfs...
[    0.654030] Freeing initrd memory: 20332K (ffff88003583a000 - ffff880036c15000)
[    0.654049] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.654052] software IO TLB [mem 0xbbe80000-0xbfe80000] (64MB) mapped at [ffff8800bbe80000-ffff8800bfe7ffff]
[    0.654109] Simple Boot Flag at 0x35 set to 0x1
[    0.654350] microcode: CPU0 sig=0x6fd, pf=0x1, revision=0xa4
[    0.654361] microcode: CPU1 sig=0x6fd, pf=0x1, revision=0xa4
[    0.654475] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.654517] Scanning for low memory corruption every 60 seconds
[    0.654939] futex hash table entries: 512 (order: 3, 32768 bytes)
[    0.654966] Initialise system trusted keyring
[    0.654999] audit: initializing netlink subsys (disabled)
[    0.655029] audit: type=2000 audit(1438143711.652:1): initialized
[    0.655543] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.658348] zpool: loaded
[    0.658353] zbud: loaded
[    0.658572] VFS: Disk quotas dquot_6.5.2
[    0.658641] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.659513] fuse init (API version 7.23)
[    0.659760] Key type big_key registered
[    0.660198] Key type asymmetric registered
[    0.660203] Asymmetric key parser 'x509' registered
[    0.660275] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.660323] io scheduler noop registered
[    0.660327] io scheduler deadline registered (default)
[    0.660383] io scheduler cfq registered
[    0.660730] pcieport 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.661146] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.661173] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.661236] intel_idle: does not run on family 6 model 15
[    0.661357] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/PNP0C0C:00/input/input0
[    0.661363] ACPI: Power Button [PWRB]
[    0.661435] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.661439] ACPI: Power Button [PWRF]
[    0.661679] GHES: HEST is not enabled!
[    0.661831] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.682223] 00:02: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.684568] Linux agpgart interface v0.103
[    0.686791] brd: module loaded
[    0.687879] loop: module loaded
[    0.688126] ata_piix 0000:00:1f.2: version 2.13
[    0.688285] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.845098] scsi host0: ata_piix
[    0.845308] scsi host1: ata_piix
[    0.845378] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    0.845381] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    0.845557] libphy: Fixed MDIO Bus: probed
[    0.845561] tun: Universal TUN/TAP device driver, 1.6
[    0.845563] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.845650] PPP generic driver version 2.4.2
[    0.845770] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.845779] ehci-pci: EHCI PCI platform driver
[    0.845962] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.845972] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.845988] ehci-pci 0000:00:1d.7: debug port 1
[    0.849898] ehci-pci 0000:00:1d.7: cache line size of 32 is not supported
[    0.849922] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd3304000
[    0.860034] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.860143] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.860148] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.860153] usb usb1: Product: EHCI Host Controller
[    0.860158] usb usb1: Manufacturer: Linux 3.19.0-25-generic ehci_hcd
[    0.860162] usb usb1: SerialNumber: 0000:00:1d.7
[    0.860369] hub 1-0:1.0: USB hub found
[    0.860380] hub 1-0:1.0: 8 ports detected
[    0.860661] ehci-platform: EHCI generic platform driver
[    0.860679] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.860690] ohci-pci: OHCI PCI platform driver
[    0.860712] ohci-platform: OHCI generic platform driver
[    0.860726] uhci_hcd: USB Universal Host Controller Interface driver
[    0.860882] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.860891] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.860899] uhci_hcd 0000:00:1d.0: detected 2 ports
[    0.860921] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[    0.860985] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.860988] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.860991] usb usb2: Product: UHCI Host Controller
[    0.860994] usb usb2: Manufacturer: Linux 3.19.0-25-generic uhci_hcd
[    0.860997] usb usb2: SerialNumber: 0000:00:1d.0
[    0.861160] hub 2-0:1.0: USB hub found
[    0.861171] hub 2-0:1.0: 2 ports detected
[    0.861422] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.861431] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.861439] uhci_hcd 0000:00:1d.1: detected 2 ports
[    0.861470] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    0.861535] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.861539] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.861542] usb usb3: Product: UHCI Host Controller
[    0.861545] usb usb3: Manufacturer: Linux 3.19.0-25-generic uhci_hcd
[    0.861548] usb usb3: SerialNumber: 0000:00:1d.1
[    0.861699] hub 3-0:1.0: USB hub found
[    0.861709] hub 3-0:1.0: 2 ports detected
[    0.861973] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.861982] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.861989] uhci_hcd 0000:00:1d.2: detected 2 ports
[    0.862019] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    0.862079] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.862083] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.862086] usb usb4: Product: UHCI Host Controller
[    0.862089] usb usb4: Manufacturer: Linux 3.19.0-25-generic uhci_hcd
[    0.862092] usb usb4: SerialNumber: 0000:00:1d.2
[    0.862251] hub 4-0:1.0: USB hub found
[    0.862261] hub 4-0:1.0: 2 ports detected
[    0.862511] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.862520] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.862527] uhci_hcd 0000:00:1d.3: detected 2 ports
[    0.862559] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    0.862618] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.862622] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.862625] usb usb5: Product: UHCI Host Controller
[    0.862628] usb usb5: Manufacturer: Linux 3.19.0-25-generic uhci_hcd
[    0.862630] usb usb5: SerialNumber: 0000:00:1d.3
[    0.862787] hub 5-0:1.0: USB hub found
[    0.862797] hub 5-0:1.0: 2 ports detected
[    0.862995] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.863381] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.863388] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.863585] mousedev: PS/2 mouse device common for all mice
[    0.863778] rtc_cmos 00:01: RTC can wake from S4
[    0.863918] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.863946] rtc_cmos 00:01: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.863971] i2c /dev entries driver
[    0.864110] device-mapper: uevent: version 1.0.3
[    0.864217] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    0.864243] ledtrig-cpu: registered to indicate activity on CPUs
[    0.864384] PCCT header not found.
[    0.864386] ACPI PCC probe failed.
[    0.864567] TCP: cubic registered
[    0.864755] NET: Registered protocol family 10
[    0.865091] NET: Registered protocol family 17
[    0.865108] Key type dns_resolver registered
[    0.865528] Loading compiled-in X.509 certificates
[    0.867096] Loaded X.509 cert 'Magrathea: Glacier signing key: 897aad757d0e4d72cd84240b25ac782885bfae3f'
[    0.867126] registered taskstats version 1
[    0.870556] Key type trusted registered
[    0.876768] Key type encrypted registered
[    0.876784] AppArmor: AppArmor sha1 policy hashing enabled
[    0.876789] ima: No TPM chip found, activating TPM-bypass!
[    0.876821] evm: HMAC attrs: 0x1
[    0.877148]   Magic number: 7:430:364
[    0.877276] rtc_cmos 00:01: setting system clock to 2015-07-29 04:21:52 UTC (1438143712)
[    0.877600] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.877603] EDD information not available.
[    0.877709] PM: Hibernation image not present or could not be loaded.
[    1.000286] ata2.01: NODEV after polling detection
[    1.008149] ata2.00: ATAPI: HL-DT-STDVD-ROM GDRH20N, 0M02, max UDMA/100
[    1.024143] ata2.00: configured for UDMA/100
[    1.029720] ata1.00: ATA-8: WDC WD1600AAJS-08WAA0, 58.01D58, max UDMA/100
[    1.029725] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.044688] ata1.00: configured for UDMA/100
[    1.044860] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-0 1D58 PQ: 0 ANSI: 5
[    1.045109] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.045177] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.045200] sd 0:0:0:0: [sda] Write Protect is off
[    1.045204] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.045339] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.046769] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDRH20N  0M02 PQ: 0 ANSI: 5
[    1.061429] sr 1:0:0:0: [sr0] scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.061435] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.061649] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.061749] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.081933]  sda: sda1 sda2 < sda5 >
[    1.082414] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.083068] Freeing unused kernel memory: 1408K (ffffffff81d36000 - ffffffff81e96000)
[    1.083074] Write protecting the kernel read-only data: 12288k
[    1.083399] Freeing unused kernel memory: 176K (ffff8800017d4000 - ffff880001800000)
[    1.083626] Freeing unused kernel memory: 336K (ffff880001bac000 - ffff880001c00000)
[    1.102564] random: systemd-udevd urandom read with 13 bits of entropy available
[    1.138457] pps_core: LinuxPPS API ver. 1 registered
[    1.138461] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.140635] PTP clock support registered
[    1.146712] tg3.c:v3.137 (May 11, 2014)
[    1.169491] FDC 0 is a post-1991 82077
[    1.209463] tg3 0000:04:00.0 eth0: Tigon3 [partno(BCM95786) rev b002] (PCI Express) MAC address 00:1c:25:c6:8f:79
[    1.209470] tg3 0000:04:00.0 eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.209474] tg3 0000:04:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.209477] tg3 0000:04:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.356069] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    1.509085] usb 3-1: New USB device found, idVendor=0557, idProduct=7000
[    1.509093] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.512168] hub 3-1:1.0: USB hub found
[    1.514080] hub 3-1:1.0: 4 ports detected
[    1.525860] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.652045] tsc: Refined TSC clocksource calibration: 1795.499 MHz
[    1.797090] usb 3-1.1: new low-speed USB device number 3 using uhci_hcd
[    1.986086] usb 3-1.1: New USB device found, idVendor=0557, idProduct=2213
[    1.986094] usb 3-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.986100] usb 3-1.1: Product: CS-1734A V4.2.416
[    1.986104] usb 3-1.1: Manufacturer: ATEN
[    2.069092] usb 3-1.3: new low-speed USB device number 4 using uhci_hcd
[    2.206172] usb 3-1.3: New USB device found, idVendor=046d, idProduct=c506
[    2.206180] usb 3-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.206185] usb 3-1.3: Product: USB Receiver
[    2.206190] usb 3-1.3: Manufacturer: Logitech
[    2.652177] Switched to clocksource tsc
[    2.679868] systemd[1]: Inserted module 'autofs4'
[    2.797870] systemd[1]: systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    2.798082] systemd[1]: Detected architecture x86-64.
[    2.810471] systemd[1]: Set hostname to <offir-vivid>.
[    3.069384] random: nonblocking pool is initialized
[    4.112516] systemd[1]: Reached target Encrypted Volumes.
[    4.112536] systemd[1]: Starting Encrypted Volumes.
[    4.112602] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    4.112615] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.
[    4.112664] systemd[1]: Created slice Root Slice.
[    4.112678] systemd[1]: Starting Root Slice.
[    4.112726] systemd[1]: Listening on Delayed Shutdown Socket.
[    4.112738] systemd[1]: Starting Delayed Shutdown Socket.
[    4.112780] systemd[1]: Listening on udev Control Socket.
[    4.112793] systemd[1]: Starting udev Control Socket.
[    4.112932] systemd[1]: Listening on Journal Audit Socket.
[    4.112947] systemd[1]: Starting Journal Audit Socket.
[    4.112996] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    4.113009] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.
[    4.113148] systemd[1]: Created slice User and Session Slice.
[    4.113162] systemd[1]: Starting User and Session Slice.
[    4.113180] systemd[1]: Reached target Remote File Systems (Pre).
[    4.113191] systemd[1]: Starting Remote File Systems (Pre).
[    4.113249] systemd[1]: Listening on Journal Socket (/dev/log).
[    4.113263] systemd[1]: Starting Journal Socket (/dev/log).
[    4.113328] systemd[1]: Listening on Journal Socket.
[    4.113348] systemd[1]: Starting Journal Socket.
[    4.113397] systemd[1]: Listening on udev Kernel Socket.
[    4.113410] systemd[1]: Starting udev Kernel Socket.
[    4.113452] systemd[1]: Listening on fsck to fsckd communication Socket.
[    4.113465] systemd[1]: Starting fsck to fsckd communication Socket.
[    4.113741] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    4.113761] systemd[1]: Starting Arbitrary Executable File Formats File System Automount Point.
[    4.113912] systemd[1]: Created slice System Slice.
[    4.113937] systemd[1]: Starting System Slice.
[    4.145476] systemd[1]: Starting Load Kernel Modules...
[    4.146759] systemd[1]: Starting Uncomplicated firewall...
[    4.147007] systemd[1]: Created slice system-getty.slice.
[    4.147034] systemd[1]: Starting system-getty.slice.
[    4.148197] systemd[1]: Starting udev Coldplug all Devices...
[    4.149352] systemd[1]: Starting Nameserver information manager...
[    4.150538] systemd[1]: Started Braille Device Support.
[    4.151451] systemd[1]: Starting Braille Device Support...
[    4.152535] systemd[1]: Mounting POSIX Message Queue File System...
[    4.327290] systemd[1]: Started Set Up Additional Binary Formats.
[    4.327385] systemd[1]: Reached target Slices.
[    4.327402] systemd[1]: Starting Slices.
[    4.328639] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    4.329883] systemd[1]: Started Read required files in advance.
[    4.330018] systemd[1]: Starting Read required files in advance...
[    4.331247] systemd[1]: Starting Setup Virtual Console...
[    4.332537] systemd[1]: Starting Increase datagram queue length...
[    4.333741] systemd[1]: Mounting Huge Pages File System...
[    4.334950] systemd[1]: Mounting Debug File System...
[    4.469708] systemd[1]: Started Setup Virtual Console.
[    4.727987] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    4.729255] systemd[1]: Starting Create Static Device Nodes in /dev...
[    4.743409] systemd[1]: Started Uncomplicated firewall.
[    5.047379] systemd[1]: Started udev Coldplug all Devices.
[    5.048696] systemd[1]: Starting udev Wait for Complete Device Initialization...
[    5.138246] systemd[1]: Mounted POSIX Message Queue File System.
[    5.138322] systemd[1]: Mounted Huge Pages File System.
[    5.138357] systemd[1]: Mounted Debug File System.
[    5.140764] systemd[1]: Started Increase datagram queue length.
[    5.155177] systemd[1]: Listening on Syslog Socket.
[    5.155201] systemd[1]: Starting Syslog Socket.
[    5.156807] systemd[1]: Starting Journal Service...
[    5.250598] lp: driver loaded but no devices found
[    5.273466] systemd[1]: Started Nameserver information manager.
[    5.297084] ppdev: user-space parallel port driver
[    5.377976] parport_pc 00:03: disabled
[    5.377986] parport_pc: probe of 00:03 failed with error -22
[    5.577386] systemd[1]: Started Load Kernel Modules.
[    5.578605] systemd[1]: Mounting FUSE Control File System...
[    5.579779] systemd[1]: Starting Apply Kernel Variables...
[    5.579903] systemd[1]: Mounted Configuration File System.
[    5.583373] systemd[1]: Mounted FUSE Control File System.
[    6.209178] systemd[1]: Started Journal Service.
[    9.570847] intel_rng: FWH not detected
[    9.793026] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102f conflicts with OpRegion 0x000000000000102c-0x000000000000102f (\GPIE) (20141107/utaddress-258)
[    9.793036] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102f conflicts with OpRegion 0x0000000000001028-0x000000000000102b (\GPIS) (20141107/utaddress-258)
[    9.793042] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102f conflicts with OpRegion 0x0000000000001000-0x000000000000102f (\_SB_.PCI0.LPC0.PMIO) (20141107/utaddress-258)
[    9.793047] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102f conflicts with OpRegion 0x000000000000102c-0x000000000000102f (\_SB_.PCI0.LPC0.GPIE) (20141107/utaddress-258)
[    9.793052] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102f conflicts with OpRegion 0x0000000000001028-0x000000000000102b (\_SB_.PCI0.LPC0.GPIS) (20141107/utaddress-258)
[    9.793057] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.793061] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011af conflicts with OpRegion 0x0000000000001180-0x00000000000011af (\_SB_.PCI0.LPC0.GPOX) (20141107/utaddress-258)
[    9.793066] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.793114] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    9.859737] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.867980] coretemp coretemp.0: Using relative temperature scale!
[    9.867998] coretemp coretemp.0: Using relative temperature scale!
[    9.931664] leds_ss4200: no LED devices found
[   10.754116] gpio_ich: GPIO from 462 to 511 on gpio_ich
[   10.801883] [drm] Initialized drm 1.1.0 20060810
[   10.851314] hidraw: raw HID events driver (C) Jiri Kosina
[   11.131499] usbcore: registered new interface driver usbhid
[   11.131505] usbhid: USB HID core driver
[   11.240905] input: ATEN CS-1734A V4.2.416 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.1/3-1.1:1.0/0003:0557:2213.0001/input/input5
[   11.296257] hid-generic 0003:0557:2213.0001: input,hidraw0: USB HID v1.00 Keyboard [ATEN CS-1734A V4.2.416] on usb-0000:00:1d.1-1.1/input0
[   11.296609] input: ATEN CS-1734A V4.2.416 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.1/3-1.1:1.1/0003:0557:2213.0002/input/input6
[   11.296787] hid-generic 0003:0557:2213.0002: input,hidraw1: USB HID v1.00 Mouse [ATEN CS-1734A V4.2.416] on usb-0000:00:1d.1-1.1/input1
[   11.297172] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.3/3-1.3:1.0/0003:046D:C506.0003/input/input7
[   11.297343] hid-generic 0003:046D:C506.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1.3/input0
[   11.637651] sound hdaudioC0D0: autoconfig: line_outs=3 (0x1b/0x1c/0x1d/0x0/0x0) type:line
[   11.637658] sound hdaudioC0D0:    speaker_outs=1 (0x1e/0x0/0x0/0x0/0x0)
[   11.637661] sound hdaudioC0D0:    hp_outs=1 (0x1a/0x0/0x0/0x0/0x0)
[   11.637664] sound hdaudioC0D0:    mono: mono_out=0x0
[   11.637667] sound hdaudioC0D0:    inputs:
[   11.637670] sound hdaudioC0D0:      Mic=0x1f
[   11.637673] sound hdaudioC0D0:      CD=0x22
[   11.644424] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   11.644560] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   11.644687] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   11.644806] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.644962] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   14.207120] Adding 4190204k swap on /dev/sda5.  Priority:-1 extents:1 across:4190204k FS
[   14.318881] nvidia: module license 'NVIDIA' taints kernel.
[   14.318888] Disabling lock debugging due to kernel taint
[   14.330807] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   14.339023] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   14.339578] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
[   14.339592] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.76  Thu Jan 22 12:11:08 PST 2015
[   15.451285] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.886466] systemd-journald[212]: Received request to flush runtime journal from PID 1
[   17.257557] audit: type=1400 audit(1438143728.878:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=401 comm="apparmor_parser"
[   17.257572] audit: type=1400 audit(1438143728.878:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=401 comm="apparmor_parser"
[   17.332836] audit: type=1400 audit(1438143728.950:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=401 comm="apparmor_parser"
[   17.332852] audit: type=1400 audit(1438143728.950:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=401 comm="apparmor_parser"
[   17.332862] audit: type=1400 audit(1438143728.950:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=401 comm="apparmor_parser"
[   17.332870] audit: type=1400 audit(1438143728.950:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=401 comm="apparmor_parser"
[   17.500275] audit: type=1400 audit(1438143729.118:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=401 comm="apparmor_parser"
[   17.500293] audit: type=1400 audit(1438143729.118:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=401 comm="apparmor_parser"
[   17.500302] audit: type=1400 audit(1438143729.118:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=401 comm="apparmor_parser"
[   17.500311] audit: type=1400 audit(1438143729.118:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=401 comm="apparmor_parser"
[   19.308871] cgroup: new mount options do not match the existing superblock, will be ignored
[   25.270656] cfg80211: Calling CRDA to update world regulatory domain
[   26.824412] cfg80211: World regulatory domain updated:
[   26.824419] cfg80211:  DFS Master region: unset
[   26.824421] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   26.824425] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   26.824428] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   26.824431] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   26.824434] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   26.824438] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   28.747551] tg3 0000:04:00.0 eth0: Link is up at 100 Mbps, full duplex
[   28.747575] tg3 0000:04:00.0 eth0: Flow control is on for TX and on for RX
[  891.281233] perf interrupt took too long (2516 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 3269.396860] perf interrupt took too long (5010 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[27772.924112] usb 3-1: USB disconnect, device number 2
[27772.924119] usb 3-1.1: USB disconnect, device number 3
[27773.012165] usb 3-1.3: USB disconnect, device number 4
[27773.528088] usb 3-1: new full-speed USB device number 5 using uhci_hcd
[27773.681156] usb 3-1: New USB device found, idVendor=0557, idProduct=7000
[27773.681163] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[27773.684773] hub 3-1:1.0: USB hub found
[27773.686139] hub 3-1:1.0: 4 ports detected
[27773.969148] usb 3-1.1: new low-speed USB device number 6 using uhci_hcd
[27779.077112] usb 3-1.1: new low-speed USB device number 7 using uhci_hcd
[27779.269101] usb 3-1.1: New USB device found, idVendor=0557, idProduct=2213
[27779.269108] usb 3-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[27779.269112] usb 3-1.1: Product: CS-1734A V4.2.416
[27779.269115] usb 3-1.1: Manufacturer: ATEN
[27779.319980] input: ATEN CS-1734A V4.2.416 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.1/3-1.1:1.0/0003:0557:2213.0004/input/input13
[27779.372427] hid-generic 0003:0557:2213.0004: input,hidraw0: USB HID v1.00 Keyboard [ATEN CS-1734A V4.2.416] on usb-0000:00:1d.1-1.1/input0
[27779.399858] input: ATEN CS-1734A V4.2.416 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.1/3-1.1:1.1/0003:0557:2213.0005/input/input14
[27779.456301] hid-generic 0003:0557:2213.0005: input,hidraw1: USB HID v1.00 Mouse [ATEN CS-1734A V4.2.416] on usb-0000:00:1d.1-1.1/input1
[28003.541689] usb 3-1.3: new low-speed USB device number 8 using uhci_hcd
[28003.677698] usb 3-1.3: New USB device found, idVendor=046d, idProduct=c506
[28003.677705] usb 3-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[28003.677709] usb 3-1.3: Product: USB Receiver
[28003.677712] usb 3-1.3: Manufacturer: Logitech
[28003.698579] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.3/3-1.3:1.0/0003:046D:C506.0006/input/input15
[28003.752350] hid-generic 0003:046D:C506.0006: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1.3/input0
[29177.394551] usb 3-1.3: USB disconnect, device number 8
[29185.393815] hub 3-1:1.0: hub_port_status failed (err = -71)
[29185.393824] hub_port_connect: 36 callbacks suppressed
[29185.393827] usb 3-1-port3: connect-debounce failed
[29185.532098] usb 3-1: USB disconnect, device number 5
[29185.532105] usb 3-1.1: USB disconnect, device number 7
[29186.088061] usb 3-1: new full-speed USB device number 9 using uhci_hcd
[29186.242098] usb 3-1: New USB device found, idVendor=0557, idProduct=7000
[29186.242105] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[29186.245205] hub 3-1:1.0: USB hub found
[29186.247090] hub 3-1:1.0: 4 ports detected
[29186.529092] usb 3-1.1: new low-speed USB device number 10 using uhci_hcd
[29191.685103] usb 3-1.1: new low-speed USB device number 11 using uhci_hcd
[29191.880106] usb 3-1.1: New USB device found, idVendor=0557, idProduct=2213
[29191.880112] usb 3-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[29191.880116] usb 3-1.1: Product: CS-1734A V4.2.416
[29191.880120] usb 3-1.1: Manufacturer: ATEN
[29191.925820] input: ATEN CS-1734A V4.2.416 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.1/3-1.1:1.0/0003:0557:2213.0007/input/input16
[29191.980396] hid-generic 0003:0557:2213.0007: input,hidraw0: USB HID v1.00 Keyboard [ATEN CS-1734A V4.2.416] on usb-0000:00:1d.1-1.1/input0
[29192.010753] input: ATEN CS-1734A V4.2.416 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.1/3-1.1:1.1/0003:0557:2213.0008/input/input17
[29192.011105] hid-generic 0003:0557:2213.0008: input,hidraw1: USB HID v1.00 Mouse [ATEN CS-1734A V4.2.416] on usb-0000:00:1d.1-1.1/input1
[29225.725186] hub 3-1:1.0: hub_port_status failed (err = -71)
[29225.956137] usb 3-1: USB disconnect, device number 9
[29225.956146] usb 3-1.1: USB disconnect, device number 11
[29226.404084] usb 3-1: new full-speed USB device number 12 using uhci_hcd
[29226.553184] usb 3-1: New USB device found, idVendor=0557, idProduct=7000
[29226.553192] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[29226.556402] hub 3-1:1.0: USB hub found
[29226.558176] hub 3-1:1.0: 4 ports detected
[29226.841211] usb 3-1.1: new low-speed USB device number 13 using uhci_hcd
[29232.110091] usb 3-1.1: new low-speed USB device number 14 using uhci_hcd
[29232.304096] usb 3-1.1: New USB device found, idVendor=0557, idProduct=2213
[29232.304104] usb 3-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[29232.304110] usb 3-1.1: Product: CS-1734A V4.2.416
[29232.304115] usb 3-1.1: Manufacturer: ATEN
[29232.350078] input: ATEN CS-1734A V4.2.416 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.1/3-1.1:1.0/0003:0557:2213.0009/input/input18
[29232.404529] hid-generic 0003:0557:2213.0009: input,hidraw0: USB HID v1.00 Keyboard [ATEN CS-1734A V4.2.416] on usb-0000:00:1d.1-1.1/input0
[29232.435987] input: ATEN CS-1734A V4.2.416 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.1/3-1.1:1.1/0003:0557:2213.000A/input/input19
[29232.492322] hid-generic 0003:0557:2213.000A: input,hidraw1: USB HID v1.00 Mouse [ATEN CS-1734A V4.2.416] on usb-0000:00:1d.1-1.1/input1
[29248.669600] usb 3-1.3: new low-speed USB device number 15 using uhci_hcd
[29248.804608] usb 3-1.3: New USB device found, idVendor=046d, idProduct=c506
[29248.804616] usb 3-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[29248.804622] usb 3-1.3: Product: USB Receiver
[29248.804627] usb 3-1.3: Manufacturer: Logitech
[29248.825391] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.3/3-1.3:1.0/0003:046D:C506.000B/input/input20
[29248.825713] hid-generic 0003:046D:C506.000B: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1.3/input0
[36693.592066] usb 1-6: new high-speed USB device number 6 using ehci-pci
[36693.758315] usb 1-6: New USB device found, idVendor=174c, idProduct=55aa
[36693.758321] usb 1-6: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[36693.758324] usb 1-6: Product: 012345678901234567890123456789012345678901234567
[36693.758327] usb 1-6: Manufacturer: 01234567890123456789012345678901234567890123
[36693.758330] usb 1-6: SerialNumber: 0123456789ABCDEF0181
[36693.950076] usb-storage 1-6:1.0: USB Mass Storage device detected
[36693.953550] usb-storage 1-6:1.0: Quirks match for vid 174c pid 55aa: 400000
[36693.953589] scsi host2: usb-storage 1-6:1.0
[36693.954027] usbcore: registered new interface driver usb-storage
[36693.973283] usbcore: registered new interface driver uas
[36701.821306] scsi 2:0:0:0: Direct-Access     WDC WD10 02FAEX-00Z3A0    05.0 PQ: 0 ANSI: 5
[36701.828473] sd 2:0:0:0: Attached scsi generic sg2 type 0
[36701.829047] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[36701.830310] sd 2:0:0:0: [sdb] Write Protect is off
[36701.830317] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[36701.831432] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[36701.857228]  sdb: sdb1
[36701.861563] sd 2:0:0:0: [sdb] Attached SCSI disk
[38291.616437] NVRM: GPU at PCI:0000:01:00: GPU-20e092d3-5961-01a4-282e-a0a1087914f0
[38291.616446] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ChID 0003, Class 00008297, Offset 000015e0, Data 00000000
[38292.832825] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ChID 0003, Class 00008297, Offset 00000f10, Data 44700000
[38298.938669] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ChID 0003, Class 00008297, Offset 00000f10, Data 44700000
[38305.022480] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ChID 0003, Class 00008297, Offset 00000f10, Data 44700000

```




this is smplayer log


```
[18:00:50:889] global_init
[18:00:50:890] global_init: config file: '/home/offir/.config/smplayer/smplayer.ini'
[18:00:50:890] Preferences::load
[18:00:50:890] AssStyles::load
[18:00:50:891] Preferences::load: config_version: 4, CURRENT_CONFIG_VERSION: 4
[18:00:50:891] Translator::loadCatalog: can't load qt_en_US from /usr/share/smplayer/translations
[18:00:50:891] Translator::loadCatalog: can't load qt_en_US from /usr/share/qt4/translations
[18:00:50:891] Translator::loadCatalog: successfully loaded smplayer_en_US from /usr/share/smplayer/translations
[18:00:50:891] This is SMPlayer v. 14.9.0 running on Linux
[18:00:50:891] Compiled with Qt v. 4.8.6, using 4.8.6
[18:00:50:892]  * application path: '/usr/bin'
[18:00:50:892]  * data path: '/usr/share/smplayer'
[18:00:50:892]  * translation path: '/usr/share/smplayer/translations'
[18:00:50:892]  * doc path: '/usr/share/doc/smplayer'
[18:00:50:892]  * themes path: '/usr/share/smplayer/themes'
[18:00:50:892]  * shortcuts path: '/usr/share/smplayer/shortcuts'
[18:00:50:892]  * config path: '/home/offir/.config/smplayer'
[18:00:50:892]  * ini path: '/home/offir/.config/smplayer'
[18:00:50:892]  * file for subtitles' styles: '/home/offir/.config/smplayer/styles.ass'
[18:00:50:892]  * current path: '/home/offir'
[18:00:50:892] SMPlayer::processArgs: arguments: 1
[18:00:50:892] SMPlayer::processArgs: 0 = smplayer
[18:00:50:892] SMPlayer::processArgs: files_to_play: count: 0
[18:00:50:892] SMPlayer::gui: changed working directory to app path
[18:00:50:892] SMPlayer::gui: current directory: /usr/bin
[18:00:50:892] Screen::setAutoHideCursor: 0
[18:00:50:892] Screen::setAutoHideCursor: 0
[18:00:50:919] Core::changeFileSettingsMethod: hash
[18:00:50:919] MplayerLayer::setRepaintBackground: 0
[18:00:50:919] Preferences::monitor_aspect_double
[18:00:50:919]  warning: monitor_aspect couldn't be parsed!
[18:00:50:919]  monitor_aspect set to 0
[18:00:50:949] Playlist::setModified: 0
[18:00:50:954] Playlist::loadSettings
[18:00:50:954] Playlist::addItem: '/media/offir/tv show/tv show/Falling Skies/4/Falling Skies 4x04 Evolve Or Die.mp4'
[18:00:50:954] Playlist::setModified: 0
[18:00:50:954] Playlist::updateView
[18:00:50:954] Playlist::updateView: name: 'Falling Skies 4x04 Evolve Or Die.mp4'
[18:00:50:965] Style name: 'gtk+'
[18:00:50:965] Style class name: 'QGtkStyle'
[18:00:50:980] Favorites::load
[18:00:50:981] Favorites::load
[18:00:50:981] TVList::parse_channels_conf
[18:00:50:981] VList::parse_channels_conf: /home/offir/.mplayer/channels.conf.ter doesn't exist
[18:00:50:981] TVList::parse_channels_conf: can't open /home/offir/.mplayer/channels.conf
[18:00:50:981] Favorites::load
[18:00:50:982] TVList::parse_channels_conf
[18:00:50:982] VList::parse_channels_conf: /home/offir/.mplayer/channels.conf.ter doesn't exist
[18:00:50:982] TVList::parse_channels_conf: can't open /home/offir/.mplayer/channels.conf
[18:00:51:003] BaseGui::initializeMenus
[18:00:51:023] BaseGui::initializeMenus
[18:00:51:024] BaseGui::updateRecents
[18:00:51:024] BaseGui::updateWidgets
[18:00:51:024] Core::changeUseAss: 1
[18:00:51:025] Core::changeSubVisilibity: 1
[18:00:51:025] Core::tellmp: 'sub_visibility 1'
[18:00:51:025] WARNING:  tellmp: no process running: sub_visibility 1
[18:00:51:025] Core::displayMessage
[18:00:51:025] BaseGui::setStayOnTop: 0
[18:00:51:025] BaseGui::setStayOnTop: nothing to do
[18:00:51:025] BaseGui::updateWidgets
[18:00:51:025] BaseGui::updateRecents
[18:00:51:033] BaseGui::initializeMenus
[18:00:51:033] BaseGui::updateRecents
[18:00:51:034] BaseGui::updateWidgets
[18:00:51:034] BaseGuiPlus::loadConfig
[18:00:51:034] DefaultGui::createStatusBar
[18:00:51:035] DefaultGui::createActions
[18:00:51:036] DefaultGui::createControlWidget
[18:00:51:036] DefaultGui::createControlWidgetMini
[18:00:51:036] AutohideWidget::installFilter: child name: "mplayerwindow" 
[18:00:51:036] AutohideWidget::installFilter: child name: "mplayerlayer" 
[18:00:51:036] AutohideWidget::installFilter: child name: "mplayerwindow logo" 
[18:00:51:036] AutohideWidget::installFilter: child name: "" 
[18:00:51:044] BaseGui::initializeMenus
[18:00:51:044] BaseGui::updateRecents
[18:00:51:044] DefaultGui::updateWidgets
[18:00:51:044] BaseGui::updateWidgets
[18:00:51:045] DefaultGui::loadConfig
[18:00:51:045] DesktopInfo::isInsideScreen: geometry of screen: x:0 y:0 w:1280 h:960
[18:00:51:045] ToolbarEditor::load: 'toolbar1'
[18:00:51:045] ToolbarEditor::load: loading action play_prev
[18:00:51:045] ToolbarEditor::load: loading action play
[18:00:51:045] ToolbarEditor::load: loading action pause
[18:00:51:046] ToolbarEditor::load: loading action pl_next
[18:00:51:046] ToolbarEditor::load: loading action screenshot
[18:00:51:046] ToolbarEditor::load: loading action mute
[18:00:51:046] ToolbarEditor::load: loading action mirror
[18:00:51:046] ToolbarEditor::load: loading action flip
[18:00:51:046] ToolbarEditor::load: loading action fullscreen
[18:00:51:046] ToolbarEditor::load: loading action repeat
[18:00:51:046] ToolbarEditor::load: loading action clear_ab_markers
[18:00:51:046] ToolbarEditor::load: loading action set_b_marker
[18:00:51:046] ToolbarEditor::load: loading action set_a_marker
[18:00:51:046] ToolbarEditor::load: 'controlwidget'
[18:00:51:046] ToolbarEditor::load: loading action play_prev
[18:00:51:047] ToolbarEditor::load: loading action play
[18:00:51:047] ToolbarEditor::load: loading action pause_and_frame_step
[18:00:51:047] ToolbarEditor::load: loading action stop
[18:00:51:047] ToolbarEditor::load: loading action play_next
[18:00:51:047] ToolbarEditor::load: loading action timeslider_action
[18:00:51:047] TimeSlider::setDragDelay: 100
[18:00:51:047] ToolbarEditor::load: loading action separator
[18:00:51:047] ToolbarEditor::load: adding separator
[18:00:51:047] ToolbarEditor::load: loading action rotate_menu
[18:00:51:047] ToolbarEditor::load: loading action mirror
[18:00:51:047] ToolbarEditor::load: loading action flip
[18:00:51:047] ToolbarEditor::load: loading action screenshot
[18:00:51:047] ToolbarEditor::load: loading action repeat
[18:00:51:048] ToolbarEditor::load: loading action clear_ab_markers
[18:00:51:048] ToolbarEditor::load: loading action set_b_marker
[18:00:51:048] ToolbarEditor::load: loading action set_a_marker
[18:00:51:048] ToolbarEditor::load: loading action fullscreen
[18:00:51:048] ToolbarEditor::load: loading action mute
[18:00:51:048] ToolbarEditor::load: loading action volumeslider_action
[18:00:51:049] ToolbarEditor::load: 'controlwidget_mini'
[18:00:51:049] ToolbarEditor::load: loading action play_or_pause
[18:00:51:049] ToolbarEditor::load: loading action stop
[18:00:51:049] ToolbarEditor::load: loading action separator
[18:00:51:049] ToolbarEditor::load: adding separator
[18:00:51:049] ToolbarEditor::load: loading action rewind1
[18:00:51:049] ToolbarEditor::load: loading action timeslider_action
[18:00:51:049] TimeSlider::setDragDelay: 100
[18:00:51:049] ToolbarEditor::load: loading action forward1
[18:00:51:050] ToolbarEditor::load: loading action separator
[18:00:51:050] ToolbarEditor::load: adding separator
[18:00:51:050] ToolbarEditor::load: loading action mute
[18:00:51:050] ToolbarEditor::load: loading action volumeslider_action
[18:00:51:050] ToolbarEditor::load: 'floating_control'
[18:00:51:050] ToolbarEditor::load: loading action play
[18:00:51:050] ToolbarEditor::load: loading action pause
[18:00:51:050] ToolbarEditor::load: loading action stop
[18:00:51:050] ToolbarEditor::load: loading action separator
[18:00:51:050] ToolbarEditor::load: adding separator
[18:00:51:051] ToolbarEditor::load: loading action rewindbutton_action
[18:00:51:051] ToolbarEditor::load: loading action timeslider_action
[18:00:51:051] TimeSlider::setDragDelay: 100
[18:00:51:051] ToolbarEditor::load: loading action forwardbutton_action
[18:00:51:051] ToolbarEditor::load: loading action separator
[18:00:51:051] ToolbarEditor::load: adding separator
[18:00:51:051] ToolbarEditor::load: loading action fullscreen
[18:00:51:051] ToolbarEditor::load: loading action mute
[18:00:51:051] ToolbarEditor::load: loading action volumeslider_action
[18:00:51:051] ToolbarEditor::load: loading action separator
[18:00:51:051] ToolbarEditor::load: adding separator
[18:00:51:051] ToolbarEditor::load: loading action timelabel_action
[18:00:51:052] Helper::qtVersion: 4806
[18:00:51:053] DefaultGui::loadConfig: playlist visible: 0
[18:00:51:053] DefaultGui::loadConfig: playlist position: 0, 0
[18:00:51:053] DefaultGui::loadConfig: playlist size: 100 x 30
[18:00:51:053] DefaultGui::updateWidgets
[18:00:51:053] BaseGui::updateWidgets
[18:00:51:063] BaseGui::showEvent
[18:00:51:072] BaseGui::loadActions
[18:00:51:072] ActionsEditor::loadFromConfig
[18:00:51:093] BaseGui::initializeMenus
[18:00:51:093] BaseGui::updateRecents
[18:00:51:094] DefaultGui::updateWidgets
[18:00:51:094] BaseGui::updateWidgets
[18:00:52:025] BaseGui::checkReminder
[18:00:53:025] BaseGui::checkIfUpgraded
[18:00:55:059] BaseGui::showLog

```

---

### Post by Bucky Ball on 2015-07-29
Is this the very last line of dmesg?

```
[38305.022480] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ChID 0003, Class 00008297, Offset 00000f10, Data 44700000
```

Try launchin SMplayer from the command line and when it crashes check the terminal error message.

---

### Post by offir on 2015-07-29
> Is this the very last line of dmesg?
yes (Attached a screenshot)


> 
Try launchin SMplayer from the command line and when it crashes check the terminal error message. 

I will do it

---

### Post by offir on 2015-07-30
> Try launchin SMplayer from the command line and when it crashes check the terminal error message. 

I try to do it
But each time the computer gets stuck
And I go back to desktop after these actions [COLOR="#0000CD"]ctrl + alt +f1[/COLOR]  and [COLOR="#FF0000"]ctrl + alt + f7[/COLOR]

The terminal is closed, and with it what recorded

---

### Post by mc4man on 2015-07-30
smplayer from a terminal would likely be worthless. Set it to save logs. The smplayer log would be auto created in ~/.config/smplayer/, the mplayer/mpv log needs you to set a path/filename, example in screen.
(- did you try what I previously suggested?

---

### Post by offir on 2015-07-31
Yes I did it
Every time the player is closed
the log is Clear



this is smplayer log 
from now

```
[08:51:38:081] global_init
[08:51:38:081] global_init: config file: '/home/offir/.config/smplayer/smplayer.ini'
[08:51:38:081] Preferences::load
[08:51:38:082] AssStyles::load
[08:51:38:083] Preferences::load: config_version: 4, CURRENT_CONFIG_VERSION: 4
[08:51:38:083] Translator::loadCatalog: can't load qt_en_US from /usr/share/smplayer/translations
[08:51:38:083] Translator::loadCatalog: can't load qt_en_US from /usr/share/qt4/translations
[08:51:38:083] Translator::loadCatalog: successfully loaded smplayer_en_US from /usr/share/smplayer/translations
[08:51:38:083] This is SMPlayer v. 14.9.0 running on Linux
[08:51:38:083] Compiled with Qt v. 4.8.6, using 4.8.6
[08:51:38:083]  * application path: '/usr/bin'
[08:51:38:083]  * data path: '/usr/share/smplayer'
[08:51:38:083]  * translation path: '/usr/share/smplayer/translations'
[08:51:38:083]  * doc path: '/usr/share/doc/smplayer'
[08:51:38:083]  * themes path: '/usr/share/smplayer/themes'
[08:51:38:083]  * shortcuts path: '/usr/share/smplayer/shortcuts'
[08:51:38:083]  * config path: '/home/offir/.config/smplayer'
[08:51:38:083]  * ini path: '/home/offir/.config/smplayer'
[08:51:38:083]  * file for subtitles' styles: '/home/offir/.config/smplayer/styles.ass'
[08:51:38:084]  * current path: '/home/offir'
[08:51:38:084] SMPlayer::processArgs: arguments: 1
[08:51:38:084] SMPlayer::processArgs: 0 = smplayer
[08:51:38:084] SMPlayer::processArgs: files_to_play: count: 0
[08:51:38:084] SMPlayer::gui: changed working directory to app path
[08:51:38:084] SMPlayer::gui: current directory: /usr/bin
[08:51:38:084] Screen::setAutoHideCursor: 0
[08:51:38:084] Screen::setAutoHideCursor: 0
[08:51:38:092] Core::changeFileSettingsMethod: hash
[08:51:38:092] MplayerLayer::setRepaintBackground: 0
[08:51:38:092] Preferences::monitor_aspect_double
[08:51:38:092]  warning: monitor_aspect couldn't be parsed!
[08:51:38:092]  monitor_aspect set to 0
[08:51:38:122] Playlist::setModified: 0
[08:51:38:128] Playlist::loadSettings
[08:51:38:128] Playlist::addItem: '/media/offir/tv show/tv show/frasier/Season 6/S06E04 - Hot Ticket.avi'
[08:51:38:129] Playlist::setModified: 0
[08:51:38:129] Playlist::updateView
[08:51:38:129] Playlist::updateView: name: 'S06E04 - Hot Ticket.avi'
[08:51:38:138] Style name: 'gtk+'
[08:51:38:138] Style class name: 'QGtkStyle'
[08:51:38:145] Favorites::load
[08:51:38:146] Favorites::load
[08:51:38:146] TVList::parse_channels_conf
[08:51:38:146] VList::parse_channels_conf: /home/offir/.mplayer/channels.conf.ter doesn't exist
[08:51:38:146] TVList::parse_channels_conf: can't open /home/offir/.mplayer/channels.conf
[08:51:38:147] Favorites::load
[08:51:38:147] TVList::parse_channels_conf
[08:51:38:147] VList::parse_channels_conf: /home/offir/.mplayer/channels.conf.ter doesn't exist
[08:51:38:147] TVList::parse_channels_conf: can't open /home/offir/.mplayer/channels.conf
[08:51:38:159] BaseGui::initializeMenus
[08:51:38:182] BaseGui::initializeMenus
[08:51:38:182] BaseGui::updateRecents
[08:51:38:182] BaseGui::updateWidgets
[08:51:38:182] Core::changeUseAss: 1
[08:51:38:182] Core::changeSubVisilibity: 1
[08:51:38:182] Core::tellmp: 'sub_visibility 1'
[08:51:38:182] WARNING:  tellmp: no process running: sub_visibility 1
[08:51:38:182] Core::displayMessage
[08:51:38:183] BaseGui::setStayOnTop: 0
[08:51:38:183] BaseGui::setStayOnTop: nothing to do
[08:51:38:183] BaseGui::updateWidgets
[08:51:38:183] BaseGui::updateRecents
[08:51:38:191] BaseGui::initializeMenus
[08:51:38:191] BaseGui::updateRecents
[08:51:38:192] BaseGui::updateWidgets
[08:51:38:192] BaseGuiPlus::loadConfig
[08:51:38:192] DefaultGui::createStatusBar
[08:51:38:193] DefaultGui::createActions
[08:51:38:194] DefaultGui::createControlWidget
[08:51:38:194] DefaultGui::createControlWidgetMini
[08:51:38:194] AutohideWidget::installFilter: child name: "mplayerwindow" 
[08:51:38:194] AutohideWidget::installFilter: child name: "mplayerlayer" 
[08:51:38:194] AutohideWidget::installFilter: child name: "mplayerwindow logo" 
[08:51:38:194] AutohideWidget::installFilter: child name: "" 
[08:51:38:201] BaseGui::initializeMenus
[08:51:38:201] BaseGui::updateRecents
[08:51:38:201] DefaultGui::updateWidgets
[08:51:38:201] BaseGui::updateWidgets
[08:51:38:202] DefaultGui::loadConfig
[08:51:38:202] DesktopInfo::isInsideScreen: geometry of screen: x:0 y:0 w:1280 h:960
[08:51:38:203] ToolbarEditor::load: 'toolbar1'
[08:51:38:203] ToolbarEditor::load: loading action play_prev
[08:51:38:203] ToolbarEditor::load: loading action play
[08:51:38:203] ToolbarEditor::load: loading action pause
[08:51:38:203] ToolbarEditor::load: loading action pl_next
[08:51:38:203] ToolbarEditor::load: loading action screenshot
[08:51:38:203] ToolbarEditor::load: loading action mute
[08:51:38:203] ToolbarEditor::load: loading action mirror
[08:51:38:203] ToolbarEditor::load: loading action flip
[08:51:38:204] ToolbarEditor::load: loading action fullscreen
[08:51:38:204] ToolbarEditor::load: loading action repeat
[08:51:38:204] ToolbarEditor::load: loading action clear_ab_markers
[08:51:38:204] ToolbarEditor::load: loading action set_b_marker
[08:51:38:204] ToolbarEditor::load: loading action set_a_marker
[08:51:38:204] ToolbarEditor::load: 'controlwidget'
[08:51:38:204] ToolbarEditor::load: loading action play_prev
[08:51:38:204] ToolbarEditor::load: loading action play
[08:51:38:204] ToolbarEditor::load: loading action pause_and_frame_step
[08:51:38:204] ToolbarEditor::load: loading action stop
[08:51:38:204] ToolbarEditor::load: loading action play_next
[08:51:38:205] ToolbarEditor::load: loading action timeslider_action
[08:51:38:205] TimeSlider::setDragDelay: 100
[08:51:38:205] ToolbarEditor::load: loading action separator
[08:51:38:205] ToolbarEditor::load: adding separator
[08:51:38:205] ToolbarEditor::load: loading action rotate_menu
[08:51:38:205] ToolbarEditor::load: loading action mirror
[08:51:38:205] ToolbarEditor::load: loading action flip
[08:51:38:205] ToolbarEditor::load: loading action screenshot
[08:51:38:205] ToolbarEditor::load: loading action repeat
[08:51:38:206] ToolbarEditor::load: loading action clear_ab_markers
[08:51:38:206] ToolbarEditor::load: loading action set_b_marker
[08:51:38:206] ToolbarEditor::load: loading action set_a_marker
[08:51:38:206] ToolbarEditor::load: loading action fullscreen
[08:51:38:206] ToolbarEditor::load: loading action mute
[08:51:38:206] ToolbarEditor::load: loading action volumeslider_action
[08:51:38:206] ToolbarEditor::load: 'controlwidget_mini'
[08:51:38:207] ToolbarEditor::load: loading action play_or_pause
[08:51:38:207] ToolbarEditor::load: loading action stop
[08:51:38:207] ToolbarEditor::load: loading action separator
[08:51:38:207] ToolbarEditor::load: adding separator
[08:51:38:207] ToolbarEditor::load: loading action rewind1
[08:51:38:207] ToolbarEditor::load: loading action timeslider_action
[08:51:38:208] TimeSlider::setDragDelay: 100
[08:51:38:208] ToolbarEditor::load: loading action forward1
[08:51:38:208] ToolbarEditor::load: loading action separator
[08:51:38:208] ToolbarEditor::load: adding separator
[08:51:38:208] ToolbarEditor::load: loading action mute
[08:51:38:208] ToolbarEditor::load: loading action volumeslider_action
[08:51:38:208] ToolbarEditor::load: 'floating_control'
[08:51:38:209] ToolbarEditor::load: loading action play
[08:51:38:209] ToolbarEditor::load: loading action pause
[08:51:38:209] ToolbarEditor::load: loading action stop
[08:51:38:209] ToolbarEditor::load: loading action separator
[08:51:38:209] ToolbarEditor::load: adding separator
[08:51:38:209] ToolbarEditor::load: loading action rewindbutton_action
[08:51:38:210] ToolbarEditor::load: loading action timeslider_action
[08:51:38:210] TimeSlider::setDragDelay: 100
[08:51:38:210] ToolbarEditor::load: loading action forwardbutton_action
[08:51:38:211] ToolbarEditor::load: loading action separator
[08:51:38:211] ToolbarEditor::load: adding separator
[08:51:38:211] ToolbarEditor::load: loading action fullscreen
[08:51:38:211] ToolbarEditor::load: loading action mute
[08:51:38:211] ToolbarEditor::load: loading action volumeslider_action
[08:51:38:211] ToolbarEditor::load: loading action separator
[08:51:38:211] ToolbarEditor::load: adding separator
[08:51:38:211] ToolbarEditor::load: loading action timelabel_action
[08:51:38:212] Helper::qtVersion: 4806
[08:51:38:214] DefaultGui::loadConfig: playlist visible: 0
[08:51:38:214] DefaultGui::loadConfig: playlist position: 0, 0
[08:51:38:214] DefaultGui::loadConfig: playlist size: 100 x 30
[08:51:38:214] DefaultGui::updateWidgets
[08:51:38:214] BaseGui::updateWidgets
[08:51:38:218] BaseGui::showEvent
[08:51:38:224] BaseGui::loadActions
[08:51:38:225] ActionsEditor::loadFromConfig
[08:51:38:252] BaseGui::initializeMenus
[08:51:38:253] BaseGui::updateRecents
[08:51:38:253] DefaultGui::updateWidgets
[08:51:38:253] BaseGui::updateWidgets
[08:51:39:183] BaseGui::checkReminder
[08:51:40:183] BaseGui::checkIfUpgraded
[08:51:41:695] BaseGui::showLog
[08:53:05:546] BaseGui::showLog
[08:53:32:910] BaseGui::showMplayerLog
[08:53:44:682] BaseGui::showPreferencesDialog
[08:53:44:697] InfoReader::run: '-identify -vo help -ao help -demuxer help -vc help -ac help'
[08:53:44:697] InfoReader::run: using QProcess
[08:53:44:839] InfoReader::run : terminating
[08:53:44:839] InfoReader::readLine: line: 'MPlayer2 2.0-728-g2c378c7-4 (C) 2000-2012 MPlayer Team'
[08:53:44:840] InfoReader::readLine: line: 'Available video output drivers:'
[08:53:44:840] InfoReader::readLine: line: 'ID_VIDEO_OUTPUTS'
[08:53:44:840] InfoReader::readLine: found key: vo
[08:53:44:840] InfoReader::readLine: line: '	vdpau	VDPAU with X11'
[08:53:44:840] InfoReader::readLine: found driver: 'vdpau' 'VDPAU with X11'
[08:53:44:840] InfoReader::readLine: line: '	xv	X11/Xv'
[08:53:44:840] InfoReader::readLine: found driver: 'xv' 'X11/Xv'
[08:53:44:840] InfoReader::readLine: line: '	gl3	OpenGL 3.x'
[08:53:44:840] InfoReader::readLine: found driver: 'gl3' 'OpenGL 3.x'
[08:53:44:840] InfoReader::readLine: line: '	gl	OpenGL'
[08:53:44:840] InfoReader::readLine: found driver: 'gl' 'OpenGL'
[08:53:44:840] InfoReader::readLine: line: '	x11	X11 ( XImage/Shm )'
[08:53:44:840] InfoReader::readLine: found driver: 'x11' 'X11 ( XImage/Shm )'
[08:53:44:840] InfoReader::readLine: line: '	sdl	SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)'
[08:53:44:840] InfoReader::readLine: found driver: 'sdl' 'SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)'
[08:53:44:840] InfoReader::readLine: line: '	caca	libcaca'
[08:53:44:840] InfoReader::readLine: found driver: 'caca' 'libcaca'
[08:53:44:840] InfoReader::readLine: line: '	v4l2	V4L2 MPEG Video Decoder Output'
[08:53:44:840] InfoReader::readLine: found driver: 'v4l2' 'V4L2 MPEG Video Decoder Output'
[08:53:44:840] InfoReader::readLine: line: '	null	Null video output'
[08:53:44:840] InfoReader::readLine: found driver: 'null' 'Null video output'
[08:53:44:841] InfoReader::readLine: line: '	directfb	Direct Framebuffer Device'
[08:53:44:841] InfoReader::readLine: found driver: 'directfb' 'Direct Framebuffer Device'
[08:53:44:841] InfoReader::readLine: line: '	yuv4mpeg	yuv4mpeg output for mjpegtools'
[08:53:44:841] InfoReader::readLine: found driver: 'yuv4mpeg' 'yuv4mpeg output for mjpegtools'
[08:53:44:841] InfoReader::readLine: line: '	png	PNG file'
[08:53:44:841] InfoReader::readLine: found driver: 'png' 'PNG file'
[08:53:44:841] InfoReader::readLine: line: '	jpeg	JPEG file'
[08:53:44:841] InfoReader::readLine: found driver: 'jpeg' 'JPEG file'
[08:53:44:841] InfoReader::readLine: line: '	gif89a	animated GIF output'
[08:53:44:841] InfoReader::readLine: found driver: 'gif89a' 'animated GIF output'
[08:53:44:841] InfoReader::readLine: line: '	tga	Targa output'
[08:53:44:841] InfoReader::readLine: found driver: 'tga' 'Targa output'
[08:53:44:841] InfoReader::readLine: line: '	pnm	PPM/PGM/PGMYUV file'
[08:53:44:841] InfoReader::readLine: found driver: 'pnm' 'PPM/PGM/PGMYUV file'
[08:53:44:841] InfoReader::readLine: line: '	md5sum	md5sum of each frame'
[08:53:44:841] InfoReader::readLine: found driver: 'md5sum' 'md5sum of each frame'
[08:53:44:841] InfoReader::readLine: line: '	gl_nosw	OpenGL no software rendering'
[08:53:44:841] InfoReader::readLine: found driver: 'gl_nosw' 'OpenGL no software rendering'
[08:53:44:841] InfoReader::readLine: line: 'Available audio output drivers:'
[08:53:44:841] WARNING: InfoReader::readLine: can't parse output driver from line 'Available audio output drivers:'
[08:53:44:841] InfoReader::readLine: line: 'ID_AUDIO_OUTPUTS'
[08:53:44:841] WARNING: InfoReader::readLine: can't parse output driver from line 'ID_AUDIO_OUTPUTS'
[08:53:44:842] InfoReader::readLine: found key: ao
[08:53:44:842] InfoReader::readLine: line: '	pulse	PulseAudio audio output'
[08:53:44:842] InfoReader::readLine: found driver: 'pulse' 'PulseAudio audio output'
[08:53:44:842] InfoReader::readLine: line: '	alsa	ALSA-0.9.x-1.x audio output'
[08:53:44:842] InfoReader::readLine: found driver: 'alsa' 'ALSA-0.9.x-1.x audio output'
[08:53:44:842] InfoReader::readLine: line: '	oss	OSS/ioctl audio output'
[08:53:44:842] InfoReader::readLine: found driver: 'oss' 'OSS/ioctl audio output'
[08:53:44:842] InfoReader::readLine: line: '	jack	JACK audio output'
[08:53:44:842] InfoReader::readLine: found driver: 'jack' 'JACK audio output'
[08:53:44:842] InfoReader::readLine: line: '	sdl	SDLlib audio output'
[08:53:44:842] InfoReader::readLine: found driver: 'sdl' 'SDLlib audio output'
[08:53:44:842] InfoReader::readLine: line: '	v4l2	V4L2 MPEG Audio Decoder output'
[08:53:44:842] InfoReader::readLine: found driver: 'v4l2' 'V4L2 MPEG Audio Decoder output'
[08:53:44:842] InfoReader::readLine: line: '	null	Null audio output'
[08:53:44:842] InfoReader::readLine: found driver: 'null' 'Null audio output'
[08:53:44:842] InfoReader::readLine: line: '	pcm	RAW PCM/WAVE file writer audio output'
[08:53:44:842] InfoReader::readLine: found driver: 'pcm' 'RAW PCM/WAVE file writer audio output'
[08:53:44:842] InfoReader::readLine: line: 'Available audio codecs:'
[08:53:44:842] WARNING: InfoReader::readLine: can't parse output driver from line 'Available audio codecs:'
[08:53:44:842] InfoReader::readLine: line: 'ID_AUDIO_CODECS'
[08:53:44:842] WARNING: InfoReader::readLine: can't parse output driver from line 'ID_AUDIO_CODECS'
[08:53:44:842] InfoReader::readLine: found key: ac
[08:53:44:843] InfoReader::readLine: line: 'ac:     afm:      status:   info:  [lib/dll]'
[08:53:44:843] WARNING: InfoReader::readLine: can't parse codec from line 'ac:     afm:      status:   info:  [lib/dll]'
[08:53:44:843] InfoReader::readLine: line: 'lavc        ffmpeg    problems  Generic libavcodec decoder'
[08:53:44:843] InfoReader::readLine: found codec: 'lavc' 'Generic libavcodec decoder'
[08:53:44:843] InfoReader::readLine: line: 'wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]'
[08:53:44:843] InfoReader::readLine: found codec: 'wma9dmo' 'Windows Media Audio 9 DMO  [wma9dmod.dll]'
[08:53:44:843] InfoReader::readLine: line: 'wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]'
[08:53:44:843] InfoReader::readLine: found codec: 'wmadmo' 'Windows Media Audio DMO  [wmadmod.dll]'
[08:53:44:843] InfoReader::readLine: line: 'wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]'
[08:53:44:843] InfoReader::readLine: found codec: 'wma9spdmo' 'Windows Media Audio 9 Speech DMO  [wmspdmod.dll]'
[08:53:44:843] InfoReader::readLine: line: 'wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax]'
[08:53:44:843] InfoReader::readLine: found codec: 'wma9spdshow' 'Windows Media Audio 9 Speech DShow  [wmavds32.ax]'
[08:53:44:843] InfoReader::readLine: line: 'ffqdm2      ffmpeg    working   FFmpeg QDM2 audio  [qdm2]'
[08:53:44:843] InfoReader::readLine: found codec: 'ffqdm2' 'FFmpeg QDM2 audio  [qdm2]'
[08:53:44:843] InfoReader::readLine: line: 'qdmc        qtaudio   working   QuickTime QDMC/QDM2 audio  [QuickTime.qts]'
[08:53:44:843] InfoReader::readLine: found codec: 'qdmc' 'QuickTime QDMC/QDM2 audio  [QuickTime.qts]'
[08:53:44:843] InfoReader::readLine: line: 'ffqclp      ffmpeg    working   FFmpeg QCLP audio  [qcelp]'
[08:53:44:843] InfoReader::readLine: found codec: 'ffqclp' 'FFmpeg QCLP audio  [qcelp]'
[08:53:44:844] InfoReader::readLine: line: 'qclp        qtaudio   working   QuickTime QCLP audio  [QuickTime.qts]'
[08:53:44:844] InfoReader::readLine: found codec: 'qclp' 'QuickTime QCLP audio  [QuickTime.qts]'
[08:53:44:844] InfoReader::readLine: line: 'qtmace3     qtaudio   working   QuickTime MACE3 audio  [QuickTime.qts]'
[08:53:44:844] InfoReader::readLine: found codec: 'qtmace3' 'QuickTime MACE3 audio  [QuickTime.qts]'
[08:53:44:844] InfoReader::readLine: line: 'qtmace6     qtaudio   working   QuickTime MACE6 audio  [QuickTime.qts]'
[08:53:44:844] InfoReader::readLine: found codec: 'qtmace6' 'QuickTime MACE6 audio  [QuickTime.qts]'
[08:53:44:844] InfoReader::readLine: line: 'zygoaudio   qtaudio   working   Zygo audio  [ZyGoAudioS.qtx]'
[08:53:44:844] InfoReader::readLine: found codec: 'zygoaudio' 'Zygo audio  [ZyGoAudioS.qtx]'
[08:53:44:844] InfoReader::readLine: line: 'ffra144     ffmpeg    working   FFmpeg RealAudio 1.0  [real_144]'
[08:53:44:845] InfoReader::readLine: found codec: 'ffra144' 'FFmpeg RealAudio 1.0  [real_144]'
[08:53:44:845] InfoReader::readLine: line: 'ffra288     ffmpeg    working   FFmpeg RealAudio 2.0  [real_288]'
[08:53:44:845] InfoReader::readLine: found codec: 'ffra288' 'FFmpeg RealAudio 2.0  [real_288]'
[08:53:44:845] InfoReader::readLine: line: 'ffcook      ffmpeg    working   FFmpeg COOK audio  [cook]'
[08:53:44:845] InfoReader::readLine: found codec: 'ffcook' 'FFmpeg COOK audio  [cook]'
[08:53:44:845] InfoReader::readLine: line: 'ffatrc      ffmpeg    working   FFmpeg Atrac 3 audio  [atrac3]'
[08:53:44:845] InfoReader::readLine: found codec: 'ffatrc' 'FFmpeg Atrac 3 audio  [atrac3]'
[08:53:44:845] InfoReader::readLine: line: 'ffsipr      ffmpeg    working   FFmpeg Sipr/Acelp.net audio  [sipr]'
[08:53:44:845] InfoReader::readLine: found codec: 'ffsipr' 'FFmpeg Sipr/Acelp.net audio  [sipr]'
[08:53:44:845] InfoReader::readLine: line: 'ra144       realaud   working   RealAudio 1.0  [14_4.so.6.0]'
[08:53:44:845] InfoReader::readLine: found codec: 'ra144' 'RealAudio 1.0  [14_4.so.6.0]'
[08:53:44:845] InfoReader::readLine: line: 'ra144win    realaud   working   Win32 RealAudio 1.0  [14_43260.dll]'
[08:53:44:845] InfoReader::readLine: found codec: 'ra144win' 'Win32 RealAudio 1.0  [14_43260.dll]'
[08:53:44:845] InfoReader::readLine: line: 'ra144mac    realaud   working   Mac OS X RealAudio 1.0  [14_4.shlb]'
[08:53:44:845] InfoReader::readLine: found codec: 'ra144mac' 'Mac OS X RealAudio 1.0  [14_4.shlb]'
[08:53:44:845] InfoReader::readLine: line: 'ra288       realaud   working   RealAudio 2.0  [28_8.so.6.0]'
[08:53:44:845] InfoReader::readLine: found codec: 'ra288' 'RealAudio 2.0  [28_8.so.6.0]'
[08:53:44:846] InfoReader::readLine: line: 'ra288win    realaud   working   Win32 RealAudio 2.0  [28_83260.dll]'
[08:53:44:846] InfoReader::readLine: found codec: 'ra288win' 'Win32 RealAudio 2.0  [28_83260.dll]'
[08:53:44:846] InfoReader::readLine: line: 'ra288mac    realaud   working   Mac OS X RealAudio 2.0  [28_8.shlb]'
[08:53:44:846] InfoReader::readLine: found codec: 'ra288mac' 'Mac OS X RealAudio 2.0  [28_8.shlb]'
[08:53:44:846] InfoReader::readLine: line: 'ra10cook    realaud   working   RealPlayer 10 COOK audio  [cook.so]'
[08:53:44:846] InfoReader::readLine: found codec: 'ra10cook' 'RealPlayer 10 COOK audio  [cook.so]'
[08:53:44:846] InfoReader::readLine: line: 'racook      realaud   working   RealAudio COOK  [cook.so.6.0]'
[08:53:44:846] InfoReader::readLine: found codec: 'racook' 'RealAudio COOK  [cook.so.6.0]'
[08:53:44:846] InfoReader::readLine: line: 'ra10cookwin realaud   working   Win32 RealAudio 10 COOK  [cook.dll]'
[08:53:44:846] InfoReader::readLine: found codec: 'ra10cookwin' 'Win32 RealAudio 10 COOK  [cook.dll]'
[08:53:44:846] InfoReader::readLine: line: 'racookwin   realaud   working   Win32 RealAudio COOK  [cook3260.dll]'
[08:53:44:846] InfoReader::readLine: found codec: 'racookwin' 'Win32 RealAudio COOK  [cook3260.dll]'
[08:53:44:846] InfoReader::readLine: line: 'racookmac   realaud   working   Mac OS X RealAudio COOK  [cook.bundle/Contents/MacOS/cook]'
[08:53:44:846] InfoReader::readLine: found codec: 'racookmac' 'Mac OS X RealAudio COOK  [cook.bundle/Contents/MacOS/cook]'
[08:53:44:846] InfoReader::readLine: line: 'rasipr      realaud   working   RealAudio Sipro  [sipr.so.6.0]'
[08:53:44:846] InfoReader::readLine: found codec: 'rasipr' 'RealAudio Sipro  [sipr.so.6.0]'
[08:53:44:846] InfoReader::readLine: line: 'ra10sipr    realaud   working   RealPlayer 10 RealAudio Sipro  [sipr.so]'
[08:53:44:847] InfoReader::readLine: found codec: 'ra10sipr' 'RealPlayer 10 RealAudio Sipro  [sipr.so]'
[08:53:44:847] InfoReader::readLine: line: 'ra10siprwin realaud   working   Win32 RealAudio 10 Sipro  [sipr.dll]'
[08:53:44:847] InfoReader::readLine: found codec: 'ra10siprwin' 'Win32 RealAudio 10 Sipro  [sipr.dll]'
[08:53:44:847] InfoReader::readLine: line: 'rasiprwin   realaud   working   Win32 RealAudio Sipro  [sipr3260.dll]'
[08:53:44:847] InfoReader::readLine: found codec: 'rasiprwin' 'Win32 RealAudio Sipro  [sipr3260.dll]'
[08:53:44:847] InfoReader::readLine: line: 'rasiprmac   realaud   working   Mac OS X RealAudio Sipro  [sipr.bundle/Contents/MacOS/sipr]'
[08:53:44:847] InfoReader::readLine: found codec: 'rasiprmac' 'Mac OS X RealAudio Sipro  [sipr.bundle/Contents/MacOS/sipr]'
[08:53:44:847] InfoReader::readLine: line: 'raatrc      realaud   working   RealAudio ATRAC3  [atrc.so.6.0]'
[08:53:44:847] InfoReader::readLine: found codec: 'raatrc' 'RealAudio ATRAC3  [atrc.so.6.0]'
[08:53:44:847] InfoReader::readLine: line: 'ra10atrc    realaud   working   RealPlayer 10 RealAudio ATRAC3  [atrc.so]'
[08:53:44:847] InfoReader::readLine: found codec: 'ra10atrc' 'RealPlayer 10 RealAudio ATRAC3  [atrc.so]'
[08:53:44:847] InfoReader::readLine: line: 'ra10atrcwin realaud   working   Win32 RealAudio 10 ATRAC3  [atrc.dll]'
[08:53:44:847] InfoReader::readLine: found codec: 'ra10atrcwin' 'Win32 RealAudio 10 ATRAC3  [atrc.dll]'
[08:53:44:847] InfoReader::readLine: line: 'raatrcwin   realaud   working   Win32 RealAudio ATRAC3  [atrc3260.dll]'
[08:53:44:847] InfoReader::readLine: found codec: 'raatrcwin' 'Win32 RealAudio ATRAC3  [atrc3260.dll]'
[08:53:44:847] InfoReader::readLine: line: 'raatrcmac   realaud   working   Mac OS X RealAudio ATRAC3  [atrc.bundle/Contents/MacOS/atrc]'
[08:53:44:847] InfoReader::readLine: found codec: 'raatrcmac' 'Mac OS X RealAudio ATRAC3  [atrc.bundle/Contents/MacOS/atrc]'
[08:53:44:847] InfoReader::readLine: line: 'ffadpcmadx  ffmpeg    working   FFmpeg SEGA CRI adx codec  [adpcm_adx]'
[08:53:44:848] InfoReader::readLine: found codec: 'ffadpcmadx' 'FFmpeg SEGA CRI adx codec  [adpcm_adx]'
[08:53:44:848] InfoReader::readLine: line: 'ffadpcmimaamv ffmpeg    working   FFmpeg AMV IMA ADPCM audio  [adpcm_ima_amv]'
[08:53:44:848] InfoReader::readLine: found codec: 'ffadpcmimaamv' 'FFmpeg AMV IMA ADPCM audio  [adpcm_ima_amv]'
[08:53:44:848] InfoReader::readLine: line: 'ffadpcmimaqt ffmpeg    working   FFmpeg QT IMA ADPCM audio  [adpcm_ima_qt]'
[08:53:44:848] InfoReader::readLine: found codec: 'ffadpcmimaqt' 'FFmpeg QT IMA ADPCM audio  [adpcm_ima_qt]'
[08:53:44:848] InfoReader::readLine: line: 'ffadpcmimawav ffmpeg    working   FFmpeg WAV IMA ADPCM audio  [adpcm_ima_wav]'
[08:53:44:848] InfoReader::readLine: found codec: 'ffadpcmimawav' 'FFmpeg WAV IMA ADPCM audio  [adpcm_ima_wav]'
[08:53:44:848] InfoReader::readLine: line: 'imaadpcm    imaadpcm  working   IMA ADPCM'
[08:53:44:848] InfoReader::readLine: found codec: 'imaadpcm' 'IMA ADPCM'
[08:53:44:848] InfoReader::readLine: line: 'ffadpcmms   ffmpeg    working   FFmpeg MS ADPCM audio  [adpcm_ms]'
[08:53:44:848] InfoReader::readLine: found codec: 'ffadpcmms' 'FFmpeg MS ADPCM audio  [adpcm_ms]'
[08:53:44:848] InfoReader::readLine: line: 'msadpcm     msadpcm   working   MS ADPCM'
[08:53:44:848] InfoReader::readLine: found codec: 'msadpcm' 'MS ADPCM'
[08:53:44:848] InfoReader::readLine: line: 'ffadpcmimadk4 ffmpeg    working   FFmpeg DK4 IMA ADPCM audio  [adpcm_ima_dk4]'
[08:53:44:848] InfoReader::readLine: found codec: 'ffadpcmimadk4' 'FFmpeg DK4 IMA ADPCM audio  [adpcm_ima_dk4]'
[08:53:44:848] InfoReader::readLine: line: 'dk4adpcm    imaadpcm  working   Duck DK4 ADPCM (rogue format number)'
[08:53:44:848] InfoReader::readLine: found codec: 'dk4adpcm' 'Duck DK4 ADPCM (rogue format number)'
[08:53:44:848] InfoReader::readLine: line: 'ffadpcmimadk3 ffmpeg    working   FFmpeg DK3 IMA ADPCM audio  [adpcm_ima_dk3]'
[08:53:44:849] InfoReader::readLine: found codec: 'ffadpcmimadk3' 'FFmpeg DK3 IMA ADPCM audio  [adpcm_ima_dk3]'
[08:53:44:849] InfoReader::readLine: line: 'dk3adpcm    dk3adpcm  working   Duck DK3 ADPCM (rogue format number)'
[08:53:44:849] InfoReader::readLine: found codec: 'dk3adpcm' 'Duck DK3 ADPCM (rogue format number)'
[08:53:44:849] InfoReader::readLine: line: 'ffroqaudio  ffmpeg    working   Id RoQ File Audio  [roq_dpcm]'
[08:53:44:849] InfoReader::readLine: found codec: 'ffroqaudio' 'Id RoQ File Audio  [roq_dpcm]'
[08:53:44:849] InfoReader::readLine: line: 'ffsmkaud    ffmpeg    problems  FFmpeg Smacker Audio  [smackaud]'
[08:53:44:849] InfoReader::readLine: found codec: 'ffsmkaud' 'FFmpeg Smacker Audio  [smackaud]'
[08:53:44:849] InfoReader::readLine: line: 'ffbinkdctaud ffmpeg    problems  FFmpeg Bink Audio (DCT)  [binkaudio_dct]'
[08:53:44:849] InfoReader::readLine: found codec: 'ffbinkdctaud' 'FFmpeg Bink Audio (DCT)  [binkaudio_dct]'
[08:53:44:849] InfoReader::readLine: line: 'ffbinkrdftaud ffmpeg    working   FFmpeg Bink Audio (RDFT)  [binkaudio_rdft]'
[08:53:44:849] InfoReader::readLine: found codec: 'ffbinkrdftaud' 'FFmpeg Bink Audio (RDFT)  [binkaudio_rdft]'
[08:53:44:849] InfoReader::readLine: line: 'ffdsicinaudio ffmpeg    working   FFmpeg Delphine CIN audio  [dsicinaudio]'
[08:53:44:849] InfoReader::readLine: found codec: 'ffdsicinaudio' 'FFmpeg Delphine CIN audio  [dsicinaudio]'
[08:53:44:849] InfoReader::readLine: line: 'ff4xmadmpcm ffmpeg    working   FFmpeg 4XM ADPCM audio  [adpcm_4xm]'
[08:53:44:849] InfoReader::readLine: found codec: 'ff4xmadmpcm' 'FFmpeg 4XM ADPCM audio  [adpcm_4xm]'
[08:53:44:849] InfoReader::readLine: line: 'ffadpcmimaws ffmpeg    working   FFmpeg Westwood IMA ADPCM audio  [adpcm_ima_ws]'
[08:53:44:849] InfoReader::readLine: found codec: 'ffadpcmimaws' 'FFmpeg Westwood IMA ADPCM audio  [adpcm_ima_ws]'
[08:53:44:849] InfoReader::readLine: line: 'ffwssnd1    ffmpeg    working   FFmpeg Westwood SND1  [ws_snd1]'
[08:53:44:849] InfoReader::readLine: found codec: 'ffwssnd1' 'FFmpeg Westwood SND1  [ws_snd1]'
[08:53:44:850] InfoReader::readLine: line: 'ffinterplaydpcm ffmpeg    working   FFmpeg Interplay DPCM audio  [interplay_dpcm]'
[08:53:44:850] InfoReader::readLine: found codec: 'ffinterplaydpcm' 'FFmpeg Interplay DPCM audio  [interplay_dpcm]'
[08:53:44:850] InfoReader::readLine: line: 'ffadpcmea   ffmpeg    working   FFmpeg EA ADPCM audio  [adpcm_ea]'
[08:53:44:850] InfoReader::readLine: found codec: 'ffadpcmea' 'FFmpeg EA ADPCM audio  [adpcm_ea]'
[08:53:44:850] InfoReader::readLine: line: 'ffadpcmeamaxis ffmpeg    working   FFmpeg EA MAXIS XA ADPCM audio  [adpcm_ea_maxis_xa]'
[08:53:44:850] InfoReader::readLine: found codec: 'ffadpcmeamaxis' 'FFmpeg EA MAXIS XA ADPCM audio  [adpcm_ea_maxis_xa]'
[08:53:44:850] InfoReader::readLine: line: 'ffadpcmxa   ffmpeg    working   FFmpeg XA ADPCM audio  [adpcm_xa]'
[08:53:44:850] InfoReader::readLine: found codec: 'ffadpcmxa' 'FFmpeg XA ADPCM audio  [adpcm_xa]'
[08:53:44:850] InfoReader::readLine: line: 'ffxandpcm   ffmpeg    working   FFmpeg XAN DPCM audio  [xan_dpcm]'
[08:53:44:850] InfoReader::readLine: found codec: 'ffxandpcm' 'FFmpeg XAN DPCM audio  [xan_dpcm]'
[08:53:44:850] InfoReader::readLine: line: 'ffyamahaadpcm ffmpeg    working   FFmpeg Yamaha ADPCM audio  [adpcm_yamaha]'
[08:53:44:850] InfoReader::readLine: found codec: 'ffyamahaadpcm' 'FFmpeg Yamaha ADPCM audio  [adpcm_yamaha]'
[08:53:44:850] InfoReader::readLine: line: 'ffadpcmthp  ffmpeg    working   FFmpeg THP ADPCM audio  [adpcm_thp]'
[08:53:44:850] InfoReader::readLine: found codec: 'ffadpcmthp' 'FFmpeg THP ADPCM audio  [adpcm_thp]'
[08:53:44:850] InfoReader::readLine: line: 'libdv       libdv     working   raw DV audio (libdv)  [libdv.so.2]'
[08:53:44:850] InfoReader::readLine: found codec: 'libdv' 'raw DV audio (libdv)  [libdv.so.2]'
[08:53:44:850] InfoReader::readLine: line: 'ffdv        ffmpeg    working   FFmpeg DV audio  [dvaudio]'
[08:53:44:851] InfoReader::readLine: found codec: 'ffdv' 'FFmpeg DV audio  [dvaudio]'
[08:53:44:851] InfoReader::readLine: line: 'fflatm      ffmpeg    working   FFmpeg AAC in LATM  [aac_latm]'
[08:53:44:851] InfoReader::readLine: found codec: 'fflatm' 'FFmpeg AAC in LATM  [aac_latm]'
[08:53:44:851] InfoReader::readLine: line: 'ffaac       ffmpeg    working   FFmpeg AAC (MPEG-2/MPEG-4 Audio)  [aac]'
[08:53:44:851] InfoReader::readLine: found codec: 'ffaac' 'FFmpeg AAC (MPEG-2/MPEG-4 Audio)  [aac]'
[08:53:44:851] InfoReader::readLine: line: 'ffflac      ffmpeg    working   FFmpeg FLAC audio  [flac]'
[08:53:44:851] InfoReader::readLine: found codec: 'ffflac' 'FFmpeg FLAC audio  [flac]'
[08:53:44:851] InfoReader::readLine: line: 'ffalac      ffmpeg    working   FFmpeg ALAC audio  [alac]'
[08:53:44:851] InfoReader::readLine: found codec: 'ffalac' 'FFmpeg ALAC audio  [alac]'
[08:53:44:851] InfoReader::readLine: line: 'fftta       ffmpeg    working   FFmpeg True Audio (TTA)  [tta]'
[08:53:44:851] InfoReader::readLine: found codec: 'fftta' 'FFmpeg True Audio (TTA)  [tta]'
[08:53:44:851] InfoReader::readLine: line: 'ffwavpack   ffmpeg    working   FFmpeg WavPack audio  [wavpack]'
[08:53:44:851] InfoReader::readLine: found codec: 'ffwavpack' 'FFmpeg WavPack audio  [wavpack]'
[08:53:44:851] InfoReader::readLine: line: 'ffshorten   ffmpeg    working   FFmpeg Shorten audio  [shorten]'
[08:53:44:851] InfoReader::readLine: found codec: 'ffshorten' 'FFmpeg Shorten audio  [shorten]'
[08:53:44:851] InfoReader::readLine: line: 'ffape       ffmpeg    working   FFmpeg Monkey's Audio  [ape]'
[08:53:44:851] InfoReader::readLine: found codec: 'ffape' 'FFmpeg Monkey's Audio  [ape]'
[08:53:44:851] InfoReader::readLine: line: 'ffals       ffmpeg    working   FFmpeg ALS  [als]'
[08:53:44:851] InfoReader::readLine: found codec: 'ffals' 'FFmpeg ALS  [als]'
[08:53:44:851] InfoReader::readLine: line: 'ffmlp       ffmpeg    working   FFmpeg MLP  [mlp]'
[08:53:44:852] InfoReader::readLine: found codec: 'ffmlp' 'FFmpeg MLP  [mlp]'
[08:53:44:852] InfoReader::readLine: line: 'fftruehd    ffmpeg    working   FFmpeg TrueHD  [truehd]'
[08:53:44:852] InfoReader::readLine: found codec: 'fftruehd' 'FFmpeg TrueHD  [truehd]'
[08:53:44:852] InfoReader::readLine: line: 'ffnellymoser ffmpeg    working   FFmpeg Nellymoser Audio  [nellymoser]'
[08:53:44:852] InfoReader::readLine: found codec: 'ffnellymoser' 'FFmpeg Nellymoser Audio  [nellymoser]'
[08:53:44:852] InfoReader::readLine: line: 'faad        faad      working   FAAD AAC (MPEG-2/MPEG-4 Audio)  [libfaad2]'
[08:53:44:852] InfoReader::readLine: found codec: 'faad' 'FAAD AAC (MPEG-2/MPEG-4 Audio)  [libfaad2]'
[08:53:44:852] InfoReader::readLine: line: 'pcm         pcm       working   Uncompressed PCM'
[08:53:44:852] InfoReader::readLine: found codec: 'pcm' 'Uncompressed PCM'
[08:53:44:852] InfoReader::readLine: line: 'divx        acm       working   DivX audio (WMA)  [divxa32.acm]'
[08:53:44:852] InfoReader::readLine: found codec: 'divx' 'DivX audio (WMA)  [divxa32.acm]'
[08:53:44:852] InfoReader::readLine: line: 'vdowaveacm  acm       working   vdowave ACM  [vdowave.acm]'
[08:53:44:852] InfoReader::readLine: found codec: 'vdowaveacm' 'vdowave ACM  [vdowave.acm]'
[08:53:44:852] InfoReader::readLine: line: 'msadpcmacm  acm       working   MS ADPCM  [msadp32.acm]'
[08:53:44:852] InfoReader::readLine: found codec: 'msadpcmacm' 'MS ADPCM  [msadp32.acm]'
[08:53:44:852] InfoReader::readLine: line: 'ffpcmdaud   ffmpeg    untested  D-Cinema audio (FFmpeg)  [pcm_s24daud]'
[08:53:44:852] InfoReader::readLine: found codec: 'ffpcmdaud' 'D-Cinema audio (FFmpeg)  [pcm_s24daud]'
[08:53:44:852] InfoReader::readLine: line: 'ffwmav1     ffmpeg    untested  DivX audio v1 (FFmpeg)  [wmav1]'
[08:53:44:852] InfoReader::readLine: found codec: 'ffwmav1' 'DivX audio v1 (FFmpeg)  [wmav1]'
[08:53:44:853] InfoReader::readLine: line: 'ffwmav2     ffmpeg    untested  DivX audio v2 (FFmpeg)  [wmav2]'
[08:53:44:853] InfoReader::readLine: found codec: 'ffwmav2' 'DivX audio v2 (FFmpeg)  [wmav2]'
[08:53:44:853] InfoReader::readLine: line: 'ffwmapro    ffmpeg    untested  WMA Pro audio (FFmpeg)  [wmapro]'
[08:53:44:853] InfoReader::readLine: found codec: 'ffwmapro' 'WMA Pro audio (FFmpeg)  [wmapro]'
[08:53:44:853] InfoReader::readLine: line: 'ffwmavoice  ffmpeg    untested  WMA Voice audio (FFmpeg)  [wmavoice]'
[08:53:44:853] InfoReader::readLine: found codec: 'ffwmavoice' 'WMA Voice audio (FFmpeg)  [wmavoice]'
[08:53:44:853] InfoReader::readLine: line: 'ffmac3      ffmpeg    untested  Macintosh Audio Compression and Expansion 3:1  [mace3]'
[08:53:44:853] InfoReader::readLine: found codec: 'ffmac3' 'Macintosh Audio Compression and Expansion 3:1  [mace3]'
[08:53:44:853] InfoReader::readLine: line: 'ffmac6      ffmpeg    untested  Macintosh Audio Compression and Expansion 6:1  [mace6]'
[08:53:44:853] InfoReader::readLine: found codec: 'ffmac6' 'Macintosh Audio Compression and Expansion 6:1  [mace6]'
[08:53:44:853] InfoReader::readLine: line: 'ffsonic     ffmpeg    untested  FFmpeg Sonic  [sonic]'
[08:53:44:853] InfoReader::readLine: found codec: 'ffsonic' 'FFmpeg Sonic  [sonic]'
[08:53:44:853] InfoReader::readLine: line: 'mpg123      mpg123    working   MPEG 1.0/2.0/2.5 layers I, II, III'
[08:53:44:853] InfoReader::readLine: found codec: 'mpg123' 'MPEG 1.0/2.0/2.5 layers I, II, III'
[08:53:44:853] InfoReader::readLine: line: 'ffmp3on4float ffmpeg    working   FFmpeg Multi-channel MPEG layer-3 on MP4 audio  [mp3on4float]'
[08:53:44:853] InfoReader::readLine: found codec: 'ffmp3on4float' 'FFmpeg Multi-channel MPEG layer-3 on MP4 audio  [mp3on4float]'
[08:53:44:853] InfoReader::readLine: line: 'ffmp3on4    ffmpeg    working   FFmpeg Multi-channel MPEG layer-3 on MP4 audio  [mp3on4]'
[08:53:44:853] InfoReader::readLine: found codec: 'ffmp3on4' 'FFmpeg Multi-channel MPEG layer-3 on MP4 audio  [mp3on4]'
[08:53:44:854] InfoReader::readLine: line: 'ffmp3float  ffmpeg    working   FFmpeg MPEG layer-3 audio  [mp3float]'
[08:53:44:854] InfoReader::readLine: found codec: 'ffmp3float' 'FFmpeg MPEG layer-3 audio  [mp3float]'
[08:53:44:854] InfoReader::readLine: line: 'ffmp3       ffmpeg    working   FFmpeg MPEG layer-3 audio  [mp3]'
[08:53:44:854] InfoReader::readLine: found codec: 'ffmp3' 'FFmpeg MPEG layer-3 audio  [mp3]'
[08:53:44:854] InfoReader::readLine: line: 'ffmp3adufloat ffmpeg    working   FFmpeg MPEG layer-3 adu audio  [mp3adufloat]'
[08:53:44:854] InfoReader::readLine: found codec: 'ffmp3adufloat' 'FFmpeg MPEG layer-3 adu audio  [mp3adufloat]'
[08:53:44:854] InfoReader::readLine: line: 'ffmp3adu    ffmpeg    working   FFmpeg MPEG layer-3 adu audio  [mp3adu]'
[08:53:44:854] InfoReader::readLine: found codec: 'ffmp3adu' 'FFmpeg MPEG layer-3 adu audio  [mp3adu]'
[08:53:44:854] InfoReader::readLine: line: 'ffmp2float  ffmpeg    working   FFmpeg MPEG layer-1 and layer-2 audio  [mp2float]'
[08:53:44:854] InfoReader::readLine: found codec: 'ffmp2float' 'FFmpeg MPEG layer-1 and layer-2 audio  [mp2float]'
[08:53:44:854] InfoReader::readLine: line: 'ffmp2       ffmpeg    working   FFmpeg MPEG layer-1 and layer-2 audio  [mp2]'
[08:53:44:854] InfoReader::readLine: found codec: 'ffmp2' 'FFmpeg MPEG layer-1 and layer-2 audio  [mp2]'
[08:53:44:854] InfoReader::readLine: line: 'mad         libmad    working   libMAD MPEG layer 1-2-3  [libmad]'
[08:53:44:854] InfoReader::readLine: found codec: 'mad' 'libMAD MPEG layer 1-2-3  [libmad]'
[08:53:44:854] InfoReader::readLine: line: 'mp3acm      acm       working   MPEG layer-3  [l3codeca.acm]'
[08:53:44:854] InfoReader::readLine: found codec: 'mp3acm' 'MPEG layer-3  [l3codeca.acm]'
[08:53:44:854] InfoReader::readLine: line: 'imaadpcmacm acm       working   IMA ADPCM  [imaadp32.acm]'
[08:53:44:855] InfoReader::readLine: found codec: 'imaadpcmacm' 'IMA ADPCM  [imaadp32.acm]'
[08:53:44:855] InfoReader::readLine: line: 'ffgsm       ffmpeg    working   FFmpeg GSM 06.10  [gsm]'
[08:53:44:855] InfoReader::readLine: found codec: 'ffgsm' 'FFmpeg GSM 06.10  [gsm]'
[08:53:44:855] InfoReader::readLine: line: 'ffgsmms     ffmpeg    working   FFmpeg MS GSM  [gsm_ms]'
[08:53:44:855] InfoReader::readLine: found codec: 'ffgsmms' 'FFmpeg MS GSM  [gsm_ms]'
[08:53:44:855] InfoReader::readLine: line: 'libgsm      ffmpeg    working   libgsm GSM 06.10  [libgsm]'
[08:53:44:855] InfoReader::readLine: found codec: 'libgsm' 'libgsm GSM 06.10  [libgsm]'
[08:53:44:855] InfoReader::readLine: line: 'libgsmms    ffmpeg    working   libgsm MS GSM  [libgsm_ms]'
[08:53:44:855] InfoReader::readLine: found codec: 'libgsmms' 'libgsm MS GSM  [libgsm_ms]'
[08:53:44:855] InfoReader::readLine: line: 'msgsmacm    acm       working   MS GSM  [msgsm32.acm]'
[08:53:44:855] InfoReader::readLine: found codec: 'msgsmacm' 'MS GSM  [msgsm32.acm]'
[08:53:44:855] InfoReader::readLine: line: 'msnaudio    acm       working   MSN AUDIO  [msnaudio.acm]'
[08:53:44:855] InfoReader::readLine: found codec: 'msnaudio' 'MSN AUDIO  [msnaudio.acm]'
[08:53:44:855] InfoReader::readLine: line: 'alaw        alaw      working   aLaw'
[08:53:44:855] InfoReader::readLine: found codec: 'alaw' 'aLaw'
[08:53:44:855] InfoReader::readLine: line: 'ulaw        alaw      working   uLaw'
[08:53:44:855] InfoReader::readLine: found codec: 'ulaw' 'uLaw'
[08:53:44:855] InfoReader::readLine: line: 'dvdpcm      dvdpcm    working   Uncompressed DVD/VOB LPCM'
[08:53:44:855] InfoReader::readLine: found codec: 'dvdpcm' 'Uncompressed DVD/VOB LPCM'
[08:53:44:856] InfoReader::readLine: line: 'fflpcm      ffmpeg    working   Blu-ray LPCM  [pcm_bluray]'
[08:53:44:856] InfoReader::readLine: found codec: 'fflpcm' 'Blu-ray LPCM  [pcm_bluray]'
[08:53:44:856] InfoReader::readLine: line: 'ffpcmlxf    ffmpeg    working   Leitch/Harris PCM  [pcm_lxf]'
[08:53:44:856] InfoReader::readLine: found codec: 'ffpcmlxf' 'Leitch/Harris PCM  [pcm_lxf]'
[08:53:44:856] InfoReader::readLine: line: 'ffs302m     ffmpeg    working   SMPTE 302M  [s302m]'
[08:53:44:856] InfoReader::readLine: found codec: 'ffs302m' 'SMPTE 302M  [s302m]'
[08:53:44:856] InfoReader::readLine: line: 'ffac3       ffmpeg    working   FFmpeg AC-3  [ac3]'
[08:53:44:856] InfoReader::readLine: found codec: 'ffac3' 'FFmpeg AC-3  [ac3]'
[08:53:44:856] InfoReader::readLine: line: 'ffeac3      ffmpeg    working   FFmpeg E-AC-3  [eac3]'
[08:53:44:856] InfoReader::readLine: found codec: 'ffeac3' 'FFmpeg E-AC-3  [eac3]'
[08:53:44:856] InfoReader::readLine: line: 'a52         liba52    working   AC3-liba52  [liba52]'
[08:53:44:856] InfoReader::readLine: found codec: 'a52' 'AC3-liba52  [liba52]'
[08:53:44:856] InfoReader::readLine: line: 'ffdca       ffmpeg    working   FFmpeg DTS  [dca]'
[08:53:44:856] InfoReader::readLine: found codec: 'ffdca' 'FFmpeg DTS  [dca]'
[08:53:44:856] InfoReader::readLine: line: 'dts         libdca    working   DTS-libdca'
[08:53:44:856] InfoReader::readLine: found codec: 'dts' 'DTS-libdca'
[08:53:44:856] InfoReader::readLine: line: 'ffmusepack7 ffmpeg    working   Musepack sv7 audio codec  [mpc7]'
[08:53:44:856] InfoReader::readLine: found codec: 'ffmusepack7' 'Musepack sv7 audio codec  [mpc7]'
[08:53:44:856] InfoReader::readLine: line: 'ffmusepack8 ffmpeg    working   Musepack sv8 audio codec  [mpc8]'
[08:53:44:856] InfoReader::readLine: found codec: 'ffmusepack8' 'Musepack sv8 audio codec  [mpc8]'
[08:53:44:857] InfoReader::readLine: line: 'musepack    mpcdec    working   Musepack audio codec'
[08:53:44:857] InfoReader::readLine: found codec: 'musepack' 'Musepack audio codec'
[08:53:44:857] InfoReader::readLine: line: 'ffamrnb     ffmpeg    working   AMR Narrowband  [amrnb]'
[08:53:44:857] InfoReader::readLine: found codec: 'ffamrnb' 'AMR Narrowband  [amrnb]'
[08:53:44:857] InfoReader::readLine: line: 'libopencoreamrnb ffmpeg    working   AMR Narrowband  [libopencore_amrnb]'
[08:53:44:857] InfoReader::readLine: found codec: 'libopencoreamrnb' 'AMR Narrowband  [libopencore_amrnb]'
[08:53:44:857] InfoReader::readLine: line: 'libopencoreamrwb ffmpeg    working   AMR Wideband  [libopencore_amrwb]'
[08:53:44:857] InfoReader::readLine: found codec: 'libopencoreamrwb' 'AMR Wideband  [libopencore_amrwb]'
[08:53:44:857] InfoReader::readLine: line: 'ffadcpmswf  ffmpeg    working   FFmpeg's ADPCM Flash-variant  [adpcm_swf]'
[08:53:44:857] InfoReader::readLine: found codec: 'ffadcpmswf' 'FFmpeg's ADPCM Flash-variant  [adpcm_swf]'
[08:53:44:857] InfoReader::readLine: line: 'voxvoice    dshow     working   VoxWare MetaVoice  [voxmvdec.ax]'
[08:53:44:857] InfoReader::readLine: found codec: 'voxvoice' 'VoxWare MetaVoice  [voxmvdec.ax]'
[08:53:44:857] InfoReader::readLine: line: 'voxware     dshow     working   VoxWare  [voxmsdec.ax]'
[08:53:44:857] InfoReader::readLine: found codec: 'voxware' 'VoxWare  [voxmsdec.ax]'
[08:53:44:857] InfoReader::readLine: line: 'acelp       dshow     working   ACELP.net Sipro Lab Audio  [acelpdec.ax]'
[08:53:44:857] InfoReader::readLine: found codec: 'acelp' 'ACELP.net Sipro Lab Audio  [acelpdec.ax]'
[08:53:44:857] InfoReader::readLine: line: 'ffimc       ffmpeg    working   FFmpeg Intel Music Coder  [imc]'
[08:53:44:857] InfoReader::readLine: found codec: 'ffimc' 'FFmpeg Intel Music Coder  [imc]'
[08:53:44:857] InfoReader::readLine: line: 'imc         acm       working   Intel Music Coder  [imc32.acm]'
[08:53:44:858] InfoReader::readLine: found codec: 'imc' 'Intel Music Coder  [imc32.acm]'
[08:53:44:858] InfoReader::readLine: line: 'iac25       acm       working   Indeo audio  [iac25_32.ax]'
[08:53:44:858] InfoReader::readLine: found codec: 'iac25' 'Indeo audio  [iac25_32.ax]'
[08:53:44:858] InfoReader::readLine: line: 'ffctadp32   ffmpeg    working   FFmpeg Creative ADPCM codec  [adpcm_ct]'
[08:53:44:858] InfoReader::readLine: found codec: 'ffctadp32' 'FFmpeg Creative ADPCM codec  [adpcm_ct]'
[08:53:44:858] InfoReader::readLine: line: 'ctadp32     acm       working   Creative ADPCM codec  [ctadp32.acm]'
[08:53:44:858] InfoReader::readLine: found codec: 'ctadp32' 'Creative ADPCM codec  [ctadp32.acm]'
[08:53:44:858] InfoReader::readLine: line: 'sc4         acm       working   SC4 : Micronas speech codec (ADPCM, MPman recording)  [mi-sc4.acm]'
[08:53:44:858] InfoReader::readLine: found codec: 'sc4' 'SC4 : Micronas speech codec (ADPCM, MPman recording)  [mi-sc4.acm]'
[08:53:44:858] InfoReader::readLine: line: 'hwac3       hwac3     working   AC3 through S/PDIF'
[08:53:44:858] InfoReader::readLine: found codec: 'hwac3' 'AC3 through S/PDIF'
[08:53:44:858] InfoReader::readLine: line: 'hwdts       hwac3     working   DTS through S/PDIF'
[08:53:44:858] InfoReader::readLine: found codec: 'hwdts' 'DTS through S/PDIF'
[08:53:44:858] InfoReader::readLine: line: 'ffvorbis    ffmpeg    working   FFmpeg Vorbis  [vorbis]'
[08:53:44:858] InfoReader::readLine: found codec: 'ffvorbis' 'FFmpeg Vorbis  [vorbis]'
[08:53:44:858] InfoReader::readLine: line: 'vorbis      libvorbis working   OggVorbis Audio  [libvorbis]'
[08:53:44:858] InfoReader::readLine: found codec: 'vorbis' 'OggVorbis Audio  [libvorbis]'
[08:53:44:858] InfoReader::readLine: line: 'tremor      tremor    working   OggVorbis audio  [tremor]'
[08:53:44:859] InfoReader::readLine: found codec: 'tremor' 'OggVorbis audio  [tremor]'
[08:53:44:859] InfoReader::readLine: line: 'vorbisacm   acm       working   OggVorbis ACM  [vorbis.acm]'
[08:53:44:859] InfoReader::readLine: found codec: 'vorbisacm' 'OggVorbis ACM  [vorbis.acm]'
[08:53:44:859] InfoReader::readLine: line: 'speex       speex     working   Speex audio  [speex]'
[08:53:44:859] InfoReader::readLine: found codec: 'speex' 'Speex audio  [speex]'
[08:53:44:859] InfoReader::readLine: line: 'vivoaudio   acm       working   Vivo G.723/Siren Audio Codec  [vivog723.acm]'
[08:53:44:859] InfoReader::readLine: found codec: 'vivoaudio' 'Vivo G.723/Siren Audio Codec  [vivog723.acm]'
[08:53:44:859] InfoReader::readLine: line: 'g72x        g72x      crashing  G.711/G.721/G.723  [g72x.c]'
[08:53:44:859] InfoReader::readLine: found codec: 'g72x' 'G.711/G.721/G.723  [g72x.c]'
[08:53:44:859] InfoReader::readLine: line: 'ffg722      ffmpeg    working   G.722 Audio  [g722]'
[08:53:44:859] InfoReader::readLine: found codec: 'ffg722' 'G.722 Audio  [g722]'
[08:53:44:859] InfoReader::readLine: line: 'ffg726      ffmpeg    working   Sharp G.726 Audio  [g726]'
[08:53:44:859] InfoReader::readLine: found codec: 'ffg726' 'Sharp G.726 Audio  [g726]'
[08:53:44:859] InfoReader::readLine: line: 'g726        acm       untested  Sharp G.726 Audio  [scg726.acm]'
[08:53:44:859] InfoReader::readLine: found codec: 'g726' 'Sharp G.726 Audio  [scg726.acm]'
[08:53:44:859] InfoReader::readLine: line: 'atrac3      acm       problems  Sony ATRAC3  [atrac3.acm]'
[08:53:44:859] InfoReader::readLine: found codec: 'atrac3' 'Sony ATRAC3  [atrac3.acm]'
[08:53:44:859] InfoReader::readLine: line: 'ALF2        acm       working   ALF2  [alf2cd.acm]'
[08:53:44:859] InfoReader::readLine: found codec: 'ALF2' 'ALF2  [alf2cd.acm]'
[08:53:44:860] InfoReader::readLine: line: 'fftruespeech ffmpeg    working   FFmpeg TrueSpeech  [truespeech]'
[08:53:44:860] InfoReader::readLine: found codec: 'fftruespeech' 'FFmpeg TrueSpeech  [truespeech]'
[08:53:44:860] InfoReader::readLine: line: 'truespeech  acm       working   DSP Group TrueSpeech(TM)  [tssoft32.acm]'
[08:53:44:860] InfoReader::readLine: found codec: 'truespeech' 'DSP Group TrueSpeech(TM)  [tssoft32.acm]'
[08:53:44:860] InfoReader::readLine: line: 'netspeakgsm acm       working   NetSpeak GSM  [nsgsm32.acm]'
[08:53:44:860] InfoReader::readLine: found codec: 'netspeakgsm' 'NetSpeak GSM  [nsgsm32.acm]'
[08:53:44:860] InfoReader::readLine: line: 'netspeakts  acm       working   NetSpeak TrueSpeech  [nstsp32.acm]'
[08:53:44:860] InfoReader::readLine: found codec: 'netspeakts' 'NetSpeak TrueSpeech  [nstsp32.acm]'
[08:53:44:860] InfoReader::readLine: line: 'voxwarert24 acm       working   VoxWare RT24 speech codec  [nsrt2432.acm]'
[08:53:44:860] InfoReader::readLine: found codec: 'voxwarert24' 'VoxWare RT24 speech codec  [nsrt2432.acm]'
[08:53:44:860] InfoReader::readLine: line: 'lhacm       acm       working   Lernout & Hauspie CELP and SBC codecs  [lhacm.acm]'
[08:53:44:860] InfoReader::readLine: found codec: 'lhacm' 'Lernout & Hauspie CELP and SBC codecs  [lhacm.acm]'
[08:53:44:860] InfoReader::readLine: line: 'lhacm2      acm       working   Voxware AC aka Lernout & Hauspie CELP and CBS codecs  [lhacm2.acm]'
[08:53:44:860] InfoReader::readLine: found codec: 'lhacm2' 'Voxware AC aka Lernout & Hauspie CELP and CBS codecs  [lhacm2.acm]'
[08:53:44:860] InfoReader::readLine: line: 'pscelp      acm       working   Philips Speech Processing CELP  [smcelp32.acm]'
[08:53:44:860] InfoReader::readLine: found codec: 'pscelp' 'Philips Speech Processing CELP  [smcelp32.acm]'
[08:53:44:860] InfoReader::readLine: line: 'fftwinvq    ffmpeg    working   FFmpeg TwinVQ  [twinvq]'
[08:53:44:860] InfoReader::readLine: found codec: 'fftwinvq' 'FFmpeg TwinVQ  [twinvq]'
[08:53:44:861] InfoReader::readLine: line: 'TwinVQ      vqf       working   VQF codec by NTTLabs  [tvqdec.dll]'
[08:53:44:861] InfoReader::readLine: found codec: 'TwinVQ' 'VQF codec by NTTLabs  [tvqdec.dll]'
[08:53:44:861] InfoReader::readLine: line: 'hwmpa       hwmpa     working   MPEG audio pass-through for hardware MPEG decoders'
[08:53:44:861] InfoReader::readLine: found codec: 'hwmpa' 'MPEG audio pass-through for hardware MPEG decoders'
[08:53:44:861] InfoReader::readLine: line: 'msnsiren    acm       working   msn siren audio codec  [sirenacm.dll]'
[08:53:44:861] InfoReader::readLine: found codec: 'msnsiren' 'msn siren audio codec  [sirenacm.dll]'
[08:53:44:861] InfoReader::readLine: line: 'uleaddva    acm       working   Ulead DV ACM  [dvacm.acm]'
[08:53:44:861] InfoReader::readLine: found codec: 'uleaddva' 'Ulead DV ACM  [dvacm.acm]'
[08:53:44:861] InfoReader::readLine: line: 'Available video codecs:'
[08:53:44:861] WARNING: InfoReader::readLine: can't parse codec from line 'Available video codecs:'
[08:53:44:861] InfoReader::readLine: line: 'ID_VIDEO_CODECS'
[08:53:44:861] WARNING: InfoReader::readLine: can't parse codec from line 'ID_VIDEO_CODECS'
[08:53:44:861] InfoReader::readLines: found key: vc
[08:53:44:861] InfoReader::readLine: line: 'vc:     vfm:      status:   info:  [lib/dll]'
[08:53:44:861] WARNING: InfoReader::readLine: can't parse codec from line 'vc:     vfm:      status:   info:  [lib/dll]'
[08:53:44:861] InfoReader::readLine: line: 'lavc        ffmpeg    problems  Generic libavcodec decoder'
[08:53:44:861] InfoReader::readLine: found codec: 'lavc' 'Generic libavcodec decoder'
[08:53:44:861] InfoReader::readLine: line: 'ffanm       ffmpeg    working   FFmpeg Deluxe Paint Animation  [anm]'
[08:53:44:861] InfoReader::readLine: found codec: 'ffanm' 'FFmpeg Deluxe Paint Animation  [anm]'
[08:53:44:861] InfoReader::readLine: line: 'ffbinkvideo ffmpeg    working   FFmpeg Bink Video  [binkvideo]'
[08:53:44:862] InfoReader::readLine: found codec: 'ffbinkvideo' 'FFmpeg Bink Video  [binkvideo]'
[08:53:44:862] InfoReader::readLine: line: 'ffcdgraphics ffmpeg    working   FFmpeg CD-Graphics  [cdgraphics]'
[08:53:44:862] InfoReader::readLine: found codec: 'ffcdgraphics' 'FFmpeg CD-Graphics  [cdgraphics]'
[08:53:44:862] InfoReader::readLine: line: 'ffmvi1      ffmpeg    working   FFmpeg Motion Pixels  [motionpixels]'
[08:53:44:862] InfoReader::readLine: found codec: 'ffmvi1' 'FFmpeg Motion Pixels  [motionpixels]'
[08:53:44:862] InfoReader::readLine: line: 'ffmdec      ffmpeg    working   FFmpeg Sony PlayStation MDEC (Motion DECoder)  [mdec]'
[08:53:44:862] InfoReader::readLine: found codec: 'ffmdec' 'FFmpeg Sony PlayStation MDEC (Motion DECoder)  [mdec]'
[08:53:44:862] InfoReader::readLine: line: 'ffsiff      ffmpeg    working   FFmpeg Beam Software SIFF  [vb]'
[08:53:44:862] InfoReader::readLine: found codec: 'ffsiff' 'FFmpeg Beam Software SIFF  [vb]'
[08:53:44:862] InfoReader::readLine: line: 'ffmimic     ffmpeg    working   FFmpeg Mimic video  [mimic]'
[08:53:44:862] InfoReader::readLine: found codec: 'ffmimic' 'FFmpeg Mimic video  [mimic]'
[08:53:44:862] InfoReader::readLine: line: 'ffkmvc      ffmpeg    working   FFmpeg Karl Morton Video Codec  [kmvc]'
[08:53:44:862] InfoReader::readLine: found codec: 'ffkmvc' 'FFmpeg Karl Morton Video Codec  [kmvc]'
[08:53:44:862] InfoReader::readLine: line: 'ffzmbv      ffmpeg    working   FFmpeg Zip Motion-Block Video  [zmbv]'
[08:53:44:862] InfoReader::readLine: found codec: 'ffzmbv' 'FFmpeg Zip Motion-Block Video  [zmbv]'
[08:53:44:862] InfoReader::readLine: line: 'geov        vfw       problems  GeoCodec  [GeoCodec.dll]'
[08:53:44:862] InfoReader::readLine: found codec: 'geov' 'GeoCodec  [GeoCodec.dll]'
[08:53:44:863] InfoReader::readLine: line: 'imm4        vfw       working   infinity cctv codec  [VCMIMM4.dll]'
[08:53:44:863] InfoReader::readLine: found codec: 'imm4' 'infinity cctv codec  [VCMIMM4.dll]'
[08:53:44:863] InfoReader::readLine: line: 'amv2        vfw       working   lossless video codec  [amv2codec.dll]'
[08:53:44:863] InfoReader::readLine: found codec: 'amv2' 'lossless video codec  [amv2codec.dll]'
[08:53:44:863] InfoReader::readLine: line: 'lzocodec    vfw       working   lzo lossless  [lzocodec.dll]'
[08:53:44:863] InfoReader::readLine: found codec: 'lzocodec' 'lzo lossless  [lzocodec.dll]'
[08:53:44:863] InfoReader::readLine: line: 'direccionalvfw vfw       working   direccional lossless codec  [direccional.dll]'
[08:53:44:863] InfoReader::readLine: found codec: 'direccionalvfw' 'direccional lossless codec  [direccional.dll]'
[08:53:44:863] InfoReader::readLine: line: 'mhuffyuv    vfw       working   mhuffyuv lossless codec  [mhuffyuv.dll]'
[08:53:44:863] InfoReader::readLine: found codec: 'mhuffyuv' 'mhuffyuv lossless codec  [mhuffyuv.dll]'
[08:53:44:863] InfoReader::readLine: line: 'zmbv        vfw       working   Zip Motion-Block Video  [zmbv.dll]'
[08:53:44:863] InfoReader::readLine: found codec: 'zmbv' 'Zip Motion-Block Video  [zmbv.dll]'
[08:53:44:863] InfoReader::readLine: line: 'yuv8        vfwex     working   YUV422 = Cb0 Y0 Cr0 Y1 Cb1 Y2 Cr1 Y3 (U Y V Y U Y V Y)  [kdvyuv8.dll]'
[08:53:44:863] InfoReader::readLine: found codec: 'yuv8' 'YUV422 = Cb0 Y0 Cr0 Y1 Cb1 Y2 Cr1 Y3 (U Y V Y U Y V Y)  [kdvyuv8.dll]'
[08:53:44:863] InfoReader::readLine: line: 'ffr210      ffmpeg    working   FFmpeg R210 - 10-bit RGB  [r210]'
[08:53:44:863] InfoReader::readLine: found codec: 'ffr210' 'FFmpeg R210 - 10-bit RGB  [r210]'
[08:53:44:863] InfoReader::readLine: line: 'ffr10k      ffmpeg    working   FFmpeg R10k - 10-bit RGB  [r10k]'
[08:53:44:864] InfoReader::readLine: found codec: 'ffr10k' 'FFmpeg R10k - 10-bit RGB  [r10k]'
[08:53:44:864] InfoReader::readLine: line: 'blackmagic  vfw       working   Blackmagic 10-bit  [BMDCodecLib.dll]'
[08:53:44:864] InfoReader::readLine: found codec: 'blackmagic' 'Blackmagic 10-bit  [BMDCodecLib.dll]'
[08:53:44:864] InfoReader::readLine: line: 'ffmpeg1     ffmpeg    working   FFmpeg MPEG-1  [mpeg1video]'
[08:53:44:864] InfoReader::readLine: found codec: 'ffmpeg1' 'FFmpeg MPEG-1  [mpeg1video]'
[08:53:44:864] InfoReader::readLine: line: 'ffmpeg2     ffmpeg    working   FFmpeg MPEG-2  [mpeg2video]'
[08:53:44:864] InfoReader::readLine: found codec: 'ffmpeg2' 'FFmpeg MPEG-2  [mpeg2video]'
[08:53:44:864] InfoReader::readLine: line: 'ffmpeg12    ffmpeg    working   FFmpeg MPEG-1/2  [mpegvideo]'
[08:53:44:864] InfoReader::readLine: found codec: 'ffmpeg12' 'FFmpeg MPEG-1/2  [mpegvideo]'
[08:53:44:864] InfoReader::readLine: line: 'ffmpeg12vdpau ffmpeg    working   FFmpeg MPEG-1/2 (VDPAU)  [mpegvideo_vdpau]'
[08:53:44:864] InfoReader::readLine: found codec: 'ffmpeg12vdpau' 'FFmpeg MPEG-1/2 (VDPAU)  [mpegvideo_vdpau]'
[08:53:44:864] InfoReader::readLine: line: 'ffmpeg2crystalhd ffmpeg    working   FFmpeg MPEG-2 (CrystalHD)  [mpeg2_crystalhd]'
[08:53:44:864] InfoReader::readLine: found codec: 'ffmpeg2crystalhd' 'FFmpeg MPEG-2 (CrystalHD)  [mpeg2_crystalhd]'
[08:53:44:864] InfoReader::readLine: line: 'mpegpes     mpegpes   working   MPEG-PES output (.mpg or DXR3/IVTV/DVB/V4L2 card)'
[08:53:44:864] InfoReader::readLine: found codec: 'mpegpes' 'MPEG-PES output (.mpg or DXR3/IVTV/DVB/V4L2 card)'
[08:53:44:864] InfoReader::readLine: line: 'ffnuv       ffmpeg    working   NuppelVideo  [nuv]'
[08:53:44:864] InfoReader::readLine: found codec: 'ffnuv' 'NuppelVideo  [nuv]'
[08:53:44:865] InfoReader::readLine: line: 'ffbmp       ffmpeg    working   FFmpeg BMP  [bmp]'
[08:53:44:865] InfoReader::readLine: found codec: 'ffbmp' 'FFmpeg BMP  [bmp]'
[08:53:44:865] InfoReader::readLine: line: 'ffdpx       ffmpeg    working   FFmpeg DPX  [dpx]'
[08:53:44:865] InfoReader::readLine: found codec: 'ffdpx' 'FFmpeg DPX  [dpx]'
[08:53:44:865] InfoReader::readLine: line: 'ffgif       ffmpeg    working   FFmpeg GIF  [gif]'
[08:53:44:865] InfoReader::readLine: found codec: 'ffgif' 'FFmpeg GIF  [gif]'
[08:53:44:865] InfoReader::readLine: line: 'fftiff      ffmpeg    working   FFmpeg TIFF  [tiff]'
[08:53:44:865] InfoReader::readLine: found codec: 'fftiff' 'FFmpeg TIFF  [tiff]'
[08:53:44:865] InfoReader::readLine: line: 'ffpcx       ffmpeg    working   FFmpeg PCX  [pcx]'
[08:53:44:865] InfoReader::readLine: found codec: 'ffpcx' 'FFmpeg PCX  [pcx]'
[08:53:44:865] InfoReader::readLine: line: 'ffpng       ffmpeg    working   FFmpeg PNG  [png]'
[08:53:44:865] InfoReader::readLine: found codec: 'ffpng' 'FFmpeg PNG  [png]'
[08:53:44:865] InfoReader::readLine: line: 'mpng        mpng      working   PNG image  [libpng]'
[08:53:44:865] InfoReader::readLine: found codec: 'mpng' 'PNG image  [libpng]'
[08:53:44:865] InfoReader::readLine: line: 'ffptx       ffmpeg    working   FFmpeg V.Flash PTX  [ptx]'
[08:53:44:865] InfoReader::readLine: found codec: 'ffptx' 'FFmpeg V.Flash PTX  [ptx]'
[08:53:44:865] InfoReader::readLine: line: 'fftga       ffmpeg    untested  FFmpeg TGA  [targa]'
[08:53:44:865] InfoReader::readLine: found codec: 'fftga' 'FFmpeg TGA  [targa]'
[08:53:44:865] InfoReader::readLine: line: 'mtga        mtga      working   TGA image'
[08:53:44:866] InfoReader::readLine: found codec: 'mtga' 'TGA image'
[08:53:44:866] InfoReader::readLine: line: 'ffsgi       ffmpeg    working   FFmpeg SGI image  [sgi]'
[08:53:44:866] InfoReader::readLine: found codec: 'ffsgi' 'FFmpeg SGI image  [sgi]'
[08:53:44:866] InfoReader::readLine: line: 'sgi         sgi       working   SGI image'
[08:53:44:866] InfoReader::readLine: found codec: 'sgi' 'SGI image'
[08:53:44:866] InfoReader::readLine: line: 'ffsunras    ffmpeg    working   FFmpeg SUN Rasterfile  [sunrast]'
[08:53:44:866] InfoReader::readLine: found codec: 'ffsunras' 'FFmpeg SUN Rasterfile  [sunrast]'
[08:53:44:866] InfoReader::readLine: line: 'ffindeo3    ffmpeg    working   FFmpeg Intel Indeo 3.1/3.2  [indeo3]'
[08:53:44:866] InfoReader::readLine: found codec: 'ffindeo3' 'FFmpeg Intel Indeo 3.1/3.2  [indeo3]'
[08:53:44:866] InfoReader::readLine: line: 'fffli       ffmpeg    working   Autodesk FLI/FLC Animation  [flic]'
[08:53:44:866] InfoReader::readLine: found codec: 'fffli' 'Autodesk FLI/FLC Animation  [flic]'
[08:53:44:866] InfoReader::readLine: line: 'ffaasc      ffmpeg    working   Autodesk RLE  [aasc]'
[08:53:44:866] InfoReader::readLine: found codec: 'ffaasc' 'Autodesk RLE  [aasc]'
[08:53:44:866] InfoReader::readLine: line: 'ffloco      ffmpeg    working   LOCO video  [loco]'
[08:53:44:866] InfoReader::readLine: found codec: 'ffloco' 'LOCO video  [loco]'
[08:53:44:866] InfoReader::readLine: line: 'ffqtrle     ffmpeg    working   QuickTime Animation (RLE)  [qtrle]'
[08:53:44:866] InfoReader::readLine: found codec: 'ffqtrle' 'QuickTime Animation (RLE)  [qtrle]'
[08:53:44:866] InfoReader::readLine: line: 'ffrpza      ffmpeg    working   QuickTime Apple Video  [rpza]'
[08:53:44:866] InfoReader::readLine: found codec: 'ffrpza' 'QuickTime Apple Video  [rpza]'
[08:53:44:867] InfoReader::readLine: line: 'ffsmc       ffmpeg    working   Apple Graphics (SMC) codec  [smc]'
[08:53:44:867] InfoReader::readLine: found codec: 'ffsmc' 'Apple Graphics (SMC) codec  [smc]'
[08:53:44:867] InfoReader::readLine: line: 'ff8bps      ffmpeg    working   Planar RGB (Photoshop)  [8bps]'
[08:53:44:867] InfoReader::readLine: found codec: 'ff8bps' 'Planar RGB (Photoshop)  [8bps]'
[08:53:44:867] InfoReader::readLine: line: 'ffcyuv      ffmpeg    working   Creative YUV (libavcodec)  [cyuv]'
[08:53:44:867] InfoReader::readLine: found codec: 'ffcyuv' 'Creative YUV (libavcodec)  [cyuv]'
[08:53:44:867] InfoReader::readLine: line: 'ffaura      ffmpeg    working   Auravision Aura (libavcodec)  [aura]'
[08:53:44:867] InfoReader::readLine: found codec: 'ffaura' 'Auravision Aura (libavcodec)  [aura]'
[08:53:44:867] InfoReader::readLine: line: 'ffaura2     ffmpeg    working   Auravision Aura 2 (libavcodec)  [aura2]'
[08:53:44:867] InfoReader::readLine: found codec: 'ffaura2' 'Auravision Aura 2 (libavcodec)  [aura2]'
[08:53:44:867] InfoReader::readLine: line: 'ffmsrle     ffmpeg    working   Microsoft RLE  [msrle]'
[08:53:44:867] InfoReader::readLine: found codec: 'ffmsrle' 'Microsoft RLE  [msrle]'
[08:53:44:867] InfoReader::readLine: line: 'ffroqvideo  ffmpeg    working   Id RoQ File Video  [roqvideo]'
[08:53:44:867] InfoReader::readLine: found codec: 'ffroqvideo' 'Id RoQ File Video  [roqvideo]'
[08:53:44:867] InfoReader::readLine: line: 'lzo         lzo       working   LZO compressed  [liblzo]'
[08:53:44:867] InfoReader::readLine: found codec: 'lzo' 'LZO compressed  [liblzo]'
[08:53:44:867] InfoReader::readLine: line: 'theora      theora    working   Theora (free, reworked VP3)  [libtheora]'
[08:53:44:867] InfoReader::readLine: found codec: 'theora' 'Theora (free, reworked VP3)  [libtheora]'
[08:53:44:867] InfoReader::readLine: line: 'nogatech    vfw       working   nogatech  [nuvision.ax]'
[08:53:44:868] InfoReader::readLine: found codec: 'nogatech' 'nogatech  [nuvision.ax]'
[08:53:44:868] InfoReader::readLine: line: 'ylc         vfw       working   YUY2 Lossless Codec  [ylc.vcm]'
[08:53:44:868] InfoReader::readLine: found codec: 'ylc' 'YUY2 Lossless Codec  [ylc.vcm]'
[08:53:44:868] InfoReader::readLine: line: 'smartsight  vfw       working   Verint Video Manager  [SN4Codec.dll]'
[08:53:44:868] InfoReader::readLine: found codec: 'smartsight' 'Verint Video Manager  [SN4Codec.dll]'
[08:53:44:868] InfoReader::readLine: line: 'msuscls     vfw       working   MSU Screen Capture Lossless Codec  [SCLS.DLL]'
[08:53:44:868] InfoReader::readLine: found codec: 'msuscls' 'MSU Screen Capture Lossless Codec  [SCLS.DLL]'
[08:53:44:868] InfoReader::readLine: line: 'wincam      vfw       working   wincam screen capture codec  [wcmv.dll]'
[08:53:44:868] InfoReader::readLine: found codec: 'wincam' 'wincam screen capture codec  [wcmv.dll]'
[08:53:44:868] InfoReader::readLine: line: 'cram        vfw       problems  Microsoft Video 1  [msvidc32.dll]'
[08:53:44:868] InfoReader::readLine: found codec: 'cram' 'Microsoft Video 1  [msvidc32.dll]'
[08:53:44:868] InfoReader::readLine: line: 'ffcvid      ffmpeg    working   FFmpeg Cinepak Video  [cinepak]'
[08:53:44:868] InfoReader::readLine: found codec: 'ffcvid' 'FFmpeg Cinepak Video  [cinepak]'
[08:53:44:868] InfoReader::readLine: line: 'cvidvfw     vfw       working   Cinepak Video  [iccvid.dll]'
[08:53:44:868] InfoReader::readLine: found codec: 'cvidvfw' 'Cinepak Video  [iccvid.dll]'
[08:53:44:868] InfoReader::readLine: line: 'huffyuv     vfw       problems  HuffYUV  [huffyuv.dll]'
[08:53:44:868] InfoReader::readLine: found codec: 'huffyuv' 'HuffYUV  [huffyuv.dll]'
[08:53:44:868] InfoReader::readLine: line: 'ffvideo1    ffmpeg    working   FFmpeg Microsoft Video 1  [msvideo1]'
[08:53:44:869] InfoReader::readLine: found codec: 'ffvideo1' 'FFmpeg Microsoft Video 1  [msvideo1]'
[08:53:44:869] InfoReader::readLine: line: 'ffmszh      ffmpeg    working   FFmpeg AVImszh  [mszh]'
[08:53:44:869] InfoReader::readLine: found codec: 'ffmszh' 'FFmpeg AVImszh  [mszh]'
[08:53:44:869] InfoReader::readLine: line: 'ffzlib      ffmpeg    working   FFmpeg AVIzlib  [zlib]'
[08:53:44:869] InfoReader::readLine: found codec: 'ffzlib' 'FFmpeg AVIzlib  [zlib]'
[08:53:44:869] InfoReader::readLine: line: 'cvidxa      xanim     problems  XAnim's Radius Cinepak Video  [vid_cvid.xa]'
[08:53:44:869] InfoReader::readLine: found codec: 'cvidxa' 'XAnim's Radius Cinepak Video  [vid_cvid.xa]'
[08:53:44:869] InfoReader::readLine: line: 'ffhuffyuv   ffmpeg    working   FFmpeg HuffYUV  [huffyuv]'
[08:53:44:869] InfoReader::readLine: found codec: 'ffhuffyuv' 'FFmpeg HuffYUV  [huffyuv]'
[08:53:44:869] InfoReader::readLine: line: 'ffv1        ffmpeg    working   FFV1 (lossless codec)  [ffv1]'
[08:53:44:869] InfoReader::readLine: found codec: 'ffv1' 'FFV1 (lossless codec)  [ffv1]'
[08:53:44:869] InfoReader::readLine: line: 'ffsnow      ffmpeg    working   FFSNOW (Michael's wavelet codec)  [snow]'
[08:53:44:869] InfoReader::readLine: found codec: 'ffsnow' 'FFSNOW (Michael's wavelet codec)  [snow]'
[08:53:44:869] InfoReader::readLine: line: 'ffasv1      ffmpeg    working   FFmpeg ASUS V1  [asv1]'
[08:53:44:869] InfoReader::readLine: found codec: 'ffasv1' 'FFmpeg ASUS V1  [asv1]'
[08:53:44:869] InfoReader::readLine: line: 'ffasv2      ffmpeg    working   FFmpeg ASUS V2  [asv2]'
[08:53:44:869] InfoReader::readLine: found codec: 'ffasv2' 'FFmpeg ASUS V2  [asv2]'
[08:53:44:869] InfoReader::readLine: line: 'ffvcr1      ffmpeg    working   FFmpeg ATI VCR1  [vcr1]'
[08:53:44:869] InfoReader::readLine: found codec: 'ffvcr1' 'FFmpeg ATI VCR1  [vcr1]'
[08:53:44:870] InfoReader::readLine: line: 'ffcljr      ffmpeg    working   FFmpeg Cirrus Logic AccuPak (CLJR)  [cljr]'
[08:53:44:870] InfoReader::readLine: found codec: 'ffcljr' 'FFmpeg Cirrus Logic AccuPak (CLJR)  [cljr]'
[08:53:44:870] InfoReader::readLine: line: 'ffsvq1      ffmpeg    working   FFmpeg Sorenson Video v1 (SVQ1)  [svq1]'
[08:53:44:870] InfoReader::readLine: found codec: 'ffsvq1' 'FFmpeg Sorenson Video v1 (SVQ1)  [svq1]'
[08:53:44:870] InfoReader::readLine: line: 'ff4xm       ffmpeg    working   FFmpeg 4XM video  [4xm]'
[08:53:44:870] InfoReader::readLine: found codec: 'ff4xm' 'FFmpeg 4XM video  [4xm]'
[08:53:44:870] InfoReader::readLine: line: 'ffvixl      ffmpeg    working   Miro/Pinnacle VideoXL codec  [xl]'
[08:53:44:870] InfoReader::readLine: found codec: 'ffvixl' 'Miro/Pinnacle VideoXL codec  [xl]'
[08:53:44:870] InfoReader::readLine: line: 'ffqtdrw     ffmpeg    working   FFmpeg QuickDraw  [qdraw]'
[08:53:44:870] InfoReader::readLine: found codec: 'ffqtdrw' 'FFmpeg QuickDraw  [qdraw]'
[08:53:44:870] InfoReader::readLine: line: 'ffindeo2    ffmpeg    working   FFmpeg Indeo 2  [indeo2]'
[08:53:44:870] InfoReader::readLine: found codec: 'ffindeo2' 'FFmpeg Indeo 2  [indeo2]'
[08:53:44:870] InfoReader::readLine: line: 'ffflv       ffmpeg    working   FFmpeg Flash video  [flv]'
[08:53:44:870] InfoReader::readLine: found codec: 'ffflv' 'FFmpeg Flash video  [flv]'
[08:53:44:870] InfoReader::readLine: line: 'fffsv       ffmpeg    working   FFmpeg Flash Screen video  [flashsv]'
[08:53:44:870] InfoReader::readLine: found codec: 'fffsv' 'FFmpeg Flash Screen video  [flashsv]'
[08:53:44:871] InfoReader::readLine: line: 'ffdivx      ffmpeg    working   FFmpeg DivX ;-) (MSMPEG-4 v3)  [msmpeg4]'
[08:53:44:871] InfoReader::readLine: found codec: 'ffdivx' 'FFmpeg DivX ;-) (MSMPEG-4 v3)  [msmpeg4]'
[08:53:44:871] InfoReader::readLine: line: 'ffdivxcrystalhd ffmpeg    problems  FFmpeg DivX ;-) (MSMPEG-4 v3) (CrystalHD)  [msmpeg4_crystalhd]'
[08:53:44:871] InfoReader::readLine: found codec: 'ffdivxcrystalhd' 'FFmpeg DivX ;-) (MSMPEG-4 v3) (CrystalHD)  [msmpeg4_crystalhd]'
[08:53:44:871] InfoReader::readLine: line: 'ffmp42      ffmpeg    working   FFmpeg MSMPEG-4 v2  [msmpeg4v2]'
[08:53:44:871] InfoReader::readLine: found codec: 'ffmp42' 'FFmpeg MSMPEG-4 v2  [msmpeg4v2]'
[08:53:44:871] InfoReader::readLine: line: 'ffmp41      ffmpeg    working   FFmpeg MSMPEG-4 v1  [msmpeg4v1]'
[08:53:44:871] InfoReader::readLine: found codec: 'ffmp41' 'FFmpeg MSMPEG-4 v1  [msmpeg4v1]'
[08:53:44:871] InfoReader::readLine: line: 'ffwmv1      ffmpeg    working   FFmpeg WMV1/WMV7  [wmv1]'
[08:53:44:871] InfoReader::readLine: found codec: 'ffwmv1' 'FFmpeg WMV1/WMV7  [wmv1]'
[08:53:44:871] InfoReader::readLine: line: 'ffwmv2      ffmpeg    working   FFmpeg WMV2/WMV8  [wmv2]'
[08:53:44:871] InfoReader::readLine: found codec: 'ffwmv2' 'FFmpeg WMV2/WMV8  [wmv2]'
[08:53:44:871] InfoReader::readLine: line: 'ffwmv3      ffmpeg    problems  FFmpeg WMV3/WMV9  [wmv3]'
[08:53:44:871] InfoReader::readLine: found codec: 'ffwmv3' 'FFmpeg WMV3/WMV9  [wmv3]'
[08:53:44:871] InfoReader::readLine: line: 'ffwmvp      ffmpeg    problems  FFmpeg WVC1  [wmv3]'
[08:53:44:871] InfoReader::readLine: found codec: 'ffwmvp' 'FFmpeg WVC1  [wmv3]'
[08:53:44:871] InfoReader::readLine: line: 'ffwmv3vdpau ffmpeg    problems  FFmpeg WMV3/WMV9 (VDPAU)  [wmv3_vdpau]'
[08:53:44:871] InfoReader::readLine: found codec: 'ffwmv3vdpau' 'FFmpeg WMV3/WMV9 (VDPAU)  [wmv3_vdpau]'
[08:53:44:872] InfoReader::readLine: line: 'ffwmv3crystalhd ffmpeg    problems  FFmpeg WMV3/WMV9 (CrystalHD)  [wmv3_crystalhd]'
[08:53:44:872] InfoReader::readLine: found codec: 'ffwmv3crystalhd' 'FFmpeg WMV3/WMV9 (CrystalHD)  [wmv3_crystalhd]'
[08:53:44:872] InfoReader::readLine: line: 'ffvc1       ffmpeg    problems  FFmpeg WVC1  [vc1]'
[08:53:44:872] InfoReader::readLine: found codec: 'ffvc1' 'FFmpeg WVC1  [vc1]'
[08:53:44:872] InfoReader::readLine: line: 'ffvc1vdpau  ffmpeg    problems  FFmpeg WVC1 (VDPAU)  [vc1_vdpau]'
[08:53:44:872] InfoReader::readLine: found codec: 'ffvc1vdpau' 'FFmpeg WVC1 (VDPAU)  [vc1_vdpau]'
[08:53:44:872] InfoReader::readLine: line: 'ffvc1crystalhd ffmpeg    problems  FFmpeg WVC1 (CrystalHD)  [vc1_crystalhd]'
[08:53:44:872] InfoReader::readLine: found codec: 'ffvc1crystalhd' 'FFmpeg WVC1 (CrystalHD)  [vc1_crystalhd]'
[08:53:44:872] InfoReader::readLine: line: 'ffh264      ffmpeg    working   FFmpeg H.264  [h264]'
[08:53:44:872] InfoReader::readLine: found codec: 'ffh264' 'FFmpeg H.264  [h264]'
[08:53:44:872] InfoReader::readLine: line: 'ffh264vdpau ffmpeg    working   FFmpeg H.264 (VDPAU)  [h264_vdpau]'
[08:53:44:872] InfoReader::readLine: found codec: 'ffh264vdpau' 'FFmpeg H.264 (VDPAU)  [h264_vdpau]'
[08:53:44:872] InfoReader::readLine: line: 'ffh264crystalhd ffmpeg    working   FFmpeg H.264 (CrystalHD)  [h264_crystalhd]'
[08:53:44:872] InfoReader::readLine: found codec: 'ffh264crystalhd' 'FFmpeg H.264 (CrystalHD)  [h264_crystalhd]'
[08:53:44:872] InfoReader::readLine: line: 'coreavcwindows dshow     working   CoreAVC H.264 for x86 - http://corecodec.org/  [CoreAVCDecoder.ax]'
[08:53:44:872] InfoReader::readLine: found codec: 'coreavcwindows' 'CoreAVC H.264 for x86 - http://corecodec.org/  [CoreAVCDecoder.ax]'
[08:53:44:872] InfoReader::readLine: line: 'ffh264vda   ffmpeg    working   FFmpeg H.264 (VDA)  [h264_vda]'
[08:53:44:872] InfoReader::readLine: found codec: 'ffh264vda' 'FFmpeg H.264 (VDA)  [h264_vda]'
[08:53:44:873] InfoReader::readLine: line: 'ffsvq3      ffmpeg    working   FFmpeg Sorenson Video v3 (SVQ3)  [svq3]'
[08:53:44:873] InfoReader::readLine: found codec: 'ffsvq3' 'FFmpeg Sorenson Video v3 (SVQ3)  [svq3]'
[08:53:44:873] InfoReader::readLine: line: 'ffodivx     ffmpeg    working   FFmpeg MPEG-4  [mpeg4]'
[08:53:44:873] InfoReader::readLine: found codec: 'ffodivx' 'FFmpeg MPEG-4  [mpeg4]'
[08:53:44:873] InfoReader::readLine: line: 'ffodivxvdpau ffmpeg    working   FFmpeg MPEG-4,DIVX-4/5 (VDPAU)  [mpeg4_vdpau]'
[08:53:44:873] InfoReader::readLine: found codec: 'ffodivxvdpau' 'FFmpeg MPEG-4,DIVX-4/5 (VDPAU)  [mpeg4_vdpau]'
[08:53:44:873] InfoReader::readLine: line: 'ffodivxcrystalhd ffmpeg    working   FFmpeg MPEG-4,DIVX-4/5 (CrystalHD)  [mpeg4_crystalhd]'
[08:53:44:873] InfoReader::readLine: found codec: 'ffodivxcrystalhd' 'FFmpeg MPEG-4,DIVX-4/5 (CrystalHD)  [mpeg4_crystalhd]'
[08:53:44:873] InfoReader::readLine: line: 'ffwv1f      ffmpeg    working   WV1F MPEG-4  [mpeg4]'
[08:53:44:873] InfoReader::readLine: found codec: 'ffwv1f' 'WV1F MPEG-4  [mpeg4]'
[08:53:44:873] InfoReader::readLine: line: 'fflibschroedinger ffmpeg    working   Dirac (through FFmpeg libschroedinger)  [libschroedinger]'
[08:53:44:873] InfoReader::readLine: found codec: 'fflibschroedinger' 'Dirac (through FFmpeg libschroedinger)  [libschroedinger]'
[08:53:44:873] InfoReader::readLine: line: 'fflibdirac  ffmpeg    working   Dirac (through FFmpeg libdirac)  [libdirac]'
[08:53:44:873] InfoReader::readLine: found codec: 'fflibdirac' 'Dirac (through FFmpeg libdirac)  [libdirac]'
[08:53:44:873] InfoReader::readLine: line: 'xvid        xvid      working   Xvid (MPEG-4)  [libxvidcore.a]'
[08:53:44:873] InfoReader::readLine: found codec: 'xvid' 'Xvid (MPEG-4)  [libxvidcore.a]'
[08:53:44:873] InfoReader::readLine: line: 'divx4vfw    vfw       problems  DivX4Windows-VFW  [divx.dll]'
[08:53:44:873] InfoReader::readLine: found codec: 'divx4vfw' 'DivX4Windows-VFW  [divx.dll]'
[08:53:44:873] InfoReader::readLine: line: 'divxds      dshow     working   DivX ;-) (MSMPEG-4 v3)  [divx_c32.ax]'
[08:53:44:874] InfoReader::readLine: found codec: 'divxds' 'DivX ;-) (MSMPEG-4 v3)  [divx_c32.ax]'
[08:53:44:874] InfoReader::readLine: line: 'divx        vfw       working   DivX ;-) (MSMPEG-4 v3)  [divxc32.dll]'
[08:53:44:874] InfoReader::readLine: found codec: 'divx' 'DivX ;-) (MSMPEG-4 v3)  [divxc32.dll]'
[08:53:44:874] InfoReader::readLine: line: 'mpeg4ds     dshow     working   Microsoft MPEG-4 v1/v2  [mpg4ds32.ax]'
[08:53:44:874] InfoReader::readLine: found codec: 'mpeg4ds' 'Microsoft MPEG-4 v1/v2  [mpg4ds32.ax]'
[08:53:44:874] InfoReader::readLine: line: 'mpeg4       vfw       working   Microsoft MPEG-4 v1/v2  [mpg4c32.dll]'
[08:53:44:874] InfoReader::readLine: found codec: 'mpeg4' 'Microsoft MPEG-4 v1/v2  [mpg4c32.dll]'
[08:53:44:874] InfoReader::readLine: line: 'wmv9dmo     dmo       working   Windows Media Video 9 DMO  [wmv9dmod.dll]'
[08:53:44:874] InfoReader::readLine: found codec: 'wmv9dmo' 'Windows Media Video 9 DMO  [wmv9dmod.dll]'
[08:53:44:874] InfoReader::readLine: line: 'wmvdmo      dmo       working   Windows Media Video DMO  [wmvdmod.dll]'
[08:53:44:874] InfoReader::readLine: found codec: 'wmvdmo' 'Windows Media Video DMO  [wmvdmod.dll]'
[08:53:44:874] InfoReader::readLine: line: 'wmv8        dshow     working   Windows Media Video 8  [wmv8ds32.ax]'
[08:53:44:874] InfoReader::readLine: found codec: 'wmv8' 'Windows Media Video 8  [wmv8ds32.ax]'
[08:53:44:874] InfoReader::readLine: line: 'wmv7        dshow     working   Windows Media Video 7  [wmvds32.ax]'
[08:53:44:874] InfoReader::readLine: found codec: 'wmv7' 'Windows Media Video 7  [wmvds32.ax]'
[08:53:44:874] InfoReader::readLine: line: 'wmvadmo     dmo       working   Windows Media Video Adv DMO  [wmvadvd.dll]'
[08:53:44:875] InfoReader::readLine: found codec: 'wmvadmo' 'Windows Media Video Adv DMO  [wmvadvd.dll]'
[08:53:44:875] InfoReader::readLine: line: 'wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile  [wvc1dmod.dll]'
[08:53:44:875] InfoReader::readLine: found codec: 'wmvvc1dmo' 'Windows Media Video (VC-1) Advanced Profile  [wvc1dmod.dll]'
[08:53:44:875] InfoReader::readLine: line: 'wmsdmod     dmo       working   Windows Media Screen Codec 2  [wmsdmod.dll]'
[08:53:44:875] InfoReader::readLine: found codec: 'wmsdmod' 'Windows Media Screen Codec 2  [wmsdmod.dll]'
[08:53:44:875] InfoReader::readLine: line: 'wms10dmod   dmo       working   Windows Media Screen Codec 2 from WMP10  [wms10dmod.dll]'
[08:53:44:875] InfoReader::readLine: found codec: 'wms10dmod' 'Windows Media Screen Codec 2 from WMP10  [wms10dmod.dll]'
[08:53:44:875] InfoReader::readLine: line: 'msascreen   dmo       working   MS ATC screen decoder 1  [scdec.dll]'
[08:53:44:875] InfoReader::readLine: found codec: 'msascreen' 'MS ATC screen decoder 1  [scdec.dll]'
[08:53:44:875] InfoReader::readLine: line: 'eescreen    dmo       working   expression encoder  [Microsoft.Expression.Encoder.EEScreen.Codec.dll]'
[08:53:44:875] InfoReader::readLine: found codec: 'eescreen' 'expression encoder  [Microsoft.Expression.Encoder.EEScreen.Codec.dll]'
[08:53:44:875] InfoReader::readLine: line: 'gotomeeting dmo       working   GoToMeeting codec  [G2M.dll]'
[08:53:44:875] InfoReader::readLine: found codec: 'gotomeeting' 'GoToMeeting codec  [G2M.dll]'
[08:53:44:875] InfoReader::readLine: line: 'ubmp4       vfw       problems  UB Video MPEG-4  [ubvmp4d.dll]'
[08:53:44:876] InfoReader::readLine: found codec: 'ubmp4' 'UB Video MPEG-4  [ubvmp4d.dll]'
[08:53:44:876] InfoReader::readLine: line: 'geomp4      vfw       working   GeoVision Advanced MPEG-4  [GXAMP4.dll]'
[08:53:44:876] InfoReader::readLine: found codec: 'geomp4' 'GeoVision Advanced MPEG-4  [GXAMP4.dll]'
[08:53:44:876] InfoReader::readLine: line: 'ffmjpeg     ffmpeg    working   FFmpeg MJPEG  [mjpeg]'
[08:53:44:876] InfoReader::readLine: found codec: 'ffmjpeg' 'FFmpeg MJPEG  [mjpeg]'
[08:53:44:876] InfoReader::readLine: line: 'ffmjpegb    ffmpeg    working   FFmpeg MJPEG-B  [mjpegb]'
[08:53:44:876] InfoReader::readLine: found codec: 'ffmjpegb' 'FFmpeg MJPEG-B  [mjpegb]'
[08:53:44:876] InfoReader::readLine: line: 'ijpg        ijpg      working   Independent JPEG Group's codec  [libjpeg]'
[08:53:44:876] InfoReader::readLine: found codec: 'ijpg' 'Independent JPEG Group's codec  [libjpeg]'
[08:53:44:876] InfoReader::readLine: line: 'm3jpeg      vfw       working   Morgan Motion JPEG Codec  [m3jpeg32.dll]'
[08:53:44:876] InfoReader::readLine: found codec: 'm3jpeg' 'Morgan Motion JPEG Codec  [m3jpeg32.dll]'
[08:53:44:876] InfoReader::readLine: line: 'mjpeg       vfw       working   MainConcept Motion JPEG  [mcmjpg32.dll]'
[08:53:44:876] InfoReader::readLine: found codec: 'mjpeg' 'MainConcept Motion JPEG  [mcmjpg32.dll]'
[08:53:44:876] InfoReader::readLine: line: 'avid        vfw       working   AVID Motion JPEG  [AvidAVICodec.dll]'
[08:53:44:876] InfoReader::readLine: found codec: 'avid' 'AVID Motion JPEG  [AvidAVICodec.dll]'
[08:53:44:876] InfoReader::readLine: line: 'LEAD        vfw       working   LEAD (M)JPEG  [LCodcCMP.dll]'
[08:53:44:876] InfoReader::readLine: found codec: 'LEAD' 'LEAD (M)JPEG  [LCodcCMP.dll]'
[08:53:44:876] InfoReader::readLine: line: 'acdsee      vfw       working   ACDSee mjpeg  [ACDV.dll]'
[08:53:44:877] InfoReader::readLine: found codec: 'acdsee' 'ACDSee mjpeg  [ACDV.dll]'
[08:53:44:877] InfoReader::readLine: line: 'imagepower  vfw       problems  ImagePower MJPEG2000  [jp2avi.dll]'
[08:53:44:877] InfoReader::readLine: found codec: 'imagepower' 'ImagePower MJPEG2000  [jp2avi.dll]'
[08:53:44:877] InfoReader::readLine: line: 'fflibopenjpeg ffmpeg    working   OpenJPEG MJPEG2000  [libopenjpeg]'
[08:53:44:877] InfoReader::readLine: found codec: 'fflibopenjpeg' 'OpenJPEG MJPEG2000  [libopenjpeg]'
[08:53:44:877] InfoReader::readLine: line: 'm3jpeg2k    vfw       working   Morgan MJPEG2000  [m3jp2k32.dll]'
[08:53:44:877] InfoReader::readLine: found codec: 'm3jpeg2k' 'Morgan MJPEG2000  [m3jp2k32.dll]'
[08:53:44:877] InfoReader::readLine: line: 'm3jpegds    dshow     crashing  Morgan MJPEG  [m3jpegdec.ax]'
[08:53:44:877] InfoReader::readLine: found codec: 'm3jpegds' 'Morgan MJPEG  [m3jpegdec.ax]'
[08:53:44:877] InfoReader::readLine: line: 'pegasusm    vfw       crashing  Pegasus Motion JPEG  [pvmjpg21.dll]'
[08:53:44:877] InfoReader::readLine: found codec: 'pegasusm' 'Pegasus Motion JPEG  [pvmjpg21.dll]'
[08:53:44:877] InfoReader::readLine: line: 'pegasusl    vfw       crashing  Pegasus lossless JPEG  [pvljpg20.dll]'
[08:53:44:878] InfoReader::readLine: found codec: 'pegasusl' 'Pegasus lossless JPEG  [pvljpg20.dll]'
[08:53:44:878] InfoReader::readLine: line: 'pegasusmwv  vfw       crashing  Pegasus Motion Wavelet 2000  [pvwv220.dll]'
[08:53:44:878] InfoReader::readLine: found codec: 'pegasusmwv' 'Pegasus Motion Wavelet 2000  [pvwv220.dll]'
[08:53:44:878] InfoReader::readLine: line: 'fffrwu      ffmpeg    working   FFmpeg Forward Uncompressed Video Codec  [FRWU]'
[08:53:44:878] InfoReader::readLine: found codec: 'fffrwu' 'FFmpeg Forward Uncompressed Video Codec  [FRWU]'
[08:53:44:878] InfoReader::readLine: line: 'frwuvfw     vfw       working   Forward Uncompressed Video Codec  [FRWU.dll]'
[08:53:44:878] InfoReader::readLine: found codec: 'frwuvfw' 'Forward Uncompressed Video Codec  [FRWU.dll]'
[08:53:44:878] InfoReader::readLine: line: 'frwdvfw     vfw       working   Forward JPEG Video Codec  [FRWD.dll]'
[08:53:44:878] InfoReader::readLine: found codec: 'frwdvfw' 'Forward JPEG Video Codec  [FRWD.dll]'
[08:53:44:878] InfoReader::readLine: line: 'frwtvfw     vfw       working   Forward JPEG+Alpha Video  [FRWT.dll]'
[08:53:44:878] InfoReader::readLine: found codec: 'frwtvfw' 'Forward JPEG+Alpha Video  [FRWT.dll]'
[08:53:44:878] InfoReader::readLine: line: 'vivo        vfw       working   Vivo H.263  [ivvideo.dll]'
[08:53:44:878] InfoReader::readLine: found codec: 'vivo' 'Vivo H.263  [ivvideo.dll]'
[08:53:44:878] InfoReader::readLine: line: 'u263        dshow     working   UB Video H.263/H.263+/H.263++  [ubv263d+.ax]'
[08:53:44:878] InfoReader::readLine: found codec: 'u263' 'UB Video H.263/H.263+/H.263++  [ubv263d+.ax]'
[08:53:44:878] InfoReader::readLine: line: 'i263        vfw       working   I263  [i263_32.drv]'
[08:53:44:878] InfoReader::readLine: found codec: 'i263' 'I263  [i263_32.drv]'
[08:53:44:879] InfoReader::readLine: line: 'ffi263      ffmpeg    working   FFmpeg I263  [h263i]'
[08:53:44:879] InfoReader::readLine: found codec: 'ffi263' 'FFmpeg I263  [h263i]'
[08:53:44:879] InfoReader::readLine: line: 'ffh263      ffmpeg    working   FFmpeg H.263+  [h263]'
[08:53:44:879] InfoReader::readLine: found codec: 'ffh263' 'FFmpeg H.263+  [h263]'
[08:53:44:879] InfoReader::readLine: line: 'ffzygo      ffmpeg    untested  FFmpeg ZyGo  [h263]'
[08:53:44:879] InfoReader::readLine: found codec: 'ffzygo' 'FFmpeg ZyGo  [h263]'
[08:53:44:879] InfoReader::readLine: line: 'h263xa      xanim     crashing  XAnim's CCITT H.263  [vid_h263.xa]'
[08:53:44:879] InfoReader::readLine: found codec: 'h263xa' 'XAnim's CCITT H.263  [vid_h263.xa]'
[08:53:44:879] InfoReader::readLine: line: 'ffh261      ffmpeg    working   CCITT H.261  [h261]'
[08:53:44:879] InfoReader::readLine: found codec: 'ffh261' 'CCITT H.261  [h261]'
[08:53:44:879] InfoReader::readLine: line: 'qt261       qtvideo   working   QuickTime H.261 video  [QuickTime.qts]'
[08:53:44:879] InfoReader::readLine: found codec: 'qt261' 'QuickTime H.261 video  [QuickTime.qts]'
[08:53:44:879] InfoReader::readLine: line: 'h261xa      xanim     problems  XAnim's CCITT H.261  [vid_h261.xa]'
[08:53:44:879] InfoReader::readLine: found codec: 'h261xa' 'XAnim's CCITT H.261  [vid_h261.xa]'
[08:53:44:879] InfoReader::readLine: line: 'm261        vfw       untested  M261  [msh261.drv]'
[08:53:44:879] InfoReader::readLine: found codec: 'm261' 'M261  [msh261.drv]'
[08:53:44:880] InfoReader::readLine: line: 'indeo5ds    dshow     working   Intel Indeo 5  [ir50_32.dll]'
[08:53:44:880] InfoReader::readLine: found codec: 'indeo5ds' 'Intel Indeo 5  [ir50_32.dll]'
[08:53:44:880] InfoReader::readLine: line: 'indeo5      vfwex     working   Intel Indeo 5  [ir50_32.dll]'
[08:53:44:880] InfoReader::readLine: found codec: 'indeo5' 'Intel Indeo 5  [ir50_32.dll]'
[08:53:44:880] InfoReader::readLine: line: 'indeo4      vfw       working   Intel Indeo 4.1  [ir41_32.dll]'
[08:53:44:880] InfoReader::readLine: found codec: 'indeo4' 'Intel Indeo 4.1  [ir41_32.dll]'
[08:53:44:880] InfoReader::readLine: line: 'indeo3      vfwex     working   Intel Indeo 3.1/3.2  [ir32_32.dll]'
[08:53:44:880] InfoReader::readLine: found codec: 'indeo3' 'Intel Indeo 3.1/3.2  [ir32_32.dll]'
[08:53:44:880] InfoReader::readLine: line: 'indeo5xa    xanim     working   XAnim's Intel Indeo 5  [vid_iv50.xa]'
[08:53:44:880] InfoReader::readLine: found codec: 'indeo5xa' 'XAnim's Intel Indeo 5  [vid_iv50.xa]'
[08:53:44:880] InfoReader::readLine: line: 'indeo4xa    xanim     working   XAnim's Intel Indeo 4.1  [vid_iv41.xa]'
[08:53:44:880] InfoReader::readLine: found codec: 'indeo4xa' 'XAnim's Intel Indeo 4.1  [vid_iv41.xa]'
[08:53:44:880] InfoReader::readLine: line: 'indeo3xa    xanim     working   XAnim's Intel Indeo 3.1/3.2  [vid_iv32.xa]'
[08:53:44:880] InfoReader::readLine: found codec: 'indeo3xa' 'XAnim's Intel Indeo 3.1/3.2  [vid_iv32.xa]'
[08:53:44:880] InfoReader::readLine: line: 'ffindeo5    ffmpeg    working   FFmpeg Indeo 5  [indeo5]'
[08:53:44:881] InfoReader::readLine: found codec: 'ffindeo5' 'FFmpeg Indeo 5  [indeo5]'
[08:53:44:881] InfoReader::readLine: line: 'ffdv        ffmpeg    working   FFmpeg DV  [dvvideo]'
[08:53:44:881] InfoReader::readLine: found codec: 'ffdv' 'FFmpeg DV  [dvvideo]'
[08:53:44:881] InfoReader::readLine: line: 'qdv         dshow     working   Sony Digital Video (DV)  [qdv.dll]'
[08:53:44:881] InfoReader::readLine: found codec: 'qdv' 'Sony Digital Video (DV)  [qdv.dll]'
[08:53:44:881] InfoReader::readLine: line: 'libdv       libdv     working   Raw DV (libdv)  [libdv.so.2]'
[08:53:44:881] InfoReader::readLine: found codec: 'libdv' 'Raw DV (libdv)  [libdv.so.2]'
[08:53:44:881] InfoReader::readLine: line: 'mcdv        vfw       working   MainConcept DV Codec  [mcdvd_32.dll]'
[08:53:44:881] InfoReader::readLine: found codec: 'mcdv' 'MainConcept DV Codec  [mcdvd_32.dll]'
[08:53:44:881] InfoReader::readLine: line: '3ivXxa      xanim     working   XAnim's 3ivx Delta 3.5 plugin  [vid_3ivX.xa]'
[08:53:44:881] InfoReader::readLine: found codec: '3ivXxa' 'XAnim's 3ivx Delta 3.5 plugin  [vid_3ivX.xa]'
[08:53:44:881] InfoReader::readLine: line: '3ivX        dshow     working   3ivx Delta 4.5  [3ivxDSDecoder.ax]'
[08:53:44:881] InfoReader::readLine: found codec: '3ivX' '3ivx Delta 4.5  [3ivxDSDecoder.ax]'
[08:53:44:881] InfoReader::readLine: line: 'rv3040      realvid   problems  Linux RealPlayer 10 RV30/40  [drvc.so]'
[08:53:44:881] InfoReader::readLine: found codec: 'rv3040' 'Linux RealPlayer 10 RV30/40  [drvc.so]'
[08:53:44:881] InfoReader::readLine: line: 'rv3040win   realvid   working   Win32 RealPlayer 10 RV30/40  [drvc.dll]'
[08:53:44:881] InfoReader::readLine: found codec: 'rv3040win' 'Win32 RealPlayer 10 RV30/40  [drvc.dll]'
[08:53:44:881] InfoReader::readLine: line: 'rv40        realvid   problems  Linux RealPlayer 9 RV40  [drv4.so.6.0]'
[08:53:44:881] InfoReader::readLine: found codec: 'rv40' 'Linux RealPlayer 9 RV40  [drv4.so.6.0]'
[08:53:44:882] InfoReader::readLine: line: 'rv40win     realvid   working   Win32 RealPlayer 9 RV40  [drv43260.dll]'
[08:53:44:882] InfoReader::readLine: found codec: 'rv40win' 'Win32 RealPlayer 9 RV40  [drv43260.dll]'
[08:53:44:882] InfoReader::readLine: line: 'rv40mac     realvid   working   Mac OS X RealPlayer 9 RV40  [drvc.bundle/Contents/MacOS/drvc]'
[08:53:44:882] InfoReader::readLine: found codec: 'rv40mac' 'Mac OS X RealPlayer 9 RV40  [drvc.bundle/Contents/MacOS/drvc]'
[08:53:44:882] InfoReader::readLine: line: 'rv30        realvid   problems  Linux RealPlayer 8 RV30  [drv3.so.6.0]'
[08:53:44:882] InfoReader::readLine: found codec: 'rv30' 'Linux RealPlayer 8 RV30  [drv3.so.6.0]'
[08:53:44:882] InfoReader::readLine: line: 'rv30win     realvid   working   Win32 RealPlayer 8 RV30  [drv33260.dll]'
[08:53:44:882] InfoReader::readLine: found codec: 'rv30win' 'Win32 RealPlayer 8 RV30  [drv33260.dll]'
[08:53:44:882] InfoReader::readLine: line: 'rv30mac     realvid   working   Mac OS X RealPlayer 9 RV30  [drvc.bundle/Contents/MacOS/drvc]'
[08:53:44:882] InfoReader::readLine: found codec: 'rv30mac' 'Mac OS X RealPlayer 9 RV30  [drvc.bundle/Contents/MacOS/drvc]'
[08:53:44:882] InfoReader::readLine: line: 'ffrv20      ffmpeg    working   FFmpeg RV20  [rv20]'
[08:53:44:882] InfoReader::readLine: found codec: 'ffrv20' 'FFmpeg RV20  [rv20]'
[08:53:44:882] InfoReader::readLine: line: 'ffrv30      ffmpeg    problems  FFmpeg RV30  [rv30]'
[08:53:44:882] InfoReader::readLine: found codec: 'ffrv30' 'FFmpeg RV30  [rv30]'
[08:53:44:882] InfoReader::readLine: line: 'ffrv40      ffmpeg    working   FFmpeg RV40  [rv40]'
[08:53:44:882] InfoReader::readLine: found codec: 'ffrv40' 'FFmpeg RV40  [rv40]'
[08:53:44:882] InfoReader::readLine: line: 'rv20        realvid   problems  Linux RealPlayer 8 RV20  [drv2.so.6.0]'
[08:53:44:883] InfoReader::readLine: found codec: 'rv20' 'Linux RealPlayer 8 RV20  [drv2.so.6.0]'
[08:53:44:883] InfoReader::readLine: line: 'rv20winrp10 realvid   working   Win32 RealPlayer 10 RV20  [drv2.dll]'
[08:53:44:883] InfoReader::readLine: found codec: 'rv20winrp10' 'Win32 RealPlayer 10 RV20  [drv2.dll]'
[08:53:44:883] InfoReader::readLine: line: 'rv20win     realvid   working   Win32 RealPlayer 8 RV20  [drv23260.dll]'
[08:53:44:883] InfoReader::readLine: found codec: 'rv20win' 'Win32 RealPlayer 8 RV20  [drv23260.dll]'
[08:53:44:883] InfoReader::readLine: line: 'rv20mac     realvid   working   Mac OS X RealPlayer 9 RV20  [drv2.bundle/Contents/MacOS/drv2]'
[08:53:44:883] InfoReader::readLine: found codec: 'rv20mac' 'Mac OS X RealPlayer 9 RV20  [drv2.bundle/Contents/MacOS/drv2]'
[08:53:44:883] InfoReader::readLine: line: 'ffrv10      ffmpeg    working   FFmpeg RV10  [rv10]'
[08:53:44:883] InfoReader::readLine: found codec: 'ffrv10' 'FFmpeg RV10  [rv10]'
[08:53:44:883] InfoReader::readLine: line: 'alpary      dshow     working   Alparysoft lossless codec dshow  [aslcodec_dshow.dll]'
[08:53:44:883] InfoReader::readLine: found codec: 'alpary' 'Alparysoft lossless codec dshow  [aslcodec_dshow.dll]'
[08:53:44:883] InfoReader::readLine: line: 'alpary2     vfw       working   Alparysoft lossless codec vfw  [aslcodec_vfw.dll]'
[08:53:44:883] InfoReader::readLine: found codec: 'alpary2' 'Alparysoft lossless codec vfw  [aslcodec_vfw.dll]'
[08:53:44:883] InfoReader::readLine: line: 'LEADMW20    dshow     working   Lead CMW wavelet 2.0  [LCODCCMW2E.dll]'
[08:53:44:883] InfoReader::readLine: found codec: 'LEADMW20' 'Lead CMW wavelet 2.0  [LCODCCMW2E.dll]'
[08:53:44:883] InfoReader::readLine: line: 'cineformhd  dshow     working   CineForm HD  [CFDecode2.ax]'
[08:53:44:883] InfoReader::readLine: found codec: 'cineformhd' 'CineForm HD  [CFDecode2.ax]'
[08:53:44:883] InfoReader::readLine: line: 'fflagarith  ffmpeg    problems  Lagarith Lossless Video Codec  [lagarith]'
[08:53:44:884] InfoReader::readLine: found codec: 'fflagarith' 'Lagarith Lossless Video Codec  [lagarith]'
[08:53:44:884] InfoReader::readLine: line: 'lagarith    vfw       working   Lagarith Lossless Video Codec  [lagarith.dll]'
[08:53:44:884] InfoReader::readLine: found codec: 'lagarith' 'Lagarith Lossless Video Codec  [lagarith.dll]'
[08:53:44:884] InfoReader::readLine: line: 'psiv        vfw       working   Infinite Video PSI_V  [psiv.dll]'
[08:53:44:884] InfoReader::readLine: found codec: 'psiv' 'Infinite Video PSI_V  [psiv.dll]'
[08:53:44:884] InfoReader::readLine: line: 'midivid1    vfw       working   http://www.midivid.com/codec/download.html  [MLZCodec.dll]'
[08:53:44:884] InfoReader::readLine: found codec: 'midivid1' 'http://www.midivid.com/codec/download.html  [MLZCodec.dll]'
[08:53:44:884] InfoReader::readLine: line: 'midivid2    vfw       working   http://www.midivid.com/codec/download.html  [MVCodec.dll]'
[08:53:44:884] InfoReader::readLine: found codec: 'midivid2' 'http://www.midivid.com/codec/download.html  [MVCodec.dll]'
[08:53:44:884] InfoReader::readLine: line: 'midivid3    vfw       working   www.midivid.com/codec/mv3codec.html  [MV3.dll]'
[08:53:44:884] InfoReader::readLine: found codec: 'midivid3' 'www.midivid.com/codec/mv3codec.html  [MV3.dll]'
[08:53:44:884] InfoReader::readLine: line: 'moyea       vfw       working   Moyea Flash to Video Converter  [MyFlashZip0.ax]'
[08:53:44:884] InfoReader::readLine: found codec: 'moyea' 'Moyea Flash to Video Converter  [MyFlashZip0.ax]'
[08:53:44:884] InfoReader::readLine: line: 'nsvideo     vfw       working   Power VideoWorks video  [nsvideo.dll]'
[08:53:44:884] InfoReader::readLine: found codec: 'nsvideo' 'Power VideoWorks video  [nsvideo.dll]'
[08:53:44:885] InfoReader::readLine: line: 'smv2vfw     vfw       working   DideoNET SMV2  [smv2vfw.dll]'
[08:53:44:885] InfoReader::readLine: found codec: 'smv2vfw' 'DideoNET SMV2  [smv2vfw.dll]'
[08:53:44:885] InfoReader::readLine: line: 'cfhdvfw     vfw       working   CineForm HD  [cinevfw.dll]'
[08:53:44:885] InfoReader::readLine: found codec: 'cfhdvfw' 'CineForm HD  [cinevfw.dll]'
[08:53:44:885] InfoReader::readLine: line: 'canopushq   vfw       working   Canopus HQ Codec  [CUVCcodc.dll]'
[08:53:44:885] InfoReader::readLine: found codec: 'canopushq' 'Canopus HQ Codec  [CUVCcodc.dll]'
[08:53:44:885] InfoReader::readLine: line: 'canopusll   vfw       working   Canopus Lossless Codec  [CLLCcodc.dll]'
[08:53:44:885] InfoReader::readLine: found codec: 'canopusll' 'Canopus Lossless Codec  [CLLCcodc.dll]'
[08:53:44:885] InfoReader::readLine: line: 'ffvp3       ffmpeg    untested  FFmpeg VP3  [vp3]'
[08:53:44:885] InfoReader::readLine: found codec: 'ffvp3' 'FFmpeg VP3  [vp3]'
[08:53:44:885] InfoReader::readLine: line: 'fftheora    ffmpeg    untested  FFmpeg Theora  [theora]'
[08:53:44:885] InfoReader::readLine: found codec: 'fftheora' 'FFmpeg Theora  [theora]'
[08:53:44:885] InfoReader::readLine: line: 'vp3         vfwex     working   On2 Open Source VP3 Codec  [vp31vfw.dll]'
[08:53:44:885] InfoReader::readLine: found codec: 'vp3' 'On2 Open Source VP3 Codec  [vp31vfw.dll]'
[08:53:44:885] InfoReader::readLine: line: 'vp4         vfwex     working   On2 VP4 Personal Codec  [vp4vfw.dll]'
[08:53:44:885] InfoReader::readLine: found codec: 'vp4' 'On2 VP4 Personal Codec  [vp4vfw.dll]'
[08:53:44:885] InfoReader::readLine: line: 'ffvp5       ffmpeg    working   FFmpeg VP5  [vp5]'
[08:53:44:885] InfoReader::readLine: found codec: 'ffvp5' 'FFmpeg VP5  [vp5]'
[08:53:44:885] InfoReader::readLine: line: 'vp5         vfwex     working   On2 VP5 Personal Codec  [vp5vfw.dll]'
[08:53:44:886] InfoReader::readLine: found codec: 'vp5' 'On2 VP5 Personal Codec  [vp5vfw.dll]'
[08:53:44:886] InfoReader::readLine: line: 'ffvp6       ffmpeg    working   FFmpeg VP6  [vp6]'
[08:53:44:886] InfoReader::readLine: found codec: 'ffvp6' 'FFmpeg VP6  [vp6]'
[08:53:44:886] InfoReader::readLine: line: 'ffvp6a      ffmpeg    untested  FFmpeg VP6A  [vp6a]'
[08:53:44:886] InfoReader::readLine: found codec: 'ffvp6a' 'FFmpeg VP6A  [vp6a]'
[08:53:44:886] InfoReader::readLine: line: 'ffvp6f      ffmpeg    working   FFmpeg VP6 Flash  [vp6f]'
[08:53:44:886] InfoReader::readLine: found codec: 'ffvp6f' 'FFmpeg VP6 Flash  [vp6f]'
[08:53:44:886] InfoReader::readLine: line: 'vp6         vfwex     working   On2 VP6 Personal Codec  [vp6vfw.dll]'
[08:53:44:886] InfoReader::readLine: found codec: 'vp6' 'On2 VP6 Personal Codec  [vp6vfw.dll]'
[08:53:44:886] InfoReader::readLine: line: 'vp6f        vfwex     working   On2 VP6F Personal Codec  [vp6vfw.dll]'
[08:53:44:886] InfoReader::readLine: found codec: 'vp6f' 'On2 VP6F Personal Codec  [vp6vfw.dll]'
[08:53:44:886] InfoReader::readLine: line: 'vp7         vfwex     working   On2 VP7 Personal Codec  [vp7vfw.dll]'
[08:53:44:886] InfoReader::readLine: found codec: 'vp7' 'On2 VP7 Personal Codec  [vp7vfw.dll]'
[08:53:44:886] InfoReader::readLine: line: 'ffvp8       ffmpeg    working   FFmpeg VP8  [vp8]'
[08:53:44:886] InfoReader::readLine: found codec: 'ffvp8' 'FFmpeg VP8  [vp8]'
[08:53:44:886] InfoReader::readLine: line: 'fflibvpx    ffmpeg    working   FFmpeg wrapper for libvpx/VP8  [libvpx]'
[08:53:44:886] InfoReader::readLine: found codec: 'fflibvpx' 'FFmpeg wrapper for libvpx/VP8  [libvpx]'
[08:53:44:886] InfoReader::readLine: line: 'mwv1        vfw       working   Motion Wavelets  [icmw_32.dll]'
[08:53:44:887] InfoReader::readLine: found codec: 'mwv1' 'Motion Wavelets  [icmw_32.dll]'
[08:53:44:887] InfoReader::readLine: line: 'wavcvfw     vfw       working   centre for wavelets, approximation and information processing  [WavCWAIP.dll]'
[08:53:44:887] InfoReader::readLine: found codec: 'wavcvfw' 'centre for wavelets, approximation and information processing  [WavCWAIP.dll]'
[08:53:44:887] InfoReader::readLine: line: 'asv2        vfw       working   ASUS V2  [asusasv2.dll]'
[08:53:44:887] InfoReader::readLine: found codec: 'asv2' 'ASUS V2  [asusasv2.dll]'
[08:53:44:887] InfoReader::readLine: line: 'asv1        vfw       working   ASUS V1  [asusasvd.dll]'
[08:53:44:887] InfoReader::readLine: found codec: 'asv1' 'ASUS V1  [asusasvd.dll]'
[08:53:44:887] InfoReader::readLine: line: 'ffultimotion ffmpeg    working   FFmpeg IBM Ultimotion  [ultimotion]'
[08:53:44:887] InfoReader::readLine: found codec: 'ffultimotion' 'FFmpeg IBM Ultimotion  [ultimotion]'
[08:53:44:887] InfoReader::readLine: line: 'ultimotion  vfw       working   IBM Ultimotion  [ultimo.dll]'
[08:53:44:887] InfoReader::readLine: found codec: 'ultimotion' 'IBM Ultimotion  [ultimo.dll]'
[08:53:44:887] InfoReader::readLine: line: 'mss1        dshow     working   Windows Screen Video  [msscds32.ax]'
[08:53:44:887] InfoReader::readLine: found codec: 'mss1' 'Windows Screen Video  [msscds32.ax]'
[08:53:44:887] InfoReader::readLine: line: 'ucod        vfw       working   UCOD-ClearVideo  [clrviddd.dll]'
[08:53:44:887] InfoReader::readLine: found codec: 'ucod' 'UCOD-ClearVideo  [clrviddd.dll]'
[08:53:44:887] InfoReader::readLine: line: 'vcr2        vfw       working   ATI VCR-2  [ativcr2.dll]'
[08:53:44:887] InfoReader::readLine: found codec: 'vcr2' 'ATI VCR-2  [ativcr2.dll]'
[08:53:44:887] InfoReader::readLine: line: 'slifvfw     vfw       working   SoftLab-NSK Forward MPEG2 I-frames  [slif.dll]'
[08:53:44:887] InfoReader::readLine: found codec: 'slifvfw' 'SoftLab-NSK Forward MPEG2 I-frames  [slif.dll]'
[08:53:44:888] InfoReader::readLine: line: 'blox        vfw       working   Jan Jezabeks BLOX MPEG Codec  [blox.dll]'
[08:53:44:888] InfoReader::readLine: found codec: 'blox' 'Jan Jezabeks BLOX MPEG Codec  [blox.dll]'
[08:53:44:888] InfoReader::readLine: line: 'cjpg        vfw       working   Creative Labs Video Blaster Webcam  [CtWbJpg.DLL]'
[08:53:44:888] InfoReader::readLine: found codec: 'cjpg' 'Creative Labs Video Blaster Webcam  [CtWbJpg.DLL]'
[08:53:44:888] InfoReader::readLine: line: 'kensington  vfw       working   kensington webcam  [aoxdxipl.ax]'
[08:53:44:888] InfoReader::readLine: found codec: 'kensington' 'kensington webcam  [aoxdxipl.ax]'
[08:53:44:888] InfoReader::readLine: line: 'xjpg        vfw       working   xiricam Veo PC Camera  [camfc.dll]'
[08:53:44:888] InfoReader::readLine: found codec: 'xjpg' 'xiricam Veo PC Camera  [camfc.dll]'
[08:53:44:888] InfoReader::readLine: line: 'ffduck      ffmpeg    working   Duck Truemotion1  [truemotion1]'
[08:53:44:888] InfoReader::readLine: found codec: 'ffduck' 'Duck Truemotion1  [truemotion1]'
[08:53:44:888] InfoReader::readLine: line: 'fftm20      ffmpeg    working   FFmpeg Duck/On2 TrueMotion 2.0  [truemotion2]'
[08:53:44:888] InfoReader::readLine: found codec: 'fftm20' 'FFmpeg Duck/On2 TrueMotion 2.0  [truemotion2]'
[08:53:44:888] InfoReader::readLine: line: 'tm20        dshow     working   TrueMotion 2.0  [tm20dec.ax]'
[08:53:44:888] InfoReader::readLine: found codec: 'tm20' 'TrueMotion 2.0  [tm20dec.ax]'
[08:53:44:888] InfoReader::readLine: line: 'tm2xvfw     vfw       working   TrueMotion 2.0  [tm2X.dll]'
[08:53:44:888] InfoReader::readLine: found codec: 'tm2xvfw' 'TrueMotion 2.0  [tm2X.dll]'
[08:53:44:888] InfoReader::readLine: line: 'tr20        vfw       working   TrueMotion RT  [tr2032.dll]'
[08:53:44:888] InfoReader::readLine: found codec: 'tr20' 'TrueMotion RT  [tr2032.dll]'
[08:53:44:889] InfoReader::readLine: line: 'sif1vfw     vfw       working   sif1 alpha4  [Sif1_vfw.dll]'
[08:53:44:889] InfoReader::readLine: found codec: 'sif1vfw' 'sif1 alpha4  [Sif1_vfw.dll]'
[08:53:44:889] InfoReader::readLine: line: 'sif1ds      dshow     problems  sif1 alpha4  [Sif1Dec.ax]'
[08:53:44:889] InfoReader::readLine: found codec: 'sif1ds' 'sif1 alpha4  [Sif1Dec.ax]'
[08:53:44:889] InfoReader::readLine: line: 'ffamv       ffmpeg    working   Modified MJPEG, used in AMV files  [amv]'
[08:53:44:889] InfoReader::readLine: found codec: 'ffamv' 'Modified MJPEG, used in AMV files  [amv]'
[08:53:44:889] InfoReader::readLine: line: 'ffsp5x      ffmpeg    working   SP5x codec - used by Aiptek MegaCam  [sp5x]'
[08:53:44:889] InfoReader::readLine: found codec: 'ffsp5x' 'SP5x codec - used by Aiptek MegaCam  [sp5x]'
[08:53:44:889] InfoReader::readLine: line: 'sp6x        vfw       problems  SP6x codec  [sp6x_32.dll]'
[08:53:44:889] InfoReader::readLine: found codec: 'sp6x' 'SP6x codec  [sp6x_32.dll]'
[08:53:44:889] InfoReader::readLine: line: 'sp5x        vfw       working   SP5x codec - used by Aiptek MegaCam  [sp5x_32.dll]'
[08:53:44:889] InfoReader::readLine: found codec: 'sp5x' 'SP5x codec - used by Aiptek MegaCam  [sp5x_32.dll]'
[08:53:44:889] InfoReader::readLine: line: 'sp4x        vfw       working   SP4x codec - used by Aiptek MegaCam  [SP4X_32.DLL]'
[08:53:44:889] InfoReader::readLine: found codec: 'sp4x' 'SP4x codec - used by Aiptek MegaCam  [SP4X_32.DLL]'
[08:53:44:889] InfoReader::readLine: line: 'bt411       vfwex     working   Brooktree 411 codec  [btvvc32.drv]'
[08:53:44:889] InfoReader::readLine: found codec: 'bt411' 'Brooktree 411 codec  [btvvc32.drv]'
[08:53:44:889] InfoReader::readLine: line: 'bwmpeg      vfwex     working   Broadway MPEG Capture Codec  [bw10.dll]'
[08:53:44:889] InfoReader::readLine: found codec: 'bwmpeg' 'Broadway MPEG Capture Codec  [bw10.dll]'
[08:53:44:889] InfoReader::readLine: line: 'csmscreen   vfw       working   csmscreen AVI lossless video codec  [csmx.dll]'
[08:53:44:890] InfoReader::readLine: found codec: 'csmscreen' 'csmscreen AVI lossless video codec  [csmx.dll]'
[08:53:44:890] InfoReader::readLine: line: 'matchware   vfw       working   matchware screen capture codec  [mwsc.dll]'
[08:53:44:890] InfoReader::readLine: found codec: 'matchware' 'matchware screen capture codec  [mwsc.dll]'
[08:53:44:890] InfoReader::readLine: line: 'zdsoft      vfwex     working   zdsoft screen recorder  [scrvid.dll]'
[08:53:44:890] InfoReader::readLine: found codec: 'zdsoft' 'zdsoft screen recorder  [scrvid.dll]'
[08:53:44:890] InfoReader::readLine: line: 'webtrain    vfw       working   WebTrain Communication lossless screen recorder  [wtvc.dll]'
[08:53:44:890] InfoReader::readLine: found codec: 'webtrain' 'WebTrain Communication lossless screen recorder  [wtvc.dll]'
[08:53:44:890] InfoReader::readLine: line: 'ffkega      ffmpeg    working   FFmpeg Kega Video  [kgv1]'
[08:53:44:890] InfoReader::readLine: found codec: 'ffkega' 'FFmpeg Kega Video  [kgv1]'
[08:53:44:890] InfoReader::readLine: line: 'kegavideo   vfw       working   Kega Video  [KGV1-VFW.dll]'
[08:53:44:890] InfoReader::readLine: found codec: 'kegavideo' 'Kega Video  [KGV1-VFW.dll]'
[08:53:44:890] InfoReader::readLine: line: 'xfire       vfw       working   xfire video  [xfcodec.dll]'
[08:53:44:890] InfoReader::readLine: found codec: 'xfire' 'xfire video  [xfcodec.dll]'
[08:53:44:890] InfoReader::readLine: line: 'vfapi       vfwex     untested  VFAPI rgb transcode codec  [VFCodec.dll]'
[08:53:44:890] InfoReader::readLine: found codec: 'vfapi' 'VFAPI rgb transcode codec  [VFCodec.dll]'
[08:53:44:890] InfoReader::readLine: line: 'eyecon      vfw       working   nokia eti camcorder eyecon  [nub2.dll]'
[08:53:44:890] InfoReader::readLine: found codec: 'eyecon' 'nokia eti camcorder eyecon  [nub2.dll]'
[08:53:44:891] InfoReader::readLine: line: 'smsvvfw     vfw       working   WorldConnect Wavelet Video  [wv32vfw.dll]'
[08:53:44:891] InfoReader::readLine: found codec: 'smsvvfw' 'WorldConnect Wavelet Video  [wv32vfw.dll]'
[08:53:44:891] InfoReader::readLine: line: 'adv601      vfw       working   Analog Devices Wavelet Codec  [ADV601.dll]'
[08:53:44:891] InfoReader::readLine: found codec: 'adv601' 'Analog Devices Wavelet Codec  [ADV601.dll]'
[08:53:44:891] InfoReader::readLine: line: 'advwavelet  vfw       working   waveletvideo.freeservers.com  [wavelet.dll]'
[08:53:44:891] InfoReader::readLine: found codec: 'advwavelet' 'waveletvideo.freeservers.com  [wavelet.dll]'
[08:53:44:891] InfoReader::readLine: line: 'loronixwavlet vfw       untested  loronix wavelet  [wavlor.dll]'
[08:53:44:891] InfoReader::readLine: found codec: 'loronixwavlet' 'loronix wavelet  [wavlor.dll]'
[08:53:44:891] InfoReader::readLine: line: 'foxmotion   vfw       working   fox motion video  [fmcodec.dll]'
[08:53:44:891] InfoReader::readLine: found codec: 'foxmotion' 'fox motion video  [fmcodec.dll]'
[08:53:44:891] InfoReader::readLine: line: 'tridvfw     vfw       untested  tridvfw  [TRICDC32.DRV]'
[08:53:44:891] InfoReader::readLine: found codec: 'tridvfw' 'tridvfw  [TRICDC32.DRV]'
[08:53:44:891] InfoReader::readLine: line: 'vdtzvfw     vfw       working   Telegeny VDTZ  [VTZ32.DLL]'
[08:53:44:891] InfoReader::readLine: found codec: 'vdtzvfw' 'Telegeny VDTZ  [VTZ32.DLL]'
[08:53:44:891] InfoReader::readLine: line: 'vivd2       vfw       working   SoftMedia ViVD V2 codec VfW  [ViVD2.dll]'
[08:53:44:891] InfoReader::readLine: found codec: 'vivd2' 'SoftMedia ViVD V2 codec VfW  [ViVD2.dll]'
[08:53:44:891] InfoReader::readLine: line: 'winx        vfwex     working   Winnov Videum winx codec  [wnvwinx.dll]'
[08:53:44:891] InfoReader::readLine: found codec: 'winx' 'Winnov Videum winx codec  [wnvwinx.dll]'
[08:53:44:891] InfoReader::readLine: line: 'ffwnv1      ffmpeg    working   FFmpeg wnv1 codec  [wnv1]'
[08:53:44:892] InfoReader::readLine: found codec: 'ffwnv1' 'FFmpeg wnv1 codec  [wnv1]'
[08:53:44:892] InfoReader::readLine: line: 'wnv1        vfwex     working   Winnov Videum wnv1 codec  [wnvplay1.dll]'
[08:53:44:892] InfoReader::readLine: found codec: 'wnv1' 'Winnov Videum wnv1 codec  [wnvplay1.dll]'
[08:53:44:892] InfoReader::readLine: line: 'vdom        vfw       working   VDOWave codec  [vdowave.drv]'
[08:53:44:892] InfoReader::readLine: found codec: 'vdom' 'VDOWave codec  [vdowave.drv]'
[08:53:44:892] InfoReader::readLine: line: 'vdowave3    vfw       working   VDOWave 3 advanced codec  [vdo32_30.drv]'
[08:53:44:892] InfoReader::readLine: found codec: 'vdowave3' 'VDOWave 3 advanced codec  [vdo32_30.drv]'
[08:53:44:892] InfoReader::readLine: line: 'lsv         vfw       working   Vianet Lsvx Video  [lsvxdec.dll]'
[08:53:44:892] InfoReader::readLine: found codec: 'lsv' 'Vianet Lsvx Video  [lsvxdec.dll]'
[08:53:44:892] InfoReader::readLine: line: 'ffvmnc      ffmpeg    working   FFmpeg VMware video  [vmnc]'
[08:53:44:892] InfoReader::readLine: found codec: 'ffvmnc' 'FFmpeg VMware video  [vmnc]'
[08:53:44:892] InfoReader::readLine: line: 'vmnc        vfw       working   VMware video  [vmnc.dll]'
[08:53:44:892] InfoReader::readLine: found codec: 'vmnc' 'VMware video  [vmnc.dll]'
[08:53:44:892] InfoReader::readLine: line: 'ffsmkvid    ffmpeg    working   FFmpeg Smacker Video  [smackvid]'
[08:53:44:892] InfoReader::readLine: found codec: 'ffsmkvid' 'FFmpeg Smacker Video  [smackvid]'
[08:53:44:892] InfoReader::readLine: line: 'ffcavs      ffmpeg    working   Chinese AVS Video  [cavs]'
[08:53:44:892] InfoReader::readLine: found codec: 'ffcavs' 'Chinese AVS Video  [cavs]'
[08:53:44:892] InfoReader::readLine: line: 'qtdnxhd     qtvideo   working   QuickTime Avid DNxHD  [AvidAVdnCodec.qtx]'
[08:53:44:892] InfoReader::readLine: found codec: 'qtdnxhd' 'QuickTime Avid DNxHD  [AvidAVdnCodec.qtx]'
[08:53:44:893] InfoReader::readLine: line: 'ffdnxhd     ffmpeg    working   FFmpeg DNxHD  [dnxhd]'
[08:53:44:893] InfoReader::readLine: found codec: 'ffdnxhd' 'FFmpeg DNxHD  [dnxhd]'
[08:53:44:893] InfoReader::readLine: line: 'qt3ivx      qtvideo   working   win32/quicktime 3IV1 (3ivx)  [3ivx Delta 3.5.qtx]'
[08:53:44:893] InfoReader::readLine: found codec: 'qt3ivx' 'win32/quicktime 3IV1 (3ivx)  [3ivx Delta 3.5.qtx]'
[08:53:44:893] InfoReader::readLine: line: 'qtactl      qtvideo   working   Win32/QuickTime Streambox ACT-L2  [ACTLComponent.qtx]'
[08:53:44:893] InfoReader::readLine: found codec: 'qtactl' 'Win32/QuickTime Streambox ACT-L2  [ACTLComponent.qtx]'
[08:53:44:893] InfoReader::readLine: line: 'qtavui      qtvideo   working   Win32/QuickTime Avid Meridien Uncompressed  [AvidQTAVUICodec.qtx]'
[08:53:44:893] InfoReader::readLine: found codec: 'qtavui' 'Win32/QuickTime Avid Meridien Uncompressed  [AvidQTAVUICodec.qtx]'
[08:53:44:893] InfoReader::readLine: line: 'qth263      qtvideo   crashing  Win32/QuickTime H.263  [QuickTime.qts]'
[08:53:44:893] InfoReader::readLine: found codec: 'qth263' 'Win32/QuickTime H.263  [QuickTime.qts]'
[08:53:44:893] InfoReader::readLine: line: 'qtrlerpza   qtvideo   crashing  Win32/Quicktime RLE/RPZA  [QuickTime.qts]'
[08:53:44:893] InfoReader::readLine: found codec: 'qtrlerpza' 'Win32/Quicktime RLE/RPZA  [QuickTime.qts]'
[08:53:44:893] InfoReader::readLine: line: 'qtvp3       qtvideo   crashing  Win32/QuickTime VP3  [On2_VP3.qtx]'
[08:53:44:893] InfoReader::readLine: found codec: 'qtvp3' 'Win32/QuickTime VP3  [On2_VP3.qtx]'
[08:53:44:893] InfoReader::readLine: line: 'qtzygo      qtvideo   problems  win32/quicktime ZyGo  [ZyGoVideo.qtx]'
[08:53:44:893] InfoReader::readLine: found codec: 'qtzygo' 'win32/quicktime ZyGo  [ZyGoVideo.qtx]'
[08:53:44:893] InfoReader::readLine: line: 'qtbhiv      qtvideo   untested  Win32/QuickTime BeHereiVideo  [BeHereiVideo.qtx]'
[08:53:44:893] InfoReader::readLine: found codec: 'qtbhiv' 'Win32/QuickTime BeHereiVideo  [BeHereiVideo.qtx]'
[08:53:44:894] InfoReader::readLine: line: 'qtcvid      qtvideo   working   Win32/QuickTime Cinepak  [QuickTime.qts]'
[08:53:44:894] InfoReader::readLine: found codec: 'qtcvid' 'Win32/QuickTime Cinepak  [QuickTime.qts]'
[08:53:44:894] InfoReader::readLine: line: 'qtindeo     qtvideo   crashing  Win32/QuickTime Indeo  [QuickTime.qts]'
[08:53:44:894] InfoReader::readLine: found codec: 'qtindeo' 'Win32/QuickTime Indeo  [QuickTime.qts]'
[08:53:44:894] InfoReader::readLine: line: 'qtmjpeg     qtvideo   crashing  Win32/QuickTime MJPEG  [QuickTime.qts]'
[08:53:44:894] InfoReader::readLine: found codec: 'qtmjpeg' 'Win32/QuickTime MJPEG  [QuickTime.qts]'
[08:53:44:894] InfoReader::readLine: line: 'qtmpeg4     qtvideo   crashing  Win32/QuickTime MPEG-4  [QuickTime.qts]'
[08:53:44:894] InfoReader::readLine: found codec: 'qtmpeg4' 'Win32/QuickTime MPEG-4  [QuickTime.qts]'
[08:53:44:894] InfoReader::readLine: line: 'qtsvq3      qtvideo   working   Win32/QuickTime SVQ3  [QuickTimeEssentials.qtx]'
[08:53:44:894] InfoReader::readLine: found codec: 'qtsvq3' 'Win32/QuickTime SVQ3  [QuickTimeEssentials.qtx]'
[08:53:44:894] InfoReader::readLine: line: 'qtsvq1      qtvideo   problems  Win32/QuickTime SVQ1  [QuickTime.qts]'
[08:53:44:894] InfoReader::readLine: found codec: 'qtsvq1' 'Win32/QuickTime SVQ1  [QuickTime.qts]'
[08:53:44:894] InfoReader::readLine: line: 'ffv210      ffmpeg    untested  FFmpeg V210 - 10-bit  [v210]'
[08:53:44:894] InfoReader::readLine: found codec: 'ffv210' 'FFmpeg V210 - 10-bit  [v210]'
[08:53:44:895] InfoReader::readLine: line: 'qtcine      qtvideo   working   cinewave uncompressed 10-bit codec  [CineWave.qtx]'
[08:53:44:895] InfoReader::readLine: found codec: 'qtcine' 'cinewave uncompressed 10-bit codec  [CineWave.qtx]'
[08:53:44:895] InfoReader::readLine: line: 'qtaic       qtvideo   untested  QuickTime AIC video decoder  [QuickTime.qts]'
[08:53:44:895] InfoReader::readLine: found codec: 'qtaic' 'QuickTime AIC video decoder  [QuickTime.qts]'
[08:53:44:895] InfoReader::readLine: line: 'ffprores    ffmpeg    working   Libav ProRes  [prores]'
[08:53:44:895] InfoReader::readLine: found codec: 'ffprores' 'Libav ProRes  [prores]'
[08:53:44:895] InfoReader::readLine: line: 'qtprores    qtvideo   working   Apple ProRes 422 (HQ) decoder  [AppleProResDecoder.qtx]'
[08:53:44:895] InfoReader::readLine: found codec: 'qtprores' 'Apple ProRes 422 (HQ) decoder  [AppleProResDecoder.qtx]'
[08:53:44:895] InfoReader::readLine: line: 'vsslight    vfw       working   VSS Codec Light  [vsslight.dll]'
[08:53:44:895] InfoReader::readLine: found codec: 'vsslight' 'VSS Codec Light  [vsslight.dll]'
[08:53:44:895] InfoReader::readLine: line: 'vssh264     dshow     working   VSS H.264 New  [vsshdsd.dll]'
[08:53:44:895] InfoReader::readLine: found codec: 'vssh264' 'VSS H.264 New  [vsshdsd.dll]'
[08:53:44:895] InfoReader::readLine: line: 'vssh264old  vfw       working   VSS H.264 Old  [vssh264.dll]'
[08:53:44:895] InfoReader::readLine: found codec: 'vssh264old' 'VSS H.264 Old  [vssh264.dll]'
[08:53:44:895] InfoReader::readLine: line: 'vsswlt      vfw       working   VSS Wavelet Video Codec  [vsswlt.dll]'
[08:53:44:896] InfoReader::readLine: found codec: 'vsswlt' 'VSS Wavelet Video Codec  [vsswlt.dll]'
[08:53:44:896] InfoReader::readLine: line: 'zlib        vfw       working   AVIzlib  [avizlib.dll]'
[08:53:44:896] InfoReader::readLine: found codec: 'zlib' 'AVIzlib  [avizlib.dll]'
[08:53:44:896] InfoReader::readLine: line: 'mszh        vfw       working   AVImszh  [avimszh.dll]'
[08:53:44:896] InfoReader::readLine: found codec: 'mszh' 'AVImszh  [avimszh.dll]'
[08:53:44:896] InfoReader::readLine: line: 'alaris      vfwex     working   Alaris VideoGramPiX  [vgpix32d.dll]'
[08:53:44:896] InfoReader::readLine: found codec: 'alaris' 'Alaris VideoGramPiX  [vgpix32d.dll]'
[08:53:44:896] InfoReader::readLine: line: 'vcr1        vfw       crashing  ATI VCR-1  [ativcr1.dll]'
[08:53:44:896] InfoReader::readLine: found codec: 'vcr1' 'ATI VCR-1  [ativcr1.dll]'
[08:53:44:896] InfoReader::readLine: line: 'pim1        vfw       crashing  Pinnacle Hardware MPEG-1  [pclepim1.dll]'
[08:53:44:896] InfoReader::readLine: found codec: 'pim1' 'Pinnacle Hardware MPEG-1  [pclepim1.dll]'
[08:53:44:896] InfoReader::readLine: line: 'qpeg        vfw       working   Q-Team's QPEG (www.q-team.de)  [qpeg32.dll]'
[08:53:44:896] InfoReader::readLine: found codec: 'qpeg' 'Q-Team's QPEG (www.q-team.de)  [qpeg32.dll]'
[08:53:44:896] InfoReader::readLine: line: 'rricm       vfw       crashing  rricm  [rricm.dll]'
[08:53:44:896] InfoReader::readLine: found codec: 'rricm' 'rricm  [rricm.dll]'
[08:53:44:896] InfoReader::readLine: line: 'ffcamtasia  ffmpeg    working   FFmpeg TechSmith Camtasia Screen Codec  [camtasia]'
[08:53:44:897] InfoReader::readLine: found codec: 'ffcamtasia' 'FFmpeg TechSmith Camtasia Screen Codec  [camtasia]'
[08:53:44:897] InfoReader::readLine: line: 'camtasia    vfw       working   TechSmith Camtasia Screen Codec  [tsccvid.dll]'
[08:53:44:897] InfoReader::readLine: found codec: 'camtasia' 'TechSmith Camtasia Screen Codec  [tsccvid.dll]'
[08:53:44:897] InfoReader::readLine: line: 'ffcamstudio ffmpeg    working   CamStudio Screen Codec  [camstudio]'
[08:53:44:897] InfoReader::readLine: found codec: 'ffcamstudio' 'CamStudio Screen Codec  [camstudio]'
[08:53:44:897] InfoReader::readLine: line: 'fraps       vfw       working   FRAPS: Realtime Video Capture  [frapsvid.dll]'
[08:53:44:897] InfoReader::readLine: found codec: 'fraps' 'FRAPS: Realtime Video Capture  [frapsvid.dll]'
[08:53:44:897] InfoReader::readLine: line: 'fffraps     ffmpeg    working   FFmpeg Fraps  [fraps]'
[08:53:44:897] InfoReader::readLine: found codec: 'fffraps' 'FFmpeg Fraps  [fraps]'
[08:53:44:897] InfoReader::readLine: line: 'ffjv        ffmpeg    working   FFmpeg Bitmap Brothers JV  [jv]'
[08:53:44:897] InfoReader::readLine: found codec: 'ffjv' 'FFmpeg Bitmap Brothers JV  [jv]'
[08:53:44:897] InfoReader::readLine: line: 'fftiertexseq ffmpeg    working   FFmpeg Tiertex SEQ  [tiertexseqvideo]'
[08:53:44:897] InfoReader::readLine: found codec: 'fftiertexseq' 'FFmpeg Tiertex SEQ  [tiertexseqvideo]'
[08:53:44:897] InfoReader::readLine: line: 'ffvmd       ffmpeg    working   FFmpeg Sierra VMD video  [vmdvideo]'
[08:53:44:897] InfoReader::readLine: found codec: 'ffvmd' 'FFmpeg Sierra VMD video  [vmdvideo]'
[08:53:44:898] InfoReader::readLine: line: 'ffdxa       ffmpeg    working   FFmpeg Feeble Files DXA video  [dxa]'
[08:53:44:898] InfoReader::readLine: found codec: 'ffdxa' 'FFmpeg Feeble Files DXA video  [dxa]'
[08:53:44:898] InfoReader::readLine: line: 'ffdsicinvideo ffmpeg    working   FFmpeg Delphine CIN video  [dsicinvideo]'
[08:53:44:898] InfoReader::readLine: found codec: 'ffdsicinvideo' 'FFmpeg Delphine CIN video  [dsicinvideo]'
[08:53:44:898] InfoReader::readLine: line: 'ffthp       ffmpeg    working   FFmpeg THP video  [thp]'
[08:53:44:898] InfoReader::readLine: found codec: 'ffthp' 'FFmpeg THP video  [thp]'
[08:53:44:898] InfoReader::readLine: line: 'ffbfi       ffmpeg    working   FFmpeg BFI Video  [bfi]'
[08:53:44:898] InfoReader::readLine: found codec: 'ffbfi' 'FFmpeg BFI Video  [bfi]'
[08:53:44:898] InfoReader::readLine: line: 'ffbethsoftvid ffmpeg    problems  FFmpeg Bethesda Software VID  [bethsoftvid]'
[08:53:44:898] InfoReader::readLine: found codec: 'ffbethsoftvid' 'FFmpeg Bethesda Software VID  [bethsoftvid]'
[08:53:44:898] InfoReader::readLine: line: 'ffrl2       ffmpeg    working   FFmpeg RL2  [rl2]'
[08:53:44:898] InfoReader::readLine: found codec: 'ffrl2' 'FFmpeg RL2  [rl2]'
[08:53:44:898] InfoReader::readLine: line: 'fftxd       ffmpeg    working   FFmpeg Renderware TeXture Dictionary  [txd]'
[08:53:44:898] InfoReader::readLine: found codec: 'fftxd' 'FFmpeg Renderware TeXture Dictionary  [txd]'
[08:53:44:898] InfoReader::readLine: line: 'xan         vfw       working   XAN Video  [xanlib.dll]'
[08:53:44:898] InfoReader::readLine: found codec: 'xan' 'XAN Video  [xanlib.dll]'
[08:53:44:899] InfoReader::readLine: line: 'ffwc4       ffmpeg    working   FFmpeg XAN wc4  [xan_wc4]'
[08:53:44:899] InfoReader::readLine: found codec: 'ffwc4' 'FFmpeg XAN wc4  [xan_wc4]'
[08:53:44:899] InfoReader::readLine: line: 'ffwc3       ffmpeg    problems  FFmpeg XAN wc3  [xan_wc3]'
[08:53:44:899] InfoReader::readLine: found codec: 'ffwc3' 'FFmpeg XAN wc3  [xan_wc3]'
[08:53:44:899] InfoReader::readLine: line: 'ffidcin     ffmpeg    problems  FFmpeg Id CIN video  [idcinvideo]'
[08:53:44:899] InfoReader::readLine: found codec: 'ffidcin' 'FFmpeg Id CIN video  [idcinvideo]'
[08:53:44:899] InfoReader::readLine: line: 'ffinterplay ffmpeg    problems  FFmpeg Interplay Video  [interplayvideo]'
[08:53:44:899] InfoReader::readLine: found codec: 'ffinterplay' 'FFmpeg Interplay Video  [interplayvideo]'
[08:53:44:899] InfoReader::readLine: line: 'ffvqa       ffmpeg    problems  FFmpeg VQA Video  [vqavideo]'
[08:53:44:899] InfoReader::readLine: found codec: 'ffvqa' 'FFmpeg VQA Video  [vqavideo]'
[08:53:44:899] InfoReader::readLine: line: 'ffc93       ffmpeg    problems  FFmpeg C93 Video  [c93]'
[08:53:44:899] InfoReader::readLine: found codec: 'ffc93' 'FFmpeg C93 Video  [c93]'
[08:53:44:899] InfoReader::readLine: line: 'ffeatgv     ffmpeg    working   FFmpeg Electronic Arts TGV  [eatgv]'
[08:53:44:899] InfoReader::readLine: found codec: 'ffeatgv' 'FFmpeg Electronic Arts TGV  [eatgv]'
[08:53:44:899] InfoReader::readLine: line: 'rawrgb32    raw       working   RAW RGB32'
[08:53:44:899] InfoReader::readLine: found codec: 'rawrgb32' 'RAW RGB32'
[08:53:44:899] InfoReader::readLine: line: 'rawrgb24    raw       working   RAW RGB24'
[08:53:44:900] InfoReader::readLine: found codec: 'rawrgb24' 'RAW RGB24'
[08:53:44:900] InfoReader::readLine: line: 'rawrgb16    raw       working   RAW RGB16'
[08:53:44:900] InfoReader::readLine: found codec: 'rawrgb16' 'RAW RGB16'
[08:53:44:900] InfoReader::readLine: line: 'rawbgr32flip raw       working   RAW BGR32'
[08:53:44:900] InfoReader::readLine: found codec: 'rawbgr32flip' 'RAW BGR32'
[08:53:44:900] InfoReader::readLine: line: 'rawbgr32    raw       working   RAW BGR32'
[08:53:44:900] InfoReader::readLine: found codec: 'rawbgr32' 'RAW BGR32'
[08:53:44:900] InfoReader::readLine: line: 'rawbgr24flip raw       working   RAW BGR24'
[08:53:44:900] InfoReader::readLine: found codec: 'rawbgr24flip' 'RAW BGR24'
[08:53:44:900] InfoReader::readLine: line: 'rawbgr24    raw       working   RAW BGR24'
[08:53:44:900] InfoReader::readLine: found codec: 'rawbgr24' 'RAW BGR24'
[08:53:44:900] InfoReader::readLine: line: 'rawbgr16flip raw       working   RAW BGR15'
[08:53:44:900] InfoReader::readLine: found codec: 'rawbgr16flip' 'RAW BGR15'
[08:53:44:900] InfoReader::readLine: line: 'rawbgr16    raw       working   RAW BGR15'
[08:53:44:900] InfoReader::readLine: found codec: 'rawbgr16' 'RAW BGR15'
[08:53:44:900] InfoReader::readLine: line: 'rawbgr15flip raw       working   RAW BGR15'
[08:53:44:900] InfoReader::readLine: found codec: 'rawbgr15flip' 'RAW BGR15'
[08:53:44:900] InfoReader::readLine: line: 'rawbgr15    raw       working   RAW BGR15'
[08:53:44:901] InfoReader::readLine: found codec: 'rawbgr15' 'RAW BGR15'
[08:53:44:901] InfoReader::readLine: line: 'rawbgr8flip raw       working   RAW BGR8'
[08:53:44:901] InfoReader::readLine: found codec: 'rawbgr8flip' 'RAW BGR8'
[08:53:44:901] InfoReader::readLine: line: 'rawbgr8     raw       working   RAW BGR8'
[08:53:44:901] InfoReader::readLine: found codec: 'rawbgr8' 'RAW BGR8'
[08:53:44:901] InfoReader::readLine: line: 'rawbgr1     raw       working   RAW BGR1'
[08:53:44:901] InfoReader::readLine: found codec: 'rawbgr1' 'RAW BGR1'
[08:53:44:901] InfoReader::readLine: line: 'rawyuy2     raw       working   RAW YUY2'
[08:53:44:901] InfoReader::readLine: found codec: 'rawyuy2' 'RAW YUY2'
[08:53:44:901] InfoReader::readLine: line: 'rawyuv2     raw       working   RAW YUV2'
[08:53:44:901] InfoReader::readLine: found codec: 'rawyuv2' 'RAW YUV2'
[08:53:44:901] InfoReader::readLine: line: 'rawuyvy     raw       working   RAW UYVY'
[08:53:44:901] InfoReader::readLine: found codec: 'rawuyvy' 'RAW UYVY'
[08:53:44:901] InfoReader::readLine: line: 'raw444P     raw       working   RAW 444P'
[08:53:44:901] InfoReader::readLine: found codec: 'raw444P' 'RAW 444P'
[08:53:44:901] InfoReader::readLine: line: 'raw422P     raw       working   RAW 422P'
[08:53:44:901] InfoReader::readLine: found codec: 'raw422P' 'RAW 422P'
[08:53:44:901] InfoReader::readLine: line: 'rawyv12     raw       working   RAW YV12'
[08:53:44:902] InfoReader::readLine: found codec: 'rawyv12' 'RAW YV12'
[08:53:44:902] InfoReader::readLine: line: 'rawnv21     raw       working   RAW NV21'
[08:53:44:902] InfoReader::readLine: found codec: 'rawnv21' 'RAW NV21'
[08:53:44:902] InfoReader::readLine: line: 'rawnv12     raw       working   RAW NV12'
[08:53:44:902] InfoReader::readLine: found codec: 'rawnv12' 'RAW NV12'
[08:53:44:902] InfoReader::readLine: line: 'rawhm12     hmblck    working   RAW HM12'
[08:53:44:902] InfoReader::readLine: found codec: 'rawhm12' 'RAW HM12'
[08:53:44:902] InfoReader::readLine: line: 'rawi420     raw       working   RAW I420'
[08:53:44:902] InfoReader::readLine: found codec: 'rawi420' 'RAW I420'
[08:53:44:902] InfoReader::readLine: line: 'rawyvu9     raw       working   RAW YVU9'
[08:53:44:902] InfoReader::readLine: found codec: 'rawyvu9' 'RAW YVU9'
[08:53:44:902] InfoReader::readLine: line: 'rawy800     raw       working   RAW Y8/Y800'
[08:53:44:902] InfoReader::readLine: found codec: 'rawy800' 'RAW Y8/Y800'
[08:53:44:902] InfoReader::readLine: line: 'ffrawyuy2   ffmpeg    working   RAW YUY2  [rawvideo]'
[08:53:44:902] InfoReader::readLine: found codec: 'ffrawyuy2' 'RAW YUY2  [rawvideo]'
[08:53:44:902] InfoReader::readLine: line: 'ffrawyuv2   ffmpeg    working   RAW YUV2  [rawvideo]'
[08:53:44:902] InfoReader::readLine: found codec: 'ffrawyuv2' 'RAW YUV2  [rawvideo]'
[08:53:44:902] InfoReader::readLine: line: 'ffrawuyvy   ffmpeg    working   RAW UYVY  [rawvideo]'
[08:53:44:903] InfoReader::readLine: found codec: 'ffrawuyvy' 'RAW UYVY  [rawvideo]'
[08:53:44:903] InfoReader::readLine: line: 'ffraw444P   ffmpeg    working   RAW 444P  [rawvideo]'
[08:53:44:903] InfoReader::readLine: found codec: 'ffraw444P' 'RAW 444P  [rawvideo]'
[08:53:44:903] InfoReader::readLine: line: 'ffraw422P   ffmpeg    working   RAW 422P  [rawvideo]'
[08:53:44:903] InfoReader::readLine: found codec: 'ffraw422P' 'RAW 422P  [rawvideo]'
[08:53:44:903] InfoReader::readLine: line: 'ffrawyv12   ffmpeg    working   RAW YV12  [rawvideo]'
[08:53:44:903] InfoReader::readLine: found codec: 'ffrawyv12' 'RAW YV12  [rawvideo]'
[08:53:44:903] InfoReader::readLine: line: 'ffrawi420   ffmpeg    working   RAW I420  [rawvideo]'
[08:53:44:903] InfoReader::readLine: found codec: 'ffrawi420' 'RAW I420  [rawvideo]'
[08:53:44:903] InfoReader::readLine: line: 'ffrawyvu9   ffmpeg    working   RAW YVU9  [rawvideo]'
[08:53:44:903] InfoReader::readLine: found codec: 'ffrawyvu9' 'RAW YVU9  [rawvideo]'
[08:53:44:903] InfoReader::readLine: line: 'ffrawy800   ffmpeg    working   RAW Y8/Y800  [rawvideo]'
[08:53:44:903] InfoReader::readLine: found codec: 'ffrawy800' 'RAW Y8/Y800  [rawvideo]'
[08:53:44:903] InfoReader::readLine: line: 'null        null      crashing  NULL codec (no decoding!)'
[08:53:44:903] InfoReader::readLine: found codec: 'null' 'NULL codec (no decoding!)'
[08:53:44:903] InfoReader::readLine: line: 'Available demuxers:'
[08:53:44:904] WARNING: InfoReader::readLine: can't parse codec from line 'Available demuxers:'
[08:53:44:904] InfoReader::readLine: line: ' demuxer:   info:  (comment)'
[08:53:44:904] WARNING: InfoReader::readLine: can't parse codec from line ' demuxer:   info:  (comment)'
[08:53:44:904] InfoReader::readLine: line: 'ID_DEMUXERS'
[08:53:44:904] WARNING: InfoReader::readLine: can't parse codec from line 'ID_DEMUXERS'
[08:53:44:904] InfoReader::readLine: found key: demuxer
[08:53:44:904] InfoReader::readLine: line: '       edl  EDL file demuxer'
[08:53:44:904] InfoReader::readLine: found demuxer: 'edl' 'EDL file demuxer'
[08:53:44:904] InfoReader::readLine: line: '  rawaudio  Raw audio demuxer'
[08:53:44:904] InfoReader::readLine: found demuxer: 'rawaudio' 'Raw audio demuxer'
[08:53:44:904] InfoReader::readLine: line: '  rawvideo  Raw video demuxer'
[08:53:44:904] InfoReader::readLine: found demuxer: 'rawvideo' 'Raw video demuxer'
[08:53:44:904] InfoReader::readLine: line: '        tv  Tv card demuxer (?)'
[08:53:44:904] InfoReader::readLine: found demuxer: 'tv' 'Tv card demuxer (?)'
[08:53:44:904] InfoReader::readLine: line: '        mf  mf demuxer (multiframe?, pictures demuxer)'
[08:53:44:904] InfoReader::readLine: found demuxer: 'mf' 'mf demuxer (multiframe?, pictures demuxer)'
[08:53:44:904] InfoReader::readLine: line: '  lavfpref  libavformat preferred demuxer (supports many formats, requires libavformat)'
[08:53:44:905] InfoReader::readLine: found demuxer: 'lavfpref' 'libavformat preferred demuxer (supports many formats, requires libavformat)'
[08:53:44:905] InfoReader::readLine: line: '       avi  AVI demuxer (AVI files, including non interleaved files)'
[08:53:44:905] InfoReader::readLine: found demuxer: 'avi' 'AVI demuxer (AVI files, including non interleaved files)'
[08:53:44:905] InfoReader::readLine: line: '       y4m  YUV4MPEG2 demuxer'
[08:53:44:905] InfoReader::readLine: found demuxer: 'y4m' 'YUV4MPEG2 demuxer'
[08:53:44:905] InfoReader::readLine: line: '       asf  ASF demuxer (ASF, WMV, WMA)'
[08:53:44:905] InfoReader::readLine: found demuxer: 'asf' 'ASF demuxer (ASF, WMV, WMA)'
[08:53:44:905] InfoReader::readLine: line: '       nsv  NullsoftVideo demuxer (nsv and nsa streaming files)'
[08:53:44:905] InfoReader::readLine: found demuxer: 'nsv' 'NullsoftVideo demuxer (nsv and nsa streaming files)'
[08:53:44:905] InfoReader::readLine: line: '      real  Realmedia demuxer (handles new .RMF files)'
[08:53:44:905] InfoReader::readLine: found demuxer: 'real' 'Realmedia demuxer (handles new .RMF files)'
[08:53:44:905] InfoReader::readLine: line: '    smjpeg  smjpeg demuxer'
[08:53:44:905] InfoReader::readLine: found demuxer: 'smjpeg' 'smjpeg demuxer'
[08:53:44:905] InfoReader::readLine: line: '       mkv  Matroska demuxer'
[08:53:44:905] InfoReader::readLine: found demuxer: 'mkv' 'Matroska demuxer'
[08:53:44:905] InfoReader::readLine: line: ' realaudio  Realaudio demuxer (handles old audio only .ra files)'
[08:53:44:906] InfoReader::readLine: found demuxer: 'realaudio' 'Realaudio demuxer (handles old audio only .ra files)'
[08:53:44:906] InfoReader::readLine: line: '       vqf  TwinVQ demuxer (ported from MPlayerXP)'
[08:53:44:906] InfoReader::readLine: found demuxer: 'vqf' 'TwinVQ demuxer (ported from MPlayerXP)'
[08:53:44:906] InfoReader::readLine: line: '       mov  Quicktime/MP4 demuxer (Handles Quicktime, MP4, 3GP)'
[08:53:44:906] InfoReader::readLine: found demuxer: 'mov' 'Quicktime/MP4 demuxer (Handles Quicktime, MP4, 3GP)'
[08:53:44:906] InfoReader::readLine: line: '      vivo  Vivo demuxer'
[08:53:44:906] InfoReader::readLine: found demuxer: 'vivo' 'Vivo demuxer'
[08:53:44:906] InfoReader::readLine: line: '       fli  Autodesk FLIC demuxer (Supports also some extensions)'
[08:53:44:906] InfoReader::readLine: found demuxer: 'fli' 'Autodesk FLIC demuxer (Supports also some extensions)'
[08:53:44:906] InfoReader::readLine: line: '      film  FILM/CPK demuxer for Sega Saturn CD-ROM games'
[08:53:44:906] InfoReader::readLine: found demuxer: 'film' 'FILM/CPK demuxer for Sega Saturn CD-ROM games'
[08:53:44:906] InfoReader::readLine: line: '       roq  RoQ demuxer'
[08:53:44:906] InfoReader::readLine: found demuxer: 'roq' 'RoQ demuxer'
[08:53:44:906] InfoReader::readLine: line: '       gif  GIF demuxer'
[08:53:44:906] InfoReader::readLine: found demuxer: 'gif' 'GIF demuxer'
[08:53:44:906] InfoReader::readLine: line: '       ogg  Ogg demuxer'
[08:53:44:906] InfoReader::readLine: found demuxer: 'ogg' 'Ogg demuxer'
[08:53:44:907] InfoReader::readLine: line: '       pva  PVA demuxer (streams from DVB cards)'
[08:53:44:907] InfoReader::readLine: found demuxer: 'pva' 'PVA demuxer (streams from DVB cards)'
[08:53:44:907] InfoReader::readLine: line: '    mpegts  MPEG-TS demuxer'
[08:53:44:907] InfoReader::readLine: found demuxer: 'mpegts' 'MPEG-TS demuxer'
[08:53:44:907] InfoReader::readLine: line: '     lmlm4  LMLM4 MPEG4 Compression Card stream demuxer'
[08:53:44:907] InfoReader::readLine: found demuxer: 'lmlm4' 'LMLM4 MPEG4 Compression Card stream demuxer'
[08:53:44:907] InfoReader::readLine: line: '    mpegps  MPEG PS demuxer (Mpeg)'
[08:53:44:907] InfoReader::readLine: found demuxer: 'mpegps' 'MPEG PS demuxer (Mpeg)'
[08:53:44:907] InfoReader::readLine: line: '   mpegpes  MPEG PES demuxer (Mpeg)'
[08:53:44:907] InfoReader::readLine: found demuxer: 'mpegpes' 'MPEG PES demuxer (Mpeg)'
[08:53:44:907] InfoReader::readLine: line: '    mpeges  MPEG ES demuxer (Mpeg)'
[08:53:44:907] InfoReader::readLine: found demuxer: 'mpeges' 'MPEG ES demuxer (Mpeg)'
[08:53:44:907] InfoReader::readLine: line: '   mpeggxf  MPEG ES in GXF demuxer (Mpeg)'
[08:53:44:907] InfoReader::readLine: found demuxer: 'mpeggxf' 'MPEG ES in GXF demuxer (Mpeg)'
[08:53:44:907] InfoReader::readLine: line: '   mpeg4es  MPEG4 ES demuxer (Mpeg)'
[08:53:44:907] InfoReader::readLine: found demuxer: 'mpeg4es' 'MPEG4 ES demuxer (Mpeg)'
[08:53:44:907] InfoReader::readLine: line: '    h264es  H.264 ES demuxer (Mpeg)'
[08:53:44:907] InfoReader::readLine: found demuxer: 'h264es' 'H.264 ES demuxer (Mpeg)'
[08:53:44:908] InfoReader::readLine: line: '     audio  Audio demuxer (Audio only files)'
[08:53:44:908] InfoReader::readLine: found demuxer: 'audio' 'Audio demuxer (Audio only files)'
[08:53:44:908] InfoReader::readLine: line: '      tivo  TiVo demuxer (Demux streams from TiVo)'
[08:53:44:908] InfoReader::readLine: found demuxer: 'tivo' 'TiVo demuxer (Demux streams from TiVo)'
[08:53:44:908] InfoReader::readLine: line: '      lavf  libavformat demuxer (supports many formats, requires libavformat)'
[08:53:44:908] InfoReader::readLine: found demuxer: 'lavf' 'libavformat demuxer (supports many formats, requires libavformat)'
[08:53:44:908] InfoReader::readLine: line: '     rawdv  Raw DV demuxer'
[08:53:44:908] InfoReader::readLine: found demuxer: 'rawdv' 'Raw DV demuxer'
[08:53:44:908] InfoReader::readLine: line: '       aac  AAC demuxer (Raw AAC files )'
[08:53:44:908] InfoReader::readLine: found demuxer: 'aac' 'AAC demuxer (Raw AAC files )'
[08:53:44:908] InfoReader::readLine: line: 'ID_EXIT=NONE'
[08:53:44:908] WARNING: InfoReader::readLine: can't parse demuxer from line 'ID_EXIT=NONE'
[08:53:44:908] DeviceInfo::alsaDevices
[08:53:44:924] DeviceInfo::alsaDevices: '**** List of PLAYBACK Hardware Devices ****
'
[08:53:44:925] DeviceInfo::alsaDevices: 'card 0: Intel [HDA Intel], device 0: AD1986A Analog [AD1986A Analog]
'
[08:53:44:925] DeviceInfo::alsaDevices: found device: '0.0' 'HDA Intel'
[08:53:44:925] DeviceInfo::alsaDevices: '  Subdevices: 0/1
'
[08:53:44:925] DeviceInfo::alsaDevices: '  Subdevice #0: subdevice #0
'
[08:53:44:925] DeviceInfo::xvAdaptors
[08:53:44:936] DeviceInfo::xvAdaptors: 'X-Video Extension version 2.2
'
[08:53:44:936] DeviceInfo::xvAdaptors: 'screen #0
'
[08:53:44:936] DeviceInfo::xvAdaptors: '  Adaptor #0: "NV17 Video Texture"
'
[08:53:44:936] DeviceInfo::xvAdaptors: found adaptor: '0' 'NV17 Video Texture'
[08:53:44:936] DeviceInfo::xvAdaptors: '    number of ports: 32
'
[08:53:44:936] DeviceInfo::xvAdaptors: '    port base: 550
'
[08:53:44:936] DeviceInfo::xvAdaptors: '    operations supported: PutImage 
'
[08:53:44:936] DeviceInfo::xvAdaptors: '    supported visuals:
'
[08:53:44:936] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x21
'
[08:53:44:936] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x24
'
[08:53:44:936] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x25
'
[08:53:44:936] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x26
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x27
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x28
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x29
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x2a
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x2b
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x2c
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x2d
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x2e
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x2f
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x30
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x31
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x32
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x33
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x34
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x35
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x36
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x37
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x38
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x39
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x3a
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x3b
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x3c
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x3d
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x3e
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x3f
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x40
'
[08:53:44:937] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x41
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x42
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x43
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x44
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x45
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x46
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x47
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x48
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x49
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x4a
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x4b
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x4c
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x4d
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x4e
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x4f
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x50
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x51
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x52
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x53
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x54
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x55
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x56
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x57
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x58
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x59
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x5a
'
[08:53:44:938] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x5b
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x5c
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x5d
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x5e
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x5f
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x60
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x61
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x62
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x63
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x64
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x65
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x66
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x22
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x67
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x68
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x69
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x6a
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x6b
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x6c
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x6d
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x6e
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x6f
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x70
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x71
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x72
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x73
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x74
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x75
'
[08:53:44:939] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x76
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x77
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x78
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x79
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x7a
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x7b
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x7c
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x7d
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x7e
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x7f
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x80
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x81
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x82
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x83
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x84
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x85
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x86
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x87
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x88
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x89
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x8a
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x8b
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x8c
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x8d
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x8e
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x8f
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x90
'
[08:53:44:940] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x91
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x92
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x93
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x94
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x95
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x96
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x97
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x98
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x99
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x9a
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x9b
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x9c
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x9d
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x9e
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0x9f
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0xa0
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0xa1
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0xa2
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0xa3
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0xa4
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0xa5
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0xa6
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0xa7
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0xa8
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      depth 24, visualID 0xa9
'
[08:53:44:941] DeviceInfo::xvAdaptors: '    number of attributes: 7
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      "XV_SET_DEFAULTS" (range 0 to 0)
'
[08:53:44:941] DeviceInfo::xvAdaptors: '              client settable attribute
'
[08:53:44:941] DeviceInfo::xvAdaptors: '      "XV_ITURBT_709" (range 0 to 1)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '              client settable attribute
'
[08:53:44:942] DeviceInfo::xvAdaptors: '              client gettable attribute (current value is 0)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '      "XV_SYNC_TO_VBLANK" (range 0 to 1)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '              client settable attribute
'
[08:53:44:942] DeviceInfo::xvAdaptors: '              client gettable attribute (current value is 1)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '      "XV_BRIGHTNESS" (range -1000 to 1000)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '              client settable attribute
'
[08:53:44:942] DeviceInfo::xvAdaptors: '              client gettable attribute (current value is 0)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '      "XV_CONTRAST" (range -1000 to 1000)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '              client settable attribute
'
[08:53:44:942] DeviceInfo::xvAdaptors: '              client gettable attribute (current value is 0)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '      "XV_SATURATION" (range -1000 to 1000)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '              client settable attribute
'
[08:53:44:942] DeviceInfo::xvAdaptors: '              client gettable attribute (current value is 0)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '      "XV_HUE" (range -1000 to 1000)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '              client settable attribute
'
[08:53:44:942] DeviceInfo::xvAdaptors: '              client gettable attribute (current value is 0)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '    maximum XvImage size: 8192 x 8192
'
[08:53:44:942] DeviceInfo::xvAdaptors: '    Number of image formats: 4
'
[08:53:44:942] DeviceInfo::xvAdaptors: '      id: 0x32595559 (YUY2)
'
[08:53:44:942] DeviceInfo::xvAdaptors: '        guid: 59555932-0000-0010-8000-00aa00389b71
'
[08:53:44:942] DeviceInfo::xvAdaptors: '        bits per pixel: 16
'
[08:53:44:942] DeviceInfo::xvAdaptors: '        number of planes: 1
'
[08:53:44:942] DeviceInfo::xvAdaptors: '        type: YUV (packed)
'
[08:53:44:943] DeviceInfo::xvAdaptors: '      id: 0x32315659 (YV12)
'
[08:53:44:943] DeviceInfo::xvAdaptors: '        guid: 59563132-0000-0010-8000-00aa00389b71
'
[08:53:44:943] DeviceInfo::xvAdaptors: '        bits per pixel: 12
'
[08:53:44:943] DeviceInfo::xvAdaptors: '        number of planes: 3
'
[08:53:44:943] DeviceInfo::xvAdaptors: '        type: YUV (planar)
'
[08:53:44:943] DeviceInfo::xvAdaptors: '      id: 0x59565955 (UYVY)
'
[08:53:44:943] DeviceInfo::xvAdaptors: '        guid: 55595659-0000-0010-8000-00aa00389b71
'
[08:53:44:943] DeviceInfo::xvAdaptors: '        bits per pixel: 16
'
[08:53:44:943] DeviceInfo::xvAdaptors: '        number of planes: 1
'
[08:53:44:943] DeviceInfo::xvAdaptors: '        type: YUV (packed)
'
[08:53:44:943] DeviceInfo::xvAdaptors: '      id: 0x30323449 (I420)
'
[08:53:44:943] DeviceInfo::xvAdaptors: '        guid: 49343230-0000-0010-8000-00aa00389b71
'
[08:53:44:943] DeviceInfo::xvAdaptors: '        bits per pixel: 12
'
[08:53:44:943] DeviceInfo::xvAdaptors: '        number of planes: 3
'
[08:53:44:943] DeviceInfo::xvAdaptors: '        type: YUV (planar)
'
[08:53:44:945] PrefGeneral::vo_combo_changed: 0
[08:53:44:945] PrefGeneral::ao_combo_changed: 0
[08:53:44:945] PrefGeneral::vo_combo_changed: -1
[08:53:44:945] PrefGeneral::ao_combo_changed: -1
[08:53:44:973] PrefDrives::updateDriveCombos: detect_cd_devices: 0
[08:53:44:976] PrefDrives::PrefDrives: device found: '/dev/cdrom'
[08:53:44:976] PrefDrives::PrefDrives: device found: '/dev/dvd'
[08:53:44:976] PrefDrives::PrefDrives: device found: '/dev/sr0'
[08:53:45:006] icon_dir: /home/offir/.config/smplayer/themes
[08:53:45:006] icon_dir: /usr/share/smplayer/themes
[08:53:45:034] PrefGeneral::vo_combo_changed: 1
[08:53:45:034] PrefGeneral::vo_combo_changed: 1
[08:53:45:034] PrefGeneral::ao_combo_changed: 0
[08:53:45:035] PrefGeneral::ao_combo_changed: 0
[08:53:45:041] PrefSubtitles:on_freetype_check_toggled: 1
[08:53:45:041] SelectColorButton::setColor: current style name: gtk+
[08:53:45:042] SelectColorButton::setColor: current style name: gtk+
[08:53:45:042] SelectColorButton::setColor: current style name: gtk+
[08:54:14:038] DefaultGui::applyNewPreferences
[08:54:14:038] BaseGui::applyNewPreferences
[08:54:14:038] AssStyles::exportStyles: filename: /home/offir/.config/smplayer/styles.ass
[08:54:14:039] PrefAdvanced::colorKey: color: 20202
[08:54:14:041] DefaultGui::updateWidgets
[08:54:14:041] BaseGui::updateWidgets
[08:54:14:041] ActionsEditor::applyChanges
[08:54:14:045] BaseGui::saveActions
[08:54:14:046] ActionsEditor::saveToConfig
[08:54:14:047] Preferences::save
[08:54:14:048] AssStyles::save
[08:54:22:573] DefaultGui::applyNewPreferences
[08:54:22:573] BaseGui::applyNewPreferences
[08:54:22:574] AssStyles::exportStyles: filename: /home/offir/.config/smplayer/styles.ass
[08:54:22:574] PrefAdvanced::colorKey: color: 20202
[08:54:22:574] DefaultGui::updateWidgets
[08:54:22:574] BaseGui::updateWidgets
[08:54:22:575] ActionsEditor::applyChanges
[08:54:22:578] BaseGui::saveActions
[08:54:22:578] ActionsEditor::saveToConfig
[08:54:22:580] Preferences::save
[08:54:22:580] AssStyles::save
[08:54:26:521] BaseGui::showLog
[08:56:38:131] Playlist::maybeSaveSettings

```

---

### Post by offir on 2015-08-29
Still the same problem

Here is smplayer log

```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 54526003 -monitorpixelaspect 1 -ass -embeddedfonts -ass-line-spacing 0 -ass-font-scale 1 -ass-styles /home/offir/.config/smplayer/styles.ass -subfont-autoscale 0 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 93 -cache 2048 -osdlevel 0 -vf-add screenshot -noslices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/offir/tv show/tv show/Arrow/Arrow 1/Arrow 1x10 Burned.mp4

MPlayer2 2.0-728-g2c378c7-4 (C) 2000-2012 MPlayer Team
Terminal type `unknown' is not defined.

Playing /media/offir/tv show/tv show/Arrow/Arrow 1/Arrow 1x10 Burned.mp4.
Cache size set to 2048 KiB

Cache fill:  0.00% (0 bytes)   
Detected file format: QuickTime / MOV (libavformat)
ID_VIDEO_ID=0
[lavf] stream 0: video (h264), -vid 0
ID_AUDIO_ID=0
ID_AID_0_LANG=und
[lavf] stream 1: audio (aac), -aid 0, -alang und
Clip info:
 major_brand: isom
ID_CLIP_INFO_NAME0=major_brand
ID_CLIP_INFO_VALUE0=isom
 minor_version: 1
ID_CLIP_INFO_NAME1=minor_version
ID_CLIP_INFO_VALUE1=1
 compatible_brands: isom
ID_CLIP_INFO_NAME2=compatible_brands
ID_CLIP_INFO_VALUE2=isom
 creation_time: 2013-01-16 18:45:19
ID_CLIP_INFO_NAME3=creation_time
ID_CLIP_INFO_VALUE3=2013-01-16 18:45:19
ID_CLIP_INFO_N=4
Load subtitles in /media/offir/tv show/tv show/Arrow/Arrow 1/
ID_FILENAME=/media/offir/tv show/tv show/Arrow/Arrow 1/Arrow 1x10 Burned.mp4
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=H264
ID_VIDEO_BITRATE=905096
ID_VIDEO_WIDTH=720
ID_VIDEO_HEIGHT=404
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=MP4A
ID_AUDIO_BITRATE=123656
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
ID_START_TIME=0.00
ID_LENGTH=2523.18
ID_SEEKABLE=1
ID_CHAPTERS=0
[ass] auto-open
Opening video filter: [screenshot]
Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [libavcodec]
ID_VIDEO_CODEC=ffh264
Selected audio codec: AAC (Advanced Audio Coding) [libavcodec]
AUDIO: 48000 Hz, 2 ch, floatle, 123.7 kbit/4.03% (ratio: 15457->384000)
ID_AUDIO_BITRATE=123656
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=ffaac
[Mixer] No hardware mixing, inserting volume filter.
Starting playback...
VIDEO:  720x404  23.976 fps  905.1 kbps (113.1 kB/s)
VO: [xv] 720x404 => 720x404 Planar YV12 
```



I tried it
With two types of drivers
The driver that comes with Linux
And Diver of Nvidia
no change

Both have the problem

---

