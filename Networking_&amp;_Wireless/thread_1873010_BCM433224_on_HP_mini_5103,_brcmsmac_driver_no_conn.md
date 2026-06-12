---
title: "BCM433224 on HP mini 5103, brcmsmac driver: no connection, system crashes"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by rbsmn on 2011-10-31
Dear knowledgeable people of the forum,

I have a HP mini 5103 and the Broadcom BCM43224 wireless card that comes with it. After having lots of problems with getting wifi to work on Ubuntu versions 10.10 and 11.04, I upgraded to 11.10. Initially everything worked perfectly using the built-in brcmsmac driver. After a week or two, wifi stopped working and trying to connect to an AP started crashing the system (more on the nature of the failure a bit later). This might have been after some updates I installed from updatemanager. I reinstalled 11.10 from a CD and got wifi working again, until after another week it stopped working again. After that I tried another reinstall, but it doesn't seem to help anymore.

I've looked at the sticky thread on the BCxx cards, but I haven't found a solution to my problem there. I tried the wl drivers too (blacklisting brcmsmac and bcma) since they seemed to work better in 11.04 than the open-source drivers, but now on 11.10 if wl is loaded instead of brcmsmac, the laptop picks up wireless AP's quite randomly. I don't usually get my own router to show up, even if the laptop is sitting right next to it. And connecting doesn't work anyway.

The brcmsmac driver seems to be loaded fine:

nm-tool
```

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        AC:81:12:33:EF:B7

```lspci -k
```

01:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
    Subsystem: Hewlett-Packard Company Device 1510
    Kernel driver in use: brcmsmac
    Kernel modules: bcma, brcmsmac

```Lots of wireless networks show up in nm-tool and the networkmanager applet, so there seems to be nothing wrong until I try to connect.

When connecting, the networkmanager applet simply keeps on asking for the WPA key. (I have it right, as witnessed by other devices. Also, no other device has problems with the router and the laptop used to work too.) After trying to connect for a while networkmanager hangs up, taking down many other things as well: sudo, ifconfig, iwconfig etc. stop working (there's just no output; ctrl-C doesn't do anything). Ubuntu's graphical interface mostly keeps on working, but not much else. The system also won't shutdown properly after having tried getting a wifi connection. Kernel.log shows that some tasks are "blocked for more than 120 seconds", and sometimes these messages come up also while trying to shutdown.

Hopefully this is enough to get started on fixing my problem!

From kern.log some time after having tried to get a wifi connection:
```

Oct 31 21:40:44 abel kernel: [  600.976147] INFO: task NetworkManager:502 blocked for more than 120 seconds.
Oct 31 21:40:44 abel kernel: [  600.976161] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 31 21:40:44 abel kernel: [  600.976172] NetworkManager  D eca0be3c     0   502      1 0x00000000
Oct 31 21:40:44 abel kernel: [  600.976190]  eca0bea0 00000086 eca0bea4 eca0be3c c1430d44 eca0be64 c175dfe0 c1868ec0
Oct 31 21:40:44 abel kernel: [  600.976212]  c1868ec0 263d0919 00000052 f5805ec0 eca02640 ec8e5940 eca0be88 c1117e0d
Oct 31 21:40:44 abel kernel: [  600.976233]  eec2c900 bf96ef18 eca0be64 ecb09680 c142a1ac 0000023c 00000240 c17abf00
Oct 31 21:40:44 abel kernel: [  600.976255] Call Trace:
Oct 31 21:40:44 abel kernel: [  600.976283]  [<c1430d44>] ? verify_iovec+0x44/0xb0
Oct 31 21:40:44 abel kernel: [  600.976300]  [<c1117e0d>] ? kmem_cache_alloc+0x11d/0x140
Oct 31 21:40:44 abel kernel: [  600.976314]  [<c142a1ac>] ? sk_prot_alloc+0x2c/0x1a0
Oct 31 21:40:44 abel kernel: [  600.976327]  [<c11182d5>] ? kmem_cache_alloc_trace+0x105/0x140
Oct 31 21:40:44 abel kernel: [  600.976343]  [<c152b656>] __mutex_lock_slowpath+0xc6/0x120
Oct 31 21:40:44 abel kernel: [  600.976356]  [<c152b304>] mutex_lock+0x24/0x40
Oct 31 21:40:44 abel kernel: [  600.976368]  [<c1445da2>] rtnl_lock+0x12/0x20
Oct 31 21:40:44 abel kernel: [  600.976380]  [<c143bd18>] dev_ioctl+0x1a8/0x2f0
Oct 31 21:40:44 abel kernel: [  600.976393]  [<c1425f54>] ? sock_alloc_file+0x84/0xf0
Oct 31 21:40:44 abel kernel: [  600.976407]  [<c152c4cd>] ? _raw_spin_lock+0xd/0x10
Oct 31 21:40:44 abel kernel: [  600.976420]  [<c148af80>] ? udp_poll+0x70/0x70
Oct 31 21:40:44 abel kernel: [  600.976432]  [<c14266ba>] sock_ioctl+0x8a/0x290
Oct 31 21:40:44 abel kernel: [  600.976445]  [<c1426630>] ? move_addr_to_user+0x90/0x90
Oct 31 21:40:44 abel kernel: [  600.976457]  [<c1138079>] do_vfs_ioctl+0x79/0x2d0
Oct 31 21:40:44 abel kernel: [  600.976469]  [<c113833f>] sys_ioctl+0x6f/0x80
Oct 31 21:40:44 abel kernel: [  600.976482]  [<c152c8e4>] syscall_call+0x7/0xb
Oct 31 21:40:44 abel kernel: [  600.976497]  [<c1520000>] ? reserve_backup_gdb.isra.11+0x26d/0x2c0
Oct 31 21:40:44 abel kernel: [  600.976521] INFO: task irqbalance:841 blocked for more than 120 seconds.
Oct 31 21:40:44 abel kernel: [  600.976529] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 31 21:40:44 abel kernel: [  600.976539] irqbalance      D 00000000     0   841      1 0x00000000
Oct 31 21:40:44 abel kernel: [  600.976553]  eb8ebea0 00000086 00000029 00000000 00000000 f2724360 c175dfe0 c1868ec0
Oct 31 21:40:44 abel kernel: [  600.976574]  c1868ec0 370ff3bf 00000051 f5805ec0 eba56600 c175dfe0 eb8ebe88 c1117e0d
Oct 31 21:40:44 abel kernel: [  600.976595]  00000000 00000000 00000000 ecb09440 c142a1ac 0000023c 00000240 c17abf00
Oct 31 21:40:44 abel kernel: [  600.976615] Call Trace:
Oct 31 21:40:44 abel kernel: [  600.976628]  [<c1117e0d>] ? kmem_cache_alloc+0x11d/0x140
Oct 31 21:40:44 abel kernel: [  600.976642]  [<c142a1ac>] ? sk_prot_alloc+0x2c/0x1a0
Oct 31 21:40:44 abel kernel: [  600.976654]  [<c11182d5>] ? kmem_cache_alloc_trace+0x105/0x140
Oct 31 21:40:44 abel kernel: [  600.976668]  [<c152b656>] __mutex_lock_slowpath+0xc6/0x120
Oct 31 21:40:44 abel kernel: [  600.976681]  [<c152b304>] mutex_lock+0x24/0x40
Oct 31 21:40:44 abel kernel: [  600.976693]  [<c1445da2>] rtnl_lock+0x12/0x20
Oct 31 21:40:44 abel kernel: [  600.976704]  [<c143bd18>] dev_ioctl+0x1a8/0x2f0
Oct 31 21:40:44 abel kernel: [  600.976717]  [<c1425f54>] ? sock_alloc_file+0x84/0xf0
Oct 31 21:40:44 abel kernel: [  600.976729]  [<c152c4cd>] ? _raw_spin_lock+0xd/0x10
Oct 31 21:40:44 abel kernel: [  600.976741]  [<c148af80>] ? udp_poll+0x70/0x70
Oct 31 21:40:44 abel kernel: [  600.976754]  [<c14266ba>] sock_ioctl+0x8a/0x290
Oct 31 21:40:44 abel kernel: [  600.976766]  [<c1426630>] ? move_addr_to_user+0x90/0x90
Oct 31 21:40:44 abel kernel: [  600.976778]  [<c1138079>] do_vfs_ioctl+0x79/0x2d0
Oct 31 21:40:44 abel kernel: [  600.976789]  [<c113833f>] sys_ioctl+0x6f/0x80
Oct 31 21:40:44 abel kernel: [  600.976802]  [<c152c8e4>] syscall_call+0x7/0xb
Oct 31 21:40:44 abel kernel: [  600.976815]  [<c1520000>] ? reserve_backup_gdb.isra.11+0x26d/0x2c0
Oct 31 21:40:44 abel kernel: [  600.976829] INFO: task wpa_supplicant:995 blocked for more than 120 seconds.
Oct 31 21:40:44 abel kernel: [  600.976837] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 31 21:40:44 abel kernel: [  600.976846] wpa_supplicant  D eb117e44     0   995      1 0x00000000
Oct 31 21:40:44 abel kernel: [  600.976861]  eb117bd0 00000086 00000014 eb117e44 c11395a8 00989676 f54d0000 c1868ec0
Oct 31 21:40:44 abel kernel: [  600.976882]  c1868ec0 e554cb7c 00000030 f5885ec0 ebb572c0 ec8e5940 eb117e74 eb117e70
Oct 31 21:40:44 abel kernel: [  600.976903]  eb117e6c eb117f60 eb117e68 eb117e64 eb117e60 00000000 00000000 00000020
Oct 31 21:40:44 abel kernel: [  600.976923] Call Trace:
Oct 31 21:40:44 abel kernel: [  600.976935]  [<c11395a8>] ? do_select+0x4e8/0x570
Oct 31 21:40:44 abel kernel: [  600.976950]  [<c152b656>] __mutex_lock_slowpath+0xc6/0x120
Oct 31 21:40:44 abel kernel: [  600.976962]  [<c152b304>] mutex_lock+0x24/0x40
Oct 31 21:40:44 abel kernel: [  600.977024]  [<f83df765>] ieee80211_request_scan+0x25/0x50 [mac80211]
Oct 31 21:40:44 abel kernel: [  600.977067]  [<f83ece6c>] ieee80211_scan+0x6c/0x90 [mac80211]
Oct 31 21:40:44 abel kernel: [  600.977110]  [<f815ccdb>] nl80211_trigger_scan+0x3bb/0x480 [cfg80211]
Oct 31 21:40:44 abel kernel: [  600.977148]  [<f8153fe0>] ? nl80211_addset_beacon+0x190/0x190 [cfg80211]
Oct 31 21:40:44 abel kernel: [  600.977162]  [<c145d4f4>] genl_rcv_msg+0x1c4/0x240
Oct 31 21:40:44 abel kernel: [  600.977179]  [<c145d330>] ? genl_rcv+0x30/0x30
Oct 31 21:40:44 abel kernel: [  600.977191]  [<c145ce9e>] netlink_rcv_skb+0x8e/0xb0
Oct 31 21:40:44 abel kernel: [  600.977202]  [<c145d31c>] genl_rcv+0x1c/0x30
Oct 31 21:40:44 abel kernel: [  600.977214]  [<c145c8a9>] netlink_unicast+0x239/0x290
Oct 31 21:40:44 abel kernel: [  600.977226]  [<c145cb5b>] netlink_sendmsg+0x25b/0x2e0
Oct 31 21:40:44 abel kernel: [  600.977240]  [<c1425d7c>] sock_sendmsg+0xec/0x110
Oct 31 21:40:44 abel kernel: [  600.977253]  [<c1425d7c>] ? sock_sendmsg+0xec/0x110
Oct 31 21:40:44 abel kernel: [  600.977268]  [<c128836f>] ? __copy_from_user_ll+0x1f/0x40
Oct 31 21:40:44 abel kernel: [  600.977281]  [<c1288502>] ? _copy_from_user+0x42/0x60
Oct 31 21:40:44 abel kernel: [  600.977294]  [<c1430d44>] ? verify_iovec+0x44/0xb0
Oct 31 21:40:44 abel kernel: [  600.977306]  [<c1427590>] __sys_sendmsg+0x270/0x280
Oct 31 21:40:44 abel kernel: [  600.977322]  [<c1058537>] ? recalc_sigpending+0x17/0x40
Oct 31 21:40:44 abel kernel: [  600.977335]  [<c1058a95>] ? __set_task_blocked+0x35/0x80
Oct 31 21:40:44 abel kernel: [  600.977347]  [<c105a9b3>] ? set_current_blocked+0x43/0x60
Oct 31 21:40:44 abel kernel: [  600.977362]  [<c100a7bd>] ? restore_i387_fxsave+0x8d/0xa0
Oct 31 21:40:44 abel kernel: [  600.977376]  [<c142839b>] sys_sendmsg+0x3b/0x60
Oct 31 21:40:44 abel kernel: [  600.977389]  [<c1428a23>] sys_socketcall+0x263/0x2c0
Oct 31 21:40:44 abel kernel: [  600.977402]  [<c12884a0>] ? copy_to_user+0x40/0x60
Oct 31 21:40:44 abel kernel: [  600.977415]  [<c104cf22>] ? sys_gettimeofday+0x32/0x70
Oct 31 21:40:44 abel kernel: [  600.977429]  [<c152c8e4>] syscall_call+0x7/0xb
Oct 31 21:40:44 abel kernel: [  600.977547] INFO: task ifconfig:2065 blocked for more than 120 seconds.
Oct 31 21:40:44 abel kernel: [  600.977555] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Oct 31 21:40:44 abel kernel: [  600.977565] ifconfig        D f6d07e2c     0  2065   2013 0x00000000
Oct 31 21:40:44 abel kernel: [  600.977580]  f6d07ea0 00000086 f6d07eb8 f6d07e2c f6d07e30 c1141929 f54d0000 c1868ec0
Oct 31 21:40:44 abel kernel: [  600.977601]  c1868ec0 0ad490ca 0000004f f5885ec0 eab34c80 f54a5940 fffffffe f6d07f78
Oct 31 21:40:44 abel kernel: [  600.977622]  00000286 00000020 e0e316c0 fffffffe f6d07f78 f6d07e74 c10aec72 f6d07e84
Oct 31 21:40:44 abel kernel: [  600.977643] Call Trace:
Oct 31 21:40:44 abel kernel: [  600.977658]  [<c1141929>] ? vfsmount_lock_local_unlock+0x19/0x20
Oct 31 21:40:44 abel kernel: [  600.977674]  [<c10aec72>] ? call_rcu_sched+0x12/0x20
Oct 31 21:40:44 abel kernel: [  600.977689]  [<c1129cff>] ? put_filp+0x4f/0x60
Oct 31 21:40:44 abel kernel: [  600.977702]  [<c11358b5>] ? release_open_intent+0x35/0x40
Oct 31 21:40:44 abel kernel: [  600.977715]  [<c1135983>] ? path_openat+0xc3/0x350
Oct 31 21:40:44 abel kernel: [  600.977728]  [<c152b656>] __mutex_lock_slowpath+0xc6/0x120
Oct 31 21:40:44 abel kernel: [  600.977741]  [<c152b304>] mutex_lock+0x24/0x40
Oct 31 21:40:44 abel kernel: [  600.977754]  [<c1445da2>] rtnl_lock+0x12/0x20
Oct 31 21:40:44 abel kernel: [  600.977766]  [<c143bdd5>] dev_ioctl+0x265/0x2f0
Oct 31 21:40:44 abel kernel: [  600.977779]  [<c148af80>] ? udp_poll+0x70/0x70
Oct 31 21:40:44 abel kernel: [  600.977792]  [<c14266ba>] sock_ioctl+0x8a/0x290
Oct 31 21:40:44 abel kernel: [  600.977804]  [<c113192b>] ? putname+0x2b/0x40
Oct 31 21:40:44 abel kernel: [  600.977816]  [<c1426630>] ? move_addr_to_user+0x90/0x90
Oct 31 21:40:44 abel kernel: [  600.977828]  [<c1138079>] do_vfs_ioctl+0x79/0x2d0
Oct 31 21:40:44 abel kernel: [  600.977839]  [<c113833f>] sys_ioctl+0x6f/0x80
Oct 31 21:40:44 abel kernel: [  600.977851]  [<c1127b1e>] ? sys_open+0x2e/0x40
Oct 31 21:40:44 abel kernel: [  600.977864]  [<c152c8e4>] syscall_call+0x7/0xb

```

---

### Post by praseodym on 2011-10-31
Hi,

use the Broadcom-STA driver for this device and blacklist the modules bcma, brcmsmac and brcm80211. Reboot after that

---

### Post by rbsmn on 2011-11-01
1. Install the package bcmwl-kernel-source. (version 5.100.82.38+bdcom-0ubuntu4)

2. Blacklist brcmsmac and bcma.

3. Reboot

lspci -k
```

01:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
    Subsystem: Hewlett-Packard Company Device 1510
    Kernel driver in use: wl
    Kernel modules: wl, bcma, brcmsmac

```nm-tool
```

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        AC:81:12:33:EF:B7

```

Just as before when trying this driver, the laptop picks up very few wireless networks in the area. "sudo iwlist scan" gives different results every time, especially my router does not come up even though the laptop is right next to it.

---

### Post by praseodym on 2011-11-01
Check:

```
lsmod
iwconfig
iwlist chan
dmesg | grep wl
```
Which channel do you want to connect to?

---

### Post by rbsmn on 2011-11-01
Networkmanager now says it has connected to my wireless router. Wireless internet connection still doesn't work. Not even the router responds to ping (that is, ping 192.168.0.1 gets no replies).

ifconfig
```

eth1      Link encap:Ethernet  HWaddr ac:81:12:33:ef:b7  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ae81:12ff:fe33:efb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:1 dropped:0 overruns:0 frame:22880
          TX packets:164 errors:21 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5350 (5.3 KB)  TX bytes:19347 (19.3 KB)
          Interrupt:16 

```

lsmod
```

Module                  Size  Used by
michael_mic            12540  4 
arc4                   12473  2 
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60049  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
btusb                  18160  2 
bluetooth             148839  23 bnep,rfcomm,btusb
psmouse                73673  0 
lib80211_crypt_tkip    17240  0 
serio_raw              12990  0 
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
wl                   2646601  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
hp_accel               21632  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
lis3lv02d              19280  1 hp_accel
input_polldev          13648  1 lis3lv02d
i915                  505108  4 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
wmi                    18744  1 hp_wmi
drm_kms_helper         32889  1 i915
drm                   192226  5 i915,drm_kms_helper
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
sky2                   49317  0 

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:216  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

iwlist scan
```

eth1      20 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Channel:6

```

dmesg | grep wl
```

[    0.000000] DMI: Hewlett-Packard HP Mini 5103/1608, BIOS 68PGP Ver. F.02 10/20/2010
[   15.128226] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.316744] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.316782] wl 0000:01:00.0: setting latency timer to 64

```

---

### Post by praseodym on 2011-11-01
Which encryption mode do you use? Try WPA2-AES. Otherwise try Wicd instead of the NetworkManager

---

### Post by rbsmn on 2011-11-02
The router is configured as "TKIP and AES". I tried to set it as "AES only", but that didn't make the connection work any better: regardless of the cipher setting networkmanager says that I'm connected to the router, but there's no actual internet connection (tried with Firefox and ping).

I got a working wireless connection at work today, so the problems must be between my laptop and wireless router at home.

...as I'm writing this, the wireless connection has started working. I have no idea what could have happened. I had tried some other settings for the router (different encryptions) but since that seemed to have no effect, the router settings are back to what they originally were. So as far as I can tell, nothing is different from yesterday but wifi works now.

Thanks!

(Though I don't expect this to be the end of all troubles with this wifi card...)

---

