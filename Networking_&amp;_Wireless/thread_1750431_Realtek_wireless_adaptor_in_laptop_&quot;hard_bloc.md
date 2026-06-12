---
title: "Realtek wireless adaptor in laptop &quot;hard blocked&quot; / unavailable after upgrade to natt"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by cpbl on 2011-05-05
Upgraded  a Lenovo T410s 10.10 to 11.04.

Wired network is fine, but wireless is no longer an option!

"sudo lshw -C  network" gives:

  *-network DISABLED
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.


So I installed some network tools package by searching for realtek in the software center.

"sudo rtl8139-diag" gives me:


Index #1: Found a RealTek (unknown chip type) adapter at 0x2000.
Realtek station address b6:f6:e0:51:02:80, chip type 'Unknown version'.
  Receiver configuration: Reception disabled
     Rx FIFO threshold 16 bytes, maximum burst 16 bytes, 8KB ring
  Transmitter disabled with normal settings, maximum burst 16 bytes.
  Flow control: Tx disabled  Rx disabled.
  The chip configuration is 0x00 0x00, MII half-duplex mode.
  Interrupt sources are pending.
   Rx Buffer Underrun indication.
   unknown-0200 indication.


"rfkill list" gives:

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
8: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no




In 10.10, pressing Fn-F5 would cycle the wireless and bluetooth on in four combos. Now it cycles on and off only the bluetooth.

Can anyone help me get access to my wireless card again?

---

### Post by josephmills on 2011-05-05
```

rfkill unblock all 

```
also try 
```

rfkill unblock wifi 

```

---

### Post by cpbl on 2011-05-05
Thanks. I tried those unblock commands. No effect. Same report from rfkill list.

There are no problems with the external wireless signal.

---

### Post by josephmills on 2011-05-05
this is a long shot but could we see a 
```

lsmod | grep dell

```
thanks

---

### Post by chili555 on 2011-05-05
> **josephmills said:**
> this is a long shot but could we see a 
```

lsmod | grep dell

```
thanksHe has a Lenovo, not a Dell, but I think this might be interesting:```
lsmod
```I wonder if Lenovo has a -laptop or -wmi driver that's not working as expected.

---

### Post by cpbl on 2011-05-05
lsmod on the Lenovo T410s says:

Module                  Size  Used by
binfmt_misc            17565  1 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
parport_pc             36959  0 
ppdev                  17113  0 
ipt_REJECT             12576  1 
ipt_LOG                17016  5 
xt_multiport           12597  2 
xt_limit               12711  7 
xt_tcpudp              12603  12 
ipt_addrtype           12599  4 
xt_state               12578  7 
ip6table_filter        12815  1 
i915                  514985  11 
ip6_tables             27845  1 ip6table_filter
drm_kms_helper         42136  1 i915
nf_nat_irc             12643  0 
nf_conntrack_irc       13383  1 nf_nat_irc
btusb                  18600  2 
snd_hda_codec_hdmi     28167  1 
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
drm                   227495  7 i915,drm_kms_helper
joydev                 17606  0 
snd_hda_codec_conexant    57511  1 
nf_nat_ftp             12649  0 
i2c_algo_bit           13400  1 i915
snd_hda_intel          33211  4 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
nf_nat                 25736  2 nf_nat_irc,nf_nat_ftp
snd_hwdep              13604  1 snd_hda_codec
nf_conntrack_ipv4      19640  9 nf_nat
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
thinkpad_acpi          81587  0 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
snd_seq_midi           13324  0 
video                  19438  1 i915
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
lp                     17825  0 
nvram                  14419  1 thinkpad_acpi
parport                46458  3 parport_pc,ppdev,lp
tpm_tis                18537  0 
uvcvideo               72195  0 
tpm                    22267  1 tpm_tis
tpm_bios               13684  1 tpm
intel_ips              18097  0 
videodev               82052  1 uvcvideo
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
nf_conntrack_ftp       13359  1 nf_nat_ftp
v4l2_compat_ioctl32    17078  1 videodev
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
nf_conntrack           81956  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
r8192se_pci           524220  0 
cfg80211              178528  1 r8192se_pci
iptable_filter         12810  1 
snd                    67382  19 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
serio_raw              13166  0 
ip_tables              27456  1 iptable_filter
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
x_tables               29581  11 ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
ahci                   25951  4 
libahci                26642  1 ahci
e1000e                159096  0

---

### Post by chili555 on 2011-05-05
Pardon me for stepping on my colleagues' toes.

We are on uncharted ground here. 11.04 has only been out a few days and we are all learning. I don't have a 410S, although I wish i did, so cpbl, you are going to have to help us learn. We may try a few things and fail, but, hopefully, we will all learn.

This look suspicious to me:> lsmod on the Lenovo T410s says:

Module Size Used by
---snip---
thinkpad_acpi 81587 0 
---snip---When we look at the module info, we see:> chili@LAPTOP60:~$ **modinfo thinkpad_acpi**
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko
license:        GPL
version:        0.24
description:    ThinkPad ACPI Extras
author:         Henrique de Moraes Holschuh <hmh@hmh.eng.br>
author:         Borislav Deianov <borislav@users.sf.net>
alias:          dmi:bvnIBM:bvrI[MU]ET??WW*
alias:          tpacpi
srcversion:     0B6457473BB90551EE1D20F
alias:          acpi*:LEN0068:*
alias:          acpi*:IBM0068:*
depends:        snd,nvram
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           experimental:Enables experimental features when non-zero (int)
parm:           debug:Sets debug level bit-mask (uint)
parm:           force_load:Attempts to load the driver even on a mis-identified ThinkPad when true (bool)
parm:           fan_control:Enables setting fan parameters features when true (bool)
parm:           brightness_mode:Selects brightness control strategy: 0=auto, 1=EC, 2=UCMS, 3=EC+NVRAM (uint)
parm:           brightness_enable:Enables backlight control when 1, disables when 0 (uint)
parm:           hotkey_report_mode:used for backwards compatibility with userspace, see documentation (uint)
parm:           volume_mode:Selects volume control strategy: 0=auto, 1=EC, 2=N/A, 3=EC+NVRAM (uint)
parm:           volume_capabilities:Selects the mixer capabilites: 0=auto, 1=volume and mute, 2=mute only (uint)
parm:           volume_control:Enables software override for the console audio control when true (bool)
parm:           index:ALSA index for the ACPI EC Mixer (int)
parm:           id:ALSA id for the ACPI EC Mixer (charp)
parm:           enable:Enable the ALSA interface for the ACPI EC Mixer (bool)
parm:           hotkey:Simulates thinkpad-acpi procfs command at module load, see documentation
parm:           bluetooth:Simulates thinkpad-acpi procfs command at module load, see documentation
parm:           video:Simulates thinkpad-acpi procfs command at module load, see documentation
parm:           light:Simulates thinkpad-acpi procfs command at module load, see documentation
parm:           cmos:Simulates thinkpad-acpi procfs command at module load, see documentation
parm:           led:Simulates thinkpad-acpi procfs command at module load, see documentation
parm:           beep:Simulates thinkpad-acpi procfs command at module load, see documentation
parm:           brightness:Simulates thinkpad-acpi procfs command at module load, see documentation
parm:           volume:Simulates thinkpad-acpi procfs command at module load, see documentation
parm:           fan:Simulates thinkpad-acpi procfs command at module load, see documentation
parm:           dbg_wlswemul:Enables WLSW emulation (uint)
***parm:           wlsw_state:Initial state of the emulated WLSW switch (bool)***
parm:           dbg_bluetoothemul:Enables bluetooth switch emulation (uint)
parm:           bluetooth_state:Initial state of the emulated bluetooth switch (bool)
parm:           dbg_wwanemul:Enables WWAN switch emulation (uint)
parm:           wwan_state:Initial state of the emulated WWAN switch (bool)
parm:           dbg_uwbemul:Enables UWB switch emulation (uint)
parm:           uwb_state:Initial state of the emulated UWB switch (bool)I am wondering if that means 'wireless switch state.'

Please try:```
sudo rmmod -f thinkpad_acpi
sudo modprobe thinkpad_acpi wlsw_state=1
```Now does your switch operate as expected? When you manipulate the switch and run:```
rfkill list all
```Can you reach a state that is not hard blocked? Does your wireless work??

Note to Chili: it may be "on" instead of "1"

---

### Post by cpbl on 2011-05-05
Thank you. I tried the rmmod and modprobe with =1 and =on. Neither had any effect.

rfkill list all still says:


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
12: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
14: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by cpbl on 2011-05-05
> **cpbl said:**
> Thank you. I tried the rmmod and modprobe with =1 and =on. Neither had any effect.



Sorry -- but I meant to report this reponse:

```
sudo modprobe thinkpad_acpi wlsw_state=1
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.

```

---

### Post by chili555 on 2011-05-05
> WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.May we see:```
cat /etc/modprobe.d/options
```Thanks.

---

### Post by cpbl on 2011-05-05
Guilty. I think I set this option when installing thinkfan:

"cat /etc/modprobe.d/options" gives:

options thinkpad_acpi fan_control=1

---

### Post by chili555 on 2011-05-05
That's easy to fix:```
sudo mv /etc/modprobe.d/options /etc/modprobe.d/options.conf
```Next, please place your right hand on my copy of C/C++ Programmer's Bible, autographed by Linus Torvalds, of course, and solemnly swear that switch #10 here is in the 'On' position. Please see attached.

---

### Post by cpbl on 2011-05-05
Gasp!! You're good! I never knew about that switch. BUT it turns out I have not mistakenly turned it off;  it is still on, showing green, and cycling it off/on makes no difference.

I'll swear in Stallman's name too...

---

### Post by josephmills on 2011-05-05
> **chili555 said:**
> Next, please place your right hand on my copy of C/C++ Programmer's Bible, autographed by Linus Torvalds, of course, and solemnly swear that switch #10 here is in the 'On' position. Please see attached.
not fair I want one

---

### Post by josephmills on 2011-05-05
> **cpbl said:**
> Gasp!! You're good! I never knew about that switch. BUT it turns out I have not mistakenly turned it off;  it is still on, showing green, and cycling it off/on makes no difference.

I'll swear in Stallman's name too...

turn it off(the switch) reboot then do ```
rfkill list 
``` it should be the same then turn it on and see if it goes away. try it back and forth a couple of time

---

### Post by cpbl on 2011-05-05
Thanks. No luck. I booted with HW switch off. I switched the HW switch after the first command, below, and back and forth after each.


```
[1731][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
[1731][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
[1732][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
[1732][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

The only difference now (hm, when!?) seems to be that Fn-F5 no longer toggles bluetooth off and on. It now cycles through 2^2 modes, as though it were switching wireless, but the wireless indicator light never goes on...

oh, wait, let me repeat experiment above, but with HW switch on, and cycling Fn-F5 : behaviour has changed! Did you mean I should reboot more than once?!

```
[1737][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
[1737][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
[1737][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
7: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
[1737][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
7: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
[1738][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
[1740][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
[1740][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
8: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
[1740][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
8: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
[1740][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
[1740][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

Yet even when both are unblocked, there's no light and I cannot turn on wireless in my toolbar...

Thank you

---

### Post by josephmills on 2011-05-05
try doing ```
rfkill unblock all 
``` in between the ```
rfkill list all
``` also try ```
rfkill unblock bluetooth
``` and ```
rfkill unblock wifi 
```

---

### Post by josephmills on 2011-05-05
> **cpbl said:**
> Thanks. No luck. I booted with HW switch off. I switched the HW switch after the first command, below, and back and forth after each.


```
[1731][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
[1731][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
[1732][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
[1732][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

The only difference now (hm, when!?) seems to be that Fn-F5 no longer toggles bluetooth off and on. It now cycles through 2^2 modes, as though it were switching wireless, but the wireless indicator light never goes on...

oh, wait, let me repeat experiment above, but with HW switch on, and cycling Fn-F5 : behaviour has changed! Did you mean I should reboot more than once?!

```
[1737][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
[1737][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
[1737][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
7: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
[1737][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
7: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
[1738][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
[1740][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
[1740][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
8: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no[b]
[1740][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
8: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no[/b]
[1740][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
[1740][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

Yet even when both are unblocked, there's no light and I cannot turn on wireless in my toolbar...

Thank you
sorry i did not see the part that i put into bold 
that is what you want, then we can go from there
> 
```

[1740][cpbl@:~]$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
8: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---

### Post by cpbl on 2011-05-05
Yes, I rebooted and rfkill list gives all unblocked.

Bizarrely, the network applet now has not only unchecked Enable wireless grayed out, but also the checked Enable network grayed out. I checked my user's permissions, and I have permission to deal with wireless.

I don't understand how I've got to where I am now (no longer hard blocked, good, but something else strange with network applet), let alone what to do next...

c

---

### Post by cpbl on 2011-05-05
Ah, but choosing "disconnect" in the network applet is possible, and after that the wired and wireless options are both available.

so.... thank you!!. My wireless is working now. But I don't understand what we learned /what we did.  I guess I'll see how it behaves in the future with reboots, etc...

---

### Post by josephmills on 2011-05-05
> **cpbl said:**
> Ah, but choosing "disconnect" in the network applet is possible, and after that the wired and wireless options are both available.

so.... thank you!!. My wireless is working now. But I don't understand what we learned /what we did.  I guess I'll see how it behaves in the future with reboots, etc...

you can not have wireless and auto eth going at the same time and all things need to be unblocked.

---

### Post by cpbl on 2011-05-05
I do right now (have auto eth0 and auto (dhcp) eth1 going together) and always have been able to under 10.10 and earlier. Or maybe I misunderstand?

---

### Post by cpbl on 2011-05-30
This problem persists. Every time I power down with the wireless turned off by software alone, ie in the taskbar networking applet/thingy, the machine boots up with wireless fixed to blocked, as I originally described, and the solution always requires another reboot after, seemingly to no effect!, unblocking it with the rfkill command.  And then when it comes up, the indicator light on this model fails to work properly until I use the applet to turn it on.  So several problems.

[https://bugs.launchpad.net/ubuntu/+source/rfkill/+bug/786233](https://bugs.launchpad.net/ubuntu/+source/rfkill/+bug/786233)

I have the same bug on my netbook... surely there are many others with it too?? No one has confirmed my bug, above.

---

