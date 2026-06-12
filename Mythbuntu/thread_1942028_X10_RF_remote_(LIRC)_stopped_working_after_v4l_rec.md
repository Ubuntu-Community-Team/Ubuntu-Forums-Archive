---
title: "X10 RF remote (LIRC) stopped working after v4l recompile"
date: 2012-03-16
forum: Mythbuntu
---

### Post by wooddealer on 2012-03-16
Last week I recompiled the drivers for one of my tuner cards (in order to get the analog half of the card working) by following the steps outlined on the MythTV website for the card:
[http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Drivers](http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Drivers)


This resulted in neither of my two tuner cards working, and I'm not sure if LIRC was working either.

I then did another recompile but this time used this as a guide (using Basic Approach):
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

This time it worked, and all the inputs on all the tuner cards I care about work.  However, my remote which is an ATI USB X10 RF, ([http://www.mythtv.org/wiki/ATI_Remote_Wonder](http://www.mythtv.org/wiki/ATI_Remote_Wonder)) not the remote which interfaces the tuner cards, was not recognized.

Once the cards were working I then tried to get LIRC back in working order by following this HOWTO:
[http://www.lirc.org/html/install.html#compiling](http://www.lirc.org/html/install.html#compiling)

This didn't work to fix the remote, LIRC would not load the lirc_dev or usbati modules.

I then decided to try and reinstall LIRC package using both synaptic and apt, neither of these solved the problem.

Finally, I used synaptic to do a complete removal of LIRC to try and start from scratch, and that is my current situation, LIRC attempted to be removed, but still hanging on, and the USB dongle removed from the machine, and I still get lirc errors listed in dmesg:

```

h@desktop->4:~ $ grep lirc /var/log/dmesg
[   16.753874] ir_lirc_codec: Unknown symbol lirc_unregister_driver
[   16.753940] ir_lirc_codec: Unknown symbol lirc_dev_fop_poll
[   16.754028] ir_lirc_codec: Unknown symbol lirc_dev_fop_open
[   16.754101] ir_lirc_codec: Unknown symbol lirc_get_pdata
[   16.754167] ir_lirc_codec: Unknown symbol lirc_dev_fop_close
[   16.754239] ir_lirc_codec: Unknown symbol lirc_dev_fop_read
[   16.754304] ir_lirc_codec: Unknown symbol lirc_register_driver
[   16.754445] ir_lirc_codec: Unknown symbol lirc_dev_fop_ioctl

h@desktop->15:~ $ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid

h@desktop->22:~ $ lircd -v
lircd 0.9.1-git

```

Unfortunately I don't have the dmesg from during these various steps, but you can see here in the archive of the messages log when it breaks down:

```

h@desktop->25:~ $ grep lirc /var/log/messages.1
Mar  7 20:14:08 desktop kernel: [    8.904174] lirc_dev: IR Remote Control driver registered, major 61
Mar  7 20:14:08 desktop kernel: [    9.222491] lirc_atiusb: USB remote driver for LIRC $Revision: 1.85 $
Mar  7 20:14:08 desktop kernel: [    9.222494] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
Mar  7 20:14:08 desktop kernel: [    9.222535] lirc_dev: lirc_register_driver: sample_rate: 0
Mar  7 20:14:08 desktop kernel: [    9.241138] lirc_atiusb[3]: X10 Wireless Technology Inc USB Receiver on usb7:3
Mar  7 20:14:08 desktop kernel: [    9.251184] usbcore: registered new interface driver lirc_atiusb
Mar  7 21:33:26 desktop kernel: [    9.292174] lirc_dev: IR Remote Control driver registered, major 61
Mar  7 21:33:26 desktop kernel: [    9.335071] lirc_atiusb: USB remote driver for LIRC $Revision: 1.85 $
Mar  7 21:33:26 desktop kernel: [    9.335073] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
Mar  7 21:33:26 desktop kernel: [    9.335108] lirc_dev: lirc_register_driver: sample_rate: 0
Mar  7 21:33:26 desktop kernel: [    9.355129] lirc_atiusb[3]: X10 Wireless Technology Inc USB Receiver on usb7:3
Mar  7 21:33:26 desktop kernel: [    9.369159] usbcore: registered new interface driver lirc_atiusb
Mar  7 21:45:58 desktop kernel: [   11.185957] lirc_dev: IR Remote Control driver registered, major 61
Mar  7 21:45:58 desktop kernel: [   11.254723] lirc_atiusb: USB remote driver for LIRC $Revision: 1.85 $
Mar  7 21:45:58 desktop kernel: [   11.254725] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
Mar  7 21:45:58 desktop kernel: [   11.254758] lirc_dev: lirc_register_driver: sample_rate: 0
Mar  7 21:45:58 desktop kernel: [   11.274193] lirc_atiusb[3]: X10 Wireless Technology Inc USB Receiver on usb7:3
Mar  7 21:45:58 desktop kernel: [   11.287207] usbcore: registered new interface driver lirc_atiusb
Mar  7 22:03:29 desktop kernel: [    9.567324] lirc_dev: IR Remote Control driver registered, major 61
Mar  7 22:03:29 desktop kernel: [    9.610279] lirc_atiusb: USB remote driver for LIRC $Revision: 1.85 $
Mar  7 22:03:29 desktop kernel: [    9.610281] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
Mar  7 22:03:29 desktop kernel: [    9.610316] lirc_dev: lirc_register_driver: sample_rate: 0
Mar  7 22:03:29 desktop kernel: [    9.630204] lirc_atiusb[3]: X10 Wireless Technology Inc USB Receiver on usb7:3
Mar  7 22:03:29 desktop kernel: [    9.641243] usbcore: registered new interface driver lirc_atiusb
Mar  7 22:33:20 desktop kernel: [   11.223272] lirc_dev: IR Remote Control driver registered, major 250
Mar  7 22:33:20 desktop kernel: [   11.315297] lirc_atiusb: disagrees about version of symbol lirc_register_driver
Mar  7 22:33:20 desktop kernel: [   11.315301] lirc_atiusb: Unknown symbol lirc_register_driver
Mar  7 22:33:55 desktop kernel: [   60.088997] lirc_atiusb: disagrees about version of symbol lirc_register_driver
Mar  7 22:33:55 desktop kernel: [   60.089001] lirc_atiusb: Unknown symbol lirc_register_driver
Mar  7 22:52:18 desktop kernel: [ 1163.743003] lirc_atiusb: disagrees about version of symbol lirc_register_driver
Mar  7 22:52:18 desktop kernel: [ 1163.743007] lirc_atiusb: Unknown symbol lirc_register_driver
Mar  7 22:57:07 desktop kernel: [   10.874412] lirc_dev: IR Remote Control driver registered, major 249
Mar  7 22:57:07 desktop kernel: [   10.995472] lirc_atiusb: disagrees about version of symbol lirc_register_driver
Mar  7 22:57:07 desktop kernel: [   10.995476] lirc_atiusb: Unknown symbol lirc_register_driver
Mar  7 22:57:41 desktop kernel: [   58.680888] lirc_atiusb: disagrees about version of symbol lirc_register_driver
Mar  7 22:57:41 desktop kernel: [   58.680892] lirc_atiusb: Unknown symbol lirc_register_driver

```

I'm sorry if this is a little disorganized, typically I can find a solution after "googling" the problem, but in this case I've gone down a confusing hole and now I'm getting lost myself.  Any help to fully remove LIRC so I can do a fresh install using a package manager would be preferred, at least I think it would be preferred.

Thank you in advance.

---

### Post by azmyth on 2012-03-17
Something is telling me you have part of the compiled lirc installed and you have a part of the package installed thus causing conflicts. What switches options did you use when compiling lirc? How did you uninstall the compiled lirc?

---

### Post by wooddealer on 2012-03-19
azmyth

You are right I have done nothing to remove the "make install" version of LIRC, (I've never used 'make install' before, I find the packages easier).  So I have executed "make uninstall" for LIRC.  When I'm not at work I'll post the results of that, as well as reconnecting my USB dongle for the X10 and see what kind of errors I receive then.

Thanks for the help.

---

### Post by wooddealer on 2012-03-19
Okay, here is the dmesg relevant to our discussion, after doing "make uninstall".  I've added emphasis to what I assume is an offending module, I don't understand how or why it is loading, I assume I don't want it, since I'm not using an IR remote.

```

[   22.832463] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   22.832754] cx23885_dev_checkrevision() Hardware revision = 0xa4
[   22.832760] cx23885[0]/0: found at 0000:04:00.0, rev: 3, irq: 17, latency: 0, mmio: 0xf7e00000
[   22.832766] cx23885 0000:04:00.0: setting latency timer to 64
[   22.832771] IRQ 17/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   22.912316] tuner-simple 1-0061: creating new instance
[   22.912320] tuner-simple 1-0061: type set to 85 (Philips FQ1236 MK5)
[   22.914602] cx18-0: Registered device video1 for encoder MPEG (64 x 32.00 kB)
[   22.914606] DVB: registering new adapter (cx18)
[   22.921264] **IR MCE Keyboard/mouse protocol handler initialized**
[   23.055216] ir_lirc_codec: Unknown symbol lirc_unregister_driver
[   23.055282] ir_lirc_codec: Unknown symbol lirc_dev_fop_poll
[   23.055370] ir_lirc_codec: Unknown symbol lirc_dev_fop_open
[   23.055443] ir_lirc_codec: Unknown symbol lirc_get_pdata
[   23.055509] ir_lirc_codec: Unknown symbol lirc_dev_fop_close
[   23.055580] ir_lirc_codec: Unknown symbol lirc_dev_fop_read
[   23.055644] ir_lirc_codec: Unknown symbol lirc_register_driver
[   23.055924] ir_lirc_codec: Unknown symbol lirc_dev_fop_ioctl
[   23.066051] MXL5005S: Attached at address 0x63
[   23.066056] DVB: registering adapter 1 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   23.066164] cx18-0: DVB Frontend registered
[   23.066167] cx18-0: Registered DVB adapter1 for TS (32 x 32.00 kB)
[   23.066197] cx18-0: Registered device video33 for encoder YUV (20 x 101.25 kB)
[   23.066220] cx18-0: Registered device vbi1 for encoder VBI (20 x 51984 bytes)
[   23.066245] cx18-0: Registered device video25 for encoder PCM audio (256 x 4.00 kB)
[   23.066248] cx18-0: Initialized card: Hauppauge HVR-1600
[   23.066273] cx18:  End initialization


```

Thoughts?  Thanks in advance

---

### Post by azmyth on 2012-03-19
Did you follow the blacklist step in the link you provided?

dmesg | grep remote

If it lists ati_remote, you missed the step.

---

### Post by wooddealer on 2012-03-19
```
dmesg | grep remote

```
Returns nothing, so I assume it's been cleanly removed.

As for the blacklist, "ati_remote" is not list in either /etc/modprobe.d/blacklist.conf or /etc/modprobe.d/lirc

However it was listed in /etc/modprobe.d/lirc-blacklist in fact it list the only thing listed there and it is listed 19 times!

I think I'll reconnect the USB dongle and reboot, then examine dmesg for any new hints.  I'll post the dmesg once that's done.  Seem like a good idea?

Thanks,
wooddealer

---

### Post by wooddealer on 2012-03-19
Okay, have reattached the USB dongle and dmesg yields the following comment concerning lirc_atiusb:

```
[    8.737670] lp: driver loaded but no devices found
[B][    9.600425] lirc_atiusb: Unknown symbol lirc_unregister_driver
[    9.600626] lirc_atiusb: Unknown symbol lirc_register_driver[/B]
[    9.740319] WARNING: You are using an experimental version of the media stack.
[    9.740321]  As the driver is backported to an older kernel, it doesn't offer
[    9.740322]  enough quality for its usage in production.
[    9.740323]  Use it with care.
[    9.740323] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[    9.740324]  e8ca6d20a65d9d94693a0ed99b12d95b882dc859 [media] tveeprom: update hauppauge tuner list thru 181
[    9.740325]  a8567cf22e0efb9faafa6cf33b607ca5aee3c2fa [media] rtl2830: prevent .read_status() when sleeping
[    9.740326]  9935eea5ac300b84036192af1bd98940a64650de [media] rtl28xxu: many small tweaks

```

```
h@desktop->91:~ $ sudo modprobe lirc_atiusb
[sudo] password for h: 
WARNING: All config files need .conf: /etc/modprobe.d/lirc-blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/lirc, it will be ignored in a future release.
WARNING: Could not open '/lib/modules/2.6.32-39-generic/kernel/drivers/media/rc/lirc_dev.ko': No such file or directory
FATAL: Error inserting lirc_atiusb (/lib/modules/2.6.32-39-generic/kernel/ubuntu/lirc/lirc_atiusb/lirc_atiusb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
h@desktop->92:~ $ sudo modprobe lirc_dev
WARNING: All config files need .conf: /etc/modprobe.d/lirc-blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/lirc, it will be ignored in a future release.
FATAL: Could not open '/lib/modules/2.6.32-39-generic/kernel/drivers/media/rc/lirc_dev.ko': No such file or directory

```

I can't tell if this means lirc is completely removed, or if this is just normal behavior from the kernel.  I'm not sure what to do?  Suggestions?  Thanks.

---

### Post by azmyth on 2012-03-20
It believe your lirc is seriously borked from when you compiled lirc or from something else as your system is looking for lirc modules in non-standard places.

---

### Post by wooddealer on 2012-03-24
You are clearly right something is very borked.

I realized the other day that the source of this problem is probably that the first "make install" I did for the v4l drivers, I never did a "make uninstall" for them.  Those drivers include drivers for IR remotes, and I think that's what screwed everything up to begin with.  It's too bad I don't remember, or may have deleted, the directory I did that install from.

I rebooted into a different kernel (at least that's what I think I did), and while I don't have lirc installed anymore, the drivers seem to be working.  Note the differences in the two dmesg logs below:

```

[    0.000000] Linux version 2.6.32-36-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) )$
...
[    9.807521] lirc_dev: IR Remote Control driver registered, major 61
[    9.809402]
[    9.809403] lirc_atiusb: USB remote driver for LIRC $Revision: 1.85 $
[    9.809405] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[    9.809455] lirc_dev: lirc_register_driver: sample_rate: 0
[    9.828995] lirc_atiusb[3]: X10 Wireless Technology Inc USB Receiver on usb7:3
[    9.843032] usbcore: registered new interface driver lirc_atiusb

```

versus

```

[    0.000000] Linux version 2.6.32-39-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) )
...
[   10.798694] lirc_atiusb: Unknown symbol lirc_unregister_driver
[   10.798894] lirc_atiusb: Unknown symbol lirc_register_driver
...
[   15.579332] ir_lirc_codec: Unknown symbol lirc_unregister_driver
[   15.579399] ir_lirc_codec: Unknown symbol lirc_dev_fop_poll
[   15.579486] ir_lirc_codec: Unknown symbol lirc_dev_fop_open
[   15.579558] ir_lirc_codec: Unknown symbol lirc_get_pdata
[   15.579624] ir_lirc_codec: Unknown symbol lirc_dev_fop_close
[   15.579696] ir_lirc_codec: Unknown symbol lirc_dev_fop_read
[   15.579760] ir_lirc_codec: Unknown symbol lirc_register_driver
[   15.579900] ir_lirc_codec: Unknown symbol lirc_dev_fop_ioctl

```

Is there anyway for me to use the working drivers from "Linux version 2.6.32-36-generic" and move them to "Linux version 2.6.32-39-generic"?  I don't understand the directory structure and drivers (*.ko files?) well enough to just start trying things un assisted?

Thanks!

---

### Post by nickrout on 2012-03-24
> **wooddealer said:**
> You are clearly right something is very borked.

I realized the other day that the source of this problem is probably that the first "make install" I did for the v4l drivers, I never did a "make uninstall" for them.  Those drivers include drivers for IR remotes, and I think that's what screwed everything up to begin with.  It's too bad I don't remember, or may have deleted, the directory I did that install from.

I rebooted into a different kernel (at least that's what I think I did), and while I don't have lirc installed anymore, the drivers seem to be working.  Note the differences in the two dmesg logs below:

```

[    0.000000] Linux version 2.6.32-36-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) )$
...
[    9.807521] lirc_dev: IR Remote Control driver registered, major 61
[    9.809402]
[    9.809403] lirc_atiusb: USB remote driver for LIRC $Revision: 1.85 $
[    9.809405] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[    9.809455] lirc_dev: lirc_register_driver: sample_rate: 0
[    9.828995] lirc_atiusb[3]: X10 Wireless Technology Inc USB Receiver on usb7:3
[    9.843032] usbcore: registered new interface driver lirc_atiusb

```

versus

```

[    0.000000] Linux version 2.6.32-39-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) )
...
[   10.798694] lirc_atiusb: Unknown symbol lirc_unregister_driver
[   10.798894] lirc_atiusb: Unknown symbol lirc_register_driver
...
[   15.579332] ir_lirc_codec: Unknown symbol lirc_unregister_driver
[   15.579399] ir_lirc_codec: Unknown symbol lirc_dev_fop_poll
[   15.579486] ir_lirc_codec: Unknown symbol lirc_dev_fop_open
[   15.579558] ir_lirc_codec: Unknown symbol lirc_get_pdata
[   15.579624] ir_lirc_codec: Unknown symbol lirc_dev_fop_close
[   15.579696] ir_lirc_codec: Unknown symbol lirc_dev_fop_read
[   15.579760] ir_lirc_codec: Unknown symbol lirc_register_driver
[   15.579900] ir_lirc_codec: Unknown symbol lirc_dev_fop_ioctl

```

Is there anyway for me to use the working drivers from "Linux version 2.6.32-36-generic" and move them to "Linux version 2.6.32-39-generic"?  I don't understand the directory structure and drivers (*.ko files?) well enough to just start trying things un assisted?

Thanks!

No, but you could re-install the 2.6.32-39 kernel and you should et the correct drivers back.

---

