---
title: "driver for cisco mpi 350 wirless (airo)"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by andrewjoint on 2010-02-11
please at all programmers!!...put all cisco drivers and firmware for wireless in a new ubuntu 10.04..!!!...i'm from italy and i love ubuntu i have a big problem with a mini pci wirelesS ciSco airo mpi 350...:popcorn:


GRAZIE!!!!

---

### Post by chili555 on 2010-02-11
Does the *airo.ko* module not work correctly for you? Or are you just trying to be sure we Aironet fans don't get abandoned?

---

### Post by andrewjoint on 2010-02-11
don't work!

---

### Post by andrewjoint on 2010-02-11
i try to use windows wirless driver non ndswrapper...but nothing...

---

### Post by chili555 on 2010-02-11
This sometimes helps: [http://ubuntuforums.org/showpost.php?p=8740779&postcount=6](http://ubuntuforums.org/showpost.php?p=8740779&postcount=6)

Please try it, reboot and let us know.

---

### Post by andrewjoint on 2010-02-11
nothing!!...please help me!!

andrew@andrew-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
snd_maestro3           19364  2 
snd_ac97_codec        101216  1 snd_maestro3
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9156  1 snd_pcm
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8187                50624  0 
snd_timer              22276  2 snd_pcm,snd_seq
mac80211              181236  1 rtl8187
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               4096  1 rtl8187
pcmcia                 36808  0 
eeprom_93cx6            1916  1 rtl8187
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
yenta_socket           24200  2 
ppdev                   6688  0 
snd                    59204  14 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rsrc_nonstatic         11644  1 yenta_socket
lp                      8964  0 
parport_pc             31940  1 
cfg80211               93052  2 rtl8187,mac80211
shpchp                 32272  0 
soundcore               7264  1 snd
dell_wmi                2564  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
airo                   72924  0 
parport                35340  3 ppdev,lp,parport_pc
psmouse                56180  0 
i2c_piix4               9932  0 
serio_raw               5280  0 
dcdbas                  7292  0 
usb_storage            52544  1 
video                  19380  0 
output                  2780  1 video
floppy                 54916  0 
intel_agp              27484  1 
agpgart                34988  1 intel_agp
andrew@andrew-laptop:~$

---

### Post by chili555 on 2010-02-11
Please remove your USB wirless device and then post:```
dmesg | grep airo
iwconfig
```Thanks.

---

### Post by andrewjoint on 2010-02-12
ok man!!! good morning...i try but my card is not USB but mini pci..

---

### Post by chili555 on 2010-02-12
Sorry, I guessed wrong! Please don't remove it, simply run those commands.

---

### Post by andrewjoint on 2010-02-12
this is the result...sorry for the disturbs....







andrew@andrew-laptop:~$ dmesg | grep airo
[   12.819631] airo(): Probing for PCI adapters
[   12.819822] airo 0000:00:10.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.819877] airo(): Found an MPI350 card
[   13.995352] airo(eth0): Firmware version 5.41.00
[   13.995361] airo(eth0): WPA supported.
[   13.995370] airo(eth0): MAC enabled 00:02:8a:31:dc:9f
[   14.012918] airo(): Finished probing for PCI adapters
[   17.300063] airo(eth0): set_wep_key: key length to set was zero
[   17.300078] airo(eth0): failed to set WEP key at index 0: -1.
[   17.300268] airo(eth0): set_wep_key: key length to set was zero
[   17.300277] airo(eth0): failed to set WEP key at index 1: -1.
[   17.300325] airo(eth0): set_wep_key: key length to set was zero
[   17.300334] airo(eth0): failed to set WEP key at index 2: -1.
[   17.300381] airo(eth0): set_wep_key: key length to set was zero
[   17.300389] airo(eth0): failed to set WEP key at index 3: -1.
[  952.177350] airo(eth0): set_wep_key: key length to set was zero
[  952.177368] airo(eth0): failed to set WEP key at index 0: -1.
[  952.177517] airo(eth0): set_wep_key: key length to set was zero
[  952.177525] airo(eth0): failed to set WEP key at index 1: -1.
[  952.177573] airo(eth0): set_wep_key: key length to set was zero
[  952.177581] airo(eth0): failed to set WEP key at index 2: -1.
[  952.177628] airo(eth0): set_wep_key: key length to set was zero
[  952.177636] airo(eth0): failed to set WEP key at index 3: -1.
[  957.220505] airo(eth0): set_wep_key: key length to set was zero
[  957.220524] airo(eth0): failed to set WEP key at index 0: -1.
[  957.220665] airo(eth0): set_wep_key: key length to set was zero
[  957.220673] airo(eth0): failed to set WEP key at index 1: -1.
[  957.220722] airo(eth0): set_wep_key: key length to set was zero
[  957.220730] airo(eth0): failed to set WEP key at index 2: -1.
[  957.220776] airo(eth0): set_wep_key: key length to set was zero
[  957.220785] airo(eth0): failed to set WEP key at index 3: -1.
[  962.257736] airo(eth0): set_wep_key: key length to set was zero
[  962.257753] airo(eth0): failed to set WEP key at index 0: -1.
[  962.257903] airo(eth0): set_wep_key: key length to set was zero
[  962.257911] airo(eth0): failed to set WEP key at index 1: -1.
[  962.257959] airo(eth0): set_wep_key: key length to set was zero
[  962.257967] airo(eth0): failed to set WEP key at index 2: -1.
[  962.258014] airo(eth0): set_wep_key: key length to set was zero
[  962.258022] airo(eth0): failed to set WEP key at index 3: -1.
[  967.301190] airo(eth0): set_wep_key: key length to set was zero
[  967.301208] airo(eth0): failed to set WEP key at index 0: -1.
[  967.301348] airo(eth0): set_wep_key: key length to set was zero
[  967.301357] airo(eth0): failed to set WEP key at index 1: -1.
[  967.301405] airo(eth0): set_wep_key: key length to set was zero
[  967.301413] airo(eth0): failed to set WEP key at index 2: -1.
[  967.301460] airo(eth0): set_wep_key: key length to set was zero
[  967.301468] airo(eth0): failed to set WEP key at index 3: -1.
[  972.339463] airo(eth0): set_wep_key: key length to set was zero
[  972.339481] airo(eth0): failed to set WEP key at index 0: -1.
[  972.339624] airo(eth0): set_wep_key: key length to set was zero
[  972.339633] airo(eth0): failed to set WEP key at index 1: -1.
[  972.339682] airo(eth0): set_wep_key: key length to set was zero
[  972.339690] airo(eth0): failed to set WEP key at index 2: -1.
[  972.339736] airo(eth0): set_wep_key: key length to set was zero
[  972.339745] airo(eth0): failed to set WEP key at index 3: -1.
[  977.390506] airo(eth0): set_wep_key: key length to set was zero
[  977.390524] airo(eth0): failed to set WEP key at index 0: -1.
[  977.390665] airo(eth0): set_wep_key: key length to set was zero
[  977.390674] airo(eth0): failed to set WEP key at index 1: -1.
[  977.390722] airo(eth0): set_wep_key: key length to set was zero
[  977.390730] airo(eth0): failed to set WEP key at index 2: -1.
[  977.390777] airo(eth0): set_wep_key: key length to set was zero
[  977.390785] airo(eth0): failed to set WEP key at index 3: -1.
[  982.428917] airo(eth0): set_wep_key: key length to set was zero
[  982.428936] airo(eth0): failed to set WEP key at index 0: -1.
[  982.429076] airo(eth0): set_wep_key: key length to set was zero
[  982.429084] airo(eth0): failed to set WEP key at index 1: -1.
[  982.429132] airo(eth0): set_wep_key: key length to set was zero
[  982.429141] airo(eth0): failed to set WEP key at index 2: -1.
[  982.429187] airo(eth0): set_wep_key: key length to set was zero
[  982.429195] airo(eth0): failed to set WEP key at index 3: -1.
[  987.467154] airo(eth0): set_wep_key: key length to set was zero
[  987.467172] airo(eth0): failed to set WEP key at index 0: -1.
[  987.467313] airo(eth0): set_wep_key: key length to set was zero
[  987.467321] airo(eth0): failed to set WEP key at index 1: -1.
[  987.467369] airo(eth0): set_wep_key: key length to set was zero
[  987.467377] airo(eth0): failed to set WEP key at index 2: -1.
[  987.467424] airo(eth0): set_wep_key: key length to set was zero
[  987.467433] airo(eth0): failed to set WEP key at index 3: -1.
[  992.510392] airo(eth0): set_wep_key: key length to set was zero
[  992.510410] airo(eth0): failed to set WEP key at index 0: -1.
[  992.510553] airo(eth0): set_wep_key: key length to set was zero
[  992.510561] airo(eth0): failed to set WEP key at index 1: -1.
[  992.510611] airo(eth0): set_wep_key: key length to set was zero
[  992.510619] airo(eth0): failed to set WEP key at index 2: -1.
[  992.510666] airo(eth0): set_wep_key: key length to set was zero
[  992.510674] airo(eth0): failed to set WEP key at index 3: -1.
[  997.548740] airo(eth0): set_wep_key: key length to set was zero
[  997.548759] airo(eth0): failed to set WEP key at index 0: -1.
[  997.548901] airo(eth0): set_wep_key: key length to set was zero
[  997.548909] airo(eth0): failed to set WEP key at index 1: -1.
[  997.548958] airo(eth0): set_wep_key: key length to set was zero
[  997.548966] airo(eth0): failed to set WEP key at index 2: -1.
[  997.549012] airo(eth0): set_wep_key: key length to set was zero
[  997.549021] airo(eth0): failed to set WEP key at index 3: -1.
[ 1002.588795] airo(eth0): set_wep_key: key length to set was zero
[ 1002.588813] airo(eth0): failed to set WEP key at index 0: -1.
[ 1002.588954] airo(eth0): set_wep_key: key length to set was zero
[ 1002.588963] airo(eth0): failed to set WEP key at index 1: -1.
[ 1002.589011] airo(eth0): set_wep_key: key length to set was zero
[ 1002.589019] airo(eth0): failed to set WEP key at index 2: -1.
[ 1002.589066] airo(eth0): set_wep_key: key length to set was zero
[ 1002.589074] airo(eth0): failed to set WEP key at index 3: -1.
[ 1006.894534] airo(eth0): set_wep_key: key length to set was zero
[ 1006.894552] airo(eth0): failed to set WEP key at index 0: -1.
[ 1006.894695] airo(eth0): set_wep_key: key length to set was zero
[ 1006.894703] airo(eth0): failed to set WEP key at index 1: -1.
[ 1006.894751] airo(eth0): set_wep_key: key length to set was zero
[ 1006.894759] airo(eth0): failed to set WEP key at index 2: -1.
[ 1006.894806] airo(eth0): set_wep_key: key length to set was zero
[ 1006.894814] airo(eth0): failed to set WEP key at index 3: -1.
[ 1022.641115] airo(eth0): set_wep_key: key length to set was zero
[ 1022.641133] airo(eth0): failed to set WEP key at index 0: -1.
[ 1022.641276] airo(eth0): set_wep_key: key length to set was zero
[ 1022.641284] airo(eth0): failed to set WEP key at index 1: -1.
[ 1022.641332] airo(eth0): set_wep_key: key length to set was zero
[ 1022.641340] airo(eth0): failed to set WEP key at index 2: -1.
[ 1022.641387] airo(eth0): set_wep_key: key length to set was zero
[ 1022.641395] airo(eth0): failed to set WEP key at index 3: -1.
[ 1027.679362] airo(eth0): set_wep_key: key length to set was zero
[ 1027.679380] airo(eth0): failed to set WEP key at index 0: -1.
[ 1027.679523] airo(eth0): set_wep_key: key length to set was zero
[ 1027.679532] airo(eth0): failed to set WEP key at index 1: -1.
[ 1027.679580] airo(eth0): set_wep_key: key length to set was zero
[ 1027.679588] airo(eth0): failed to set WEP key at index 2: -1.
[ 1027.679635] airo(eth0): set_wep_key: key length to set was zero
[ 1027.679643] airo(eth0): failed to set WEP key at index 3: -1.
[ 1032.722308] airo(eth0): set_wep_key: key length to set was zero
[ 1032.722326] airo(eth0): failed to set WEP key at index 0: -1.
[ 1032.722467] airo(eth0): set_wep_key: key length to set was zero
[ 1032.722475] airo(eth0): failed to set WEP key at index 1: -1.
[ 1032.722524] airo(eth0): set_wep_key: key length to set was zero
[ 1032.722532] airo(eth0): failed to set WEP key at index 2: -1.
[ 1032.722578] airo(eth0): set_wep_key: key length to set was zero
[ 1032.722587] airo(eth0): failed to set WEP key at index 3: -1.
[ 1037.760734] airo(eth0): set_wep_key: key length to set was zero
[ 1037.760752] airo(eth0): failed to set WEP key at index 0: -1.
[ 1037.760894] airo(eth0): set_wep_key: key length to set was zero
[ 1037.760902] airo(eth0): failed to set WEP key at index 1: -1.
[ 1037.760952] airo(eth0): set_wep_key: key length to set was zero
[ 1037.760960] airo(eth0): failed to set WEP key at index 2: -1.
[ 1037.761007] airo(eth0): set_wep_key: key length to set was zero
[ 1037.761015] airo(eth0): failed to set WEP key at index 3: -1.
[ 1042.798976] airo(eth0): set_wep_key: key length to set was zero
[ 1042.798994] airo(eth0): failed to set WEP key at index 0: -1.
[ 1042.799135] airo(eth0): set_wep_key: key length to set was zero
[ 1042.799144] airo(eth0): failed to set WEP key at index 1: -1.
[ 1042.799192] airo(eth0): set_wep_key: key length to set was zero
[ 1042.799200] airo(eth0): failed to set WEP key at index 2: -1.
[ 1042.799247] airo(eth0): set_wep_key: key length to set was zero
[ 1042.799255] airo(eth0): failed to set WEP key at index 3: -1.
[ 1047.837674] airo(eth0): set_wep_key: key length to set was zero
[ 1047.837692] airo(eth0): failed to set WEP key at index 0: -1.
[ 1047.837833] airo(eth0): set_wep_key: key length to set was zero
[ 1047.837842] airo(eth0): failed to set WEP key at index 1: -1.
[ 1047.837891] airo(eth0): set_wep_key: key length to set was zero
[ 1047.837899] airo(eth0): failed to set WEP key at index 2: -1.
[ 1047.837947] airo(eth0): set_wep_key: key length to set was zero
[ 1047.837955] airo(eth0): failed to set WEP key at index 3: -1.
[ 1052.876087] airo(eth0): set_wep_key: key length to set was zero
[ 1052.876105] airo(eth0): failed to set WEP key at index 0: -1.
[ 1052.876246] airo(eth0): set_wep_key: key length to set was zero
[ 1052.876254] airo(eth0): failed to set WEP key at index 1: -1.
[ 1052.876304] airo(eth0): set_wep_key: key length to set was zero
[ 1052.876312] airo(eth0): failed to set WEP key at index 2: -1.
[ 1052.876359] airo(eth0): set_wep_key: key length to set was zero
[ 1052.876367] airo(eth0): failed to set WEP key at index 3: -1.
[ 1057.909562] airo(eth0): set_wep_key: key length to set was zero
[ 1057.909579] airo(eth0): failed to set WEP key at index 0: -1.
[ 1057.909721] airo(eth0): set_wep_key: key length to set was zero
[ 1057.909729] airo(eth0): failed to set WEP key at index 1: -1.
[ 1057.909777] airo(eth0): set_wep_key: key length to set was zero
[ 1057.909785] airo(eth0): failed to set WEP key at index 2: -1.
[ 1057.909832] airo(eth0): set_wep_key: key length to set was zero
[ 1057.909840] airo(eth0): failed to set WEP key at index 3: -1.
[ 1062.945125] airo(eth0): set_wep_key: key length to set was zero
[ 1062.945143] airo(eth0): failed to set WEP key at index 0: -1.
[ 1062.945284] airo(eth0): set_wep_key: key length to set was zero
[ 1062.945292] airo(eth0): failed to set WEP key at index 1: -1.
[ 1062.945340] airo(eth0): set_wep_key: key length to set was zero
[ 1062.945349] airo(eth0): failed to set WEP key at index 2: -1.
[ 1062.945395] airo(eth0): set_wep_key: key length to set was zero
[ 1062.945403] airo(eth0): failed to set WEP key at index 3: -1.
[ 1067.983436] airo(eth0): set_wep_key: key length to set was zero
[ 1067.983453] airo(eth0): failed to set WEP key at index 0: -1.
[ 1067.983595] airo(eth0): set_wep_key: key length to set was zero
[ 1067.983603] airo(eth0): failed to set WEP key at index 1: -1.
[ 1067.983652] airo(eth0): set_wep_key: key length to set was zero
[ 1067.983660] airo(eth0): failed to set WEP key at index 2: -1.
[ 1067.983707] airo(eth0): set_wep_key: key length to set was zero
[ 1067.983716] airo(eth0): failed to set WEP key at index 3: -1.
[ 1073.026220] airo(eth0): set_wep_key: key length to set was zero
[ 1073.026237] airo(eth0): failed to set WEP key at index 0: -1.
[ 1073.026379] airo(eth0): set_wep_key: key length to set was zero
[ 1073.026387] airo(eth0): failed to set WEP key at index 1: -1.
[ 1073.026436] airo(eth0): set_wep_key: key length to set was zero
[ 1073.026445] airo(eth0): failed to set WEP key at index 2: -1.
[ 1073.026492] airo(eth0): set_wep_key: key length to set was zero
[ 1073.026500] airo(eth0): failed to set WEP key at index 3: -1.
[ 1077.885743] airo(eth0): set_wep_key: key length to set was zero
[ 1077.885763] airo(eth0): failed to set WEP key at index 0: -1.
[ 1077.885928] airo(eth0): set_wep_key: key length to set was zero
[ 1077.885936] airo(eth0): failed to set WEP key at index 1: -1.
[ 1077.885984] airo(eth0): set_wep_key: key length to set was zero
[ 1077.885993] airo(eth0): failed to set WEP key at index 2: -1.
[ 1077.886039] airo(eth0): set_wep_key: key length to set was zero
[ 1077.886047] airo(eth0): failed to set WEP key at index 3: -1.
[ 1144.006530] airo(eth0): set_wep_key: key length to set was zero
[ 1144.006547] airo(eth0): failed to set WEP key at index 0: -1.
[ 1144.006688] airo(eth0): set_wep_key: key length to set was zero
[ 1144.006696] airo(eth0): failed to set WEP key at index 1: -1.
[ 1144.006744] airo(eth0): set_wep_key: key length to set was zero
[ 1144.006752] airo(eth0): failed to set WEP key at index 2: -1.
[ 1144.006799] airo(eth0): set_wep_key: key length to set was zero
[ 1144.006807] airo(eth0): failed to set WEP key at index 3: -1.
[ 1149.044826] airo(eth0): set_wep_key: key length to set was zero
[ 1149.044843] airo(eth0): failed to set WEP key at index 0: -1.
[ 1149.044990] airo(eth0): set_wep_key: key length to set was zero
[ 1149.044998] airo(eth0): failed to set WEP key at index 1: -1.
[ 1149.045046] airo(eth0): set_wep_key: key length to set was zero
[ 1149.045054] airo(eth0): failed to set WEP key at index 2: -1.
[ 1149.045101] airo(eth0): set_wep_key: key length to set was zero
[ 1149.045109] airo(eth0): failed to set WEP key at index 3: -1.
[ 1154.083090] airo(eth0): set_wep_key: key length to set was zero
[ 1154.083107] airo(eth0): failed to set WEP key at index 0: -1.
[ 1154.083251] airo(eth0): set_wep_key: key length to set was zero
[ 1154.083260] airo(eth0): failed to set WEP key at index 1: -1.
[ 1154.083309] airo(eth0): set_wep_key: key length to set was zero
[ 1154.083317] airo(eth0): failed to set WEP key at index 2: -1.
[ 1154.083364] airo(eth0): set_wep_key: key length to set was zero
[ 1154.083372] airo(eth0): failed to set WEP key at index 3: -1.
[ 1159.121451] airo(eth0): set_wep_key: key length to set was zero
[ 1159.121469] airo(eth0): failed to set WEP key at index 0: -1.
[ 1159.121616] airo(eth0): set_wep_key: key length to set was zero
[ 1159.121625] airo(eth0): failed to set WEP key at index 1: -1.
[ 1159.121673] airo(eth0): set_wep_key: key length to set was zero
[ 1159.121681] airo(eth0): failed to set WEP key at index 2: -1.
[ 1159.121727] airo(eth0): set_wep_key: key length to set was zero
[ 1159.121736] airo(eth0): failed to set WEP key at index 3: -1.
[ 1161.879338] airo(eth0): set_wep_key: key length to set was zero
[ 1161.879356] airo(eth0): failed to set WEP key at index 0: -1.
[ 1161.879525] airo(eth0): set_wep_key: key length to set was zero
[ 1161.879534] airo(eth0): failed to set WEP key at index 1: -1.
[ 1161.879581] airo(eth0): set_wep_key: key length to set was zero
[ 1161.879590] airo(eth0): failed to set WEP key at index 2: -1.
[ 1161.879636] airo(eth0): set_wep_key: key length to set was zero
[ 1161.879644] airo(eth0): failed to set WEP key at index 3: -1.
[ 1180.129764] airo(eth0): set_wep_key: key length to set was zero
[ 1180.129782] airo(eth0): failed to set WEP key at index 0: -1.
[ 1180.129924] airo(eth0): set_wep_key: key length to set was zero
[ 1180.129932] airo(eth0): failed to set WEP key at index 1: -1.
[ 1180.129981] airo(eth0): set_wep_key: key length to set was zero
[ 1180.129989] airo(eth0): failed to set WEP key at index 2: -1.
[ 1180.130035] airo(eth0): set_wep_key: key length to set was zero
[ 1180.130044] airo(eth0): failed to set WEP key at index 3: -1.
[ 1185.167192] airo(eth0): set_wep_key: key length to set was zero
[ 1185.167210] airo(eth0): failed to set WEP key at index 0: -1.
[ 1185.167353] airo(eth0): set_wep_key: key length to set was zero
[ 1185.167361] airo(eth0): failed to set WEP key at index 1: -1.
[ 1185.167410] airo(eth0): set_wep_key: key length to set was zero
[ 1185.167418] airo(eth0): failed to set WEP key at index 2: -1.
[ 1185.167465] airo(eth0): set_wep_key: key length to set was zero
[ 1185.167473] airo(eth0): failed to set WEP key at index 3: -1.
[ 1190.205510] airo(eth0): set_wep_key: key length to set was zero
[ 1190.205528] airo(eth0): failed to set WEP key at index 0: -1.
[ 1190.205668] airo(eth0): set_wep_key: key length to set was zero
[ 1190.205677] airo(eth0): failed to set WEP key at index 1: -1.
[ 1190.205725] airo(eth0): set_wep_key: key length to set was zero
[ 1190.205734] airo(eth0): failed to set WEP key at index 2: -1.
[ 1190.205780] airo(eth0): set_wep_key: key length to set was zero
[ 1190.205788] airo(eth0): failed to set WEP key at index 3: -1.
[ 1195.243797] airo(eth0): set_wep_key: key length to set was zero
[ 1195.243815] airo(eth0): failed to set WEP key at index 0: -1.
[ 1195.243955] airo(eth0): set_wep_key: key length to set was zero
[ 1195.243964] airo(eth0): failed to set WEP key at index 1: -1.
[ 1195.246057] airo(eth0): set_wep_key: key length to set was zero
[ 1195.246073] airo(eth0): failed to set WEP key at index 2: -1.
[ 1195.246202] airo(eth0): set_wep_key: key length to set was zero
[ 1195.246210] airo(eth0): failed to set WEP key at index 3: -1.
[ 1200.284371] airo(eth0): set_wep_key: key length to set was zero
[ 1200.284389] airo(eth0): failed to set WEP key at index 0: -1.
[ 1200.284531] airo(eth0): set_wep_key: key length to set was zero
[ 1200.284540] airo(eth0): failed to set WEP key at index 1: -1.
[ 1200.284588] airo(eth0): set_wep_key: key length to set was zero
[ 1200.284597] airo(eth0): failed to set WEP key at index 2: -1.
[ 1200.284643] airo(eth0): set_wep_key: key length to set was zero
[ 1200.284651] airo(eth0): failed to set WEP key at index 3: -1.
[ 1205.325025] airo(eth0): set_wep_key: key length to set was zero
[ 1205.325043] airo(eth0): failed to set WEP key at index 0: -1.
[ 1205.325185] airo(eth0): set_wep_key: key length to set was zero
[ 1205.325193] airo(eth0): failed to set WEP key at index 1: -1.
[ 1205.325242] airo(eth0): set_wep_key: key length to set was zero
[ 1205.325250] airo(eth0): failed to set WEP key at index 2: -1.
[ 1205.325296] airo(eth0): set_wep_key: key length to set was zero
[ 1205.325305] airo(eth0): failed to set WEP key at index 3: -1.
[ 1210.363275] airo(eth0): set_wep_key: key length to set was zero
[ 1210.363293] airo(eth0): failed to set WEP key at index 0: -1.
[ 1210.363434] airo(eth0): set_wep_key: key length to set was zero
[ 1210.363443] airo(eth0): failed to set WEP key at index 1: -1.
[ 1210.363491] airo(eth0): set_wep_key: key length to set was zero
[ 1210.363500] airo(eth0): failed to set WEP key at index 2: -1.
[ 1210.363546] airo(eth0): set_wep_key: key length to set was zero
[ 1210.363554] airo(eth0): failed to set WEP key at index 3: -1.
[ 1215.401682] airo(eth0): set_wep_key: key length to set was zero
[ 1215.401700] airo(eth0): failed to set WEP key at index 0: -1.
[ 1215.401841] airo(eth0): set_wep_key: key length to set was zero
[ 1215.401850] airo(eth0): failed to set WEP key at index 1: -1.
[ 1215.401898] airo(eth0): set_wep_key: key length to set was zero
[ 1215.401906] airo(eth0): failed to set WEP key at index 2: -1.
[ 1215.401952] airo(eth0): set_wep_key: key length to set was zero
[ 1215.401961] airo(eth0): failed to set WEP key at index 3: -1.
[ 1220.444579] airo(eth0): set_wep_key: key length to set was zero
[ 1220.444597] airo(eth0): failed to set WEP key at index 0: -1.
[ 1220.444739] airo(eth0): set_wep_key: key length to set was zero
[ 1220.444748] airo(eth0): failed to set WEP key at index 1: -1.
[ 1220.444796] airo(eth0): set_wep_key: key length to set was zero
[ 1220.444804] airo(eth0): failed to set WEP key at index 2: -1.
[ 1220.444850] airo(eth0): set_wep_key: key length to set was zero
[ 1220.444858] airo(eth0): failed to set WEP key at index 3: -1.
[ 1225.487511] airo(eth0): set_wep_key: key length to set was zero
[ 1225.487529] airo(eth0): failed to set WEP key at index 0: -1.
[ 1225.487670] airo(eth0): set_wep_key: key length to set was zero
[ 1225.487678] airo(eth0): failed to set WEP key at index 1: -1.
[ 1225.487726] airo(eth0): set_wep_key: key length to set was zero
[ 1225.487734] airo(eth0): failed to set WEP key at index 2: -1.
[ 1225.487780] airo(eth0): set_wep_key: key length to set was zero
[ 1225.487788] airo(eth0): failed to set WEP key at index 3: -1.
[ 1230.530251] airo(eth0): set_wep_key: key length to set was zero
[ 1230.530268] airo(eth0): failed to set WEP key at index 0: -1.
[ 1230.530411] airo(eth0): set_wep_key: key length to set was zero
[ 1230.530419] airo(eth0): failed to set WEP key at index 1: -1.
[ 1230.530467] airo(eth0): set_wep_key: key length to set was zero
[ 1230.530475] airo(eth0): failed to set WEP key at index 2: -1.
[ 1230.530523] airo(eth0): set_wep_key: key length to set was zero
[ 1230.530531] airo(eth0): failed to set WEP key at index 3: -1.
[ 1234.912630] airo(eth0): set_wep_key: key length to set was zero
[ 1234.912651] airo(eth0): failed to set WEP key at index 0: -1.
[ 1234.912882] airo(eth0): set_wep_key: key length to set was zero
[ 1234.912891] airo(eth0): failed to set WEP key at index 1: -1.
[ 1234.912945] airo(eth0): set_wep_key: key length to set was zero
[ 1234.912954] airo(eth0): failed to set WEP key at index 2: -1.
[ 1234.913001] airo(eth0): set_wep_key: key length to set was zero
[ 1234.913009] airo(eth0): failed to set WEP key at index 3: -1.
[ 1515.469410] airo(eth0): link lost (local choice)
[ 1515.487746] airo(eth0): set_wep_key: key length to set was zero
[ 1515.487764] airo(eth0): failed to set WEP key at index 0: -1.
[ 1515.487914] airo(eth0): set_wep_key: key length to set was zero
[ 1515.487922] airo(eth0): failed to set WEP key at index 1: -1.
[ 1515.487972] airo(eth0): set_wep_key: key length to set was zero
[ 1515.487980] airo(eth0): failed to set WEP key at index 2: -1.
[ 1515.488083] airo(eth0): set_wep_key: key length to set was zero
[ 1515.488092] airo(eth0): failed to set WEP key at index 3: -1.
[ 1515.488140] airo(eth0): set_wep_key: key length to set was zero
[ 1515.488148] airo(eth0): failed to set WEP key at index 0: -1.
[ 1540.817901] airo(eth0): link lost (local choice)
[ 1540.837064] airo(eth0): set_wep_key: key length to set was zero
[ 1540.837083] airo(eth0): failed to set WEP key at index 0: -1.
[ 1540.837239] airo(eth0): set_wep_key: key length to set was zero
[ 1540.837248] airo(eth0): failed to set WEP key at index 1: -1.
[ 1540.837296] airo(eth0): set_wep_key: key length to set was zero
[ 1540.837304] airo(eth0): failed to set WEP key at index 2: -1.
[ 1540.837351] airo(eth0): set_wep_key: key length to set was zero
[ 1540.837359] airo(eth0): failed to set WEP key at index 3: -1.
[ 1540.837406] airo(eth0): set_wep_key: key length to set was zero
[ 1540.837414] airo(eth0): failed to set WEP key at index 0: -1.

---

### Post by chili555 on 2010-02-12
> set_wep_key: key length to set was zeroIs Network Manager asking for a WEP key? Are you supplying the correct key? What does this tell us?```
sudo iwlist eth1 scan
```Thanks.

---

### Post by andrewjoint on 2010-02-14
sorry for late....

i done your  code but....

interface doesnt support scanning


i iinstalled driver wireless of windows...the connection now in active but if i put a wpa key don't connect...

the he answer me always the wpa key but is not connect....

SORRY FOR MY ENGLISH..

---

### Post by chili555 on 2010-02-14
Now that you have installed the Windows drivers, is your wireless interface now wlan0? Find out with:```
iwconfig
```Let's see if your card actually supports WPA. Please do:```
sudo iwlist wlan0 auth
```If your card can do WPA, you should get something like this:> wlan0     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMPYour English is just fine.

---

### Post by andrewjoint on 2010-02-14
andrew@andrew-laptop:~$ iwconfig
lo        no wireless extensions.

wlan21    IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

andrew@andrew-laptop:~$ sudo iwlist wlan21 auth
[sudo] password for andrew: 
wlan21    Authentication capabilities :
        WPA
        CIPHER-TKIP
          Current WPA version :
        WPA
          Current Key management :
        PSK
          Current Pairwise cipher :
        none
          Current Pairwise cipher :
        none
          Current Authentication algorithm :
        open


andrew@andrew-laptop:~$ 




this is a message


i'm active now?...but if i put a "wpa" he answer me continously the key

---

