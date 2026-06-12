---
title: "getting started my dvbworld 2006 pci e in ubuntu"
date: 2011-11-20
forum: Multimedia Software
---

### Post by vishvish on 2011-11-20
hello experts , hi to everyone

i am new to linux . I am not getting started my dw2006 card . 

What all i need to be installed . I installed ubuntu 11.10 . 

I tred to copy dvb-fe-ds3000.fw to /lib/firmware/

i tryied to install s2-lipiainin . From web page .transcation aborting . Dont know ?

If i try to install from .gz file it takes files 

but card is not detecting in me tv 

please any one help me to get install my card from scrach

thanks

---

### Post by vishvish on 2011-11-21
come on guys . Please help me .

---

### Post by vishvish on 2011-11-26
hello . finally i have installed s2-liplianin drivers in ubuntu 10.04 LTS , with kernel 2.6.32 genric, my card detected but still not tuning , hope any one take a look at logs and give give ideas



dmesg
```

18.468981] smi2032 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.468992] smi2032 0000:02:00.0: setting latency timer to 64
[   18.469012] smi2032_probe: pci_resource_start = 93100000
[   18.469015] smi2032_probe: pci_resource_len = 1000
[   18.469132] smi_cfg_dma_B(): Config PCIE port B, DMA channel0
[   18.469136] smi_cfg_dma_B(): DMA memory low  address = 0x338C0000
[   18.469139] smi_cfg_dma_B(): DMA memory high address = 0x00000000
[   18.469143] smi_cfg_dma_B(): DMA memory control register = 0x11C2F000
[   18.469146] smi_cfg_dma_B(): DMA memory management = 0x00000003
[   18.469154] smi2032_hw_init: i2c_sw_ctl 32c8, 
[   18.469161] smi2032_hw_init: pci config 0x1ade
[   18.469436] DVB: registering new adapter (smi2032)
[   18.483285] parport_pc 00:07: reported by Plug and Play ACPI
[   18.483315] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   18.605740] ppdev: user-space parallel port driver
[   18.672875] lp0: using parport0 (interrupt-driven).
[   18.691083] Console: switching to colour frame buffer device 80x30
[   18.719095] DS3000 chip version: 0.192 attached.
[   18.719103] DVB: registering adapter 0 frontend 0 (Montage Technology DS3000/TS2020)...

dmesg | grep ds3000

[   30.171378] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
[   30.171390] smi2032 0000:02:00.0: firmware: requesting dvb-fe-ds3000.fw
[   30.218407] ds3000_firmware_ondemand: Waiting for firmware upload(2)...
[   30.232676] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.248533] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.264539] ds3000_writeFW: write error(err == -1, reg == 0xb0

continues


dmesg | grep firmware


[   18.408700] intel_rng: don't want to disable this in firmware setup, and if
[   30.171378] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
[   30.171390] smi2032 0000:02:00.0: firmware: requesting dvb-fe-ds3000.fw
[   30.218407] ds3000_firmware_ondemand: Waiting for firmware upload(2)...


lspci -vvv

02:00.0 Multimedia video controller: Spin Master Ltd. Device 2032 (rev 01)
    Subsystem: Spin Master Ltd. Device 1234
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at 93100000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: smi2032
    Kernel modules: smi2032


dmesg | grep -i dvb


[   18.469436] DVB: registering new adapter (smi2032)
[   18.719103] DVB: registering adapter 0 frontend 0 (Montage Technology DS3000/TS2020)...
[   30.171378] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
[   30.171390] smi2032 0000:02:00.0: firmware: requesting dvb-fe-ds3000.fw
[  803.459359] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
[  803.459370] smi2032 0000:02:00.0: firmware: requesting dvb-fe-ds3000.fw
[ 1167.426335] DVB: adapter 0 frontend 0 frequency 100470000 out of range (950000..2150000)



lsmod


Module                  Size  Used by
binfmt_misc             6587  1 
rfcomm                 33421  4 
sco                     7917  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  3 
l2cap                  30624  18 rfcomm,bnep
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
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
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ds3000                 12623  1 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
parport_pc             25962  1 
smi2032                11596  0 
intel_agp              24375  0 
btusb                  11053  4 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
lp                      7028  0 
soundcore               6620  1 snd
psmouse                63677  0 
serio_raw               3978  0 
nvidia               9961216  28 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
dvb_core               86202  1 smi2032
agpgart                31724  2 intel_agp,nvidia
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  3 ppdev,parport_pc,lp
usb_storage            39841  1 
e100                   28211  0 
mii                     4381  1 e100


ls -l  /lib/firmware/

total 13556
drwxr-xr-x 32 root root    4096 2011-07-19 17:39 2.6.32-33-generic
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 3com
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 acenic
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 adaptec
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 advansys
-rw-r--r--  1 root root   50698 2010-12-14 21:55 agere_ap_fw.bin
-rw-r--r--  1 root root   65046 2010-12-14 21:55 agere_sta_fw.bin
-rw-r--r--  1 root root   22622 2010-12-14 21:56 aic94xx-seq.fw
-rw-r--r--  1 root root   70624 2011-02-18 23:31 ar7010_1_1.fw
-rw-r--r--  1 root root   83968 2010-12-14 21:55 ar9170-1.fw
-rw-r--r--  1 root root    3508 2010-12-14 21:55 ar9170-2.fw
-rw-r--r--  1 root root   15960 2010-12-14 21:56 ar9170.fw
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 asihpi
-rw-r--r--  1 root root  246804 2010-12-14 21:55 ath3k-1.fw
-rw-r--r--  1 root root   30348 2010-12-14 21:56 atmel_at76c502_3com.bin
-rw-r--r--  1 root root   31764 2010-12-14 21:56 atmel_at76c502.bin
-rw-r--r--  1 root root   31764 2010-12-14 21:56 atmel_at76c502d.bin
-rw-r--r--  1 root root   31776 2010-12-14 21:56 atmel_at76c502e.bin
-rw-r--r--  1 root root   35180 2010-12-14 21:56 atmel_at76c504_2958.bin
-rw-r--r--  1 root root   39928 2010-12-14 21:56 atmel_at76c504a_2958.bin
-rw-r--r--  1 root root   31748 2010-12-14 21:56 atmel_at76c504.bin
-rw-r--r--  1 root root   31824 2010-12-14 21:56 atmel_at76c506.bin
-rw-r--r--  1 root root    9726 2010-12-14 21:55 atmsar11.fw
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 av7110
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 bnx2
-rw-r--r--  1 root root  165768 2010-12-14 21:55 bnx2x-e1-4.8.53.0.fw
-rw-r--r--  1 root root  162800 2010-12-14 21:55 bnx2x-e1-5.2.7.0.fw
-rw-r--r--  1 root root  192400 2010-12-14 21:55 bnx2x-e1h-4.8.53.0.fw
-rw-r--r--  1 root root  205488 2010-12-14 21:55 bnx2x-e1h-5.2.7.0.fw
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 cis
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 cpia2
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 cxgb3
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 dabusb
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 dsp56k
-rw-r--r--  1 root root    2285 2011-11-24 20:56 dvb-fe-bcm3510-01.fw
**-rw-r--r--  1 root root    8192 2011-11-26 19:27 dvb-fe-ds3000.fw**
-rw-r--r--  1 root root   12772 2011-11-24 20:56 dvb-fe-or51132-qam.fw
-rw-r--r--  1 root root   17532 2011-11-24 20:56 dvb-fe-or51132-vsb.fw
-rw-r--r--  1 root root    8518 2011-11-24 20:56 dvb-fe-or51211.fw
-rw-r--r--  1 root root   12401 2011-11-24 20:56 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root  226460 2011-11-24 20:56 dvb-ttpci-01.fw-261a
-rw-r--r--  1 root root  226408 2011-11-24 20:56 dvb-ttpci-01.fw-261b
-rw-r--r--  1 root root  226376 2011-11-24 20:56 dvb-ttpci-01.fw-261c
-rw-r--r--  1 root root  231952 2011-11-24 20:56 dvb-ttpci-01.fw-261d
-rw-r--r--  1 root root  234284 2011-11-24 20:56 dvb-ttpci-01.fw-261f
-rw-r--r--  1 root root  239956 2011-11-24 20:56 dvb-ttpci-01.fw-2622
-rw-r--r--  1 root root   10757 2011-11-24 20:56 dvb-usb-avertv-a800-02.fw
-rw-r--r--  1 root root    9025 2011-11-24 20:56 dvb-usb-bluebird-01.fw
-rw-r--r--  1 root root   33768 2011-11-24 20:56 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root    9180 2011-11-24 20:56 dvb-usb-dibusb-5.0.0.11.fw
-rw-r--r--  1 root root    7558 2011-11-24 20:56 dvb-usb-dibusb-6.0.0.8.fw
-rw-r--r--  1 root root    7431 2011-11-24 20:56 dvb-usb-dtt200u-01.fw
-rw-r--r--  1 root root   50222 2011-11-24 20:56 dvb-usb-terratec-h5-drxk.fw
-rw-r--r--  1 root root    8832 2011-11-24 20:56 dvb-usb-terratec-h7-az6007.fw
-rw-r--r--  1 root root    7770 2011-11-24 20:56 dvb-usb-terratec-h7-drxk.fw
-rw-r--r--  1 root root    4286 2011-11-24 20:56 dvb-usb-umt-010-02.fw
-rw-r--r--  1 root root   10752 2011-11-24 20:56 dvb-usb-vp702x-01.fw
-rw-r--r--  1 root root   10752 2011-11-24 20:56 dvb-usb-vp7045-01.fw
-rw-r--r--  1 root root    8581 2011-11-24 20:56 dvb-usb-wt220u-01.fw
-rw-r--r--  1 root root    8480 2011-11-24 20:56 dvb-usb-wt220u-02.fw
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 e100
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 ea
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 edgeport
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 emi26
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 emi62
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 ess
-rw-r--r--  1 root root 1142480 2010-12-14 21:56 i2400m-fw-usb-1.3.sbcf
-rw-r--r--  1 root root 1251036 2010-12-14 21:55 i2400m-fw-usb-1.4.sbcf
-rw-r--r--  1 root root   34304 2010-12-14 21:55 intelliport2.bin
-rw-r--r--  1 root root  209190 2010-12-14 21:56 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 2010-12-14 21:56 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 2010-12-14 21:56 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 2010-12-14 21:56 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 2010-12-14 21:56 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 2010-12-14 21:56 ipw2200-sniffer.fw
-rw-r--r--  1 root root  335056 2010-12-14 21:55 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  150100 2010-12-14 21:55 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 2010-12-14 21:55 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2010-12-14 21:55 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2010-12-14 21:55 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  340696 2011-03-03 21:30 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root  337400 2010-12-14 21:55 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  462280 2010-12-14 21:55 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 2011-02-11 19:56 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  460912 2011-02-11 19:56 iwlwifi-6000g2b-5.ucode
-rw-r--r--  1 root root  463692 2011-03-03 21:30 iwlwifi-6050-4.ucode
-rw-r--r--  1 root root  469780 2010-12-14 21:56 iwlwifi-6050-5.ucode
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 kaweth
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 keyspan
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 keyspan_pda
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 korg
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 libertas
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 matrox
-rw-r--r--  1 root root   13847 2010-12-14 21:55 mts_cdma.fw
-rw-r--r--  1 root root   14067 2010-12-14 21:55 mts_edge.fw
-rw-r--r--  1 root root   13847 2010-12-14 21:55 mts_gsm.fw
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 mwl8k
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 myricom
-rw-r--r--  1 root root   15664 2010-12-14 21:56 NPE-B
-rw-r--r--  1 root root   15664 2010-12-14 21:56 NPE-C
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 ositech
-rw-r--r--  1 root root   76802 2010-12-14 21:55 ql2100_fw.bin
-rw-r--r--  1 root root   84566 2010-12-14 21:55 ql2200_fw.bin
-rw-r--r--  1 root root  123170 2010-12-14 21:55 ql2300_fw.bin
-rw-r--r--  1 root root  132978 2010-12-14 21:55 ql2322_fw.bin
-rw-r--r--  1 root root  228056 2010-12-14 21:55 ql2400_fw.bin
-rw-r--r--  1 root root  199776 2010-12-14 21:55 ql2500_fw.bin
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 qlogic
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 r128
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 radeon
-rw-r--r--  1 root root    8192 2010-12-14 21:55 rt2561.bin
-rw-r--r--  1 root root    8192 2010-12-14 21:55 rt2561s.bin
-rw-r--r--  1 root root    8192 2010-12-14 21:55 rt2661.bin
-rw-r--r--  1 root root    8192 2010-12-14 21:55 rt2860.bin
-rw-r--r--  1 root root    4096 2010-12-14 21:55 rt2870.bin
-rw-r--r--  1 root root    4096 2010-12-14 21:55 rt3070.bin
-rw-r--r--  1 root root    4096 2010-12-14 21:55 rt3071.bin
-rw-r--r--  1 root root    2048 2010-12-14 21:55 rt73.bin
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 RTL8192E
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 RTL8192SE
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 sb16
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 scripts
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 slicoss
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 sun
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 sxg
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 tehuti
-rw-r--r--  1 root root   13765 2010-12-14 21:55 ti_3410.fw
-rw-r--r--  1 root root   13764 2010-12-14 21:55 ti_5052.fw
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 tigon
-rw-r--r--  1 root root    7614 2010-12-14 21:55 tr_smctr.bin
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 ttusb-budget
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 usbdux
-rw-r--r--  1 root root     999 2010-12-14 21:55 usbduxfast_firmware.bin
-rw-r--r--  1 root root    1770 2010-12-14 21:55 usbdux_firmware.bin
-rw-r--r--  1 root root   16382 2011-11-24 20:56 v4l-cx231xx-avcore-01.fw
-rw-r--r--  1 root root  141200 2011-11-24 20:56 v4l-cx23418-apu.fw
-rw-r--r--  1 root root  158332 2011-11-24 20:56 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root   16382 2011-11-24 20:56 v4l-cx23418-dig.fw
-rw-r--r--  1 root root  262144 2010-12-14 21:56 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root  376836 2010-12-14 21:56 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root  155648 2010-12-14 21:56 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root   16382 2011-11-24 20:56 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root   16382 2011-11-24 20:56 v4l-cx23885-enc.fw
-rw-r--r--  1 root root   16382 2011-11-24 20:56 v4l-cx25840.fw
-rw-r--r--  1 root root    8192 2010-12-14 21:56 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root    8192 2010-12-14 21:56 v4l-pvrusb2-29xxx-01.fw
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 vicam
-rw-r--r--  1 root root   23554 2010-12-14 21:55 whiteheat.fw
-rw-r--r--  1 root root    5626 2010-12-14 21:55 whiteheat_loader.fw
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 yam
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 yamaha
-rw-r--r--  1 root root   62484 2010-12-14 21:56 zd1201-ap.fw
-rw-r--r--  1 root root   70612 2010-12-14 21:56 zd1201.fw
drwxr-xr-x  2 root root    4096 2011-07-19 17:44 zd1211

dmesg | grep dvb

[   30.171378] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
[   30.171390] smi2032 0000:02:00.0: firmware: requesting dvb-fe-ds3000.fw
dmesg | grep ds3000
[   30.171378] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
[   30.171390] smi2032 0000:02:00.0: firmware: requesting dvb-fe-ds3000.fw
[   30.218407] ds3000_firmware_ondemand: Waiting for firmware upload(2)...
[   30.232676] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.248533] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.264539] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.280538] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.300525] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.317245] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.332545] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.348569] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.364559] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.380630] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.396539] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.412535] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.430609] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.444528] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.460531] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.476553] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.492529] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.508529] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.524530] ds3000_writeFW: write error(err == -1, reg == 0xb0
[   30.540529] ds3000_writeFW: write error(err == -1, reg == 0xb0

```

modprobe ds3000

nothing happens 
 
dvbtune

dvbtune -f 12522000 -p v -s 40700 -d 1 -m
Using DVB card "Montage Technology DS3000/TS2020"
tuning DVB-S to L-Band:134513994, Pol:V Srate=40700000, 22kHz=off
polling....
Getting frontend event
FE_STATUS:
polling....
polling....
polling....
polling....
polling....
polling....
polling....
polling....

continues 



i really not understanding how to get start 

thanks

---

### Post by vishvish on 2011-11-26
dvbtune -c3 -f 12522000 -p v -s 40700 -d 1 -m

Signal=65000, Verror=0, SNR=57640dB, BlockErrors=0, ()
Signal=65000, Verror=-1, SNR=57640dB, BlockErrors=0, ()
Signal=65000, Verror=-1, SNR=57640dB, BlockErrors=0, ()
Signal=65000, Verror=-1, SNR=15720dB, BlockErrors=0, ()
Signal=65000, Verror=-1, SNR=15720dB, BlockErrors=0, ()


is this ok?


dvbtune -c3 -f 12522000 -p v -s 40700 -d 1 -m 2>/dev/null &[2] 2668
rock@rock-desktop:~$ scan -c -U
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
dumping lists (0 services)
Done.
[2]+  Exit 255                dvbtune -c3 -f 12522000 -p v -s 40700 -d 1 -m 2> /dev/null


what to do ?

---

### Post by vishvish on 2011-11-28
ls -l /dev/dvb/

total 0
drwxr-xr-x 2 root root 120 2011-11-28 15:18 adapter0



ls -l /dev/dvb/adapter0


total 0
crw-rw----+ 1 root video 212, 0 2011-11-28 15:18 demux0
crw-rw----+ 1 root video 212, 1 2011-11-28 15:18 dvr0
crw-rw----+ 1 root video 212, 2 2011-11-28 15:18 frontend0
crw-rw----+ 1 root video 212, 3 2011-11-28 15:18 net0

dvbtune
dvbtune -f 12522000 -p v -s 40700 -d 1 -m
dvbtune -f 12522000 -p v -s 40700 -d 1 -m
Using DVB card "Montage Technology DS3000/TS2020"
tuning DVB-S to L-Band:134513994, Pol:V Srate=40700000, 22kHz=off
polling....
Getting frontend event
FE_STATUS:
polling....
polling....



if i try kaffine ,tuning dvb s 


i get these error messges  dmesges

polling....
polling....dmesg | grep ds3000
[  740.587055] ds3000_firmware_ondemand: Waiting for firmware upload (dvb-fe-ds3000.fw)...
[  740.587068] smi2032 0000:02:00.0: firmware: requesting dvb-fe-ds3000.fw
[  740.642472] ds3000_firmware_ondemand: Waiting for firmware upload(2)...
[  740.656521] ds3000_writeFW: write error(err == -1, reg == 0xb0
[  740.672518] ds3000_writeFW: write error(err == -1, reg == 0xb0
[  740.688517] ds3000_writeFW: write error(err == -1, reg == 0xb0
[  740.704018] ds3000_writeFW: write error(err == -1, reg == 0xb0
[  740.720016] ds3000_writeFW: write error(err == -1, reg == 0xb0
[  740.736015] ds3000_writeFW: write error(err == -1, reg == 0xb0
[  740.752021] ds3000_writeFW: write error(err == -1, reg == 0xb0
[  740.768016] ds3000_writeFW: write error(err == -1, reg == 0xb0
[  740.784015] ds3000_writeFW: write error(err == -1, reg == 0xb0
[  740.800025] ds3000_writeFW: write error(err == -1, reg == 0xb0
[  740.816015] ds3000_writeFW: write error(err == -1, reg == 0xb0
[  745.232018] ds3000_writereg: writereg error(err == -1, reg == 0x03, value == 0x11)
[  745.252019] ds3000_writereg: writereg error(err == -1, reg == 0x03, value == 0x11)
[  745.284022] ds3000_writereg: writereg error(err == -1, reg == 0x03, value == 0x12)
[  745.304018] ds3000_tuner_readreg: reg=0x3d(error=-1)
[  745.320016] ds3000_writereg: writereg error(err == -1, reg == 0x03, value == 0x11)
[  745.336016] ds3000_tuner_writereg: writereg error(err == -1, reg == 0x60, value == 0x0f)

ls -l /dev/v4l

ls: cannot access /dev/v4l: No such file or directory

ls -l /dev/video

ls: cannot access /dev/video: No such file or directory

. although i installed s2-liplianin in ubuntu kernel 2.6.33 genric 

thanks

---

