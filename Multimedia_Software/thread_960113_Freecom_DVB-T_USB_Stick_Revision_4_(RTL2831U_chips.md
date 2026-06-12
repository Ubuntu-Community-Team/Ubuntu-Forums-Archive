---
title: "Freecom DVB-T USB Stick Revision 4 (RTL2831U chipset)"
date: 2008-10-27
forum: Multimedia Software
---

### Post by ugm6hr on 2008-10-27
This is a new thread for Freecom DVB-T USB stick (Rev 4) owners.

A Linux driver exists for the Hardy kernel as discussed in the Archives - quoted below.

> **ugm6hr said:**
> I'm toying with the idea of upgrading to Hardy now.  Does this still work with the final Hardy?

PS: Has anyone tried the AMD64 Hardy with this?

EDIT: The rapidshare link doesn't work - try the German forum link for download: [http://forum.ubuntuusers.de/download/9970/](http://forum.ubuntuusers.de/download/9970/)

CONFIRMED:
This works just fine in Hardy 64-bit :)

In the uncompressed folder - just:
```
make
sudo make install
```

This is a new thread for further discussion - specifically with regard to anyone who has had success with the new Intrepid kernel.

---

### Post by WILLI on 2008-11-02
If I try to compile and install it under ubuntu 8.10 (64 bit), the stick isn't recognised after installation. I hoped the driver for this stick would be integrated in the 8.10 kernel but this isn't obviously the case...

greetz,
Willi

---

### Post by ugm6hr on 2008-11-02
> **WILLI said:**
> If I try to compile and install it under ubuntu 8.10 (64 bit), the stick isn't recognised after installation. I hoped the driver for this stick would be integrated in the 8.10 kernel but this isn't obviously the case...

Shame.  Looks like I'll be sticking with Hardy for the foreseeable future then.

As for the kernel integration of the driver - I can't see much discussion about development of that since the original driver was released.

---

### Post by WILLI on 2008-11-03
Hey all, 

This is what dmesg gives me when I connect my conceptronic dvb-t usb stick:

Nov  3 15:10:01 Robert kernel: [   22.531576] dvb-usb: found a 'Freecom USB 2.0 DVB-T Device' in warm state.
Nov  3 15:10:01 Robert kernel: [   22.531585] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Nov  3 15:10:01 Robert kernel: [   22.531952] PGD 7ace5067 PUD 7ace4067 PMD 0 
Nov  3 15:10:01 Robert kernel: [   22.532006] CPU 0 
Nov  3 15:10:01 Robert kernel: [   22.532006] Modules linked in: dvb_usb_rtl2831u(+) dvb_usb dvb_core i2c_core psmouse pcspkr(+) serio_raw iwl3945(+) evdev yenta_socket rfkill rsrc_nonstatic pcmcia_core snd_hda_intel iTCO_wdt iTCO_vendor_support snd_pcm_oss snd_mixer_oss mac80211 led_class snd_pcm parport_pc parport snd_seq_dummy cfg80211 snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device container snd video output wmi soundcore button battery shpchp pci_hotplug intel_agp ac snd_page_alloc ext3 jbd mbcache sr_mod cdrom pata_acpi sd_mod crc_t10dif ata_generic b44 sg usb_storage libusual ahci ata_piix libata scsi_mod dock ssb mii ohci1394 ieee1394 ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Nov  3 15:10:01 Robert kernel: [   22.532006] Pid: 2914, comm: modprobe Not tainted 2.6.27-7-generic #1
Nov  3 15:10:01 Robert kernel: [   22.532006] RIP: 0010:[<ffffffffa043049b>]  [<ffffffffa043049b>] dvb_register_adapter+0x3b/0x150 [dvb_core]
Nov  3 15:10:01 Robert kernel: [   22.532006] RSP: 0018:ffff88007accdb68  EFLAGS: 00010246
Nov  3 15:10:01 Robert kernel: [   22.532006] RAX: 0000000000000000 RBX: ffff88007d9a8d50 RCX: 0000000000000000
Nov  3 15:10:01 Robert kernel: [   22.532006] RDX: ffffffffa046b100 RSI: ffffffffa0445be0 RDI: ffffffffa0445bf0
Nov  3 15:10:01 Robert kernel: [   22.532006] RBP: ffff88007accdb98 R08: 0000000000000000 R09: ffff88007c456000
Nov  3 15:10:01 Robert kernel: [   22.532006] R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000000000
Nov  3 15:10:01 Robert kernel: [   22.532006] R13: ffff88007d9a8db8 R14: ffffffffa04664bd R15: ffffffffa046b100
Nov  3 15:10:01 Robert kernel: [   22.532006] FS:  00007ff1ff3116e0(0000) GS:ffffffff806e1a80(0000) knlGS:0000000000000000
Nov  3 15:10:01 Robert kernel: [   22.532006] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov  3 15:10:01 Robert kernel: [   22.532006] CR2: 0000000000000000 CR3: 000000007ace1000 CR4: 00000000000006e0
Nov  3 15:10:01 Robert kernel: [   22.532006] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov  3 15:10:01 Robert kernel: [   22.532006] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov  3 15:10:01 Robert kernel: [   22.532006] Process modprobe (pid: 2914, threadinfo ffff88007accc000, task ffff88007acd1670)
Nov  3 15:10:01 Robert kernel: [   22.532006] Stack:  ffff88007b06d088 ffff88007d9a8d50 ffff88007d9a8000 ffff88007d9a8000
Nov  3 15:10:01 Robert kernel: [   22.532006]  ffff88007d9a8db8 0000000000000000 ffff88007accdbd8<6>iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
Nov  3 15:10:01 Robert kernel: [   22.532006]  ffffffffa044b281
Nov  3 15:10:01 Robert kernel: [   22.532006]  0000000200000010 ffff88007d9a8d50 ffff88007d9a8d50 ffff88007d9a8000
Nov  3 15:10:01 Robert kernel: [   22.532006] Call Trace:
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffffa044b281>] dvb_usb_adapter_dvb_init+0x51/0x1d0 [dvb_usb]
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffffa044a632>] dvb_usb_adapter_init+0xf2/0x2d0 [dvb_usb]
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffffa044a8b4>] dvb_usb_init+0xa4/0x110 [dvb_usb]
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffffa044ab1e>] dvb_usb_device_init+0x1fe/0x2e0 [dvb_usb]
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffffa0463eb6>] rtd2831u_usb_probe+0x26/0x60 [dvb_usb_rtl2831u]
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffffa00586fc>] usb_probe_interface+0xcc/0x180 [usbcore]
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff80430552>] really_probe+0x72/0x1a0
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff804306d0>] driver_probe_device+0x50/0x60
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff8043076b>] __driver_attach+0x8b/0x90
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff804306e0>] ? __driver_attach+0x0/0x90
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff8042fcdb>] bus_for_each_dev+0x6b/0xa0
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff802e1ecb>] ? kmem_cache_alloc+0x8b/0xd0
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff804303b1>] driver_attach+0x21/0x30
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff8042f548>] bus_add_driver+0x1f8/0x270
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff80430965>] driver_register+0x75/0x170
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffffa0058a69>] usb_register_driver+0xa9/0x120 [usbcore]
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffffa00bc000>] ? rtd2831u_usb_module_init+0x0/0x49 [dvb_usb_rtl2831u]
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffffa00bc028>] rtd2831u_usb_module_init+0x28/0x49 [dvb_usb_rtl2831u]
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff8026c261>] ? __blocking_notifier_call_chain+0x21/0x90
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff8027d085>] sys_init_module+0xb5/0x1f0
Nov  3 15:10:01 Robert kernel: [   22.532006]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Nov  3 15:10:01 Robert kernel: [   22.532006] 
Nov  3 15:10:01 Robert kernel: [   22.532006] 
Nov  3 15:10:01 Robert kernel: [   22.532006]  RSP <ffff88007accdb68>
Nov  3 15:10:01 Robert kernel: [   22.541152] ---[ end trace 049bf7af02fbd2cc ]---

Anyone who can make something from it?

Thanks,
Willi

---

### Post by bas.doodeman on 2008-11-03
Got it working in Intrepid.

1. Open the attachment.
2. Extract it.
3. make
4. sudo make install

The source in the archive is based on: [rtl2831u_dvb-usb_v0.0.2mod.tar.gz]("http://rapidshare.com/files/93685682/rtl2831u_dvb-usb_v0.0.2mod.tar.gz.html")

I have updated the following files with the sources from 2.6.27-7 as explained in Doc/Readmeubuntu.txt:
demux.h
dmxdev.h
dvb_demux.h
dvbdev.h
dvb_frontend.h
dvb_net.h
dvb-pll.h
dvb_ringbuffer.h
dvb-usb.h
dvb-usb-ids.h

I could not find the source of dvbt_demod_base.h, and I have left the original from 2.6.22-14 in place.

After this I have updated rtd2830u.c as follows:
1. inserted the line 

DVB_DEFINE_MOD_OPT_ADAPTER_NR(adapter_nr);

after 

MODULE_PARM_DESC(debug, "set debugging level (1=info,xfer=2 (or-able))." DVB_USB_DEBUG_STATUS);

2. changed 

if (dvb_usb_device_init(intf,&rtd2831u_properties,THIS_MODULE,NULL) == 0 ||
            dvb_usb_device_init(intf,&haihua_properties,THIS_MODULE,NULL) == 0 )

to

if (dvb_usb_device_init(intf,&rtd2831u_properties,THIS_MODULE,NULL,adapter_nr) == 0 ||
            dvb_usb_device_init(intf,&haihua_properties,THIS_MODULE,NULL,adapter_nr) == 0 )

That seemed to do the trick. Everything compiles with the usual warnings. :)

---

### Post by WILLI on 2008-11-03
Hey,

I want to thank you, this works like a charm!!

Thank you,
Willi

---

### Post by ralle_b1 on 2008-11-19
Thanks a lot, bas.doodeman


Your fix workes on my system. 

One remark: I first overread the line "the fix is based on..." and downloaded the wrong file, which didn't worked in intrepid of course. Reading carefully helps. So a Warning: For intrepid: Download the file at the end of Bas post!

Thanks again, Ralle

---

### Post by ranjo on 2008-12-13
Thank you! This fix works great. I can tune and watch using Xine. I tried using mythtv as well but that isn't working. Could this be a failure of the driver or is it mythtv?

---

### Post by ugm6hr on 2008-12-13
> **ranjo said:**
> Thank you! This fix works great. I can tune and watch using Xine. I tried using mythtv as well but that isn't working. Could this be a failure of the driver or is it mythtv?

How do you use xine?  I use me-tv (which has an xine base), but it is very slow.  Kaffeine is better (but KDE based).

And will xine record?

---

### Post by ranjo on 2008-12-27
Thanks for your help!

Mythtv was my problem, when scanning channels it makes mistakes with filling the database correctly. The transport frequencies weren't filled in or were wrong. Now it's working perfectly and I can record four channels at the same time (from the same frequency). So this cheap usb device is working great! I hope that these drivers will be added into the linux kernel, that would make my mythtv box working without compiling anything :)

---

### Post by pacote on 2008-12-27
I'm using Ubuntu 8.04 Hardy with kernel 2.6.24-22-generic (i686). I tried with rtl2831u_dvb-usb_v0.0.2mod.tar.gz, following instructions in the previous post: [http://ubuntuforums.org/showthread.php?t=665315](http://ubuntuforums.org/showthread.php?t=665315) but it doesn't work. Compilation and installation was fine, but device /dev/dvb/adapter0/frontend0 was not created.

Next I tried with rtl2831u_dvb-usb_v0.0.2mod-intrepid.tar.bz2 in the bas.doodeman previous post #5. The headers files were different than mines in the current kernel, I didn't change any source contained in the package, I left 2.6.27-7 intrepid's ones, compilation and installation were successful. I think this solution is also applicable to Hardy (not only Intrepid) with kenels > 2.6.24-16. I would appreciate user feedback sharing their experiences.

Thank you
Paco

---

### Post by ugm6hr on 2008-12-27
I am still using the Hardy file on 64-bit Ubuntu. It works fine for me.

EDIT: Sorry - I use the Hardy mod (the original was for Gutsy).

---

### Post by pacote on 2009-01-07
I tried to install my DVB-T usb stick in intrepid with no luck. I'm using the latest kernel update: 2.6.27-9-generic, but also tried with previous version 2.6.27-7. I followed instructions in rtl2831u_dvb-usb_v0.0.2mod-intrepid.tar.bz2 to create the module. Compilation was successful, but after reboot this is the output of lsmod | grep dvb:

dvb_usb_rtl2831u      104964  0         
dvb_usb                24460  1 dvb_usb_rtl2831u
dvb_core               86272  1 dvb_usb         
i2c_core               31892  1 dvb_usb         
usbcore               148848  6 dvb_usb_rtl2831u,dvb_usb,usbhid,ehci_hcd,uhci_hcd

The modules dvb_pll and i2c bridge are missing. Kaffeine detects the device but channel scanning give me this kind of errors:

Invalid section length or timeout: pid=17

Do you know what is going wrong?

Thank you,
Paco

---

### Post by ugm6hr on 2009-03-28
Guess it's that time again...

New Ubuntu release on the horizon, and still no kernel integration for this driver.

Anyone tried it on Jaunty yet?

---

### Post by ranjo on 2009-04-03
Tryed it out at my computer. I took the intrepid package which I used on the old kernel.

```
make clean
make
sudo make install
sudo modprobe dvb-usb-rtl2831u 
```

dmesg tells:
[ 1599.008102] usbcore: registered new interface driver dvb_usb_rtd2831u

The device was pluged in all the time, so I removed it, en pluged it in again. This time is seemed to really do something:

```
[ 1882.428619] usb 1-6: new high speed USB device using ehci_hcd and address 5
[ 1882.566210] usb 1-6: configuration #1 chosen from 1 choice
[ 1882.566855] dvb-usb: found a 'DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver' in warm state.
[ 1882.566858] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 1882.569746] DVB: registering new adapter (DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver)
[ 1882.570017] BUG: unable to handle kernel NULL pointer dereference at 00000000
[ 1882.570021] IP: [<f91f3b0e>] rtd2831u_frontend_attach+0xe/0x34 [dvb_usb_rtl2831u]
[ 1882.570026] *pde = 00000000 
[ 1882.570028] Oops: 0002 [#1] SMP 
[ 1882.570030] last sysfs file: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/bInterfaceProtocol
[ 1882.570034] Dumping ftrace buffer:
[ 1882.570036]    (ftrace buffer empty)

```
And so on..

So... I don't think the "intrepid" code is suitable for the new kernel. I'm considering to look for a different DVB-T usb stick, which should work out of the box.

---

### Post by stealthbanana on 2009-04-11
Not used the thing for over a year.  Thanks to bas.doodeman for his change.

It's working on Jaunty beta very well, not checked the IR, as I cannot find any AAA batteries for the remote.
kernel in use is - 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:38:53 UTC 2009 i686 GNU/Linux.

Updated the files from the latest kernel source, usual errors but installs and it works, as usual better than on a windows machine, though I too am contemplating a replacement for easier use.

Just say, I am using a Twinhan Azurewave TU-2000:
Bus 001 Device 012: ID 13d3:3216 IMC Networks DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver

 
```

[ 3076.564204] usb 1-4.1.2: new high speed USB device using ehci_hcd and address 12
[ 3076.697132] usb 1-4.1.2: configuration #1 chosen from 1 choice
[ 3076.766546] dvb-usb: found a 'DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver' in warm state.
[ 3076.766561] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 3076.766779] DVB: registering new adapter (DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver)
[ 3076.767389] +rtd2831u_fe_attach
[ 3076.767516] -rtd2831u_fe_attach
[ 3076.767524] DVB: registering adapter 0 frontend 0 (Realtek RTD2830 DVB-T)...
[ 3076.767740] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.2/usb1/1-4/1-4.1/1-4.1.2/input/input10
[ 3076.800272] dvb-usb: schedule remote query interval to 300 msecs.
[ 3076.800284] dvb-usb: DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver successfully initialized and connected.
[ 3076.800331] usbcore: registered new interface driver dvb_usb_rtd2831u

```

---

### Post by david.r.b on 2009-05-07
Many Thanks. This works perfectly with my Jaunty installation!

---

### Post by jan123 on 2009-05-19
I've noticed this thread and the older one on [http://ubuntuforums.org/showthread.php?t=665315&page=7](http://ubuntuforums.org/showthread.php?t=665315&page=7)

I maintain the development archive at:
[http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2)

I see many differences between the version I maintain and the latest jaunty bzip posted here.
Is there a plan to merge these versions ?

In addition, I'd like to re-state the current status of kernel inclusion (same as my posting of Tue, 16 Sep 2008 08:02:36 to the mail list [email]linux-dvb@linuxtv.org[/email])
For kernel inclusion, front-end and back-end split up is mandatory.
Splitting the code up into front-end and back-end is more of a hassle 
than I assumed. I'm struggling with the old include files, the data 
structures (where used) and the linux interface protocols in general.

A version that does not even compile (NO USE FOR END USERS !)
[http://linuxtv.org/hg/~jhoogenraad/rtl2831-sepfront]("http://linuxtv.org/hg/%7Ejhoogenraad/rtl2831-sepfront")
I have synched the version with the version on my harddisk.

Part of the code is already recycled into the kernel.
As Alistair noticed, this is now blocking for getting the support for 
the stick into the main line. A pity for the users.
It would be great if somebody can help me on the split-up, so that these sticks can be supported out-of-the-box.

---

### Post by ranjo on 2009-08-25
I don't have much experience with coding kernel drivers, but if I need to test something or anything useful then let me know.

Meanwhile, Karmic is almost coming to its future freeze, anyone success with compiling the drivers into the new kernel?

---

### Post by jan123 on 2009-08-26
I'd appreciate if somebody would try to compile it under Karmac, just so that we know.
Probably Karmac will be the last kernel WITHOUT support for this stick.
On the DVB development forum, somebody is now recoding the driver so that it can be included in future versions of the kernel.
[http://vger.kernel.org/vger-lists.html#linux-media](http://vger.kernel.org/vger-lists.html#linux-media)
Testers will be needed shortly for this new development.

---

### Post by ronaldd on 2009-10-14
Attached is a tgz that compiles on Karmic Koala :)

The fix was really quite minor, FIRMWARE_MAX_NAME has been deprecated and is now fixed at 30:

[http://lkml.indiana.edu/hypermail/linux/kernel/0905.3/01078.html](http://lkml.indiana.edu/hypermail/linux/kernel/0905.3/01078.html)

At least the RTL2831 kernel module is a lot easier to get going now than previous kernel versions. :)

All the best!
Ronald

---

### Post by ugm6hr on 2009-10-14
I'll be sure to give this a try when I upgrade in a month or 2.

Thanks.

---

### Post by ld1083 on 2009-10-31
Hi! Thanks to this thread, in the past I managed to make my Freecom stick work under Hardy and Intrepid.

Now the fixed driver given by ronaldd compiles on Karmic indeed: modules are loaded... but unfortunately the device is not recognised.

dmesg tells:
[    9.403876] usbcore: registered new interface driver dvb_usb_rtd2831u

and lsmod | grep dvb:
dvb_usb_rtl2831u       91904  0 
dvb_usb                16200  1 dvb_usb_rtl2831u
dvb_core               87364  1 dvb_usb

but lsusb:
Bus 001 Device 005: ID 14aa:0160 AVerMedia (again) or C&E

Happy to know that the driver will be included in future versions of the kernel!

---

### Post by jan123 on 2009-11-01
Could you also try to compile the version from   [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2) under Karmac ?  I don't have Karmac yet, and I don't know if it is still working.  A new branch for the RTL2831 is set up for inclusion into the kernel. The code base is started from scratch:    [http://linuxtv.org/hg/~anttip/rtl2831u/](http://linuxtv.org/hg/~anttip/rtl2831u/) However, NO IR code is included at this stage.  It has been tested on a couple of systems, and I am eager to get more test results.

---

### Post by mxm on 2009-11-01
> **ld1083 said:**
> Hi! Thanks to this thread, in the past I managed to make my Freecom stick work under Hardy and Intrepid.

Now the fixed driver given by ronaldd compiles on Karmic indeed: modules are loaded... but unfortunately the device is not recognised.

dmesg tells:
[    9.403876] usbcore: registered new interface driver dvb_usb_rtd2831u

and lsmod | grep dvb:
dvb_usb_rtl2831u       91904  0 
dvb_usb                16200  1 dvb_usb_rtl2831u
dvb_core               87364  1 dvb_usb

but lsusb:
Bus 001 Device 005: ID 14aa:0160 AVerMedia (again) or C&E

Happy to know that the driver will be included in future versions of the kernel!

I second that. Same applies for the source at [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2).

It would be really neat to get my freecom stick working under karmic again :)

---

### Post by AgedP on 2009-11-02
> **jan123 said:**
> Could you also try to compile the version from   [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2) under Karmac ?  I don't have Karmac yet, and I don't know if it is still working.  A new branch for the RTL2831 is set up for inclusion into the kernel. The code base is started from scratch:    [http://linuxtv.org/hg/~anttip/rtl2831u/](http://linuxtv.org/hg/~anttip/rtl2831u/) However, NO IR code is included at this stage.  It has been tested on a couple of systems, and I am eager to get more test results.

I tried this using the procedure described in [http://crysol.org/en/node/1082](http://crysol.org/en/node/1082) which has worked well for me for both Jaunty & Intrepid.
However it didn't work this time with Karmic using " ~jhoogenraad "
maybe it would work using " ~anttip" files in the URL?
But it's probably work in progress and we should just be patient.

---

### Post by gourou on 2009-11-03
Hi all,

I may have a noob question, but once inserted in kernel, this driver doesn't give us a frontend and even seens not operating at all.
I found no way to use it with Mythtv (V4L). I've googled around but I found no answer...

Once I've installed this module (modprobe dvb-usb-rtl2831u), what should I do to make this card used by my DVR (MythTv) ?

Thks for your answers.
Gourou



Nb: My MythTV installation is OK with 2 Zarlink MT352 DVB-T card. I've just wanted to add another DVB-T card.

dmesg (Avermedia is OK, but Freecom USB is NOT ok)
[   14.981553] bttv0: detected: AVermedia AverTV DVB-T 771 [card=123], PCI subsystem ID is 1461:0771
[   14.981558] bttv0: using: AVerMedia AVerTV DVB-T 771 [card=123,autodetected]
[   15.022085] bttv1: detected: AVermedia AverTV DVB-T 771 [card=123], PCI subsystem ID is 1461:0771
[   15.022091] bttv1: using: AVerMedia AVerTV DVB-T 771 [card=123,autodetected]
[   15.346871] bt878_probe: card id=[0x7711461],[ AVermedia AverTV DVB-T 771 ] has DVB functions.
[   15.347295] bt878_probe: card id=[0x7711461],[ AVermedia AverTV DVB-T 771 ] has DVB functions.
[   15.740514] DVB: registering new adapter (bttv0)
[   15.874612] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...
[   15.874686] DVB: registering new adapter (bttv1)
[   15.875510] DVB: registering adapter 1 frontend 0 (Zarlink MT352 DVB-T)...

...
[21343.390041] usb 1-7: new high speed USB device using ehci_hcd and address 9
[21343.542860] usb 1-7: configuration #1 chosen from 1 choice

lsusb
Bus 001 Device 009: ID 13d3:3216 IMC Networks DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver

---

### Post by jan123 on 2009-11-04
I have updated the sources at [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2) so that all code should be compatible with the latest kernel (rtl2831-specific code was not changed, but all othe code is now in sync). The module runs wel with Jaunty. Can somebody try compiling this update with Karmic ?

---

### Post by gourou on 2009-11-04
> **jan123 said:**
> The module runs wel with Jaunty. Can somebody try compiling this update with Karmic ?

Failed for me... but I am definitely a newbie in such stuff, so I put all stdout here :

root@mythtv:/usr/src/rtl2831-r2-989c5dae9184# make all
make -C /usr/src/rtl2831-r2-989c5dae9184/v4l all
make[1]: entrant dans le rÃ©pertoire Â« /usr/src/rtl2831-r2-989c5dae9184/v4l Â»
No version yet, using 2.6.31-14-generic
make[1]: quittant le rÃ©pertoire Â« /usr/src/rtl2831-r2-989c5dae9184/v4l Â»
make[1]: entrant dans le rÃ©pertoire Â« /usr/src/rtl2831-r2-989c5dae9184/v4l Â»
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.31

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at [http://kernel.org](http://kernel.org).
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: quittant le rÃ©pertoire Â« /usr/src/rtl2831-r2-989c5dae9184/v4l Â»
make[1]: entrant dans le rÃ©pertoire Â« /usr/src/rtl2831-r2-989c5dae9184/v4l Â»
perl scripts/make_config_compat.pl /lib/modules/2.6.31-14-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/usr/src/rtl2831-r2-989c5dae9184/v4l/firmware'
make[2]: Leaving directory `/usr/src/rtl2831-r2-989c5dae9184/v4l/firmware'
make -C firmware
make[2]: Entering directory `/usr/src/rtl2831-r2-989c5dae9184/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/usr/src/rtl2831-r2-989c5dae9184/v4l/firmware'
Kernel build directory is /lib/modules/2.6.31-14-generic/build
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/usr/src/rtl2831-r2-989c5dae9184/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/tuner-xc2028.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/tuner-simple.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/tuner-types.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/mt20xx.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/tda8290.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/tea5767.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/tea5761.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/tda9887.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/tda827x.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/au0828-core.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/au0828-i2c.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/au0828-cards.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/au0828-dvb.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/au0828-video.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/au8522_dig.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/au8522_decoder.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/flexcop-pci.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/flexcop-usb.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/flexcop.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/flexcop-fe-tuner.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/flexcop-i2c.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/flexcop-sram.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/flexcop-eeprom.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/flexcop-misc.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/flexcop-hw-filter.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/flexcop-dma.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/bttv-driver.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/bttv-cards.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/bttv-if.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/bttv-risc.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/bttv-vbi.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/bttv-i2c.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/bttv-gpio.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/bttv-input.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/bttv-audio-hook.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cpia2_v4l.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cpia2_usb.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cpia2_core.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-driver.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-cards.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-i2c.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-firmware.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-gpio.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-queue.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-streams.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-fileops.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-ioctl.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-controls.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-mailbox.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-vbi.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-audio.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-video.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-irq.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-av-core.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-av-audio.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-av-firmware.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-av-vbi.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-scb.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-dvb.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx18-io.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx231xx-audio.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx231xx-video.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx231xx-i2c.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx231xx-cards.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx231xx-core.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx231xx-avcore.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx231xx-pcb-cfg.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx231xx-vbi.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx23885-cards.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx23885-video.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx23885-vbi.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx23885-core.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx23885-i2c.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx23885-dvb.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx23885-417.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx23885-ioctl.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx23885-ir.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx23885-input.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx23888-ir.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/netup-init.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cimax2.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/netup-eeprom.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx25840-core.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx25840-audio.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx25840-firmware.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx25840-vbi.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx88-video.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx88-vbi.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx88-mpeg.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx88-cards.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx88-core.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx88-i2c.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx88-tvaudio.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx88-dsp.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cx88-input.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvbdev.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dmxdev.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb_demux.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb_filter.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb_ca_en50221.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb_frontend.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb_net.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb_ringbuffer.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb_math.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/av7110_hw.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/av7110_v4l.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/av7110_av.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/av7110_ca.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/av7110.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/av7110_ipack.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/av7110_ir.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/a800.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/af9005-remote.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/af9005.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/af9005-fe.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/af9015.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/anysee.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/au6610.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/ce6230.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cinergyT2-core.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cinergyT2-fe.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/cxusb.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dib0700_core.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dib0700_devices.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dibusb-common.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dibusb-mb.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dibusb-mc.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/digitv.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dtt200u.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dtt200u-fe.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dtv5100.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dw2102.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/friio.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/friio-fe.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/gl861.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/gp8psk.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/gp8psk-fe.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/m920x.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/nova-t-usb2.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/opera1.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/math_mpi.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/foundation.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/demod_rtl2830.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/tuner_demod_io.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/tuner_mxl5005s.o
/usr/src/rtl2831-r2-989c5dae9184/v4l/tuner_mxl5005s.c: In function 'mxl5005s_SetRegMaskBits':
/usr/src/rtl2831-r2-989c5dae9184/v4l/tuner_mxl5005s.c:550: warning: 'RegByte' may be used uninitialized in this function
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/mt_spuravoid.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/mt_userdef.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/mt2060_basic.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/tuner_ah.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/MT2060Tuner.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.o
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:65: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:65: warning: (near initialization for 'rtd2831u_rc5_keys[0]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:66: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:66: warning: (near initialization for 'rtd2831u_rc5_keys[1]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:67: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:67: warning: (near initialization for 'rtd2831u_rc5_keys[2]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:68: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:68: warning: (near initialization for 'rtd2831u_rc5_keys[3]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:69: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:69: warning: (near initialization for 'rtd2831u_rc5_keys[4]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:102: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:102: warning: (near initialization for 'rtd2831u_conceptronic_keys[0]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:103: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:103: warning: (near initialization for 'rtd2831u_conceptronic_keys[1]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:104: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:104: warning: (near initialization for 'rtd2831u_conceptronic_keys[2]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:105: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:105: warning: (near initialization for 'rtd2831u_conceptronic_keys[3]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:106: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:106: warning: (near initialization for 'rtd2831u_conceptronic_keys[4]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:107: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:107: warning: (near initialization for 'rtd2831u_conceptronic_keys[5]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:108: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:108: warning: (near initialization for 'rtd2831u_conceptronic_keys[6]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:109: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:109: warning: (near initialization for 'rtd2831u_conceptronic_keys[7]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:110: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:110: warning: (near initialization for 'rtd2831u_conceptronic_keys[8]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:111: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:111: warning: (near initialization for 'rtd2831u_conceptronic_keys[9]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:113: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:113: warning: (near initialization for 'rtd2831u_conceptronic_keys[10]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:114: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:114: warning: (near initialization for 'rtd2831u_conceptronic_keys[11]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:115: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:115: warning: (near initialization for 'rtd2831u_conceptronic_keys[12]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:117: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:117: warning: (near initialization for 'rtd2831u_conceptronic_keys[13]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:118: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:118: warning: (near initialization for 'rtd2831u_conceptronic_keys[14]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:120: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:120: warning: (near initialization for 'rtd2831u_conceptronic_keys[15]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:121: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:121: warning: (near initialization for 'rtd2831u_conceptronic_keys[16]')
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:123: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/rtd2830u.c:123: warning: (near initialization for 'rtd2831u_conceptronic_keys[17]')
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/ttusb2.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/umt-010.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/vp702x.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/vp702x-fe.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/vp7045.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/vp7045-fe.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb-usb-firmware.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb-usb-init.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb-usb-urb.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb-usb-i2c.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb-usb-dvb.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/dvb-usb-remote.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/usb-urb.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/pt1.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/va1j5jf8007s.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/va1j5jf8007t.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/em28xx-audio.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/em28xx-video.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/em28xx-i2c.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/em28xx-cards.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/em28xx-core.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/em28xx-input.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/em28xx-vbi.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/et61x251_core.o
/usr/src/rtl2831-r2-989c5dae9184/v4l/et61x251_core.c: In function 'et61x251_ioctl_v4l2':
/usr/src/rtl2831-r2-989c5dae9184/v4l/et61x251_core.c:2493: warning: the frame size of 1408 bytes is larger than 1024 bytes
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/et61x251_tas5130d1b.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-avc.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-ci.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-dvb.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-fe.o
  CC [M]  /usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.o
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:37: warning: 'struct hpsb_iso' declared inside parameter list
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:37: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:53: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:54: error: implicit declaration of function 'hpsb_iso_n_ready'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:61: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:62: error: implicit declaration of function 'dma_region_i'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:62: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:62: error: expected expression before 'unsigned'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:63: warning: assignment makes pointer from integer without a cast
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:68: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:82: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: In function 'node_of':
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:87: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:87: warning: type defaults to 'int' in declaration of '__mptr'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:87: warning: initialization from incompatible pointer type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:87: error: invalid use of undefined type 'struct unit_directory'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: In function 'node_lock':
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:92: error: implicit declaration of function 'hpsb_node_lock'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:92: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:92: error: (Each undeclared identifier is reported only once
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:92: error: for each function it appears in.)
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:93: error: 'quadlet_t' undeclared (first use in this function)
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:93: error: expected ')' before 'arg'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: In function 'node_read':
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:98: error: implicit declaration of function 'hpsb_node_read'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: In function 'node_write':
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:103: error: implicit declaration of function 'hpsb_node_write'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: In function 'start_iso':
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:114: error: implicit declaration of function 'hpsb_iso_recv_init'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:114: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:116: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:118: warning: assignment makes pointer from integer without a cast
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:125: error: implicit declaration of function 'hpsb_iso_recv_start'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:128: error: implicit declaration of function 'hpsb_iso_shutdown'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: In function 'stop_iso':
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:139: error: implicit declaration of function 'hpsb_iso_stop'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: At top level:
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:154: warning: 'struct hpsb_host' declared inside parameter list
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: In function 'fcp_request':
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:167: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:168: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: In function 'node_probe':
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:182: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:182: warning: type defaults to 'int' in declaration of '__mptr'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:182: warning: initialization from incompatible pointer type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:182: error: invalid use of undefined type 'struct unit_directory'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:187: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:187: error: 'quadlet_t' undeclared (first use in this function)
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:188: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:188: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:188: warning: assignment makes pointer from integer without a cast
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: At top level:
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:243: warning: 'struct unit_directory' declared inside parameter list
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: In function 'node_update':
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:245: error: dereferencing pointer to incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: At top level:
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:253: error: variable 'fdtv_driver' has initializer but incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:254: error: unknown field 'name' specified in initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:254: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:254: warning: (near initialization for 'fdtv_driver')
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:255: error: unknown field 'update' specified in initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:255: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:255: warning: (near initialization for 'fdtv_driver')
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:256: error: unknown field 'driver' specified in initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:256: error: extra brace group at end of initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:256: error: (near initialization for 'fdtv_driver')
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:259: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:259: warning: (near initialization for 'fdtv_driver')
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:262: error: variable 'fdtv_highlevel' has initializer but incomplete type
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:263: error: unknown field 'name' specified in initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:263: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:263: warning: (near initialization for 'fdtv_highlevel')
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:264: error: unknown field 'fcp_request' specified in initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:264: warning: excess elements in struct initializer
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:264: warning: (near initialization for 'fdtv_highlevel')
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:271: error: implicit declaration of function 'hpsb_register_highlevel'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:272: error: invalid use of undefined type 'struct hpsb_protocol_driver'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:273: error: implicit declaration of function 'hpsb_register_protocol'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:276: error: implicit declaration of function 'hpsb_unregister_highlevel'
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.c:283: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/usr/src/rtl2831-r2-989c5dae9184/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/usr/src/rtl2831-r2-989c5dae9184/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [default] Erreur 2
make[1]: quittant le rÃ©pertoire Â« /usr/src/rtl2831-r2-989c5dae9184/v4l Â»
make: *** [all] Erreur 2

---

### Post by jicarretero on 2009-11-04
This worked for me:

[http://ubuntuforums.org/showthread.php?t=1305228](http://ubuntuforums.org/showthread.php?t=1305228)

---

### Post by sempronius on 2009-11-04
While I didn't have any major problem with the driver for 14aa:0160 in previous kernel versions, this became different with my current kernel 2.6.30.

The old procedures did not work any longer, and the jhoogenraad driver gave me kernel oopses (though I was able to watch TV) and other annoyances (endless messages about not detecting IR, after resuming from hibernation).

So I gave anttip a try!

And wow, this one works very well.
There is still an issue left, after resuming from hibernation I cannot use the dvb-t stick without replugging it; there is an alternative without unplugging it, though: unloading ehci_hcd and reloading it.

At any rate, so far, I am quite pleased with the anttip drivers.


sempronius

---

### Post by mxm on 2009-11-06
> **sempronius said:**
> While I didn't have any major problem with the driver for 14aa:0160 in previous kernel versions, this became different with my current kernel 2.6.30.

The old procedures did not work any longer, and the jhoogenraad driver gave me kernel oopses (though I was able to watch TV) and other annoyances (endless messages about not detecting IR, after resuming from hibernation).

So I gave anttip a try!

And wow, this one works very well.
There is still an issue left, after resuming from hibernation I cannot use the dvb-t stick without replugging it; there is an alternative without unplugging it, though: unloading ehci_hcd and reloading it.

At any rate, so far, I am quite pleased with the anttip drivers.


sempronius

same here! dear developer, thank you very much :)

---

### Post by ld1083 on 2009-11-06
Wow, mxm & sempronius, how did you get the driver working?? I tried without success jhoogenraad as well as anttip driver... Nothing new since my previous post :-k

---

### Post by gourou on 2009-11-07
> **ld1083 said:**
> Wow, mxm & sempronius, how did you get the driver working?? I tried without success jhoogenraad as well as anttip driver... Nothing new since my previous post :-k

Same here...

I am using the default generic kernel for 9.10 64 bits release (2.6.31-14-generic), can someone post an already compiled module for the default kernel to make sure our troubles are not "compile-time" related.

Thks

---

### Post by mxm on 2009-11-08
> **gourou said:**
> Same here...

I am using the default generic kernel for 9.10 64 bits release (2.6.31-14-generic), can someone post an already compiled module for the default kernel to make sure our troubles are not "compile-time" related.

Thks

Sorry guys, i didn't get the drivers working. they compiled fine and the module is being loaded when plugging in the usb cord but lsusb shows the stick as AVer Media...thus no playback.

---

### Post by CnlPepper on 2009-11-22
I've also got a rev 4 Freecom USB stick and today I've tried compiling both the jhoogenraad and anttip drivers on Karmic 2.6.31-15 kernel. I've got neither modules to work with MythTV. There are varying degrees of success:

jhoogenraad:

* compiles fine after removing the FireDTV module from the install (use "make menuconfig" to bring up the config menu, you'll need to install libncurses5-dev first using apt)
* does not seem to do anything, lsusb reports: *14aa:0160 AVerMedia (again) or C&E*
* no dvb entries in /dev
* nothing in dmesg other than reporting a fast usb device detected

anttip:

* again compiles fine once FireDTV module removed
* lsusb reports: 14aa:0160 AVerMedia (again) or C&E
* see the following in demsg on usb stick connection:

[ 2262.840016] usb 1-7: new high speed USB device using ehci_hcd and address 6
[ 2262.991916] usb 1-7: configuration #1 chosen from 1 choice
[ 2262.992973] rtl2831u_probe: interface:0
[ 2262.992977] dvb-usb: found a 'Freecom USB2.0 DVB-T' in warm state.
[ 2262.993445] rtl2831u_power_ctrl: onoff:1 < sys_0:20 gpo:10
[ 2262.993449] rtl2831u_power_ctrl: onoff:1 > sys_0:e0 gpo:01
[ 2262.995984] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 2262.996248] DVB: registering new adapter (Freecom USB2.0 DVB-T)
[ 2262.996535] rtl2831u_frontend_attach:
[ 2263.006193] rtl2831u_frontend_attach: tuner:1
[ 2263.006305] DVB: registering adapter 0 frontend 0 (Realtek RTL2830 DVB-T)...
[ 2263.006360] rtl2831u_tuner_attach:
[ 2263.008832] MT2060: successfully identified (IF1 = 1220)
[ 2263.586252] rtl2831u_power_ctrl: onoff:0 < sys_0:e0 gpo:01
[ 2263.586256] rtl2831u_power_ctrl: onoff:0 > sys_0:e0 gpo:01
[ 2263.588626] dvb-usb: Freecom USB2.0 DVB-T successfully initialized and connected.

* new nodes present in /dev/:

dvb0.frontend0
dvb0.demux0 
dvb0.dvr0
dvb0.net0

* but can not find tuner in mythtv setup.

Don't know if there should be but there is no entry in /v4l/by-id or by-path. Is there ment to be?

There is no /dev/dvb.

---

### Post by AgedP on 2009-11-27
> **jan123 said:**
> Could you also try to compile the version from   [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2) under Karmac ?  I don't have Karmac yet, and I don't know if it is still working.  A new branch for the RTL2831 is set up for inclusion into the kernel. The code base is started from scratch:    [http://linuxtv.org/hg/~anttip/rtl2831u/](http://linuxtv.org/hg/~anttip/rtl2831u/) However, NO IR code is included at this stage.  It has been tested on a couple of systems, and I am eager to get more test results.

I have sucessfully compiled the dvb-usb-rtl2831u module on amd64 system. However the device is not recognised.  This is what I did...
sudo apt-get install linux-headers-$(uname -r)
hg clone [http://linuxtv.org/hg/~anttip/rtl2831u](http://linuxtv.org/hg/~anttip/rtl2831u)

Edited the v4l folder .config file. (See gefenm11)
make 
sudo make install
sudo modprobe dvb-usb-rtl2831u      (All OK)

Restarted the system
lsusb 
Bus 001 Device 005 ID 0bda:2831 Realtek Semiconductor Corp. 2831U Device

However device does not appear under /dev

Part of dmesg follows...

[    7.110886] EDAC MC: Ver: 2.1.0 Nov 10 2009
[    7.653067] parport_pc 00:0a: reported by Plug and Play ACPI
[    7.653114] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    7.656452] rtl2831u_module_init:
[    7.656471] rtl2831u_probe: interface:0
[    7.656474] dvb-usb: found a 'RTL2831U DVB-T USB2.0 DEVICE' in warm state.
[    7.657895] rtl2831u_power_ctrl: onoff:1 < sys_0:e0 gpo:01
[    7.657898] rtl2831u_power_ctrl: onoff:1 > sys_0:e0 gpo:01
[    7.658680] lp: driver loaded but no devices found
[    7.660184] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    7.660415] DVB: registering new adapter (RTL2831U DVB-T USB2.0 DEVICE)
[    7.660656] rtl2831u_frontend_attach:
[    7.670022] rtl2831u_frontend_attach: tuner:1
[    7.680492] EDAC amd64_edac:  Ver: 3.2.0 Nov 10 2009
[    7.680880] EDAC amd64: This node reports that Memory ECC is currently disabled.
[    7.680886] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[    7.680889] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[    7.680891]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[    7.680892]     Might be a BIOS bug, if BIOS says ECC is enabled
[    7.680893]     Use of the override can cause unknown side effects.
[    7.680910] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    7.732645] lp0: using parport0 (interrupt-driven).
[    7.930650] ppdev: user-space parallel port driver
[    7.941710] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.981971] DVB: registering adapter 0 frontend 0 (Realtek RTL2830 DVB-T)...
[    7.982028] rtl2831u_tuner_attach:
[    8.243856] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[    8.272019] MT2060: successfully identified (IF1 = 1220)
[    8.861772] rtl2831u_power_ctrl: onoff:0 < sys_0:e0 gpo:01
[    8.861776] rtl2831u_power_ctrl: onoff:0 > sys_0:e0 gpo:01
[    8.867947] dvb-usb: RTL2831U DVB-T USB2.0 DEVICE successfully initialized and connected.

Seems to be a problem with EDAC amd64_edac module?
Google search shows that this may be a kernel bug but I am way out of my depth.

Just like to thank jan123 for all his work on rtl2831

---

### Post by mxm on 2009-11-27
This is what I get ([http://linuxtv.org/hg/~anttip/rtl2831u](http://linuxtv.org/hg/~anttip/rtl2831u)) with same configuration as above:

```

[ 9731.140070] usb 1-5: new high speed USB device using ehci_hcd and address 8
[ 9731.274115] usb 1-5: configuration #1 chosen from 1 choice
[ 9731.309165] rtl2831u_module_init:
[ 9731.309195] rtl2831u_probe: interface:0
[ 9731.309197] dvb-usb: found a 'Freecom USB2.0 DVB-T' in warm state.
[ 9731.309676] rtl2831u_power_ctrl: onoff:1 < sys_0:20 gpo:10
[ 9731.309679] rtl2831u_power_ctrl: onoff:1 > sys_0:e0 gpo:01
[ 9731.310218] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 9731.310480] DVB: registering new adapter (Freecom USB2.0 DVB-T)
[ 9731.310765] rtl2831u_frontend_attach:
[ 9731.320183] rtl2831u_frontend_attach: tuner:1
[ 9731.320304] DVB: registering adapter 0 frontend 0 (Realtek RTL2830 DVB-T)...
[ 9731.320380] rtl2831u_tuner_attach:
[ 9731.333681] MT2060: successfully identified (IF1 = 1220)
[ 9731.821332] rtl2831u_power_ctrl: onoff:0 < sys_0:e0 gpo:01
[ 9731.821340] rtl2831u_power_ctrl: onoff:0 > sys_0:e0 gpo:01
[ 9731.821830] dvb-usb: Freecom USB2.0 DVB-T successfully initialized and connected.
[ 9731.821894] usbcore: registered new interface driver dvb_usb_rtl2831u

```

lsusb shows

Bus 001 Device 011: ID 14aa:0160 AVerMedia (again) or C&E

---

### Post by AgedP on 2009-12-10
I have now got this device working in karmic.
The current version of udev fails to set up /dev/dvb/adapter0.
If you look at /lib/udev/rules.d/50-udev-default.rules and find the section dealing with dvb you will see that the code has been curtailed in this karmic version compared with the jaunty version.
Look at [http://ubuntuforums.org/showthread.php?t=1327337](http://ubuntuforums.org/showthread.php?t=1327337) which gives solution for the problem by installing a new rule:-
/etc/udev/rules.d/50-udev.rules
It works for me!

---

### Post by mxm on 2009-12-11
> **AgedP said:**
> I have now got this device working in karmic.
The current version of udev fails to set up /dev/dvb/adapter0.
If you look at /lib/udev/rules.d/50-udev-default.rules and find the section dealing with dvb you will see that the code has been curtailed in this karmic version compared with the jaunty version.
Look at [http://ubuntuforums.org/showthread.php?t=1327337](http://ubuntuforums.org/showthread.php?t=1327337) which gives solution for the problem by installing a new rule:-
/etc/udev/rules.d/50-udev.rules
It works for me!

thanks. which driver source did you choose?

---

### Post by AgedP on 2009-12-12
> **mxm said:**
> thanks. which driver source did you choose?

I used the '~anttip' version.   See my post #37 above for details.
Important to understand that present version of udev is failing to set up the /dev/dsp/adapter0 tree.    
**This problem probably affects all karmic users of dvb-t usb dongles!**
Just follow the link to jarlethorsen and go to bottom of page (post #6) and copy his new /etc/udev/rules.d/50-udev.rules to same place your system (do NOT edit /lib/udev/rules.d)
I use me-tv and it worked straight away after scanning channels

---

### Post by ld1083 on 2009-12-12
It works! Thank you, AgedP [-o<

---

### Post by mxm on 2009-12-12
I can't believe this....I'm watching TV. Worked like charm, AgedP[-o<

---

### Post by gamx on 2010-01-08
It was working for me up to now. Ubuntu has updated the kernel to 2.6.31-17, and now I have a very strange problem. When I compile the module, it uses the old version of the kernel. It says,
"Kernel build directory is /lib/modules/2.6.31-16-generic/build"
even though I am using the new one.
What option should I pass to the make command to change that to the current kernel?
Thanks,

Gamx

---

### Post by jan123 on 2010-01-09
Type     make distclean    make allmodconfig this updates the make configuration.

---

### Post by gamx on 2010-01-09
Thanks Jan123. That did it for me! It works great.
Best,

Gamx

---

### Post by xadm on 2010-04-19
Does anyone has a solution for ubuntu 10.04 lucid lynx?

---

### Post by gamx on 2010-04-25
Exactly. It does not work with Lucid RC. Compiling leads to the following messages. No idea what they mean...

make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/gamx/Temp/rtl2831u/v4l/dmxdev.o
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c: In function 'dvb_dmxdev_buffer_read':
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c:83: error: 'TASK_INTERRUPTIBLE' undeclared (first use in this function)
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c:83: error: (Each undeclared identifier is reported only once
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c:83: error: for each function it appears in.)
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c:83: error: implicit declaration of function 'signal_pending'
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c:83: error: implicit declaration of function 'schedule'
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c: In function 'dvb_dvr_release':
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c:212: error: 'TASK_NORMAL' undeclared (first use in this function)
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c: In function 'dvb_dmxdev_filter_timeout':
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c:338: error: 'TASK_NORMAL' undeclared (first use in this function)
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c: In function 'dvb_dmxdev_section_callback':
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c:364: error: 'TASK_NORMAL' undeclared (first use in this function)
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c: In function 'dvb_dmxdev_ts_callback':
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c:415: error: 'TASK_NORMAL' undeclared (first use in this function)
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c: In function 'dvb_dmxdev_filter_free':
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c:791: error: 'TASK_NORMAL' undeclared (first use in this function)
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c: In function 'dvb_demux_release':
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c:1131: error: 'TASK_NORMAL' undeclared (first use in this function)
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c: In function 'dvb_dmxdev_release':
/home/gamx/Temp/rtl2831u/v4l/dmxdev.c:1259: error: 'TASK_UNINTERRUPTIBLE' undeclared (first use in this function)
make[3]: *** [/home/gamx/Temp/rtl2831u/v4l/dmxdev.o] Error 1
make[2]: *** [_module_/home/gamx/Temp/rtl2831u/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/gamx/Temp/rtl2831u/v4l'
make: *** [all] Error 2


Any ideas?

Gamx

---

### Post by joshruehlig on 2010-04-30
We have had similar problems on lucid with a rtl driver and compiling. Maybe the kernel doesn't have it supported?

[http://ubuntuforums.org/showthread.php?p=9203570#post9203570](http://ubuntuforums.org/showthread.php?p=9203570#post9203570)

---

### Post by mr_a on 2010-05-03
I have the same problem as Gamx. 

It was working fine under Karmic but does not work under Lucid.

Have tried the various options described above but no joy.

It would be great to get this sorted as then I can watch whilst I write my school reports. 

Matthew

---

### Post by jan123 on 2010-05-04
Do you get the same results (EXACTLY the same messages for dmxdev) for BOTH of the trees below ?  [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2/](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2/)  [http://linuxtv.org/hg/~anttip/rtl2831u/](http://linuxtv.org/hg/~anttip/rtl2831u/)  pull the latest version from hg, and do both 'make distclean' and 'make'  Please confirm them on the latest version of both trees, so that I can see what I can do. The first one should have a very recent dmxdev)

---

### Post by mr_a on 2010-05-04
Jan,

Thanks for your reply.

I am not an expert by any means and have mainly learnt from following tutorials and searching forums!

Here's what I did (take from AgedP post #37) and slightly adapted

sudo apt-get install linux-headers-$(uname -r)
hg clone [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2/](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2/)
cd rtl2831-r2
make distclean
make
sudo make install

At the end of the make I get the following

make[3]: *** [/root/Documents/rtl2831-r2/v4l/firedtv-1394.o] Error 1 
make[2]: *** [_module_/root/Documents/rtl2831-r2/v4l] Error 2 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic' 
make[1]: *** [default] Error 2 
make[1]: Leaving directory `/root/Documents/rtl2831-r2/v4l' 
make: *** [all] Error 2 

I have left out all of the other output but have made a copy of it, if this were to be of any help.

When I then do 
sudo modprobe dvb-usb-rtl2831u
FATAL: Module dvb_usb_rtl2831u not found.

Any help or advice would be greatly appreciated.

Thanks.

Matthew

---

### Post by jan123 on 2010-05-05
I forgot to include  'make allyesconfig' before the make. This way, the offending module should be deselected. Apologies: I'm stumbling often into the mistake of forgetting this.

---

### Post by AgedP on 2010-05-05
> **jan123 said:**
> I forgot to include  'make allyesconfig' before the make. This way, the offending module should be deselected. Apologies: I'm stumbling often into the mistake of forgetting this.

Thank you Jan.  It works fine.
I notice that we now use [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2/](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2/)
and not the anttip version.

---

### Post by mr_a on 2010-05-05
Jan,

Success.

Here's what I did.

sudo apt-get install linux-headers-$(uname -r)
hg clone [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2/](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2/)
cd rtl2831-r2
make distclean
make allyesconfig
make
sudo make install

All ran fine and I then had no Fatal Error when I sudo modprobe dvb-usb-rtl2831u.

Many thanks for your help.

Matthew

---

### Post by Pagadeux on 2010-05-06
Sorry, I need some help with this. Unfortunately I', relatively new to Linux. I exactly replicated the steps in the last post but when I run "make allyesconfig" I get:

Preparing to compile for kernel version 2.6.32

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at [http://kernel.org](http://kernel.org).
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

VIDEO_TVP7002: Requires at least kernel 2.6.34
SOC_CAMERA: Requires at least kernel 2.6.33
SOC_CAMERA_MT9M001: Requires at least kernel 2.6.33
SOC_CAMERA_MT9M111: Requires at least kernel 2.6.33
SOC_CAMERA_MT9T031: Requires at least kernel 2.6.33
SOC_CAMERA_MT9V022: Requires at least kernel 2.6.33
SOC_CAMERA_TW9910: Requires at least kernel 2.6.33
SOC_CAMERA_PLATFORM: Requires at least kernel 2.6.33
SOC_CAMERA_OV772X: Requires at least kernel 2.6.33
RADIO_SAA7706H: Requires at least kernel 2.6.34
Created default (all yes) .config file
./scripts/fix_kconfig.pl


If I continue with make and make install I end up getting the same errors as mr_a reported in Post #52. What am I doing wrong?

---

### Post by xadm on 2010-05-07
I also did it as described by mr_a in post #55, but I still get the error :-(

---

### Post by harrri on 2010-05-07
I ran into the same troubles! With the following procedure my stick now works with lucid lynx. Don't understand why, but i can watch my Austrian TV now.

[COLOR=Red]First of all. Do it Jan's way![/COLOR]

sudo apt-get install linux-headers-$(uname -r)
hg clone [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2/]("http://linuxtv.org/hg/%7Ejhoogenraad/rtl2831-r2/")
cd rtl2831-r2
make distclean
make allyesconfig

[COLOR=Red]Then, following the link from post #30 I made a change in the ".config" file in the v4l folder.[/COLOR]

"in the v4l folder, open the **.config** file,
 find the line
      Code:
     CONFIG_DVB_FIREDTV=m 
 and change it to
      Code:
     CONFIG_DVB_FIREDTV=n 
 "
[COLOR=Red]finally[/COLOR]

make
sudo make install

Thanks to all the linux experts in this forum!

---

### Post by sepius on 2010-05-08
To all and harri, thanks for all the hard work.  Got my Cobolt USB2.0 DVB-T working now ($25.00 from Sam's).  For the record it is the USB ID 0bda:2831.  Running now on 10.04 x64 system in Australia.

Again, thanks to all .... you're all awsome!!

---

### Post by xadm on 2010-05-09
hey, it works! thank you very very much! :-) :-)

---

### Post by Pagadeux on 2010-05-09
Works great! Thanks harrri!

---

### Post by mxm on 2010-10-30
Can't compile the source anymore using Ubuntu 10.10:

```

/home/max/src/rtl2831-r2-36045596ac74/v4l/tuner-xc2028.c: In function 'free_firmware':
/home/max/src/rtl2831-r2-36045596ac74/v4l/tuner-xc2028.c:252: error: implicit declaration of function 'kfree'

```

Any solutions?

---

### Post by jan123 on 2010-10-31
Dit you pull the latest version ?
I thought I fixed this end of august 2010.
Please mention your kernel version as well: I need this to debug if needed.

---

### Post by mxm on 2010-10-31
> **jan123 said:**
> Dit you pull the latest version ?
I thought I fixed this end of august 2010.
Please mention your kernel version as well: I need this to debug if needed.

Urgs, you're right. I forgot to pull the latest version. The driver compiles and loads perfectly under 2.6.35-22-generic. Thanks!

---

### Post by skodsamler on 2011-02-28
i like ubuntu 10.10 its nice and free but  just  so hard getting things to work, in windows i can run setup file in linux most work via software center , but so come some devil saying use  terminal compile and do tons of stuff and after 3 weeks still no tv, so mabey i just is too stuppid to use linux

---

### Post by gamx on 2011-05-01
As usual, with every new version of Ubuntu a new problem arises with this module... It used to work just fine with Maverick. Now in Natty, when I try to compile it I get the following error:

make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/gamx/Temp/rtl2831-r2/v4l/flexcop-i2c.o
/home/gamx/Temp/rtl2831-r2/v4l/flexcop-i2c.c: In function 'flexcop_i2c_init':
/home/gamx/Temp/rtl2831-r2/v4l/flexcop-i2c.c:253:39: error: 'I2C_CLASS_TV_DIGITAL' undeclared (first use in this function)
/home/gamx/Temp/rtl2831-r2/v4l/flexcop-i2c.c:253:39: note: each undeclared identifier is reported only once for each function it appears in
make[3]: *** [/home/gamx/Temp/rtl2831-r2/v4l/flexcop-i2c.o] Error 1
make[2]: *** [_module_/home/gamx/Temp/rtl2831-r2/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/gamx/Temp/rtl2831-r2/v4l'


Any idea of what is going on?
Thanks, 

Gamx

---

### Post by Happyl on 2011-05-12
same here :(

it seems to be a kernel problem. I'm thinking of downgrading my ubuntu

---

### Post by ppsalama on 2011-05-12
The same problem with a dvbt usb stick with [B]RTL2831U chipset.
usually with new kernels I did [this recipe]("http://metalzonix.wordpress.com/2010/05/21/instalar-drivers-rtl2831u-para-el-receptor-tdt-zaapa-en-ubuntu-10-10/")
and it worked fine
[/B][B]but with natty I get the same response than gamx.
Anybody can check this posible solution: [here]("http://www.ryanlothian.com/projects/linux/freecom-dvb-t-stick")
thanks

[/B]

---

### Post by AgedP on 2011-05-17
I don't think ppsalama solution will help. It fetches a firmware file and rtl2831u does not any - it's complete in that regard.
I am looking forward to hearing what jan123 has to say about this new problem which I am sure is kernel related.
I have also tried to install on 2.6.32-amd64 but without success.

---

### Post by AgedP on 2011-05-17
Sorry, a mistake!!
I tried to install rtl2831u on 2.6.38-5-amd64 kernel.
NOT 2.6.32-5.

---

### Post by oscarah on 2011-05-29
Hi to all,

I think I found a solution for this problem. You can read it on this message, at crysol.org: [http://crysol.org/es/node/1082#comment-5014](http://crysol.org/es/node/1082#comment-5014)

Thanks.

---

### Post by Happyl on 2011-05-30
thanks for your effort !
anyway still got some errors
> 
/home/holger/Downloads/rtl2831-r2/v4l/v4l2-dev.c:371:2: error: unknown field 'ioctl' specified in initializer
/home/holger/Downloads/rtl2831-r2/v4l/v4l2-dev.c:371:2: warning: initialization from incompatible pointer type
make[3]: *** [/home/holger/Downloads/rtl2831-r2/v4l/v4l2-dev.o] Fehler 1

i replaced the config and patched successfully. I have to admit my spanish isn't really good :confused:

---

### Post by oscarah on 2011-05-30
Hello and thanks for testing!

Please, could you paste here the full compilation log. I've not modified every file, just only the ones I need, but these may be different for you. Thanks.

Edit: Oops, sorry. The patch is malformed:

> patching file linux/drivers/media/video/v4l2-common.c
patch: **** malformed patch at line 582: --- 909,908 ----


Please, wait until I fix it :)

Edit: done. I edited the patch by hand... bad idea :) Please, insert coin and try again! ;)

---

### Post by gamx on 2011-06-01
Hi,
I have tried to compile the module with the patch but I still get an error. This time is the following: 

/home/gamx/Temp/rtl2831-r2_patched/v4l/flexcop-i2c.c: In function 'flexcop_i2c_init':
/home/gamx/Temp/rtl2831-r2_patched/v4l/flexcop-i2c.c:253:39: error: 'I2C_CLASS_TV_DIGITAL' undeclared (first use in this function)
/home/gamx/Temp/rtl2831-r2_patched/v4l/flexcop-i2c.c:253:39: note: each undeclared identifier is reported only once for each function it appears in
make[3]: *** [/home/gamx/Temp/rtl2831-r2_patched/v4l/flexcop-i2c.o] Error 1
make[2]: *** [_module_/home/gamx/Temp/rtl2831-r2_patched/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/gamx/Temp/rtl2831-r2_patched/v4l'
make: *** [all] Error 2



Gamx

---

### Post by oscarah on 2011-06-02
Yep, you should use the config I use. All IR modules must be disabled for now. Sorry.

---

### Post by gamx on 2011-06-04
My fault. My Spanish is good but I did not read the instructions carefully enough.;-) Sorry.
With your config file (replacing the one in the v4l directory) I manage to get a bit further but I still get an error. Am I supposed to change anything more? I am not an expert...

/home/gamx/Temp/rtl2831-r2_patched/v4l/v4l2-compat-ioctl32.c: In function 'native_ioctl':
/home/gamx/Temp/rtl2831-r2_patched/v4l/v4l2-compat-ioctl32.c:232:21: error: 'const struct file_operations' has no member named 'ioctl'
/home/gamx/Temp/rtl2831-r2_patched/v4l/v4l2-compat-ioctl32.c:237:19: error: 'const struct file_operations' has no member named 'ioctl'
/home/gamx/Temp/rtl2831-r2_patched/v4l/v4l2-compat-ioctl32.c: In function 'get_v4l2_format32':
/home/gamx/Temp/rtl2831-r2_patched/v4l/v4l2-compat-ioctl32.c:379:2: warning: case value '0' not in enumerated type 'enum v4l2_buf_type'
/home/gamx/Temp/rtl2831-r2_patched/v4l/v4l2-compat-ioctl32.c: In function 'put_v4l2_format32':
/home/gamx/Temp/rtl2831-r2_patched/v4l/v4l2-compat-ioctl32.c:410:2: warning: case value '0' not in enumerated type 'enum v4l2_buf_type'
/home/gamx/Temp/rtl2831-r2_patched/v4l/v4l2-compat-ioctl32.c: In function 'v4l2_compat_ioctl32':
/home/gamx/Temp/rtl2831-r2_patched/v4l/v4l2-compat-ioctl32.c:981:17: error: 'const struct file_operations' has no member named 'ioctl'
make[3]: *** [/home/gamx/Temp/rtl2831-r2_patched/v4l/v4l2-compat-ioctl32.o] Error 1
make[2]: *** [_module_/home/gamx/Temp/rtl2831-r2_patched/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/gamx/Temp/rtl2831-r2_patched/v4l'
make: *** [all] Error 2


Thanks,

Gamx

---

### Post by ppsalama on 2011-06-22
SOLVED !!!!!!!... sorry my english is not so good, but I paste here a comment (pending of moderation) left at [metalzonix]("http://metalzonix.wordpress.com/2010/05/21/instalar-drivers-rtl2831u-para-el-receptor-tdt-zaapa-en-ubuntu-10-10/"). In that post metalzonix had a recipe for ubuntu 10.10. With that recipe and the patch of [crysol]("http://crysol.org/es/node/1082#comment-5014") I tried to combine doing the following (comments in spanish):

¡¡¡ Lo conseguí !!! he combinado las instrucciones de este post con el parche [http://crysol.org/es/node/1082#comment-5014](http://crysol.org/es/node/1082#comment-5014)

No soy experto en esto… en un probar por probar hice lo siguiente (trataré de recordarlo todo, no tomé notas porque no creía que funcionaría):

# sudo apt-get install linux-source linux-headers-$(uname -r)
# sudo apt-get install mercurial
# hg clone [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2)
# cd rtl2831-r2/

hasta aquí como en este post…. ahora el parche tal y como dice

# rtl2831-r2$ wget [http://arco.esi.uclm.es/~oscar.acena/crysol/rtl2831/kernel_2.6.38.patch](http://arco.esi.uclm.es/~oscar.acena/crysol/rtl2831/kernel_2.6.38.patch)
# rtl2831-r2$ patch -p1 < kernel_2.6.38.patch

Dado que el post que habla del parche también habla de un archivo config… yo añado su descarga (aunque no se si hice algo con él, de hecho no se si vale o no)

# rtl2831-r2$ wget [http://arco.esi.uclm.es/~oscar.acena/crysol/rtl2831/config](http://arco.esi.uclm.es/~oscar.acena/crysol/rtl2831/config)

Ahora continúo como en este post

# sudo make menuconfig

Y aquí viene, creo, lo importante… deshabilité todo (salvo el apartado audio, quité las marcas a todo) y solo dejé lo que hacía referencia a RTL2831u

# sudo make clean
# sudo make
# sudo make install

Algún error por medio creo que dió, pero dió la sensación que la instalación finalizó correctamente así que… desconecté y volví a conectar el tdt usb stick zappa y…

# lsmod | grep dvb

bingooooooooooo !!! me apareció esto…

dvb_usb_rtl2831u 93776 0
dvb_usb 19240 1 dvb_usb_rtl2831u
dvb_core 90137 1 dvb_usb

Abrí VLC, desempolvé mi archivo channels.conf y…. viendo la tdt en Ubuntu 11.04.

Rogaría a metalzonix, que tú si que sabes, que depurara o diera sentido a lo que he escrito en este comentario, con el fin de ver si he recordado algo mal o he hecho algo de más o de menos.

GRACIAS.

---

### Post by gamx on 2011-06-23
Finally it works for me. I had to disable V4L (on top of what was already disabled in the config file mentioned above) and now it seems to work.
Thanks to all,

Gamx

---

### Post by Happyl on 2011-07-03
yeah, nice work dudes...finally i have a running dvb-t device :popcorn:

---

### Post by sepius on 2011-11-11
Thanks ppsalama, this process worked for me perfectly on a Linux Mint (Katya) amd64 architecture.

Muchas gracias.

---

