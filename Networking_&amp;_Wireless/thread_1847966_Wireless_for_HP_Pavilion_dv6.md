---
title: "Wireless for HP Pavilion dv6"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by newtoubun2 on 2011-09-21
I've just downloaded Ubuntu 11.04 onto my new HP laptop and i cannot get the wireless to work.  Does anyone know what I should do to get connected to the internet?

---

### Post by josephmills on 2011-09-21
Hi there and welcome to the forum ! 
could you please open your terminal and type in 
```
lspci -nn 
```
```
lsmod
```
```
rfkill list all
```

and paste here thanks

---

### Post by newtoubun2 on 2011-09-21
I put those commands into the terminal, but I can't paste the results into this response because (since I can't get online when I'm using Ubuntu) I'm using my roommates internet to be on the forum.  Can you tell me what I should be looking for in the results, or would it be too complicated to explain?

---

### Post by kvmapr on 2011-09-21
I seem to have the same issues after accepting the latest update on my HP DV6 running 11.04. But I have an old fashioned ethernet cable that stretches all the way across the room to my wireless router, so I can post my outputs to the commands above:

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
uvcvideo               66851  0 
snd_rawmidi            25269  1 snd_seq_midi
videodev               75143  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
hp_wmi                 13418  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13666  1 hp_wmi
i915                  451068  3 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rc_rc6_mce             12454  0 
ir_lirc_codec          12770  0 
lirc_dev               18720  1 ir_lirc_codec
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
hp_accel               21632  0 
ir_rc6_decoder         12490  0 
drm_kms_helper         40745  1 i915
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
ene_ir                 22309  0 
drm                   184164  4 i915,drm_kms_helper
rc_core                25760  9 rc_rc6_mce,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ene_ir
psmouse                59039  0 
lis3lv02d              19285  1 hp_accel
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
input_polldev          13735  1 lis3lv02d
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
r8169                  46630  0 
libahci                25548  1 ahci

rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

Thanks for any help you can provide.

---

### Post by Jagoly on 2011-09-21
well, I have a dv6, and the wireless work fine out of the box on 11.04.

What model of the dv6 is it? if you're unsure, what are some of the basic specs (cpu, hard drive size ect)?

---

### Post by kvmapr on 2011-09-21
It's a dv6-2150-us.

And it worked find when I first upgraded to 11.04 as well. But today there was a sizeable software update from Ubuntu. I applied it but unfortunately had to walk away and couldn't watch everything that was modified.

After the restart however, wireless stopped working.

If you haven't applied the latest update, beware!

---

### Post by newtoubun2 on 2011-09-21
Mine is a dv6-6135DX, and where kvmapr's has a network and ethernet controller, mine only shows an ethernet one.

---

### Post by wildmanne39 on 2011-09-21
Hi kvmapr, it says your hardware switch is off, please see if there is a button to turn it on, or you may have to hit like fn f11 or a key like that.

Also if that does not work make sure a setting in your bios did not turn it off, then if you still have problems try this.
```
sudo rmmod -f hp-wmi
```
if you have to use the command use it as a last resort and if it works we will need to make it permanent.
Than you

---

### Post by kvmapr on 2011-09-21
Thanks everyone for the help. The wireless switch glows amber, which indicates its off, hard block. But it's also non-responsive when I push it to turn wireless on. I found another thread here that discussed a similar problem. In that thread there was a link to some directions that I've followed to successfully activate the wireless driver.

That thread is at this link:
[http://ubuntuforums.org/showthread.php?t=1789409](http://ubuntuforums.org/showthread.php?t=1789409)

And the instructions I followed are at this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by wildmanne39 on 2011-09-21
Hi, your welcome! I am glad it is working.

---

### Post by newtoubun2 on 2011-09-22
I got my computer connected with an Ethernet cable, so now I can paste the results of my terminal commands.

lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1705]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9641]
00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:1714]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:1707]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:1709]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:170a]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:170b]
00:10.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB XHCI Controller [1022:7812] (rev 03)
00:10.1 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB XHCI Controller [1022:7812] (rev 03)
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] [1022:7804]
00:12.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
00:12.2 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
00:13.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
00:13.2 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] Hudson SMBus Controller [1022:780b] (rev 13)
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] Hudson IDE Controller [1022:780c] (rev 40)
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] Hudson LPC Bridge [1022:780e] (rev 11)
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] Hudson PCI Bridge [1022:780f] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc NI Whistler [AMD Radeon HD 6600M Series] [1002:6741]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
03:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)

lsmod
Module                  Size  Used by
cdc_acm                22574  0 
usb_storage            53538  1 
uas                    17996  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
joydev                 17606  0 
snd_hda_codec_idt      71137  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
radeon                982197  1 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ttm                    76664  1 radeon
hp_wmi                 13706  0 
uvcvideo               72195  0 
snd_timer              29602  2 snd_pcm,snd_seq
drm_kms_helper         42136  1 radeon
sparse_keymap          13898  1 hp_wmi
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               82052  1 uvcvideo
drm                   227495  3 radeon,ttm,drm_kms_helper
v4l2_compat_ioctl32    17078  1 videodev
psmouse                73535  0 
rts_pstor             440614  0 
serio_raw              13166  0 
i2c_algo_bit           13400  1 radeon
i2c_piix4              13303  0 
snd                    67382  14 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                13119  0 
soundcore              12680  1 snd
xhci_hcd               77643  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  0 
hp_accel               21880  0 
lis3lv02d              19893  1 hp_accel
input_polldev          14007  1 lis3lv02d
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  1 
libahci                26642  1 ahci
r8169                  48022  0 
pata_atiixp            13165  0 

and nothing comes up when I put in "rfkill list all."

Can anybody help me?

---

### Post by wildmanne39 on 2011-09-22
Hi, the driver you need, you will have to download, and compile it, here is a link with directions.
The link is here start at 58, and all  the directions are in post 58. If you need more help post back here.
Thank you
[http://ubuntuforums.org/showthread.php?t=1779005&page=6](http://ubuntuforums.org/showthread.php?t=1779005&page=6)

---

### Post by newtoubun2 on 2011-09-22
When I got to the part to input "make" I got the reply:  "make: *** No rule to make target `install'.  Stop."

---

### Post by wildmanne39 on 2011-09-22
Hi, let's make sure you have the required packages installed to compile the driver, I believe you do but we will make sure.
```
sudo apt-get install build-essential && sudo apt-get install linux-headers-generic
```

Also I good idea to make sure is system is up to date first.

I do not think you are in the directory of the driver, take the file that you extracted and drag it to the terminal that will put you in the directory for sure then run the commands again.
Thank you

---

