---
title: "ralink 2500 &amp; Master Mode"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by metacortex88 on 2009-02-12
Hey guys, 

I have read that the ralink 2500 drivers should work out of the box but I cant quite get them working. I need to be able to put the card in master mode  but it is not working. (fresh install of Ibex i386)

```

x@x:/usr/src$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8T890 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
**00:0a.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)**
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7800 GTX] (rev a1)

```

```

x@x:/usr/src$ sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

```

I have installed the rt2500-source packages and have attempted use module-assistant to rebuild and reinstall them but it keeps failing the build with

```

touch config.mk \                      
        && /usr/bin/make clean 
make[1]: Entering directory `/usr/src/modules/rt2500' 
make[1]: Leaving directory `/usr/src/modules/rt2500'
dh_clean 
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules 
make[1]: Entering directory `/usr/src/modules/rt2500' 
touch config.mk \ 
        && /usr/bin/make clean 
make[2]: Entering directory `/usr/src/modules/rt2500' 
make[2]: Leaving directory `/usr/src/modules/rt2500' 
dh_clean 
for templ in ; do \ 
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-11-generic/g'` ; \ 
  done     
for templ in `ls debian/*.modules.in` ; do \ 
     test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} 
${templ%.modules.in}.backup 2>/dev/null || true; \ 
     sed -e 's/##KVERS##/2.6.27-11-generic/g  
;s/#KVERS#/2.6.27-11-generic/g ; s/_KVERS_/2.6.27-11-generic/g ; 
s/##KDREV##/2.6.27-11.27/g ; s/#KDREV#/2.6.27-11.27/g ;
 s/_KDREV_/2.6.27-11.27/g  ' < $templ > ${templ%.modules.in}; \
  done 
# Install module
dh_installdirs lib/modules/2.6.27-11-generic/kernel/drivers/net/wireless
# Build modules
/usr/bin/make KERNDIR=/usr/src/linux PATCHLEVEL=6 
make[2]: Entering directory `/usr/src/modules/rt2500'
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /usr/src/modules/rt2500/rtmp_main.o 
  CC [M]  /usr/src/modules/rt2500/mlme.o
  CC [M]  /usr/src/modules/rt2500/connect.o
  CC [M]  /usr/src/modules/rt2500/sync.o
  CC [M]  /usr/src/modules/rt2500/assoc.o
  CC [M]  /usr/src/modules/rt2500/auth.o
  CC [M]  /usr/src/modules/rt2500/auth_rsp.o
  CC [M]  /usr/src/modules/rt2500/rtmp_data.o 
  CC [M]  /usr/src/modules/rt2500/rtmp_init.o 
  CC [M]  /usr/src/modules/rt2500/sanity.o 
  CC [M]  /usr/src/modules/rt2500/rtmp_wep.o 
  CC [M]  /usr/src/modules/rt2500/wpa.o      
  CC [M]  /usr/src/modules/rt2500/md5.o      
  CC [M]  /usr/src/modules/rt2500/rtmp_tkip.o 
  CC [M]  /usr/src/modules/rt2500/rtmp_info.o 
/usr/src/modules/rt2500/rtmp_info.c: In function ‘rt_ioctl_giwscan’: 
/usr/src/modules/rt2500/rtmp_info.c:494: warning: passing argument 1 of 
‘iwe_stream_add_event’ from incompatible pointer type 
/usr/src/modules/rt2500/rtmp_info.c:494: warning: passing argument 3 of 
‘iwe_stream_add_event’ from incompatible pointer type 
/usr/src/modules/rt2500/rtmp_info.c:494: warning: passing argument 4 of
‘iwe_stream_add_event’ makes pointer from integer without a cast 
/usr/src/modules/rt2500/rtmp_info.c:494: error: too few arguments to 
function ‘iwe_stream_add_event’ 
/usr/src/modules/rt2500/rtmp_info.c:512: warning: passing argument 1 of 
‘iwe_stream_add_event’ from incompatible pointer type 
/usr/src/modules/rt2500/rtmp_info.c:512: warning: passing argument 3 of 
‘iwe_stream_add_event’ from incompatible pointer type 
/usr/src/modules/rt2500/rtmp_info.c:512: warning: passing argument 4 of 
‘iwe_stream_add_event’ makes pointer from integer without a cast 
/usr/src/modules/rt2500/rtmp_info.c:512: error: too few arguments to 
function ‘iwe_stream_add_event’ 
/usr/src/modules/rt2500/rtmp_info.c:518: warning: passing argument 1 of 
'iwe_stream_add_point’ from incompatible pointer type 
/usr/src/modules/rt2500/rtmp_info.c:518: warning: passing argument 3 of 
‘iwe_stream_add_point’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:518: warning: passing argument 4 of
‘iwe_stream_add_point’ from incompatible pointer type 
/usr/src/modules/rt2500/rtmp_info.c:518: error: too few arguments to 
function ‘iwe_stream_add_point’ 
/usr/src/modules/rt2500/rtmp_info.c:526: warning: passing argument 1 of
‘iwe_stream_add_point’ from incompatible pointer type 
/usr/src/modules/rt2500/rtmp_info.c:526: warning: passing argument 3 of
‘iwe_stream_add_point’ from incompatible pointer type 
/usr/src/modules/rt2500/rtmp_info.c:526: warning: passing argument 4 of 
‘iwe_stream_add_point’ from incompatible pointer type 
/usr/src/modules/rt2500/rtmp_info.c:526: error: too few arguments to 
function ‘iwe_stream_add_point’
/usr/src/modules/rt2500/rtmp_info.c:539: warning: passing argument 1 of 
‘iwe_stream_add_value’ from incompatible pointer type 
/usr/src/modules/rt2500/rtmp_info.c:539: warning: passing argument 5 of 
‘iwe_stream_add_value’ makes pointer from integer without a cast 
/usr/src/modules/rt2500/rtmp_info.c:539: error: too few arguments to 
function ‘iwe_stream_add_value’ 
/usr/src/modules/rt2500/rtmp_info.c:550: warning: passing argument 1 of 
iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:550: warning: passing argument 3 of 
iwe_stream_add_event’ from incompatible pointer type 
/usr/src/modules/rt2500/rtmp_info.c:550: warning: passing argument 4 of 
‘iwe_stream_add_event’ makes pointer from integer without a cast  
/usr/src/modules/rt2500/rtmp_info.c:550: error: too few arguments to  
function ‘iwe_stream_add_event’ 
/usr/src/modules/rt2500/rtmp_info.c:562: warning: passing argument 1 of
‘iwe_stream_add_event’ from incompatible pointer type 
/usr/src/modules/rt2500/rtmp_info.c:562: warning: passing argument 3 of 
/usr/src/modules/rt2500/rtmp_info.c:539: warning: passing argument 4 of
‘iwe_stream_add_event’ from incompatible pointer type
/usr/src/modules/rt2500/rtmp_info.c:562: warning: passing argument 4 of
‘iwe_stream_add_event’ makes pointer from integer without a cast
/usr/src/modules/rt2500/rtmp_info.c:562: error: too few arguments to
function ‘iwe_stream_add_event’
make[4]: *** [/usr/src/modules/rt2500/rtmp_info.o] Error 1
make[3]: *** [_module_/usr/src/modules/rt2500] Error 2 
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
rt2500.ko failed to build!
make[2]: *** [module] Error 1
make[2]: Leaving directory `/usr/src/modules/rt2500'
make[1]: *** [binary_modules] Error 2
make[1]: Leaving directory `/usr/src/modules/rt2500'
make: *** [kdist_build] Error 2  
^Y

```

Does anyone have any ideas?

---

### Post by metacortex88 on 2009-02-15
bueller? bueller?

---

