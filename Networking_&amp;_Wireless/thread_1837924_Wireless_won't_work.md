---
title: "Wireless won't work"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by Howlin1 on 2011-09-02
Hello,
I installed Ubuntu 11.04 today and I can't get the internet to work on it without having the ethernet cable plugged in. I did do 
```

sudo lshw ~C network

```and the wireless card vendor I got back is Atheros Communications
I did search for a solution but they seems to be aimed towards Broadcom. I'm a noob with Ubuntu, so I don't know what else to do. Will anyone help me?

---

### Post by nm_geo on 2011-09-02
> **Howlin1 said:**
> Hello,
I installed Ubuntu 11.04 today and I can't get the internet to work on it without having the ethernet cable plugged in. I did do 
```

sudo lshw ~C network

```and the wireless card vendor I got back is Atheros Communications
I did search for a solution but they seems to be aimed towards Broadcom. I'm a noob with Ubuntu, so I don't know what else to do. Will anyone help me?
 
Post the result of your 
```
 
sudo lshw -C network

```
 
and give us a few others
 
```
 
lspci -nn | grep 0280 

```
 
```
 
lsmod

```
 
The result of those will help..

---

### Post by Howlin1 on 2011-09-02
sudo lshw -C network

```

  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:16:00:43:d0
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f6000000-f6000fff memory:f0000000-f001ffff
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 04
       serial: 00:16:44:de:22:1c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fa000000-fa00ffff

```
lspci -nn | grep 0280
lsmod
```

Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  162 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
arc4                   12473  2 
joydev                 17322  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
ath5k                 144412  0 
ath                    19141  1 ath5k
acer_wmi               23123  0 
mac80211              257001  1 ath5k
sparse_keymap          13666  1 acer_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              156212  3 ath5k,ath,mac80211
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
psmouse                73312  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450944  3 
usb_storage            43946  5 
uas                    17676  0 
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
ahci                   21591  0 
libahci                25548  1 ahci
i2c_algo_bit           13184  1 i915
r8169                  42534  0 
video                  18951  1 i915

```

---

### Post by nm_geo on 2011-09-02
Ok do the following too.
 
```
 
rfkill list all

```

---

### Post by Howlin1 on 2011-09-02
```

0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```

---

### Post by nm_geo on 2011-09-02
> **Howlin1 said:**
> ```

0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```
 
Okay lets try to unblock those soft blocks
 
```
 
rfkill unblock all

``` 
 
Then  
 
```
 
rfkill list all 

```
 
you have a module that we might need to blacklist if that command does not give us no everywhere.  This is like the wifi switch but software (Soft Blocked).

---

### Post by Howlin1 on 2011-09-02
```

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

But now when I click the internet tab between the battery and the volume, the Enable Wireless option is blacked out.

---

### Post by nm_geo on 2011-09-02
> **Howlin1 said:**
> ```

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
 
But now when I click the internet tab between the battery and the volume, the Enable Wireless option is blacked out.
 
Okay try this 
 
```
 
sudo rmmod -f acer-wmi

```
 
That may be a temporary fix .. In other words when you reboot it will not stay fixed, but we need to know if it works temporarily.
 
Did you turn your wifi switch **[COLOR=red]OFF[/COLOR]**?

---

### Post by Howlin1 on 2011-09-02
What was meant to happen? I put that command in, it asked for a password and then nothing happened. The enbable wireless option is still blacked out.

EDIT: MY wifi switch is press the  FN and F1 button and then clicking the on option.

---

### Post by nm_geo on 2011-09-02
> **Howlin1 said:**
> What was meant to happen? I put that command in, it asked for a password and then nothing happened. The enbable wireless option is still blacked out.
 
EDIT: MY wifi switch is press the FN and F1 button and then clicking the on option.
 
Okay good .. Let's experiment a little with your wifi switch.. That hard block usually indicates that the switch is not in the correct position. Change it then run 
```
 
rfkill list all

```
Go the other way with the switch and run
```
 
rfkill list all

```
 
OH please show results in thread each time.
 
I hoped the rfkill unblock all would clear the software blocks, and did not expect it to cause a hard wire block.
 
After our experiment reboot and let's look at it again.

---

### Post by Howlin1 on 2011-09-02
> **nm_geo said:**
> Okay good .. Let's experiment a little with your wifi switch.. That hard block usually indicates that the switch is not in the correct position. Change it then run.
I can't change it because when I press FN and F1 nothing happens, but if I press FN and F3 the sound will mute/unmute.

Should I reboot?

---

### Post by nm_geo on 2011-09-02
> **Howlin1 said:**
> I can't change it because when I press FN and F1 nothing happens, but if I press FN and F3 the sound will mute/unmute.
 
Should I reboot?
 
Okay reboot we have to get rid of the hard block yes statement..
Again the yes statement indicates that the wifi switch is turned **off**
 
That is why I wanted to see the rfkill list all results when you toggled the wifi switch.

---

### Post by Howlin1 on 2011-09-02
> **nm_geo said:**
> Okay reboot we have to get rid of the hard block yes statement..
Again the yes statement indicates that the wifi switch is turned **off**
 
That is why I wanted to see the rfkill list all results when you toggled the wifi switch.
```

0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```

```

joe@joe-AMILO-Li-2727:~$ sudo rmmod -f acer-wmi
[sudo] password for joe: 
joe@joe-AMILO-Li-2727:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```

That what you wanted?

---

### Post by nm_geo on 2011-09-02
> **Howlin1 said:**
> ```

0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```
 
```

joe@joe-AMILO-Li-2727:~$ sudo rmmod -f acer-wmi
[sudo] password for joe: 
joe@joe-AMILO-Li-2727:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```
 
That what you wanted?
 
Yes it is ...
let's try these three commands one at a time. ..Then reboot..
```
 
sudo su
echo "acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit

```
 
Ok here is the explanation the acer_wmi module does not always work well in Linux and can cause confusion with the wifi switch. We have had good results with blacklisting that module and then getting wireless cards working. If it does not make a change we can remove the blacklist.. I had hoped when you did the temporary rmmod -f acer-wmi the wireless would have sprung to life. Be sure to reboot without ethernet cable installed.. The network manager typically will not allow a wireless connection if the ethernet cable is in.

---

### Post by Howlin1 on 2011-09-02
I did what you said and then did a rfkill list all I get
```

0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```

---

### Post by nm_geo on 2011-09-02
okay do the 

```
rfkill unblock all
```

Then post results of 

```
rfkill list all
```

---

### Post by praseodym on 2011-09-02
Hi,

there was a typo/syntax error here:
> ```
sudo su
echo "acer[COLOR="Red"]-[/COLOR]wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
Change via

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
the entry
```
acer[COLOR="Red"]-[/COLOR]wmi
```
to
```
[COLOR="Red"]blacklist[/COLOR] acer[COLOR="Red"]_[/COLOR]wmi
```
save and reboot. After that try
```
sudo rfkill unblock all
```

---

### Post by Howlin1 on 2011-09-02
```

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

I just looked and I can see the wireless connections now. Thanks :) 
Will I need to do this every time I turn off/on the laptop?

---

### Post by nm_geo on 2011-09-02
Also please copy and paste this one in terminal and then results. It best to just copy and paste as the l is a small L .. The 0 are zeros not cap O.. easier to copy and paste. The symbol | is called a pipe same key as the shift \ key right near top of keyboard.

```
lspci -nn | grep 0280
```I need to make sure the driver matches the card. 

then do 

```
modinfo ath5k
```results we will make sure your driver and chip match.

---

### Post by nm_geo on 2011-09-02
Excellent ..
I don't think you will have to do it but maybe...
If so we can add a permanent command somewhere..
Please mark Thread Solved at the top.

Let's test reboot and see if you need to rfkill unblock all.

---

### Post by praseodym on 2011-09-02
As you can see

```
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```
the module [COLOR="Red"]acer_wmi[/COLOR] is still loaded (check "lsmod"). But, if it works

---

### Post by Howlin1 on 2011-09-02
> **nm_geo said:**
> Also please copy and paste this one in terminal and then results. It best to just copy and paste as the l is a small L .. The 0 are zeros not cap O.. easier to copy and paste. The symbol | is called a pipe same key as the shift \ key right near top of keyboard.

```
lspci -nn | grep 0280
```I need to make sure the driver matches the card. 

then do 

```
modinfo ath5k
```results we will make sure your driver and chip match.

Pipe? I thought it was known as a pip. MEh
```

filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     F4251C9C364128E69095BD1
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           all_channels:Expose all channels the device can use. (bool)

```


Thanks a lot :)  
Will do.

---

### Post by nm_geo on 2011-09-02
Try 

```
lspci -nn
```

I am not seeing the wireless card yet..

and

```
nm-tool
```

go ahead and install nm-tool if you don't already have it. then run.. nm-tool

---

### Post by Howlin1 on 2011-09-02
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
08:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 04)

```
and 
```

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1F:16:00:43:D0

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         ....
    Prefix:          ....
    Gateway:         ....

    DNS:             ....
    DNS:             ....


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:16:44:DE:22:1C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Belkin_G_Wireless_061601: ....
    ASUS:            ....

```

I'll try a reboot now and see what happens.

---

### Post by nm_geo on 2011-09-02
Yes correct driver and chipset

alias:          pci:v0000**168C**d0000**001C**sv*sd*bc*sc*i*

08:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [**168c:001c**] (rev 04)

 we are getting there..

---

### Post by nm_geo on 2011-09-02
> **praseodym said:**
> Hi,

there was a typo/syntax error here:

Change via

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```the entry
```
acer[COLOR=Red]-[/COLOR]wmi
```to
```
[COLOR=Red]blacklist[/COLOR] acer[COLOR=Red]_[/COLOR]wmi
```save and reboot. After that try
```
sudo rfkill unblock all
```

Yes thanks praseodym.. i was in transit and missed your message..

I did make a typo

should have been 

```
sudo su 
echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf 
exit 

```

---

### Post by Howlin1 on 2011-09-02
When I reset the laptop the wireless wasn't turn on.
Doing a 
```

rfkill unblock all

```
will give me 
```

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by nm_geo on 2011-09-02
> **Howlin1 said:**
> When I reset the laptop the wireless wasn't turn on.
Doing a 
```

rfkill unblock all

```will give me 
```

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

See the discussion right above I made a typo in the command to blacklist the acer_wmi... If you follow praseodym instructions it will be more fun for you.. You get to see root operate in gedit.. or you could do my corrected echo. We need to get that module blacklisted.

---

### Post by Howlin1 on 2011-09-02
I did what was on that post and reset the laptop and then did sudo rfkill unblock all and now the "enable wireless" option is blacked out.

---

### Post by nm_geo on 2011-09-02
hmmm...

```
lsmod
```

please..

So you did the 

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Method and added or corrected the line

```
blacklist acer_wmi
```

Correct?

---

### Post by Howlin1 on 2011-09-02
> **nm_geo said:**
> hmmm...

```
lsmod
```please..



```

Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  332 
aes_generic            38023  1 aes_i586
dm_crypt               22463  1 
arc4                   12473  2 
joydev                 17322  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
ath5k                 144412  0 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              156212  3 ath5k,ath,mac80211
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450944  3 
usb_storage            43946  5 
uas                    17676  0 
drm_kms_helper         40745  1 i915
ahci                   21591  0 
drm                   180037  4 i915,drm_kms_helper
libahci                25548  1 ahci
r8169                  42534  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

```> 
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Method and added or corrected the line

```
blacklist acer_wmi
```Correct?No I did
```

sudo su 
echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf 
exit

```
But 
"blacklist acer_wmi" is in the blacklist.conf file.

---

### Post by nm_geo on 2011-09-02
Reboot 

```
rfkill list all
```then 
```

rfkill unblock all
```one more time 
```
rfkill list all
```See if your wifi kill switch changes anything at all too..

if we get all no answers let's get wifi running..

---

### Post by Howlin1 on 2011-09-02
```

joe@joe-AMILO-Li-2727:~$ rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

joe@joe-AMILO-Li-2727:~$ rfkill unblock all

joe@joe-AMILO-Li-2727:~$ rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by nm_geo on 2011-09-02
Dang the wifi switch does nothing?

We may need to get that danged acer-wmi out of the blacklist.conf file for a bit. It will be a good thing to show you anyway.

when you do 

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```You can place a # symbol in front of the blacklist acer_wmi line..
That comments it out ..
 Then let's reboot and do 

```
sudo rfkill unblock all

```I have not been adding the sudo before the command and probably should have..sorry

As i remember where we have been at one time you had all no answers after that command even though acer_wmi was not blacklisted.

---

### Post by Howlin1 on 2011-09-02
```

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

There is a little red light indicating the wireless is turned on, but I can't see any wireless networks (I should see 2)

---

### Post by nm_geo on 2011-09-02
did you do?

did you check if the wifi switch does anything? 

```
sudo rfkill unblock all
```

Does that make a change?

---

### Post by Howlin1 on 2011-09-02
It does nothing. On windows when I press it a box comes up that allows me to turn it on or off. I don't get that option on ubuntu.

---

### Post by nm_geo on 2011-09-02
> **Howlin1 said:**
> It does nothing. On windows when I press it a box comes up that allows me to turn it on or off. I don't get that option on ubuntu.

That is why we did the blacklist attempt. I was hoping it did something after we released the blacklist acer-wmi..

Okay let's try another shot at this..

```
sudo rmmod -f acer-wmi
sudo rfkill unblock all 
rfkill list all
```

---

### Post by Howlin1 on 2011-09-02
```

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

I'm sorry, but it's late (for me) and I have to go to bed.

---

### Post by nm_geo on 2011-09-02
> **Howlin1 said:**
> ```

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```I'm sorry, but it's late (for me) and I have to go to bed.

It is okay i think i am on to something.. I will leave you a message .. on what we might try..Get some rest.

---

### Post by nm_geo on 2011-09-02
This link 

[http://ubuntuforums.org/showthread.php?t=1745317#10](http://ubuntuforums.org/showthread.php?t=1745317#10)

and the tenth message begin the information that might help us.

We will need to test it.. after blacklisting the acer-wmi again.

Then we will do what chili555 wrote in 

[http://ubuntuforums.org/showthread.php?t=1745317&page=2#12](http://ubuntuforums.org/showthread.php?t=1745317&page=2#12)

It had happy endings for some.. Try to follow it when you get a chance..
Be sure you add those lines above the exit 0

---

### Post by Howlin1 on 2011-09-03
It works perfectly now! I can see and connect to the internet now. I rebooted the laptop and it's working. :)
Thanks so much for your help :)

---

