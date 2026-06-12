---
title: "Wireless USB stick is causing sleep/shutdown issues"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by SeanDS on 2012-05-24
Hello, I've tried searching for similar issues and haven't come across any that seem relevant.

I'm using Ubuntu 11.10 with Gnome 3.

I recently started using an old Wireless-G USB stick (Linksys WUSB54GC) on my desktop Ubuntu installation after I moved the computer and was unable to use an ethernet cable. Since I started using the USB stick I have had issues with Ubuntu going to sleep and shutting down. When I try to make it sleep, it doesn't actually switch off but instead remains on the lock screen page (the one you would see if you were to 'wake' the computer from a successful sleep). When I try to make it shut down, it hangs on the 'shutting down...' box and eventually I have to switch the computer off manually.

I tried troubleshooting by changing BIOS settings such as ACPI, PnP, etc. to no avail. Eventually I looked at the system logs more closely and discovered a message in /var/log/pm-suspend.log saying:

> Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

This made me think it could have been the USB stick so I unplugged it and tried suspending again. It didn't work that time, but I suspected it might be an issue with the kernel not unloading the module or something so I rebooted without the USB stick plugged in and it was then able to successfully sleep and shut down.

Clearly the issue is related to the USB stick. The kernel, or some other piece of software, cannot seem to put the wlan interface provided by the USB stick to sleep, which is causing the system to remain awake.

Does anyone have any idea of how to fix this issue so as to allow me to keep using the USB stick? Perhaps a hotfix might be to edit some sort of shutdown sequence file to include a command to forcefully close the wlan interface? I would need some help in doing this as I have no idea how to go about doing such a thing.

Thanks a lot.

---

### Post by praseodym on 2012-05-24
Hi,
please show

```
lsusb
lsmod
```
The module of the stick (plus the "common suspects" from the output of
```
lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' 
```
need to be unloaded before and reloaded after S/H). For this put these modules into this file:
```
sudo touch /etc/pm/config.d/00sleep_module
sudo chmod +x /etc/pm/config.d/00sleep_module
```
Open the file via
```
gksudo gedit /etc/pm/config.d/00sleep_module
```
and add the modules like this:
```
SUSPEND_MODULES="$SUSPEND_MODULES ehci-hcd uhci-hcd usbcore forcedeth" 
```
(example). Save, close the editor, and try it again

---

### Post by SeanDS on 2012-05-24
Hi there, thanks for your answer.

Here is the output of lsusb:

> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 007 Device 002: ID 1532:0007 Razer USA, Ltd DeathAdder Mouse
Bus 001 Device 003: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]


and the output of lsmod:

> Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
twofish_generic        16635  0 
twofish_x86_64         12567  0 
twofish_common         20919  2 twofish_generic,twofish_x86_64
serpent                29125  0 
xts                    12756  0 
gf128mul               14951  1 xts
dm_crypt               23199  0 
arc4                   12529  2 
rt73usb                31735  0 
rt2x00usb              20830  1 rt73usb
rt2x00lib              54461  2 rt73usb,rt2x00usb
mac80211              462046  2 rt2x00usb,rt2x00lib
cfg80211              199630  2 rt2x00lib,mac80211
bnep                   18436  2 
rfcomm                 47946  4 
bluetooth             166150  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  4 vboxpci,vboxnetadp,vboxnetflt
nfsd                  322392  11 
lockd                  86161  1 nfsd
nfs_acl                12883  1 nfsd
auth_rpcgss            53320  1 nfsd
kvm_intel              61643  0 
sunrpc                240940  17 nfsd,lockd,nfs_acl,auth_rpcgss
kvm                   383910  1 kvm_intel
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
vesafb                 13844  1 
snd_hda_codec_analog    93522  1 
nvidia              11713772  64 
snd_virtuoso           41045  2 
snd_oxygen_lib         41445  1 snd_virtuoso
snd_mpu401_uart        14169  1 snd_oxygen_lib
snd_hda_intel          33390  2 
snd_hda_codec         104968  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_oxygen_lib,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
asus_atk0110           18078  0 
snd                    68266  20 snd_hda_codec_analog,snd_virtuoso,snd_oxygen_lib,snd_mpu401_uart,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
x38_edac               13092  0 
edac_core              53746  2 x38_edac
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57900  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
uas                    18027  0 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  2 rt73usb,firewire_core
sky2                   58799  0 
ahci                   26002  5 
libahci                26861  1 ahci
floppy                 70365  0 

I'm not sure what you mean by the rest of your post - are they instructions to fix the sleep issue? Will this also fix the shutdown issue?

---

### Post by praseodym on 2012-05-25
I dont know about the shutdown issue, **rt73usb** is the wireless driver.

This would be the output:

grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' test.txt 
```
rt73usb 31735 0
rt2x00usb 20830 1 rt73usb
rt2x00lib 54461 2 rt73usb,rt2x00usb
mac80211 462046 2 rt2x00usb,rt2x00lib
cfg80211 199630 2 rt2x00lib,mac80211
usb_storage 57900 0
usbhid 47198 0
hid 95463 1 usbhid
uas 18027 0
firewire_ohci 40722 0
firewire_core 63626 1 firewire_ohci
crc_itu_t 12707 2 rt73usb,firewire_core
ahci 26002 5
libahci 26861 1 ahci
```
Put all these modules into that file as described.

---

### Post by SeanDS on 2012-05-31
> **praseodym said:**
> I dont know about the shutdown issue, **rt73usb** is the wireless driver.

This would be the output:

grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' test.txt 
```
rt73usb 31735 0
rt2x00usb 20830 1 rt73usb
rt2x00lib 54461 2 rt73usb,rt2x00usb
mac80211 462046 2 rt2x00usb,rt2x00lib
cfg80211 199630 2 rt2x00lib,mac80211
usb_storage 57900 0
usbhid 47198 0
hid 95463 1 usbhid
uas 18027 0
firewire_ohci 40722 0
firewire_core 63626 1 firewire_ohci
crc_itu_t 12707 2 rt73usb,firewire_core
ahci 26002 5
libahci 26861 1 ahci
```Put all these modules into that file as described.
Thanks for the help. I have installed Linux Mint and the issue does not exist anymore, so I guess the issue was with an Ubuntu-specific module. Perhaps LightDM?

Thanks for all the help you provided regardless.

---

