---
title: "Cannot connect to network using Linksys Wusb600n v2"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by daGrevis on 2011-07-16
Hey there, guys!

After several hours of failure, I decided to ask for help!

My OS is Linux Xubuntu 11.04 (32 bits) and I'm trying to get Linksys Wusb600n network adapter to work.

I followed [**this post**]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/#post3940804") and did all that was written in it... almost. When i came to blacklisting, I blacklisted all drivers that starts with rt**x** (where **x** is any digit). Here are lines that I pasted in *blacklist.conf*:

```
blacklist rt2860sta
blacklist rt2870sta
blacklist rt2x00usb
blacklist rt2500usb
blacklist rt73usb
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
blacklist rt2800lib
blacklist rt2400pci
blacklist rt2500pci
blacklist rt61pci
blacklist rt2800pci
blacklist rt2500usb
blacklist rt73usb
blacklist rt2800usb
```

Here are some additional info that may help you, guys:

```
dagrevis@dagrevis:~$ sudo iwconfig 
[sudo] password for dagrevis: 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dagrevis@dagrevis:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1737:0079 Linksys WUSB600N Wireless-N USB Network Adapter with Dual-Band ver. 2
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dagrevis@dagrevis:~$ uname -r
2.6.38-8-generic
```

**The problem:** I do see all available networks. So I guess... it somehow works. Anyway, problem is that it does not connect successfully to my network.

I click on it - it asks my password. I enter it and click 'Connect'. Nothing, except that network icon is started to like spin around (trying to connect, I guess), happens. After few minutes, it asks for password.... again. I enter it and all starts from the beginning. Its like a loop!

[[IMG]http://i.imgur.com/huuzy.jpg[/IMG]](http://imgur.com/huuzy)


Note: I don't have any other things installed except *linux-firmware-nonfree_1.9_all.deb* and, don't know how successfully, but [*RT3572USB 2.5.0.0*]("http://www.ralinktech.com/support.php?s=2").

---

### Post by daGrevis on 2011-07-16
Oh my God, guys! Oh my God!!

I just followed [Comment 85 for bug 408165]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165/comments/85") and all works! Automagically.:D:D

---

### Post by fubofo on 2012-02-22
Hey, just wondering if you got this working on Ubuntu 11.10 ? (kernel 3.*)

EDIT: nevermind, got it working

---

### Post by kittkatt on 2012-02-23
> Hey, just wondering if you got this working on Ubuntu 11.10 ? (kernel 3.*)

EDIT: nevermind, got it working 

How did you get it working?  I'm using 3.2.0-16-generic and although its supposed to work natively and I've loaded the rt2x00usb module, I can't get wlan0 up.  I only have eth0 and lo

---

### Post by fubofo on 2012-02-23
Hey kittkatt,

check my other post, I made a full guide to follow (and a quick and dirty copy-paste method at the end) ;)

[http://ubuntuforums.org/showthread.php?p=11711811#post11711811](http://ubuntuforums.org/showthread.php?p=11711811#post11711811)

---

### Post by kittkatt on 2012-03-03
> Hey kittkatt,

check my other post, I made a full guide to follow (and a quick and dirty copy-paste method at the end) 

[http://ubuntuforums.org/showthread.p...1#post11711811](http://ubuntuforums.org/showthread.p...1#post11711811)

Tried this, and does not work with 11.10 + 3.2.0-16-generic.  

```
[    6.294994] BUG: unable to handle kernel paging request at 2b5d3f20
[    6.294998] IP: [<f89fd97f>] MainVirtualIF_open+0x4f/0x120 [rt3572sta]
[    6.295012] *pde = 00000000 
[    6.295014] Oops: 0002 [#1] SMP 
[    6.295017] Modules linked in: hid_logitech_dj snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel rt3572sta(O) snd_hda_codec snd_seq_midi snd_rawmidi snd_seq_midi_event snd_hwdep snd_pcm snd_seq joydev psmouse nvidia(P) ppdev serio_raw binfmt_misc snd_seq_device mac_hid snd_timer k10temp snd parport_pc wmi soundcore sp5100_tco i2c_piix4 snd_page_alloc lp parport usbhid usb_storage hid vesafb firewire_ohci firewire_core crc_itu_t floppy r8169 ati_agp pata_atiixp
[    6.295038] 
[    6.295041] Pid: 1027, comm: NetworkManager Tainted: P           O 3.2.0-16-generic #25-Ubuntu Gigabyte Technology Co., Ltd. GA-MA770-UD3/GA-MA770-UD3
[    6.295045] EIP: 0060:[<f89fd97f>] EFLAGS: 00010293 CPU: 1
[    6.295055] EIP is at MainVirtualIF_open+0x4f/0x120 [rt3572sta]
[    6.295057] EAX: f5dabf20 EBX: f663f800 ECX: f886e100 EDX: 00000296
[    6.295058] ESI: f886e000 EDI: 00000000 EBP: f679db3c ESP: f679db28
[    6.295060]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[    6.295062] Process NetworkManager (pid: 1027, ti=f679c000 task=f5c5bf20 task.ti=f679c000)
[    6.295063] Stack:
[    6.295064]  00000000 00000000 f663f800 f800e000 00000000 f679db58 c147b583 c1573746
[    6.295069]  f679db58 c147b4ee f663f800 00001003 f679db80 c147b7f2 00000000 00000000
[    6.295073]  00000000 00001002 00000001 f663f800 f5ca0610 00001002 f679db94 c147b961
[    6.295077] Call Trace:
[    6.295082]  [<c147b583>] __dev_open+0x83/0xd0
[    6.295086]  [<c1573746>] ? _raw_spin_unlock_bh+0x16/0x20
[    6.295088]  [<c147b4ee>] ? dev_set_rx_mode+0x2e/0x40
[    6.295091]  [<c147b7f2>] __dev_change_flags+0x82/0x150
[    6.295093]  [<c147b961>] dev_change_flags+0x21/0x60
[    6.295095]  [<c1485aaf>] do_setlink+0x22f/0x6f0
[    6.295099]  [<c12af346>] ? nla_parse+0x66/0xa0
[    6.295102]  [<c11233d5>] ? __kmalloc_track_caller+0x185/0x1d0
[    6.295104]  [<c1485f70>] ? do_setlink+0x6f0/0x6f0
[    6.295106]  [<c1486027>] rtnl_setlink+0xb7/0x110
[    6.295110]  [<c15724b8>] ? mutex_lock+0x18/0x40
[    6.295112]  [<c14871fe>] rtnetlink_rcv_msg+0x13e/0x270
[    6.295114]  [<c1120c5a>] ? kmem_cache_free+0xea/0x100
[    6.295116]  [<c146ca2e>] ? kfree_skbmem+0x2e/0x80
[    6.295118]  [<c14870c0>] ? __rtnl_unlock+0x20/0x20
[    6.295122]  [<c149c8ce>] netlink_rcv_skb+0x8e/0xb0
[    6.295125]  [<c14855dc>] rtnetlink_rcv+0x1c/0x30
[    6.295127]  [<c149c2a9>] netlink_unicast+0x239/0x290
[    6.295130]  [<c149c4e8>] netlink_sendmsg+0x1e8/0x310
[    6.295133]  [<c14658a7>] sock_sendmsg+0xf7/0x120
[    6.295135]  [<c14658a7>] ? sock_sendmsg+0xf7/0x120
[    6.295137]  [<c157364d>] ? _raw_spin_lock+0xd/0x10
[    6.295141]  [<c12a268f>] ? __copy_from_user_ll+0x1f/0x40
[    6.295143]  [<c12a2822>] ? _copy_from_user+0x42/0x60
[    6.295146]  [<c1470b54>] ? verify_iovec+0x44/0xb0
[    6.295148]  [<c146680a>] __sys_sendmsg+0x24a/0x260
[    6.295151]  [<c129c2e4>] ? rb_erase+0xb4/0x120
[    6.295153]  [<c1001d40>] ? __switch_to+0xf0/0x1a0
[    6.295156]  [<c103a481>] ? finish_task_switch+0x41/0xc0
[    6.295159]  [<c1467dab>] sys_sendmsg+0x3b/0x60
[    6.295161]  [<c1468433>] sys_socketcall+0x263/0x2c0
[    6.295164]  [<c157af7b>] ? do_IRQ+0x4b/0xc0
[    6.295166]  [<c1573a24>] syscall_call+0x7/0xb
[    6.295168] Code: f4 8b 75 f8 8b 7d fc 89 ec 5d c3 90 8b 46 08 85 c0 74 59 83 c0 01 89 46 08 83 3d 80 21 a3 f8 02 0f 84 ab 00 00 00 a1 f0 22 a3 f8 <64> ff 00 a1 c8 5f 82 c1 85 c0 75 6e 8b 83 00 02 00 00 f0 80 60 
[    6.295191] EIP: [<f89fd97f>] MainVirtualIF_open+0x4f/0x120 [rt3572sta] SS:ESP 0068:f679db28
[    6.295200] CR2: 000000002b5d3f20
[    6.295202] ---[ end trace 391ae02c82c33852 ]---
[    6.420617] audit_printk_skb: 27 callbacks suppressed
[    6.420620] type=1400 audit(1330819561.113:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1291 comm="apparmor_parser"
[    6.421064] type=1400 audit(1330819561.113:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1291 comm="apparmor_parser"
[    7.141424] r8169 0000:03:00.0: eth0: link up
[    7.666909] init: plymouth-upstart-bridge main process (911) killed by TERM signal

```

```
Linux:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
dm_crypt               22559  0 
hid_logitech_dj        18178  0 
snd_hda_codec_hdmi     31806  4 
snd_hda_codec_realtek   174009  1 
snd_hda_intel          32765  3 
rt3572sta             626527  0 [permanent]
snd_hda_codec         109534  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi           13132  0 
snd_rawmidi            25455  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
joydev                 17393  0 
psmouse                87140  0 
nvidia              10937322  42 
ppdev                  12849  0 
serio_raw              13027  0 
binfmt_misc            17292  1 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
snd_timer              28932  2 snd_seq,snd_pcm
k10temp                12990  0 
snd                    62065  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
parport_pc             32114  1 
wmi                    18744  0 
soundcore              14635  1 snd
sp5100_tco             13495  0 
i2c_piix4              13093  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  1 hid_logitech_dj
usb_storage            39647  2 
hid                    77367  2 hid_logitech_dj,usbhid
vesafb                 13489  1 
firewire_ohci          40180  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 60310  0 
r8169                  56321  0 
ati_agp                13242  0 
pata_atiixp            12999  1 
```

---

