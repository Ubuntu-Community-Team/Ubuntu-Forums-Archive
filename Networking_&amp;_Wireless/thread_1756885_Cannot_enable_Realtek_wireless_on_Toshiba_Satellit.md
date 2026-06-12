---
title: "Cannot enable Realtek wireless on Toshiba Satellite Pro L500 in Ubuntu 11.04"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by ubut on 2011-05-12
I have just installed Ubuntu 11.04 on my brother's Toshiba Satellite Pro L500 and have spent all day trying to get the wireless to work. I am fairly new to Ubuntu (have played about without getting my hands dirty for a while), but I have tried everything I could find in the threads and still cannot solve the problem, so here goes...
 
the laptop does not have a physical wifi-switch (it should switch on-off with Fn+F8, which doesn't work), the drivers seem to be installed, but I cannot 'enable wireless', and I found that it is 'Hard blocked':[U]
sudo rfkill list all [/U]:
 0: phy0: Wireless LAN 
     Soft blocked: no 
     Hard blocked: yes 
 …
but 'rfkill unblock all' does nothing.
 
Some people mention that certain wireless devices might need to be switched on in another OS, but this is not an option, as I hastily removed Windows and have no way to re-install it.  


 Below, I put all sorts of information (which I only partly understand, but saw was advised in a 'How to post about wifi' thread):
 
Toshiba Satellite L500
 Ubuntu 11.04
 2.6.38-8-generic-pae i686
 
_Wireless Brand … (lspci)_:
 ...
 14:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
 
 _Interface (iwconfig wlan0)_:
 wlan0     802.11bg  Nickname:"rtl8191SEVA2" 
           Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated    
           Bit Rate:1 Mb/s    
           Retry:on   RTS thr:off   Fragment thr:off 
           Power Management:off 
           Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm 
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
_Modules (lsmod | grep r8192)_: (NOT SURE if there are others?)
 r8192se_pci           482548  0  
 cfg80211              156212  1 r8192se_pci
 
_Kernel boot messages (dmesg | grep r8192 )_:
 [10264.285931] ============> r8192E suspend call. 
 [10264.285935] r8192E support WOL call?????????????????????? 
 [10264.923747] ================>r8192E resume call.
 
_Network configuration (sudo lshw -C network)_:
 ...
 *-network DISABLED 
        description: Wireless interface 
        product: RTL8191SEvB Wireless LAN Controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:14:00.0 
        logical name: wlan0 
        version: 10 
        serial: b4:82:fe:8f:4a:d3 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=0 latency=0 link=no multicast=yes wireless=802.11bg 
        resources: irq:19 ioport:4000(size=256) memory:f2200000-f2203fff
 
_Scan for networks (iwlist scan wlan0)_:
 wlan0     Failed to read scan data : Network is down
 
 _Restarting the network (sudo /etc/init.d/networking restart )_:
  * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces 
  * Reconfiguring network interfaces...                                                    Ignoring unknown interface eth0=eth0.

---

### Post by chili555 on 2011-05-12
Let's have a look at:```
lsmod | grep wmi
```Thanks.

---

### Post by ubut on 2011-05-12
super quick reply. cool!

_lsmod | grep wmi_:

snd_rawmidi            25269  1 snd_seq_midi
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

---

### Post by chili555 on 2011-05-12
Hmmm. No acer-wmi or similar. Let's see all of:```
lsmod
```Something should be driving your hotkeys and isn't doing so correctly.

---

### Post by ubut on 2011-05-12
here goes (lsmod):

Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
rfcomm                 38125  8 
binfmt_misc            13213  1 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
joydev                 17322  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255820  1 
btusb                  18160  2 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
snd_hda_intel          24140  4 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
i915                  450979  3 
r8192se_pci           482548  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
psmouse                59039  0 
uvcvideo               66851  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  1 r8192se_pci
serio_raw              12990  0 
snd                    55295  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
drm                   184133  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
sparse_keymap          13666  0 
toshiba_bluetooth      12711  0 
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  4 
libahci                25548  1 ahci
r8169                  46630  0 


Regarding the hotkeys (you mean my Fn+F8 that should toggle the wifi?), all the other Fn+... (sound, etc.) work, so I thought it was a driver or some other similar problem (admittedly I am in deep waters, and don't really know).

---

### Post by chili555 on 2011-05-12
Have you tried:```
[COLOR="Red"]sudo[/COLOR] rfkill unblock all
```Please do:```
sudo tail -f /var/log/syslog
```Leave the terminal open as you manipulate the switch. Are there any interesting messages that appear in syslog?

Are you certain the Fn+F8 key is not a multi-function switch? That is, one press is bluetooth, second is bluetooth and wireless, third is wireless and fourth is none. I have one of those keys on my IBM T40.

---

### Post by ubut on 2011-05-12
I have tried
```
sudo rfkill unblock all
```and variations, e.g. rfkill unblock wifi
then I would always check
 ```
sudo rfkill list all
```and always get:

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: noregarding syslog: I tried what you said, but it would not react to me pressing Fn+F8, or any other Fn combination. It did give the following (every time):

> May 13 00:41:54 ArjanPro kernel: [17727.437705] atkbd serio0: Unknown key pressed (translated set 2, code 0xbd on isa0060/serio0).
May 13 00:41:54 ArjanPro kernel: [17727.437709] atkbd serio0: Use 'setkeycodes e03d <keycode>' to make it known.
May 13 00:41:54 ArjanPro kernel: [17727.445189] atkbd serio0: Unknown key released (translated set 2, code 0xbd on isa0060/serio0).
May 13 00:41:54 ArjanPro kernel: [17727.445193] atkbd serio0: Use 'setkeycodes e03d <keycode>' to make it known.
May 13 01:17:01 ArjanPro CRON[4955]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 13 02:02:32 ArjanPro kernel: [22564.871197] atkbd serio0: Unknown key pressed (translated set 2, code 0xbd on isa0060/serio0).
May 13 02:02:32 ArjanPro kernel: [22564.871204] atkbd serio0: Use 'setkeycodes e03d <keycode>' to make it known.
May 13 02:02:32 ArjanPro kernel: [22564.878753] atkbd serio0: Unknown key released (translated set 2, code 0xbd on isa0060/serio0).
May 13 02:02:32 ArjanPro kernel: [22564.878777] atkbd serio0: Use 'setkeycodes e03d <keycode>' to make it known.
May 13 02:17:01 ArjanPro CRON[5406]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)the last entry being almost an hour old.

Also,
I am pretty sure Fn+F8 is not a multi-function switch. I have checked this by seeing if anything changed in 'rfkill list all' and in the networks icon in the tray when I pressed it, but nothing. Should\can I check what the combination is mapped to? and how?

---

### Post by ubut on 2011-05-12
just to say that I'll be out of action for a while (bed time), but thanks for your help so far!

---

### Post by chili555 on 2011-05-12
At least for now, I am stumped. Let me sleep on it.

I wonder if this helps us: /etc/acpi/events/tosh-wireless and /etc/acpi/tosh-wireless.sh

In this case, *tosh* refers to Toshiba.

See you tomorrow.

---

### Post by chili555 on 2011-05-12
Please try:```
sudo modprobe omnibook wifi=1
```Now does Fn+F8 work?

Please see:```
modinfo omnibook
```

---

### Post by ubut on 2011-05-13
I checked /etc/acpi/events/tosh-wireless

>  # /etc/acpi/events/tosh-wireless
  # This is called when the user presses the wireless button and calls
  # /etc/acpi/wireless.sh for further processing.
  

  event=hkey VAL[DZ] 00000001 00000142
  action=/etc/acpi/tosh-wireless.sh
 and /etc/acpi/tosh-wireless.sh
> #!/bin/sh 
  
 test -f /usr/share/acpi-support/key-constants || exit 0 
  
 . /usr/share/acpi-support/state-funcs 
  
 if isAnyWirelessPoweredOn; then 
     if [ -x /usr/bin/toshset ]; then 
         if `toshset -bluetooth | grep -q attached`; then 
                 toshset -bluetooth off 
                 toggleAllWirelessStates 
         else 
                 toshset -bluetooth on 
         fi 
     else 
     toggleAllWirelessStates 
     fi 
 else 
         toggleAllWirelessStates 
 fi
note: in /etc/acpi i have tosh-wireless.sh, but also asus-wireless.sh, ibm-wireless.sh
 
and I tried 
```
sudo /etc/acpi/tosh-wireless.sh up
```with no results, or anything.

Then, I looked at modinfo omnibook
> description:    Kernel interface for HP OmniBook, HP Pavilion, Toshiba Satellite and Compal ACL00 laptops
...
parm:           wifi:Use 0 to disable, 1 to enable Wifi adapter control (int)
...and the first time I bashed
```
sudo modprobe omnibook wifi=1

```the screen went black, and there was some message (which I couldn't make out, but I don't think looked promising). When I pressed a key (at random) it disappeared, not giving me time to write any of it down. I tried again, and it would just hang there, not doing anything, and not giving any message, until I Cntrl+C -ed it.

Not really sure what to do...

---

### Post by chili555 on 2011-05-13
> Not really sure what to do...I'm not, either. I found out about omnibook here: [http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=44430](http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=44430)

Of course, without the hardware in question, I have no idea if it would work or not. I was quite surprised to see that omnibook is part of the kernel in Natty.

In the forum post I gave you, the poster says:> #modprobe omnibook ectype=12Looking at *modinfo omnibook*, it says:> parm: [COLOR="Red"]ectype[/COLOR]:Type of embedded controller firmwareYou might look in dmesg and see if you can find the ectype. Maybe we need to do:```
sudo modprobe omnibook ectype=?? wifi=1
```Look for the embedded controller type with:```
dmesg | grep -e ectype -e embed
dmesg | grep -i ec
```If you want to zip up your entire dmesg, I'll help look:```
dmesg > ubut_dmesg.txt
zip ubut_dmesg.zip ubut_dmesg.txt
```In your user directory you will find the zip; attach it to your reply using the paperclip tool at the top of the reply box.

I am off to learn more about omnibook.

---

### Post by chili555 on 2011-05-13
This is interesting:  [http://answerpot.com/showthread.php?540534-2009%2Fdevel%2Fkernel%2Fdefault%2Fdrivers%2Fmodule-omnibook+-+Add+another+quirk+for+Toshiba+Satellite+L500+%28%23135](http://answerpot.com/showthread.php?540534-2009%2Fdevel%2Fkernel%2Fdefault%2Fdrivers%2Fmodule-omnibook+-+Add+another+quirk+for+Toshiba+Satellite+L500+%28%23135)...> @@ -57,6 +52,13 @@



+
+ 2010-06-23
+ 0.0_20090720
+ [COLOR="Red"]Add another quirk for Toshiba Satellite L500[/COLOR] (#13575).
+ Ozan Ã&#8225;aÄ&#376;layan
+

2010-06-14
0.0_20090720That suggests that omnibook is supposed to work with your machine...hopefully...maybe...

This is kinda fun! I feel like when I went to Skip Barber and my instructor said, "What do you care, it's not your equipment."

---

### Post by ubut on 2011-05-13
so... I had a look at the link you sent me :[URL="http://forums.computers.toshiba-euro...threadID=44430"] http://forums.computers.toshiba-euro...threadID=44430
[/URL] and tried
```
modprobe omnibook ectype=12

```not knowing what to expect.

It created the folder /proc/omnibook , but it is empty, whereas in the thread they say:
> #modprobe omnibook ectype=12

now /proc/omnibook is correctly populated for me

#ls
blank  bluetooth  display  dmi  lcd  temperature  throttling  version  wifi

and then...then I looked in dmesg, as you advised, but could not find any ectype entry, so I've attached the zip file, in case you know what to look for better than I do (which isn't hard really).

this post from the same Toshiba forum scares and annoys me!:
> There seems to be NO POSSIBILITY to turn on wifi from within Linux, if  it was not turned on (using the FN/F8 combination) prior to installing  Linux. I had to order the recover DVD, install windows, turn the wifi  on, and re-install Linux. and it's not even an option for me.

so, I'll run off and see what I can find out about ectype

---

### Post by chili555 on 2011-05-13
> [10405.398884] omnibook: Driver version 2.20090707-trunk.
[10405.398888] omnibook: Forced load with EC type 12.
[10405.400775][COLOR="Red"] BUG: unable to handle kernel paging request at 746f6fa4[/COLOR]
[10405.400926] IP: [<fc75006a>] omnibook_init+0x2c/0x178 [omnibook]
[10405.401028] *pdpt = 000000002d127001 *pde = 0000000000000000 
[10405.401123] [COLOR="Red"]Oops[/COLOR]: 0000 [#1] SMP A kernel oops is never a good thing. I don't think ectype=12 is correct. More reading...

I'd go ahead and remove omnibook until we learn more:```
sudo rmmod -f omnibook
```

---

### Post by chili555 on 2011-05-13
Would you please try:```
sudo rmmod -f omnibook
sudo modprobe omnibook ectype=14 wireless=1
```Now does Fn+F8 work? Any interesting messages here?```
dmesg | tail -n10
```

---

### Post by ubut on 2011-05-13
I'll quickly post what you told me to try (as I don't really know what it is telling me), no luck: still Hard blocked and no wifi,
and run off to see what else I can find...

(note: I get an error with rmmod ... . Don't know if this is because I restarted my laptop in the mean time (of course hibernate is having trouble too))

> $ sudo rmmod -f omnibook

ERROR: Removing 'omnibook': No such file or directory

$ sudo modprobe omnibook ectype=14 wifi=1

$ dmesg | tail -n10

[  146.504007]  [<fb2323e1>] omnibook_module_init+0xdd/0xfe [omnibook]
[  146.504007]  [<c1003165>] do_one_initcall+0x35/0x170
[  146.504007]  [<fb232304>] ? omnibook_module_init+0x0/0xfe [omnibook]
[  146.504007]  [<c10922db>] sys_init_module+0xdb/0x230
[  146.504007]  [<c1131025>] ? sys_close+0x75/0xd0
[  146.504007]  [<c100ab5f>] sysenter_do_call+0x12/0x28
[  146.504007] Code: 89 e5 57 bf ea ff ff ff 56 53 89 c3 83 ec 0c 85 c0 0f 84 56 01 00 00 8b 70 24 85 f6 74 75 eb 2e 85 05 a0 cc 22 fb 74 23 8b 46 04 <8b> 50 30 85 d2 74 09 8d 46 04 ff d2 85 c0 75 10 83 c6 04 bf ed 
[  146.504007] EIP: [<fb23206a>] omnibook_init+0x2c/0x178 [omnibook] SS:ESP 0068:efb31e18
[  146.504007] CR2: 00000000746f6fa4
[  146.574892] ---[ end trace 042a564efbb5948d ]---


---

### Post by chili555 on 2011-05-13
> Don't know if this is because I restarted my laptop in the mean timeExactly; without an explicit .conf file, omnibook was not reloaded on reboot. We're not going to write a conf file until we (hopefully) find the magic combination of commands.> [ 146.504007] [<fb2323e1>] omnibook_module_init+0xdd/0xfe [omnibook]
[ 146.504007] [<c1003165>] do_one_initcall+0x35/0x170
[ 146.504007] [<fb232304>] ? omnibook_module_init+0x0/0xfe [omnibook]
[ 146.504007] [<c10922db>] sys_init_module+0xdb/0x230
[ 146.504007] [<c1131025>] ? sys_close+0x75/0xd0
[ 146.504007] [<c100ab5f>] sysenter_do_call+0x12/0x28
[ 146.504007] Code: 89 e5 57 bf ea ff ff ff 56 53 89 c3 83 ec 0c 85 c0 0f 84 56 01 00 00 8b 70 24 85 f6 74 75 eb 2e 85 05 a0 cc 22 fb 74 23 8b 46 04 <8b> 50 30 85 d2 74 09 8d 46 04 ff d2 85 c0 75 10 83 c6 04 bf ed
[ 146.504007] EIP: [<fb23206a>] omnibook_init+0x2c/0x178 [omnibook] SS:ESP 0068:efb31e18
[ 146.504007] CR2: 00000000746f6fa4
[ 146.574892] ---[ end trace 042a564efbb5948d ]--- This looks disappointing. I'd love to see the ten or so lines preceding this; I suspect it's also a kernel oops.```
dmesg | tail -n25
```I haven't been able to find a README or guide for omnibook yet.

---

### Post by chili555 on 2011-05-13
Lots of interesting stuff here: [http://ubuntuforums.org/showthread.php?t=316358](http://ubuntuforums.org/showthread.php?t=316358)

PS- Do you have a Phoenix BIOS?

---

### Post by ubut on 2011-05-13
I've put in more than 25 lines. I start from where I first see omnibook and then the oops. the only difference (from the zip file) I see is that now it says ''EC type 14'':

> [  146.501608] omnibook: Driver version 2.20090707-trunk.
[  146.501611] omnibook: Forced load with EC type 14.
[  146.501781] BUG: unable to handle kernel paging request at 746f6fa4
[  146.501930] IP: [<fb23206a>] omnibook_init+0x2c/0x178 [omnibook]
[  146.502031] *pdpt = 000000002db3d001 *pde = 0000000000000000 
[  146.502126] Oops: 0000 [#1] SMP 
[  146.502191] last sysfs file: /sys/devices/system/cpu/cpu1/cache/index2/shared_cpu_map
[  146.502293] Modules linked in: omnibook(+) parport_pc ppdev binfmt_misc rfcomm sco bnep l2cap joydev snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm btusb bluetooth snd_seq_midi r8192se_pci i915 snd_rawmidi snd_seq_midi_event snd_seq drm_kms_helper snd_timer snd_seq_device drm cfg80211 psmouse uvcvideo serio_raw snd videodev i2c_algo_bit soundcore snd_page_alloc video sparse_keymap toshiba_bluetooth lp parport ahci libahci r8169
[  146.503184] 
[  146.503215] Pid: 1820, comm: modprobe Not tainted 2.6.38-8-generic-pae #42-Ubuntu TOSHIBA Satellite Pro L500/KSWAA
[  146.503382] EIP: 0060:[<fb23206a>] EFLAGS: 00010206 CPU: 0
[  146.503475] EIP is at omnibook_init+0x2c/0x178 [omnibook]
[  146.503545] EAX: 746f6f74 EBX: fb22c6fc ECX: 00000000 EDX: eda74c40
[  146.503637] ESI: fb22a2e8 EDI: ffffffea EBP: efb31e30 ESP: efb31e18
[  146.503730]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[  146.503800] Process modprobe (pid: 1820, ti=efb30000 task=ed99d860 task.ti=efb30000)
[  146.503919] Stack:
[  146.503952]  00000034 00000040 000080d0 0000009c 00000003 13b13b2a efb31e4c fb232277
[  146.504007]  c11903b7 00000001 edb6a608 fb22c014 fb22c014 efb31e54 c134e661 efb31e78
[  146.504007]  c134d43d edb6a664 00000000 efb31e78 c135562b edb6a608 ffffffed fb22c014
[  146.504007] Call Trace:
[  146.504007]  [<fb232277>] omnibook_probe+0xc1/0x122 [omnibook]
[  146.504007]  [<c11903b7>] ? sysfs_create_link+0x17/0x20
[  146.504007]  [<c134e661>] platform_drv_probe+0x11/0x20
[  146.504007]  [<c134d43d>] really_probe+0x4d/0x150
[  146.504007]  [<c135562b>] ? pm_runtime_barrier+0x4b/0xb0
[  146.504007]  [<c134d6dc>] driver_probe_device+0x3c/0x60
[  146.504007]  [<c134d7d9>] __device_attach+0x49/0x60
[  146.504007]  [<c134d790>] ? __device_attach+0x0/0x60
[  146.504007]  [<c134c56f>] bus_for_each_drv+0x4f/0x70
[  146.504007]  [<c134d5fa>] device_attach+0x7a/0x90
[  146.504007]  [<c134d790>] ? __device_attach+0x0/0x60
[  146.504007]  [<c134cdb5>] bus_probe_device+0x25/0x40
[  146.504007]  [<c134af7c>] device_add+0x28c/0x380
[  146.504007]  [<c1288c53>] ? kvasprintf+0x43/0x60
[  146.504007]  [<c127efc4>] ? kobject_set_name_vargs+0x64/0x70
[  146.504007]  [<c134ee67>] platform_device_add+0xe7/0x1a0
[  146.504007]  [<c134f054>] ? platform_device_alloc+0x54/0x70
[  146.504007]  [<fb2323e1>] omnibook_module_init+0xdd/0xfe [omnibook]
[  146.504007]  [<c1003165>] do_one_initcall+0x35/0x170
[  146.504007]  [<fb232304>] ? omnibook_module_init+0x0/0xfe [omnibook]
[  146.504007]  [<c10922db>] sys_init_module+0xdb/0x230
[  146.504007]  [<c1131025>] ? sys_close+0x75/0xd0
[  146.504007]  [<c100ab5f>] sysenter_do_call+0x12/0x28
[  146.504007] Code: 89 e5 57 bf ea ff ff ff 56 53 89 c3 83 ec 0c 85 c0 0f 84 56 01 00 00 8b 70 24 85 f6 74 75 eb 2e 85 05 a0 cc 22 fb 74 23 8b 46 04 <8b> 50 30 85 d2 74 09 8d 46 04 ff d2 85 c0 75 10 83 c6 04 bf ed 
[  146.504007] EIP: [<fb23206a>] omnibook_init+0x2c/0x178 [omnibook] SS:ESP 0068:efb31e18
[  146.504007] CR2: 00000000746f6fa4
[  146.574892] ---[ end trace 042a564efbb5948d ]---I too can't find much on omnibook. 

but they all (e.g. the Toshiba forum you had sent my way) seem to say:
 /proc/omnibook needs to be populated, e.g.
> #ls
blank  bluetooth  display  dmi  lcd  temperature  throttling  version  wifi
and then to use
```
echo 1 >/proc/omnibook/wifi

```but mine is not ''populated''. it's empty.

also I wanted to try with another ectype (as mentioned in the last thread you sent me, using 
```
sudo modprobe -r omnibook
sudo modprobe omnibook ectype=14 && dmesg | grep omnibook && hcitool dev

```with different ectype numbers, 
so I bashed
> sudo rmmod -f omnibook
ERROR: Removing 'omnibook': Device or resource busy

sudo modprobe -r omnibook
the last just hung. so I was wondering if ```
sudo make unload
``` is the same?

---

### Post by ubut on 2011-05-13
I'm guessing I have SMBIOS

> sudo dmidecode -t 0
# dmidecode 2.9
SMBIOS 2.5 present.
...

---

### Post by ubut on 2011-05-13
I just found a thread (in french unfortunately, but I think I got the gist of it):
[COLOR=Blue][http://forum.ubuntu-fr.org/viewtopic.php?id=367563](http://forum.ubuntu-fr.org/viewtopic.php?id=367563)
[/COLOR] 
says (in 2010) that he solved the problem with
```
sudo modprobe r8192se_pci
```and then ''suppressing'' (french-ism?) the file /etc/modprobe.d/ndiswrapper (which I don't have)

it didn't do anything for me, still I wonder: should I be looking at this r8192se_pci?

---

### Post by chili555 on 2011-05-13
> I was wondering if
Code:

sudo make unload

is the same?Nope. 'make' looks for a Makefile in the current directory with a script telling how to proceed. We have none.

If the system is hanging trying to stop omnibook, I'd reboot.

Please see:  [http://ubuntuforums.org/showthread.php?t=316358&page=11](http://ubuntuforums.org/showthread.php?t=316358&page=11)

You might try:```
sudo modprobe omnibook userset=1 wireless=1
```Then check dmesg:```
dmesg | tail -n25
```> [ 146.501608] omnibook: Driver version 2.20090707-trunk.
[ 146.501611] omnibook: Forced load with EC type 14.
[ 146.501781] BUG: unable to handle kernel paging request at 746f6fa4
[ 146.501930] IP: [<fb23206a>] omnibook_init+0x2c/0x178 [omnibook]
[ 146.502031] *pdpt = 000000002db3d001 *pde = 0000000000000000
[ 146.502126] Oops: 0000 [#1] SMP Another kernel oops, as I suspected...sigh!

I am running extremely low on talent/ideas/mojo.

---

### Post by chili555 on 2011-05-13
> **ubut said:**
> I just found a thread (in french unfortunately, but I think I got the gist of it):
[COLOR=Blue][http://forum.ubuntu-fr.org/viewtopic.php?id=367563](http://forum.ubuntu-fr.org/viewtopic.php?id=367563)
[/COLOR] 
says (in 2010) that he solved the problem with
```
sudo modprobe r8192se_pci
```and then ''suppressing'' (french-ism?) the file /etc/modprobe.d/ndiswrapper (which I don't have)

it didn't do anything for me, still I wonder: should I be looking at this r8192se_pci?You already have it loaded, remember?> Modules (lsmod | grep r8192): (NOT SURE if there are others?)
[COLOR="Red"]r8192se_pci[/COLOR] 482548 0
cfg80211 156212 1 r8192se_pciThat's the driver for the wireless card that won't work until the system turns the card on.

---

### Post by ubut on 2011-05-15
hey chili,
sorry for the lack of reply, but i thought with it all day yesterday and got the wireless to work, but was knackered by the end of it.

so, basically i cheated\gave up. i followed the advice in the toshiba forum you sent my way, got a copy of windows xp, installed it and all the toshiba drivers, then switched on the wireless (with fn+f8 in windowns, and istalled ubuntu all over. the wireless now works, i can switch it on\off from the network manager icon, but of course fn+f8 still does absolutely nothing. the interesting thing is that the other fn keys do their thing.

i guess there should be a _big warning_ for anyone with a satellite pro that wants to install ubuntu.

anyhow, i'm happy like this, also because i have to return the laptop to my brother tomorrow, and the monitor still gives me problems (on time it will start up in full 16:9, and the next time with huge black\cutt-off edges), so i have to go fight with that.

_super thanks! _for all your help and patients, and i hope you don't mind my giving up (on it and so on your help).

---

### Post by chili555 on 2011-05-15
I'm glad it's working no matter how. Much as I would like to think otherwise, we can't fix everything. I actually think it's a design flaw and blatantly anti-competitive that you can only manipulate the wireless using Windows.

---

### Post by lynxmaniac on 2011-08-09
Hi ubut /chilli555,

I would like to share the fixes of the same issue I was facing before few months on Toshiba Satellite L510 laptop with ubuntu 11.04. I hope this helps someone having same issues.

You can try to do so by following below mentioned steps:
(1) Please try to install 'ndisgtk' (to use windows driver on ubuntu)
> sudo apt-get install ndiswrapper-common
> sudo apt-get install ndiswrapper-utils-1.9

(2) Download relevant Realtek wireless driver
([http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PNid=13&PFid=21&Level=4&Conn=3](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PNid=13&PFid=21&Level=4&Conn=3))

(3) Install/Browse Realtek Drivers by opening ndiswrapper/windows wireless driver app & confirm it shows 'Hardware Present=Yes"

(4) Run following commands in terminal:
> ndiswrapper -l
> ndiswrapper -m
> ifconfig wlan0 up
> ifconfig

Now try to connect with wireless from network manager/wicd UI.

LynxManiac,
Freelance Server Administrator (Setup & Maintenance)
Website: [http://bit.ly/oumSXm](http://bit.ly/oumSXm)
[Click here]("http://www.infowaywebsolutions.com/domains/") for Cheap Domain Registration & Quality Web Hosting

---

### Post by megajuan88 on 2013-04-06
i have the same problem but in my toshiba satellite pro c840

---

### Post by chili555 on 2013-04-06
> **megajuan88 said:**
> i have the same problem but in my toshiba satellite pro c840What is your exact wireless device?```
lspci -nn | grep 0280
```

---

