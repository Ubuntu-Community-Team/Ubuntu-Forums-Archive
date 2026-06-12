---
title: "DTV1000 T - cannot load cx88-dvb"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by r57 on 2008-01-07
Hi there community, here I am! 

I've just register, because I cannot solve my probem. I've google it... then google it again and again, hoping that someone had similar problem. Well... someone had, but updates solved it. But I have my ubuntu fully updated and stilll cannot get this to work.

So, there is my problem: after an update, I cannot use my DVB-T card (DTV1000 T from Leadtek).
It was a kernel update, I thing. After it I cannot see D-TV in kaffeine, nor dvb in /dev. In dmesg I can see that some modules wont load ("videobuf" and "cx88" prefixed modules). When I try modprobe cx88 I got errors too. There is my output:

> 
r57@r57-desktop:~$ sudo modprobe cx88-dvb
WARNING: Error inserting video_buf_dvb (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/video-buf-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting video_buf (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/video-buf.ko): Invalid module format
WARNING: Error inserting cx88xx (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx88/cx88xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cx8802 (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx88/cx8802.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)


and dmesg related part:
> 
.....
[   20.556000] lp0: using parport0 (interrupt-driven).
[   20.704000] video_buf_dvb: disagrees about version of symbol videobuf_read_stop
[   20.704000] video_buf_dvb: Unknown symbol videobuf_read_stop
[   20.704000] video_buf_dvb: disagrees about version of symbol videobuf_waiton
[   20.704000] video_buf_dvb: Unknown symbol videobuf_waiton
[   20.704000] video_buf_dvb: disagrees about version of symbol videobuf_read_start
[   20.704000] video_buf_dvb: Unknown symbol videobuf_read_start
[   20.704000] video_buf: exports duplicate symbol videobuf_mmap_mapper (owned by videobuf_core)
[   20.724000] cx88xx: disagrees about version of symbol videobuf_waiton
[   20.724000] cx88xx: Unknown symbol videobuf_waiton
[   20.724000] cx88xx: disagrees about version of symbol videobuf_dma_unmap
[   20.724000] cx88xx: Unknown symbol videobuf_dma_unmap
[   20.724000] cx8802: Unknown symbol cx88_reset
[   20.724000] cx8802: Unknown symbol cx88_wakeup
[   20.724000] cx8802: Unknown symbol cx88_risc_stopper
[   20.724000] cx8802: Unknown symbol cx88_print_irqbits
[   20.724000] cx8802: Unknown symbol cx88_shutdown
[   20.724000] cx8802: Unknown symbol cx88_core_put
[   20.724000] cx8802: Unknown symbol cx88_core_irq
[   20.724000] cx8802: Unknown symbol cx88_core_get
[   20.724000] cx8802: Unknown symbol cx88_sram_channels
[   20.724000] cx8802: Unknown symbol cx88_sram_channel_dump
[   20.724000] cx8802: Unknown symbol cx88_sram_channel_setup
[   20.724000] cx8802: disagrees about version of symbol videobuf_iolock
[   20.724000] cx8802: Unknown symbol videobuf_iolock
[   20.728000] cx8802: Unknown symbol cx88_free_buffer
[   20.728000] cx8802: Unknown symbol cx88_boards
[   20.728000] cx8802: Unknown symbol cx88_risc_databuffer
[   20.736000] cx88_dvb: Unknown symbol cx88_call_i2c_clients
[   20.736000] cx88_dvb: Unknown symbol cx8802_get_driver
[   20.736000] cx88_dvb: Unknown symbol cx8802_unregister_driver
[   20.736000] cx88_dvb: Unknown symbol videobuf_queue_init
[   20.736000] cx88_dvb: Unknown symbol cx8802_register_driver
[   20.736000] cx88_dvb: Unknown symbol videobuf_dvb_unregister
[   20.736000] cx88_dvb: Unknown symbol videobuf_dvb_register
[   20.740000] cx88_dvb: Unknown symbol cx8802_buf_prepare
[   20.740000] cx88_dvb: Unknown symbol cx88_free_buffer
[   20.740000] cx88_dvb: Unknown symbol cx88_boards
[   20.740000] cx88_dvb: Unknown symbol cx8802_buf_queue
[   20.776000] w83627hf: Found W83697HF chip at 0x290
[   20.868000] Adding 2000052k swap on /dev/hda6.  Priority:-1 extents:1 across:2000052k
......


Note that all files lised by modrpobe cx88-dvb is on their paths.

Thank U for any advises. I really appreciate it. If U will need some more info I will post it asap.

PS: This is my first post, so pls taky my pardon if I posted into wrong section or something similar.

PS2: sry for my english, not even close language ;)

---

### Post by elbeasto on 2008-02-04
I'm having the exact same problem!

If someone could post a fix.... :-)

---

### Post by r57 on 2008-02-04
Hi, I "solved" this problem recently by reinstalling ubuntu and everthing works well now. But of course... it's not a solution.

---

### Post by huntercj on 2008-02-08
I have the same problem with a Nova S Plus in Mythbuntu. It appears to have occurred after a reboot requested by the system after a routine update. Worked absolutely fine up until then. I'm not at all keen on the re-install Mythbuntu approach....

Can anybody help? I think I've tried all of the obvious stuff. :(

---

### Post by r57 on 2008-02-08
huntercj: my "lucky" update was an kernel update. after it U need to recompile all kernel modules that U had before update. May be this is your case. But I havent add/replace anything in kernel.... so... still dunno what happened :(

---

### Post by huntercj on 2008-02-10
r57, thank you, how right you were. Now I know another of Linux's dirty little secrets. I wouldn't have worked that out myself anytime soon. I guess I need to keep a note of all the extra kernel modules I add and manually reinstall after a kernel upgrade.

In this case I had to reinstall v4l-dvb. For me I followed steps 3 to 6 of the following Ubuntu forum post.

[http://ubuntuforums.org/showthread.php?t=246959](http://ubuntuforums.org/showthread.php?t=246959)

After the reboot all is up and running again. Well, as good as it ever was. When I ran Kaffeine it locked and I had to kill it and run again and then it worked. This seems to pretty normal for my setup. Must study the log files and track down the glitch sometime. Right now, I just leave Kaffeine running 24/7 and turn the TV and surround receiver off. Works for me. :)

---

### Post by r57 on 2008-02-10
Glad U made it ;-)

---

