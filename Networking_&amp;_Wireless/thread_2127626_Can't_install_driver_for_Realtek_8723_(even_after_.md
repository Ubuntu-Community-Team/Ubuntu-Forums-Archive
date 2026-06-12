---
title: "Can't install driver for Realtek 8723 (even after following other threads)"
date: 2013-03-20
forum: Networking &amp; Wireless
---

### Post by dougao06 on 2013-03-20
Hello all,

I just bought a LG N460, which comes with a (07:00.0 Network controller:) Realtek Semiconductor Co., Ltd. Device 8723.

I tried both the solution here: [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)
and tried downloading compat-drivers.

In both cases, what I can make and install the drivers without a problem, but when I try to use modprobe, I get this:

```
pedro@pedro-N460-P-BG55P1:~$ sudo modprobe rtl8723eFATAL: Error inserting rtl8723e (/lib/modules/3.5.0-26-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko): Invalid argument
pedro@pedro-N460-P-BG55P1:~$ dmesg | grep "wlan_module_name"
pedro@pedro-N460-P-BG55P1:~$ dmesg | grep rtl
[   17.527701] rtl8723e: disagrees about version of symbol efuse_read_1byte
[   17.527706] rtl8723e: Unknown symbol efuse_read_1byte (err -22)
[   17.527723] rtl8723e: Unknown symbol rtl_process_phyinfo (err 0)
[   17.527726] rtl8723e: disagrees about version of symbol rtl_cam_reset_all_entry
[   17.527728] rtl8723e: Unknown symbol rtl_cam_reset_all_entry (err -22)
[   17.527733] rtl8723e: disagrees about version of symbol rtl_cam_empty_entry
[   17.527735] rtl8723e: Unknown symbol rtl_cam_empty_entry (err -22)
[   17.527737] rtl8723e: disagrees about version of symbol rtl_cam_del_entry
[   17.527739] rtl8723e: Unknown symbol rtl_cam_del_entry (err -22)
[   17.527744] rtl8723e: disagrees about version of symbol rtl_cam_mark_invalid
[   17.527745] rtl8723e: Unknown symbol rtl_cam_mark_invalid (err -22)
[   17.527754] rtl8723e: disagrees about version of symbol ieee80211_find_sta
[   17.527756] rtl8723e: Unknown symbol ieee80211_find_sta (err -22)
[   17.527760] rtl8723e: disagrees about version of symbol rtl_pci_disconnect
[   17.527762] rtl8723e: Unknown symbol rtl_pci_disconnect (err -22)
[   17.527764] rtl8723e: disagrees about version of symbol rtl_pci_suspend
[   17.527766] rtl8723e: Unknown symbol rtl_pci_suspend (err -22)
[   17.527799] rtl8723e: Unknown symbol rtl_signal_scale_mapping (err 0)
[   17.527847] rtl8723e: disagrees about version of symbol rtl_ps_enable_nic
[   17.527849] rtl8723e: Unknown symbol rtl_ps_enable_nic (err -22)
[   17.527851] rtl8723e: disagrees about version of symbol rtl_pci_resume
[   17.527852] rtl8723e: Unknown symbol rtl_pci_resume (err -22)
[   17.527862] rtl8723e: Unknown symbol rtl_evm_db_to_percentage (err 0)
[   17.527866] rtl8723e: disagrees about version of symbol rtl_cam_add_one_entry
[   17.527867] rtl8723e: Unknown symbol rtl_cam_add_one_entry (err -22)
[   17.527874] rtl8723e: Unknown symbol rtl_query_rxpwrpercentage (err 0)
[   17.527878] rtl8723e: disagrees about version of symbol rtl_efuse_shadow_map_update
[   17.527879] rtl8723e: Unknown symbol rtl_efuse_shadow_map_update (err -22)
[   17.527881] rtl8723e: disagrees about version of symbol rtl_get_tcb_desc
[   17.527882] rtl8723e: Unknown symbol rtl_get_tcb_desc (err -22)
[   17.527884] rtl8723e: disagrees about version of symbol rtl_ps_disable_nic
[   17.527886] rtl8723e: Unknown symbol rtl_ps_disable_nic (err -22)
[   17.527891] rtl8723e: disagrees about version of symbol rtl_cam_get_free_entry
[   17.527893] rtl8723e: Unknown symbol rtl_cam_get_free_entry (err -22)
[   17.527895] rtl8723e: disagrees about version of symbol rtl_pci_probe
[   17.527896] rtl8723e: Unknown symbol rtl_pci_probe (err -22)
[   17.527900] rtl8723e: disagrees about version of symbol rtl_cam_delete_one_entry
[   17.527902] rtl8723e: Unknown symbol rtl_cam_delete_one_entry (err -22)
[   17.528279] rtl8723ae: disagrees about version of symbol efuse_read_1byte
[   17.528282] rtl8723ae: Unknown symbol efuse_read_1byte (err -22)
[   17.528292] rtl8723ae: Unknown symbol rtl_process_phyinfo (err 0)
[   17.528295] rtl8723ae: disagrees about version of symbol rtl_cam_reset_all_entry
[   17.528296] rtl8723ae: Unknown symbol rtl_cam_reset_all_entry (err -22)
[   17.528300] rtl8723ae: disagrees about version of symbol rtl_cam_empty_entry
[   17.528302] rtl8723ae: Unknown symbol rtl_cam_empty_entry (err -22)
[   17.528313] rtl8723ae: disagrees about version of symbol rtl_cam_del_entry
[   17.528314] rtl8723ae: Unknown symbol rtl_cam_del_entry (err -22)
[   17.528320] rtl8723ae: disagrees about version of symbol rtl_cam_mark_invalid
[   17.528322] rtl8723ae: Unknown symbol rtl_cam_mark_invalid (err -22)
[   17.528337] rtl8723ae: disagrees about version of symbol rtl_pci_disconnect
[   17.528339] rtl8723ae: Unknown symbol rtl_pci_disconnect (err -22)
[   17.528341] rtl8723ae: disagrees about version of symbol rtl_pci_suspend
[   17.528342] rtl8723ae: Unknown symbol rtl_pci_suspend (err -22)
[   17.528345] rtl8723ae: disagrees about version of symbol rtlwifi_rate_mapping
[   17.528346] rtl8723ae: Unknown symbol rtlwifi_rate_mapping (err -22)
[   17.528355] rtl8723ae: Unknown symbol rtl_signal_scale_mapping (err 0)
[   17.528362] rtl8723ae: disagrees about version of symbol rtl_ps_enable_nic
[   17.528363] rtl8723ae: Unknown symbol rtl_ps_enable_nic (err -22)
[   17.528366] rtl8723ae: disagrees about version of symbol rtl_pci_resume
[   17.528367] rtl8723ae: Unknown symbol rtl_pci_resume (err -22)
[   17.528376] rtl8723ae: Unknown symbol rtl_evm_db_to_percentage (err 0)
[   17.528379] rtl8723ae: disagrees about version of symbol rtl_cam_add_one_entry
[   17.528380] rtl8723ae: Unknown symbol rtl_cam_add_one_entry (err -22)
[   17.528387] rtl8723ae: Unknown symbol rtl_query_rxpwrpercentage (err 0)
[   17.528390] rtl8723ae: disagrees about version of symbol rtl_efuse_shadow_map_update
[   17.528392] rtl8723ae: Unknown symbol rtl_efuse_shadow_map_update (err -22)
[   17.528393] rtl8723ae: disagrees about version of symbol rtl_get_tcb_desc
[   17.528395] rtl8723ae: Unknown symbol rtl_get_tcb_desc (err -22)
[   17.528397] rtl8723ae: disagrees about version of symbol rtl_ps_disable_nic
[   17.528399] rtl8723ae: Unknown symbol rtl_ps_disable_nic (err -22)
[   17.528403] rtl8723ae: disagrees about version of symbol rtl_cam_get_free_entry
[   17.528404] rtl8723ae: Unknown symbol rtl_cam_get_free_entry (err -22)
[   17.528407] rtl8723ae: disagrees about version of symbol rtl_pci_probe
[   17.528408] rtl8723ae: Unknown symbol rtl_pci_probe (err -22)
[   17.528411] rtl8723ae: disagrees about version of symbol rtl_fw_cb
[   17.528412] rtl8723ae: Unknown symbol rtl_fw_cb (err -22)
[   17.528414] rtl8723ae: disagrees about version of symbol rtl_cam_delete_one_entry
[   17.528416] rtl8723ae: Unknown symbol rtl_cam_delete_one_entry (err -22)
[  721.751735] rtl8723e: disagrees about version of symbol efuse_read_1byte
[  721.751742] rtl8723e: Unknown symbol efuse_read_1byte (err -22)
[  721.751774] rtl8723e: Unknown symbol rtl_process_phyinfo (err 0)
[  721.751784] rtl8723e: disagrees about version of symbol rtl_cam_reset_all_entry
[  721.751787] rtl8723e: Unknown symbol rtl_cam_reset_all_entry (err -22)
[  721.751801] rtl8723e: disagrees about version of symbol rtl_cam_empty_entry
[  721.751803] rtl8723e: Unknown symbol rtl_cam_empty_entry (err -22)
[  721.751812] rtl8723e: disagrees about version of symbol rtl_cam_del_entry
[  721.751814] rtl8723e: Unknown symbol rtl_cam_del_entry (err -22)
[  721.751827] rtl8723e: disagrees about version of symbol rtl_cam_mark_invalid
[  721.751829] rtl8723e: Unknown symbol rtl_cam_mark_invalid (err -22)
[  721.751848] rtl8723e: disagrees about version of symbol ieee80211_find_sta
[  721.751851] rtl8723e: Unknown symbol ieee80211_find_sta (err -22)
[  721.751863] rtl8723e: disagrees about version of symbol rtl_pci_disconnect
[  721.751865] rtl8723e: Unknown symbol rtl_pci_disconnect (err -22)
[  721.751873] rtl8723e: disagrees about version of symbol rtl_pci_suspend
[  721.751875] rtl8723e: Unknown symbol rtl_pci_suspend (err -22)
[  721.751893] rtl8723e: Unknown symbol rtl_signal_scale_mapping (err 0)
[  721.751911] rtl8723e: disagrees about version of symbol rtl_ps_enable_nic
[  721.751913] rtl8723e: Unknown symbol rtl_ps_enable_nic (err -22)
[  721.751921] rtl8723e: disagrees about version of symbol rtl_pci_resume
[  721.751924] rtl8723e: Unknown symbol rtl_pci_resume (err -22)
[  721.751941] rtl8723e: Unknown symbol rtl_evm_db_to_percentage (err 0)
[  721.751952] rtl8723e: disagrees about version of symbol rtl_cam_add_one_entry
[  721.751954] rtl8723e: Unknown symbol rtl_cam_add_one_entry (err -22)
[  721.751969] rtl8723e: Unknown symbol rtl_query_rxpwrpercentage (err 0)
[  721.751979] rtl8723e: disagrees about version of symbol rtl_efuse_shadow_map_update
[  721.751982] rtl8723e: Unknown symbol rtl_efuse_shadow_map_update (err -22)
[  721.751989] rtl8723e: disagrees about version of symbol rtl_get_tcb_desc
[  721.751992] rtl8723e: Unknown symbol rtl_get_tcb_desc (err -22)
[  721.751999] rtl8723e: disagrees about version of symbol rtl_ps_disable_nic
[  721.752002] rtl8723e: Unknown symbol rtl_ps_disable_nic (err -22)
[  721.752013] rtl8723e: disagrees about version of symbol rtl_cam_get_free_entry
[  721.752016] rtl8723e: Unknown symbol rtl_cam_get_free_entry (err -22)
[  721.752023] rtl8723e: disagrees about version of symbol rtl_pci_probe
[  721.752026] rtl8723e: Unknown symbol rtl_pci_probe (err -22)
[  721.752034] rtl8723e: disagrees about version of symbol rtl_cam_delete_one_entry
[  721.752037] rtl8723e: Unknown symbol rtl_cam_delete_one_entry (err -22)



```

I've searched literally the entire day for a solution, but I can't find any. Can anyone help me please?

If it is useful:

iwconfig:
```

pedro@pedro-N460-P-BG55P1:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.

```

lsmod:

```



pedro@pedro-N460-P-BG55P1:~$ lsmod | grep "wlan_module_name"
pedro@pedro-N460-P-BG55P1:~$ lsmod
Module                  Size  Used by
parport_pc             32689  0 
ppdev                  17074  0 
rfcomm                 42652  16 
bnep                   18141  2 
nls_iso8859_1          12714  1 
joydev                 17458  0 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
coretemp               13401  0 
kvm_intel             132760  0 
kvm                   414071  1 kvm_intel
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
microcode              22804  0 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                95595  0 
snd_seq_midi           13325  0 
serio_raw              13216  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
rtsx_pci_ms            13012  0 
memstick               16555  1 rtsx_pci_ms
rtlwifi                74703  0 
btusb                  18335  0 
bluetooth             205000  22 rfcomm,bnep,btusb
mac80211              549341  1 rtlwifi
mac_hid                13206  0 
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
cfg80211              211134  2 rtlwifi,mac80211
mei                    40691  0 
lpc_ich                17062  0 
alx                    81293  0 
compat                 14950  8 rfcomm,bnep,rtlwifi,btusb,bluetooth,mac80211,cfg80211,alx
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
rtsx_pci_sdmmc         17476  0 
rtsx_pci               28325  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25721  4 
libahci                31192  1 ahci
radeon                895730  1 
i915                  520615  3 
ttm                    83596  1 radeon
drm_kms_helper         49113  2 radeon,i915
drm                   288721  7 radeon,i915,ttm,drm_kms_helper
i2c_algo_bit           13414  2 i915,radeon
wmi                    19071  0 
video                  19391  1 i915



```

Thank you all already for the help!

edit:
Maybe also helpful:
```
pedro@pedro-N460-P-BG55P1:~$ lsb_release -dDescription:    Ubuntu 12.10
pedro@pedro-N460-P-BG55P1:~$ uname -mr
3.5.0-26-generic x86_64




```

---

### Post by chili555 on 2013-03-20
Which version of the driver did you compile? This one? rtl_92ce_92se_92de_8723ae_linux_mac80211_000[COLOR="#FF0000"]6.0514.2012[/COLOR] There is a slightly improved version. Here is a link from my own Dropbox. [https://dl.dropbox.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz](https://dl.dropbox.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz)

Post back if you need additional guidance.

---

### Post by dougao06 on 2013-03-21
Hello Chilli,

thank you for replying (my timezone is different I guess, that is why it took me long to reply).

The version I compiled is rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012, which apparently is the newer version you are talking about (I think I even got it from your post in an older thread).

So I assume the answer is not there. In an older thread (in an openSUSE forum, actually), someone says you need to use rmmod rtl8192se when met with this issue (the thread is here: [http://forums.opensuse.org/english/get-technical-help-here/wireless/477285-rtl8723ae-realtek-wirless-driver-hell-2.html](http://forums.opensuse.org/english/get-technical-help-here/wireless/477285-rtl8723ae-realtek-wirless-driver-hell-2.html)). But this doesn't work in my case either (there is no such module)!

---

### Post by chili555 on 2013-03-21
Please show me:```
cd Desktop/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809 .2012  [COLOR="#FF0000"]<--or wherever you extracted the package[/COLOR]
sudo su
make clean
make
make install
modprobe rtl8723e
exit
```Copy and paste from the terminal output to post here.

---

### Post by dougao06 on 2013-03-21
I don't know if you meant to post everything, but here it goes (sorry if some of it is superfluous):

make clean:
```
root@pedro-N460-P-BG55P1:/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012# make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Entering directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
make[1]: Entering directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
make[1]: Entering directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make[1]: Entering directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'
```

make:
```
root@pedro-N460-P-BG55P1:/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012# makemake -C /lib/modules/3.5.0-26-generic/build M=/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/base.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rc.o
/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rc.c:284:2: warning: initialization from incompatible pointer type [enabled by default]
/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rc.c:284:2: warning: (near initialization for ‘rtl_rate_ops.rate_update’) [enabled by default]
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/debug.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/regd.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/efuse.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/cam.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/ps.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/core.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/stats.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/pci.o
  LD [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtlwifi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtlwifi.mod.o
  LD [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtlwifi.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make[1]: Entering directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
make -C /lib/modules/3.5.0-26-generic/build M=/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/hw.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/table.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/sw.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/trx.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/led.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/fw.o
/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/fw.c: In function ‘rtl92c_download_fw’:
/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/fw.c:239:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 4 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/phy.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/rf.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/dm.o
  LD [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/rtl8192ce.o
  Building modules, stage 2.                                                                                                                                                                    
  MODPOST 1 modules                                                                                                                                                                             
  CC      /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/rtl8192ce.mod.o                                                                               
  LD [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce/rtl8192ce.ko                                                                                  
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'                                                                                                                            
make[1]: Leaving directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'                                                                            
make[1]: Entering directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'                                                                           
make -C /lib/modules/3.5.0-26-generic/build M=/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se modules                                                   
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'                                                                                                                           
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/hw.o                                                                                          
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/table.o                                                                                       
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/sw.o                                                                                          
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/trx.o                                                                                         
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/led.o                                                                                         
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/fw.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/phy.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/rf.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/dm.o
  LD [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/rtl8192se.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se/rtl8192se.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make[1]: Leaving directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
make[1]: Entering directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make -C /lib/modules/3.5.0-26-generic/build M=/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/hw.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/table.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/sw.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/trx.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/led.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/fw.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/phy.o
/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/phy.c: In function ‘rtl92d_phy_reset_iqk_result’:
/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/phy.c:3002:2: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/rf.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/dm.o
  LD [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/rtl8192de.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de/rtl8192de.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make[1]: Leaving directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make[1]: Entering directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'
make -C /lib/modules/3.5.0-26-generic/build M=/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/hw.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/table.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/sw.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/trx.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/led.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/fw.o
/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/fw.c: In function ‘rtl8723e_download_fw’:
/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/fw.c:204:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 4 has type ‘long unsigned int’ [-Wformat]
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/phy.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/rf.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/dm.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/pwrseq.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/pwrseqcmd.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/hal_btc.o
  CC [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/hal_bt_coexist.o
  LD [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/rtl8723e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/rtl8723e.mod.o
  LD [M]  /home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e/rtl8723e.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make[1]: Leaving directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'

```

make install:
```
root@pedro-N460-P-BG55P1:/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012# make installmake -C /lib/modules/3.5.0-26-generic/build M=/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make[1]: Entering directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
make -C /lib/modules/3.5.0-26-generic/build M=/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make[1]: Leaving directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192ce'
make[1]: Entering directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
make -C /lib/modules/3.5.0-26-generic/build M=/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make[1]: Leaving directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192se'
make[1]: Entering directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make -C /lib/modules/3.5.0-26-generic/build M=/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make[1]: Leaving directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8192de'
make[1]: Entering directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'
make -C /lib/modules/3.5.0-26-generic/build M=/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e modules
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make[1]: Leaving directory `/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/rtl8723e'
find /lib/modules/3.5.0-26-generic -name "r8192se_*.ko" -exec rm {} \;
find /lib/modules/3.5.0-26-generic -name "r8192ce_*.ko" -exec rm {} \;
find /lib/modules/3.5.0-26-generic -name "r8723e_*.ko" -exec rm {} \;

```

modprobe:
```
root@pedro-N460-P-BG55P1:/home/pedro/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012# modprobe rtl8723eFATAL: Error inserting rtl8723e (/lib/modules/3.5.0-26-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko): Invalid argument

```

---

### Post by chili555 on 2013-03-21
Please see: [http://www.jfdesignnet.com/?p=2450](http://www.jfdesignnet.com/?p=2450)> If you’ve got error trying to modprobe rtl8723e, just like this :


```
[root@user-NEON-RNE rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012]# modprobe rtl8723e
FATAL: Error inserting rtl8723e (/lib/modules/3.2.0-30-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko): Invalid argument
```

then it means there is some compat wireless module especially with rtlwifi.ko module that conflicting with this rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 driver. You must make sure there were no compat wireless on the system by removing / uninstalling them before doing make. If you were using atheros ethernet ar8161 with compat-wireless or there is the linux-backports-modules-cw-xxx module on system, you must uninstall them first.Do you have the package linux-backports-modules-cw-3.xx installed? For your ethernet, by any chance? If so, now the *really* hard work begins!!!

---

### Post by dougao06 on 2013-03-21
I'm afraid so, I actually have the exact ethernet board he mentions (atheros ar8161).
I installed the driver using this: [http://askubuntu.com/questions/217361/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller-on-64-bit-12](http://askubuntu.com/questions/217361/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller-on-64-bit-12) (the accepted answer), but using [FONT=Ubuntu Mono]3.5.0-26 instead of 3.5.0-18.
Should I uninstall it and install the wireless one, then? But then when I try to reinstall it will both work?[/FONT]

---

### Post by chili555 on 2013-03-21
> **dougao06 said:**
> I'm afraid so, I actually have the exact ethernet board he mentions (atheros ar8161).
I installed the driver using this: [http://askubuntu.com/questions/217361/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller-on-64-bit-12](http://askubuntu.com/questions/217361/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller-on-64-bit-12) (the accepted answer), but using [FONT=Ubuntu Mono]3.5.0-26 instead of 3.5.0-18.
Should I uninstall it and install the wireless one, then? But then when I try to reinstall it will both work?[/FONT]My belief, based on a few years of experience in such matters and a bit of guesswork, is that the backports package handles the x80211 pieces differently than the native built-in drivers as well as rtl8723e. Therefor, you end up with a sad situation where wireless works and ethernet doesn't or vice versa, but never both. There is another post about that here and a couple, if I remember correctly, at askubuntu.com. Maybe that's alright with you. Maybe you can use wireless everywhere. If that's the case, I'd uninstall backports, compile rtl8723e and hope for an early fix. Before you do so, however, I'd download a copy of backports to your desktop in case you get in a jam and need to reinstall it. It may reside in your apt cache; check:```
ls /var/cache/apt/archives/ | grep backports
```If the .deb file is there, that's all the lifeline you need to reinstall. Here is a reference from my machine:> /var/cache/apt/archives/linux-backports-modules-cw-3.6-3.5.0-25-generic_3.5.0-25.11_amd64.deb
/var/cache/apt/archives/linux-backports-modules-cw-3.6-3.5.0-26-generic_3.5.0-26.12_amd64.deb
/var/cache/apt/archives/linux-backports-modules-cw-3.6-quantal-generic_3.5.0.25.31_amd64.deb
/var/cache/apt/archives/linux-backports-modules-cw-3.6-quantal-generic_3.5.0.26.32_amd64.deb


If you truly need both ethernet and wireless,I'd uninstall backports (after saving a backup, of course), compile rtl8723e and then compile compat-wireless using the driver-select to specify only the ethernet driver alx is to be installed, not the wireless parts. I'd compile compat-wireless-3.6.8-1-***snpc***. Then, I strongly believe both will work.

I wish I could point you to a link where this succeeded but I can't. You may be the first to even try it!

You seem pretty adept since you got this far unaided, as far as I know, but if you need additional guidance, I'll be happy to help.

Be careful out there on the tightrope. If in doubt, stop and ask.

---

### Post by dougao06 on 2013-03-21
Thank you Chilli,

actually it was easier than expected! I uninstalled the backports, as you suggested, and the internet didn't stop working. So I restarted the PC, and not only didn't the ethernet stop, but the wireless worked.

I don't understand why (maybe between linux-3.5.0.18 and 3.5.0.26 the driver was added to the kernel?), but I'm not complaining, heheh.

Anyway, thank you again! Although it ended up being an easy fix, I would never have thought of it without your help.

---

### Post by chili555 on 2013-03-21
I believe *alx* was added in -24 and later. Of course, whether it worked as perfectly as it should is another question, which you have now answered!

Glad it's all working now.

---

