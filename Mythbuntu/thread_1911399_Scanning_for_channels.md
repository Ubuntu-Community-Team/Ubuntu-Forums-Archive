---
title: "Scanning for channels"
date: 2012-01-18
forum: Mythbuntu
---

### Post by langner on 2012-01-18
Dear all,

I have been trying to scan for channels for the past day and get nothing. I have a DVB-S2 card which according to the terminal is install correctly. See quote 1.

In the backend I have set it to DVB capture card (v3.x) and can see a DVB-S2 card listed below it. I have done the listings for the Radio times and set this option, (video source), when scanning for channels. I have upped both the signal timeout from 7000 to 60000 and the turning timeout to 62500, see [parker1.co.uk/mythtv_freesat.php]("parker1.co.uk/mythtv_freesat.php"). 

I have tried both the settings for SD and HD setting when scanning that are listed on the above site. Each time I get only a reading on 'Single/Noise' at 100%. After a time no channels window comes up and I am back where I started. 

On the above site it says have a look at /var/log/kern.log. I have done this and it means _____ all to me but there are some errors at the end. See quote 2. 

Thanks for your help on this, (because if I can't get this sorted I'll be in the back books with the wife)

Matthew 

Quote 1
> myth@desktop:~$ dmesg | grep cx88
[   16.899575] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.9 loaded
[   16.937631] cx88/0: cx2388x v4l2 driver version 0.0.9 loaded
[   17.139174] cx88[0]: subsystem: 8920:8888, board: TBS 8920 DVB-S/S2 [card=72,autodetected], frontend(s): 1
[   17.139178] cx88[0]: TV tuner type 4, Radio tuner type -1
[   17.700151] input: cx88 IR (TBS 8920 DVB-S/S2) as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/rc/rc0/input5
[   17.700256] rc0: cx88 IR (TBS 8920 DVB-S/S2) as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/rc/rc0
[   17.700376] input: MCE IR Keyboard/Mouse (cx88xx) as /devices/virtual/input/input6
[   17.700499] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
[   17.700505] cx88[0]/2: cx2388x 8802 Driver Manager
[   17.700540] cx88-mpeg driver manager 0000:03:06.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.700550] cx88[0]/2: found at 0000:03:06.2, rev: 5, irq: 21, latency: 64, mmio: 0xfc000000
[   17.701670] cx8800 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.701682] cx88[0]/0: found at 0000:03:06.0, rev: 5, irq: 21, latency: 64, mmio: 0xfd000000
[   17.701867] cx88[0]/0: registered device video0 [v4l2]
[   17.701903] cx88[0]/0: registered device vbi0
[   17.709104] cx88/2: cx2388x dvb driver version 0.0.9 loaded
[   17.709109] cx88/2: registering cx8802 driver, type: dvb access: shared
[   17.709115] cx88[0]/2: subsystem: 8920:8888, board: TBS 8920 DVB-S/S2 [card=72]
[   17.709120] cx88[0]/2: cx2388x based DVB/ATSC card
[   17.709122] cx8802_alloc_frontends() allocating 1 frontend(s)
[   17.714862] DVB: registering new adapter (cx88[0])



Quote 2
> 
**This is the end of the log. Too big to fit in this help post**

Jan 19 00:15:03 desktop kernel: [ 5235.615409] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
Jan 19 00:15:03 desktop kernel: [ 5235.615414] cx24116_firmware_ondemand: No firmware uploaded (timeout or file not found?)
Jan 19 00:15:03 desktop kernel: [ 5235.615417] cx24116_cmd_execute(): Unable initialise the firmware
Jan 19 00:16:07 desktop kernel: [ 5299.800840] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
Jan 19 00:16:07 desktop kernel: [ 5299.805165] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
Jan 19 00:16:07 desktop kernel: [ 5299.805172] cx24116_firmware_ondemand: No firmware uploaded (timeout or file not found?)
Jan 19 00:16:07 desktop kernel: [ 5299.805178] cx24116_cmd_execute(): Unable initialise the firmware
Jan 19 00:16:24 desktop kernel: [ 5316.845543] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
Jan 19 00:16:24 desktop kernel: [ 5316.849746] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
Jan 19 00:16:24 desktop kernel: [ 5316.849753] cx24116_firmware_ondemand: No firmware uploaded (timeout or file not found?)
Jan 19 00:16:24 desktop kernel: [ 5316.849759] cx24116_cmd_execute(): Unable initialise the firmware
Jan 19 00:16:27 desktop kernel: [ 5319.974622] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
Jan 19 00:16:27 desktop kernel: [ 5319.978632] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
Jan 19 00:16:27 desktop kernel: [ 5319.978638] cx24116_firmware_ondemand: No firmware uploaded (timeout or file not found?)
Jan 19 00:16:27 desktop kernel: [ 5319.978645] cx24116_cmd_execute(): Unable initialise the firmware

---

### Post by langner on 2012-01-18
Hi all,

Can I just say one thing before I go on,


aaaaaaaaaaaaaaaaaaaaaaahhhhhhhhhhhhhhhhhhhhhhhhhhh

Thanks

Now I know what I did wrong so don't fall into the same trap as I did. I forgot to copy a file into the firmware folder. That is what is at the end of quote 2.  *No firmware uploaded*. 

It works now. 

So the moral of the story is, read all of the instructions; don't just try to remember it.

Thanks for reading

---

