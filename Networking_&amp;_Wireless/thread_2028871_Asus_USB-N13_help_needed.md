---
title: "Asus USB-N13 help needed"
date: 2012-07-19
forum: Networking &amp; Wireless
---

### Post by cbezerra on 2012-07-19
I tried to follow the direction from the read me file that was extracted. However I cannot get it completely installed. 

here is some basic info:

this is the file I dled from the ASUS site:
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422

lsusb:


Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

iwconfig:


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod:

Module                  Size  Used by
rt2870sta             461811  0 
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
tpm_infineon            7745  0 
snd_hda_codec_analog    58598  1 
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 30784  0 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
radeon                678607  2 
ppdev                   5259  0 
ttm                    49847  1 radeon
drm_kms_helper         29329  1 radeon
parport_pc             25962  1 
tpm_tis                 7488  0 
tpm                    14000  2 tpm_infineon,tpm_tis
tpm_bios                5266  1 tpm
video                  17375  0 
output                  1871  1 video
hp_accel               11144  0 
lis3lv02d               6096  1 hp_accel
input_polldev           2482  1 lis3lv02d
led_class               2864  1 hp_accel
snd                    54244  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ati_agp                 5094  0 
drm                   163779  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
agpgart                31724  3 ttm,ati_agp,drm
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
k8temp                  3152  0 
i2c_piix4               8335  0 
shpchp                 28835  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ahci                   32680  2 
pata_atiixp             3148  0 
tg3                   109324  0 



THANKS for any help!

---

### Post by cbezerra on 2012-07-19
iwconfig:


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr: off   Fragment thr: off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2012-07-19
I'm frankly astonished that you got this far!!! Asus has released the USB-N13 with at least two different chipsets. Let's explore a bit. Please run and post:```
modinfo rt2870sta | grep 17AB
```I picked the '17AB' from your device ID:> ID 0b05:[COLOR="Red"]17ab[/COLOR] ASUSTek Computer, Inc. Also, please post:```
dmesg | grep -i rt2
lsb_release -d
```I actually think the correct driver is rtl8192cu.

---

### Post by cbezerra on 2012-07-19
Lol. Thanks

modinfo rt2870sta | grep 17AB:

grep17ab: command not found

dmesg | grep -i rt2:

There was no response. 

lsb_release -d:

Description: ubuntu 10.04.4 LTS

---

### Post by chili555 on 2012-07-19
There is no colon or other punctuation at the end of any of these commands. Also, make sure there is a space after grep.> modinfo rt2870sta | grep 17AB[COLOR="Red"]**:**[/COLOR]

grep17ab[COLOR="Red"]**:**[/COLOR] command not found


---

### Post by cbezerra on 2012-07-19
Yeah I put the colon there in the post only.

---

### Post by cbezerra on 2012-07-19
Update

modinfo rt2870sta | grep 17AB

No response. Just a new command prompt. 

dmesg | grep -i rt2

There was no response. Same.

lsb_release -d

Description: ubuntu 10.04.4 LTS

---

### Post by chili555 on 2012-07-19
That indicates that your device is not claimed by rt2870sta. Indeed, the rt2870sta module isn't loaded. 

Please check here: [http://ubuntuforums.org/showthread.php?p=12049424](http://ubuntuforums.org/showthread.php?p=12049424)

---

### Post by cbezerra on 2012-07-20
I followed the directions, and did a reboot. Then plugged in the usb adapter. Nothing.

---

### Post by chili555 on 2012-07-20
With the device plugged in, please run and post:```
sudo modprobe rtl8192cu
dmesg | grep 8192
iwconfig
```Thanks.

---

### Post by cbezerra on 2012-07-20
sudo mod probe rtl8192cu

FATAL: Module rtl8192cu not found. 

dmesg | grep 8192 

[ 792.208192] #

lo no wireless extensions. 

eth0 no wireless extensions.

---

### Post by chili555 on 2012-07-20
> FATAL: Module rtl8192cu not found.When you followed the directions to build the driver, were there any errors or warnings? Can you run through the process again and check? Please post them here so we can troubleshoot.

---

### Post by cbezerra on 2012-07-20
sudo modprobe rtl8192cu 

FATAL: Module rtl8192cu not found. 

dmesg | grep 8192 

[ 792.208192] # 

iwconfig 

lo no wireless extensions. 

eth0 no wireless extensions.

---

### Post by chili555 on 2012-07-20
> Can you run through the process again and check? Please post them here so we can troubleshoot.I mean the process to build the driver as linked in post #8. You said you followed all the instructions and we need to know if there were errors or warnings and what they were, if any.

---

### Post by cbezerra on 2012-07-20
Don't recall how to uninstall it I can restart the process.

chris@chris-laptop:~$ sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src
rtl8192cu-3.3.23192/
rtl8192cu-3.3.23192/src/
rtl8192cu-3.3.23192/src/os_dep/
rtl8192cu-3.3.23192/src/include/
rtl8192cu-3.3.23192/src/hal/
rtl8192cu-3.3.23192/src/core/
rtl8192cu-3.3.23192/src/os_dep/linux/
rtl8192cu-3.3.23192/src/include/byteorder/
rtl8192cu-3.3.23192/src/hal/rtl8192d/
rtl8192cu-3.3.23192/src/hal/rtl8192c/
rtl8192cu-3.3.23192/src/core/efuse/
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/
rtl8192cu-3.3.23192/Makefile
rtl8192cu-3.3.23192/dkms.conf
rtl8192cu-3.3.23192/src/wlan0dhcp
rtl8192cu-3.3.23192/src/Makefile
rtl8192cu-3.3.23192/src/make_drv
rtl8192cu-3.3.23192/src/Kconfig
rtl8192cu-3.3.23192/src/ifcfg-wlan0
rtl8192cu-3.3.23192/src/clean
rtl8192cu-3.3.23192/src/autoconf_rtl8192d_usb_linux.h
rtl8192cu-3.3.23192/src/autoconf_rtl8192c_usb_linux.h
rtl8192cu-3.3.23192/src/os_dep/osdep_service.c
rtl8192cu-3.3.23192/src/include/rtw_ioctl.h
rtl8192cu-3.3.23192/src/include/rtw_mp.h
rtl8192cu-3.3.23192/src/include/rtl8192c_sreset.h
rtl8192cu-3.3.23192/src/include/xmit_osdep.h
rtl8192cu-3.3.23192/src/include/if_ether.h
rtl8192cu-3.3.23192/src/include/rtw_led.h
rtl8192cu-3.3.23192/src/include/ip.h
rtl8192cu-3.3.23192/src/include/rtl8192c_hal.h
rtl8192cu-3.3.23192/src/include/basic_types.h
rtl8192cu-3.3.23192/src/include/circ_buf.h
rtl8192cu-3.3.23192/src/include/rtw_br_ext.h
rtl8192cu-3.3.23192/src/include/Hal8192DPhyReg.h
rtl8192cu-3.3.23192/src/include/rtw_io.h
rtl8192cu-3.3.23192/src/include/sdio_hal.h
rtl8192cu-3.3.23192/src/include/rtw_security.h
rtl8192cu-3.3.23192/src/include/autoconf.h
rtl8192cu-3.3.23192/src/include/usb_hal.h
rtl8192cu-3.3.23192/src/include/rtw_rf.h
rtl8192cu-3.3.23192/src/include/rtw_mp_phy_regdef.h
rtl8192cu-3.3.23192/src/include/rtw_iol.h
rtl8192cu-3.3.23192/src/include/sta_info.h
rtl8192cu-3.3.23192/src/include/osdep_intf.h
rtl8192cu-3.3.23192/src/include/rtw_debug.h
rtl8192cu-3.3.23192/src/include/mlme_osdep.h
rtl8192cu-3.3.23192/src/include/rtw_event.h
rtl8192cu-3.3.23192/src/include/rtl8192c_cmd.h
rtl8192cu-3.3.23192/src/include/pci_ops.h
rtl8192cu-3.3.23192/src/include/rtl8192d_rf.h
rtl8192cu-3.3.23192/src/include/rtw_cmd.h
rtl8192cu-3.3.23192/src/include/pci_osintf.h
rtl8192cu-3.3.23192/src/include/h2clbk.h
rtl8192cu-3.3.23192/src/include/rtw_ioctl_set.h
rtl8192cu-3.3.23192/src/include/rtl8192d_cmd.h
rtl8192cu-3.3.23192/src/include/rtw_version.h
rtl8192cu-3.3.23192/src/include/rtl8192d_xmit.h
rtl8192cu-3.3.23192/src/include/rtw_byteorder.h
rtl8192cu-3.3.23192/src/include/drv_types_xp.h
rtl8192cu-3.3.23192/src/include/rtw_eeprom.h
rtl8192cu-3.3.23192/src/include/rtw_ioctl_query.h
rtl8192cu-3.3.23192/src/include/osdep_service.h
rtl8192cu-3.3.23192/src/include/usb_vendor_req.h
rtl8192cu-3.3.23192/src/include/drv_conf.h
rtl8192cu-3.3.23192/src/include/pci_hal.h
rtl8192cu-3.3.23192/src/include/rtw_p2p.h
rtl8192cu-3.3.23192/src/include/Hal8192CEHWImg.h
rtl8192cu-3.3.23192/src/include/sdio_osintf.h
rtl8192cu-3.3.23192/src/include/Hal8192DETestHWImg.h
rtl8192cu-3.3.23192/src/include/sdio_ops_xp.h
rtl8192cu-3.3.23192/src/include/rtw_mp_ioctl.h
rtl8192cu-3.3.23192/src/include/rtl8192d_led.h
rtl8192cu-3.3.23192/src/include/Hal8192CPhyCfg.h
rtl8192cu-3.3.23192/src/include/drv_types_ce.h
rtl8192cu-3.3.23192/src/include/ieee80211_ext.h
rtl8192cu-3.3.23192/src/include/Hal8192DEHWImg.h
rtl8192cu-3.3.23192/src/include/drv_types.h
rtl8192cu-3.3.23192/src/include/hal_init.h
rtl8192cu-3.3.23192/src/include/rtw_mlme.h
rtl8192cu-3.3.23192/src/include/rtl8192c_spec.h
rtl8192cu-3.3.23192/src/include/Hal8192DUHWImg.h
rtl8192cu-3.3.23192/src/include/sdio_ops_linux.h
rtl8192cu-3.3.23192/src/include/rtw_ioctl_rtl.h
rtl8192cu-3.3.23192/src/include/mp_custom_oid.h
rtl8192cu-3.3.23192/src/include/ethernet.h
rtl8192cu-3.3.23192/src/include/rtw_ht.h
rtl8192cu-3.3.23192/src/include/usb_ops.h
rtl8192cu-3.3.23192/src/include/Hal8192DUTestHWImg.h
rtl8192cu-3.3.23192/src/include/sdio_ops_ce.h
rtl8192cu-3.3.23192/src/include/Hal8192CUHWImg.h
rtl8192cu-3.3.23192/src/include/rtw_efuse.h
rtl8192cu-3.3.23192/src/include/drv_types_linux.h
rtl8192cu-3.3.23192/src/include/recv_osdep.h
rtl8192cu-3.3.23192/src/include/ieee80211.h
rtl8192cu-3.3.23192/src/include/sdio_ops.h
rtl8192cu-3.3.23192/src/include/osdep_ce_service.h
rtl8192cu-3.3.23192/src/include/rtl8192d_spec.h
rtl8192cu-3.3.23192/src/include/rtl8192c_xmit.h
rtl8192cu-3.3.23192/src/include/rtw_pwrctrl.h
rtl8192cu-3.3.23192/src/include/rtw_qos.h
rtl8192cu-3.3.23192/src/include/rtl8192c_event.h
rtl8192cu-3.3.23192/src/include/rtw_xmit.h
rtl8192cu-3.3.23192/src/include/rtl8192d_dm.h
rtl8192cu-3.3.23192/src/include/usb_osintf.h
rtl8192cu-3.3.23192/src/include/nic_spec.h
rtl8192cu-3.3.23192/src/include/rtl8192c_recv.h
rtl8192cu-3.3.23192/src/include/rtl8192c_rf.h
rtl8192cu-3.3.23192/src/include/rtl8192c_dm.h
rtl8192cu-3.3.23192/src/include/rtl8192d_hal.h
rtl8192cu-3.3.23192/src/include/Hal8192DPhyCfg.h
rtl8192cu-3.3.23192/src/include/Hal8192CPhyReg.h
rtl8192cu-3.3.23192/src/include/farray.h
rtl8192cu-3.3.23192/src/include/rtl8192d_recv.h
rtl8192cu-3.3.23192/src/include/rtl8192c_led.h
rtl8192cu-3.3.23192/src/include/wifi.h
rtl8192cu-3.3.23192/src/include/rtw_mlme_ext.h
rtl8192cu-3.3.23192/src/include/rtw_recv.h
rtl8192cu-3.3.23192/src/include/cmd_osdep.h
rtl8192cu-3.3.23192/src/include/wlan_bssdef.h
rtl8192cu-3.3.23192/src/hal/hal_init.c
rtl8192cu-3.3.23192/src/core/rtw_iol.c
rtl8192cu-3.3.23192/src/core/rtw_ioctl_set.c
rtl8192cu-3.3.23192/src/core/rtw_mp_ioctl.c
rtl8192cu-3.3.23192/src/core/rtw_ioctl_rtl.c
rtl8192cu-3.3.23192/src/core/rtw_io.c
rtl8192cu-3.3.23192/src/core/rtw_mlme_ext.c
rtl8192cu-3.3.23192/src/core/rtw_wlan_util.c
rtl8192cu-3.3.23192/src/core/rtw_pwrctrl.c
rtl8192cu-3.3.23192/src/core/rtw_rf.c
rtl8192cu-3.3.23192/src/core/rtw_sta_mgt.c
rtl8192cu-3.3.23192/src/core/rtw_mp.c
rtl8192cu-3.3.23192/src/core/rtw_mlme.c
rtl8192cu-3.3.23192/src/core/rtw_cmd.c
rtl8192cu-3.3.23192/src/core/rtw_security.c
rtl8192cu-3.3.23192/src/core/rtw_ieee80211.c
rtl8192cu-3.3.23192/src/core/rtw_p2p.c
rtl8192cu-3.3.23192/src/core/rtw_debug.c
rtl8192cu-3.3.23192/src/core/rtw_eeprom.c
rtl8192cu-3.3.23192/src/core/rtw_br_ext.c
rtl8192cu-3.3.23192/src/core/rtw_recv.c
rtl8192cu-3.3.23192/src/core/rtw_ioctl_query.c
rtl8192cu-3.3.23192/src/core/rtw_xmit.c
rtl8192cu-3.3.23192/src/os_dep/linux/xmit_linux.c
rtl8192cu-3.3.23192/src/os_dep/linux/sdio_intf.c
rtl8192cu-3.3.23192/src/os_dep/linux/pci_intf.c
rtl8192cu-3.3.23192/src/os_dep/linux/mlme_linux.c
rtl8192cu-3.3.23192/src/os_dep/linux/usb_intf.c
rtl8192cu-3.3.23192/src/os_dep/linux/os_intfs.c
rtl8192cu-3.3.23192/src/os_dep/linux/recv_linux.c
rtl8192cu-3.3.23192/src/os_dep/linux/ioctl_linux.c
rtl8192cu-3.3.23192/src/include/byteorder/generic.h
rtl8192cu-3.3.23192/src/include/byteorder/little_endian.h
rtl8192cu-3.3.23192/src/include/byteorder/big_endian.h
rtl8192cu-3.3.23192/src/include/byteorder/swabb.h
rtl8192cu-3.3.23192/src/include/byteorder/swab.h
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_hal_init.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_rf6052.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_dm.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_mp.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_phycfg.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_cmd.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_rxdesc.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_hal_init.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_sreset.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_rf6052.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_mp.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_dm.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_phycfg.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_cmd.c
rtl8192cu-3.3.23192/src/core/efuse/rtw_efuse.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/usb_ops_linux.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/rtl8192du_led.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/Hal8192DUHWImg.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/rtl8192du_xmit.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/usb_halinit.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/rtl8192du_recv.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/Hal8192DUTestHWImg.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_xp.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_linux.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_ce.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_halinit.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_led.c
chris@chris-laptop:~$ sudo dkms build -m rtl8192cu -v 3.3.23192

Error! This module/version has already been built on: 2.6.32-41-generic
Directory: /var/lib/dkms/rtl8192cu/3.3.23192/2.6.32-41-generic/i686
already exists.  Use the dkms remove function before trying to build again.

---

### Post by chili555 on 2012-07-21
> chris@chris-laptop:~$ sudo dkms build -m rtl8192cu -v 3.3.23192

Error! This module/version has already been built on: 2.6.32-41-generic
Directory: /var/lib/dkms/rtl8192cu/3.3.23192/2.6.32-41-generic/i686
already exists. Use the dkms remove function before trying to build again.Please try:```
sudo dkms remove rtl8192cu -v 3.3.23192
sudo dkms add -m rtl8192cu -v 3.3.23192
sudo dkms build -m rtl8192cu -v 3.3.23192
sudo dkms install -m rtl8192cu -v 3.3.23192
```Please note any errors or warnings and post them here.

---

### Post by cbezerra on 2012-07-21
Didn't see anything out of the ordinary. Rebooted and plugged in the usb adapter. Nothing. 

chris@chris-laptop:~$ sudo dkms remove -m rtl8192cu -v 3.3.23192 --all

-------- Uninstall Beginning --------
Module:  rtl8192cu
Version: 3.3.23192
Kernel:  2.6.32-41-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

8192cu.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-41-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall Completed.

------------------------------
Deleting module version: 3.3.23192
completely from the DKMS tree.
------------------------------
Done.
chris@chris-laptop:~$ sudo dkms add -m rtl8192cu -v 3.3.23192

Creating symlink /var/lib/dkms/rtl8192cu/3.3.23192/source ->
                 /usr/src/rtl8192cu-3.3.23192

DKMS: add Completed.
chris@chris-laptop:~$ sudo dkms build -m rtl8192cu -v 3.3.23192

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C src/ all................
cleaning build area....

DKMS: build Completed.
chris@chris-laptop:~$ sudo dkms install -m rtl8192cu -v 3.3.23192

8192cu.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-41-generic/updates/dkms/

depmod....

DKMS: install Completed.

---

### Post by chili555 on 2012-07-21
Please post:```
sudo modprobe 8192cu
dmesg | grep 8192
iwconfig
```Thanks.

---

### Post by cbezerra on 2012-07-21
Here. Thank you.

---

### Post by chili555 on 2012-07-22
> [sudo] password for chris: 
chris@chris-laptop:~$ sudo modprobe [COLOR="Red"]rtl8192cu[/COLOR]
FATAL: Module rtl8192cu not found.
chris@chris-laptop:~$ sudo modprobe [COLOR="Red"]8192[/COLOR]
FATAL: Module 8192 not found.Neither are what I asked for.> sudo modprobe [COLOR="Red"]8192cu[/COLOR]
dmesg | grep 8192
iwconfigI wonder why you have a wireless interface, aliased RT3070STA, when you, as far as I can see, have no compatible device.

Using the same method you used to post the text document above, please create and post a new one for me:```
sudo modprobe 8192cu > cbez.txt
dmesg >> cbez.txt
ls /etc/modprobe.d >> cbez.txt
cat /etc/udev/rules.d/network_drivers.rules >> cbez.txt
lspci -nn | grep 0280 >> cbez.txt
lsusb >> cbez.txt
```Now find the cbez.txt file in your user directory and post it here.

---

### Post by cbezerra on 2012-07-25
sudo modprobe 8192cu
chris@chris-laptop:~$ dmesg | grep 8192
[  758.681924] device disconnected
[  758.819218] device disconnected
[19089.325236] usbcore: registered new interface driver rtl8192cu
chris@chris-laptop:~$ ls /etc/modprobe.d
alsa-base.conf          blacklist.conf           blacklist-framebuffer.conf  blacklist-oss.conf       libpisock9.conf
blacklist-ath_pci.conf  blacklist-firewire.conf  blacklist-modem.conf        blacklist-watchdog.conf  network_drivers.conf
chris@chris-laptop:~$ cat /etc/udev/rules.d/network_drivers.rules
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="17ab", RUN+="/sbin/modprobe -qba rt2870sta"
chris@chris-laptop:~$ lspci -nn | grep 0280
chris@chris-laptop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 0951:168a Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by cbezerra on 2012-07-25
[  758.895220] device disconnected
[  758.896222] device disconnected
[  758.897221] device disconnected
[  758.898219] device disconnected
[  758.899218] device disconnected
[  758.900224] device disconnected
[  758.901223] device disconnected
[  758.902221] device disconnected
[  758.902225] device disconnected
[  758.902229] device disconnected
[  758.902232] device disconnected
[  758.903231] device disconnected
[  758.903235] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903240] Retry count exhausted or device removed!!!
[  758.903244] device disconnected
[  758.903248] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903253] Retry count exhausted or device removed!!!
[  758.903257] device disconnected
[  758.903261] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903266] Retry count exhausted or device removed!!!
[  758.903270] device disconnected
[  758.903274] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903279] Retry count exhausted or device removed!!!
[  758.903283] device disconnected
[  758.903288] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903292] Retry count exhausted or device removed!!!
[  758.903296] device disconnected
[  758.903301] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903305] Retry count exhausted or device removed!!!
[  758.903310] device disconnected
[  758.903314] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903318] Retry count exhausted or device removed!!!
[  758.903323] device disconnected
[  758.903327] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903331] Retry count exhausted or device removed!!!
[  758.903336] device disconnected
[  758.903340] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903345] Retry count exhausted or device removed!!!
[  758.903349] device disconnected
[  758.903353] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903358] Retry count exhausted or device removed!!!
[  758.903362] device disconnected
[  758.903366] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903371] Retry count exhausted or device removed!!!
[  758.903375] device disconnected
[  758.903379] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903384] Retry count exhausted or device removed!!!
[  758.903388] device disconnected
[  758.903392] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903397] Retry count exhausted or device removed!!!
[  758.903401] device disconnected
[  758.903405] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903410] Retry count exhausted or device removed!!!
[  758.903414] device disconnected
[  758.903418] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903423] Retry count exhausted or device removed!!!
[  758.903427] device disconnected
[  758.903432] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903436] Retry count exhausted or device removed!!!
[  758.903440] device disconnected
[  758.903445] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903449] Retry count exhausted or device removed!!!
[  758.903454] device disconnected
[  758.903458] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903462] Retry count exhausted or device removed!!!
[  758.903467] device disconnected
[  758.903471] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903475] Retry count exhausted or device removed!!!
[  758.903480] device disconnected
[  758.903484] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=0!
[  758.903488] Retry count exhausted or device removed!!!
[  758.903493] ERROR!!! NICInitializeAdapter failed, Status[=0x00000001]
[  758.908470] ---> RTMPFreeTxRxRingMemory
[  758.908479] #
[  758.913547] <--- ReleaseAdapter
[  758.913553] !!! RTxx70 Initialized fail !!!
[  758.925360] #
[  758.942229] #
[  758.959240] #
[  758.964219] RTUSB_VendorRequest failed(-71),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x101c
[  758.964227] RTUSBReadBBPRegister(BBP_CSR_CFG_1):retry count=1!
[  758.964233] Retry count exhausted or device removed!!!
[  758.964238] device disconnected
[  758.964242] RTUSBWriteBBPRegister(BBP_CSR_CFG):retry count=0!
[  758.964247] Retry count exhausted or device removed!!!
[  758.964252] device disconnected
[  758.964255] device disconnected
[  758.964259] device disconnected
[  758.964263] device disconnected
[  758.964267] device disconnected
[  758.964270] device disconnected
[  758.964274] device disconnected
[  758.964278] device disconnected
[  758.964282] device disconnected
[  758.964285] device disconnected
[  758.964293] device disconnected
[  758.964297] device disconnected
[  758.964300] device disconnected
[  758.964306] device disconnected
[  758.964310] device disconnected
[ 7019.848461] usb 2-1: USB disconnect, address 2
[ 7027.584070] usb 2-1: new low speed USB device using ohci_hcd and address 3
[ 7027.754377] usb 2-1: configuration #1 chosen from 1 choice
[ 7027.762038] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input10
[ 7027.762609] generic-usb 0003:045E:0084.0002: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:13.0-1/input0
[19047.168084] usb 1-8: new high speed USB device using ehci_hcd and address 7
[19047.305341] usb 1-8: configuration #1 chosen from 1 choice
[19047.305693] scsi7 : SCSI emulation for USB Mass Storage devices
[19047.306030] usb-storage: device found at 7
[19047.306035] usb-storage: waiting for device to settle before scanning
[19052.304393] usb-storage: device scan complete
[19052.381447] scsi 7:0:0:0: Direct-Access     Kingston DT Micro         PMAP PQ: 0 ANSI: 0 CCS
[19052.382892] sd 7:0:0:0: Attached scsi generic sg2 type 0
[19053.556076] sd 7:0:0:0: [sdb] 15356160 512-byte logical blocks: (7.86 GB/7.32 GiB)
[19053.556670] sd 7:0:0:0: [sdb] Write Protect is off
[19053.556679] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00
[19053.556686] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[19053.560440] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[19053.560459]  sdb: sdb1
[19053.584428] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[19053.584445] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[19089.325184] 
[19089.325186] rtw driver version=v3.3.2_3192.20120103
[19089.325236] usbcore: registered new interface driver rtl8192cu
[19248.762005] usb 1-8: USB disconnect, address 7
[19464.164074] usb 1-8: new high speed USB device using ehci_hcd and address 8
[19464.301257] usb 1-8: configuration #1 chosen from 1 choice
[19464.301583] scsi8 : SCSI emulation for USB Mass Storage devices
[19464.301915] usb-storage: device found at 8
[19464.301920] usb-storage: waiting for device to settle before scanning
[19469.300406] usb-storage: device scan complete
[19469.377460] scsi 8:0:0:0: Direct-Access     Kingston DT Micro         PMAP PQ: 0 ANSI: 0 CCS
[19469.378896] sd 8:0:0:0: Attached scsi generic sg2 type 0
[19470.551844] sd 8:0:0:0: [sdb] 15356160 512-byte logical blocks: (7.86 GB/7.32 GiB)
[19470.552461] sd 8:0:0:0: [sdb] Write Protect is off
[19470.552470] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[19470.552478] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[19470.557198] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[19470.557212]  sdb: sdb1
[19470.582073] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[19470.582089] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[38242.966217] tg3 0000:10:00.0: PME# enabled
[38242.966256] tg3 0000:10:00.0: wake-up capability enabled by ACPI
[38243.357038] PM: Syncing filesystems ... done.
[38243.358788] PM: Preparing system for mem sleep
[38243.358791] Freezing user space processes ... (elapsed 0.00 seconds) done.
[38243.359725] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[38243.359818] PM: Entering mem sleep
[38243.359830] Suspending console(s) (use no_console_suspend to debug)
[38243.420078] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[38243.446620] sd 2:0:0:0: [sda] Stopping disk
[38244.057958] PM: suspend of drv:sd dev:2:0:0:0 complete after 637.880 msecs
[38248.098872] PM: suspend of drv:psmouse dev:serio4 complete after 4040.829 msecs
[38248.200054] PM: suspend of drv:atkbd dev:serio0 complete after 101.160 msecs
[38248.202553] ACPI handle has no context!
[38248.248042] tpm_tis 00:03: Operation Timed out
[38248.249050] parport_pc 00:02: disabled
[38248.253283] ACPI handle has no context!
[38250.405129] radeon 0000:01:05.0: PCI INT B disabled
[38250.420053] PM: suspend of drv:radeon dev:0000:01:05.0 complete after 2151.892 msecs
[38250.628114] HDA Intel 0000:00:14.2: PCI INT A disabled
[38250.648840] HDA Intel 0000:00:14.2: power state changed by ACPI to D3
[38250.648849] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 228.770 msecs
[38250.648992] ehci_hcd 0000:00:13.5: PCI INT D disabled
[38250.649003] ohci_hcd 0000:00:13.4: PCI INT C disabled
[38250.649014] ohci_hcd 0000:00:13.3: PCI INT B disabled
[38250.649024] ohci_hcd 0000:00:13.2: PCI INT C disabled
[38250.649035] ohci_hcd 0000:00:13.1: PCI INT B disabled
[38250.649046] ohci_hcd 0000:00:13.0: PCI INT A disabled
[38250.664222] ahci 0000:00:12.0: PCI INT A disabled
[38250.666639] PM: suspend of devices complete after 7306.497 msecs
[38250.666642] PM: suspend devices took 7.308 seconds
[38250.680391] PM: late suspend of devices complete after 13.746 msecs
[38250.680481] ACPI: Preparing to enter system sleep state S3
[38250.680834] Disabling non-boot CPUs ...
[38250.680854] CPU0 attaching NULL sched-domain.
[38250.680859] CPU1 attaching NULL sched-domain.
[38250.728041] CPU0 attaching NULL sched-domain.
[38250.729143] Breaking affinity for irq 12
[38250.729165] Breaking affinity for irq 23
[38250.832033] CPU 1 is now offline
[38250.832035] SMP alternatives: switching to UP code
[38250.836121] Extended CMOS year: 2000
[38250.836121] Back to C!
[38250.836121] Extended CMOS year: 2000
[38250.836285] Enabling non-boot CPUs ...
[38250.836523] SMP alternatives: switching to SMP code
[38250.839931] Booting processor 1 APIC 0x1 ip 0x6000
[38250.836066] Initializing CPU#1
[38250.836066] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[38250.836066] CPU: L2 Cache: 512K (64 bytes/line)
[38250.836066] CPU: Physical Processor ID: 0
[38250.836066] CPU: Processor Core ID: 1
[38250.836066] Switch to broadcast mode on CPU1
[38250.928075] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-64 stepping 01
[38250.928155] CPU0 attaching NULL sched-domain.
[38250.956044] CPU0 attaching sched-domain:
[38250.956047]  domain 0: span 0-1 level MC
[38250.956050]   groups: 0 1
[38250.956054] CPU1 attaching sched-domain:
[38250.956056]  domain 0: span 0-1 level MC
[38250.956058]   groups: 1 0
[38250.956360] CPU1 is up
[38250.956667] ACPI: Waking up from system sleep state S3
[38251.168966] pci 0000:00:01.0: restoring config space at offset 0x7 (was 0x2204141, writing 0x22204141)
[38251.168987] pcieport 0000:00:04.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[38251.168991] pcieport 0000:00:04.0: restoring config space at offset 0x8 (was 0x0, writing 0xd000d000)
[38251.168994] pcieport 0000:00:04.0: restoring config space at offset 0x7 (was 0x101, writing 0x1f1)
[38251.168999] pcieport 0000:00:04.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[38251.169003] pcieport 0000:00:04.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[38251.169034] pcieport 0000:00:05.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[38251.169037] pcieport 0000:00:05.0: restoring config space at offset 0x8 (was 0x0, writing 0xcff0cc00)
[38251.169041] pcieport 0000:00:05.0: restoring config space at offset 0x7 (was 0x101, writing 0x3121)
[38251.169046] pcieport 0000:00:05.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[38251.169050] pcieport 0000:00:05.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[38251.169072] pcieport 0000:00:06.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[38251.169075] pcieport 0000:00:06.0: restoring config space at offset 0x8 (was 0x0, writing 0xc800c800)
[38251.169079] pcieport 0000:00:06.0: restoring config space at offset 0x7 (was 0x101, writing 0x1f1)
[38251.169083] pcieport 0000:00:06.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[38251.169087] pcieport 0000:00:06.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[38251.169110] ahci 0000:00:12.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[38251.169130] ahci 0000:00:12.0: restoring config space at offset 0x3 (was 0x0, writing 0x4010)
[38251.169135] ahci 0000:00:12.0: restoring config space at offset 0x2 (was 0x1018f00, writing 0x1060100)
[38251.169154] ahci 0000:00:12.0: set SATA to AHCI mode
[38251.169403] HDA Intel 0000:00:14.2: restoring config space at offset 0xf (was 0x10a, writing 0xa)
[38251.169527] radeon 0000:01:05.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
[38251.169595] tg3 0000:10:00.0: restoring config space at offset 0xf (was 0x159, writing 0x10a)
[38251.169603] tg3 0000:10:00.0: restoring config space at offset 0xc (was 0x0, writing 0xf8e0000)
[38251.169615] tg3 0000:10:00.0: restoring config space at offset 0x5 (was 0x80e02811, writing 0x0)
[38251.169620] tg3 0000:10:00.0: restoring config space at offset 0x4 (was 0x39510004, writing 0xd0000004)
[38251.169625] tg3 0000:10:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[38251.169631] tg3 0000:10:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[38251.169671] yenta_cardbus 0000:02:04.0: restoring config space at offset 0xf (was 0x7000100, writing 0x580010a)
[38251.169677] yenta_cardbus 0000:02:04.0: restoring config space at offset 0xe (was 0x0, writing 0x14fc)
[38251.169682] yenta_cardbus 0000:02:04.0: restoring config space at offset 0xd (was 0x0, writing 0x1400)
[38251.169689] yenta_cardbus 0000:02:04.0: restoring config space at offset 0xc (was 0x0, writing 0x10fc)
[38251.169694] yenta_cardbus 0000:02:04.0: restoring config space at offset 0xb (was 0x0, writing 0x1000)
[38251.169700] yenta_cardbus 0000:02:04.0: restoring config space at offset 0xa (was 0x0, writing 0x8bfff000)
[38251.169706] yenta_cardbus 0000:02:04.0: restoring config space at offset 0x9 (was 0x0, writing 0x88000000)
[38251.169712] yenta_cardbus 0000:02:04.0: restoring config space at offset 0x8 (was 0x0, writing 0x83fff000)
[38251.169718] yenta_cardbus 0000:02:04.0: restoring config space at offset 0x7 (was 0x0, writing 0x80000000)
[38251.169724] yenta_cardbus 0000:02:04.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0060302)
[38251.169731] yenta_cardbus 0000:02:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xd0100000)
[38251.169737] yenta_cardbus 0000:02:04.0: restoring config space at offset 0x3 (was 0x820000, writing 0x82a800)
[38251.169745] yenta_cardbus 0000:02:04.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100007)
[38251.184075] ohci1394 0000:02:04.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[38251.184082] ohci1394 0000:02:04.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[38251.184633] PM: early resume of devices complete after 15.887 msecs
[38251.249900] ahci 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[38251.249962] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[38251.308018] usb usb2: root hub lost power or was reset
[38251.308035] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[38251.368014] usb usb3: root hub lost power or was reset
[38251.368030] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[38251.428013] usb usb4: root hub lost power or was reset
[38251.428029] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[38251.488021] usb usb5: root hub lost power or was reset
[38251.488033] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[38251.548021] usb usb6: root hub lost power or was reset
[38251.548034] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[38251.548042] usb usb1: root hub lost power or was reset
[38251.554193] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[38251.554231] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[38251.554263] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[38251.554295] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[38251.554302] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[38251.554355] radeon 0000:01:05.0: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[38251.554566] [drm] GPU reset succeed (RBBM_STATUS=0x10000140)
[38251.568066] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[38251.568940] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[38251.569980] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[38251.569984] ata3.00: configured for UDMA/133
[38251.637297] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[38251.637304] [drm] radeon: cp idle (0x10000C03)
[38251.637318] [drm] radeon: ring at 0x0000000080000000
[38251.637336] [drm] ring test succeeded in 1 usecs
[38251.637346] [drm] ib test succeeded in 0 usecs
[38251.712532] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[38251.712536] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[38251.728488] ata1.00: configured for MWDMA2
[38252.465705] PM: resume of drv:radeon dev:0000:01:05.0 complete after 911.350 msecs
[38252.604042] PM: resume of drv:yenta_cardbus dev:0000:02:04.0 complete after 138.317 msecs
[38252.662062] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d0101000-d01017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[38252.670805] parport_pc 00:02: activated
[38252.860037] tpm_tis 00:03: Operation Timed out
[38252.860042] PM: resume of drv:tpm_tis dev:00:03 complete after 189.229 msecs
[38253.216042] PM: resume of drv:usb dev:usb1 complete after 355.367 msecs
[38253.504043] PM: resume of drv:usb dev:usb2 complete after 287.980 msecs
[38253.792041] PM: resume of drv:usb dev:usb4 complete after 287.965 msecs
[38253.793711] sd 2:0:0:0: [sda] Starting disk
[38253.948040] usb 4-1: reset full speed USB device using ohci_hcd and address 2
[38254.111086] PM: resume of drv:usb dev:4-1 complete after 298.044 msecs
[38254.392042] usb 2-1: reset low speed USB device using ohci_hcd and address 3
[38254.706079] PM: resume of drv:usb dev:2-1 complete after 594.671 msecs
[38254.816042] usb 1-8: reset high speed USB device using ehci_hcd and address 8
[38254.949780] PM: resume of drv:usb dev:1-8 complete after 243.670 msecs
[38254.949834] PM: resume of devices complete after 3765.171 msecs
[38254.950007] PM: resume devices took 3.764 seconds
[38254.950035] PM: Finishing wakeup.
[38254.950036] Restarting tasks ... 
[38254.950090] usb 1-3: USB disconnect, address 4
[38254.950178] rtusb_disconnect: unregister usbnet usb-0000:00:13.5-3
[38254.950182] rtusb_disconnect: unregister_netdev(), dev->name=wlan0!
[38254.965113]  RTUSB disconnect successfully
[38254.975881] done.
[38255.375019] tg3 0000:10:00.0: wake-up capability disabled by ACPI
[38255.375074] tg3 0000:10:00.0: PME# disabled
[38255.375172] tg3 0000:10:00.0: irq 27 for MSI/MSI-X
[38255.407791] ADDRCONF(NETDEV_UP): eth0: link is not ready
[38255.680062] usb 3-2: new full speed USB device using ohci_hcd and address 2
[38255.860247] usb 3-2: configuration #1 chosen from 1 choice
[38255.926940] usbcore: registered new interface driver usbserial
[38255.927399] USB Serial support registered for generic
[38255.927789] usbcore: registered new interface driver usbserial_generic
[38255.927792] usbserial: USB Serial Driver core
[38255.969635] USB Serial support registered for Sierra USB modem
[38255.969680] sierra 3-2:1.0: Sierra USB modem converter detected
[38255.970612] usb 3-2: Sierra USB modem converter now attached to ttyUSB0
[38255.970738] usb 3-2: Sierra USB modem converter now attached to ttyUSB1
[38255.970863] usb 3-2: Sierra USB modem converter now attached to ttyUSB2
[38255.970888] usbcore: registered new interface driver sierra
[38255.970892] sierra: v.1.3.8:USB Driver for Sierra Wireless USB modems
[38264.077091] usb 3-2: USB disconnect, address 2
[38264.079210] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
[38264.079534] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
[38264.079721] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
[38264.079754] sierra 3-2:1.0: device disconnected
[38404.784075] usb 2-2: new full speed USB device using ohci_hcd and address 4
[38404.966380] usb 2-2: configuration #1 chosen from 1 choice
[38405.163148] Bluetooth: Core ver 2.15
[38405.163316] NET: Registered protocol family 31
[38405.163321] Bluetooth: HCI device and connection manager initialized
[38405.163330] Bluetooth: HCI socket layer initialized
[38405.189882] Bluetooth: Generic Bluetooth USB driver ver 0.6
[38405.203013] usbcore: registered new interface driver btusb
[38405.316520] Bluetooth: L2CAP ver 2.14
[38405.316529] Bluetooth: L2CAP socket layer initialized
[38405.392509] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[38405.392518] Bluetooth: BNEP filters: protocol multicast
[38405.430903] Bridge firewalling registered
[38405.465007] Bluetooth: SCO (Voice Link) ver 0.6
[38405.465020] Bluetooth: SCO socket layer initialized
[38405.565588] Bluetooth: RFCOMM TTY layer initialized
[38405.565603] Bluetooth: RFCOMM socket layer initialized
[38405.565609] Bluetooth: RFCOMM ver 1.11
[38442.559977] usb 2-2: USB disconnect, address 4
[38442.560107] btusb_bulk_complete: hci0 urb f2b77880 failed to resubmit (19)
[38442.561088] btusb_bulk_complete: hci0 urb f2b77380 failed to resubmit (19)
[38442.561106] btusb_intr_complete: hci0 urb f2b77480 failed to resubmit (19)
[38442.561747] btusb_send_frame: hci0 urb efe44380 submission failed
[38463.118509] usb 1-8: USB disconnect, address 8
[39397.613856] tg3 0000:10:00.0: PME# enabled
[39397.613874] tg3 0000:10:00.0: wake-up capability enabled by ACPI
[39397.893935] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
[39397.893939] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[39397.893943] PM: Basic memory bitmaps created
[39397.893945] PM: Syncing filesystems ... done.
[39397.895824] Freezing user space processes ... (elapsed 0.00 seconds) done.
[39397.896782] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[39397.896907] PM: Preallocating image memory... done (allocated 351124 pages)
[39398.457150] PM: Allocated 1404496 kbytes in 0.56 seconds (2508.02 MB/s)
[39398.457153] Suspending console(s) (use no_console_suspend to debug)
[39398.458601] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[39398.459528] ACPI handle has no context!
[39398.504038] tpm_tis 00:03: Operation Timed out
[39398.505041] parport_pc 00:02: disabled
[39398.510270] ACPI handle has no context!
[39408.608048] PM: freeze of drv:radeon dev:0000:01:05.0 complete after 10083.883 msecs
[39408.712129] HDA Intel 0000:00:14.2: PCI INT A disabled
[39408.732583] HDA Intel 0000:00:14.2: power state changed by ACPI to D3
[39408.732595] PM: freeze of drv:HDA Intel dev:0000:00:14.2 complete after 124.520 msecs
[39408.748223] ahci 0000:00:12.0: PCI INT A disabled
[39408.750386] PM: freeze of devices complete after 10292.917 msecs
[39408.751537] PM: late freeze of devices complete after 1.145 msecs
[39408.751616] ACPI: Preparing to enter system sleep state S4
[39408.751788] PM: Saving platform NVS memory
[39408.754765] Disabling non-boot CPUs ...
[39408.754780] CPU0 attaching NULL sched-domain.
[39408.754784] CPU1 attaching NULL sched-domain.
[39408.801041] CPU0 attaching NULL sched-domain.
[39408.802121] Breaking affinity for irq 9
[39408.802149] Breaking affinity for irq 23
[39408.904034] CPU 1 is now offline
[39408.904036] SMP alternatives: switching to UP code
[39408.908329] Extended CMOS year: 2000
[39408.908416] PM: Creating hibernation image: 
[39408.912015] PM: Need to copy 77893 pages
[39408.912015] PM: Normal pages needed: 34143 + 1024, available pages: 193049
[39408.912015] PM: Restoring platform NVS memory
[39408.912015] Extended CMOS year: 2000
[39408.912015] Enabling non-boot CPUs ...
[39408.912015] SMP alternatives: switching to SMP code
[39408.912319] Booting processor 1 APIC 0x1 ip 0x6000
[39408.912015] Initializing CPU#1
[39408.912015] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[39408.912015] CPU: L2 Cache: 512K (64 bytes/line)
[39408.912015] CPU: Physical Processor ID: 0
[39408.912015] CPU: Processor Core ID: 1
[39408.912015] Switch to broadcast mode on CPU1
[39409.000075] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-64 stepping 01
[39409.000154] CPU0 attaching NULL sched-domain.
[39409.028044] CPU0 attaching sched-domain:
[39409.028047]  domain 0: span 0-1 level MC
[39409.028050]   groups: 0 1
[39409.028054] CPU1 attaching sched-domain:
[39409.028056]  domain 0: span 0-1 level MC
[39409.028058]   groups: 1 0
[39409.028354] CPU1 is up
[39409.028726] ACPI: Waking up from system sleep state S4
[39409.236965] pci 0000:00:01.0: restoring config space at offset 0x7 (was 0x22204141, writing 0x2204141)
[39409.237080] ahci 0000:00:12.0: restoring config space at offset 0x1 (was 0x2300003, writing 0x2300007)
[39409.237335] HDA Intel 0000:00:14.2: restoring config space at offset 0xf (was 0x10a, writing 0xa)
[39409.237357] HDA Intel 0000:00:14.2: restoring config space at offset 0x1 (was 0x4100006, writing 0x4100002)
[39409.237411] pci 0000:00:14.4: restoring config space at offset 0x6 (was 0x40030200, writing 0x40060200)
[39409.276040] __ratelimit: 18 callbacks suppressed
[39409.276042] tg3 0000:10:00.0: Refused to change power state, currently in D3
[39409.276048] tg3 0000:10:00.0: restoring config space at offset 0xf (was 0xffffffff, writing 0x10a)
[39409.276052] tg3 0000:10:00.0: restoring config space at offset 0xe (was 0xffffffff, writing 0x0)
[39409.276055] tg3 0000:10:00.0: restoring config space at offset 0xd (was 0xffffffff, writing 0x48)
[39409.276059] tg3 0000:10:00.0: restoring config space at offset 0xc (was 0xffffffff, writing 0xfbe0000)
[39409.276063] tg3 0000:10:00.0: restoring config space at offset 0xb (was 0xffffffff, writing 0x30c2103c)
[39409.276067] tg3 0000:10:00.0: restoring config space at offset 0xa (was 0xffffffff, writing 0x0)
[39409.276071] tg3 0000:10:00.0: restoring config space at offset 0x9 (was 0xffffffff, writing 0x0)
[39409.276074] tg3 0000:10:00.0: restoring config space at offset 0x8 (was 0xffffffff, writing 0x0)
[39409.276078] tg3 0000:10:00.0: restoring config space at offset 0x7 (was 0xffffffff, writing 0x0)
[39409.276082] tg3 0000:10:00.0: restoring config space at offset 0x6 (was 0xffffffff, writing 0x0)
[39409.276085] tg3 0000:10:00.0: restoring config space at offset 0x5 (was 0xffffffff, writing 0x0)
[39409.276089] tg3 0000:10:00.0: restoring config space at offset 0x4 (was 0xffffffff, writing 0xd0000004)
[39409.276093] tg3 0000:10:00.0: restoring config space at offset 0x3 (was 0xffffffff, writing 0x10)
[39409.276097] tg3 0000:10:00.0: restoring config space at offset 0x2 (was 0xffffffff, writing 0x2000002)
[39409.276101] tg3 0000:10:00.0: restoring config space at offset 0x1 (was 0xffffffff, writing 0x100006)
[39409.276105] tg3 0000:10:00.0: restoring config space at offset 0x0 (was 0xffffffff, writing 0x169314e4)
[39409.276130] yenta_cardbus 0000:02:04.0: restoring config space at offset 0xf (was 0x780010a, writing 0x580010a)
[39409.276154] yenta_cardbus 0000:02:04.0: restoring config space at offset 0x3 (was 0x824000, writing 0x82a800)
[39409.292073] ohci1394 0000:02:04.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[39409.292081] ohci1394 0000:02:04.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[39409.292588] PM: early restore of devices complete after 55.836 msecs
[39409.382742] ahci 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[39409.440019] usb usb2: root hub lost power or was reset
[39409.500013] usb usb3: root hub lost power or was reset
[39409.560013] usb usb4: root hub lost power or was reset
[39409.620020] usb usb5: root hub lost power or was reset
[39409.680021] usb usb6: root hub lost power or was reset
[39409.680035] usb usb1: root hub lost power or was reset
[39409.686010] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[39409.686047] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[39409.686080] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[39409.686111] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[39409.686118] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[39409.686375] [drm] GPU reset succeed (RBBM_STATUS=0x10000140)
[39409.700071] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[39409.701434] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[39409.703466] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[39409.703469] ata3.00: configured for UDMA/133
[39410.181305] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[39410.181312] [drm] radeon: cp idle (0x10000C03)
[39410.181331] [drm] radeon: ring at 0x0000000080000000
[39410.181349] [drm] ring test succeeded in 1 usecs
[39410.181362] [drm] ib test succeeded in 0 usecs
[39410.593067] PM: restore of drv:radeon dev:0000:01:05.0 complete after 906.896 msecs
[39410.732058] PM: restore of drv:yenta_cardbus dev:0000:02:04.0 complete after 138.967 msecs
[39410.789089] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d0101000-d01017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[39410.797510] parport_pc 00:02: activated
[39410.988055] tpm_tis 00:03: Operation Timed out
[39410.988059] PM: restore of drv:tpm_tis dev:00:03 complete after 190.540 msecs
[39411.241064] PM: restore of drv:usb dev:usb1 complete after 252.373 msecs
[39411.529040] PM: restore of drv:usb dev:usb2 complete after 287.954 msecs
[39411.817039] PM: restore of drv:usb dev:usb4 complete after 287.966 msecs
[39411.818719] sd 2:0:0:0: [sda] Starting disk
[39412.012046] usb 4-1: reset full speed USB device using ohci_hcd and address 2
[39412.175085] PM: restore of drv:usb dev:4-1 complete after 295.992 msecs
[39412.456046] usb 2-1: reset low speed USB device using ohci_hcd and address 3
[39412.770080] PM: restore of drv:usb dev:2-1 complete after 594.689 msecs
[39412.770110] PM: restore of devices complete after 3450.201 msecs
[39412.770341] PM: Image restored successfully.
[39412.770343] Restarting tasks ... done.
[39412.787525] PM: Basic memory bitmaps freed
[39414.833776] tg3 0000:10:00.0: wake-up capability disabled by ACPI
[39414.833793] tg3 0000:10:00.0: PME# disabled
[39414.837289] ata1.00: qc timeout (cmd 0xa1)
[39414.837306] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[39414.837314] ata1.00: revalidation failed (errno=-5)
[39414.849060] tg3 0000:10:00.0: Refused to change power state, currently in D3
[39416.110325] tg3: eth0: No firmware running.
[39427.045376] ADDRCONF(NETDEV_UP): eth0: link is not ready
[39437.044085] ata1.00: qc timeout (cmd 0xa1)
[39437.044106] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[39437.044115] ata1.00: revalidation failed (errno=-5)
[39461.492072] usb 1-8: new high speed USB device using ehci_hcd and address 11
[39461.629233] usb 1-8: configuration #1 chosen from 1 choice
[39461.629595] scsi9 : SCSI emulation for USB Mass Storage devices
[39461.629948] usb-storage: device found at 11
[39461.629953] usb-storage: waiting for device to settle before scanning
[39466.628391] usb-storage: device scan complete
[39466.705454] scsi 9:0:0:0: Direct-Access     Kingston DT Micro         PMAP PQ: 0 ANSI: 0 CCS
[39466.706870] sd 9:0:0:0: Attached scsi generic sg2 type 0
[39467.200078] ata1.00: qc timeout (cmd 0xa1)
[39467.200098] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[39467.200107] ata1.00: revalidation failed (errno=-5)
[39467.200117] ata1.00: disabled
[39467.200186] ata1: soft resetting link
[39467.356125] ata1: EH complete
[39467.877832] sd 9:0:0:0: [sdb] 15356160 512-byte logical blocks: (7.86 GB/7.32 GiB)
[39467.878427] sd 9:0:0:0: [sdb] Write Protect is off
[39467.878436] sd 9:0:0:0: [sdb] Mode Sense: 23 00 00 00
[39467.878443] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[39467.883057] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[39467.883071]  sdb: sdb1
[39467.907933] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[39467.907949] sd 9:0:0:0: [sdb] Attached SCSI removable disk
chris@chris-laptop:~$

---

### Post by cbezerra on 2012-07-25
The files wouldn't attach so I had to cut and paste. dmesg would always output like you see there. Cutting off the top. That's why I did dmesg grep with the first post.

---

### Post by chili555 on 2012-07-25
Please do:```
sudo su
echo 8192cu >> /etc/modules
rm /etc/modprobe.d/network_drivers.conf
rm /etc/udev/rules.d/network_drivers.rules
exit
```Reboot and then run and post:```
iwconfig
```Thanks.

---

### Post by cbezerra on 2012-07-25
Nice that worked. Blue light comes on it finds the network. I just can't get the wifi password to go through. My only options are wpa and wpa2. I need wep.

---

### Post by cbezerra on 2012-07-25
SOLVED!!


wlan0     IEEE 802.11bg  ESSID:"MWGardens"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 94:44:52:5E:F3:86   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=69/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Thank you, Chili55!
Your help and time were much appreciated.

---

### Post by chili555 on 2012-07-25
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

Have fun!

---

