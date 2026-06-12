---
title: "can't get wireless connection with broadcom bcm4312"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by leon.alberti on 2013-03-25
The title pretty much says it.

All the useful information:

> prospero@tempest:~$ lspci -nn | grep Broadcom
10:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
prospero@tempest:~$ ifconfig
eth0      Link encap:Ethernet  Endereço de HW 00:1e:ec:2f:26:00  
          inet end.: 192.168.0.102  Bcast:192.168.0.255  Masc:255.255.255.0
          endereço inet6: fe80::21e:ecff:fe2f:2600/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:6719 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:5872 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:6309886 (6.3 MB) TX bytes:746599 (746.5 KB)


lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:1104 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:1104 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:94006 (94.0 KB) TX bytes:94006 (94.0 KB)


prospero@tempest:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


prospero@tempest:~$ lsmod
Module                  Size  Used by
snd_hrtimer            12649  1 
joydev                 17162  0 
coretemp               13169  0 
hp_wmi                 13617  0 
sparse_keymap          13659  1 hp_wmi
snd_hda_codec_conexant    52203  1 
pcmcia                 39545  0 
snd_hda_intel          32516  2 
snd_hda_codec         111548  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
microcode              18210  0 
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
psmouse                84878  0 
lpc_ich                16926  0 
snd_seq_midi_event     14476  1 snd_seq_midi
serio_raw              13032  0 
b43                   347311  0 
yenta_socket           27096  0 
pcmcia_rsrc            18192  1 yenta_socket
pcmcia_core            21506  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq                51281  3 snd_seq_midi,snd_seq_midi_event
mac80211              461203  1 b43
snd_timer              24412  3 snd_hrtimer,snd_pcm,snd_seq
i915                  457247  3 
bnep                   17708  0 
cfg80211              175574  2 b43,mac80211
rfcomm                 37277  0 
parport_pc             31969  0 
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
bcma                   34484  1 b43
ppdev                  12818  0 
bluetooth             183270  4 bnep,rfcomm
drm_kms_helper         47304  1 i915
drm                   238811  4 i915,drm_kms_helper
binfmt_misc            17261  1 
snd                    62146  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13198  1 i915
wmi                    18591  1 hp_wmi
mac_hid                13038  0 
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
video                  18848  1 i915
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
e100                   35904  0 
ssb                    50088  1 b43


prospero@tempest:~$ sudo lshw -C network
  *-network               
       descrição: Network controller
       produto: BCM4312 802.11b/g LP-PHY
       fabricante: Broadcom Corporation
       physical id: 0
       informações do barramento: pci@0000:10:00.0
       versão: 01
       largura: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuração: driver=b43-pci-bridge latency=0
       recursos: irq:17 memória:f0000000-f0003fff
  *-network
       descrição: Ethernet interface
       produto: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       fabricante: Intel Corporation
       physical id: 8
       informações do barramento: pci@0000:02:08.0
       nome lógico: eth0
       versão: 01
       serial: 00:1e:ec:2f:26:00
       tamanho: 100Mbit/s
       capacidade: 100Mbit/s
       largura: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuração: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.0.102 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       recursos: irq:20 memória:f0101000-f0101fff ioport:2000(tamanho=64)


I know the wireless itself is working because I could get it working with windows.
I appreciate any help.

---

### Post by wildmanne39 on 2013-03-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by leon.alberti on 2013-03-25
Thank you for the fast reply, Wild man.

---

### Post by wildmanne39 on 2013-03-25
Hi, you are missing the firmware.
Please do:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
```
sudo modprobe b43
```
Thanks

---

### Post by leon.alberti on 2013-03-25
Thank you, it's working (altough it's giving erros messages when connecting).
Marking as solved.

---

### Post by wildmanne39 on 2013-03-25
What error messages? from where?
Thanks

---

### Post by leon.alberti on 2013-03-25
Strangely it only appeared the first time I connected, it was something related to user privilege.
Anyway, it's working perfect now. Danke!

---

### Post by wildmanne39 on 2013-03-25
Your welcome!

---

