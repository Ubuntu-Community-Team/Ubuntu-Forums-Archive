---
title: "Wireless is disabled by hardware switch on Ubuntu 12.04."
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by PebbsLily on 2013-02-16
I have instlled Ubuntu 12.04. on my Dell Inspirion Mini 1018. After  doing one of regular updates, my wifi stop working, and it gives me  message "Wireless is disabled by hardware switch". 
How can I enable it? I tried opening network connections, but there I  find: Wireless Unavaible. Hardware Address 1C:65:9D:68:9E:6B


Thank I tried System testing, it gives me a message: "# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci"


This what I get after mn-tool :
Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             unavailable
  Default:           no
  HW Address:        1C:65:9D:68:9E:6B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

Next command I used sudo lshw -C network :

  *-network DISABLED
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 1c:65:9d:68:9e:6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-37-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:f0100000-f0103fff


How can I enable it?

---

### Post by chili555 on 2013-02-16
Please run and post:```
rfkill list all
dmesg | grep rtl
```Have you tried the wireless button F2?

---

### Post by PebbsLily on 2013-02-16
rfkill list all
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

dmesg | grep rtl
[   26.466807] rtl8192ce 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.466830] rtl8192ce 0000:07:00.0: setting latency timer to 64
[   28.056166] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   28.064943] rtlwifi: wireless switch is on

---

### Post by chili555 on 2013-02-16
And how about the wireless button F2? Does that change anything?```
rfkill list all
```Press F2.```
rfkill list all
```Any changes?

---

### Post by PebbsLily on 2013-02-16
No reaction on F2, same results.
rfkill list all
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
 
F@   rfkill list all
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
ljiljana@ljiljana-laptop:~$

---

### Post by chili555 on 2013-02-16
Please see if you have a module loaded *dell-wmi*.```
lsmod | grep dell
```If so, let's try temporarily removing it:```
sudo modprobe -r dell-wmi
sudo rfkill unblock all
rfkill list all
```Any change?

---

### Post by PebbsLily on 2013-02-16
On a first command I got this:

dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop


Before I start next step, just wanted to say, I have AipPlane Mode ON all the time, I can't switch it. I tried few times, but it always goes back on. Curious, does this can provoke disabled wifi? If you know how to disable AirPlane Mode, please, tell me. Perhaps only through terminal?

---

### Post by chili555 on 2013-02-16
Airplane Mode simply means the switch is set to disable the wireless radio.

Please proceed.

---

### Post by PebbsLily on 2013-02-17
ljiljana@ljiljana-laptop:~$ sudo modprobe -r dell-wmi
[sudo] password for ljiljana: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
ljiljana@ljiljana-laptop:~$ sudo rfkill unblock all
ljiljana@ljiljana-laptop:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
ljiljana@ljiljana-laptop:~$

---

### Post by PebbsLily on 2013-02-17
Did all you asked, and posted in my last replay. 
Here is a second thing that is not normal (at least I think it is not normal).... Look at this, please: AirPlane Mode that is always ON. Just wanted to know what instruction I use to put it to sleep? When I just press OFF button, it switches for a short time, till I close network connection, or I go other settings. Same moment I do anything else it goes back to ON. Is there some way to prevent it and keep my laptop out of AirPlane Mode? 
Maybe we should finish first what we started, than this, but I am just a bit confuzed with all this. Thanks for helping me !!

---

### Post by chili555 on 2013-02-17
> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.Uh oh! May we see it?```
cat /etc/modprobe.d/blacklist
```May we also see:```
lsmod | grep ndis
dmesg | grep ndis
```

---

### Post by Hadaka on 2013-02-17
Hi, please click the airplane mode to OFF and post the
output of..

```
rkill list all
lsmod 
```
thanks

---

### Post by Hadaka on 2013-02-17
Hi, I'm also curious about the RTL card in a dell machine
please post..
```
lspci -nn | egrep '0200|0280'
lsusb 
```
thanks

---

### Post by PebbsLily on 2013-02-17
Looks like we live in a very different time zone. Sorry for going to bed yesterday, but it was already around 3 am here when I left. Now is 9 pm. I will try to stay awake as long as I could. Would love to resolve this problem soon. Thanks. 
I followed your instructions, here is copy paste:

ljiljana@ljiljana-laptop:~$ sudo modprobe -r dell-wmi
[sudo] password for ljiljana: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
ljiljana@ljiljana-laptop:~$ sudo rfkill unblock all
ljiljana@ljiljana-laptop:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
ljiljana@ljiljana-laptop:~$

---

### Post by PebbsLily on 2013-02-17
Sorry for repeating myself! 

Here is now one. First 3 command you sent :

ljiljana@ljiljana-laptop:~$ cat /etc/modprobe.d/blacklist
blacklist ath pci
blacklist rtl819x
ljiljana@ljiljana-laptop:~$ lsmod | grep ndis
ljiljana@ljiljana-laptop:~$ dmesg | grep ndis

---

### Post by PebbsLily on 2013-02-17
Next:

ljiljana@ljiljana-laptop:~$ rkill list all
The program 'rkill' is currently not installed.  You can install it by typing:
sudo apt-get install pslist
ljiljana@ljiljana-laptop:~$ 

ljiljana@ljiljana-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
ums_realtek            17920  0 
usb_storage            39646  1 ums_realtek
uas                    17828  0 
hidp                   22165  0 
hid                    77428  1 hidp
dm_crypt               22528  0 
btusb                  17948  2 
wl                   2906597  0 
joydev                 17393  0 
lib80211               14040  1 wl
arc4                   12473  2 
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158479  24 hidp,btusb,rfcomm,bnep
ppdev                  12849  0 
uvcvideo               67203  0 
snd_hda_codec_realtek   174313  1 
rtl8192ce              75529  0 
psmouse                96718  0 
videodev               86588  1 uvcvideo
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95839  1 rtl8192ce
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
serio_raw              13027  0 
binfmt_misc            17292  1 
mac80211              436493  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
cfg80211              178877  3 wl,rtlwifi,mac80211
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  419326  3 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
r8169                  56368  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
ljiljana@ljiljana-laptop:~$

---

### Post by PebbsLily on 2013-02-17
Third mail output:

ljiljana@ljiljana-laptop:~$ lspci -nn | egrep '0200|0280'
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
ljiljana@ljiljana-laptop:~$ 

ljiljana@ljiljana-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 174f:1127 Syntek 
Bus 005 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
ljiljana@ljiljana-laptop:~$

---

### Post by PebbsLily on 2013-02-17
Again second output, this time with airplane mode set on off (forgot to do it first time)

ljiljana@ljiljana-laptop:~$ rkill list all
The program 'rkill' is currently not installed.  You can install it by typing:
sudo apt-get install pslist
ljiljana@ljiljana-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
ums_realtek            17920  0 
usb_storage            39646  1 ums_realtek
uas                    17828  0 
hidp                   22165  0 
hid                    77428  1 hidp
dm_crypt               22528  0 
btusb                  17948  2 
wl                   2906597  0 
joydev                 17393  0 
lib80211               14040  1 wl
arc4                   12473  2 
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158479  24 hidp,btusb,rfcomm,bnep
ppdev                  12849  0 
uvcvideo               67203  0 
snd_hda_codec_realtek   174313  1 
rtl8192ce              75529  0 
psmouse                96718  0 
videodev               86588  1 uvcvideo
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95839  1 rtl8192ce
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
serio_raw              13027  0 
binfmt_misc            17292  1 
mac80211              436493  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
cfg80211              178877  3 wl,rtlwifi,mac80211
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  419326  3 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
r8169                  56368  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
ljiljana@ljiljana-laptop:~$

---

### Post by chili555 on 2013-02-17
This just gets crazier by the moment. I am almost afraid to open each succeeding post! First, the blacklist file (*NOT* blacklist.conf) is needless. Let's remove it:```
sudo rm /etc/modprobe.d/blacklist
```Second, you have no Broadcom wireless card, although the driver for a card you don't have is loaded!> [COLOR="Red"]wl[/COLOR] 2906597 0
joydev 17393 0
[COLOR="Red"]lib80211[/COLOR] 14040 1 [COLOR="Red"]wl[/COLOR]
arc4 12473 2
dell_laptop 17767 0
dcdbas 14098 1 dell_laptop
<snip>Let's remove the driver:```
sudo apt-get remove --purge bcmwl-kernel-source
```Next, let's be sure there is no directive to load *wl* or anything other than rtl8192ce:```
gksudo gedit /etc/modules
```If *wl* is in there, remove it. If anything else related to wireless is in there, tell me so we can decide to remove it. Proofread, save and close gedit.

Reboot and let me have your report.

---

### Post by PebbsLily on 2013-02-17
I am posting it all, step by step. If anything go wrong, hope we can return to previous...

Here is a first output:

ljiljana@ljiljana-laptop:~$ sudo rm /etc/modprobe.d/blacklist
[sudo] password for ljiljana: 
ljiljana@ljiljana-laptop:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29-generic linux-headers-3.2.0-29
  linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,656 kB disk space will be freed.
Do you want to continue [Y/n]? 

I pressed y , here it is:
Do you want to continue [Y/n]? y
(Reading database ... 497182 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules

---

### Post by PebbsLily on 2013-02-17
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic

---

### Post by PebbsLily on 2013-02-17
modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
lp

---

### Post by chili555 on 2013-02-17
So far, so good!

---

### Post by PebbsLily on 2013-02-17
wireless still disabled by hardware switch

---

### Post by Hadaka on 2013-02-17
Hi, please hold down the Fn key (should be next to the windows key..bottom left)
and while holding down the Fn key press the F2 key...ONE.time, then please post

```
rfkill list all 
```
also see that the airplane mode is OFF
thanks

---

### Post by PebbsLily on 2013-02-17
ljiljana@ljiljana-laptop:~$ rfkill list all
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
ljiljana@ljiljana-laptop:~$

---

### Post by Hadaka on 2013-02-17
Hi, please press the Fn/F2 One more time please, 
to return the wireless back to the unblocked state
and then again please do..
```
rfkill list all 
```to verify .
also...after you post, power down and remove
anything you may have plugged into a usb port.
thanks

---

### Post by PebbsLily on 2013-02-17
as i said, this doesn't work... i tried 1.000 times... it should be resolved differently, not by switching it on and off - not possible

---

### Post by Hadaka on 2013-02-17
Hi, I know it is late for you and this is very frustrating, but there has been
a couple of items found that were adding to the problem and sometimes
things need to be repeated to verify forward progress, with that would you
please post the output of..

```
grep blacklist /etc/modprobe.d/blacklist.conf 
```

thanks for hanging in there.

---

### Post by PebbsLily on 2013-02-18
Here is the output:
ljiljana@ljiljana-laptop:~$ grep blacklist /etc/modprobe.d/blacklist.conf
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist ssb
blacklist ath_hal
blacklist ath_pci
ljiljana@ljiljana-laptop:~$

---

### Post by Hadaka on 2013-02-18
Hi, in this thread, with the same dell mini computer and blockages you have
chili555 suggested resetting the bios to default values and that solved the
issue, perhaps you should give that a try also..

[http://ubuntuforums.org/showthread.php?t=2047017&page=2](http://ubuntuforums.org/showthread.php?t=2047017&page=2)

---

### Post by PebbsLily on 2013-02-18
Chilly, help!! What to do next, please? My wifi is still not working

---

### Post by chili555 on 2013-02-18
Frankly, I have no further ideas. If you have tried F2, removing *dell-laptop*, rfkill unblock all and resetting the BIOS and nothing makes any difference whatever, I don't know anything else to try. I am very sorry.

---

### Post by Hadaka on 2013-02-18
Hi, were you able to reset any values in bios ?
if you need help with the dell bios and how to
navigate it, let me know
thanks.

---

### Post by PebbsLily on 2013-02-19
I don't know how to work in bios, thanks

---

### Post by PebbsLily on 2013-02-20
give me instruction what to do in bios,please

---

### Post by lxjaiji on 2013-04-24
is it possible that two drivers are installed?

---

### Post by chili555 on 2013-04-24
> **lxjaiji said:**
> is it possible that two drivers are installed?If you installed a second driver and didn't blacklist the default driver, then yes. Did you?

---

### Post by lxjaiji on 2013-04-26
my wireless already working. im asking pebslily.. :-)  seems pebslily hasnt turn on the wi-fi switch of his/her lap top. look at the rfkill list 

ljiljana@ljiljana-laptop:~$ sudo modprobe -r dell-wmi
[sudo] password for ljiljana: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
ljiljana@ljiljana-laptop:~$ sudo rfkill unblock all
ljiljana@ljiljana-laptop:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    [COLOR=#ff0000]Hard blocked: yes[/COLOR]
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
ljiljana@ljiljana-laptop:~$

---

### Post by chili555 on 2013-04-26
> im asking pebslily.. seems pebslily hasnt turn on the wi-fi switch of his/her lap top. look at the rfkill listAs you can see by reading the entire thread, he has pressed the switch many, many times and nothing has changed.

---

