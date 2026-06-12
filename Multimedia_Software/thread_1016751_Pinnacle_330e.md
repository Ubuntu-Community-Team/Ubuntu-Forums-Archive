---
title: "Pinnacle 330e"
date: 2008-12-20
forum: Multimedia Software
---

### Post by porcorosso76 on 2008-12-20
There is not hope to install this tv usb pen in intrepid?
I've followed this howto:

> A rough guide to installing the Pinnacle PCTV Hybrid Pro on Ubuntu Edgy 6.10. I’m not going to beat around the bush with this - I’m just going to tell you how I did it. This tutorial will probably help install other tv cards based on the em28xx chipset but I cannot be sure.
1. Now open a terminal (Application->Accessories->Termial in Ubuntu).
2. I hate all this messing around with sudo at the front of every command put yourself into root with:
sudo su
3. Now you need to install some stuff first so do this:
apt-get install mercurial linux-headers-$(uname -r) gcc g++ make xawtv kaffeine dialog
4. Change Directory by executing this command:
cd /lib/firmware
5. Download the firmware for this specific product:
wget [http://konstantin.filtschew.de/v4l-firmware/firmware_v3.tgz](http://konstantin.filtschew.de/v4l-firmware/firmware_v3.tgz)
6. Extract it here:
tar xvzf firmware_v3.tgz
5. Change Directory again:
cd /usr/src/
6. This downloads the necissary V4L drivers:
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)
7. Change Directory:
cd v4l-dvb-experimental/
8. This one takes some time, it compiles the drivers - I think it took me about an hour on my slow laptop:
make
9. And then:
make install
The drivers are now installed but we need to reboot
10. Make sure you bookmark this page so that you can return to after you restart.
– reboot now –
11. Open a terminal and get into root again:
sudo su
12. Type these 3 lines into the terminal one by one; if any error occurs then something has gone wrong and I can’t help you.
modprobe em28xx
modprobe em28xx-audio
modprobe em2880-dvb
13. If all went well type:
gedit /etc/init.d/bootmisc.sh
14. Copy and paste these lines into the bottom of the file and then save it.
modprobe em28xx
modprobe em28xx-audio
modprobe em2880-dvb

Everything should now be running smoothly.
15. Open Kaffeine from Applications->Sound & Video->Kaffeine
Digital TV
A new “Digital TV” icon should have appeared - Click that and being the wonders of digital TV. Or if you want to watch Analouge TV hang on a second.
Analogue TV

To view analogue TV in Ubuntu, open XawTV (Applications->Sound & Video->XawTV)
Video: To change channels in XawTV use the up and down arrow keys on your keyboard until you come to something that looks somewhat like an image. There are other applications for this kind of thing but I won’t go through them with you - instead I shall palm you off onto [http://www.linuxtv.org](http://www.linuxtv.org)
Audio: Audio is a strange affair with this.
1.1. Open XawTV and make sure that the region is set correctly. For the UK use PAL-I from the selection; this makes sure that the audio will work properly. 
2.2. Find a channel in XawTV (In the UK I have found that the analogue channels are in the range of channels 20 to 40 in XawTV). 
3.3. Download this file and save it in a nice place so that you will remember it. 
4.4. Open a Terminal. 
5.5. Run this command: sudo su 
6.6. Now, Change Directory to where you saved the earlier downloaded file. (e.g. cd /home/rob/Downloads or wherever you stored the file) 
7.7. Run this command: chmod +x v4l-scripts-usbaudio_setup.sh 
8.8. And finally run this command: ./v4l-scripts-usbaudio_setup.sh 
*
WARNING: You will have to do steps 5, 6 and 8 each time you chose to watch analogue TV with sound.


I stop myself failing to make and make install at point 8.

this is the output:

> root@PC-Stefano:/usr/src/v4l-dvb-experimental# make

running ./build.sh build

make[1]: Entering directory `/usr/src/v4l-dvb-experimental'
rm -rf Module.symvers; 
make -C /lib/modules/`if [ -d /lib/modules/2.6.21.4-eeepc ]; then echo 2.6.21.4-eeepc; else uname -r; fi`/build SUBDIRS=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/v4l-dvb-experimental/em2880-dvb.o
In file included from /usr/src/v4l-dvb-experimental/em2880-dvb.c:33:
/usr/src/v4l-dvb-experimental/em28xx.h:31:20: error: dmxdev.h: Nessun file o directory
/usr/src/v4l-dvb-experimental/em28xx.h:32:23: error: dvb_demux.h: Nessun file o directory
/usr/src/v4l-dvb-experimental/em28xx.h:33:21: error: dvb_net.h: Nessun file o directory
/usr/src/v4l-dvb-experimental/em28xx.h:34:26: error: dvb_frontend.h: Nessun file o directory
In file included from /usr/src/v4l-dvb-experimental/em2880-dvb.c:33:
/usr/src/v4l-dvb-experimental/em28xx.h:557: error: field ‘demux’ has incomplete type
/usr/src/v4l-dvb-experimental/em28xx.h:565: error: field ‘adapter’ has incomplete type
/usr/src/v4l-dvb-experimental/em28xx.h:568: error: field ‘dmxdev’ has incomplete type
/usr/src/v4l-dvb-experimental/em28xx.h:570: error: field ‘dvbnet’ has incomplete type
In file included from /usr/src/v4l-dvb-experimental/em2880-dvb.c:40:
/usr/src/v4l-dvb-experimental/mt352/mt352.h: In function ‘mt352_write’:
/usr/src/v4l-dvb-experimental/mt352/mt352.h:68: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/mt352/mt352.h:69: error: dereferencing pointer to incomplete type
In file included from /usr/src/v4l-dvb-experimental/em2880-dvb.c:42:
/usr/src/v4l-dvb-experimental/drx3973d/drx3973d_demod.h: At top level:
/usr/src/v4l-dvb-experimental/drx3973d/drx3973d_demod.h:9: error: field ‘frontend’ has incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:48:22: error: lgdt330x.h: Nessun file o directory
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em2880_complete_irq’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:257: error: implicit declaration of function ‘dvb_dmx_swfilter’
/usr/src/v4l-dvb-experimental/em2880-dvb.c: At top level:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:366: warning: ‘struct dvb_demux_feed’ declared inside parameter list
/usr/src/v4l-dvb-experimental/em2880-dvb.c:366: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em2880_start_feed’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:368: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:369: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: At top level:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:383: warning: ‘struct dvb_demux_feed’ declared inside parameter list
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em2880_stop_feed’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:385: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:386: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em28xx_ts_bus_ctrl’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:412: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘mt352_pinnacle_init’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:463: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: At top level:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:491: error: variable ‘em2880_lgdt3303_dev’ has initializer but incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:492: error: unknown field ‘demod_address’ specified in initializer
/usr/src/v4l-dvb-experimental/em2880-dvb.c:492: warning: excess elements in struct initializer
/usr/src/v4l-dvb-experimental/em2880-dvb.c:492: warning: (near initialization for ‘em2880_lgdt3303_dev’)
/usr/src/v4l-dvb-experimental/em2880-dvb.c:493: error: unknown field ‘demod_chip’ specified in initializer
/usr/src/v4l-dvb-experimental/em2880-dvb.c:493: error: ‘LGDT3303’ undeclared here (not in a function)
/usr/src/v4l-dvb-experimental/em2880-dvb.c:494: warning: excess elements in struct initializer
/usr/src/v4l-dvb-experimental/em2880-dvb.c:494: warning: (near initialization for ‘em2880_lgdt3303_dev’)
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘kworld355u_i2c_gate_ctrl’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:508: error: field ‘frontend’ has incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:514: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em28xx_set_params’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:528: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:537: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em28xx_get_frequency’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:655: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em28xx_get_bandwidth’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:662: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em28xx_dvb_init’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:670: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em28xx_s921_init’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:725: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em28xx_zl10353_init’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:742: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em28xx_zl10353_sleep’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:791: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em28xx_dvb_sleep’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:807: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em2880_dvb_init’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:878: error: implicit declaration of function ‘dvb_attach’
/usr/src/v4l-dvb-experimental/em2880-dvb.c:882: warning: assignment makes pointer from integer without a cast
/usr/src/v4l-dvb-experimental/em2880-dvb.c:901: warning: assignment makes pointer from integer without a cast
/usr/src/v4l-dvb-experimental/em2880-dvb.c:904: warning: assignment makes pointer from integer without a cast
/usr/src/v4l-dvb-experimental/em2880-dvb.c:909: warning: assignment makes pointer from integer without a cast
/usr/src/v4l-dvb-experimental/em2880-dvb.c:915: error: ‘lgdt330x_attach’ undeclared (first use in this function)
/usr/src/v4l-dvb-experimental/em2880-dvb.c:915: error: (Each undeclared identifier is reported only once
/usr/src/v4l-dvb-experimental/em2880-dvb.c:915: error: for each function it appears in.)
/usr/src/v4l-dvb-experimental/em2880-dvb.c:916: warning: assignment makes pointer from integer without a cast
/usr/src/v4l-dvb-experimental/em2880-dvb.c:925: warning: assignment makes pointer from integer without a cast
/usr/src/v4l-dvb-experimental/em2880-dvb.c:930: warning: assignment makes pointer from integer without a cast
/usr/src/v4l-dvb-experimental/em2880-dvb.c:936: warning: assignment makes pointer from integer without a cast
/usr/src/v4l-dvb-experimental/em2880-dvb.c:939: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:940: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:941: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:962: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:963: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:965: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:967: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:971: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:973: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:982: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:996: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:998: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:999: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1017: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1020: error: implicit declaration of function ‘dvb_register_adapter’
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1037: error: implicit declaration of function ‘dvb_register_frontend’
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1044: error: ‘DMX_TS_FILTERING’ undeclared (first use in this function)
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1045: error: ‘DMX_SECTION_FILTERING’ undeclared (first use in this function)
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1046: error: ‘DMX_MEMORY_BASED_FILTERING’ undeclared (first use in this function)
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1048: error: implicit declaration of function ‘dvb_dmx_init’
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1059: error: implicit declaration of function ‘dvb_dmxdev_init’
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1063: error: implicit declaration of function ‘dvb_dmxdev_release’
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1074: error: implicit declaration of function ‘dvb_net_init’
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1074: error: dereferencing pointer to incomplete type
/usr/src/v4l-dvb-experimental/em2880-dvb.c: In function ‘em2880_dvb_fini’:
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1094: error: implicit declaration of function ‘dvb_net_release’
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1095: error: implicit declaration of function ‘dvb_unregister_frontend’
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1096: error: implicit declaration of function ‘dvb_frontend_detach’
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1100: error: implicit declaration of function ‘dvb_dmx_release’
/usr/src/v4l-dvb-experimental/em2880-dvb.c:1102: error: implicit declaration of function ‘dvb_unregister_adapter’
make[3]: *** [/usr/src/v4l-dvb-experimental/em2880-dvb.o] Error 1
make[2]: *** [_module_/usr/src/v4l-dvb-experimental] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/v4l-dvb-experimental'


Rebooting and doing modprobe says that there is no module found.

Can you please help me to installa the LAST piece of HARDWARE that I cannot use with my UBUNTU?

THANKS A LOT

---

