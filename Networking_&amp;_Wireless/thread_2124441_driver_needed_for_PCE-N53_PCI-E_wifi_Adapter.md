---
title: "driver needed for PCE-N53 PCI-E wifi Adapter"
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by sandman0842 on 2013-03-11
My lan1 is working perfectly, everything in my ubunto12.10 is working great after my initial install 7 days ago, but have 2 problems

1. my wifi recognizes my networks and connects just fine, but after that i get a freeze 
2. my dual monitors are stuck in 'mirrored' and i cannot unmirror them under any of my drivers. 

so do i have the wrong driver? which one should i pick for my wifi? 

go easy on me with terms, im n0ob :/

-sandman

---

### Post by varunendra on 2013-03-11
Welcome to the forums sandman0842 ! :)

Please open a terminal (Ctrl+Alt+T) and post back result of following commands (you may copy-paste to avoid typing errors) -
```
lspci -nnk | grep -iA2 net
lsmod
```
While posting, wrap the pasted output in 'Code' tags to preserve its formatting. (follow the 'Code tag example' link in my signature to see how).

---

### Post by sandman0842 on 2013-03-11
thank you for your help!

```
System-Product-Name:~$ lspci -nnk | grep -ia2 
net00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4 [1022:1404]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5 [1022:1405]
02:00.0 Network controller [0280]: Ralink corp. Device [1814:5592]
    Subsystem: ASUSTeK Computer Inc. Device [1043:851a]
    Kernel driver in use: rt2860
    Kernel modules: rt5592sta
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard [1043:8505]
    Kernel driver in use: r8169
```

and 

```
System-Product-Name:~$ lsmod
Module                  Size  Used by
dm_crypt               23012  1 
rfcomm                 46620  0 
bnep                   18141  2 
bluetooth             209249  10 rfcomm,bnep
nls_iso8859_1          12714  2 
kvm_amd                55605  0 
kvm                   414071  1 kvm_amd
ppdev                  17074  0 
eeepc_wmi              13110  0 
asus_wmi               24089  1 eeepc_wmi
sparse_keymap          13891  1 asus_wmi
snd_hda_codec_realtek    78147  1 
snd_hda_intel          33492  5 
snd_hda_codec         134213  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
usblp                  18141  0 
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78921  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                95595  0 
microcode              22804  0 
parport_pc             32689  1 
k10temp                13127  0 
i2c_piix4              13168  0 
serio_raw              13216  0 
rt5592sta            1176200  1 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
mac_hid                13206  0 
fglrx                4715455  176 
amd_iommu_v2           19098  1 fglrx
lp                     17760  0 
parport                46346  3 ppdev,parport_pc,lp
usb_storage            48839  1 
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
ghash_clmulni_intel    13221  0 
wmi                    19071  1 asus_wmi
r8169                  61651  0 
aesni_intel            51038  823 
cryptd                 20404  6 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
```


-sandman

---

### Post by varunendra on 2013-03-11
> **sandman0842 said:**
> 
02:00.0 Network controller [0280]: Ralink corp. Device [1814:**[COLOR="#FF0000"]5592[/COLOR]**]

```
System-Product-Name:~$ lsmod
Module                  Size  Used by
...
**[COLOR="#FF0000"]rt5592sta[/COLOR]**            1176200  1 
...
```

That seems like a brand new chip just launched into the market. Where did you get the driver (rt5592sta) for it ?

Please post outputs of -
```
modinfo rt5592sta
dmesg | grep -ie 5592 -e network
```

---

### Post by sandman0842 on 2013-03-11
i downloaded it from the disk that came with the wireless card...

output...
```
System-Product-Name:~$ sudo modinfo rt5592stafilename:       /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/rt5592sta.ko
version:        2.6.0.0_20120326
srcversion:     9E605E301B126FDDF16DE7D
alias:          pci:v00001814d00005592sv*sd*bc*sc*i*
depends:        
vermagic:       3.5.0-25-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
```

```
System-Product-Name:~$ sudo dmesg | grep -ie 5592 -e network
[    0.279850] pci 0000:02:00.0: [1814:5592] type 00 class 0x028000
[    8.222294] type=1400 audit(1362968684.921:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
[    8.973955] /home/sandman/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_asic.c:2601 assert KeyIdx < 4failed
[    8.973962] /home/sandman/Downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../common/cmm_asic.c:2601 assert KeyIdx < 4failed

```

---

### Post by sandman0842 on 2013-03-11
my friend is telling me that it could possibly be the _video driver_ or the _memory_ that is causing my OS to freeze and not allowing the monitors to unmirror themselves.

---

### Post by varunendra on 2013-03-11
> **sandman0842 said:**
> my friend is telling me that it could possibly be the _video driver_ or the _memory_ that is causing my OS to freeze and not allowing the monitors to unmirror themselves.

Could be. I know next to nothing about graphics drivers. But I do know that an incorrect graphics driver is most often the cause for system freezes.

One possible way to test that is to boot into recovery mode with safe graphics *(**failsafeX**, not sure if it is called the same in 12.10)* and see if the system freezes there or not. To get the grub menu *(if it does not appear by default)* to choose recovery mode, press and hold '**Shift**' key while the system is booting.

If the system works fine in recovery mode, then it is more likely the graphics driver. In that case, you should ask your question in a new thread in 'Hardware' section, with output of following -
```
sudo lshw -C display
```
..to get started.

---

### Post by sandman0842 on 2013-03-11
ok, i will pose my problem in the hardware section asap, but I'm having a problem with the 'shift key during reboot' thing. my friend and I both tried holding down the shift key during reboot process about 1 dozen times and nothing happens, but my keyboard is configured just fine as im able to access the bios. 

output... 

```
~$ sudo lshw -C display[sudo]
  *-display               
       description: VGA compatible controller
       product: Trinity [Radeon HD 7560D]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:44 memory:c0000000-cfffffff ioport:f000(size=256) memory:feb00000-feb3ffff

```

---

### Post by varunendra on 2013-03-11
> **sandman0842 said:**
> but I'm having a problem with the 'shift key during reboot' thing

In some cases it works with 'Esc' key (for reasons unknown to me) as mentioned here : [https://help.ubuntu.com/community/Grub2#GRUB_vs_GRUB_2](https://help.ubuntu.com/community/Grub2#GRUB_vs_GRUB_2)

Alternately, you can permanently set it to show up on startup by commenting out the **GRUB_HIDDEN_TIMEOUT=0** line in /etc/default/grub file :
```
gksu gedit /etc/default/grub
```
so it becomes -
> **#**GRUB_HIDDEN_TIMEOUT=0
Also, make sure the **GRUB_TIMEOUT=** line has a value higher than 0 (seconds) :
> GRUB_TIMEOUT=**10**
..proofread, save and close the file. Then do -
```
sudo update-grub
```

This will make its appearance permanent on boot up.

Also, not my field of expertise, but it seems you are using proprietary fglrx driver for your display adapter. Do you have ATI Catalyst Control Center installed with it (**fglrx-amdcccle** package)? Doesn't it provide the option to span or other things with dual monitors?

---

### Post by sandman0842 on 2013-03-13
_**Problem Solved!**_

my roommate took a turn at it, he found a patch online, noting that the 12.10 was buggy with the AMD HD 7000series, then he took the fglrx off and used the original driver that came with the initial boot up, thus negating the patch and fglrx driver all together. 
so apparently what went wrong was when i downloaded the fglrx driver, apparently its buggy, and ubuntu made a patch for it already. so the driver that comes with the 12.10 install is the one to use in the first place, no update needed for the AMD video driver. 

thank you so much for your persistence, knowledge and help! 

-sandman

---

### Post by varunendra on 2013-03-13
> **sandman0842 said:**
> ..took the fglrx off and used the original driver that came with the initial boot up, thus negating the patch and fglrx driver all together...

Wow! That used to be an issue when I registered on this forum. Didn't think such discrepancies still prevail!

Afaik, fglrx was (is??) known to offer more 'features' than the native driver, but at a cost of much higher resource usage. Not sure if that is still a fact too.

Anyway, thanks to YOU for the valuable feedback. :)

---

