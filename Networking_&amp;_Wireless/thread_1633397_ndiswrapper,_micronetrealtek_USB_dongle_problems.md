---
title: "ndiswrapper, micronet/realtek USB dongle problems"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by duckling9 on 2010-11-29
[COLOR=#000000][FONT=Sans Serif]Hello
Thanks for the very informative ndiswrapper troubleshooting guide. However it doesn't seem to have fixed my problems, in trying to connect a Micronet usb dongle to my Dell desktop. There are some things I can't run the diagnostics on because when I plug my dongle in the system partially hangs. So it work run lshw -C network for example. And see below for some unhealthy looking outputs from /var/log/messages.

uname -r 2.6.32-26-generic

dmesg | grep ndiswrapper
[   28.307931] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   31.081961] usbcore: registered new interface driver ndiswrapper

ndiswrapper -l[/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif]WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif]net8187b : driver installed[/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif]    device (0BDA:8187) present (alternate driver: rtl8187)[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Sans Serif]lsusb
Bus 001 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter[/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif]
more /var/log/messages
Nov 29 12:37:11 duckling kernel: [ 1308.280038] usb 1-8: new high speed USB devi
ce using ehci_hcd and address 5
Nov 29 12:37:16 duckling kernel: [ 1313.431954] usb 1-8: configuration #1 chosen
 from 1 choice
Nov 29 12:37:16 duckling kernel: [ 1313.560043] usb 1-8: reset high speed USB de
vice using ehci_hcd and address 5
Nov 29 12:37:16 duckling kernel: [ 1313.753667] ndiswrapper (link_pe_images:575)
: fixing KI_USER_SHARED_DATA address in the driver
Nov 29 12:37:16 duckling kernel: [ 1313.756557] ndiswrapper: driver net8187b (Re
altek Semiconductor Corp.,04/15/2009,5.1160.0415.2009) loaded
Nov 29 12:37:17 duckling kernel: [ 1314.691882] wlan0: ethernet device 00:11:3b:
13:74:3f using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor:
 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0B
DA:8187.F.conf
Nov 29 12:37:17 duckling kernel: [ 1314.693111] wlan0: encryption modes supporte
d: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Nov 29 12:37:17 duckling kernel: [ 1314.742602] CPU 0 Nov 29 12:37:17 duckling kernel: [ 1314.742606] Modules linked in: binfmt_misc p
pdev parport_pc kvm_amd kvm snd_hda_codec_idt fbcon tileblit font bitblit softcu
rsor vga16fb vgastate snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixe
r_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_ev
ent snd_seq snd_timer snd_seq_device radeon ndiswrapper snd ttm drm_kms_helper d
ell_wmi dcdbas usbhid psmouse k8temp serio_raw edac_core edac_mce_amd soundcore snd_page_alloc drm i2c_algo_bit i2c_nforce2 lp parport hid usb_storage b44 ssb m
ii sata_nv
Nov 29 12:37:17 duckling kernel: [ 1314.742684] Pid: 806, comm: ntos_wq Tainted:
 P           2.6.32-26-generic #47-Ubuntu Dimension E521
Nov 29 12:37:17 duckling kernel: [ 1314.742690] RIP: 0010:[<ffffc90004d94abd>]  [<ffffc90004d94abd>] 0xffffc90004d94abd
Nov 29 12:37:17 duckling kernel: [ 1314.742703] RSP: 0018:ffff8800676af998  EFLA
GS: 00010202
Nov 29 12:37:17 duckling kernel: [ 1314.742707] RAX: 00000000000000ff RBX: ffffc
90004de6000 RCX: ffffc90004de6001
Nov 29 12:37:17 duckling kernel: [ 1314.742712] RDX: ffff880043602000 RSI: ffffc
90004991000 RDI: 0000000000000000
Nov 29 12:37:17 duckling kernel: [ 1314.742717] RBP: ffffc90004de6000 R08: ffffc
90005312024 R09: 0000000000000001
Nov 29 12:37:17 duckling kernel: [ 1314.742722] R10: ffffffffa0173a70 R11: ffff8
800676afc70 R12: ffffc90004de7398
Nov 29 12:37:17 duckling kernel: [ 1314.742727] R13: ffff880064703800 R14: ffffc
90005312024 R15: ffff8800676aff00
Nov 29 12:37:17 duckling kernel: [ 1314.742733] FS:  00007f4d05811700(0000) GS:f
fff880001c00000(0000) knlGS:00000000f694e760
Nov 29 12:37:17 duckling kernel: [ 1314.742739] CS:  0010 DS: 0018 ES: 0018 CR0:
 0000000080050033
Nov 29 12:37:17 duckling kernel: [ 1314.742743] CR2: 00007ff9212026c0 CR3: 00000
000462bf000 CR4: 00000000000006f0
Nov 29 12:37:17 duckling kernel: [ 1314.742748] DR0: 0000000000000000 DR1: 00000
00000000000 DR2: 0000000000000000
Nov 29 12:37:17 duckling kernel: [ 1314.742753] DR3: 0000000000000000 DR6: 00000
000ffff0ff0 DR7: 0000000000000400
Nov 29 12:37:17 duckling kernel: [ 1314.742759] Process ntos_wq (pid: 806, threa
dinfo ffff8800676ae000, task ffff880074895b80)
Nov 29 12:37:17 duckling kernel: [ 1314.742766]  0000000000015bc0 ffff8800676af9
e0 ffffffff81052b68 ffff880001c15c50
Nov 29 12:37:17 duckling kernel: [ 1314.742774] <0> 0000000000000000 ffff880001c
10000 ffff880043602000 ffff880066960018
Nov 29 12:37:17 duckling kernel: [ 1314.742782] <0> ffff88006696dbb8 ffff8800676
af9f0 ffffc90004991000 ffff8800676afa10
Nov 29 12:37:17 duckling kernel: [ 1314.742806]  [<ffffffff81052b68>] ? enqueue_
sleeper+0x158/0x220
Nov 29 12:37:17 duckling kernel: [ 1314.742817]  [<ffffffff8104baa6>] ? resched_
task+0x76/0x90
Nov 29 12:37:17 duckling kernel: [ 1314.742826]  [<ffffffff81061f98>] ? check_pr
eempt_wakeup+0x2b8/0x3c0
Nov 29 12:37:17 duckling kernel: [ 1314.742834]  [<ffffffff81059826>] ? try_to_w
ake_up+0x2e6/0x470
Nov 29 12:37:17 duckling kernel: [ 1314.742842]  [<ffffffff810599c2>] ? default_
wake_function+0x12/0x20
Nov 29 12:37:17 duckling kernel: [ 1314.742851]  [<ffffffff81084586>] ? autoremo
ve_wake_function+0x16/0x40
Nov 29 12:37:17 duckling kernel: [ 1314.742858]  [<ffffffff8104acc9>] ? __wake_u
p_common+0x59/0x90
Nov 29 12:37:17 duckling kernel: [ 1314.742865]  [<ffffffff810525e3>] ? __wake_u
p+0x53/0x70
Nov 29 12:37:17 duckling kernel: [ 1314.742873]  [<ffffffff8104b769>] ? wake_aff
ine+0x2e9/0x370
Nov 29 12:37:17 duckling kernel: [ 1314.742883]  [<ffffffff812b3143>] ? cpumask_
next_and+0x23/0x40
Nov 29 12:37:17 duckling kernel: [ 1314.742890]  [<ffffffff81052cc5>] ? select_i
dle_sibling+0x95/0x150
Nov 29 12:37:17 duckling kernel: [ 1314.742898]  [<ffffffff81052b68>] ? enqueue_
sleeper+0x158/0x220
Nov 29 12:37:17 duckling kernel: [ 1314.742944]  [<ffffffffa0181726>] ? win2lin1
+0xb/0xe [ndiswrapper]
Nov 29 12:37:17 duckling kernel: [ 1314.742951]  [<ffffffff81061ea4>] ? check_pr
eempt_wakeup+0x1c4/0x3c0
Nov 29 12:37:17 duckling kernel: [ 1314.742987]  [<ffffffffa0181737>] ? win2lin2
+0xe/0x11 [ndiswrapper]
Nov 29 12:37:17 duckling kernel: [ 1314.742994]  [<ffffffff81052890>] ? __dequeu
e_entity+0x30/0x50
Nov 29 12:37:17 duckling kernel: [ 1314.743022]  [<ffffffffa016a6dc>] ? mp_timer
_dpc+0x4c/0x70 [ndiswrapper]
Nov 29 12:37:17 duckling kernel: [ 1314.743030]  [<ffffffff810578b0>] ? finish_t
ask_switch+0x50/0xe0
Nov 29 12:37:17 duckling kernel: [ 1314.743063]  [<ffffffffa0181762>] ? win2lin4
+0x14/0x17 [ndiswrapper]
Nov 29 12:37:17 duckling kernel: [ 1314.743095]  [<ffffffffa017367c>] ? kdpc_wor
ker+0xec/0x170 [ndiswrapper]
Nov 29 12:37:17 duckling kernel: [ 1314.743126]  [<ffffffffa017365a>] ? kdpc_wor
ker+0xca/0x170 [ndiswrapper]
Nov 29 12:37:17 duckling kernel: [ 1314.743157]  [<ffffffffa0173590>] ? kdpc_wor
ker+0x0/0x170 [ndiswrapper]
Nov 29 12:37:17 duckling kernel: [ 1314.743167]  [<ffffffff8107f9a7>] ? run_work
queue+0xc7/0x1a0
Nov 29 12:37:17 duckling kernel: [ 1314.743175]  [<ffffffff8107fb23>] ? worker_t
hread+0xa3/0x110
Nov 29 12:37:17 duckling kernel: [ 1314.743183]  [<ffffffff81084570>] ? autoremo
ve_wake_function+0x0/0x40
Nov 29 12:37:17 duckling kernel: [ 1314.743190]  [<ffffffff8107fa80>] ? worker_t
hread+0x0/0x110
Nov 29 12:37:17 duckling kernel: [ 1314.743197]  [<ffffffff810841f6>] ? kthread+
0x96/0xa0
Nov 29 12:37:17 duckling kernel: [ 1314.743205]  [<ffffffff810131ea>] ? child_ri
p+0xa/0x20
Nov 29 12:37:17 duckling kernel: [ 1314.743212]  [<ffffffff81084160>] ? kthread+
0x0/0xa0
Nov 29 12:37:17 duckling kernel: [ 1314.743217]  [<ffffffff810131e0>] ? child_ri
p+0x0/0x20
Nov 29 12:37:17 duckling kernel: [ 1314.743289]  RSP <ffff8800676af998>
Nov 29 12:37:17 duckling kernel: [ 1314.743320] ---[ end trace 2a0297359af0366a ]---
Nov 29 12:37:17 duckling kernel: [ 1314.774003] ADDRCONF(NETDEV_UP): wlan0: link
 is not ready



I've been trying for weeks to get this working, so any thoughts gratefully received!
thanks
d[/FONT][/COLOR]

---

### Post by Joe of loath on 2010-11-29
Which dongle is it? I bought a micronet one with the RTL8187B chipset which works out of the box on Ubuntu.

---

### Post by chili555 on 2010-11-29
> ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8187b : driver installed
device (0BDA:8187) present (alternate driver: rtl8187)I'd love to see your tests again with rtl8187 properly blacklisted:```
sudo su
mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
rmmod -f rtl8187
echo "blacklist rtl8187" >> /etc/modprobe.d/blacklist.conf
exit
```Thanks.

---

### Post by duckling9 on 2010-11-29
@Joe: the dongle is a micronet SP907GK v6. What was yours?

---

### Post by duckling9 on 2010-11-29
@Chilli555
Thanks. I have blacklisted the rtl8187 as you suggest but it still hangs

> ndiswrapper -l
net8187b : driver installed
    device (0BDA:8187) present (alternate driver: rtl8187)

var/log/messages still gives me lots of errors that ends in:
Nov 29 14:55:15 duckling kernel: [  519.263293]  RSP <ffff8800670b1998>
Nov 29 14:55:15 duckling kernel: [  519.263300] ---[ end trace f34e21628ebac203
]---
Nov 29 14:55:15 duckling kernel: [  519.295173] ADDRCONF(NETDEV_UP): wlan0: link
 is not ready

---

### Post by Joe of loath on 2010-11-29
The very same.

---

### Post by duckling9 on 2010-11-29
@ Joe.
!!
Are you running a 64 bit kernel? (I am) Perhaps this makes a difference? Maybe I  should kill ndiswrapper and try to get rtl8187 to work? Not sure how though...
The dongle works under windows, so its not completely stuffed.
J

---

### Post by Joe of loath on 2010-11-29
I'm on Arch at the moment, but it works with the x86_64 kernel on here.

Remove ndiswrapper and try, and if that doesn't work, try it on a liveCD.

---

### Post by duckling9 on 2010-11-29
I would like to try to disable ndiswrapper, and to use whatever it is that works out of the box for you, Joe, but I'm not sure how to do this. I'm probably missing something straightforward, but don't know what.

I've done
ndiswrapper -r net8187b
and have rebooted

I have 
> lsusb
Bus 001 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

but I now don't see any wireless device.
```

> iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

```

there's also nothing I can see relevant in lsmod
```

Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
parport_pc             29958  0 
kvm_amd                36942  0 
kvm                   285887  1 kvm_amd
snd_hda_codec_idt      61450  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25741  2 
snd_hda_codec          85759  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                742816  2 
usbhid                 41116  0 
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hid                    83472  1 usbhid
ttm                    60847  1 radeon
drm_kms_helper         30742  1 radeon
snd                    71251  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           244832  0 
dell_wmi                2177  0 
psmouse                64576  0 
dcdbas                  6886  0 
serio_raw               4918  0 
drm                   198948  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon
k8temp                  4040  0 
edac_core              45423  0 
edac_mce_amd            9278  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_nforce2             6099  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usb_storage            49961  0 
b44                    30687  0 
ssb                    45395  1 b44
mii                     5237  1 b44
sata_nv                23714  6 

```
weirdly ssb claims to be blacklisted in /etc/modprobe.d/blacklist.conf, but it still appears in lsmod??

---

### Post by Joe of loath on 2010-11-29
I think you've overcomplicated things here, mine simply worked when I plugged it in, no configuration necessary. Try uninstalling ndiswrapper, setting your blacklist back to how it was before etc.

---

### Post by duckling9 on 2010-11-29
Joe,
Unfortunately mine doesn't work just like this. I don't know what else I'm meant to do, but it doesn't. As I said, I have also rebooted after editing blacklist and removing the driver from ndiswrapper. The relevant modules are not loaded & i don't see the wireless interface....

d

---

### Post by chili555 on 2010-11-29
Please try:```
sudo modprobe rtl8187
iwconfig
```Now do you have a wireless interface? If not, let's see what's happening:```
dmesg | grep rtl8187
```Thanks.

---

### Post by duckling9 on 2010-12-04
chilli555 - thanks I've been away for a bit but now am back trying to figure it out again!

I've removed the ndiswrapper net8187b driver.
I've insmod rtl8187
and can see a wireless network, but can't connect

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```

dmesg indeed shows some problems....
```

dmesg | grep 8187

[   30.706389] rtl8187: inconsistency between id with OEM info!
[   30.780869] phy0: hwaddr 00:11:3b:13:74:3f, RTL8187BvB(early) V0 + rtl8225z2, rfkill mask 2
[   30.802389] rtl8187: Customer ID is 0xFF
[   30.802443] Registered led device: rtl8187-phy0::tx
[   30.802461] Registered led device: rtl8187-phy0::rx
[   30.803509] rtl8187: wireless switch is on
[   30.803551] usbcore: registered new interface driver rtl8187


```

thanks for your continued help.
d

---

### Post by chili555 on 2010-12-04
> rtl8187: wireless switch is onPlease post:```
rfkill list all
```> rtl8187: inconsistency between id with OEM info!
This is bothersome but I am not sure of it's exact significance. I am googling and have not yet found an answer. Let's dig deeper:```
sudo cat /var/log/syslog | grep 8187
```Thanks.

---

### Post by duckling9 on 2010-12-04
i also tried some googling on the oem info line - but rapidly decided that I didn't know remotely enough to understand!
Here's the output of your suggested diagnostics:

```

dt@duckling:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

and

```


sudo cat /var/log/syslog | grep 8187

Dec  4 13:38:10 duckling kernel: [   30.706389] rtl8187: inconsistency between id with OEM info!
Dec  4 13:38:10 duckling kernel: [   30.780869] phy0: hwaddr 00:11:3b:13:74:3f, RTL8187BvB(early) V0 + rtl8225z2, rfkill mask 2
Dec  4 13:38:10 duckling kernel: [   30.802389] rtl8187: Customer ID is 0xFF
Dec  4 13:38:10 duckling kernel: [   30.802443] Registered led device: rtl8187-phy0::tx
Dec  4 13:38:10 duckling kernel: [   30.802461] Registered led device: rtl8187-phy0::rx
Dec  4 13:38:10 duckling kernel: [   30.803509] rtl8187: wireless switch is on
Dec  4 13:38:10 duckling kernel: [   30.803551] usbcore: registered new interface driver rtl8187
Dec  4 13:38:14 duckling NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rtl8187')

```

---

### Post by duckling9 on 2010-12-04
should i try compiling/using this?
[http://ubuntuforums.org/showthread.php?t=1446894](http://ubuntuforums.org/showthread.php?t=1446894)
if so, how?

(not sure whether this is later or older than the one compiled in my current kernel)

this was suggested as a solution to a similar array of problems :[http://www.spinics.net/lists/linux-wireless/msg48773.html](http://www.spinics.net/lists/linux-wireless/msg48773.html) , though it is not recorded if it solved the problem.

d

---

### Post by chili555 on 2010-12-04
There is nothing obvious in there that needs fixing; that's good news.> and can see a wireless network, but can't connectWhat happens when you click the Network Manager icon and try to connect? Does it ask for the encryption key? Have you detached the ethernet cable before you try to connect with wireless?

---

### Post by chili555 on 2010-12-04
> **duckling9 said:**
> should i try compiling/using this?
[http://ubuntuforums.org/showthread.php?t=1446894](http://ubuntuforums.org/showthread.php?t=1446894)
if so, how?

(not sure whether this is later or older than the one compiled in my current kernel)

this was suggested as a solution to a similar array of problems :[http://www.spinics.net/lists/linux-wireless/msg48773.html](http://www.spinics.net/lists/linux-wireless/msg48773.html) , though it is not recorded if it solved the problem.

dIt's a bit old; let's hold that for Plan B:> Release date = 2009-11-12
Operating system release = REDHAT 9/OPENSUSE 11/[COLOR="Red"]ubuntu9.04[/COLOR]
Kernel version = 2.4.20-8smp/2.4.31/2.6.25.5-1/2.6.28/2.6.31
Release driver version = 1056.1112.2009
Change history = 1. Setup "ChannelPlan" by calling userspace program "ChannelPlanBin" for Toshiba.
		 2. Add WG111v3 VID/PID, VID=0846, PID=4260
		 3. [COLOR="Red"]Update to kernel 2.6.31-14[/COLOR].For reference, we are now at kernel version 2.6.35, if you are running Ubuntu 10.10.

---

### Post by duckling9 on 2010-12-04
> What happens when you click the Network Manager icon and try to connect? 
um... looks a bit sheepish ... where do i find that?
i have installed wcid, but don't see anything called networkmanager?

wcid tells me that it can't get an ip address. or it tells me that the password is wrong (it isn't, i've asked for a sanity check from a third party observer!)  These were similar errors to those observed on post cited above. i have both physically disconnected eth cable, and not but used wcid to disconnect - no difference in wireless outcome.

d

---

### Post by chili555 on 2010-12-04
> i have installed wcid, but don't see anything called networkmanager?That's as it should be. Wicd is a replacement for Network Manager, so you should not find both.

You might look at:```
sudo less /var/log/wicd/wicd.log
```Scroll back and forth with the arrow keys and tell us what you see that's suspicious. 

Is your router set up with WPA or WPA2 or the troublesome mixed WPA and WPA2 mode? I'd suggest WPA2 and not mixed mode.

---

### Post by duckling9 on 2010-12-04
I'm using WEP rather than WPA. Is this a problem?

it says

attempting to set hostname with dhclient
2010/12/04 13:50:13 :: using dhcpcd or another supported client may work better

so I've installed dhcpcd but it doesn't yet show as an option in wcid. am rebooting and see how that works....

---

### Post by chili555 on 2010-12-04
> I'm using WEP rather than WPA. Is this a problem?Not at all.> am rebooting and see how that works.... Excellent, we're anxiously waiting.

How many characters in your WEP key? If there are letters, did you try both upper and lower-case?

---

### Post by duckling9 on 2010-12-04
Sigh.
What can I say - it apparently connected, then it disconnected. Then I tried again, then it complained of bad password. I tried again, it didn't validate the IP. Then the whole machine hung and I had to hard reboot. I've tried again various times, and don't seem to get anything particularly replicable.

What can I tell you, so you could help me find a way out of this mess... or is it simply time to realise that I'm stuck with ethernet cables draped around my house?
d

---

### Post by duckling9 on 2010-12-04
My WEP is 10 hex letters. Yes, I've tried both cases - but you'll see from the above post, that random behaviour doesn't seem related to my password!

---

### Post by chili555 on 2010-12-04
> What can I tell you, so you could help me find a way out of this mess... or is it simply time to realise that I'm stuck with ethernet cables draped around my house?No ethernet!

It sounds like you have a deeper systemic problem. Maybe we can troubleshoot. Let's have a look at your last two sets of kernel messages and see if there's a clue in there. Run these commands one at a time right after each other; a text file will be created and we'll zip it so you can attach it to your reply. I and hopefully others will examine it to look for errors.```
dmesg > duck.txt
sudo cat /var/log/dmesg.0 >> duck.txt
zip duck.zip duck.txt
```Attach the file duck.zip to your reply using the paperclip tool above the reply box.

---

### Post by duckling9 on 2010-12-19
hello,
again sorry for silence. i had given up in frustration for a bit (this is the third serious attempt i've had to fix this!)

now, i think i have a working system with the USB dongle attached to socket in the front  of the machine, which is great and will do. (I was trying to use the one in the back - the signal is apparently 60%+ and it works for windows, but won't work under linux - who knows why)

In any case I have a working system, so thanks very much for your help - it was really appreciated and gave me the strength to keep trying to fix it!!

---

