---
title: "irw produces no output"
date: 2011-03-13
forum: Multimedia Software
---

### Post by CoasterMaster on 2011-03-13
I just installed lirc using **sudo apt-get install lirc** and selected **Windows Media Center Transcievers/Remotes (all)** as I have a windows MCE remote.  This configuration was working in Ubuntu 10.04.  Ever since I upgraded to 10.10, I have been unable to get my remote working.  When running irw, I get no output after pressing buttons on my remote.  My IR receiver is connected and is receiving power (as I can see a little red LED in the receiver when I press buttons).  

lsusb output:

```

xbmc@xbmc-desktop:~$ lsusb
Bus 002 Device 004: ID 147a:e017 Formosa Industrial Computing, Inc. eHome Infrared Receiver
Bus 002 Device 002: ID 04f2:0963 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04fc:0c25 Sunplus Technology Co., Ltd SATALink SPIF225A
Bus 001 Device 002: ID 04fc:0c25 Sunplus Technology Co., Ltd SATALink SPIF225A
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
xbmc@xbmc-desktop:~$ 

```

The receiver is the first item listed.  I looked at the documentation at [https://help.ubuntu.com/community/InstallLirc/Maverick#Adding%20support%20for%20more%20remotes](https://help.ubuntu.com/community/InstallLirc/Maverick#Adding%20support%20for%20more%20remotes) and I noticed that the device ID (e017) is already listed in the code.  The only thing that I've noticed out of the ordinary is that **/dev/lirc0** and **/dev/lirc** do not exist (but **/dev/lircd** does).  Trying to run mode2 returns the following output:

```

xbmc@xbmc-desktop:~$ mode2
mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory

```

It appears that the modules get loaded:

```

xbmc@xbmc-desktop:~$ lsmod | grep lirc
lirc_mceusb            19509  0 
lirc_dev                9510  1 lirc_mceusb

```


I've been tackling this for several days, but I'm not sure what else I should look at.  Any help will be greatly appreciated.

One more thing I figure I should include is the output of dmesg | grep lirc:

```

xbmc@xbmc-desktop:~$ dmesg | grep lirc
[   10.439512] lirc_dev: IR Remote Control driver registered, major 61 
[   10.867357] ir_lirc_codec: Unknown symbol lirc_dev_fop_poll (err 0)
[   10.867737] ir_lirc_codec: Unknown symbol lirc_dev_fop_open (err 0)
[   10.868037] ir_lirc_codec: disagrees about version of symbol lirc_get_pdata
[   10.868043] ir_lirc_codec: Unknown symbol lirc_get_pdata (err -22)
[   10.868350] ir_lirc_codec: Unknown symbol lirc_dev_fop_close (err 0)
[   10.868657] ir_lirc_codec: Unknown symbol lirc_dev_fop_read (err 0)
[   10.868913] ir_lirc_codec: disagrees about version of symbol lirc_register_driver
[   10.868919] ir_lirc_codec: Unknown symbol lirc_register_driver (err -22)
[   10.869569] ir_lirc_codec: Unknown symbol lirc_dev_fop_ioctl (err 0)
[   10.901560] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   10.901571] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   10.902147] usbcore: registered new interface driver lirc_mceusb
[100486.097555] usbcore: deregistering interface driver lirc_mceusb
[100509.438047] lirc_dev: IR Remote Control driver registered, major 61 
[100518.089440] lirc_mod_mce: Windows Media Center Edition USB IR Keyboard and Transceiver driver for LIRC 0.4.0
[100518.089453] lirc_mod_mce: Jon Davies <jon@hedgerows.org.uk>, Ryan Reading, Florian Demski, Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[100518.089561] usbcore: registered new interface driver lirc_mod_mce

```

---

