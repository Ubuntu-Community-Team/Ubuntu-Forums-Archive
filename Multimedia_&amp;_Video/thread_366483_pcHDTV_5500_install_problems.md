---
title: "pcHDTV 5500 install problems"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by d0rp on 2007-02-20
I've been having some issues getting my pcHDTV 5500 card to work with my Edgy installation. I had this same system running under Gentoo, but after playing around with Ubuntu on another machine, I decided to give it a shot with this machine because there were some software issues that I never bothered to fix. Every other aspect of the install was fantastically easier than my previous Gentoo installation, but I can't seem to get this card to work.

I downloaded and installed the v4l-dvb-HD-5500-driver.tar.gz and dvb-atsc-tools-1.0.4.tar.gz, but it didn't just work like I thought it would. After doing some google searching, I found a few things that people suggested, but none of them has worked.

When I do a 
```
$ dtvsignal 19
```

This is what I get:
> using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: failed opening '/dev/dvb/adapter0/frontend0' (No such file or directory)
dtvsignal ver 1.0.4 - by Jack Kelliher (c) 2002,2005,2006
channel = 19 freq = 503000000Hz
 30db       0%         25%         50%         75%        100%
Signal:     |     .     :     .     |     ._____:_____._____|
Signal: 087 $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

It says that it can't find the device files, but the fact that it does show that I am getting a signal (and it's different for each channel) makes me think that it recognizes the card at least at some level.

I tried copying 
> /lib/firmware/v4l-cx2341x-enc.fw
/lib/firmware/v4l-cx25840.fw
/lib/firmware/v4l-cx2341x-dec.fw
to
> /lib/firmware/2.6.17-11-generic/

but that didn't seem to help much.

When I try to 

```
$ sudo modprobe cx88_dvb
```

I get the following:

> WARNING: Error inserting cx88xx (/lib/modules/2.6.17-11-generic/kernel/drivers/media/video/cx88/cx88xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cx8802 (/lib/modules/2.6.17-11-generic/kernel/drivers/media/video/cx88/cx8802.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.17-11-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and a 
```
$ dmesg | grep cx88
```

produces:

> [17179589.392000] cx88xx: Unknown parameter `index'
[17179589.400000] cx8800: Unknown symbol cx88_reset
[17179589.400000] cx8800: Unknown symbol cx88_call_i2c_clients
[17179589.400000] cx8800: Unknown symbol cx88_wakeup
[17179589.400000] cx8800: Unknown symbol cx88_risc_stopper
[17179589.400000] cx8800: Unknown symbol cx88_print_irqbits
[17179589.400000] cx8800: Unknown symbol cx88_set_scale
[17179589.400000] cx8800: Unknown symbol cx88_shutdown
[17179589.400000] cx8800: Unknown symbol cx88_vdev_init
[17179589.400000] cx8800: Unknown symbol cx88_core_put
[17179589.400000] cx8800: Unknown symbol cx88_audio_thread
[17179589.400000] cx8800: Unknown symbol cx88_core_irq
[17179589.400000] cx8800: Unknown symbol cx88_core_get
[17179589.400000] cx8800: Unknown symbol cx88_get_stereo
[17179589.400000] cx8800: Unknown symbol cx88_set_tvnorm
[17179589.400000] cx8800: Unknown symbol cx88_risc_buffer
[17179589.400000] cx8800: Unknown symbol cx88_set_stereo
[17179589.400000] cx8800: Unknown symbol cx88_sram_channels
[17179589.400000] cx8800: Unknown symbol cx88_set_tvaudio
[17179589.400000] cx8800: Unknown symbol cx88_sram_channel_dump
[17179589.400000] cx8800: Unknown symbol cx88_sram_channel_setup
[17179589.400000] cx8800: Unknown symbol cx88_free_buffer
[17179589.400000] cx8800: Unknown symbol cx88_boards
[17179589.400000] cx8800: Unknown symbol cx88_newstation
[17179591.580000] cx88xx: Unknown parameter `index'
[17179591.584000] cx8802: Unknown symbol cx88_reset
[17179591.584000] cx8802: Unknown symbol cx88_wakeup
[17179591.584000] cx8802: Unknown symbol cx88_risc_stopper
[17179591.584000] cx8802: Unknown symbol cx88_print_irqbits
[17179591.584000] cx8802: Unknown symbol cx88_shutdown
[17179591.584000] cx8802: Unknown symbol cx88_core_irq
[17179591.584000] cx8802: Unknown symbol cx88_sram_channels
[17179591.584000] cx8802: Unknown symbol cx88_sram_channel_dump
[17179591.584000] cx8802: Unknown symbol cx88_sram_channel_setup
[17179591.584000] cx8802: Unknown symbol cx88_free_buffer
[17179591.584000] cx8802: Unknown symbol cx88_boards
[17179591.584000] cx8802: Unknown symbol cx88_risc_databuffer
[17179592.520000] cx88_dvb: Unknown symbol cx8802_fini_common
[17179592.520000] cx88_dvb: Unknown symbol cx88_call_i2c_clients
[17179592.520000] cx88_dvb: Unknown symbol cx88_core_put
[17179592.520000] cx88_dvb: Unknown symbol cx88_core_get
[17179592.520000] cx88_dvb: Unknown symbol cx8802_resume_common
[17179592.520000] cx88_dvb: Unknown symbol cx8802_buf_prepare
[17179592.520000] cx88_dvb: Unknown symbol cx8802_init_common
[17179592.520000] cx88_dvb: Unknown symbol cx88_free_buffer
[17179592.520000] cx88_dvb: Unknown symbol cx88_boards
[17179592.520000] cx88_dvb: Unknown symbol cx8802_buf_queue
[17179592.520000] cx88_dvb: Unknown symbol cx8802_suspend_common
[17179592.544000] cx88xx: Unknown parameter `index'
[17179592.544000] cx8800: Unknown symbol cx88_reset
[17179592.544000] cx8800: Unknown symbol cx88_call_i2c_clients
[17179592.544000] cx8800: Unknown symbol cx88_wakeup
[17179592.544000] cx8800: Unknown symbol cx88_risc_stopper
[17179592.544000] cx8800: Unknown symbol cx88_print_irqbits
[17179592.544000] cx8800: Unknown symbol cx88_set_scale
[17179592.544000] cx8800: Unknown symbol cx88_shutdown
[17179592.544000] cx8800: Unknown symbol cx88_vdev_init
[17179592.544000] cx8800: Unknown symbol cx88_core_put
[17179592.544000] cx8800: Unknown symbol cx88_audio_thread
[17179592.544000] cx8800: Unknown symbol cx88_core_irq
[17179592.544000] cx8800: Unknown symbol cx88_core_get
[17179592.544000] cx8800: Unknown symbol cx88_get_stereo
[17179592.544000] cx8800: Unknown symbol cx88_set_tvnorm
[17179592.544000] cx8800: Unknown symbol cx88_risc_buffer
[17179592.544000] cx8800: Unknown symbol cx88_set_stereo
[17179592.544000] cx8800: Unknown symbol cx88_sram_channels
[17179592.544000] cx8800: Unknown symbol cx88_set_tvaudio
[17179592.544000] cx8800: Unknown symbol cx88_sram_channel_dump
[17179592.544000] cx8800: Unknown symbol cx88_sram_channel_setup
[17179592.544000] cx8800: Unknown symbol cx88_free_buffer
[17179592.544000] cx8800: Unknown symbol cx88_boards
[17179592.544000] cx8800: Unknown symbol cx88_newstation
[17179592.548000] cx8802: Unknown symbol cx88_reset
[17179592.548000] cx8802: Unknown symbol cx88_wakeup
[17179592.548000] cx8802: Unknown symbol cx88_risc_stopper
[17179592.548000] cx8802: Unknown symbol cx88_print_irqbits
[17179592.548000] cx8802: Unknown symbol cx88_shutdown
[17179592.548000] cx8802: Unknown symbol cx88_core_irq
[17179592.548000] cx8802: Unknown symbol cx88_sram_channels
[17179592.548000] cx8802: Unknown symbol cx88_sram_channel_dump
[17179592.548000] cx8802: Unknown symbol cx88_sram_channel_setup
[17179592.548000] cx8802: Unknown symbol cx88_free_buffer
[17179592.548000] cx8802: Unknown symbol cx88_boards
[17179592.548000] cx8802: Unknown symbol cx88_risc_databuffer
[17179592.552000] cx88_blackbird: Unknown symbol cx8802_fini_common
[17179592.552000] cx88_blackbird: Unknown symbol cx88_set_scale
[17179592.552000] cx88_blackbird: Unknown symbol cx88_vdev_init
[17179592.552000] cx88_blackbird: Unknown symbol cx88_core_put
[17179592.552000] cx88_blackbird: Unknown symbol cx88_core_get
[17179592.552000] cx88_blackbird: Unknown symbol cx8802_resume_common
[17179592.552000] cx88_blackbird: Unknown symbol cx8802_buf_prepare
[17179592.552000] cx88_blackbird: Unknown symbol cx88_do_ioctl
[17179592.552000] cx88_blackbird: Unknown symbol cx8802_init_common
[17179592.552000] cx88_blackbird: Unknown symbol cx88_free_buffer
[17179592.552000] cx88_blackbird: Unknown symbol cx88_boards
[17179592.552000] cx88_blackbird: Unknown symbol cx8802_buf_queue
[17179592.552000] cx88_blackbird: Unknown symbol cx8802_suspend_common
[17179592.584000] cx88xx: Unknown parameter `index'
[17179592.600000] cx88_alsa: Unknown symbol cx88_reset
[17179592.600000] cx88_alsa: Unknown symbol cx88_print_irqbits
[17179592.600000] cx88_alsa: Unknown symbol cx88_core_put
[17179592.600000] cx88_alsa: Unknown symbol cx88_core_get
[17179592.600000] cx88_alsa: Unknown symbol cx88_sram_channels
[17179592.600000] cx88_alsa: Unknown symbol cx88_sram_channel_dump
[17179592.600000] cx88_alsa: Unknown symbol cx88_sram_channel_setup
[17179592.600000] cx88_alsa: Unknown symbol cx88_risc_databuffer
[17179943.812000] cx88xx: Unknown parameter `index'
[17179943.820000] cx8802: Unknown symbol cx88_reset
[17179943.820000] cx8802: Unknown symbol cx88_wakeup
[17179943.820000] cx8802: Unknown symbol cx88_risc_stopper
[17179943.820000] cx8802: Unknown symbol cx88_print_irqbits
[17179943.820000] cx8802: Unknown symbol cx88_shutdown
[17179943.820000] cx8802: Unknown symbol cx88_core_irq
[17179943.820000] cx8802: Unknown symbol cx88_sram_channels
[17179943.820000] cx8802: Unknown symbol cx88_sram_channel_dump
[17179943.820000] cx8802: Unknown symbol cx88_sram_channel_setup
[17179943.820000] cx8802: Unknown symbol cx88_free_buffer
[17179943.820000] cx8802: Unknown symbol cx88_boards
[17179943.820000] cx8802: Unknown symbol cx88_risc_databuffer
[17179943.824000] cx88_dvb: Unknown symbol cx8802_fini_common
[17179943.824000] cx88_dvb: Unknown symbol cx88_call_i2c_clients
[17179943.824000] cx88_dvb: Unknown symbol cx88_core_put
[17179943.824000] cx88_dvb: Unknown symbol cx88_core_get
[17179943.824000] cx88_dvb: Unknown symbol cx8802_resume_common
[17179943.824000] cx88_dvb: Unknown symbol cx8802_buf_prepare
[17179943.824000] cx88_dvb: Unknown symbol cx8802_init_common
[17179943.824000] cx88_dvb: Unknown symbol cx88_free_buffer
[17179943.824000] cx88_dvb: Unknown symbol cx88_boards
[17179943.824000] cx88_dvb: Unknown symbol cx8802_buf_queue
[17179943.824000] cx88_dvb: Unknown symbol cx8802_suspend_common
[17179983.368000] cx88xx: Unknown parameter `index'
[17179983.372000] cx8802: Unknown symbol cx88_reset
[17179983.372000] cx8802: Unknown symbol cx88_wakeup
[17179983.372000] cx8802: Unknown symbol cx88_risc_stopper
[17179983.372000] cx8802: Unknown symbol cx88_print_irqbits
[17179983.372000] cx8802: Unknown symbol cx88_shutdown
[17179983.372000] cx8802: Unknown symbol cx88_core_irq
[17179983.372000] cx8802: Unknown symbol cx88_sram_channels
[17179983.372000] cx8802: Unknown symbol cx88_sram_channel_dump
[17179983.372000] cx8802: Unknown symbol cx88_sram_channel_setup
[17179983.372000] cx8802: Unknown symbol cx88_free_buffer
[17179983.372000] cx8802: Unknown symbol cx88_boards
[17179983.372000] cx8802: Unknown symbol cx88_risc_databuffer
[17179983.372000] cx88_dvb: Unknown symbol cx8802_fini_common
[17179983.372000] cx88_dvb: Unknown symbol cx88_call_i2c_clients
[17179983.372000] cx88_dvb: Unknown symbol cx88_core_put
[17179983.372000] cx88_dvb: Unknown symbol cx88_core_get
[17179983.372000] cx88_dvb: Unknown symbol cx8802_resume_common
[17179983.372000] cx88_dvb: Unknown symbol cx8802_buf_prepare
[17179983.372000] cx88_dvb: Unknown symbol cx8802_init_common
[17179983.372000] cx88_dvb: Unknown symbol cx88_free_buffer
[17179983.372000] cx88_dvb: Unknown symbol cx88_boards
[17179983.372000] cx88_dvb: Unknown symbol cx8802_buf_queue
[17179983.372000] cx88_dvb: Unknown symbol cx8802_suspend_common
[17182878.952000] cx88xx: Unknown parameter `index'
[17186720.744000] cx88xx: Unknown parameter `index'
[17186720.756000] cx8802: Unknown symbol cx88_reset
[17186720.756000] cx8802: Unknown symbol cx88_wakeup
[17186720.756000] cx8802: Unknown symbol cx88_risc_stopper
[17186720.756000] cx8802: Unknown symbol cx88_print_irqbits
[17186720.756000] cx8802: Unknown symbol cx88_shutdown
[17186720.756000] cx8802: Unknown symbol cx88_core_irq
[17186720.756000] cx8802: Unknown symbol cx88_sram_channels
[17186720.756000] cx8802: Unknown symbol cx88_sram_channel_dump
[17186720.756000] cx8802: Unknown symbol cx88_sram_channel_setup
[17186720.756000] cx8802: Unknown symbol cx88_free_buffer
[17186720.756000] cx8802: Unknown symbol cx88_boards
[17186720.756000] cx8802: Unknown symbol cx88_risc_databuffer
[17186720.760000] cx88_dvb: Unknown symbol cx8802_fini_common
[17186720.760000] cx88_dvb: Unknown symbol cx88_call_i2c_clients
[17186720.760000] cx88_dvb: Unknown symbol cx88_core_put
[17186720.760000] cx88_dvb: Unknown symbol cx88_core_get
[17186720.760000] cx88_dvb: Unknown symbol cx8802_resume_common
[17186720.760000] cx88_dvb: Unknown symbol cx8802_buf_prepare
[17186720.760000] cx88_dvb: Unknown symbol cx8802_init_common
[17186720.760000] cx88_dvb: Unknown symbol cx88_free_buffer
[17186720.760000] cx88_dvb: Unknown symbol cx88_boards
[17186720.760000] cx88_dvb: Unknown symbol cx8802_buf_queue
[17186720.760000] cx88_dvb: Unknown symbol cx8802_suspend_common

I've also seen that some people's solution has been to install a 2.6.18 kernel with the default pcHDTV 5500 driver compiled in, but that seems a little drastic at this point, and I don't know how I would go about such an operation in Ubuntu.

Any suggestions would be greatly appreciated.

---

### Post by d0rp on 2007-02-22
I was able to get the card working:

I put the Live CD back in and booted from it and noticed that the cx88 drivers were all loaded, so I went ahead and rebuilt the whole system. Somehow along the way I must have done something to break them the first time.

Once I got the drivers loaded, I still had no /dev/dvb device files, which was frustrating until I took a look at my dmesg and noticed that the drivers were complaining that they couldn't determine what type of card it was (my pcHDTV 5500 is listed as card=47, but the list it had only went up to 46), so I went and downloaded and installed the drivers off of the pchdtv website and rebooted and everything worked fine from there on out.

---

