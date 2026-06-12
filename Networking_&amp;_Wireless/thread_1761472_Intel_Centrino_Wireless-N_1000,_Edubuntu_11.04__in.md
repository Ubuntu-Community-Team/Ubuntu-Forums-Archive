---
title: "Intel Centrino Wireless-N 1000, Edubuntu 11.04  in Lenovo Thinkpad Edge 420"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by madik on 2011-05-18
Hi i am requesting help for my problem with Wifi on my notebook Lenovo E420. I just cant get it working :(

Here are some terminal outputs:

lspci
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.7 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Whistler [AMD Radeon HD 6600M Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 04)
09:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
madik@madik-ThinkPad-E420:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.7 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Whistler [AMD Radeon HD 6600M Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 04)
09:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

```lsusb

```
Bus 002 Device 006: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 002 Device 003: ID 147e:1002 Upek 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b257 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```lsmod

```

Module                  Size  Used by
hidp                   22572  1 
hid                    91020  1 hidp
iptable_filter         12810  1 
ip_tables              27456  1 iptable_filter
x_tables               29581  2 iptable_filter,ip_tables
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
joydev                 17606  0 
binfmt_misc            17565  1 
rfcomm                 47694  8 
sco                    18131  2 
bnep                   18308  2 
l2cap                  53570  21 hidp,rfcomm,bnep
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
thinkpad_acpi          81587  0 
iwlagn                333500  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
btusb                  18600  4 
acer_wmi               23771  0 
iwlcore               167503  1 iwlagn
mac80211              294370  2 iwlagn,iwlcore
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13898  1 acer_wmi
bluetooth              72448  10 hidp,rfcomm,sco,bnep,l2cap,btusb
i915                  514985  2 
uvcvideo               72195  0 
psmouse                73535  0 
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2739144  0 
cfg80211              178528  3 iwlagn,iwlcore,mac80211
videodev               82052  1 uvcvideo
serio_raw              13166  0 
v4l2_compat_ioctl32    17078  1 videodev
drm_kms_helper         42136  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   227495  3 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
soundcore              12680  1 snd
nvram                  14419  1 thinkpad_acpi
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
r8169                  48022  0 
libahci                26642  1 ahci
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci

```sudo lshw -C network
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:54:a1:6e
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.148 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:41 ioport:4000(size=256) memory:e0404000-e0404fff memory:e0400000-e0403fff
  *-network DISABLED
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:6d:39:f0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:44 memory:e1d00000-e1d01fff

```

rfkill list
```
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

I would appreciate any help with my Wifi issue. thanks

---

### Post by chili555 on 2011-05-18
> 1: phy0: Wireless LAN
    [COLOR="Red"]Soft blocked: yes[/COLOR]
    Hard blocked: noThe laptop thinks the wireless is turned off in software. Be sure the ethernet cable is detached so that Network Manager doesn't interfere and do:```
sudo rfkill unblock all
rfkill list all
```Is soft block now changed to no? If not, try:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all
```We can modify a couple of files to make which ever combination works permanent.

I am a bit surprised that a Thinkpad thinks it's an Acer and that both thinkpad-acpi and acer-wmi are loaded. I still learn something new every day.

---

### Post by madik on 2011-05-18
Awesome chill555 this worked like a charm.
```

sudo rmmod -f acer-wmi
sudo rfkill unblock all 
rfkill list all

```

Wifi is now working nicely

Thanks a lot

---

### Post by chili555 on 2011-05-18
Would you care to make it permanent?```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Upon your next boot, you should be all set.

---

### Post by madik on 2011-05-18
Hehe i love this support. i was just coming back after restart to ask how to make it permanent. thanks a lot

---

### Post by rjantz on 2011-07-04
I am thinking seriously about getting an Edge 420 and running Ubuntu on it.  Are you happy with yours?

---

### Post by MorrisseyJ on 2011-08-26
Hi, 

Thanks for this, the advice worked for me as well - also using a Centrino Wireless-N 1000, on a Lenovo Thinkpad x121e.

One difference though, my thinkpad doesn't seem to think its an acer as 'sudo rfkill list', gives:
> 0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: noGiven this i was wondering if you could tell me how to make these changes permanent.

Thanks.

---

### Post by chili555 on 2011-08-26
> **MorrisseyJ said:**
> Hi, 

Thanks for this, the advice worked for me as well - also using a Centrino Wireless-N 1000, on a Lenovo Thinkpad x121e.

One difference though, my thinkpad doesn't seem to think its an acer as 'sudo rfkill list', gives:
Given this i was wondering if you could tell me how to make these changes permanent.

Thanks.I am assuming all you need to get the wireless going is:```
sudo rfkill unblock all
```If that's the case, please do:```
sudo gedit /etc/rc.local
```Add a line above exit 0:```
rfkill unblock all
```Proofread carefully, save and close gedit. You should be all set, but feel free to post back if you need more help.

---

### Post by MorrisseyJ on 2011-08-26
Yes, you assumed correctly (sorry for not being clear).

All works perfectly now. Thanks very much. 

One thing i could add in case anyone stumbles across this thread. The wireless on my ubuntu install would only disappear if i restarted without the battery plugged in. Then i could get it back by booting to windows, using the wireless, and restarting (with the battery in).

This is a much better solution.

Thanks again.

---

### Post by MorrisseyJ on 2011-08-27
Hi,

While this solution works at getting my wireless working, it appears to have left me unable to turn off my bluetooth. When i click on the bluetooth icon from the top panel, there is no longer any option to turn it off. I am guessing that i have somehow turned it on all the time.

This isn't too bad, but since mine is a portable laptop, switching off the bluetooth is nice for being able to extend battery life. 

Any ideas how i might set this up so that wireless is enabled and bluetooth can be turned off?

thanks again,

---

### Post by chili555 on 2011-08-27
> 0: tpacpi_bluetooth_sw: Bluetooth
Soft blocked: no
Hard blocked: yes
[COLOR="Red"]1: phy0: Wireless[/COLOR] LAN
Soft blocked: no
Hard blocked: no
5: hci0: Bluetooth
Soft blocked: no
Hard blocked: no You might try changing your rc.local line to:```
rfkill unblock wifi
```Or else:```
rfkill unblock 1
```Post back, please, so the searchers will learn.

---

### Post by MorrisseyJ on 2011-08-27
Yeah, > rfkill unblock wireless works. 

The problem appears to be that my bluetooth is doing the same thing as my wireless. When i uplug the battery i lose them both  - without the ability to turn them back on from the top panel.

> rfkill unblock wifi unblocks the wifi, leaving the bluetooth blocked. If i want to unblock the bluetooth i have to > rfkill unblock bluetooth

The problem then is that i lose the ability to turn the bluetooth off via the top panel. Notably, once i > rfkill unblock wifi i can still turn off the wifi from the top panel. 

Toggling bluetooth (which i rarely use) with > rfkill unblock bluetooth is an ok solution, but it would be nice to know exactly what is going on here.

As always, your help on these things is very much appreciated.

---

### Post by chili555 on 2011-08-27
> but it would be nice to know exactly what is going on here.I rather imagine what is going on is that the module that is supposed to translate key presses into commands the kernel understands is not working correctly. It may be, in your system, ideapad-laptop or some other. Can you please check?```
lsmod
```Perhaps you, me and Google, can find a solution.

These modules are notoriously imperfect on newer laptops. On my ancient Thinkpad T40, everything works perfectly, as far as I can tell!

---

### Post by MorrisseyJ on 2011-08-27
Cool, 

There doesn't appear to be a button for the wirless, but there is one for the bluetooth (Fn + F5). As you say however, pressing it doesn't register any effect.

Here is the output of lsmod:

```
Module                  Size  Used by
rfcomm                 47694  0 
sco                    18187  0 
bnep                   18308  0 
l2cap                  53570  4 rfcomm,bnep
btusb                  18600  0 
bluetooth              72320  5 rfcomm,sco,bnep,l2cap,btusb
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_conexant    57511  1 
joydev                 17606  0 
binfmt_misc            17565  1 
arc4                   12529  2 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlagn                333716  0 
i915                  515121  4 
iwlcore               167502  1 iwlagn
thinkpad_acpi          81587  0 
mac80211              294370  2 iwlagn,iwlcore
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
drm_kms_helper         42136  1 i915
uvcvideo               72195  0 
cfg80211              178528  3 iwlagn,iwlcore,mac80211
snd_seq_midi_event     14899  1 snd_seq_midi
drm                   227534  5 i915,drm_kms_helper
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
tpm_tis                18537  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
rts_pstor             440614  0 
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 i915
tpm                    22267  1 tpm_tis
tpm_bios               13684  1 tpm
soundcore              12680  1 snd
nvram                  14419  1 thinkpad_acpi
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  2 
libahci                26642  1 ahci
atl1c                  41171  0 
```

---

### Post by chili555 on 2011-08-27
You have the usually reliable thinkpad_acpi. Let's get back to basics. Please run:```
sudo gedit /etc/rc.local
```Comment out your rfkill line so it's temporarily ineffective. Reboot. Now run and post:```
rfkill list all
```Next, manipulate the Fn+Fxx button that is supposed to control wireless and bluetooth. Again, run:```
rfkill list all
```On my Lenovo T60, one key combination, Fn+F5 controls both by successive presses.

Please run (but don't post):```
modinfo thinkpad-acpi
```You will see that there are many parameters to manipulate. Some interesting parameters are:> parm:           bluetooth:Simulates thinkpad-acpi procfs command at module load, see documentation
parm:           dbg_bluetoothemul:Enables bluetooth switch emulation (uint)
parm:           bluetooth_state:Initial state of the emulated bluetooth switch (bool)
Perhaps we just need to load thinkpad_acpi with an extra parameter.

---

### Post by MorrisseyJ on 2011-08-27
Commented "rfkill unblock wifi" in my /etc/rc/.local file.

Turned off and removed the battery - i have to do this to get these settings to switch off.

> rfkill list all gives: ```
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```Then i manipulate Fn + F5 and > rfkill list all gives: ```
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```- So one more option has been added to the list, but nothing has happened in the top menu bar. I still can't turn off the bluetooth without > rfkill block bluetooth> modinfo thinkpad-acpi brings up a lot of options. Do i edit these by: > sudo gedit /lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko?

---

### Post by chili555 on 2011-08-27
> Do i edit these by:
Quote:
sudo gedit /lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko
?A good guess, but no. You create a .conf file so that when thinkpad_acpi loads, it is loaded with a parameter. I suggest your first trial be:```
sudo gedit /etc/modprobe.d/thinkpad_acpi.conf
```Add a single line:```
options thinkpad_acpi bluetooth_state=on
```Proofread, save and close gedit. Reboot and try the tests again.

[http://www.mjmwired.net/kernel/Documentation/laptops/thinkpad-acpi.txt](http://www.mjmwired.net/kernel/Documentation/laptops/thinkpad-acpi.txt)

[http://www.thinkwiki.org/wiki/How_to_setup_Bluetooth](http://www.thinkwiki.org/wiki/How_to_setup_Bluetooth)  <---Don't go too crazy here; let's try the easy stuff first.

---

### Post by phaedrus54 on 2011-08-29
You're a life-saver chili555!

Many thanks, the rfkill unblock all works like a charm to make my 1000 N based Tm2t work =D.

Strangely enough this wifi card works fine with Ubuntu based distros but not pure Debian ones /shrug.

---

### Post by chili555 on 2011-08-29
> **phaedrus54 said:**
> 
Strangely enough this wifi card works fine with Ubuntu based distros but not pure Debian ones /shrug.I'm not sure the required firmware is provided by default in Debian.

---

### Post by LinuxTheDragon on 2011-09-14
> **chili555 said:**
> The laptop thinks the wireless is turned off in software. Be sure the ethernet cable is detached so that Network Manager doesn't interfere and do:```
sudo rfkill unblock all
rfkill list all
```Is soft block now changed to no? If not, try:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all
```We can modify a couple of files to make which ever combination works permanent.

I am a bit surprised that a Thinkpad thinks it's an Acer and that both thinkpad-acpi and acer-wmi are loaded. I still learn something new every day.

Hey just wanted to say thanks to chili555 as well - I had the same issues and this fixed the problem right quick. Kudos! These forums and people taking the time to post has helped me on numerous occasions.:)

---

### Post by martinyt on 2011-10-01
> **chili555 said:**
> I am assuming all you need to get the wireless going is:```
sudo rfkill unblock all
```If that's the case, please do:```
sudo gedit /etc/rc.local
```Add a line above exit 0:```
rfkill unblock all
```Proofread carefully, save and close gedit. You should be all set, but feel free to post back if you need more help.

Thanks. This also worked for me. However, sometimes when I boot I can't connect to my network..... it tries but fails - it is a wpa network. I have a lenovo x121e by the way and I have updated the bios. Anyone who knows what might fix this?

---

