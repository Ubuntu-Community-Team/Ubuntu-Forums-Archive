---
title: "Please Help! Freecom USB DVB-t Kaffeine Problem"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by rupes on 2006-09-01
I managed to get my freeview tuner working with Kaffeine and had even recorded some programs.

I turned the computer on this morning to set some timers and its not working. Whenever I launch Kaffeine it says 'Can't bind info socket !!!'. I haven't changed any settings or anything so I'm really puzzled :confused: . I have tried reinstaling drivers and Kaffeine to no success. :( 

I'm really new to ubuntu/linux so please make your answers easy to follow. ;) 

Thanks

Rupes

---

### Post by bricha on 2006-09-01
I have the same problem as [COLOR="Red"]rupes[/COLOR]. I followed the procedure in the LinuxTVWiki and received the same message. Dmesg says:

[COLOR="Blue"][17179592.896000] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in cold state, will try to load a firmware[/COLOR]
[COLOR="Black"][17179593.076000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 217
[17179593.076000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179593.104000] ts: Compaq touchscreen protocol output
[17179593.148000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179593.260000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1[/COLOR]
[COLOR="Blue"]17179593.264000] dvb-usb: did not find the firmware file. (dvb-usb-wt220u-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems.
[17179593.264000] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) error while loading driver (-2)
[/COLOR]
If I start Windoze first (where the Stick works) and then restart into Dapper, the Stick is recognised, all the Channels are there and can be selected but without audio. Dmesg says:

[COLOR="Blue"][17179594.084000] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in warm state.
[17179594.084000] dvb-usb: will use the device's hardware PID filter (table count: 15).
[17179594.084000] DVB: registering new adapter (WideView WT-220U PenType Receiver (Typhoon/Freecom)).
[17179594.084000] DVB: registering frontend 0 (WideView USB DVB-T)...
[17179594.088000] input: IR-receiver inside an USB DVB receiver as /class/input/input4
[17179594.088000] dvb-usb: schedule remote query interval to 300 msecs.
[17179594.088000] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
[/COLOR]
There seem to be two versions of firmware, dvb-usb-wt220u-02.fw and dvb-usb-wt220u-zl0353-01.fw. I think the latter includes remote control. I note that a previous version is being looked for in the unsuccessful boot but I would expect later versions to be acceptable. The Wiki says the firmware should be in either /lib/firmware or /usr/lib/hotplug/firmware. The latter does not exist on my machine. I have tried the /lib/firmware location and in the kernel folder but there is no difference.

If I unplug the Stick when it is 'working' and then re-insert it, it reverts to the non-working state. This means to me that hotplug is not working or the firmware is not in a location where hotplug can detect it.

I have now reached the limited level of my competence and would welcome any help I can get. My sole consolation is, as others have observed, that the video under Dapper is superior to the Windoze version.

BTW, this is my first post.

brianr

---

