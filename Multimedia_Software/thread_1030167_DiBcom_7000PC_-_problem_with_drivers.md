---
title: "DiBcom 7000PC - problem with drivers"
date: 2009-01-04
forum: Multimedia Software
---

### Post by le0pard on 2009-01-04
Hello to all!:D
I have some problem with my Asus A7Sv. On Ubuntu 8.10 all work excelent, except TV-tuner.
I install driver by [this manual]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers"), and it find by my system:
```
#dmesg
...
dib0700: loaded with support for 8 different device-types                                                                                                     
[   21.329266] dvb-usb: found a 'YUAN High-Tech STK7700PH' in warm state.                                                                                                    
[   21.329355] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.                                                                               
[   21.329654] DVB: registering new adapter (YUAN High-Tech STK7700PH)                                                                                                       
[   21.514051] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...                                                                                                      
[   21.581167] xc2028 1-0061: creating new instance                                                                                                                          
[   21.581215] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner                                                                                                         
[   21.581265] dvb-usb: YUAN High-Tech STK7700PH successfully initialized and connected.                                                                                     
[   21.581423] usbcore: registered new interface driver dvb_usb_dib0700                
...
```

Next for me need will be xc3028-v27.fw. I build it using [this manual]("http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028#How_to_Obtain_the_Firmware"), and have this message in dmesg and /var/log/messages:
```
...
[ 1057.561318] xc2028 1-0061: Error on line 1122: -5
[ 1074.531589] firmware: requesting xc3028-v27.fw
[ 1074.564647] xc2028 1-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[ 1074.587340] xc2028 1-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[ 1074.619343] xc2028 1-0061: i2c output error: rc = -5 (should be 64)
[ 1074.619355] xc2028 1-0061: -5 returned from send
[ 1074.619363] xc2028 1-0061: Error -22 while loading base firmware
[ 1074.695338] xc2028 1-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[ 1074.727344] xc2028 1-0061: i2c output error: rc = -5 (should be 64)
[ 1074.727357] xc2028 1-0061: -5 returned from send
...
```

P.S.
May be (I don't sure) it error with xc3028-v27.fw (it doesn't have my drivers),
I have dvb7700all.sys (with my drivers for Windows Vista), but doesn't known how convert this to *.fw file.
I attach dvb7700all.sys and xc3028-v27.fw.

Will be grateful for any assistance.:D

---

