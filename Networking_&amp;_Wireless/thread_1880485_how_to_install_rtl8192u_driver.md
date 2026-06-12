---
title: "how to install rtl8192u driver"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by inhinieri on 2011-11-13
Hey guys! I have a rtl8192u device from Realtek that is a wireless usb adapter. I have tray to install the drivers in Backtrack 5 with vmware  but nothing. I have read the others post and I looked for a solution on Debian and I found a page on the Debian Wiki that contains the instructions and the driver:

[http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x)

Unfortunately, I'm not experienced enough with Ubuntu or Debian to follow the instructions correctly (I tried these instructions on a Debian install and a Ubuntu install 
Please can any one help me to install rtl8192u device

---

### Post by praseodym on 2011-11-13
Hi,

which device is that? Please show:

```
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by inhinieri on 2011-11-13
root@bt:~# lsusb Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 001 Device 003: ID 0bda:8192 Realtek Semiconductor Corp. RTL8192U 802.11n Wireless Adapter Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub root@bt:~# lsmod Module                  Size  Used by nls_utf8                1069  1  isofs                  32015  1  snd_ens1371            18023  0  gameport                7778  1 snd_ens1371 snd_ac97_codec        101869  1 snd_ens1371 ac97_bus                 982  1 snd_ac97_codec snd_pcm_oss            36427  0  snd_mixer_oss          13581  1 snd_pcm_oss snd_pcm                68662  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss snd_seq_dummy           1358  0  snd_seq_oss            26216  0  snd_seq_midi            4460  0  snd_rawmidi            18745  2 snd_ens1371,snd_seq_midi snd_seq_midi_event      5720  2 snd_seq_oss,snd_seq_midi snd_seq                45875  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event snd_timer              17803  2 snd_pcm,snd_seq snd_seq_device          5281  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq r8192u_usb            251963  0  snd                    50697  10 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device ppdev                   5096  0  soundcore               6048  1 snd snd_page_alloc          6801  1 snd_pcm joydev                  8649  0  parport_pc             26143  1  vmw_balloon             3566  0  psmouse                52655  0  serio_raw               3744  0  i2c_piix4               7907  0  mac_hid                 3029  0  shpchp                 24986  0  lp                      7373  0  parport                29468  3 ppdev,parport_pc,lp usbhid                 35443  0  hid                    69090  1 usbhid mptspi                 14781  2  intel_agp               9614  1  mptscsih               29911  1 mptspi intel_gtt              13296  1 intel_agp pcnet32                29779  0  floppy                 54673  0  mii                     4091  1 pcnet32 mptbase                86277  2 mptspi,mptscsih agpgart                27414  2 intel_agp,intel_gtt root@bt:~# iwconfig lo        no wireless extensions.  eth0      no wireless extensions.  wlan0     802.11b/g/n  Mode:Monitor  Frequency=2.457 GHz  Bit Rate=1 Mb/s              Retry min limit:7   RTS thr:off   Fragment thr:off           Power Management:off           Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  root@bt:~# rfkill list Can't open RFKILL control device: No such file or directory

---

### Post by inhinieri on 2011-11-13
the device is (ENCORE ELECTRONICS 802.11N WIRELESS ADAPTER)   ENUWI-NX2.     Windows7 know like rtl8192u

---

### Post by praseodym on 2011-11-14
Install a new driver via cable connection:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://media.cdn.ubuntu-de.org/forum/attachments/2858455/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn.tar.gz
tar xvf rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn.tar.gz
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn
make
sudo make install 
echo "blacklist r8192u_usb" | sudo tee -a /etc/modprobe.d/blacklist.conf  
```
Reboot and check:

```
iwconfig
uname -a
sudo iwlist scan
lsmod
dmesg | grep r8
```

---

### Post by inhinieri on 2011-11-14
hi again my device don't work i have use the Code and the outputs are: 


root@bt:~# sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdmraid1.0.0.rc16 python-pyicu libdebian-installer4 cryptsetup
  libecryptfs0 reiserfsprogs rdate bogl-bterm ecryptfs-utils libdebconfclient0
  dmraid
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/7,258kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 245870 files and directories currently installed.)
Preparing to replace build-essential 11.4build1 (using .../build-essential_11.4build1_i386.deb) ...
Unpacking replacement build-essential ...
Preparing to replace linux-headers-2.6.39.4 2.6.39.4-10.00.Custom (using .../linux-headers-2.6.39.4_2.6.39.4-10.00.Custom_i386.deb) ...
Unpacking replacement linux-headers-2.6.39.4 ...
Setting up build-essential (11.4build1) ...
Setting up linux-headers-2.6.39.4 (2.6.39.4-10.00.Custom) ...






root@bt:~# wget [http://media.cdn.ubuntu-de.org/forum/attachments/2858455/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2858455/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn.tar.gz)
--2011-11-14 13:00:35--  [http://media.cdn.ubuntu-de.org/forum/attachments/2858455/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2858455/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn.tar.gz)
Resolving media.cdn.ubuntu-de.org... 213.95.41.13
Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 436218 (426K) [application/octet-stream]
Saving to: `rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn.tar.gz.1'

100%[======================================>] 436,218      105K/s   in 7.9s    

2011-11-14 13:00:43 (53.9 KB/s) - `rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn.tar.gz.1' saved [436218/436218]






root@bt:~# tar xvf rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn.tar.gz
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/xmit/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/sta_mgt/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/rf/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/recv/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/pwrctrl/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/os_intf/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/os_dep/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/mp/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/mlme/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/led/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/ioctl/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/io/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/hal/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/efuse/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/eeprom/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/debug/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/crypto/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/cmd/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/os_intf/linux/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/os_dep/linux/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/byteorder/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/hal/rtl8712/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/sdio_reg/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/modules.order
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/wpa1.conf
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/wlan0dhcp
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/runwpa
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/Makefile
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/ifcfg-wlan0
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/config
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/clean
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/autoconf_rtl8712_usb_linux.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/xmit/rtl871x_xmit.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/xmit/rtl8712_xmit.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/sta_mgt/rtl871x_sta_mgt.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/rf/rtl871x_rf.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/rf/rtl8712_rf.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/recv/rtl871x_recv.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/recv/rtl8712_recv.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/pwrctrl/rtl871x_pwrctrl.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/os_intf/osdep_service.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/mp/rtl871x_mp_ioctl.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/mp/rtl871x_mp.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/mlme/rtl871x_mlme.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/mlme/ieee80211.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/led/rtl8712_led.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/ioctl/rtl871x_ioctl_set.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/ioctl/rtl871x_ioctl_rtl.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/ioctl/rtl871x_ioctl_query.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/ioctl/rtl871x_ioctl_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/io/rtl871x_io.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/io/rtl8712_io.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/xmit_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/wlan_bssdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/wifi.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/version.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/usb_vendor_req.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/usb_osintf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/usb_ops.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/usb_hal.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/sta_info.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/sdio_osintf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/sdio_ops_xp.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/sdio_ops_linux.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/sdio_ops_ce.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/sdio_ops.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/sdio_hal.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_xmit.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_wlan_sme.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_wlan_mlme.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_security.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_rf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_recv.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_qos.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_pwrctrl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_mp_phy_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_mp_ioctl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_mp.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_mlme_ext.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_mlme.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_led.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_ioctl_set.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_ioctl_rtl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_ioctl_query.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_ioctl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_io.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_ht.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_event.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_eeprom.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_debug.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_cmd.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl871x_byteorder.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_xmit.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_rf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_recv.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_hal.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_event.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_efuse.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_cmd.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/recv_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/osdep_service.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/osdep_intf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/osdep_ce_service.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/nic_spec.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/mp_custom_oid.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/mlme_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/ip.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/if_ether.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/ieee80211_ext.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/ieee80211.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/hal_init.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/h2clbk.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/farray.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/ethernet.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/drv_types_xp.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/drv_types_linux.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/drv_types_ce.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/drv_types.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/drv_conf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/cmd_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/circ_buf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/basic_types.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/autoconf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/efuse/rtl8712_efuse.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/eeprom/rtl871x_eeprom.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/debug/rtl871x_debug.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/crypto/rtl871x_security.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/cmd/rtl871x_cmd.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/cmd/rtl8712_cmd.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/os_intf/linux/usb_intf.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/os_intf/linux/os_intfs.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/os_dep/linux/xmit_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/os_dep/linux/recv_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/os_dep/linux/mlme_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/os_dep/linux/io_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/os_dep/linux/cmd_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/byteorder/swabb.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/byteorder/swab.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/byteorder/little_endian.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/byteorder/generic.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/byteorder/big_endian.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/hal/rtl8712/usb_ops_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/hal/rtl8712/usb_ops.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/hal/rtl8712/usb_halinit.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/hal/rtl8712/hal_init.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/sdio_reg/rtl8712_sdio_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/sdio_reg/rtl8712_sdio_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/vssver.scc
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_wmac_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_wmac_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_timectrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_timectrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_syscfg_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_syscfg_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_security_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_security_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_ratectrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_ratectrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_powersave_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_powersave_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_offload_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_offload_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_macsetting_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_macsetting_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_interrupt_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_interrupt_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_gp_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_gp_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_fifoctrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_fifoctrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_edcasetting_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_edcasetting_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_debugctrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_debugctrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_cmdctrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn/include/rtl8712_spec/ioreg_def/rtl8712_cmdctrl_bitdef.h






root@bt:~# cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn
root@bt:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn#



root@bt:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn# make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.39.4/build M=/root/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn  modules
make: *** /lib/modules/2.6.39.4/build: No such file or directory.  Stop.
make: *** [modules] Error 2
root@bt:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn# 






root@bt:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn# sudo make install 
Makefile:11: /config: No such file or directory
make: *** No rule to make target `/config'.  Stop.
root@bt:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn#



root@bt:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn# echo "blacklist r8192u_usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist r8192u_usb
root@bt:~/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111_802IIn#

---

### Post by inhinieri on 2011-11-14
after i rebut





root@bt:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@bt:~# uname -a
Linux bt 2.6.39.4 #1 SMP Thu Aug 18 13:38:02 NZST 2011 i686 GNU/Linux
root@bt:~# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

root@bt:~# lsmod
Module                  Size  Used by
dm_crypt               14720  0 
snd_ens1371            18023  0 
gameport                7778  1 snd_ens1371
snd_ac97_codec        101869  1 snd_ens1371
ac97_bus                 982  1 snd_ac97_codec
snd_pcm_oss            36427  0 
snd_mixer_oss          13581  1 snd_pcm_oss
snd_pcm                68662  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1358  0 
snd_seq_oss            26216  0 
snd_seq_midi            4460  0 
snd_rawmidi            18745  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      5720  2 snd_seq_oss,snd_seq_midi
snd_seq                45875  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              17803  2 snd_pcm,snd_seq
snd_seq_device          5281  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vmw_balloon             3566  0 
ppdev                   5096  0 
psmouse                52655  0 
parport_pc             26143  1 
joydev                  8649  0 
snd                    50697  10 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               3744  0 
soundcore               6048  1 snd
snd_page_alloc          6801  1 snd_pcm
mac_hid                 3029  0 
shpchp                 24986  0 
i2c_piix4               7907  0 
lp                      7373  0 
parport                29468  3 ppdev,parport_pc,lp
usbhid                 35443  0 
hid                    69090  1 usbhid
mptspi                 14781  2 
mptscsih               29911  1 mptspi
intel_agp               9614  1 
pcnet32                29779  0 
intel_gtt              13296  1 intel_agp
floppy                 54673  0 
mii                     4091  1 pcnet32
mptbase                86277  2 mptspi,mptscsih
agpgart                27414  2 intel_agp,intel_gtt
root@bt:~# dmesg | grep r8
root@bt:~#

---

### Post by praseodym on 2011-11-14
Ok, my fault, its Debian, right? Take the module off the blacklist (all as "root")

```
gedit /etc/modprobe.d/blacklist.conf
```
and install the firmware according to here:
[http://wiki.debian.org/rtl819x#r8192u_usb](http://wiki.debian.org/rtl819x#r8192u_usb)
```
gedit /etc/apt/sources.list
```
add the line
```
deb http://ftp.us.debian.org/debian wheezy main contrib non-free
```
save close and:
```
aptitude update
aptitude install firmware-realtek wireless-tools unzip && exit
wget ftp://ftp.dlink.com/Wireless/dwa130_revC/Drivers/dwa130_revC_drivers_linux_006.zip
unzip dwa130_revC_drivers_linux_006.zip
su
mkdir -p /usr/local/lib/firmware/RTL8192U
cp rtl8192u_linux_2.6.0006.1031.2008/firmware/RTL8192U/* /usr/local/lib/firmware/RTL8192U
exit
```
Reboot.

---

### Post by inhinieri on 2011-11-14
when i put 


root@bt:~# deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) wheezy main contrib non-free 
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main) 
deb: command not found   is these ok

---

### Post by inhinieri on 2011-11-14
is these ok?

---

### Post by praseodym on 2011-11-14
Open the _file_ as root via:

```
gedit /etc/apt/sources.list
```
and add the line:
```
deb http://ftp.us.debian.org/debian wheezy main contrib non-free 
```
its not a terminal command

---

### Post by inhinieri on 2011-11-15
I have try and again not work!!!!!!!!!:confused:

---

### Post by praseodym on 2011-11-15
Did you execute all the other commands, too?

---

### Post by inhinieri on 2011-11-16
not working

---

### Post by inhinieri on 2011-11-16
Yes i have execute all the other commands and the output are



root@bt:~# aptitude update
Get:1 [http://32.repository.backtrack-linux.org](http://32.repository.backtrack-linux.org) revolution Release.gpg [197B]
Get:2 [http://all.repository.backtrack-linux.org](http://all.repository.backtrack-linux.org) revolution Release.gpg [197B]
Ign [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/main Translation-en_US
Ign [http://32.repository.backtrack-linux.org/](http://32.repository.backtrack-linux.org/) revolution/main Translation-en_US
Get:3 [http://source.repository.backtrack-linux.org](http://source.repository.backtrack-linux.org) revolution Release.gpg [197B]
Ign [http://source.repository.backtrack-linux.org/](http://source.repository.backtrack-linux.org/) revolution/main Translation-en_US
Ign [http://32.repository.backtrack-linux.org/](http://32.repository.backtrack-linux.org/) revolution/microverse Translation-en_US
Ign [http://32.repository.backtrack-linux.org/](http://32.repository.backtrack-linux.org/) revolution/non-free Translation-en_US
Ign [http://32.repository.backtrack-linux.org/](http://32.repository.backtrack-linux.org/) revolution/testing Translation-en_US
Ign [http://source.repository.backtrack-linux.org/](http://source.repository.backtrack-linux.org/) revolution/microverse Translation-en_US
Ign [http://source.repository.backtrack-linux.org/](http://source.repository.backtrack-linux.org/) revolution/non-free Translation-en_US
Ign [http://source.repository.backtrack-linux.org/](http://source.repository.backtrack-linux.org/) revolution/testing Translation-en_US
Ign [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/microverse Translation-en_US
Ign [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/non-free Translation-en_US
Ign [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/testing Translation-en_US
Get:4 [http://all.repository.backtrack-linux.org](http://all.repository.backtrack-linux.org) revolution Release [13.5kB]
Get:5 [http://32.repository.backtrack-linux.org](http://32.repository.backtrack-linux.org) revolution Release [5,041B]
Get:6 [http://source.repository.backtrack-linux.org](http://source.repository.backtrack-linux.org) revolution Release [13.5kB]  
Hit [http://32.repository.backtrack-linux.org](http://32.repository.backtrack-linux.org) revolution/main Packages           
Hit [http://source.repository.backtrack-linux.org](http://source.repository.backtrack-linux.org) revolution/main Packages
Hit [http://32.repository.backtrack-linux.org](http://32.repository.backtrack-linux.org) revolution/microverse Packages
Hit [http://32.repository.backtrack-linux.org](http://32.repository.backtrack-linux.org) revolution/non-free Packages
Get:7 [http://32.repository.backtrack-linux.org](http://32.repository.backtrack-linux.org) revolution/testing Packages [39.8kB]
Hit [http://source.repository.backtrack-linux.org](http://source.repository.backtrack-linux.org) revolution/microverse Packages
Hit [http://source.repository.backtrack-linux.org](http://source.repository.backtrack-linux.org) revolution/non-free Packages
Hit [http://source.repository.backtrack-linux.org](http://source.repository.backtrack-linux.org) revolution/testing Packages
Hit [http://all.repository.backtrack-linux.org](http://all.repository.backtrack-linux.org) revolution/main Packages     
Hit [http://all.repository.backtrack-linux.org](http://all.repository.backtrack-linux.org) revolution/microverse Packages
Hit [http://all.repository.backtrack-linux.org](http://all.repository.backtrack-linux.org) revolution/non-free Packages
Hit [http://all.repository.backtrack-linux.org](http://all.repository.backtrack-linux.org) revolution/testing Packages
Fetched 72.4kB in 1s (48.3kB/s)
Reading package lists... Done

Current status: 23 updates [+1].
root@bt:~# aptitude install firmware-realtek wireless-tools unzip && exit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Couldn't find any package whose name or description matched "firmware-realtek"
Couldn't find any package whose name or description matched "firmware-realtek"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done


root@bt:~# wget [ftp://ftp.dlink.com/Wireless/dwa130_revC/Drivers/dwa130_revC_drivers_linux_006.zip](ftp://ftp.dlink.com/Wireless/dwa130_revC/Drivers/dwa130_revC_drivers_linux_006.zip)
--2011-11-14 22:02:09--  [ftp://ftp.dlink.com/Wireless/dwa130_revC/Drivers/dwa130_revC_drivers_linux_006.zip](ftp://ftp.dlink.com/Wireless/dwa130_revC/Drivers/dwa130_revC_drivers_linux_006.zip)
           => `dwa130_revC_drivers_linux_006.zip.3'
Resolving ftp.dlink.com... 12.130.207.40
Connecting to ftp.dlink.com|12.130.207.40|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /Wireless/dwa130_revC/Drivers ... done.
==> SIZE dwa130_revC_drivers_linux_006.zip ... 1289752
==> PASV ... done.    ==> RETR dwa130_revC_drivers_linux_006.zip ... done.
Length: 1289752 (1.2M) (unauthoritative)

100%[======================================>] 1,289,752   91.7K/s   in 19s     

2011-11-14 22:02:37 (67.0 KB/s) - `dwa130_revC_drivers_linux_006.zip.3' saved [1289752]



root@bt:~# unzip dwa130_revC_drivers_linux_006.zip
Archive:  dwa130_revC_drivers_linux_006.zip
replace rtl8192u_linux_2.6.0006.1031.2008/firmware/RTL8192U/boot.img? [y]es, [n]o, [A]ll, [N]one, [r]ename: A
  inflating: rtl8192u_linux_2.6.0006.1031.2008/firmware/RTL8192U/boot.img  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/firmware/RTL8192U/data.img  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/firmware/RTL8192U/main.img  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/authors  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/changes  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/copying  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/dot11d.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/ieee80211.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/ieee80211_crypt.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/license  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/Makefile  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8180_93cx6.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8180_93cx6.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8180_pm.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8180_pm.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8190_rtl8256.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8190_rtl8256.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8192U.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8192U_core.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8192U_dm.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8192U_dm.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8192U_hw.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8192U_wx.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r8192U_wx.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r819xU_cmdpkt.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r819xU_cmdpkt.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r819xU_firmware.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r819xU_firmware.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r819xU_firmware_img.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r819xU_firmware_img.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r819xU_HTGen.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r819xU_HTType.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r819xU_phy.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r819xU_phy.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/r819xU_phyreg.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/HAL/rtl8192u/tags  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/aes.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/api.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/arc4.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/autoload.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/cipher.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/compress.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/crypto_compat.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/digest.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/dot11d.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/dot11d.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/EndianFree.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_crypt.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_crypt.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_crypt_ccmp.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_crypt_tkip.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_crypt_wep.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_rx.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_softmac.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_softmac_wx.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_tx.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_wx.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/internal.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/kmap_types.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/license  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/Makefile  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/michael_mic.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/proc.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/readme  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/rtl819x_BA.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/rtl819x_BAProc.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/rtl819x_HT.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/rtl819x_HTProc.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/rtl819x_Qos.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/rtl819x_TS.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/rtl819x_TSProc.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/rtl_crypto.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/scatterwalk.c  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/scatterwalk.h  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/ieee80211/tags  
 extracting: rtl8192u_linux_2.6.0006.1031.2008/ifcfg-wlan0  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/Makefile  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/readme.txt  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/release_note  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/wlan0dhcp  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/wlan0down  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/wlan0up  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/wpa1.conf  
  inflating: rtl8192u_linux_2.6.0006.1031.2008/wpa_supplicant-0.5.10.tar.gz  



root@bt:~# su
root@bt:~# mkdir -p /usr/local/lib/firmware/RTL8192U
root@bt:~# cp rtl8192u_linux_2.6.0006.1031.2008/firmware/RTL8192U/* /usr/local/lib/firmware/RTL8192U
root@bt:~# exit
exit


after reboot

root@bt:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@bt:~#

---

### Post by inhinieri on 2011-11-16
is anything else that i can do?

Help me please!!

---

