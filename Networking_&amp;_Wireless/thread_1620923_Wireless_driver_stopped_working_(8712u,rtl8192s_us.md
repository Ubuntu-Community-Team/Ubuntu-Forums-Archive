---
title: "Wireless driver stopped working (8712u,rtl8192s_usb)"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by bosbeemer on 2010-11-13
I have a Realtek USB Wireless-N dongle that was working fine until a week back. Realtek Customer support had emailed me the driver that I compiled and installed. The driver that worked fine was 8712u.

After an update about a month back some restricted driver was installed. After that update on every boot I had to manually remove the driver r8192s_usb and reinsert the usb dongle to get it to use 8712u.

However even that stopped working today. I have no idea what changed. In the past few hours I have followed every advise on every forum on this topic, but to no avail. 

The r8192s_usb driver is loaded every time I insert the dongle. 8712u driver is not at all recognized by the dongle even after I remove r8192s_usb.

Thanks for all the help.
```

lsusb

Bus 002 Device 011: ID 0bda:8192 Realtek Semiconductor Corp.

dmesg | tail

Nov 13 15:40:18 emachine kernel: [ 3260.189164] usb 2-4: USB disconnect, address 11
Nov 13 15:40:18 emachine kernel: [ 3260.189975] read_nic_byte TimeOut! status:-19
Nov 13 15:40:18 emachine kernel: [ 3260.189977] write_nic_byte TimeOut! status:-19
Nov 13 15:40:18 emachine kernel: [ 3260.200132] =====>rtl8192SU_link_change 1
Nov 13 15:40:18 emachine kernel: [ 3260.200135] read_nic_dword TimeOut! status:-19
Nov 13 15:40:18 emachine kernel: [ 3260.200137] write_nic_dword TimeOut! status:-19
Nov 13 15:40:18 emachine kernel: [ 3260.200139] read_nic_byte TimeOut! status:-19
Nov 13 15:40:18 emachine kernel: [ 3260.200141] write_nic_byte TimeOut! status:-19
Nov 13 15:40:18 emachine kernel: [ 3260.200142] <=====rtl8192SU_link_change 2





Nov 13 15:40:28 emachine kernel: [ 3269.630031] usb 2-4: new full speed USB device using ohci_hcd and address 12
Nov 13 15:40:28 emachine kernel: [ 3269.842327] usb 2-4: not running at top speed; connect to a high speed hub
Nov 13 15:40:28 emachine kernel: [ 3269.852458] usb 2-4: configuration #1 chosen from 1 choice
Nov 13 15:40:28 emachine kernel: [ 3269.866681] ==>ep_num:6, in_ep_num:1, out_ep_num:5
Nov 13 15:40:28 emachine kernel: [ 3269.866685] ==>RtInPipes:3  
Nov 13 15:40:28 emachine kernel: [ 3269.866687] ==>RtOutPipes:4  5  6  7  13  
Nov 13 15:40:28 emachine kernel: [ 3269.866691] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
Nov 13 15:40:28 emachine kernel: [ 3269.866693] 3  2  1  0  4  4  4  4  4  
Nov 13 15:40:28 emachine kernel: [ 3269.896329] Dot11d_Init()
Nov 13 15:40:28 emachine kernel: [ 3269.905054] udev: renamed network interface wlan0 to wlan1
Nov 13 15:40:28 emachine kernel: [ 3269.998345] usb 2-4: firmware: requesting RTL8192SU/rtl8192sfw.bin
Nov 13 15:40:33 emachine kernel: [ 3274.473004] ADDRCONF(NETDEV_UP): wlan1: link is not ready


```

---

### Post by bosbeemer on 2010-11-16
I am on kernel 2.6.32-25-generic. Does anyone at least know what driver is needed for the usb dongle? As mentioned above ```
 lsusb 
``` output gives a device id of ```
 obda:8192 
```. The driver in the kernel staging area ```
 r8192s_usb 
``` definitely doesn't work. It loads fine when the device the inserted, however it is unable to connect to any network.

---

### Post by chili555 on 2010-11-16
If you installed a new kernel, or linux-image, as a result of an update, you'd need to recompile the 8172u driver; something like:```
cd DownloadDirectory/rtl8172ublahblah
make clean 
make
sudo make install
```Then I'd blacklist 8192s_usb and add 8172u to /etc/modules.

You seem pretty capable, so I haven't explained all this in detail; post back if you need additional guidance.

---

### Post by bosbeemer on 2010-11-16
For sure I compiled and compiled again. After I blacklist r8192s_usb, nothing happens on inserting the usb stick. I load the 8712u driver manually using modprobe and still nothing. It's almost as if the driver is no longer associated with the card.

What  all locations should I look at to make sure that everything is where it should be?

Chili555, I have read all your posts I could. Thanks a lot for helping out on the Ubuntu forums.

---

### Post by chili555 on 2010-11-16
> Bus 002 Device 011: ID [COLOR="Red"]0bda:8192[/COLOR] Realtek Semiconductor Corp.

Does your usb.id show up in 8172u?```
modinfo 8172u | grep 8192
```I wonder if your device doesn't actually work with r8192[COLOR="Red"]u[/COLOR]_usb.> modinfo r8192u_usb | grep 8192
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
alias:          usb:v[COLOR="Red"]0BDA[/COLOR]p[COLOR="Red"]8192[/COLOR]d*dc*dsc*dp*ic*isc*ip*Thank you for your kind comments.

---

### Post by Cariboo1938 on 2010-11-16
May I join the circle, also I'm not that literate in software/programming.
**[SIZE="2"]Facts:[/SIZE]** 
- OS 
-->Ubuntu 10.04-amd64

- uname -a 
--->2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux

- lsusb
--->...
Bus 001 Device 007: ID 0bda:8172 Realtek Semiconductor Corp.
...
According to Realtek the hardware ID 0bda:8172 is Realtek RTL8191SU chip set. The driver is "RTL8191SU Linux Version 0006.20100625".

- Driver downloaded from Realtek as recommended 
--->Please download RTL8191SU Linux driver source from below URL.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SU)

- Driver installation according to the directions given [HERE.]("http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html") 

- dmesg | tail 
---> 640099] Dot11d_Init()
[34574.693651] rtl819xU: --->FirmwareDownload92S()
[34574.693656] 
[34574.693667] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[34574.760989] rtl819xU:request firmware fail!
[34574.760993] 
[34574.761253] rtl819xU:Firmware Download Fail!!a
[34574.761258] 
[34574.773563] rtl819xU: --->FirmwareDownload92S()
[34574.773567] 
[34574.773577] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[34574.777067] rtl819xU:request firmware fail!
[34574.777070] 
[34574.778418] rtl819xU:Firmware Download Fail!!a
[34574.778421] 
[34574.778428] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[34574.778431] 
[34574.812466] rtl819xU: --->FirmwareDownload92S()
[34574.812471] 
[34574.812482] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[34574.816047] rtl819xU:request firmware fail!
[34574.816051] 
[34574.816787] rtl819xU:Firmware Download Fail!!a
[34574.816790] 
[34574.835897] rtl819xU: --->FirmwareDownload92S()
[34574.835901] 
[34574.835911] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[34574.844126] rtl819xU:request firmware fail!
[34574.844129] 
[34574.844828] rtl819xU:Firmware Download Fail!!a
[34574.844833] 
[34574.844842] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[34574.844

- modinfo 8172u | grep 8192
--->ERROR: modinfo: could not find module 8172u

**[SIZE="2"]Issue:[/SIZE]**

- USB wireless adapter dongle TRENDnet TEW-649UB is not working.
 
What did I do wrong?
Help please!:confused:

---

### Post by chili555 on 2010-11-16
> [34574.773577] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[34574.777067] rtl819xU:request firmware fail!You probably have the firmware but in the wrong place. Here is where it is on my system:> /lib/firmware/RTL8192[COLOR="Red"]SE[/COLOR]/rtl8192sfw74.binHowever, your system is looking for it in RTL8192[COLOR="Red"]SU[/COLOR]. Let's just copy it over.```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw74.bin /lib/firmware/RTL8192SU

```> --->ERROR: modinfo: could not find module 8172u
The module you built is **8712u**, not 8172u. The usb.id you are looking for is 0bda:8172. Crazy, eh?>  modinfo 8712u | grep 8172
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*Let's unload and reload the module and see if it grabs your firmware:```
sudo rmmod -f 8712u
sudo modprobe 8712u
```Is your wireless working? If not, see what dmesg says after [34574.844842] and post it.

---

### Post by Cariboo1938 on 2010-11-16
Hello chili555!
Thank you so much for your immediate and detailed response :) 

> Is your wireless working?
No, not yet! Here is my dmesg printout...

> [34574.844833] 
[34574.844842] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[34574.844845] 
[46864.901894] +r8712u_drv_halt
[46864.901902] usbcore: deregistering interface driver r871x_usb_drv
[46864.901967] -r8712u_drv_halt
[46891.265698] usbcore: registered new interface driver r871x_usb_drv
[46959.742197] usb 1-4.4: USB disconnect, address 7
[46959.790082] rtl819xU:=============>wlan driver to be removed
[46959.790088] 
[46959.802308] rtl819xU:wlan driver removed
[46959.802310] 
[46983.210596] usb 1-4.4: new high speed USB device using ehci_hcd and address 8
[46983.323125] usb 1-4.4: configuration #1 chosen from 1 choice
[46983.324489] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[46983.324494] ==>RtInPipes:3  
[46983.324500] ==>RtOutPipes:4  6  13  
[46983.324508] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[46983.324513] 1  1  0  0  2  2  2  2  2  
[46983.590741] Dot11d_Init()
[46983.621263] rtl819xU: --->FirmwareDownload92S()
[46983.621268] 
[46983.621279] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[46983.655158] rtl819xU:request firmware fail!
[46983.655161] 
[46983.655572] rtl819xU:Firmware Download Fail!!a
[46983.655575] 
[46983.666722] rtl819xU: --->FirmwareDownload92S()
[46983.666729] 
[46983.666739] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[46983.672632] rtl819xU:request firmware fail!
[46983.672636] 
[46983.673212] rtl819xU:Firmware Download Fail!!a
[46983.673215] 
[46983.673221] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[46983.673224] 
[46983.692249] rtl819xU: --->FirmwareDownload92S()
[46983.692252] 
[46983.692257] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[46983.694435] rtl819xU:request firmware fail!
[46983.694436] 
[46983.694983] rtl819xU:Firmware Download Fail!!a
[46983.694986] 
[46983.706251] rtl819xU: --->FirmwareDownload92S()
[46983.706254] 
[46983.706261] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[46983.708380] rtl819xU:request firmware fail!
[46983.708382] 
[46983.709500] rtl819xU:Firmware Download Fail!!a
[46983.709503] 
[46983.709507] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[46983.709509] 
karibu@karibu-desktop:/lib/firmware$ 

Do you need any other information?

---

### Post by chili555 on 2010-11-16
Let's see:```
ls -al /lib/firmware/RTL8192SU
```Thanks.

---

### Post by Cariboo1938 on 2010-11-16
> **chili555 said:**
> Let's see:```
ls -al /lib/firmware/RTL8192SU
```Thanks.

karibu@karibu-desktop:~$ ls -al /lib/firmware/RTL8192SU
total 108
drwxr-xr-x  2 root root  4096 2010-11-16 12:38 .
drwxr-xr-x 49 root root 16384 2010-11-16 12:37 ..
-rw-r--r--  1 root root 89616 2010-11-16 12:38 rtl8192sfw74.bin
karibu@karibu-desktop:~$

---

### Post by chili555 on 2010-11-16
It ought to work just fine, let's try a reboot. Then:```
dmesg | grep -e 819 -e 8712
```Thanks.

---

### Post by Cariboo1938 on 2010-11-16
> **chili555 said:**
> It ought to work just fine, let's try a reboot. Then:```
dmesg | grep -e 819 -e 8712
```Thanks.
\Thanks for the trouble. After restart 
- System hangs
- Screen black
- Keyboard dead lock
- Mouse dead lock
only way out; Hardware reset. Then:
karibu@karibu-desktop:~$ dmesg | grep -e 819 -e 8712
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u262144
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u262144 alloc=1*2097152
[    0.000000] Memory: 1781944k/1834560k available (5420k kernel code, 452k absent, 52164k reserved, 2974k data, 872k init)
[    0.356819] usbcore: registered new interface driver usbfs
[    0.815819] cpuidle: using governor ladder
[    9.223068] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[    9.230195] Linux kernel driver for RTL8192 based WLAN cards
[    9.491976] usbcore: registered new interface driver rtl819xU
[   10.638008] rtl819xU: --->FirmwareDownload92S()
[   10.638015] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   10.730936] rtl819xU:request firmware fail!
[   10.731350] rtl819xU:Firmware Download Fail!!a
[   10.743267] rtl819xU: --->FirmwareDownload92S()
[   10.743281] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   10.745232] rtl819xU:request firmware fail!
[   10.746593] rtl819xU:Firmware Download Fail!!a
[   10.746597] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   10.782248] rtl819xU: --->FirmwareDownload92S()
[   10.782256] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   10.788740] rtl819xU:request firmware fail!
[   10.789487] rtl819xU:Firmware Download Fail!!a
[   10.800770] rtl819xU: --->FirmwareDownload92S()
[   10.800777] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   10.824525] rtl819xU:request firmware fail!
[   10.825247] rtl819xU:Firmware Download Fail!!a
[   10.825251] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
karibu@karibu-desktop:~$

---

### Post by chili555 on 2010-11-16
> r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.As I mentioned previously, you need to blacklist r8192s_usb. Please do:```
sudo su
echo "blacklist r8192s_usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and run the tests again.```
dmesg | grep -e 819 -e 8712
```

---

### Post by bosbeemer on 2010-11-16
> **chili555 said:**
> Does your usb.id show up in 8172u?```
modinfo 8172u | grep 8192
```I wonder if your device doesn't actually work with r8192[COLOR=Red]u[/COLOR]_usb.Thank you for your kind comments.

```

modinfo 8712u | grep 8192

```doesn't show anything, so I guess 8712u doesn't support my device.

One thing weird is that my device used to show an id of 0bda:8171, but now it shows 0bda:8192. Is that possible after changes to the OS.

The driver in the staging area detects the device never connects to any network. RealTek emailed me a driver and I get the following with it ... It basically crashes.

Thanks again for all your help.

```

modinfo r8192_usb| grep 8192

```gives 

```

filename:       /lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/r8192_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
alias:          usb:v0BDAp8192d*dc*dsc*dp*ic*isc*ip*

```However on inserting the card I get this 

```

[ 2043.590018] usb 2-4: new full speed USB device using ohci_hcd and address 4
[ 2043.803114] usb 2-4: not running at top speed; connect to a high speed hub
[ 2043.813233] usb 2-4: configuration #1 chosen from 1 choice
[ 2044.134095] rtl819xU:EEPROM ID is invalid(is 0x0(should be 0x8129)
[ 2044.134098] 
[ 2044.134897] ------------[ cut here ]------------
[ 2044.134906] WARNING: at /build/buildd/linux-2.6.32/fs/proc/generic.c:590 proc_register+0x118/0x200()
[ 2044.134908] Hardware name: T6211
[ 2044.134910] proc_dir_entry 'rtl819xU/wlan0' already registered
[ 2044.134912] Modules linked in: r8192_usb iptable_filter ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 ip_tables x_tables bridge stp vboxdrv binfmt_misc lirc_mceusb lirc_dev snd_atiixp snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event tifm_sd fbcon tileblit snd_seq tifm_core font snd_timer bitblit snd_seq_device sbp2 softcursor nvidia(P) ppdev vga16fb snd vgastate edac_core psmouse lp soundcore parport_pc edac_mce_amd k8temp serio_raw snd_page_alloc i2c_piix4 parport shpchp usb_storage 8139too ohci1394 8139cp usbhid hid mii ieee1394 floppy sata_sil pata_atiixp [last unloaded: 8712u]
[ 2044.134958] Pid: 22, comm: khubd Tainted: P           2.6.32-25-generic #45-Ubuntu
[ 2044.134961] Call Trace:
[ 2044.134968]  [<ffffffff81065efb>] warn_slowpath_common+0x7b/0xc0
[ 2044.134972]  [<ffffffff81065fa1>] warn_slowpath_fmt+0x41/0x50
[ 2044.134976]  [<ffffffff811a0858>] proc_register+0x118/0x200
[ 2044.134980]  [<ffffffff811a0d88>] ? __proc_create+0xd8/0x130
[ 2044.134983]  [<ffffffff811a0f0e>] create_proc_entry+0x5e/0xb0
[ 2044.134999]  [<ffffffffa0f1fdc7>] rtl8192_proc_init_one+0x27/0x330 [r8192_usb]
[ 2044.135007]  [<ffffffffa0f20227>] rtl8192_usb_probe+0x157/0x2c0 [r8192_usb]
[ 2044.135012]  [<ffffffff813db235>] usb_probe_interface+0xe5/0x1d0
[ 2044.135017]  [<ffffffff8136ab75>] really_probe+0x65/0x170
[ 2044.135020]  [<ffffffff8136acc5>] driver_probe_device+0x45/0x70
[ 2044.135023]  [<ffffffff8136ad90>] ? __device_attach+0x0/0x60
[ 2044.135026]  [<ffffffff8136ade3>] __device_attach+0x53/0x60
[ 2044.135029]  [<ffffffff81369c48>] bus_for_each_drv+0x68/0x90
[ 2044.135032]  [<ffffffff8136aeac>] device_attach+0x8c/0xa0
[ 2044.135034]  [<ffffffff81369a2d>] bus_probe_device+0x2d/0x50
[ 2044.135039]  [<ffffffff813682a4>] device_add+0x2e4/0x4b0
[ 2044.135042]  [<ffffffff813d9888>] usb_set_configuration+0x478/0x770
[ 2044.135046]  [<ffffffff813e33b3>] generic_probe+0x43/0xc0
[ 2044.135049]  [<ffffffff8136aa52>] ? driver_sysfs_add+0x62/0x90
[ 2044.135052]  [<ffffffff813d9c6a>] usb_probe_device+0x2a/0x30
[ 2044.135055]  [<ffffffff8136ab75>] really_probe+0x65/0x170
[ 2044.135058]  [<ffffffff8136acc5>] driver_probe_device+0x45/0x70
[ 2044.135061]  [<ffffffff8136ad90>] ? __device_attach+0x0/0x60
[ 2044.135064]  [<ffffffff8136ade3>] __device_attach+0x53/0x60
[ 2044.135067]  [<ffffffff81369c48>] bus_for_each_drv+0x68/0x90
[ 2044.135070]  [<ffffffff8136aeac>] device_attach+0x8c/0xa0
[ 2044.135072]  [<ffffffff81369a2d>] bus_probe_device+0x2d/0x50
[ 2044.135090]  [<ffffffff813682a4>] device_add+0x2e4/0x4b0
[ 2044.135094]  [<ffffffff813d150a>] usb_new_device+0x6a/0xe0
[ 2044.135098]  [<ffffffff813d2218>] hub_port_connect_change+0x5e8/0x9d0
[ 2044.135102]  [<ffffffff813d3002>] hub_events+0x3b2/0x5a0
[ 2044.135106]  [<ffffffff815411d0>] ? thread_return+0x48/0x418
[ 2044.135110]  [<ffffffff813d3245>] hub_thread+0x55/0x190
[ 2044.135114]  [<ffffffff81084580>] ? autoremove_wake_function+0x0/0x40
[ 2044.135118]  [<ffffffff813d31f0>] ? hub_thread+0x0/0x190
[ 2044.135121]  [<ffffffff81084206>] kthread+0x96/0xa0
[ 2044.135125]  [<ffffffff810131ea>] child_rip+0xa/0x20
[ 2044.135128]  [<ffffffff81084170>] ? kthread+0x0/0xa0
[ 2044.135130]  [<ffffffff810131e0>] ? child_rip+0x0/0x20
[ 2044.135133] ---[ end trace a1da02bfc59c430e ]---
[ 2044.147805] udev: renamed network interface wlan0 to wlan2
[ 2044.250086] rtl819xU:====>error=====dwRegRead: 0, WriteData: fffff027 
[ 2044.250089] 
[ 2044.250091] rtl819xU:PHY_RF8256_Config():Check PHY0 Fail!!

```

---

### Post by chili555 on 2010-11-16
In post # 2, you said:> output gives a device id of
Code:

 obda:8192

Are you as confused as I am?> One thing weird is that my device used to show an id of 0bda:8171, but now it shows 0bda:8192. Is that possible after changes to the OS.Very doubtful.

Insert the device and please show me all of:```
lsusb
```I think I need an adult beverage and a tranquilizer.

---

### Post by bosbeemer on 2010-11-16
Here you go ...

```

tarun@emachine:~$ lsusb
Bus 003 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 0bda:8192 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The reason I'm sure the device ID has changed is because I had posted a question earlier in the forums when I first got the device. That has the different device ID. [http://ubuntuforums.org/showthread.php?t=1519743](http://ubuntuforums.org/showthread.php?t=1519743) . However Realtek emailed me the drivers and that worked fine for a while. 

Do you know what can cause the device id to change. Is there a way to fake the device ID back to 8171, so that I can try the 8712u driver again.

---

### Post by chili555 on 2010-11-16
More tranquilizers, please!!!

Please see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034)

Especially see posts #35 and #36.

I suggest you try this. If you need assistance, please post back.

---

### Post by Cariboo1938 on 2010-11-16
> **chili555 said:**
> As I mentioned previously, you need to blacklist r8192s_usb. Please do:```
sudo su
echo "blacklist r8192s_usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot .....

After this operation I'm now really in trouble...System does not boot anymore...I took a screen shot from booting in Recovery Mode. It shows where boot stops...Kernel Panic...nothing goes anymore...I'm writing this from my Windows 7-64bit partition with wireless connection through the dongle in question... I think I have to use my remastered Live CD and install fresh??????:confused: Any other options?

---

### Post by Cariboo1938 on 2010-11-16
I just got this email 
From: Jerry-chuang <jerry-chuang@realtek.com>

> Thank you for your email.
Excuse me. it is no support 64bit OS. The RTL8191SU linux driver source just support 32bit OS.
 
BR
Jerry

Is there a way around????

---

### Post by bosbeemer on 2010-11-16
> **Cariboo1938 said:**
> After this operation I'm now really in trouble...System does not boot anymore...I took a screen shot from booting in Recovery Mode. It shows where boot stops...Kernel Panic...nothing goes anymore...I'm writing this from my Windows 7 partition with wireless connection through the dongle in question... I think I have to use my remastered Live CD and install fresh??????:confused: Any other options?

Looks like after you blacklisted the 8192 driver, some other driver must have been loaded and that caused the kernel panic. You don't need to do a fresh install. You can either boot with your usb dongle not plugged in. Or you can boot into recovery mode.

In both cases simply remove the line blacklist r8192s_usb from blacklist.conf

---

### Post by bosbeemer on 2010-11-16
> **chili555 said:**
> More tranquilizers, please!!!

Please see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034)

Especially see posts #35 and #36.

I suggest you try this. If you need assistance, please post back.

I tried that too. I get the following when I insert the stick. Do you know why would I get the last line. <i>wlan1: link is not ready</i>

Thanks.

```
[11441.260014] usb 2-4: new full speed USB device using ohci_hcd and address 9
[11441.473063] usb 2-4: not running at top speed; connect to a high speed hub
[11441.483201] usb 2-4: configuration #1 chosen from 1 choice
[11441.497525] ==>ep_num:6, in_ep_num:1, out_ep_num:5
[11441.497528] ==>RtInPipes:3  
[11441.497530] ==>RtOutPipes:4  5  6  7  13  
[11441.497534] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[11441.497536] 3  2  1  0  4  4  4  4  4  
[11441.527061] Dot11d_Init()
[11441.527085] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[11441.527087] 
[11441.536522] udev: renamed network interface wlan0 to wlan1
[11441.627052] rtl819xU: --->FirmwareDownload92S()
[11441.627056] 
[11441.627063] usb 2-4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[11441.629358] rtl819xU:signature:8192, version:902b, size:30, imemsize:7408, sram size:9688
[11441.629360] 
[11441.629401] rtl819xU:--->FirmwareDownloadCode()
[11441.629402] 
[11441.629438] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[11441.672053] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(1), rtStatus(0)
[11441.672055] 
[11441.672058] rtl819xU:--->FirmwareDownloadCode()
[11441.672059] 
[11441.672106] rtl819xU:--->FirmwareCheckReady(): LoadStaus(2),
[11441.728047] rtl819xU:-->FirmwareEnableCPU()
[11441.728051] 
[11441.738044] rtl819xU:IMEM Ready after CPU has refilled.
[11441.738046] 
[11441.738048] rtl819xU:<--FirmwareEnableCPU(): rtStatus(0x0)
[11441.738049] 
[11441.738051] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(2), rtStatus(0)
[11441.738052] 
[11441.738055] rtl819xU:--->FirmwareDownloadCode()
[11441.738056] 
[11441.738062] rtl819xU:--->FirmwareCheckReady(): LoadStaus(3),
[11441.742046] rtl819xU:DMEM code download success, CPUStatus(0xff)
[11441.742047] 
[11441.744043] rtl819xU:Polling Load Firmware ready, CPUStatus(ff)
[11441.744044] 
[11441.752045] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[11441.752046] 
[11441.754045] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(3), rtStatus(0)
[11441.754046] 
[11441.754047] rtl819xU:Firmware Download Success!!
[11441.754048] 
[11446.100246] ADDRCONF(NETDEV_UP): wlan1: link is not ready
```

---

### Post by Cariboo1938 on 2010-11-16
> **bosbeemer said:**
> ....In both cases simply remove the line blacklist r8192s_usb from blacklist.conf

**Were is blacklist.conf located?**

Edit:
Never mind, I found it here: /etc/modprobe.d

---

### Post by Cariboo1938 on 2010-11-16
OK, I removed line ***blacklist r8192s_usb*** from blacklist.conf.
Now, as soon as I plug in the dongle the system freezes. The only way out is hardware reset or restart.
What else is to do? 
Is it true that the amd64 system is not supported?
:confused:

---

### Post by chili555 on 2010-11-17
> Is it true that the amd64 system is not supported?Evidently so; that's what the manufacturer has told you.

I suggest you leave the wireless device out and uninstall the 8712u driver. Follow the same process as you used to install it, except the only command you need is:```
sudo make uninstall
```Just to be very sure, look in /lib/modules/[COLOR="Red"]2.6.35-22-generic[/COLOR]/kernel/drivers/net/wireless/ to make sure it is gone. Substitute your kernel version if it's not 2.6.35-22-generic:```
uname -r
```Also, look in /etc/modules and be sure 8712u is not explicitly loaded. If it is listed there, remove it.

Now reinsert your device.

---

### Post by chili555 on 2010-11-17
> Do you know why would I get the last line. <i>wlan1: link is not ready</i>Not without more diagnostics:```
dmesg | grep wlan
iwconfig wlan1
sudo iwlist wlan1 scan
```

---

### Post by Cariboo1938 on 2010-11-17
I'm not sure about the uninstall procedure?  I didn't change any thing yet.

Kernel version is
> karibu@karibu-desktop:~$ uname -r
2.6.32-25-generic


In /etc/modules the driver is listed twice.
> #/etc/modules:
# kernel modules to load at boot time.
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
lp
rtc
8712u
8712u

There is no 
> /lib/modules/2.6.35-22-generic

You wrote :Follow the same process as you used to install it, except the only command you need ...
Do you mean to go to the directory where the "Makefile" of the installation is located and execute *sudo make uninstall*?

What is the procedure to substitute the kernel?

---

### Post by bosbeemer on 2010-11-17
> **Cariboo1938 said:**
> I'm not sure about the uninstall procedure?  I didn't change any thing yet.

Kernel version is


In /etc/modules the driver is listed twice.


There is no 


You wrote :Follow the same process as you used to install it, except the only command you need ...
Do you mean to go to the directory where the "Makefile" of the installation is located and execute *sudo make uninstall*?

What is the procedure to substitute the kernel?

Yes do the following first ...

```

sudo modprobe -rv 8712u

```

That would remove the module from memory. After that go the directory where the Makefile for the installation is. The do following ...

```

sudo su
make uninstall

```

The above would delete the driver and the firmware. After that remove the two entries for 8712u from /etc/modules.

---

### Post by bosbeemer on 2010-11-17
It is /lib/modules/2.6.32-25-generic and not  /lib/modules/2.6.35-22-generic

---

### Post by tapas_mishra on 2010-11-17
Ok I came in a bit little late
just make sure you upgrade your firmware as mentioned here.
[http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x)
Here you should see the latest driver for your hardware
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers/staging/rtl8192u;h=37ba68ee8891f0de189c0ab0fa92645b9710ab1a;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers/staging/rtl8192u;h=37ba68ee8891f0de189c0ab0fa92645b9710ab1a;hb=HEAD)

From what I understand from lists here and there this device right now does not have a driver other than staging driver.
Ubuntu does have a staging driver (someone correct me if I am wrong)
Check this link
[http://www.bioticaindia.com/rtl8192.html](http://www.bioticaindia.com/rtl8192.html)
and this one also 
[http://rapidshare.com/#!download|321tl3|300697346|rtl8192efirmware.zip|23]("http://rapidshare.com/#%21download%7C321tl3%7C300697346%7Crtl8192efirmware.zip%7C23")
and 
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-a-761714/page3.html](http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-a-761714/page3.html)
[http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=9&Level=6&Conn=5&ProdID=176](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=9&Level=6&Conn=5&ProdID=176)
does it help?

---

### Post by Cariboo1938 on 2010-11-17
> **bosbeemer said:**
> It is /lib/modules/2.6.32-25-generic and not  /lib/modules/2.6.35-22-generic

chili555 wrote > Substitute your kernel version if it's not 2.6.35-22-generic:

Does it mean I have to go back to an older kernel version
:confused:

---

### Post by tapas_mishra on 2010-11-17
> **Cariboo1938 said:**
> chili555 wrote 

Does it mean I have to go back to an older kernel version
:confused:


Yes it means that only.I got one link from Ubuntu mailing list here it is 
[http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815)

---

### Post by chili555 on 2010-11-17
> From what I understand from lists here and there this device right now does not have a driver other than staging driver.Correct; not in 64-bit.> In /etc/modules the driver is listed twice.
Quote:
#/etc/modules:
# kernel modules to load at boot time.
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
lp
rtc
8712u
8712u That is what is causing the lock-up. Let's remove it:```
sudo gedit /etc/modules
```Remove both lines:```
In /etc/modules the driver is listed twice.
Quote:
#/etc/modules:
# kernel modules to load at boot time.
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
lp
rtc
[COLOR="Red"]8712u[/COLOR]
[COLOR="Red"]8712u [/COLOR]
```Proofread, save and close gedit.> 

---

### Post by chili555 on 2010-11-17
> **tapas_mishra said:**
> Yes it means that only.I got one link from Ubuntu mailing list here it is 
[http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815)I don't believe you need to go to an earlier kernel version.

Y'all gonna fix him up? Shall I depart?

---

### Post by Cariboo1938 on 2010-11-17
> **chili555 said:**
> I don't believe ..... Shall I depart?
 
No, please don't! All you thought me so far sounded very understandable to me...:)
I just contacted Realtek again because I learned [HERE]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-a-761714/page3.html") that there is a 64bit support!
:confused:

---

### Post by chili555 on 2010-11-17
Let's remove the old 8712u. Open a terminal and navigate to the directory where you originally installed it; for instance:```
cd Desktop/RTLwherever
ls
```Make sure you are in the same directory as the Makefile. Now do:```
sudo make uninstall
sudo updatedb
locate 8712u
```updatedb will take a few moments so be patient.

Is there anything left in /lib/modules/...? If so, please do:```
sudo rm 
```Now copy the location in /lib/modules where you located 8712u.ko. Press Enter to rid us all of the headaches. For example:```
sudo rm /lib/modules/2.6.32-25-generic/drivers/net/wireless/8712u.ko
```Substitute the actual location if my guesswork is faulty.

Reinsert your device and run:```
dmesg | grep 819
```Post the result and let's see if we can fiddle the native driver to life while we wait for a reply from Realtek.

---

### Post by Cariboo1938 on 2010-11-17
I got stuck here:

> **chili555 said:**
> .....
Is there anything left in /lib/modules/...? Yes 
> root@karibu-desktop:/lib/modules# ls -l
total 4
drwxr-xr-x 5 root root 4096 2010-11-17 13:50 2.6.32-25-generic
> root@karibu-desktop:/lib/modules/2.6.32-25-generic# 
ls -l
total 3680
lrwxrwxrwx  1 root root     40 2010-10-01 23:18 build -> /usr/src/linux-headers-2.6.32-25-generic
drwxr-xr-x  2 root root   4096 2010-11-10 22:52 initrd
drwxr-xr-x 10 root root   4096 2010-10-01 23:17 kernel
-rw-r--r--  1 root root 600870 2010-11-17 13:50 modules.alias
-rw-r--r--  1 root root 574508 2010-11-17 13:50 modules.alias.bin
-rw-r--r--  1 root root   4673 2010-10-16 13:37 modules.builtin
-rw-r--r--  1 root root   6123 2010-11-17 13:50 modules.builtin.bin
-rw-r--r--  1 root root     69 2010-11-17 13:50 modules.ccwmap
-rw-r--r--  1 root root 252771 2010-11-17 13:50 modules.dep
-rw-r--r--  1 root root 372334 2010-11-17 13:50 modules.dep.bin
-rw-r--r--  1 root root   1405 2010-11-17 13:50 modules.ieee1394map
-rw-r--r--  1 root root    218 2010-11-17 13:50 modules.inputmap
-rw-r--r--  1 root root   8441 2010-11-17 13:50 modules.isapnpmap
-rw-r--r--  1 root root     74 2010-11-17 13:50 modules.ofmap
-rw-r--r--  1 root root  97970 2010-10-16 13:37 modules.order
-rw-r--r--  1 root root 417971 2010-11-17 13:50 modules.pcimap
-rw-r--r--  1 root root   1345 2010-11-17 13:50 modules.seriomap
-rw-r--r--  1 root root 213936 2010-11-17 13:50 modules.symbols
-rw-r--r--  1 root root 277412 2010-11-17 13:50 modules.symbols.bin
-rw-r--r--  1 root root 883469 2010-11-17 13:50 modules.usbmap
drwxr-xr-x  3 root root   4096 2010-10-01 23:19 updates
root@karibu-desktop:/lib/modules/2.6.32-25-generic# 

Am I at the right place? I don't dare to rm all....!

---

### Post by chili555 on 2010-11-17
> I don't dare to rm all....!In the name of all that's holy! NO!!!

Keep drilling down:```
ls /lib/modules/2.6.32-25-generic/drivers/net/wireless
```What's in there? a 8712u.ko? If not, we're good; if so rm it *and only it*!

---

### Post by Cariboo1938 on 2010-11-17
I like your sense of humor
> **chili555 said:**
> [COLOR="DeepSkyBlue"]In the name of all that's holy! NO!!![/COLOR]
> **chili555 said:**
> 
Keep drilling down:```
ls /lib/modules/2.6.32-25-generic/drivers/net/wireless
```What's in there? a 8712u.ko? If not, we're good; if so rm it *and only it*!

There is no > /lib/modules/2.6.32-25-generic/drivers/net/wireless
But there is > root@karibu-desktop:/lib/modules/2.6.32-25-generic/[B][COLOR="Magenta"]kernel[/COLOR]
[/B]/drivers/net/wireless# ls -l
total 816

Is this the right location?

There was no 8712u.ko
> root@karibu-desktop:/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless# ls -l *.ko
-rw-r--r-- 1 root root  49272 2010-10-16 13:37 adm8211.ko
-rw-r--r-- 1 root root  11344 2010-10-16 13:37 airo_cs.ko
-rw-r--r-- 1 root root 136616 2010-10-16 13:37 airo.ko
-rw-r--r-- 1 root root  75136 2010-10-16 13:37 at76c50x-usb.ko
-rw-r--r-- 1 root root  14632 2010-10-16 13:37 atmel_cs.ko
-rw-r--r-- 1 root root  58912 2010-10-16 13:37 atmel.ko
-rw-r--r-- 1 root root   5976 2010-10-16 13:37 atmel_pci.ko
-rw-r--r-- 1 root root  34104 2010-10-16 13:37 mac80211_hwsim.ko
-rw-r--r-- 1 root root  49224 2010-10-16 13:37 mwl8k.ko
-rw-r--r-- 1 root root  21440 2010-10-16 13:37 netwave_cs.ko
-rw-r--r-- 1 root root  48640 2010-10-16 13:37 ray_cs.ko
-rw-r--r-- 1 root root  49416 2010-10-16 13:37 rndis_wlan.ko
-rw-r--r-- 1 root root  47024 2010-10-16 13:37 strip.ko
-rw-r--r-- 1 root root  45728 2010-10-16 13:37 wavelan_cs.ko
-rw-r--r-- 1 root root  41376 2010-10-16 13:37 wl3501_cs.ko
-rw-r--r-- 1 root root  39024 2010-10-16 13:37 zd1201.ko
root@karibu-desktop:/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless# 

---

### Post by chili555 on 2010-11-17
> # ls -l *.koTry it without the .ko. Any suspicious looking diretcories? No?

Excellent! Now reinsert your device and let's have a peek at:```
dmesg | grep 819
lsmod | grep 819
```We are probably only interested in the last 15 or so lines if it's lengthy.

---

### Post by Cariboo1938 on 2010-11-17
Before I move on concerning your question
> **chili555 said:**
> Try it without the .ko. Any suspicious looking diretcories? No?
I can't judge that
> root@karibu-desktop:/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless# ls -l
total 816
-rw-r--r-- 1 root root  49272 2010-10-16 13:37 adm8211.ko
-rw-r--r-- 1 root root  11344 2010-10-16 13:37 airo_cs.ko
-rw-r--r-- 1 root root 136616 2010-10-16 13:37 airo.ko
-rw-r--r-- 1 root root  75136 2010-10-16 13:37 at76c50x-usb.ko
drwxr-xr-x 5 root root   4096 2010-11-10 22:52 ath
-rw-r--r-- 1 root root  14632 2010-10-16 13:37 atmel_cs.ko
-rw-r--r-- 1 root root  58912 2010-10-16 13:37 atmel.ko
-rw-r--r-- 1 root root   5976 2010-10-16 13:37 atmel_pci.ko
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 b43
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 b43legacy
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 hostap
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 ipw2x00
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 iwlwifi
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 iwmc3200wifi
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 libertas
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 libertas_tf
-rw-r--r-- 1 root root  34104 2010-10-16 13:37 mac80211_hwsim.ko
-rw-r--r-- 1 root root  49224 2010-10-16 13:37 mwl8k.ko
-rw-r--r-- 1 root root  21440 2010-10-16 13:37 netwave_cs.ko
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 orinoco
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 p54
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 prism54
-rw-r--r-- 1 root root  48640 2010-10-16 13:37 ray_cs.ko
-rw-r--r-- 1 root root  49416 2010-10-16 13:37 rndis_wlan.ko
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 rt2x00
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 rtl818x
-rw-r--r-- 1 root root  47024 2010-10-16 13:37 strip.ko
-rw-r--r-- 1 root root  45728 2010-10-16 13:37 wavelan_cs.ko
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 wl12xx
-rw-r--r-- 1 root root  41376 2010-10-16 13:37 wl3501_cs.ko
-rw-r--r-- 1 root root  39024 2010-10-16 13:37 zd1201.ko
drwxr-xr-x 2 root root   4096 2010-11-10 22:52 zd1211rw
root@karibu-desktop:/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless# 


There are two rt* directories!
> root@karibu-desktop:/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/rtl818x# ls -l
total 164
-rw-r--r-- 1 root root 63640 2010-10-16 13:37 rtl8180.ko
-rw-r--r-- 1 root root 99944 2010-10-16 13:37 rtl8187.ko
root@karibu-desktop:/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/rtl818x# and
> root@karibu-desktop:/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/rt2x00# ls -l
total 360
-rw-r--r-- 1 root root 25064 2010-10-16 13:37 rt2400pci.ko
-rw-r--r-- 1 root root 28208 2010-10-16 13:37 rt2500pci.ko
-rw-r--r-- 1 root root 39760 2010-10-16 13:37 rt2500usb.ko
-rw-r--r-- 1 root root 71368 2010-10-16 13:37 rt2800usb.ko
-rw-r--r-- 1 root root 56920 2010-10-16 13:37 rt2x00lib.ko
-rw-r--r-- 1 root root 17560 2010-10-16 13:37 rt2x00pci.ko
-rw-r--r-- 1 root root 23952 2010-10-16 13:37 rt2x00usb.ko
-rw-r--r-- 1 root root 36880 2010-10-16 13:37 rt61pci.ko
-rw-r--r-- 1 root root 51080 2010-10-16 13:37 rt73usb.ko
root@karibu-desktop:/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/rt2x00#

---

### Post by chili555 on 2010-11-17
No 8712u.ko. We are safe, at least from that villain. Let's insert the device and see what happens or not.

---

### Post by Cariboo1938 on 2010-11-17
Here we are
> root@karibu-desktop:/# dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u262144
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u262144 alloc=1*2097152
[    0.000000] Memory: 1781944k/1834560k available (5420k kernel code, 452k absent, 52164k reserved, 2974k data, 872k init)
[28740.832231] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[28740.843020] Linux kernel driver for RTL8192 based WLAN cards
[28741.114973] usbcore: registered new interface driver rtl819xU
[28741.262046] rtl819xU: --->FirmwareDownload92S()
[28741.262062] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[28741.363780] rtl819xU:request firmware fail!
[28741.365529] rtl819xU:Firmware Download Fail!!a
[28741.379255] rtl819xU: --->FirmwareDownload92S()
[28741.379271] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[28741.383585] rtl819xU:request firmware fail!
[28741.384218] rtl819xU:Firmware Download Fail!!a
[28741.384227] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[28741.499705] rtl819xU: --->FirmwareDownload92S()
[28741.499723] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[28741.504172] rtl819xU:request firmware fail!
[28741.504695] rtl819xU:Firmware Download Fail!!a
[28741.519833] rtl819xU: --->FirmwareDownload92S()
[28741.519849] usb 1-4.4: firmware: requesting RTL8192SU/rtl8192sfw.bin
[28741.526293] rtl819xU:request firmware fail!
[28741.527645] rtl819xU:Firmware Download Fail!!a
[28741.527657] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
root@karibu-desktop:/# 

Doesn't look good, does it?

---

### Post by chili555 on 2010-11-17
Hey, I've seen worse; it isn't a kernel panic!

Please see: [http://ubuntuforums.org/showpost.php?p=10125636&postcount=17](http://ubuntuforums.org/showpost.php?p=10125636&postcount=17)

Please try the approach in post #35 in the link:> wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/You will need an internet connection.

Then do:```
sudo rmmod -f r8192s_usb
sudo modprobe r8192s_usb
```Any improvement?

As always, post back if I can help.

---

### Post by Cariboo1938 on 2010-11-17
Just wondering do I need to to unplug the adapter when trying out the commands?

---

### Post by chili555 on 2010-11-17
Not really, but it's a handy shortcut. It should unload the r8192s_usb module when you unplug it and reload it, hopefully with firmware, when you plug it back in.

---

### Post by Cariboo1938 on 2010-11-17
:guitar:
[COLOR="Magenta"][SIZE="3"]**Yes, it works! I'm on wireless!**[/SIZE][/COLOR]

[SIZE="3"]**[COLOR="Magenta"]Thank you, chili555, for the outstanding support![/COLOR]**[/SIZE]

To make a summery, the issue was solved practically with these three commands:
> wget [I][http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/[/I]

Is that correct? And I didn't have to downgrade on the kernel version either! Thanks again!
:)

---

### Post by chili555 on 2010-11-17
Woo hoo! If it works, it's all good. Enjoy your wireless.

---

### Post by bosbeemer on 2010-11-17
:), it finally worked !!!. I had to follow the instructions here [http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815)  but with some tweaks. My problem was kind of reverse of everyone  else's. My card reported a device id of obda:8192, however it did NOT  work with r8192s_usb or r8192_usb drivers. My card works fine with  8712u. I had the 8712u drivers from before when Realtek had emailed them  to me.

I changed /etc/modprobe.d/network_drivers.conf to contain the following ...
```
install 8712u /sbin/modprobe --ignore-install 8712u $CMDLINE_OPTS; /bin/echo "0bda 8192" > /sys/bus/usb/drivers/r871x_usb_drv/new_id
```and

changed /etc/udev/rules.d/network_drivers.rules to contain the following ...
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0bda", ATTR{idProduct}=="8192", RUN+="/sbin/modprobe -qba 8712u"
```As you can see that I had to trick the kernel into associating 8712u  with 0bda:8192. Simply loading 8712u with modprobe didn't do the trick,  the above changes were necessary. Of course I had to blacklist  r8192u_usb too.

Thanks all for your help. You've all been very kind.
[COLOR=#888888]
[/COLOR]

---

### Post by chili555 on 2010-11-17
I'm glad it's working for everybody.

---

### Post by Cariboo1938 on 2010-11-17
Here is what I had to do to get the TRENDnet wireless adapter 
TEW-649UB working on my Ubuntu 10.04-64bit system 
(with kernel 2.6.32-25-generic #45...UTC 2010 x86_64 GNU/Linux):

0) Unplug the adapter! Open Terminal!

1) Download from Launchpad  
- *wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)*
     (**NOTE**: the dots ... stand for 12/rtl)

2) cd /Where ever your Downloads are...
- *gunzip rtl8192sfw.bin.gz*

3) *Find* in Downloads
- rtl8192sfw.bin

4) Put file to the correct location
- *sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/*

5) Execute the commands
- *sudo rmmod -f r8192s_usb*
- *sudo modprobe r8192s_usb*

6) Plugin the TRENDnet wireless adapter TEW-649UB
and enjoy your wireless connection to the rest of the world...
:)

EDIT:
In case this doesn't work for you, I want to mention that Realtek sent me another driver (rtl8712_8188_8191_8192SU_usb_linux_v7_0.20100628.tar.gz),
which is supposed to work for 64bit systems! Ask by email: <ythuang@realtek.com>. They send it to you! 
I didn't try it though;)

---

### Post by jshuford on 2010-11-18
> **Cariboo1938 said:**
> :guitar:
[COLOR=Magenta][SIZE=3]**Yes, it works! I'm on wireless!**[/SIZE][/COLOR]

[SIZE=3]**[COLOR=Magenta]Thank you, chili555, for the outstanding support![/COLOR]**[/SIZE]

To make a summery, the issue was solved practically with these three commands:


Is that correct? And I didn't have to downgrade on the kernel version either! Thanks again!
:)

Worked great for me as well!!! Thank you...

---

### Post by r_avital on 2010-11-26
Thank you all for all the wonderful work and info on this thread.  Unfortunately, I am unable to find the file referenced in the thread:

> 
1) Download from 
- [http://launchpadlibrarian.net/373876...8192sfw.bin.gz](http://launchpadlibrarian.net/373876...8192sfw.bin.gz)

I'm getting stuck at this first step, because this URL returns "Error 404: File not Found."

It figures, right?  The moment something is useful, it disappears.

Anyone know where I can find this?  

Thanks in advance.

---

### Post by chili555 on 2010-11-26
Please click on this link. The download should start automatically.

[http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)

---

### Post by cgibble on 2010-12-15
This worked great for me too, but ONLY if I set my wireless router to "G mode only". That is, in "N-only mode or "B/G/N mode", the card would not connect, with or without any security settings enabled.
 
I wondered if the router (an ENCORE ENHWI-N) was a different draft-N specification than the ENUWI-N4, but the interesting thing is that the computer connects fine in N-only mode when it boots into Windows XP.
 
Any thoughts? I can live with G-only speeds, but out of principle it would be nice to get my N-adapter to work with my N-router!

---

### Post by rocksockdoc on 2011-04-24
I just found this thread searching for why the Amped UA600 WiFi range extender isn't recognized by Ubuntu 10.04 and just want to say I have a similar problem:
- [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10716334#post10716334")

The device I'm trying to plug into my USB ports is shown in the picture below from the Amped support site:
- [Setup Guide]("http://www.ampedwireless.com/datasheets/support/UA600_SetupGuide_LR.pdf") (windows only information!)
- [User's Guide]("http://www.ampedwireless.com/datasheets/support/UA600_UsersGuide.pdf") (windows only information!)
- [Datasheet]("http://www.ampedwireless.com/datasheets/Amped_UA600_Datasheet_LR.pdf") (see screenshot included below)

The operating system is a (an almost) pristine Ubuntu 10.04 lucid:
```
$ uname -a
...
Linux library 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686 GNU/Linux
```The output from lsusb is the following:
```
$ lsusb
...
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp.
...
```The output from dmesg is the following:
```
$ dmesg | tail
...
[11570.806468] rtl819xU: --->FirmwareDownload92S()
[11570.806471] 
[11570.806476] usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[11570.814333] rtl819xU:request firmware fail!
[11570.814335] 
[11570.815654] rtl819xU:Firmware Download Fail!!a
[11570.815656] 
[11570.815660] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[11570.815662]

```

The /lib/firmware directory contains the following:
```

$ ls -l /lib/firmware/RTL*

/lib/firmware/RTL8192E:
total 52
-rw-r--r-- 1 root root   344 2010-12-14 08:25 boot.img
-rw-r--r-- 1 root root   848 2010-12-14 08:25 data.img
-rw-r--r-- 1 root root 42944 2010-12-14 08:25 main.img

/lib/firmware/RTL8192SE:
total 244
-rw-r--r-- 1 root root 75984 2010-12-14 08:26 rtl8192sfw492.bin
-rw-r--r-- 1 root root 89616 2010-12-14 08:26 rtl8192sfw74.bin
-rw-r--r-- 1 root root 80976 2010-12-14 08:26 rtl8192sfw.bin

```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189813&stc=1&d=1303591188[/IMG]

---

### Post by chili555 on 2011-04-25
Please see post #2 here:  [http://ubuntuforums.org/showthread.php?t=1464471](http://ubuntuforums.org/showthread.php?t=1464471)

---

### Post by rocksockdoc on 2011-04-25
> **chili555 said:**
> Please see post #2 here:  [http://ubuntuforums.org/showthread.php?t=1464471](http://ubuntuforums.org/showthread.php?t=1464471)

Thanks. That helped a lot to understand and work around this (apparently known) Ubuntu bug which sidetracked me for a day.

I detailed my efforts to insert an external USB WiFi radio into my laptop in this thread:
- [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10718746#post10718746")

On my version of a pristine Ubuntu 10.04 laptop installation:
```
$uname -a
...
Linux library 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686 GNU/Linux

```

At first, Ubuntu would not recognize the [Amped UA600 USB WiFi radio adapter ]("http://www.ampedwireless.com/support/model/ua600.html")when it was plugged into the laptop USB port.

```

$ ifconfig | grep wlan   
...
eth0 Link encap:Ethernet  HWaddr 00:a0:c3:3a:93:38
wlan0 Link encap:Ethernet  HWaddr 00:0a:8d:37:b3:ba

```

First, I determined the device identifier using 'list short USB":
```

$ lsusb
...
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. 

```

Then, in the /var/log/messages (dmesg | tail), I determined what driver Ubuntu was (mistakenly) looking for:
```

usb 2-1: new high speed USB device using ehci_hcd and address 2
usb 2-1: configuration #1 chosen from 1 choice
r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned. <=== huh?
 ...
Linux kernel driver for RTL8192 based WLAN cards
Copyright (c) 2007-2008, Realsil Wlan
...
rtl8192_proc_init_one+0x25/0x460 [r8192s_usb]
rtl8192_usb_probe+0x148/0x191 [r8192s_usb]       **[COLOR=DarkRed]<==== NOTE: This will be useful for the modinfo [/COLOR]**command syntax!
...
usbcore: registered new interface driver rtl819xU [COLOR=DarkRed]**  <=== NOTICE the "U" (Ubuntu has only the "E")**[/COLOR]
usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
...
usb 2-1: USB disconnect, address 3
...

```

Placing that keyword into "module information", I could see the desired driver:
```

$ modinfo r8192s_usb
...
filename:       /lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
...

```

A quick look in the /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless directory shows an "rtl818x" directory with the following contents:

```

$ ls -alsF /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rtl818x/*
...
44 -rw-r--r--  1 root root 43176 2011-04-08 16:36 rtl8180.ko
72 -rw-r--r--  1 root root 73640 2011-04-08 16:36 rtl8187.ko

```

The problem appears to be that Ubuntu is looking for the following location  (which doesn't exist):
```

$ ls /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin
...
ls: cannot access /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin: No such file or directory

```

The file exists (rtl8192sfw_bin); it's just in a different location on Ubuntu:
```

$ ls -alsF /lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**
...
/lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**:
total 244
-rw-r--r-- 1 root root 75984 2010-12-14 08:26 rtl8192sfw492.bin
-rw-r--r-- 1 root root 89616 2010-12-14 08:26 rtl8192sfw74.bin
-rw-r--r-- 1 root root 80976 2010-12-14 08:26 rtl8192sfw.bin

```

[Post #35]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/35") and [post #36]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/36") of [this thread]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17") provided a (different sized, same-named file):
-[ [STAGING] realtek rtl8192su chipset based USB wireless devices fail to work    ]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17")

> 
logari81 wrote on 2010-11-15: post #35
...
 We have just confirmed this bug using the LiveCD of Ubuntu 10.10 with the the following device:
 Bus 001 Device 006: ID 0b05:1786 ASUSTek Computer, Inc.
  After connecting the wifi stick, the driver r8192s_usb cannot find the firmware:
...
 looking at: [http://lxr.linux.no/#linux+v2.6.36/drivers/staging/rtl8192su/r8192S_firmware.c](http://lxr.linux.no/#linux+v2.6.36/drivers/staging/rtl8192su/r8192S_firmware.c)
it seems that the driver r8192s_usb looks for a firmware file /lib/firmware/RTL8192SU/rtl8192sfw.bin
but the directory RTL8192SU doesn't exist in Maverick.
...
We first tried copying the firmware file from RTL8192SE:
 sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/
 after this the wifi stick could detect wireless networks but couldn't connect (the filesize of this firmware is 80976 bytes).
...
Then we tried a different version of the firmware:
 wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
  gunzip rtl8192sfw.bin.gz
  sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
...
With this one the wifi stick could both detect wireless networks and connect to them (the filesize of the used firmware is 68368 bytes).
...


Here's what I did to obtain that differently-sized file (I guess I should call it a "driver"):
```

http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
    $ gunzip rtl8192sfw.bin.gz
    $ sudo mkdir /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**
    $ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/.

```

Finally, I was able to get Ubuntu to recognize the external WiFi radio when plugged in:
```

$ ifconfig | grep wlan
...
wlan0     Link encap:Ethernet  HWaddr 00:0a:8d:37:b3:ba
wlan1     Link encap:Ethernet  HWaddr f8:78:8c:a1:45:f4

```

Now that the driver is finally working, I can get back to the original question asked in that thread:
- [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10718746#post10718746")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189999&stc=1&d=1303756077[/IMG]

---

### Post by nesnfsn on 2011-11-05
> **rocksockdoc said:**
> I just found this thread searching for why the Amped UA600 WiFi range extender isn't recognized by Ubuntu 10.04 and just want to say I have a similar problem:
- [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10716334#post10716334")

The device I'm trying to plug into my USB ports is shown in the picture below from the Amped support site:
- [Setup Guide]("http://www.ampedwireless.com/datasheets/support/UA600_SetupGuide_LR.pdf") (windows only information!)
- [User's Guide]("http://www.ampedwireless.com/datasheets/support/UA600_UsersGuide.pdf") (windows only information!)
- [Datasheet]("http://www.ampedwireless.com/datasheets/Amped_UA600_Datasheet_LR.pdf") (see screenshot included below)

The operating system is a (an almost) pristine Ubuntu 10.04 lucid:
```
$ uname -a
...
Linux library 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686 GNU/Linux
```The output from lsusb is the following:
```
$ lsusb
...
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp.
...
```The output from dmesg is the following:
```
$ dmesg | tail
...
[11570.806468] rtl819xU: --->FirmwareDownload92S()
[11570.806471] 
[11570.806476] usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[11570.814333] rtl819xU:request firmware fail!
[11570.814335] 
[11570.815654] rtl819xU:Firmware Download Fail!!a
[11570.815656] 
[11570.815660] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[11570.815662]

```

The /lib/firmware directory contains the following:
```

$ ls -l /lib/firmware/RTL*

/lib/firmware/RTL8192E:
total 52
-rw-r--r-- 1 root root   344 2010-12-14 08:25 boot.img
-rw-r--r-- 1 root root   848 2010-12-14 08:25 data.img
-rw-r--r-- 1 root root 42944 2010-12-14 08:25 main.img

/lib/firmware/RTL8192SE:
total 244
-rw-r--r-- 1 root root 75984 2010-12-14 08:26 rtl8192sfw492.bin
-rw-r--r-- 1 root root 89616 2010-12-14 08:26 rtl8192sfw74.bin
-rw-r--r-- 1 root root 80976 2010-12-14 08:26 rtl8192sfw.bin

```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189813&stc=1&d=1303591188[/IMG]

I liked this USB Adapter also, and it works well with both MS Windows and Mac OS X. Too bad it will not cooperate with linux.

Just purchased a wireless N300 usb adapter from Monoprice (OEM self-branded), and works with all 3 of the aforementioned OS. I had to install drivers for MS and Mac, but not linux, worked OOB for linux. Happy with device. Sad about UA600 which is 2.5 months old and cannot be returned to the CompUS_ store that I had purchased it from.

If you are interested in a great little usb wireless-n adapter with 2 antennae, visit [www.monoprice](www.monoprice) DOT com.

nesnfsn

---

