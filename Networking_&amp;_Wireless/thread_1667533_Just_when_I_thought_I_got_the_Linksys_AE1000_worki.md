---
title: "Just when I thought I got the Linksys AE1000 working..."
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by spitfirejunky on 2011-01-15
... a bizarre, undocumented crash occurs shortly after attempting to connect to my router.
 
I should first mention that I have been troubleshooting multiple wireless USB network adapters for a week now with no solid results. I've done everything from tweaking the living hell out of ndiswrapper to compiling source from both manufacturers and third parties. So I need some really creative suggestions.
 
This current adapter is the closest I've gotten to any success. After following this thread with chili's lead ([http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558)) I've actually been able to establish a long, stable internet connection. But when I restart, the network front-end takes a long time to establish the same connection with the same settings that were working before. Then when I cancel and retry a couple times, Ubuntu dead-locks. I have tried this with both network-manager and Wicd, but not while both were installed at the same time. They both have the same exact result, although Wicd returns a curious "Bad Password" error message just before Ubuntu freezes.
 
There's too much else to go over, so ask anything you need to ask and I'll go into greater detail. For now, here is the dmesg log that is generated during a failed attempt to connect after restart:
 
linux-image-2.6.35-24-generic
 
```
[ 34.981396] === pAd = ffffc9001321f000, size = 553456 ===
[ 34.981396] 
[ 34.981469] <-- RTMPAllocTxRxRingMemory, Status=0
[ 34.981518] <-- RTMPAllocAdapterBlock, Status=0
[ 34.982368] usbcore: registered new interface driver rt2870
[ 34.987823] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 34.987825] (Reassign Efuse for 3x7x/3x9x/53xx) Size=0x3c [3c0-3fb] 
[ 35.246462] RTMP_TimerListAdd: add timer obj ffffc900132686a8!
[ 35.246465] RTMP_TimerListAdd: add timer obj ffffc90013268728!
[ 35.246468] RTMP_TimerListAdd: add timer obj ffffc900132687a8!
[ 35.246471] RTMP_TimerListAdd: add timer obj ffffc90013268628!
[ 35.246474] RTMP_TimerListAdd: add timer obj ffffc900132684a8!
[ 35.246476] RTMP_TimerListAdd: add timer obj ffffc90013268528!
[ 35.246478] RTMP_TimerListAdd: add timer obj ffffc90013232970!
[ 35.246481] RTMP_TimerListAdd: add timer obj ffffc900132215f8!
[ 35.246483] RTMP_TimerListAdd: add timer obj ffffc90013221680!
[ 35.246485] RTMP_TimerListAdd: add timer obj ffffc90013232b18!
[ 35.246488] RTMP_TimerListAdd: add timer obj ffffc90013232870!
[ 35.246491] RTMP_TimerListAdd: add timer obj ffffc90013232a90!
[ 35.247838] -->RTUSBVenderReset
[ 35.247962] <--RTUSBVenderReset
[ 35.534002] Key1Str is Invalid key length(0) or Type(0)
[ 35.534019] Key2Str is Invalid key length(0) or Type(0)
[ 35.534035] Key3Str is Invalid key length(0) or Type(0)
[ 35.534051] Key4Str is Invalid key length(0) or Type(0)
[ 35.534372] 1. Phy Mode = 5
[ 35.534373] 2. Phy Mode = 5
[ 35.534374] NVM is Efuse and its size =3c[3c0-3fb] 
[ 35.589181] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 35.589184] (Reassign Efuse for 3x7x/3x9x/53xx) Size=0x3c [3c0-3fb] 
[ 35.608405] 3. Phy Mode = 5
[ 35.676503] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 35.679622] MCS Set = ff ff 00 00 01
[ 35.690308] <==== rt28xx_init, Status=0
[ 35.691740] 0x1300 = 00064300
[ 35.808083] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 587
[ 38.574860] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 2887
[ 38.576858] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 2887
[ 46.078466] ra0: no IPv6 routers present
[ 59.025620] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3319
[ 59.025735] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
[ 59.027664] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3319
[ 66.912192] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 3467
[ 66.912319] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
[ 66.914172] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 3467
[ 74.808659] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 3467
[ 74.808836] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
[ 74.810967] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 2863
[ 74.883424] BUG: unable to handle kernel paging request at ffffcfb0132681ec
[ 74.883430] IP: [<ffffffffa0ab67e8>] CntlOidRTBssidProc+0x78/0x570 [rt3572sta]
[ 74.883454] PGD 0 
[ 74.883456] Oops: 0000 [#1] SMP 
[ 74.883459] last sysfs file: /sys/devices/system/cpu/cpu7/cache/index2/shared_cpu_map
[ 74.883463] CPU 3 
[ 74.883464] Modules linked in: rt3572sta parport_pc ppdev binfmt_misc snd_hda_codec_nvhdmi snd_hda_codec_realtek psmouse nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_seq_midi snd_pcm snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device joydev i7core_edac asus_atk0110 snd serio_raw edac_core soundcore snd_page_alloc xhci_hcd lp parport usbhid hid firewire_ohci firewire_core crc_itu_t sky2
[ 74.883493] 
[ 74.883497] Pid: 1735, comm: RtmpMlmeTask Tainted: P 2.6.35-24-generic #42-Ubuntu P6X58D PREMIUM/System Product Name
[ 74.883500] RIP: 0010:[<ffffffffa0ab67e8>] [<ffffffffa0ab67e8>] CntlOidRTBssidProc+0x78/0x570 [rt3572sta]
[ 74.883520] RSP: 0018:ffff880315897d10 EFLAGS: 00010202
[ 74.883523] RAX: 00000000ffffffff RBX: ffffc9001321f000 RCX: 0000000000000004
[ 74.883526] RDX: 000000000000000f RSI: 000006affffff950 RDI: ffffc9001322ae1a
[ 74.883528] RBP: ffff880315897db0 R08: ffffc9001322ae18 R09: ffffc9001326ec78
[ 74.883531] R10: 000000000000000f R11: 0000000000000001 R12: ffffc9001322ae18
[ 74.883533] R13: ffff880315897e68 R14: ffffc900132226c4 R15: ffffc90013222168
[ 74.883537] FS: 0000000000000000(0000) GS:ffff880001e60000(0000) knlGS:0000000000000000
[ 74.883540] CS: 0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[ 74.883542] CR2: ffffcfb0132681ec CR3: 0000000320ebd000 CR4: 00000000000006e0
[ 74.883545] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 74.883548] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 74.883551] Process RtmpMlmeTask (pid: 1735, threadinfo ffff880315896000, task ffff880319d40000)
[ 74.883553] Stack:
[ 74.883555] ffff880315897d20 0000000000000000 ffffc9001321f000 ffff880315897d40
[ 74.883559] <0> ffff880315897d80 ffffffffa0ad2c07 0000000000024230 ffffc9001321f000
[ 74.883563] <0> 1302000000000000 ffffc9001321f000 0000000000000030 ffff880315897e68
[ 74.883568] Call Trace:
[ 74.883585] [<ffffffffa0ad2c07>] ? RTUSBWriteBBPRegister+0xc7/0x100 [rt3572sta]
[ 74.883604] [<ffffffffa0ab74c5>] CntlIdleProc+0xb5/0x170 [rt3572sta]
[ 74.883622] [<ffffffffa0ab7668>] MlmeCntlMachinePerformAction+0xe8/0x250 [rt3572sta]
[ 74.883634] [<ffffffffa0a7d09c>] MlmeHandler+0x1dc/0x320 [rt3572sta]
[ 74.883649] [<ffffffffa0adb76b>] MlmeThread+0x5b/0xc0 [rt3572sta]
[ 74.883663] [<ffffffffa0adb710>] ? MlmeThread+0x0/0xc0 [rt3572sta]
[ 74.883668] [<ffffffff8107f1d6>] kthread+0x96/0xa0
[ 74.883673] [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
[ 74.883676] [<ffffffff8107f140>] ? kthread+0x0/0xa0
[ 74.883680] [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
[ 74.883682] Code: a0 3b 01 00 48 81 c7 28 98 04 00 e8 53 26 fc ff 80 bb 29 28 00 00 00 0f 88 e6 00 00 00 48 69 f0 b0 06 00 00 0f b6 8b c1 3b 01 00 <3a> 8c 33 9c 98 04 00 0f 84 43 03 00 00 b9 ff ff ff ff 8b 93 10 
[ 74.883718] RIP [<ffffffffa0ab67e8>] CntlOidRTBssidProc+0x78/0x570 [rt3572sta]
[ 74.883736] RSP <ffff880315897d10>
[ 74.883738] CR2: ffffcfb0132681ec
[ 74.883741] ---[ end trace 26e1fe743e640977 ]---
```
 
Thanks in advance for your efforts.

---

### Post by chili555 on 2011-01-15
> [ 74.883424] BUG: unable to handle kernel paging request at ffffcfb0132681ec
[ 74.883430] IP: [<ffffffffa0ab67e8>] CntlOidRTBssidProc+0x78/0x570 [rt3572sta]
[ 74.883454] PGD 0 
[ 74.883456] Oops: 0000 [#1] SMP A kernel oops is a fairly serious thing. I am not a kernel expert, so I can't tell you how to fix it. It has been suggested that the most recent kernel image is defective: [http://www1.ubuntuforums.org/showthread.php?p=10318736](http://www1.ubuntuforums.org/showthread.php?p=10318736)

See post #5. Find your kernel version with:```
uname -r
```

If you decide to implement the possible fix, be sure to use the GRUB menu to boot into another kernel besides -24.

---

### Post by spitfirejunky on 2011-01-15
chili to the rescue again. :-)
 
Yes, I'm using the most recent kernel, 24. I actually don't know if restarting into 22 causes the same problem. Guess there's only one way to find out.
 
I'll reply when I've tested it.

---

### Post by chili555 on 2011-01-15
You'll probably need to rebuild the module for the older kernel:```
sudo su
make clean
make
make install 
modprobe rt3572sta
exit
```

---

### Post by spitfirejunky on 2011-01-15
> **chili555 said:**
> You'll probably need to rebuild the module for the older kernel:```
sudo su
make clean
make
make install 
modprobe rt3572sta
exit
```
 
Yep, I know.
 
Confirmed: same exact error (almost exactly the same log) happens under 22. Worked right after install as usual, then crashes the computer after restart.
 
linux-image-2.6.35-22-generic
 
```
[ 8.498633] === pAd = ffffc9001262e000, size = 553456 ===
[ 8.498633] 
[ 8.498704] <-- RTMPAllocTxRxRingMemory, Status=0
[ 8.498747] <-- RTMPAllocAdapterBlock, Status=0
[ 8.499393] usbcore: registered new interface driver rt2870
[ 8.653613] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[ 8.780186] type=1400 audit(1295110654.437:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=957 comm="apparmor_parser"
[ 8.780195] type=1400 audit(1295110654.437:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=952 comm="apparmor_parser"
[ 8.780316] type=1400 audit(1295110654.437:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=953 comm="apparmor_parser"
[ 8.780365] type=1400 audit(1295110654.437:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=956 comm="apparmor_parser"
[ 8.780655] type=1400 audit(1295110654.437:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=953 comm="apparmor_parser"
[ 8.780809] type=1400 audit(1295110654.437:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=956 comm="apparmor_parser"
[ 8.780836] type=1400 audit(1295110654.437:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=954 comm="apparmor_parser"
[ 8.905658] sky2 0000:06:00.0: eth0: enabling interface
[ 8.906882] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 8.911063] sky2 0000:05:00.0: eth1: enabling interface
[ 8.911886] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 8.913508] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 8.913512] (Reassign Efuse for 3x7x/3x9x/53xx) Size=0x3c [3c0-3fb] 
[ 9.173275] RTMP_TimerListAdd: add timer obj ffffc900126776a8!
[ 9.173278] RTMP_TimerListAdd: add timer obj ffffc90012677728!
[ 9.173281] RTMP_TimerListAdd: add timer obj ffffc900126777a8!
[ 9.173284] RTMP_TimerListAdd: add timer obj ffffc90012677628!
[ 9.173286] RTMP_TimerListAdd: add timer obj ffffc900126774a8!
[ 9.173289] RTMP_TimerListAdd: add timer obj ffffc90012677528!
[ 9.173291] RTMP_TimerListAdd: add timer obj ffffc90012641970!
[ 9.173293] RTMP_TimerListAdd: add timer obj ffffc900126305f8!
[ 9.173295] RTMP_TimerListAdd: add timer obj ffffc90012630680!
[ 9.173298] RTMP_TimerListAdd: add timer obj ffffc90012641b18!
[ 9.173301] RTMP_TimerListAdd: add timer obj ffffc90012641870!
[ 9.173303] RTMP_TimerListAdd: add timer obj ffffc90012641a90!
[ 9.174649] -->RTUSBVenderReset
[ 9.174776] <--RTUSBVenderReset
[ 9.472363] Key1Str is Invalid key length(0) or Type(0)
[ 9.472379] Key2Str is Invalid key length(0) or Type(0)
[ 9.472395] Key3Str is Invalid key length(0) or Type(0)
[ 9.472412] Key4Str is Invalid key length(0) or Type(0)
[ 9.472736] 1. Phy Mode = 5
[ 9.472737] 2. Phy Mode = 5
[ 9.472739] NVM is Efuse and its size =3c[3c0-3fb] 
[ 9.527845] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 9.527848] (Reassign Efuse for 3x7x/3x9x/53xx) Size=0x3c [3c0-3fb] 
[ 9.547211] 3. Phy Mode = 5
[ 9.615684] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 9.618803] MCS Set = ff ff 00 00 01
[ 9.629566] <==== rt28xx_init, Status=0
[ 9.631047] 0x1300 = 00064300
[ 10.083401] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
[ 10.312730] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 10.312734] (Reassign Efuse for 3x7x/3x9x/53xx) Size=0x3c [3c0-3fb] 
[ 10.371369] ppdev: user-space parallel port driver
[ 10.573336] RTMP_TimerListAdd: add timer obj ffffc900126776a8!
[ 10.573339] RTMP_TimerListAdd: add timer obj ffffc90012677728!
[ 10.573341] RTMP_TimerListAdd: add timer obj ffffc900126777a8!
[ 10.573342] RTMP_TimerListAdd: add timer obj ffffc90012677628!
[ 10.573344] RTMP_TimerListAdd: add timer obj ffffc900126774a8!
[ 10.573345] RTMP_TimerListAdd: add timer obj ffffc90012677528!
[ 10.573347] RTMP_TimerListAdd: add timer obj ffffc90012641970!
[ 10.573349] RTMP_TimerListAdd: add timer obj ffffc900126305f8!
[ 10.573350] RTMP_TimerListAdd: add timer obj ffffc90012630680!
[ 10.573352] RTMP_TimerListAdd: add timer obj ffffc90012641b18!
[ 10.573353] RTMP_TimerListAdd: add timer obj ffffc90012641870!
[ 10.573355] RTMP_TimerListAdd: add timer obj ffffc90012641a90!
[ 10.575353] -->RTUSBVenderReset
[ 10.575478] <--RTUSBVenderReset
[ 10.853262] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[ 10.853269] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[ 10.853498] Key1Str is Invalid key length(0) or Type(0)
[ 10.853518] Key2Str is Invalid key length(0) or Type(0)
[ 10.853538] Key3Str is Invalid key length(0) or Type(0)
[ 10.853560] Key4Str is Invalid key length(0) or Type(0)
[ 10.853996] 1. Phy Mode = 5
[ 10.853997] 2. Phy Mode = 5
[ 10.853999] NVM is Efuse and its size =3c[3c0-3fb] 
[ 10.909449] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 10.909452] (Reassign Efuse for 3x7x/3x9x/53xx) Size=0x3c [3c0-3fb] 
[ 10.928687] 3. Phy Mode = 5
[ 10.997158] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 11.000280] MCS Set = ff ff 00 00 01
[ 11.011089] <==== rt28xx_init, Status=0
[ 11.012523] 0x1300 = 00064300
[ 12.075378] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
[ 13.935872] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1641
[ 13.937820] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1641
[ 21.569094] ra0: no IPv6 routers present
[ 26.670963] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 26.670968] (Reassign Efuse for 3x7x/3x9x/53xx) Size=0x3c [3c0-3fb] 
[ 26.931300] RTMP_TimerListAdd: add timer obj ffffc900126776a8!
[ 26.931304] RTMP_TimerListAdd: add timer obj ffffc90012677728!
[ 26.931307] RTMP_TimerListAdd: add timer obj ffffc900126777a8!
[ 26.931309] RTMP_TimerListAdd: add timer obj ffffc90012677628!
[ 26.931312] RTMP_TimerListAdd: add timer obj ffffc900126774a8!
[ 26.931314] RTMP_TimerListAdd: add timer obj ffffc90012677528!
[ 26.931317] RTMP_TimerListAdd: add timer obj ffffc90012641970!
[ 26.931319] RTMP_TimerListAdd: add timer obj ffffc900126305f8!
[ 26.931321] RTMP_TimerListAdd: add timer obj ffffc90012630680!
[ 26.931324] RTMP_TimerListAdd: add timer obj ffffc90012641b18!
[ 26.931327] RTMP_TimerListAdd: add timer obj ffffc90012641870!
[ 26.931329] RTMP_TimerListAdd: add timer obj ffffc90012641a90!
[ 26.932712] -->RTUSBVenderReset
[ 26.932837] <--RTUSBVenderReset
[ 27.209241] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[ 27.209252] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[ 27.209480] Key1Str is Invalid key length(0) or Type(0)
[ 27.209496] Key2Str is Invalid key length(0) or Type(0)
[ 27.209512] Key3Str is Invalid key length(0) or Type(0)
[ 27.209528] Key4Str is Invalid key length(0) or Type(0)
[ 27.209850] 1. Phy Mode = 5
[ 27.209851] 2. Phy Mode = 5
[ 27.209852] NVM is Efuse and its size =3c[3c0-3fb] 
[ 27.265434] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 27.265438] (Reassign Efuse for 3x7x/3x9x/53xx) Size=0x3c [3c0-3fb] 
[ 27.284798] 3. Phy Mode = 5
[ 27.353150] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 27.356307] MCS Set = ff ff 00 00 01
[ 27.367033] <==== rt28xx_init, Status=0
[ 27.368493] 0x1300 = 00064300
[ 30.258376] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1882
[ 30.260321] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1882
[ 37.541681] ra0: no IPv6 routers present
[ 38.567310] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 2830
[ 38.567483] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
[ 38.569550] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 2830
[ 46.450616] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 3015
[ 46.450744] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
[ 46.452713] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 3015
[ 54.336442] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3159
[ 54.336568] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
[ 54.338604] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3159
[ 62.222751] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 3379
[ 62.222912] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
[ 62.224705] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 3379
[ 70.108922] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 3379
[ 70.109108] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
[ 70.111793] ===>rt_ioctl_giwscan. 17(17) BSS returned, data->length = 2974
[ 77.996621] ===>rt_ioctl_giwscan. 18(18) BSS returned, data->length = 3291
[ 77.996720] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
[ 77.998793] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1979
[ 78.072435] BUG: unable to handle kernel paging request at ffffcfb0126771ec
[ 78.072439] IP: [<ffffffffa02dd7e8>] CntlOidRTBssidProc+0x78/0x570 [rt3572sta]
[ 78.072452] PGD 0 
[ 78.072454] Oops: 0000 [#1] SMP 
[ 78.072455] last sysfs file: /sys/devices/pci0000:ff/0000:ff:06.3/modalias
[ 78.072457] CPU 1 
[ 78.072458] Modules linked in: parport_pc ppdev binfmt_misc rt3572sta snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi nouveau snd_seq_midi_event snd_seq ttm snd_timer snd_seq_device drm_kms_helper joydev snd psmouse asus_atk0110 drm i2c_algo_bit xhci_hcd serio_raw i7core_edac soundcore snd_page_alloc edac_core lp parport usbhid hid firewire_ohci firewire_core crc_itu_t sky2
[ 78.072474] 
[ 78.072476] Pid: 1714, comm: RtmpMlmeTask Not tainted 2.6.35-22-generic #33-Ubuntu P6X58D PREMIUM/System Product Name
[ 78.072477] RIP: 0010:[<ffffffffa02dd7e8>] [<ffffffffa02dd7e8>] CntlOidRTBssidProc+0x78/0x570 [rt3572sta]
[ 78.072488] RSP: 0018:ffff88031afe7d10 EFLAGS: 00010202
[ 78.072489] RAX: 00000000ffffffff RBX: ffffc9001262e000 RCX: 0000000000000004
[ 78.072491] RDX: 000000000000000a RSI: 000006affffff950 RDI: ffffc90012632a3a
[ 78.072492] RBP: ffff88031afe7db0 R08: ffffc90012632a38 R09: ffffc9001267bb08
[ 78.072493] R10: 000000000000000a R11: 0000000000000001 R12: ffffc90012632a38
[ 78.072495] R13: ffff88031afe7e68 R14: ffffc900126316c4 R15: ffffc90012631168
[ 78.072496] FS: 0000000000000000(0000) GS:ffff880001e20000(0000) knlGS:0000000000000000
[ 78.072498] CS: 0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[ 78.072499] CR2: ffffcfb0126771ec CR3: 0000000321239000 CR4: 00000000000006e0
[ 78.072500] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 78.072502] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 78.072503] Process RtmpMlmeTask (pid: 1714, threadinfo ffff88031afe6000, task ffff88032d7fc4a0)
[ 78.072504] Stack:
[ 78.072505] ffff88031afe7d20 0000000000000000 ffffc9001262e000 ffff88031afe7d40
[ 78.072507] <0> ffff88031afe7d80 ffffffffa02f9c07 0000000000024230 ffffc9001262e000
[ 78.072510] <0> 1302000000000000 ffffc9001262e000 0000000000000030 ffff88031afe7e68
[ 78.072512] Call Trace:
[ 78.072522] [<ffffffffa02f9c07>] ? RTUSBWriteBBPRegister+0xc7/0x100 [rt3572sta]
[ 78.072531] [<ffffffffa02de4c5>] CntlIdleProc+0xb5/0x170 [rt3572sta]
[ 78.072541] [<ffffffffa02de668>] MlmeCntlMachinePerformAction+0xe8/0x250 [rt3572sta]
[ 78.072547] [<ffffffffa02a409c>] MlmeHandler+0x1dc/0x320 [rt3572sta]
[ 78.072554] [<ffffffffa030276b>] MlmeThread+0x5b/0xc0 [rt3572sta]
[ 78.072561] [<ffffffffa0302710>] ? MlmeThread+0x0/0xc0 [rt3572sta]
[ 78.072564] [<ffffffff8107f0b6>] kthread+0x96/0xa0
[ 78.072567] [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
[ 78.072569] [<ffffffff8107f020>] ? kthread+0x0/0xa0
[ 78.072571] [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
[ 78.072572] Code: a0 3b 01 00 48 81 c7 28 98 04 00 e8 53 26 fc ff 80 bb 29 28 00 00 00 0f 88 e6 00 00 00 48 69 f0 b0 06 00 00 0f b6 8b c1 3b 01 00 <3a> 8c 33 9c 98 04 00 0f 84 43 03 00 00 b9 ff ff ff ff 8b 93 10 
[ 78.072590] RIP [<ffffffffa02dd7e8>] CntlOidRTBssidProc+0x78/0x570 [rt3572sta]
[ 78.072599] RSP <ffff88031afe7d10>
[ 78.072600] CR2: ffffcfb0126771ec
[ 78.072602] ---[ end trace 1bd3482f03410141 ]---
```

---

### Post by chili555 on 2011-01-15
I'm sorry; I have no more suggestions. You might ask about kernel oops in General Help.

---

