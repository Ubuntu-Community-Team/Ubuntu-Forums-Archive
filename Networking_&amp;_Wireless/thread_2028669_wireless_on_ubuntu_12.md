---
title: "wireless on ubuntu 12"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by antobbo on 2012-07-18
Hi quick question about the wireless. I have a dell xps 17 dual booting and the wireless is currently turned off. Usually, well in windows, I can turn it on using the fn key + f2 but that trick doesn't work in ubunto. How do I switch the wireless on please?

---

### Post by Finnicella on 2012-07-18
Have you tried to leave your wifi up from windows and check if in Ubunto work?
Otherwise write these commands in the terminal:
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

---

### Post by rukiaEnix on 2012-07-18
Didn't you check at the time you were installing Ubuntu if you could connect using wireless?

At installation time you used the wireless? Please answer

---

### Post by antobbo on 2012-07-19
Hi thanks for that.
@rukiaEnix I used the wired connection during the installation because the wireless is switched off
@Finnicella if I switch it on in Windows it works in ubuntu too, but I feel it is a bit odd that if I want to use the wireless I need to go back to windows. 
I tried your command: the first one returns
SIOCSIFFLAGS: Operation not possible due to RF-kill

the second one
 command not found

Any idea? thanks

---

### Post by rukiaEnix on 2012-07-19
I think drivers for your wireless weren't installed as you had it turned off...

Have you check in the menu System>Administration for the option Hardware drivers and see if it's there?

---

### Post by antobbo on 2012-07-19
hi there, thanks do you mean "system settings"? there is only additional drivers option there, any other way to find it? Can I not install it from the terminal somehow?
thanks

---

### Post by rukiaEnix on 2012-07-19
Please post the result of this:

```

lspci

```

---

### Post by Finnicella on 2012-07-20
> **antobbo said:**
> Hi thanks for that.
@rukiaEnix I used the wired connection during the installation because the wireless is switched off
@Finnicella if I switch it on in Windows it works in ubuntu too, but I feel it is a bit odd that if I want to use the wireless I need to go back to windows. 
I tried your command: the first one returns
SIOCSIFFLAGS: Operation not possible due to RF-kill

the second one
 command not found

Any idea? thanks

Ok try:
```
sudo rfkill unblock all
```
if with this command your wireless doesn't work yet, write to me the output of:
```
sudo lshw -C network
```
Bye

---

### Post by antobbo on 2012-07-20
ho thanks unfortunately none of the commands work.
The output of your command gives this:
 *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: bc:77:37:67:39:32
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-26-generic firmware=18.168.6.1 ip=81.200.64.50 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:55 memory:f3b00000-f3b01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 06
       serial: 14:fe:b5:ac:ce:96
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.0.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:52 ioport:2000(size=256) memory:f3004000-f3004fff memory:f3000000-f3003fff

thanks

---

### Post by NikTh on 2012-07-21
Hi , 
please run this command again 
```
sudo rfkill unblock all
```then give this command ```
sudo ifconfig wlan0 up
```and give the output of this command ```
rfkill list all
```Regards

---

### Post by antobbo on 2012-07-22
Hi NikTh, thanks for that, here's the output. SOmething I need to mention is that, contrary to what I said in the post before, I have notice that now even if I enable the wireless in windows, it is still disabled in ubuntu

antobbo@antobbo-xps17-ubuntu:~$ sudo rfkill unblock all
[sudo] password for antobbo: 
antobbo@antobbo-xps17-ubuntu:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
antobbo@antobbo-xps17-ubuntu:~$ rfkill list all
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Thanks

---

### Post by NikTh on 2012-07-22
Hi , 
we can try something else and see if works . 

Open a terminal and copy-paste (carefully) . 

```
echo 'blacklist dell-wifi' | sudo tee -a /etc/modprobe.d/blacklist.conf 
```reboot your system (without ethernet cable plugged) and give the results of these commands 
```
sudo rfkill unblock all
iwconfig 
lsmod 
lspci -nnk | grep -iA2 net
rfkill list all
```**Please put the results inside [CODE] tags , by highlighting the text and click [SIZE=3]#[/SIZE] symbol on top of message pane . **
Thanks

---

### Post by antobbo on 2012-07-22
hi thanks, here's the output sorry it is extremely long:

antobbo@antobbo-xps17-ubuntu:~$ iwconfig 
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.



antobbo@antobbo-xps17-ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
binfmt_misc            17540  1 
arc4                   12529  2 
snd_hda_intel          33773  3 
joydev                 17693  0 
iwlwifi               332672  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
nvidia              12319264  0 
mac80211              506816  1 iwlwifi
i915                  468737  2 
drm_kms_helper         46978  1 i915
drm                   242038  3 i915,drm_kms_helper
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87692  0 
cfg80211              205544  2 iwlwifi,mac80211
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
serio_raw              13211  0 
dell_wmi               12681  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32    17128  1 videodev
i2c_algo_bit           13423  1 i915
mei                    41616  0 
sparse_keymap          13890  1 dell_wmi
wmi                    19256  1 dell_wmi
mac_hid                13253  0 
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ lsmod
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ Module                  Size  Used by
Module: command not found
antobbo@antobbo-xps17-ubuntu:~$ bnep                   18281  2 
No command 'bnep' found, did you mean:
 Command 'beep' from package 'beep' (universe)
bnep: command not found
antobbo@antobbo-xps17-ubuntu:~$ rfcomm                 47604  0 
RFCOMM configuration utility ver 4.98
Usage:
    rfcomm [options] <command> <dev>

Options:
    -i [hciX|bdaddr]      Local HCI device or BD Address
    -h, --help            Display help
    -r, --raw             Switch TTY into raw mode
    -A, --auth            Enable authentication
    -E, --encrypt         Enable encryption
    -S, --secure          Secure connection
    -M, --master          Become the master of a piconet
    -f, --config [file]   Specify alternate config file
    -a                    Show all devices (default)

Commands:
    bind     <dev> <bdaddr> [channel]    Bind device
    release  <dev>                       Release device
    show     <dev>                       Show device
    connect  <dev> <bdaddr> [channel]    Connect device
    listen   <dev> [channel [cmd]]       Listen
    watch    <dev> [channel [cmd]]       Watch

antobbo@antobbo-xps17-ubuntu:~$ bluetooth             180104  10 bnep,rfcomm
No command 'bluetooth' found, did you mean:
 Command 'bluetoothd' from package 'bluez' (main)
bluetooth: command not found
antobbo@antobbo-xps17-ubuntu:~$ parport_pc             32866  0 
parport_pc: command not found
antobbo@antobbo-xps17-ubuntu:~$ ppdev                  17113  0 
No command 'ppdev' found, did you mean:
 Command 'ppdep' from package 'fp-utils-2.4.4' (universe)
ppdev: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hda_codec_hdmi     32474  1 
snd_hda_codec_hdmi: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hda_codec_realtek   223867  1 
snd_hda_codec_realtek: command not found
antobbo@antobbo-xps17-ubuntu:~$ binfmt_misc            17540  1 
binfmt_misc: command not found
antobbo@antobbo-xps17-ubuntu:~$ arc4                   12529  2 
No command 'arc4' found, did you mean:
 Command 'arch' from package 'coreutils' (main)
 Command 'arc' from package 'arc' (universe)
arc4: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hda_intel          33773  3 
snd_hda_intel: command not found
antobbo@antobbo-xps17-ubuntu:~$ joydev                 17693  0 
joydev: command not found
antobbo@antobbo-xps17-ubuntu:~$ iwlwifi               332672  0 
iwlwifi: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hda_codec: command not found
antobbo@antobbo-xps17-ubuntu:~$ nvidia              12319264  0 
nvidia: command not found
antobbo@antobbo-xps17-ubuntu:~$ mac80211              506816  1 iwlwifi
mac80211: command not found
antobbo@antobbo-xps17-ubuntu:~$ i915                  468737  2 
i915: command not found
antobbo@antobbo-xps17-ubuntu:~$ drm_kms_helper         46978  1 i915
drm_kms_helper: command not found
antobbo@antobbo-xps17-ubuntu:~$ drm                   242038  3 i915,drm_kms_helper
No command 'drm' found, did you mean:
 Command 'dpm' from package 'dpm-server-postgres' (universe)
 Command 'dpm' from package 'dpm-server-mysql' (universe)
 Command 'crm' from package 'pacemaker' (main)
 Command 'crm' from package 'crm114' (universe)
 Command 'arm' from package 'tor-arm' (universe)
 Command 'rm' from package 'coreutils' (main)
 Command 'rm' from package 'safe-rm' (universe)
 Command 'vrm' from package 'atfs' (universe)
 Command 'srm' from package 'secure-delete' (universe)
 Command 'drc' from package 'drc' (universe)
 Command 'frm' from package 'mailutils' (universe)
 Command 'drr' from package 'plastimatch' (universe)
 Command 'dwm' from package 'dwm' (universe)
drm: command not found
antobbo@antobbo-xps17-ubuntu:~$ dell_laptop            18119  0 
dell_laptop: command not found
antobbo@antobbo-xps17-ubuntu:~$ dcdbas                 14490  1 dell_laptop
dcdbas: command not found
antobbo@antobbo-xps17-ubuntu:~$ uvcvideo               72627  0 
uvcvideo: command not found
antobbo@antobbo-xps17-ubuntu:~$ videodev               98259  1 uvcvideo
videodev: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hwdep              13668  1 snd_hda_codec
snd_hwdep: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_pcm: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_seq_midi           13324  0 
snd_seq_midi: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_rawmidi            30748  1 snd_seq_midi
snd_rawmidi: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq_midi_event: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_seq: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_timer              29990  2 snd_pcm,snd_seq
snd_timer: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_device: command not found
antobbo@antobbo-xps17-ubuntu:~$ psmouse                87692  0 
psmouse: command not found
antobbo@antobbo-xps17-ubuntu:~$ cfg80211              205544  2 iwlwifi,mac80211
cfg80211: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
The program 'snd' can be found in the following packages:
 * snd-gtk-jack
 * snd-gtk-pulse
 * snd-nox
Try: sudo apt-get install <selected package>
antobbo@antobbo-xps17-ubuntu:~$ soundcore              15091  1 snd
soundcore: command not found
antobbo@antobbo-xps17-ubuntu:~$ serio_raw              13211  0 
serio_raw: command not found
antobbo@antobbo-xps17-ubuntu:~$ dell_wmi               12681  0 
dell_wmi: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd_page_alloc: command not found
antobbo@antobbo-xps17-ubuntu:~$ v4l2_compat_ioctl32    17128  1 videodev
v4l2_compat_ioctl32: command not found
antobbo@antobbo-xps17-ubuntu:~$ i2c_algo_bit           13423  1 i915
i2c_algo_bit: command not found
antobbo@antobbo-xps17-ubuntu:~$ mei                    41616  0 
No command 'mei' found, did you mean:
 Command 'mev' from package 'gpm' (universe)
 Command 'mex' from package 'texlive-lang-polish' (main)
 Command 'mi' from package 'libxgks-dev' (universe)
mei: command not found
antobbo@antobbo-xps17-ubuntu:~$ sparse_keymap          13890  1 dell_wmi
sparse_keymap: command not found
antobbo@antobbo-xps17-ubuntu:~$ wmi                    19256  1 dell_wmi
No command 'wmi' found, did you mean:
 Command 'wmu' from package 'wml' (universe)
 Command 'wmk' from package 'wml' (universe)
 Command 'wmb' from package 'wml' (universe)
 Command 'wmf' from package 'wmf' (universe)
 Command 'wmd' from package 'wml' (universe)
 Command 'wm2' from package 'wm2' (universe)
 Command 'wmii' from package 'wmii' (universe)
 Command 'pmi' from package 'powermanagement-interface' (universe)
 Command 'wmix' from package 'wmix' (universe)
 Command 'smi' from package 'scmxx' (universe)
 Command 'fmi' from package 'alliance' (universe)
 Command 'wmc' from package 'wine1.4' (universe)
 Command 'mi' from package 'libxgks-dev' (universe)
 Command 'wml' from package 'wml' (universe)
wmi: command not found
antobbo@antobbo-xps17-ubuntu:~$ mac_hid                13253  0 
mac_hid: command not found
antobbo@antobbo-xps17-ubuntu:~$ video                  19596  1 i915
video: command not found
antobbo@antobbo-xps17-ubuntu:~$ lp                     17799  0 
lp: Error - unable to access "17799" - No such file or directory
antobbo@antobbo-xps17-ubuntu:~$ parport                46562  3 parport_pc,ppdev,lp
parport: command not found
antobbo@antobbo-xps17-ubuntu:~$ r8169                  62099  0 
r8169: command not found
antobbo@antobbo-xps17-ubuntu:~$ 


    -S, --secure          Secure connection
    -M, --master          Become the master of a piconet
    -f, --config [file]   Specify alternate config file
    -a                    Show all devices (default)

Commands:
    bind     <dev> <bdaddr> [channel]    Bind device
    release  <dev>                       Release device
    show     <dev>                       Show device
    connect  <dev> <bdaddr> [channel]    Connect device
    listen   <dev> [channel [cmd]]       Listen
    watch    <dev> [channel [cmd]]       Watch

antobbo@antobbo-xps17-ubuntu:~$ bluetooth             180104  10 bnep,rfcomm

No command 'bluetooth' found, did you mean:
 Command 'bluetoothd' from package 'bluez' (main)
bluetooth: command not found
antobbo@antobbo-xps17-ubuntu:~$ parport_pc             32866  0 

parport_pc: command not found
antobbo@antobbo-xps17-ubuntu:~$ ppdev                  17113  0 

No command 'ppdev' found, did you mean:
 Command 'ppdep' from package 'fp-utils-2.4.4' (universe)
ppdev: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hda_codec_hdmi     32474  1 

snd_hda_codec_hdmi: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hda_codec_realtek   223867  1 

snd_hda_codec_realtek: command not found
antobbo@antobbo-xps17-ubuntu:~$ binfmt_misc            17540  1 

binfmt_misc: command not found
antobbo@antobbo-xps17-ubuntu:~$ arc4                   12529  2 

No command 'arc4' found, did you mean:
 Command 'arch' from package 'coreutils' (main)
 Command 'arc' from package 'arc' (universe)
arc4: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hda_intel          33773  3 

snd_hda_intel: command not found
antobbo@antobbo-xps17-ubuntu:~$ joydev                 17693  0 

joydev: command not found
antobbo@antobbo-xps17-ubuntu:~$ iwlwifi               332672  0 

iwlwifi: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel

snd_hda_codec: command not found
antobbo@antobbo-xps17-ubuntu:~$ nvidia              12319264  0 

nvidia: command not found
antobbo@antobbo-xps17-ubuntu:~$ mac80211              506816  1 iwlwifi

mac80211: command not found
antobbo@antobbo-xps17-ubuntu:~$ i915                  468737  2 

i915: command not found
antobbo@antobbo-xps17-ubuntu:~$ drm_kms_helper         46978  1 i915

drm_kms_helper: command not found
antobbo@antobbo-xps17-ubuntu:~$ drm                   242038  3 i915,drm_kms_helper

No command 'drm' found, did you mean:
 Command 'dpm' from package 'dpm-server-postgres' (universe)
 Command 'dpm' from package 'dpm-server-mysql' (universe)
 Command 'crm' from package 'pacemaker' (main)
 Command 'crm' from package 'crm114' (universe)
 Command 'arm' from package 'tor-arm' (universe)
 Command 'rm' from package 'coreutils' (main)
 Command 'rm' from package 'safe-rm' (universe)
 Command 'vrm' from package 'atfs' (universe)
 Command 'srm' from package 'secure-delete' (universe)
 Command 'drc' from package 'drc' (universe)
 Command 'frm' from package 'mailutils' (universe)
 Command 'drr' from package 'plastimatch' (universe)
 Command 'dwm' from package 'dwm' (universe)
drm: command not found
antobbo@antobbo-xps17-ubuntu:~$ dell_laptop            18119  0 

dell_laptop: command not found
antobbo@antobbo-xps17-ubuntu:~$ dcdbas                 14490  1 dell_laptop

dcdbas: command not found
antobbo@antobbo-xps17-ubuntu:~$ uvcvideo               72627  0 

uvcvideo: command not found
antobbo@antobbo-xps17-ubuntu:~$ videodev               98259  1 uvcvideo

videodev: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hwdep              13668  1 snd_hda_codec

snd_hwdep: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec

snd_pcm: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_seq_midi           13324  0 

snd_seq_midi: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_rawmidi            30748  1 snd_seq_midi

snd_rawmidi: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_seq_midi_event     14899  1 snd_seq_midi

snd_seq_midi_event: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event

snd_seq: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_timer              29990  2 snd_pcm,snd_seq

snd_timer: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq

snd_seq_device: command not found
antobbo@antobbo-xps17-ubuntu:~$ psmouse                87692  0 

psmouse: command not found
antobbo@antobbo-xps17-ubuntu:~$ cfg80211              205544  2 iwlwifi,mac80211

cfg80211: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

The program 'snd' can be found in the following packages:
 * snd-gtk-jack
 * snd-gtk-pulse
 * snd-nox
Try: sudo apt-get install <selected package>
antobbo@antobbo-xps17-ubuntu:~$ soundcore              15091  1 snd

soundcore: command not found
antobbo@antobbo-xps17-ubuntu:~$ serio_raw              13211  0 

serio_raw: command not found
antobbo@antobbo-xps17-ubuntu:~$ dell_wmi               12681  0 

dell_wmi: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_page_alloc         18529  2 snd_hda_intel,snd_pcm

snd_page_alloc: command not found
antobbo@antobbo-xps17-ubuntu:~$ v4l2_compat_ioctl32    17128  1 videodev

v4l2_compat_ioctl32: command not found
antobbo@antobbo-xps17-ubuntu:~$ i2c_algo_bit           13423  1 i915

i2c_algo_bit: command not found
antobbo@antobbo-xps17-ubuntu:~$ mei                    41616  0 

No command 'mei' found, did you mean:
 Command 'mev' from package 'gpm' (universe)
 Command 'mex' from package 'texlive-lang-polish' (main)
 Command 'mi' from package 'libxgks-dev' (universe)
mei: command not found
antobbo@antobbo-xps17-ubuntu:~$ sparse_keymap          13890  1 dell_wmi

sparse_keymap: command not found
antobbo@antobbo-xps17-ubuntu:~$ wmi                    19256  1 dell_wmi

No command 'wmi' found, did you mean:
 Command 'wmu' from package 'wml' (universe)
 Command 'wmk' from package 'wml' (universe)
 Command 'wmb' from package 'wml' (universe)
 Command 'wmf' from package 'wmf' (universe)
 Command 'wmd' from package 'wml' (universe)
 Command 'wm2' from package 'wm2' (universe)
 Command 'wmii' from package 'wmii' (universe)
 Command 'pmi' from package 'powermanagement-interface' (universe)
 Command 'wmix' from package 'wmix' (universe)
 Command 'smi' from package 'scmxx' (universe)
 Command 'fmi' from package 'alliance' (universe)
 Command 'wmc' from package 'wine1.4' (universe)
 Command 'mi' from package 'libxgks-dev' (universe)
 Command 'wml' from package 'wml' (universe)
wmi: command not found
antobbo@antobbo-xps17-ubuntu:~$ mac_hid                13253  0 

mac_hid: command not found
antobbo@antobbo-xps17-ubuntu:~$ video                  19596  1 i915

video: command not found
antobbo@antobbo-xps17-ubuntu:~$ lp                     17799  0 

lp: Error - unable to access "17799" - No such file or directory
antobbo@antobbo-xps17-ubuntu:~$ parport                46562  3 parport_pc,ppdev,lp

parport: command not found
antobbo@antobbo-xps17-ubuntu:~$ r8169                  62099  0 

r8169: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ lsmod

antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$: command not found

antobbo@antobbo-xps17-ubuntu:~$:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ Module                  Size  Used by

antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ Module: command not found

Module:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ bnep                   18281  2 

antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ No command 'bnep' found, did you mean:

No: command not found
antobbo@antobbo-xps17-ubuntu:~$  Command 'beep' from package 'beep' (universe)

bash: syntax error near unexpected token `('
antobbo@antobbo-xps17-ubuntu:~$ bnep: command not found

bnep:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ rfcomm                 47604  0 

antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ RFCOMM configuration utility ver 4.98

RFCOMM: command not found
antobbo@antobbo-xps17-ubuntu:~$ Usage:

Usage:: command not found
antobbo@antobbo-xps17-ubuntu:~$ rfcomm [options] <command> <dev>

bash: syntax error near unexpected token `<'
antobbo@antobbo-xps17-ubuntu:~$ 

antobbo@antobbo-xps17-ubuntu:~$ Options:

Options:: command not found
antobbo@antobbo-xps17-ubuntu:~$ -i [hciX|bdaddr]      Local HCI device or BD Address

-i: command not found
bdaddr]: command not found
antobbo@antobbo-xps17-ubuntu:~$ -h, --help            Display help

-h,: command not found
antobbo@antobbo-xps17-ubuntu:~$ -r, --raw             Switch TTY into raw mode

-r,: command not found
antobbo@antobbo-xps17-ubuntu:~$ -A, --auth            Enable authentication

-A,: command not found
antobbo@antobbo-xps17-ubuntu:~$ -E, --encrypt         Enable encryption

-E,: command not found
antobbo@antobbo-xps17-ubuntu:~$ -S, --secure          Secure connection

-S,: command not found
antobbo@antobbo-xps17-ubuntu:~$ -M, --master          Become the master of a piconet

-M,: command not found
antobbo@antobbo-xps17-ubuntu:~$ -f, --config [file]   Specify alternate config file

-f,: command not found
antobbo@antobbo-xps17-ubuntu:~$ -a                    Show all devices (default)

bash: syntax error near unexpected token `('
antobbo@antobbo-xps17-ubuntu:~$ 

antobbo@antobbo-xps17-ubuntu:~$ Commands:

Commands:: command not found
antobbo@antobbo-xps17-ubuntu:~$ bind     <dev> <bdaddr> [channel]Bind device

bash: syntax error near unexpected token `<'
antobbo@antobbo-xps17-ubuntu:~$ release  <dev>                   Release device

bash: dev: No such file or directory
antobbo@antobbo-xps17-ubuntu:~$ show     <dev>                   Show device

bash: dev: No such file or directory
antobbo@antobbo-xps17-ubuntu:~$ connect  <dev> <bdaddr> [channel]Connect device

bash: syntax error near unexpected token `<'
antobbo@antobbo-xps17-ubuntu:~$ listen   <dev> [channel [cmd]]   Listen

bash: dev: No such file or directory
antobbo@antobbo-xps17-ubuntu:~$ watch    <dev> [channel [cmd]]   Watch

bash: dev: No such file or directory
antobbo@antobbo-xps17-ubuntu:~$ 

antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ bluetooth             180104  10 bnep,rfcomm

antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ No command 'bluetooth' found, did you mean:

No: command not found
antobbo@antobbo-xps17-ubuntu:~$  Command 'bluetoothd' from package 'bluez' (main)
bash: syntax error near unexpected token `('
antobbo@antobbo-xps17-ubuntu:~$ bluetooth: command not found
No command 'bluetooth:' found, did you mean:
 Command 'bluetoothd' from package 'bluez' (main)
bluetooth:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ parport_pc             32866  0 
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ parport_pc: command not found
parport_pc:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ ppdev                  17113  0 
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ No command 'ppdev' found, did you mean:
No: command not found
antobbo@antobbo-xps17-ubuntu:~$  Command 'ppdep' from package 'fp-utils-2.4.4' (universe)
bash: syntax error near unexpected token `('
antobbo@antobbo-xps17-ubuntu:~$ ppdev: command not found
ppdev:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ snd_hda_codec_hdmi     32474  1 
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hda_codec_hdmi: command not found
snd_hda_codec_hdmi:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ snd_hda_codec_realtek   223867  1 
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hda_codec_realtek: command not found
snd_hda_codec_realtek:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ binfmt_misc           
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ binfmt_misc: command not found
binfmt_misc:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobb
antobb: command not found
antobbo@antobbo-xps17-ubuntu:~$ No command 'arc4' found, did you
No: command not found
antobbo@antobbo-xps17-ubuntu:~$  Command 'arch' from package 'co
>  Command 'arc' from package 'arc' (universe)
> arc4: command not found
> antobbo@
> snd_hda_intel: command not found
> antobbo@antobbo-xps17-ubuntu:~$ 
> joydev: command not found
> antobbo@
> iwlwifi: command not found
> antob
> snd_hda_codec: command not found
> antobbo@antobbo-xps17-ubuntu:~$ 
> nvidia: command not found
> antobb
> mac80211: command not found
> anto
> i915: command not found
> antobbo@antobbo-xps17-ubuntu:~$ drm_kms_helper         46978  
> drm_kms_helper: command not foun
> antobbo@antobbo-xps17-ubuntu:~$ drm    
> No command 'drm' found, did you 
>  Command 'dpm' from package 'dpm-ser
Command: command not found
antobbo@antobbo-xps17-ubuntu:~$  Command 'dpm' from package 'dpm-server-mysql' (uni
bash: syntax error near unexpected token `('
antobbo@antobbo-xps17-ubuntu:~$  Command 'crm' from package 'pac
>  Command 'crm' from package 'crm114' (unive
>  Command 'arm' from package 'tor
Command: command not found
antobbo@antobbo-xps17-ubuntu:~$  Command 'rm' from package 'coreutils' (
bash: syntax error near unexpected token `('
antobbo@antobbo-xps17-ubuntu:~$  Command 'rm' from package 'safe-rm' (univers
bash: syntax error near unexpected token `('
antobbo@antobbo-xps17-ubuntu:~$  Command 'vrm' from package 'atfs' (universe)
bash: syntax error near unexpected token `('
antobbo@antobbo-xps17-ubuntu:~$  Command 'srm' from package 'sec
>  Command 'drc' from package 'drc
Command: command not found
antobbo@antobbo-xps17-ubuntu:~$  Command 'frm' from package 'mailutils' (uni
bash: syntax error near unexpected token `('
antobbo@antobbo-xps17-ubuntu:~$  Command 'drr' from package 'plastimatch' (u
bash: syntax error near unexpected token `('
antobbo@antobbo-xps17-ubuntu:~$  Command 'dwm' from package 'dwm' (universe)
bash: syntax error near unexpected token `('
antobbo@antobbo-xps17-ubuntu:~$ drm: command not f
drm:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ dell_laptop    
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ dell_laptop: command not found
dell_laptop:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ d
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ dcdbas: command not found
dcdbas:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobb
antobb: command not found
antobbo@antobbo-xps17-ubuntu:~$ uvcvideo: command not found
uvcvideo:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps1
antobbo@antobbo-xps1: command not found
antobbo@antobbo-xps17-ubuntu:~$ videodev: command not found
videodev:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ snd_hwdep              13668  1 snd_hda_codec
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_hwdep: command not found
snd_hwdep:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:
antobbo@antobbo-xps17-ubuntu:: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_pcm: command not found
snd_pcm:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@
antobbo@: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_seq_midi: command not found
snd_seq_midi:: command not found
antobbo@antobbo-xps17-ubuntu:~$ 
antobbo@antobbo-xps17-ubuntu:~$ snd_rawmidi: command not found
snd_rawmidi:: command not found
antobbo@antobbo-xps17-ubuntu:~$ a
a: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_seq_midi_event: command not found
snd_seq_midi_event:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo
antobbo@antobbo: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_seq: command not found
snd_seq:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antob
antobbo@antob: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_timer: command not found
snd_timer:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo
antobbo: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_seq_device: command not foun
snd_seq_device:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ psmouse 
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ psmouse: command not found
psmouse:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antob
antobbo@antob: command not found
antobbo@antobbo-xps17-ubuntu:~$ cfg80211: command not found
cfg80211:: command not found
antobbo@antobbo-xps17-ubuntu:~$ anto
No command 'anto' found, did you mean:
 Command 'canto' from package 'canto' (universe)
 Command 'ant' from package 'ant' (main)
 Command 'ant' from package 'ant1.7' (universe)
 Command 'anno' from package 'nmh' (universe)
 Command 'anno' from package 'mailutils-mh' (universe)
anto: command not found
antobbo@antobbo-xps17-ubuntu:~$ The program 'snd' can be found in th
No command 'The' found, did you mean:
 Command 'the' from package 'the' (universe)
The: command not found
antobbo@antobbo-xps17-ubuntu:~$  * snd-gtk-jack
Desktop: command not found
antobbo@antobbo-xps17-ubuntu:~$  * snd-gtk-pulse
Desktop: command not found
antobbo@antobbo-xps17-ubuntu:~$  * snd-nox
Desktop: command not found
antobbo@antobbo-xps17-ubuntu:~$ Try: sudo apt-get install <selected pack
bash: selected: No such file or directory
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ 
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ soundcore: command not found
soundcore:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ serio_ra
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ serio_raw: command not found
serio_raw:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17
antobbo@antobbo-xps17: command not found
antobbo@antobbo-xps17-ubuntu:~$ dell_wmi: command not found
dell_wmi:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ snd_page_
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ snd_page_alloc: command n
snd_page_alloc:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ v4l2_compat_ioctl32    17128  1 
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ v4l2_compat_ioctl32: command not found
v4l2_compat_ioctl32:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ i2c_algo_bit  
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ i2c_algo_bit: command n
i2c_algo_bit:: command not found
antobbo@antobbo-xps17-ubuntu:~$ antobbo@antobbo-xps17-ubuntu:~$ mei                    41616  0 
antobbo@antobbo-xps17-ubuntu:~$: command not found
antobbo@antobbo-xps17-ubuntu:~$ No command 'mei' found, did you mean:
No: command not found
antobbo@antobbo-xps17-ubuntu:~$  Comma
Comma: command not found
antobbo@antobbo-xps17-ubuntu:~$  Command 'mex' from package 'texl
> 
> mei: com
> antobbo@antobbo-xps17-ubuntu:~$ sparse_keymap        
> sparse_keymap: command not found
> an
> No command 'wmi' found, did you mean:
>  Command 
>  Command 'wmk' from package 'wml' (universe)
>  Command 'wmb' from package 'wml' (unive
>  Command 'wmf' from package 'wmf' (unive
>  Command 'wmd' from package 'wml' (universe)
>  Command
>  Command 'wmii' from package 'wmii' (universe)
>  Comm
>  Command 'wmix' from package 'wmix' (universe)
>  C
> 
>  Command 
>  Command 'mi' from package 'libxgks-dev' (univ
>  Command 'wml' from package 'wml' (universe)
> wmi:
> antobbo@antobbo-xps17-ubuntu:~$ mac_hid       
> mac_hid: command not found
> antobbo@antobbo-xps17-
> video: command not found
> antobbo@antobbo-
> lp: Error - unable to access "17799" - N
> 
> parport: command not found
> antobbo@antobbo-xps17-ubuntu:~$ r8169            
> r8169: command not found
> antobbo@antobbo-xp
> 

Let me know if you want me to do it again

---

### Post by NikTh on 2012-07-22
Hi , 

sorry but i cannot understand , what are all these. 
First of all:
**Please put the results inside [CODE] tags , by highlighting the text and click [SIZE=3]#[/SIZE] symbol on top of message pane . **

So the output can be readable . 
This you posted its not readable. I cannot read anything. Sorry. 

Second :  did you  COPY-PASTE the commands (from here to YOUR terminal) . Did you do that ? 

One line = One Command. 

Do again what its in #12th post , and please **Edit** your 13th post by adding [CODE] tags , [CODE] brackets .. 
highlight the text and click # symbol on top of message pane. 

Thanks

---

### Post by bkratz on 2012-07-22
[COLOR=Black]@[antobbo]("http://ubuntuforums.org/member.php?u=914731")[/COLOR]

When exiting windows did you have the wireless turned off?   Leave the switch on when leaving windows and try again in Ubuntu, this seems to be fairly common when windows has control.


[http://askubuntu.com/questions/127977/wireless-is-disabled-by-hardware-switch-on-dell-inspiron-1750](http://askubuntu.com/questions/127977/wireless-is-disabled-by-hardware-switch-on-dell-inspiron-1750)

[http://askubuntu.com/questions/148215/wireless-card-works-in-ubuntu-wubi-install-only-if-i-dont-turn-it-off-in-window](http://askubuntu.com/questions/148215/wireless-card-works-in-ubuntu-wubi-install-only-if-i-dont-turn-it-off-in-window)

---

### Post by antobbo on 2012-07-28
Hi apologies for that, I forgot to format the text correctly and also the output was funny. I have done it again.


The first command ```
echo 'blacklist dell-wifi' | sudo tee -a /etc/modprobe.d/blacklist.conf g
```enerates this:

```
antobbo@antobbo-xps17-ubuntu:~$ echo 'blacklist dell-wifi' | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for antobbo: 
blacklist dell-wifi
antobbo@antobbo-xps17-ubuntu:~$
```


Then I unplugged the cable and restarted the machine. Without cable here are the input and output:
The first command
```
sudo rfkill unblock all
```
generated nothing, it only asked for my password:
```
antobbo@antobbo-xps17-ubuntu:~$ sudo rfkill unblock all
[sudo] password for antobbo: 
antobbo@antobbo-xps17-ubuntu:~$ 
```

The second ```
iwconfig
``` generated this:
```
antobbo@antobbo-xps17-ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

antobbo@antobbo-xps17-ubuntu:~$ 

```
The third one ```
lsmod
``` this:
```
antobbo@antobbo-xps17-ubuntu:~$ lsmod
Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223962  1 
joydev                 17693  0 
binfmt_misc            17540  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
nvidia              12319264  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
arc4                   12529  2 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop            18119  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
psmouse                87692  0 
serio_raw              13211  0 
v4l2_compat_ioctl32    17128  1 videodev
iwlwifi               332672  0 
i915                  472897  2 
mac80211              506816  1 iwlwifi
soundcore              15091  1 snd
drm_kms_helper         46978  1 i915
dcdbas                 14490  1 dell_laptop
cfg80211              205544  2 iwlwifi,mac80211
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
drm                   242038  3 i915,drm_kms_helper
mac_hid                13253  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
wmi                    19256  1 dell_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
antobbo@antobbo-xps17-ubuntu:~$ 

```
the fourth one ```
lspci -nnk | grep -iA2 net
``` this:

```
antobbo@antobbo-xps17-ubuntu:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008a] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
    Kernel driver in use: iwlwifi
--
0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Dell Device [1028:04b8]
    Kernel driver in use: r8169
antobbo@antobbo-xps17-ubuntu:~$ 

```

The fifth one  ```
rfkill list all
``` this:
```
antobbo@antobbo-xps17-ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```

SO it looks like it is hard blocked whatever that means.
@bkratz, I tried that, no joy
thanks

---

### Post by Finnicella on 2012-08-04
Try with these commands:
```
sudo rfkill unblock 0
```
```
sudo rfkill unblock 1
```
```
sudo rfkill unblock 2
```
and give the output of this command:
```
sudo rfkill list all
```
Bye

---

### Post by antobbo on 2012-08-04
hi thanks I sorted it out. I had to download and install the drivers , it works now
thanks

---

### Post by Finnicella on 2012-08-04
Ok, I'm very happy to know.
Bye

---

