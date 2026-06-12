---
title: "WIFI: Adapter 3945abg on 12.10"
date: 2013-03-29
forum: Networking &amp; Wireless
---

### Post by Volleumel on 2013-03-29
Hi,

I'm absolutely new to Linux!

My netbook lenovo x61s with Wifi Adapter Intel 3945abg doesn´t connect. The hardware switch is ON and the adapter should work (WinXP is installed on the same machine and Wifi works). 

I tried many things that are recommended throughout the Internet, but as Newbie I'm rather typing commands than understanding what I do. :confused: I think I even erased the Network Manager... fighting myself through vi-Editor etc. etc.. I think I spent at least 10hours struggling with wifi.

To be honest I am completely lost and this will be my last attempt. Otherwise I will deinstall it.

iwconfig results:
wlan0 IEEE 802.11abg  ESSID: off/any Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm Retry long limit:7 RTS thr: off Fragment thr: off Power Management: on
lo no wireless extensions
eth0 no wireless extensions


What shall I do? HELP ME PLEASE!

thanks in advance
Volleumel

---

### Post by wildmanne39 on 2013-03-29
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by Volleumel on 2013-03-29
> **Wild Man said:**
> 
It will **download** 

Here's the first problem: No WIFI, no Internet on the machine. My router doesn't have a LAN port. Is there a possibility to do that like downloading said script with my desktop-machine onto a USB-stick and to execute it from said stick?

---

### Post by wildmanne39 on 2013-03-29
Follow the directions in this link to run the script without internet access.
[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)
Thanks

---

### Post by Volleumel on 2013-03-29
I tried it but the "Execute" checkbox in "permissions" immediately gets empty again... Is that Linux where every little step turns into a new problem?

Edit: now it works. wait a minute for the netinfo file!

---

### Post by Volleumel on 2013-03-29
*************** info trace ****************



**** uname -a ****


Linux MiniMe 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
    Subsystem: Lenovo Device [17aa:20de]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
    Subsystem: Intel Corporation ThinkPad R60e/X60s [8086:1011]
    Kernel driver in use: iwl3945


**** lsusb ****


Bus 001 Device 003: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


**** rfkill ****


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            39350  1 
uas                    17556  0 
snd_hda_codec_analog    75059  1 
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel
parport_pc             31968  0 
ppdev                  12817  0 
rfcomm                 37276  16 
bnep                   17707  2 
pcmcia                 39509  0 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
psmouse                84843  0 
arc4                   12473  2 
microcode              18209  0 
serio_raw              13031  0 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
thinkpad_acpi          69337  1 
iwl3945                63695  0 
iwlegacy               87736  1 iwl3945
yenta_socket           27095  0 
pcmcia_rsrc            18191  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
lpc_ich                16925  0 
nvram                  13986  1 thinkpad_acpi
mac80211              461161  2 iwl3945,iwlegacy
cfg80211              175375  3 iwl3945,iwlegacy,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
btusb                  17950  0 
bluetooth             183228  22 rfcomm,bnep,btusb
tpm_tis                18208  0 
i915                  457161  2 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61991  18 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
mac_hid                13037  0 
drm_kms_helper         45271  1 i915
drm                   230463  3 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
video                  18847  1 i915
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
firewire_ohci          35521  0 
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e1000e                174645  0 


**** nm-tool ****




**** NetworkManager.state ****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[   15.872128] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   15.872131] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   16.782481] iwl3945 0000:03:00.0: >Tunable channels: 13 802.11bg, 23 802.11a channels
[   16.782487] iwl3945 0000:03:00.0: >Detected Intel Wireless WiFi Link 3945ABG
[   16.782646] iwl3945 0000:03:00.0: >irq 44 for MSI/MSI-X
[   16.819366] ieee80211 phy0: >Selected rate control algorithm 'iwl-3945-rs'


**************** done ********************

---

### Post by wildmanne39 on 2013-03-29
Let's turn power management off:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off 
```
above exit0, then save gedit, close and reboot.
If this does not get it working we will try some driver parameters.
Thanks

---

### Post by Volleumel on 2013-03-29
I typed in 

gksudo gedit /etc/pm/power.d/wireless

pressed return, and: Nothing happens! A new command line appears, that's all. 

:confused:

---

### Post by wildmanne39 on 2013-03-29
Did you follow the rest of the directions under the command?
Thanks

---

### Post by Volleumel on 2013-03-29
What directions? As I said I typed in the command you told me, but I've got the impression that there is no gedit application on my machine. No editor appears. I tried to create the code with vi but several error messages later the folder "power.d" is still empty. 
You have to tell me each and every keystroke...

---

### Post by wildmanne39 on 2013-03-29
Xubuntu using leafpad, sorry I did not see that you were using xubuntu, I always install gedit that is my preferred editor.
I am not exactly sure how you use leafpad but you have to make sure you save the file, exit then reboot.
Thanks

---

### Post by Volleumel on 2013-03-29
I even created that file in WinXP with Notepad on my USB Stick, put the latter into my Netbook but Linux doesn't allow me to copy it into said directory!

---

### Post by wildmanne39 on 2013-03-29
This is the command for xubuntu:
```
gksudo leafpad /etc/pm/power.d/wireless
```
after you enter the command you need to enter your user password but it will not show in the terminal just hit enter fter you copy and paste the command.
I have to go to the doctor be back in a few hours.
Thanks

---

### Post by Volleumel on 2013-03-29
Okay, thanks so far.

> **Wild Man said:**
> 
If this does not get it working we will try some driver parameters.
Thanks

Here we are!

---

### Post by Volleumel on 2013-03-29
What shall I do next?

---

### Post by wildmanne39 on 2013-03-29
Please try:
```
sudo su
echo options iwl3945 swcrypto=1 >> /etc/modprobe.d/iwl3945.conf
```
Thanks

---

### Post by Volleumel on 2013-03-30
I think it doesn't work. But to be sure: how can I check wifi function when my Network Manager icon disappeared?

---

### Post by wildmanne39 on 2013-03-30
Remove the infotext file from your home folder and run the script again and post the results so we can see if it is connecting also see if you can load web pages.
Thanks

---

### Post by Volleumel on 2013-03-30
Voilà


*************** info trace ****************



**** uname -a ****


Linux MiniMe 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
    Subsystem: Lenovo Device [17aa:20de]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
    Subsystem: Intel Corporation ThinkPad R60e/X60s [8086:1011]
    Kernel driver in use: iwl3945


**** lsusb ****


Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


**** rfkill ****


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
snd_hda_codec_analog    75059  1 
parport_pc             31968  0 
ppdev                  12817  0 
rfcomm                 37276  16 
bnep                   17707  2 
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel
pcmcia                 39509  0 
psmouse                84843  0 
microcode              18209  0 
arc4                   12473  2 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
iwl3945                63695  0 
yenta_socket           27095  0 
serio_raw              13031  0 
pcmcia_rsrc            18191  1 yenta_socket
btusb                  17950  0 
thinkpad_acpi          69337  1 
snd_timer              24411  2 snd_pcm,snd_seq
iwlegacy               87736  1 iwl3945
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              461161  2 iwl3945,iwlegacy
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
tpm_tis                18208  0 
lpc_ich                16925  0 
bluetooth             183228  22 rfcomm,bnep,btusb
nvram                  13986  1 thinkpad_acpi
mac_hid                13037  0 
i915                  457161  2 
snd                    61991  18 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
cfg80211              175375  3 iwl3945,iwlegacy,mac80211
drm_kms_helper         45271  1 i915
drm                   230463  3 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
e1000e                174645  0 


**** nm-tool ****




**** NetworkManager.state ****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[   14.755830] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   14.755833] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   14.815831] iwl3945 0000:03:00.0: >Tunable channels: 13 802.11bg, 23 802.11a channels
[   14.815837] iwl3945 0000:03:00.0: >Detected Intel Wireless WiFi Link 3945ABG
[   14.815995] iwl3945 0000:03:00.0: >irq 44 for MSI/MSI-X
[   14.845951] ieee80211 phy0: >Selected rate control algorithm 'iwl-3945-rs'


**************** done ********************

---

### Post by wildmanne39 on 2013-03-30
The power management still did not turn off so let's try it this way please:
```
echo -e '#!/bin/bash\n/sbin/iwconfig wlan0 power off' | sudo tee -a /etc/pm/power.d/wireless

```
Reboot
Thanks

---

### Post by Volleumel on 2013-03-30
It's still ON. Here's the file again:


*************** info trace ****************



**** uname -a ****


Linux MiniMe 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
    Subsystem: Lenovo Device [17aa:20de]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
    Subsystem: Intel Corporation ThinkPad R60e/X60s [8086:1011]
    Kernel driver in use: iwl3945


**** lsusb ****


Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


**** rfkill ****


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
snd_hda_codec_analog    75059  1 
coretemp               13168  0 
kvm_intel             126745  0 
parport_pc             31968  0 
ppdev                  12817  0 
kvm                   357806  1 kvm_intel
rfcomm                 37276  16 
bnep                   17707  2 
pcmcia                 39509  0 
arc4                   12473  2 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
microcode              18209  0 
iwl3945                63695  0 
psmouse                84843  0 
yenta_socket           27095  0 
iwlegacy               87736  1 iwl3945
pcmcia_rsrc            18191  1 yenta_socket
serio_raw              13031  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
mac80211              461161  2 iwl3945,iwlegacy
thinkpad_acpi          69337  1 
snd_timer              24411  2 snd_pcm,snd_seq
nvram                  13986  1 thinkpad_acpi
lpc_ich                16925  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              175375  3 iwl3945,iwlegacy,mac80211
btusb                  17950  0 
bluetooth             183228  22 rfcomm,bnep,btusb
snd                    61991  18 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device
tpm_tis                18208  0 
i915                  457161  2 
mac_hid                13037  0 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
drm_kms_helper         45271  1 i915
drm                   230463  3 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
e1000e                174645  0 


**** nm-tool ****




**** NetworkManager.state ****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[   16.586796] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   16.586802] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   16.643163] iwl3945 0000:03:00.0: >Tunable channels: 13 802.11bg, 23 802.11a channels
[   16.643169] iwl3945 0000:03:00.0: >Detected Intel Wireless WiFi Link 3945ABG
[   16.643331] iwl3945 0000:03:00.0: >irq 44 for MSI/MSI-X
[   16.674659] ieee80211 phy0: >Selected rate control algorithm 'iwl-3945-rs'


**************** done ********************

---

### Post by wildmanne39 on 2013-03-30
Let me do a little checking and see if that file may have been moved in 12.10.
Thanks

---

### Post by Volleumel on 2013-03-30
Thanks. I will wait for you!

---

### Post by wildmanne39 on 2013-03-30
Post the output of:
```
iwconfig
```please.
I ask the expert to take a look so maybe he will drop by.
Thanks

---

### Post by Volleumel on 2013-03-30
wlan0     IEEE 802.11abg  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:n
          
lo no wireless extensions

eth0 no wireless extensions

---

### Post by chili555 on 2013-03-30
Rather than pass suggestions to Wild Man by PM and then have him suggest them to you, why don't I just barge in and help. More heads are better than less.> I think I even erased the Network Manager.Let's check that first:```
sudo dpkg -s network-manager
```If it's installed, you will see OK Installed OK. Otherwise, dpkg-query: package 'network-manager' is not installed and no information is available. 

How we get your wireless going will differ between the two answers.

Does your interface scan?```
sudo rfkill unblock all
sudo iwlist wlan0 scan
```If there are errors or warnings, we need to see what they are in order to proceed.

---

### Post by Volleumel on 2013-03-30
thanks for helping me. Here's the log of the three commands:

sugardaddy@MiniMe:~$ sudo dpkg -s network-manager
[sudo] password for sugardaddy: 
Package: network-manager
Status: deinstall ok config-files
Priority: optional
Section: net
Installed-Size: 1784
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 0.9.6.0-0ubuntu7
Config-Version: 0.9.6.0-0ubuntu7
Depends: libc6 (>= 2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libglib2.0-0 (>= 2.31.8), libgudev-1.0-0 (>= 147), libnl-3-200 (>= 3.2.7), libnl-genl-3-200 (>= 3.2.7), libnl-route-3-200, libnm-glib4 (>= 0.9.4.0+git201206081144.2efeac8), libnm-util2 (>= 0.9.4.0+git201206041025.716a09d), libpolkit-gobject-1-0 (>= 0.99), libsoup2.4-1 (>= 2.26.1), upstart-job, lsb-base (>= 3.2-14), wpasupplicant (>= 0.7.3-1), dbus (>= 1.1.2), udev, isc-dhcp-client (>= 4.1.1-P1-4), iproute, dnsmasq-base, policykit-1, iputils-arping
Pre-Depends: dpkg (>= 1.15.7.2)
Recommends: network-manager-pptp, network-manager-gnome | network-manager-kde | plasma-widget-networkmanagement, ppp (>= 2.4.5), iptables, modemmanager
Suggests: avahi-autoipd, python
Breaks: network-manager-gnome (<< 0.8.99), network-manager-kde (<< 1:0.9~~), network-manager-openvpn (<< 0.8.99), network-manager-pptp (<< 0.8.99), network-manager-vpnc (<< 0.8.99), ppp (<< 2.4.5)
Conflicts: connman
Conffiles:
 /etc/dnsmasq.d/network-manager c1f294c4513fa544565d671dcba6a913
 /etc/NetworkManager/NetworkManager.conf 725fe5849b897aeda40cc37b83f9e1ef
 /etc/NetworkManager/dispatcher.d/01ifupdown e491a5bec6ce58505181d573d38036bc
 /etc/dbus-1/system.d/org.freedesktop.NetworkManager.conf 085862a743c8c19373b74c062a241f1a
 /etc/dbus-1/system.d/nm-dhcp-client.conf 06b1ecfd8f1fa2a501a5f352e2e5e88e
 /etc/dbus-1/system.d/nm-dispatcher.conf 5711a76c31a3763750fe2c331741f679
 /etc/dbus-1/system.d/nm-avahi-autoipd.conf 91ab68968b0dc06c3a55b482b50b3028
 /etc/init/network-manager.conf 080b2a860317698f65f960687f5363cc
Description: network management framework (daemon and userspace tools)
 NetworkManager is a system network service that manages your network devices
 and connections, attempting to keep active network connectivity when
 available. It manages ethernet, WiFi, mobile broadband (WWAN), and PPPoE
 devices, and provides VPN integration with a variety of different VPN
 services.
 .
 This package provides the userspace daemons and a command line interface to
 interact with NetworkManager.
 .
 Optional dependencies:
  * ppp: Required for establishing dial-up connections (e.g. via GSM).
  * avahi-autoipd: Used for IPv4LL, a protocol for automatic Link-Local IP
    address configuration.
Homepage: [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>
sugardaddy@MiniMe:~$ sudo rfkill unblock all
[sudo] password for sugardaddy: 
sugardaddy@MiniMe:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

---

### Post by chili555 on 2013-03-30
> sugardaddy@MiniMe:~$ sudo dpkg -s network-manager
[sudo] password for sugardaddy:
Package: network-manager
[COLOR="#FF0000"]Status: deinstall ok config-files[/COLOR]I believe that means the package network-manager is removed and the configuration files were not removed. I think the package being removed is confirmed by the absence of any reply to nm-tool. Now let's see:```
sudo ifconfig wlan0 up
ifconfig
iwconfig
```Again, we may see errors or warnings which help us.

---

### Post by Volleumel on 2013-03-30
Voilà

sugardaddy@MiniMe:~$ sudo ifconfig wlan0 up
[sudo] password for sugardaddy: 
sugardaddy@MiniMe:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13712 (13.7 KB)  TX bytes:13712 (13.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:6e:ba:6a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sugardaddy@MiniMe:~$ iwconfig
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2013-03-30
Now we see wlan0 as UP in ifconfig. Did the rfkill command solve the soft-blocked issue?```
sudo rfkill unblock all
rfkill list all
```If so, now it should scan:```
sudo iwlist wlan0 scan
```If not, we wonder if there are messages in the logs about this peculiar little issue:```
dmesg | grep iwl
```Are you connected by ethernet? How?

---

### Post by Volleumel on 2013-03-30
> **chili555 said:**
> Now we see wlan0 as UP in ifconfig. Did the rfkill command solve the soft-blocked issue?```
sudo rfkill unblock all
rfkill list all
```If so, now it should scan:```
sudo iwlist wlan0 scan
```...

yes. It finally scanned and found my router. How can I put in the password?

---

### Post by chili555 on 2013-03-30
> yes. It finally scanned and found my router.Awesome! There are two options. If this is a stay-at-home computer and you just need to connect to your home router, I'd fill in /etc/network/interfaces with your details; something like:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid <your_router>
wpa-psk <your_key>

```Then restart the interface to get it to read the file and use the details:```
sudo ifdown wlan0 && sudo ifup wlan0
```Be sure you connected and got an IP address:```
ifconfig
```And that you can reach ye olde interwebs:```
ping -c3 www.google.com
```Of course, substitute your details here.

On the other hand, if you take your computer to the coffee shop, library, etc., I'd probably re-install Network Manager.

EDIT: As always, if you need specific guidance, please feel free to ask us. Wild Man and I will be very happy to help.

---

### Post by Volleumel on 2013-03-30
Thank you very much. You guys are a great help. I think I will try to reinstall the network manager. I'll let you know when I need further assistance. Probably very soon...

---

### Post by Volleumel on 2013-03-30
I haven't had time to do anything in the meantime, but when I came back and started my machine again the wlan scan wasn't possible anymore:

sudo iwlist wlan0 scan

resulted in:
wlan0 Interface doesn't support scanning : Network is down


In order to come back to the point where I can detect my router I had to repeat the command: 

sudo ifconfig wlan0 up


Is there a way to to keep it up even after rebooting the system?
I guess it doesn't make sense to reinstall network manager at this stage. Right?

---

### Post by wildmanne39 on 2013-03-30
That is because network manager is not insatlled, run this command with a wired connection:
```
sudo apt-get install --reinstall network-manager network-manager-gnome
```
Thanks

---

### Post by chili555 on 2013-03-30
In fact, a big part of the purpose of NM is to bring up and manage your interface.

---

### Post by Volleumel on 2013-03-31
> **Wild Man said:**
> That is because network manager is not insatlled, run this command with a wired connection:
```
sudo apt-get install --reinstall network-manager network-manager-gnome
```
Thanks

My router is a pure Wifi device, no wired connection. I think I have to download the necessary packages with my other machine and install it.  I browsed the network manager packages at packages.ubuntu.com but I'm not sure which are the right ones.

---

### Post by Volleumel on 2013-03-31
Now I'm completely pissed off. Every f... little step results in a sound internet search. I think I found the deb file I need but the Ubuntu Software Center doesn't allow me to click install. Such a mess! What's the command to get it run. Otherwise please let me know how to deinstall the mess!

---

### Post by chili555 on 2013-03-31
Assuming the package is on your desktop, then:```
cd Desktop
sudo dpkg -i network*.deb
```

---

### Post by wildmanne39 on 2013-03-31
These are the packages you need.
```
network-manager network-manager-gnome
```
Thanks

---

### Post by Volleumel on 2013-03-31
Sorry, guys. I decided to erase the linux partition. My life is too short to become the slave of an OS. Thank you anyway.

---

### Post by wildmanne39 on 2013-03-31
Good luck!!! if you ever reinstall someone will be here to help.

---

