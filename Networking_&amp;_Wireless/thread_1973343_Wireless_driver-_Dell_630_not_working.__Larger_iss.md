---
title: "Wireless driver- Dell 630 not working.  Larger issue?"
date: 2012-05-04
forum: Networking &amp; Wireless
---

### Post by ryghlles on 2012-05-04
Hi all, I am an Ubuntu newbie and I'm having problems getting the wireless to work.  I tried a number of different things so far, but it looks like there may be a larger issue.  I cannot get certain modules to install, but I haven't been able to determine what the problem is or the best course of action.

Any help is appreciated.

Results of a few tests I ran: let me know if you need more info!

ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net
[INDENT]09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
[/INDENT]
ubuntu@ubuntu:~$ lsmod
[INDENT]Module                  Size  Used by
dm_crypt               22528  0 
pata_pcmcia            16938  1 
joydev                 17393  0 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39791  1 pata_pcmcia
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
dell_wmi               12601  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
dell_laptop            13671  0 
sparse_keymap          13658  1 dell_wmi
rfcomm                 38139  0 
soundcore              14635  1 snd
bnep                   17830  2 
dm_multipath           22710  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
dcdbas                 14098  1 dell_laptop
parport_pc             32114  0 
psmouse                72919  0 
serio_raw              13027  0 
mac_hid                13077  0 
bluetooth             158438  10 rfcomm,bnep
arc4                   12473  2 
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
ext2                   67987  1 
squashfs               36095  1 
overlayfs              27511  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   141369  0 
i915                  414603  3 
wmi                    18744  1 dell_wmi
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
ssb                    50691  1 b43
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
usb_storage            39646  1

[/INDENT]ubuntu@ubuntu:~$ rfkill list
[INDENT]0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[/INDENT]ubuntu@ubuntu:~$ iwconfig
[INDENT]lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

[/INDENT]ubuntu@ubuntu:~$ sudo iwlist scan
[INDENT]lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.
[/INDENT]ubuntu@ubuntu:~$ iwlist chan
[INDENT]lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
eth0      no frequency information.
[/INDENT]

---

### Post by ryghlles on 2012-05-04
I believe the issue may have to do with a few packages that are having problems updating.  When I run Synaptic Package Manager and try to install the firmware-b43-lpphy-installer package I get the following error:

[INDENT]Selecting previously unselected package b43-fwcutter.
(Reading database ... 177816 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_015-9_i386.deb) ...
Selecting previously unselected package firmware-b43-lpphy-installer.
Unpacking firmware-b43-lpphy-installer (from .../firmware-b43-lpphy-installer_1%3a015-9_all.deb) ...
Processing triggers for man-db ...
Setting up linux-image-3.2.0-24-generic-pae (3.2.0-24.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-24-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-3.2.0-24-generic-pae (3.2.0-24.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic-pae /boot/vmlinuz-3.2.0-24-generic-pae
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-24-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-24-generic-pae; however:
  Package linux-image-3.2.0-24-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.24.26); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-24-generic-pae
 linux-image-generic-pae
 linux-generic-pae

[/INDENT]

---

### Post by chili555 on 2012-05-04
What kernel messages are there about this?```
dmesg | grep b43
```If it says you need firmware, open a terminal and do:```
sudo apt-get install b43-fwcutter firmware-b43-installer
```If it's not firmware, post back and tell us what it says.

Reboot and enjoy your new wireless.

---

### Post by VanCardboardbox on 2012-05-04
D630 user here. Experienced the same thing. Fixed it by disabling the driver that installs by default, then:

```
sudo apt-get install firmware-b43-installer
```

---

### Post by ryghlles on 2012-05-04
Thanks you so much!  I followed chili555's instructions and I am on the wireless connection right now!

---

### Post by chili555 on 2012-05-04
> **ryghlles said:**
> I believe the issue may have to do with a few packages that are having problems updating.  When I run Synaptic Package Manager and try to install the firmware-b43-lpphy-installer package I get the following error:

[INDENT]Selecting previously unselected package b43-fwcutter.
(Reading database ... 177816 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_015-9_i386.deb) ...
Selecting previously unselected package firmware-b43-lpphy-installer.
Unpacking firmware-b43-lpphy-installer (from .../firmware-b43-lpphy-installer_1%3a015-9_all.deb) ...
Processing triggers for man-db ...
<snip>Yikes!! You might try to fix broken packages with:```
sudo apt-get install -f
```

---

