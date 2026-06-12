---
title: "WinTV NOVA DVB-S2 PCI Card"
date: 2009-02-08
forum: Multimedia Software
---

### Post by dsmith1974 on 2009-02-08
HI,

I'm now at the end of day five of trying to get TV sorted on Kubuntu - still good fun though!

The Environment: Kubuntu-64 2.6.27-11-generic, WinTV NOVA HD DVB-S2 PCI, ASUS Athena, Intel Q6600, 8GB

By following this thread [http://ubuntuforums.org/showthread.php?p=6391900](http://ubuntuforums.org/showthread.php?p=6391900) earlier, I'd managed to get my card working (briefly) by compiling the liplianin sources rather than v4l.  After a re-boot I could run scan on the astra 28.2e file and get all of the bbc/itv channels into a channels.conf (all good!).

Happy that the underlying dvb-s stuff was all working I started work on MythTV and somewhere along the way the card stopped working - now I've tried re-building from a clean system (many times) by make clean && remove, rm /lib/modules/2.6.27-11-generic/kernel/drivers/media/video/cx -f, physically removing the card, rebooting, re-building the latest v4l-dvb sources (tried v4l and liplianin now) using both the 32bit firmware, and then the 64bit firmware, this German hack [http://forum.ubuntuusers.de/topic/hauppauge-wintv-nova-hd-s2-einrichten/3/](http://forum.ubuntuusers.de/topic/hauppauge-wintv-nova-hd-s2-einrichten/3/) (though the patch file is no longer available - think it's been merged into the latest v4l sources anyway).

No matter how many combinations/attempts of cleaning and re-installing the dvb-drivers I make, am I able to get past this on start-up:

<code>
dusmith@dcfap1:~$ dmesg |grep cx
[   11.662728] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   11.663232] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
[   11.663234] cx88[0]: TV tuner type -1, Radio tuner type -1
[   11.673694] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   11.775436] cx2388x alsa driver version 0.0.6 loaded
[   12.069961] cx88[0]: hauppauge eeprom: model=69100
[   12.070018] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:1e.0/0000:05:01.2/input/input6
[   12.105600] cx88[0]/2: cx2388x 8802 Driver Manager
[   12.105614] cx88-mpeg driver manager 0000:05:01.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.105624] cx88[0]/2: found at 0000:05:01.2, rev: 5, irq: 17, latency: 64, mmio: 0xfc000000
[   12.105772] cx8800 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.105792] cx88[0]/0: found at 0000:05:01.0, rev: 5, irq: 17, latency: 64, mmio: 0xfa000000
[   12.105934] cx88[0]/0: registered device video0 [v4l2]
[   12.105966] cx88[0]/0: registered device vbi0
[   12.146406] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   12.146409] cx88/2: registering cx8802 driver, type: dvb access: shared
[   12.146412] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
[   12.146414] cx88[0]/2: cx2388x based DVB/ATSC card
[   12.146416] cx8802_alloc_frontends() allocating 1 frontend(s)
[   12.173681] cx88_audio 0000:05:01.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.173706] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   12.193985] cx88[0]/2: dvb_register failed (err = -22)
[   12.193990] cx88[0]/2: cx8802 probe failed, err = -22
</code>

Seems the card just fails to register 'dvb_register failed err -22'.  Is there anything more I can do?

Many thanks,

Duncan

---

