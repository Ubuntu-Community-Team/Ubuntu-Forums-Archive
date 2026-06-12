---
title: "Karmic: Can't build latest pvrusb2 driver"
date: 2009-11-04
forum: Mythbuntu
---

### Post by deadland on 2009-11-04
Dear all,

since I have problems with lirc and my Hauppauge HVR-1950 it try to compile the latest driver, hoping it resolves my problems, but even this doesn't work:

```
make --directory driver
make: Gehe in Verzeichnis '/tmp/pvrusb2-mci-20091031/driver'
make INSTALL_MOD_DIR=pvrusb2 -C /lib/modules/2.6.31-14-generic/build M=/tmp/pvrusb2-mci-20091031/driver CONFIG_VIDEO_PVRUSB2=m CONFIG_VIDEO_PVRUSB2_24XXX=y CONFIG_VIDEO_PVRUSB2_SYSFS=y CONFIG_VIDEO_PVRUSB2_DVB=y CONFIG_VIDEO_PVRUSB2_DEBUGIFC=y CONFIG_VIDEO_ADV_DEBUG=y modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.o
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:42:22: error: tda18271.h: No such file or directory
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:43:21: error: tda8290.h: No such file or directory
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:44:26: error: tuner-simple.h: No such file or directory
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c: In function ‘pvr2_lgh06xf_attach’:
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:208: error: ‘simple_tuner_attach’ undeclared (first use in this function)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:208: error: (Each undeclared identifier is reported only once
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:208: error: for each function it appears in.)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:208: warning: type defaults to ‘int’ in declaration of ‘__a’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:208: warning: type defaults to ‘int’ in declaration of ‘type name’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:208: warning: type defaults to ‘int’ in declaration of ‘type name’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:208: error: called object ‘__a’ is not a function
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c: In function ‘pvr2_fcv1236d_attach’:
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:274: error: ‘simple_tuner_attach’ undeclared (first use in this function)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:274: warning: type defaults to ‘int’ in declaration of ‘__a’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:274: warning: type defaults to ‘int’ in declaration of ‘type name’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:274: warning: type defaults to ‘int’ in declaration of ‘type name’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:274: error: called object ‘__a’ is not a function
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c: At top level:
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:335: error: variable ‘tda829x_no_probe’ has initializer but incomplete type
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:336: error: unknown field ‘probe_tuner’ specified in initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:336: error: ‘TDA829X_DONT_PROBE’ undeclared here (not in a function)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:336: warning: excess elements in struct initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:336: warning: (near initialization for ‘tda829x_no_probe’)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:339: error: variable ‘hauppauge_tda18271_dvb_config’ has initializer but incomplete type
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:340: error: unknown field ‘gate’ specified in initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:340: error: ‘TDA18271_GATE_ANALOG’ undeclared here (not in a function)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:340: warning: excess elements in struct initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:340: warning: (near initialization for ‘hauppauge_tda18271_dvb_config’)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c: In function ‘pvr2_73xxx_tda18271_8295_attach’:
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:358: error: ‘tda829x_attach’ undeclared (first use in this function)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:358: warning: type defaults to ‘int’ in declaration of ‘__a’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:358: warning: type defaults to ‘int’ in declaration of ‘type name’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:358: warning: type defaults to ‘int’ in declaration of ‘type name’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:358: error: called object ‘__a’ is not a function
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:361: error: ‘tda18271_attach’ undeclared (first use in this function)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:361: warning: type defaults to ‘int’ in declaration of ‘__a’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:361: warning: type defaults to ‘int’ in declaration of ‘type name’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:361: warning: type defaults to ‘int’ in declaration of ‘type name’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:361: error: called object ‘__a’ is not a function
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c: At top level:
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:429: error: variable ‘hauppauge_tda18271_std_map’ has initializer but incomplete type
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:430: error: unknown field ‘atsc_6’ specified in initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:430: error: extra brace group at end of initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:430: error: (near initialization for ‘hauppauge_tda18271_std_map’)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:431: warning: excess elements in struct initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:431: warning: (near initialization for ‘hauppauge_tda18271_std_map’)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:432: error: unknown field ‘qam_6’ specified in initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:432: error: extra brace group at end of initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:432: error: (near initialization for ‘hauppauge_tda18271_std_map’)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:433: warning: excess elements in struct initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:433: warning: (near initialization for ‘hauppauge_tda18271_std_map’)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:436: error: variable ‘hauppauge_tda18271_config’ has initializer but incomplete type
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:437: error: unknown field ‘std_map’ specified in initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:437: warning: excess elements in struct initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:437: warning: (near initialization for ‘hauppauge_tda18271_config’)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:438: error: unknown field ‘gate’ specified in initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:438: warning: excess elements in struct initializer
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:438: warning: (near initialization for ‘hauppauge_tda18271_config’)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c: In function ‘pvr2_tda18271_8295_attach’:
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:466: error: ‘tda829x_attach’ undeclared (first use in this function)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:466: warning: type defaults to ‘int’ in declaration of ‘__a’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:466: warning: type defaults to ‘int’ in declaration of ‘type name’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:466: warning: type defaults to ‘int’ in declaration of ‘type name’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:466: error: called object ‘__a’ is not a function
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:469: error: ‘tda18271_attach’ undeclared (first use in this function)
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:469: warning: type defaults to ‘int’ in declaration of ‘__a’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:469: warning: type defaults to ‘int’ in declaration of ‘type name’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:469: warning: type defaults to ‘int’ in declaration of ‘type name’
/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.c:469: error: called object ‘__a’ is not a function
make[2]: *** [/tmp/pvrusb2-mci-20091031/driver/pvrusb2-devattr.o] Fehler 1
make[1]: *** [_module_/tmp/pvrusb2-mci-20091031/driver] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Fehler 2
make: Verlasse Verzeichnis '/tmp/pvrusb2-mci-20091031/driver'

```

```
locate tda18271.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/media/tuner/tda18271.h

```

Driver: pvrusb2-mci-20091031

Sorry guys, but I'm just frustrated

---

### Post by deadland on 2009-11-17
Please help! The header files are available, what's wrong?

---

### Post by concordfta on 2009-11-18
Have you followed this: [http://www.isely.net/pvrusb2/setup.html#Compilation](http://www.isely.net/pvrusb2/setup.html#Compilation)

Also, the latest pvrusb2 is merged into Mercurial of V4L, so you could just build the latest V4L:  [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

---

### Post by deadland on 2009-11-30
Thanks for your help. I finally got the latest v4l-dvb compiled on my system. But I had problems, but this helped me:

> These steps worked for me:

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make menuconfig <-- dont change anything, just "Exit" and save changes
gedit v4l/.config <-- change CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n
make
sudo make install

---

### Post by !win on 2010-01-06
Removed

---

