---
title: "Help me with Terratec Cinergy C PCI HD"
date: 2010-10-05
forum: Mythbuntu
---

### Post by eriksson25 on 2010-10-05
Hi, I realy need help. Trying to set up mythtv on a ubuntu machine with this card of mine. But I cant get it to detect the card, eathir tiwh mythtv or keffine.

a output

```
media@media:~$ lspci -vnn -s 03:07.0
03:07.0 Multimedia controller [0480]: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] [1822:4e35] (rev 01)
    Subsystem: TERRATEC Electronic GmbH Device [153b:1178]
    Flags: bus master, medium devsel, latency 32, IRQ 11
    Memory at fdbff000 (32-bit, prefetchable) [size=4K]

```

I have tried to compile the mantis driver, but cant get it to work.

Runing this
```
sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
hg clone http://mercurial.intuxication.org/hg/s2-liplianin
cd s2-liplianin
make
sudo make install
sudo reboot

```

I get folowing error on make

```
/home/media/s2-liplianin/v4l/va1j5jf8007s.c:596: warning: initialization from incompatible pointer type
  CC [M]  /home/media/s2-liplianin/v4l/va1j5jf8007t.o
/home/media/s2-liplianin/v4l/va1j5jf8007t.c:445: warning: initialization from incompatible pointer type
  CC [M]  /home/media/s2-liplianin/v4l/em28xx-audio.o
  CC [M]  /home/media/s2-liplianin/v4l/em28xx-video.o
  CC [M]  /home/media/s2-liplianin/v4l/em28xx-i2c.o
  CC [M]  /home/media/s2-liplianin/v4l/em28xx-cards.o
  CC [M]  /home/media/s2-liplianin/v4l/em28xx-core.o
  CC [M]  /home/media/s2-liplianin/v4l/em28xx-input.o
  CC [M]  /home/media/s2-liplianin/v4l/em28xx-vbi.o
  CC [M]  /home/media/s2-liplianin/v4l/et61x251_core.o
  CC [M]  /home/media/s2-liplianin/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/media/s2-liplianin/v4l/firedtv-avc.o
  CC [M]  /home/media/s2-liplianin/v4l/firedtv-ci.o
  CC [M]  /home/media/s2-liplianin/v4l/firedtv-dvb.o
  CC [M]  /home/media/s2-liplianin/v4l/firedtv-fe.o
  CC [M]  /home/media/s2-liplianin/v4l/firedtv-1394.o
/home/media/s2-liplianin/v4l/firedtv-1394.c:22:17: error: dma.h: No such file or directory
/home/media/s2-liplianin/v4l/firedtv-1394.c:23:21: error: csr1212.h: No such file or directory
/home/media/s2-liplianin/v4l/firedtv-1394.c:24:23: error: highlevel.h: No such file or directory
/home/media/s2-liplianin/v4l/firedtv-1394.c:25:19: error: hosts.h: No such file or directory
/home/media/s2-liplianin/v4l/firedtv-1394.c:26:22: error: ieee1394.h: No such file or directory
/home/media/s2-liplianin/v4l/firedtv-1394.c:27:17: error: iso.h: No such file or directory
/home/media/s2-liplianin/v4l/firedtv-1394.c:28:21: error: nodemgr.h: No such file or directory
/home/media/s2-liplianin/v4l/firedtv-1394.c:41: warning: 'struct hpsb_iso' declared inside parameter list
/home/media/s2-liplianin/v4l/firedtv-1394.c:41: warning: its scope is only this definition or declaration, which is probably not what you want
/home/media/s2-liplianin/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/media/s2-liplianin/v4l/firedtv-1394.c:57: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:58: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/media/s2-liplianin/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:66: error: implicit declaration of function 'dma_region_i'
/home/media/s2-liplianin/v4l/firedtv-1394.c:66: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:66: error: expected expression before 'unsigned'
/home/media/s2-liplianin/v4l/firedtv-1394.c:68: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:72: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:86: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/media/s2-liplianin/v4l/firedtv-1394.c: In function 'node_of':
/home/media/s2-liplianin/v4l/firedtv-1394.c:91: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:91: warning: type defaults to 'int' in declaration of '__mptr'
/home/media/s2-liplianin/v4l/firedtv-1394.c:91: warning: initialization from incompatible pointer type
/home/media/s2-liplianin/v4l/firedtv-1394.c:91: error: invalid use of undefined type 'struct unit_directory'
/home/media/s2-liplianin/v4l/firedtv-1394.c: In function 'node_lock':
/home/media/s2-liplianin/v4l/firedtv-1394.c:96: error: 'quadlet_t' undeclared (first use in this function)
/home/media/s2-liplianin/v4l/firedtv-1394.c:96: error: (Each undeclared identifier is reported only once
/home/media/s2-liplianin/v4l/firedtv-1394.c:96: error: for each function it appears in.)
/home/media/s2-liplianin/v4l/firedtv-1394.c:96: error: 'd' undeclared (first use in this function)
/home/media/s2-liplianin/v4l/firedtv-1394.c:97: warning: ISO C90 forbids mixed declarations and code
/home/media/s2-liplianin/v4l/firedtv-1394.c:99: error: implicit declaration of function 'hpsb_node_lock'
/home/media/s2-liplianin/v4l/firedtv-1394.c:100: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/media/s2-liplianin/v4l/firedtv-1394.c: In function 'node_read':
/home/media/s2-liplianin/v4l/firedtv-1394.c:108: error: implicit declaration of function 'hpsb_node_read'
/home/media/s2-liplianin/v4l/firedtv-1394.c: In function 'node_write':
/home/media/s2-liplianin/v4l/firedtv-1394.c:113: error: implicit declaration of function 'hpsb_node_write'
/home/media/s2-liplianin/v4l/firedtv-1394.c: In function 'start_iso':
/home/media/s2-liplianin/v4l/firedtv-1394.c:124: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/media/s2-liplianin/v4l/firedtv-1394.c:124: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:126: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/media/s2-liplianin/v4l/firedtv-1394.c:135: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/media/s2-liplianin/v4l/firedtv-1394.c:138: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/media/s2-liplianin/v4l/firedtv-1394.c: In function 'stop_iso':
/home/media/s2-liplianin/v4l/firedtv-1394.c:149: error: implicit declaration of function 'hpsb_iso_stop'
/home/media/s2-liplianin/v4l/firedtv-1394.c: At top level:
/home/media/s2-liplianin/v4l/firedtv-1394.c:164: warning: 'struct hpsb_host' declared inside parameter list
/home/media/s2-liplianin/v4l/firedtv-1394.c: In function 'fcp_request':
/home/media/s2-liplianin/v4l/firedtv-1394.c:177: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:178: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c: In function 'node_probe':
/home/media/s2-liplianin/v4l/firedtv-1394.c:192: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:192: warning: type defaults to 'int' in declaration of '__mptr'
/home/media/s2-liplianin/v4l/firedtv-1394.c:192: warning: initialization from incompatible pointer type
/home/media/s2-liplianin/v4l/firedtv-1394.c:192: error: invalid use of undefined type 'struct unit_directory'
/home/media/s2-liplianin/v4l/firedtv-1394.c:197: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:198: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:199: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/media/s2-liplianin/v4l/firedtv-1394.c:199: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c: At top level:
/home/media/s2-liplianin/v4l/firedtv-1394.c:258: warning: 'struct unit_directory' declared inside parameter list
/home/media/s2-liplianin/v4l/firedtv-1394.c: In function 'node_update':
/home/media/s2-liplianin/v4l/firedtv-1394.c:260: error: dereferencing pointer to incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c: At top level:
/home/media/s2-liplianin/v4l/firedtv-1394.c:268: error: variable 'fdtv_driver' has initializer but incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:269: error: unknown field 'name' specified in initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/media/s2-liplianin/v4l/firedtv-1394.c:270: error: unknown field 'id_table' specified in initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:270: warning: excess elements in struct initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:270: warning: (near initialization for 'fdtv_driver')
/home/media/s2-liplianin/v4l/firedtv-1394.c:271: error: unknown field 'update' specified in initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:271: warning: excess elements in struct initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:271: warning: (near initialization for 'fdtv_driver')
/home/media/s2-liplianin/v4l/firedtv-1394.c:272: error: unknown field 'driver' specified in initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:272: error: extra brace group at end of initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:272: error: (near initialization for 'fdtv_driver')
/home/media/s2-liplianin/v4l/firedtv-1394.c:275: warning: excess elements in struct initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:275: warning: (near initialization for 'fdtv_driver')
/home/media/s2-liplianin/v4l/firedtv-1394.c:278: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/media/s2-liplianin/v4l/firedtv-1394.c:279: error: unknown field 'name' specified in initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:279: warning: excess elements in struct initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:279: warning: (near initialization for 'fdtv_highlevel')
/home/media/s2-liplianin/v4l/firedtv-1394.c:280: error: unknown field 'fcp_request' specified in initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:280: warning: excess elements in struct initializer
/home/media/s2-liplianin/v4l/firedtv-1394.c:280: warning: (near initialization for 'fdtv_highlevel')
/home/media/s2-liplianin/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/media/s2-liplianin/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_highlevel'
/home/media/s2-liplianin/v4l/firedtv-1394.c:288: error: implicit declaration of function 'hpsb_register_protocol'
/home/media/s2-liplianin/v4l/firedtv-1394.c:291: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/media/s2-liplianin/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/media/s2-liplianin/v4l/firedtv-1394.c:298: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/media/s2-liplianin/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/media/s2-liplianin/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/media/s2-liplianin/v4l'
make: *** [all] Error 2

```

It looks like that error only regards the firedtv and that shuldent efect me right? So dont know what more to do.

---

### Post by marduk667 on 2010-10-05
You should remove the firedtv from the build otherwise the build won't finish, so:

```
sed -i 's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config
```

After that do a make again (or if you have 2 cores a make -j2)

Regards,
Dennis

---

### Post by eriksson25 on 2010-10-05
> **marduk667 said:**
> You should remove the firedtv from the build otherwise the build won't finish, so:

```
sed -i 's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config
```

After that do a make again (or if you have 2 cores a make -j2)

Regards,
Dennis

Oki, thx, that got me a step closer. But now it fails on a new filer

```
/home/media/s2-liplianin/v4l/ir-sysfs.c: In function 'store_protocols':
/home/media/s2-liplianin/v4l/ir-sysfs.c:137: error: implicit declaration of function 'skip_spaces'
/home/media/s2-liplianin/v4l/ir-sysfs.c:137: warning: assignment makes pointer from integer without a cast
/home/media/s2-liplianin/v4l/ir-sysfs.c:178: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/media/s2-liplianin/v4l/ir-sysfs.o] Error 1
make[2]: *** [_module_/home/media/s2-liplianin/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/media/s2-liplianin/v4l'
make: *** [all] Error 2

```

I found this thread taking up the same thing, but dont understand there solution. Where am I sopose to put the patch file?

[http://www.satelliteguys.us/free-air-pc-dvb-discussion/226891-tbs6981-dvb-s2-problems-2.html]("http://www.satelliteguys.us/free-air-pc-dvb-discussion/226891-tbs6981-dvb-s2-problems-2.html")

> Copy and paste this patch file from Mauro into a text file and save it in the v4l-dvb/linux directory of your repository. (the file name is your choice)

cd into the linux directory and run the following command
Code:
patch -p1 -i patchfile-name

where is my  "v4l-dvb/linux directory of your repository"

Thx for the support

---

### Post by eriksson25 on 2010-10-05
Well, got everything to work, put that file in the linux folder of s2 and run it as it sad. Then it compiled everything like it shuld and are up and runing. Thx for your help

---

### Post by mholst on 2010-10-14
Hello there.
Nice to finally find someone else with the same card as myself. I have been struggling width MythTV for a very long time now, and I am kinda exhausted. The most painful experience is that when i have to record something, i insert the card into my old XP machine and it just works. However, as I have a running Ubuntu server I would prefer to gather it all in that.

Okay, but if you made yours work, i will give it a last go as well.

I added the patch from satguys, but I still get some errors, probably due to the fact that I am building some modules that are not really needed.

Can you show me your config file?

Best regards
Morten

When i do a "make" the following error is displayed:
  CC [M]  /usr/src/mantis-mercurial/v4l/ir-keytable.o
/usr/src/mantis-mercurial/v4l/ir-keytable.c: In function '__ir_input_register':
/usr/src/mantis-mercurial/v4l/ir-keytable.c:452: warning: assignment from incompatible pointer type
/usr/src/mantis-mercurial/v4l/ir-keytable.c:453: warning: assignment from incompatible pointer type


Added the patch and removed all modules that I probably dont need. But when loading I get the error below. Any suggestions?

[   23.072174] mantis_frontend_init (0): Probing for CU1216 (DVB-C)
[   23.075738] TDA10023: i2c-addr = 0x0c, id = 0x7d
[   23.075745] mantis_frontend_init (0): found Philips CU1216 DVB-C frontend (TDA10023) @ 0x0c
[   23.075818] mantis_frontend_init (0): Mantis DVB-C Philips CU1216 frontend attach success
[   23.075895] DVB: registering adapter 0 frontend 0 (Philips TDA10023 DVB-C)...
[   23.086245] mantis_ca_init (0): Registering EN50221 device
[   23.104988] mantis_ca_init (0): Registered EN50221 device
[   23.105074] mantis_hif_init (0): Adapter(0) Initializing Mantis Host Interface
[   23.160074] IR keymap rc-vp2040 not found
[   23.160178] mantis_rc_init (0): rc registering failed
[   23.160244] mantis_pci_probe (0): Mantis core init failed
[   23.160346] Mantis 0000:01:08.0: PCI INT A disabled

---

