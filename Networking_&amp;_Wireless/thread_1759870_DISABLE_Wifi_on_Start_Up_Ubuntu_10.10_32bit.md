---
title: "DISABLE Wifi on Start Up Ubuntu 10.10 32bit"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by nexul on 2011-05-16
Hi Guys,
 
Ive wiped my Toshiba NB500 of 7 Starter and installed 10.10 and now I've lost my ability to **turn off** my wireless radio!!
 
There's plenty and plenty of posts to enable wireless but for me its different, my wifi light is switching on as soon as I boot the netbook and it immediately scans for wifi.
 
When 7 starter was installed I could easily toggle via Fn F8 key to turn on/off wireless but that disappeared after I installed 10.10 - no problem but surely there's a way to turn it off when Im not using it ...to save battery and all that.
 
Ive tried various methods suggested in various forum posts but this baby just aint happening. Heres a brief (and not syntactically correct) overview of my attempts to get this going:
 
1. Network connections > wifi connection > automatically connect disabled - **Not work**
2. Network connection > Enable Wireless check box unchecked - **Not work**
2. sudo ifconfig **wlan0** off (or was it down) - **Not work**
3. Somebody suggested Jupiter ? - is it safe to install Jupiter on 10.10 ?
 
NOTE: I had to install Realtek drivers to get my wifi to work after installation of 10.10 - might it be something I need to tweak in the Realtek drivers ?
 
Or should I have turned wireless off in Windows before overwriting with 10.10 ?
 
I just want to be able to toggle on/off like I could like in windows Intel Pro wireless like functionality. I dont want it to be constantly scanning for WIFIs when I dont want it to, especially when Im running on battery!
 
Any ideas guys ?
 
Thanks.

---

### Post by walt.smith1960 on 2011-05-16
I'm not certain this will help you but look in Synaptic Package Manager.  Put "toshiba" in the search box.  The first few entries should contain 'toshutils' and 'toshset' or something like that.  I don't have a Toshiba but if I did I'd install one or both.  I'd expect one of those to let you select wifi on/off.  The other way to handle it is if you never want to wifi on, open a terminal and type 'lsmod'.  This will show you which modules are loaded.  If you can figure out which module enables your wireless, you could blacklist that module. I did this with an older wireless card that I replaced with a faster USB dongle and it has worked fine-the old wireless card stays off.

---

### Post by nexul on 2011-05-17
Thanks walt.smith1960, some nice info there. 
 
I did find some tosh utils in Synaptic but couldn't get them to download for some reason. Further googling revealed that tosh utils were more for older Toshiba systems and mine being a new nb500 I kinda moved on from there.
 
Blacklisting is an option but I find this might be too heavy handed for me as I want to toggle on/off as and when required. I might resort to this at some point.
 
Interestingly, **when I disable** wifi via Jupiter or Ubuntu and run sudo iwconfig I get this:
 
[HTML]sudo iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any
         Mode:Managed  Access Point: Not-Associated   Tx-Power=off
         Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
         Encryption key:off
         Power Management:off[/HTML]
 
 
**When I enable:**
 
[HTML]lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any
         Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
         Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
         Encryption key:off
         Power Management:off
[/HTML]
 
 
Is my wifi radio REALLY off when I disable it via Jupiter/Ubuntu ?
 
Thank's.

---

### Post by walt.smith1960 on 2011-05-17
> **nexul said:**
> Thanks walt.smith1960, some nice info there. 
 
I did find some tosh utils in Synaptic but couldn't get them to download for some reason. Further googling revealed that tosh utils were more for older Toshiba systems and mine being a new nb500 I kinda moved on from there.
 
Blacklisting is an option but I find this might be too heavy handed for me as I want to toggle on/off as and when required. I might resort to this at some point.
 
Interestingly, **when I disable** wifi via Jupiter or Ubuntu and run sudo iwconfig I get this:
 
[HTML]sudo iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any
         Mode:Managed  Access Point: Not-Associated   Tx-Power=off
         Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
         Encryption key:off
         Power Management:off[/HTML]**When I enable:**
 
[HTML]lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any
         Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
         Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
         Encryption key:off
         Power Management:off
[/HTML]Is my wifi radio REALLY off when I disable it via Jupiter/Ubuntu ?
 
Thank's.

It seems like your best solution would be to enable the Fn+F8 function in Ubuntu if possible. Some sort of script?  I have no knowledge in this area. On a Thinkpad I can disable wifi adapters per session via network manager but the radio stays energized or at least the indicator light stays on.  It isn't active-the indicator isn't blinking-but the indicator is on so I assume the radio is using at least some power.  I hope you can come up with a solution.

---

### Post by nexul on 2011-05-17
Thanks walt.smith1960, I may have an led bug on this new tosh netbook.  Cheers. N.

---

### Post by nicks27 on 2011-07-09
I'd really like a resolution to this too, it's a problem on my Toshiba NB520 which otherwise seems to be running 11.04 (Xubuntu-desktop-i386) fine.

The command [FONT=Courier New] **lspci -vv**[/FONT]  shows that the kernel driver **[FONT=Courier New]ath9k[/FONT]** is in use for this device.
Blacklisting that in **[FONT=Courier New]/etc/modprobe.d/blacklist.conf[/FONT]** and rebooting appears to disable wireless (i.e. **[FONT=Courier New]wlan1[/FONT]** isn't listed by the **[FONT=Courier New]iwconfig[/FONT]** command) but the LED is still on so I'm not convinced it's been properly disabled (and safe to use the machine in hospitals, etc).

The info at [http://memebeam.org/toys/ToshibaAcpiDriver](http://memebeam.org/toys/ToshibaAcpiDriver) suggests the solution might be via the [FONT=Courier New]**toshiba_acpi**[/FONT] kernel module, but the module won't load (it gives the "No such device" error). I have updated to the latest v1.90 BIOS from Toshiba's website to no avail (and there only seems to be one BIOS setting called "Built-in LAN" which appears to disable *all* on-board networking including the wired connection, which is no good). 

The Fn+F8 key combination works fine under WIndows7, so the problem appears to be a Linux-specific configuration issue (and/or Toshiba's proprietary assing around). I don't know if this relates to the bug at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/482119](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/482119) where I've also just posted.

Are there any solutions... or at least explanations?

---

### Post by tux_i on 2011-08-12
hello,

any update ?

does the wifi can be disable or enable with that : 
You can enable wireless (and bluetooth) without Windows by using the omnibook
module with ectype=12. Once you compile and install the omnibook driver, you
must load it with modprobe omnibook ectype=12, then you can use 'echo 1
>/proc/omnibook/wifi' to turn it on. Note that some NB200/NB205 guides will tell
you to use ectype=14, ignore that and use ectype=12 instead. Also, be sure you
do NOT use btcoex_enable=1 with the ath9k module or wifi won't work. Wifi and
bluetooth coexist perfectly without enabling bluetooth coexistance in the ath9k
driver.

---

### Post by nicks27 on 2011-08-12
No, I've not been able to make any progress with this issue, and it's still a problem.
My issue is also in the thread [http://ubuntuforums.org/showthread.php?t=1805187](http://ubuntuforums.org/showthread.php?t=1805187)
and I filed a related bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/815419](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/815419) 

Thanks for your suggestion... I tried  **[FONT=Courier New]sudo modprobe omnibook ectype=12[/FONT]**  and it gave a kernel error (similar to a couple of weeks ago when I tried without the "ectype=12" option) - the details from  [FONT=Courier New]**/var/log/kern.log**[/FONT]  are below.

As you can see from the log that's with the        "2.20090707-trunk" version of omnibook already  installed with my Xubuntu.  I don't know how to compile/install another version of this  kernel module, but in any case I found the sources at [http://sourceforge.net/projects/omnibook/](http://sourceforge.net/projects/omnibook/) and it says version "2.20070211" (over 2 years older).

```

[   86.653497] omnibook: Driver version 2.20090707-trunk.
[   86.653508] omnibook: Forced load with EC type 12.
[   86.655635] BUG: unable to handle kernel paging request at 746f6fa4
[   86.655822] IP: [<f917e06a>] omnibook_init+0x2c/0x178 [omnibook]
[   86.655998] *pde = 00000000 
[   86.656022] Oops: 0000 [#1] SMP 
[   86.656022] last sysfs file: /sys/devices/platform/omnibook/uevent
[   86.656022] Modules linked in: omnibook(+) usbhid hid parport_pc  ppdev joydev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep  snd_pcm snd_seq_midi snd_rawmidi i915 snd_seq_midi_event snd_seq  snd_timer psmouse serio_raw snd_seq_device uvcvideo videodev snd  sparse_keymap drm_kms_helper soundcore snd_page_alloc drm i2c_algo_bit  video lp parport usb_storage uas ahci libahci r8169
[   86.656022] 
[   86.656022] Pid: 1556, comm: modprobe Not tainted 2.6.38-10-generic #46-Ubuntu TOSHIBA TOSHIBA NB520/PBU00
[   86.656022] EIP: 0060:[<f917e06a>] EFLAGS: 00010206 CPU: 1
[   86.656022] EIP is at omnibook_init+0x2c/0x178 [omnibook]
[   86.656022] EAX: 746f6f74 EBX: f82ab71c ECX: 00000000 EDX: ea47f8c0
[   86.656022] ESI: f82a92e8 EDI: ffffffea EBP: efc0fe30 ESP: efc0fe18
[   86.656022]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   86.656022] Process modprobe (pid: 1556, ti=efc0e000 task=f47071a0 task.ti=efc0e000)
[   86.656022] Stack:
[   86.656022]  00000034 00000040 000080d0 0000009c 00000003 13b13b2a efc0fe4c f917e277
[   86.656022]  c11850c7 00000001 f4607a08 f82ab014 f82ab014 efc0fe54 c1335631 efc0fe78
[   86.656022]  c133440d f4607a64 00000000 efc0fe78 c133c67b f4607a08 ffffffed f82ab014
[   86.656022] Call Trace:
[   86.656022]  [<f917e277>] omnibook_probe+0xc1/0x122 [omnibook]
[   86.656022]  [<c11850c7>] ? sysfs_create_link+0x17/0x20
[   86.656022]  [<c1335631>] platform_drv_probe+0x11/0x20
[   86.656022]  [<c133440d>] really_probe+0x4d/0x150
[   86.656022]  [<c133c67b>] ? pm_runtime_barrier+0x4b/0xb0
[   86.656022]  [<c13346ac>] driver_probe_device+0x3c/0x60
[   86.656022]  [<c13347a9>] __device_attach+0x49/0x60
[   86.656022]  [<c1334760>] ? __device_attach+0x0/0x60
[   86.656022]  [<c133353f>] bus_for_each_drv+0x4f/0x70
[   86.656022]  [<c13345ca>] device_attach+0x7a/0x90
[   86.656022]  [<c1334760>] ? __device_attach+0x0/0x60
[   86.656022]  [<c1333d85>] bus_probe_device+0x25/0x40
[   86.656022]  [<c1331f4c>] device_add+0x28c/0x380
[   86.656022]  [<c127d033>] ? kvasprintf+0x43/0x60
[   86.656022]  [<c1273504>] ? kobject_set_name_vargs+0x64/0x70
[   86.656022]  [<c1335ea7>] platform_device_add+0xe7/0x1a0
[   86.656022]  [<c1336094>] ? platform_device_alloc+0x54/0x70
[   86.656022]  [<f917e3e1>] omnibook_module_init+0xdd/0xfe [omnibook]
[   86.656022]  [<c1001255>] do_one_initcall+0x35/0x170
[   86.656022]  [<f917e304>] ? omnibook_module_init+0x0/0xfe [omnibook]
[   86.656022]  [<c1088afb>] sys_init_module+0xdb/0x230
[   86.656022]  [<c1125aa5>] ? sys_close+0x75/0xd0
[   86.656022]  [<c150a194>] syscall_call+0x7/0xb
[   86.656022] Code: 89 e5 57 bf ea ff ff ff 56 53 89 c3 83 ec 0c 85 c0  0f 84 56 01 00 00 8b 70 24 85 f6 74 75 eb 2e 85 05 c0 bc 2a f8 74 23 8b  46 04 <8b> 50 30 85 d2 74 09 8d 46 04 ff d2 85 c0 75 10 83 c6 04  bf ed 
[   86.656022] EIP: [<f917e06a>] omnibook_init+0x2c/0x178 [omnibook] SS:ESP 0068:efc0fe18
[   86.656022] CR2: 00000000746f6fa4
[   86.726198] ---[ end trace 0cac74e251ca94d6 ]---

```

---

### Post by tux_i on 2011-08-14
i just buy the nb520-10h yesterday ... i had try meego and ubuntu in usb live  ..same
 problem with rfkill : physical interface is block.

i will make ameego install soon

update !
wifi work on linux when i activate it on windows before

else for your hospital problem you can type : iwconfig wlan txpower=off to disable the wifi radio , else with rmmod it can work.
the orange led of wifi is always enable , i think it's a ath9k bug ...

if i find a solution , i'll mail you. but i think that the ath9k driver isn't optimize for toshiba nb520 netbook :(

---

### Post by chili555 on 2011-08-14
Has anyone tried:```
sudo rfkill block all
```

---

### Post by tux_i on 2011-08-15
yes,

but on meego live usb , the command doesn't exist . on ubuntu it work but no bluetooth is present.

i think i must install compact wireless before ??

---

### Post by IT Support on 2011-08-15
Maybe  you can disable wi-fi from bios  :) in my  notebook i anable wi-fi from bios, but  in this case u cann`t use wi-fi until you restart notebook and anable wi-fi in bios again :)

---

### Post by tux_i on 2011-08-15
good idea , but no bios option on tosh :D

so , my only option is to install ubuntu 11.04 or meego 1.2 on the harddrive and after make update and install compact wireless for trying.

---

### Post by fdrake on 2011-08-15
did you try?

```
sudo ifconfig wlan0 down
```

from 
> man ifconfig
......
down   This flag causes the driver for this interface to be shut down.
......

---

### Post by chili555 on 2011-08-15
> **tux_i said:**
> yes,

but on meego live usb , the command doesn't exist . on ubuntu it work but no bluetooth is present.

i think i must install compact wireless before ??I am not totally aware of every aspect of compat-wireless but can you please tell me what it provides that shuts down the wireless radio that the current driver doesn't? If I've understood the original question correctly, the issue is to turn off the wireless radio, not disable the driver.

To turn off wireless radio only and not bluetooth, please try:```
sudo rfkill block wireless
```

---

### Post by tux_i on 2011-08-15
if i read the first post the question is to disable the radio of this netbook in hsotpital

there is some way to doing it :
rfkill wlan0 blockall
ifconfig wlan0 down 
iwconfig txpower off 
rmmod ...

my problems with this chipset is 
- that i must ACTIVATE it with FN+F8 key on windows to ACCESS it on linux ... if not i can't see it with iwconfig
it' a major problem for me
- the bluetooth part of this doesn't work!;; i can't see it

if anybody can help me with that ( i see some problem on other forum)

---

### Post by chili555 on 2011-08-15
> **tux_i said:**
> ***if i read the first post the question is to disable the radio of this netbook in hsotpital***

there is some way to doing it :
rfkill wlan0 blockall
ifconfig wlan0 down 
iwconfig txpower off 
rmmod ...

my problems with this chipset is 
- that i must ACTIVATE it with FN+F8 key on windows to ACCESS it on linux ... if not i can't see it with iwconfig
it' a major problem for me
- the bluetooth part of this doesn't work!;; i can't see it

if anybody can help me with that ( i see some problem on other forum)Then you have an entirely different problem. I suggest you start a new thread and leave a link here. I'll be very glad to help.

---

