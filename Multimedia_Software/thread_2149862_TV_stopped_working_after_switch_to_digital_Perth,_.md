---
title: "TV stopped working after switch to digital? Perth, AF9015"
date: 2013-05-30
forum: Multimedia Software
---

### Post by AshNova on 2013-05-30
Hello,

I was using a Kworld tuner (AF9015), tvheadend and XBMC to watch TV. 

However, it appears after the switch to digital on 16th April, Live TV on XBMC no longer works. I was receiving digital channels before the switch.

 I think it's a problem on my end although I'm not sure what.

Could anyone please help me out?

This is the output of dmesg :

```

17.891731] dvb-usb: found a 'KWorld USB DVB-T TV Stick II (VS-DVB-T 395U)' in cold state, will try to load a firmware
[   17.964780] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   18.037749] dvb-usb: found a 'KWorld USB DVB-T TV Stick II (VS-DVB-T 395U)' in warm state.
[   18.037829] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   18.038474] DVB: registering new adapter (KWorld USB DVB-T TV Stick II (VS-DVB-T 395U))
[   18.060961] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/rc/rc0/input8
[   18.062411] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/rc/rc0
[   18.062414] dvb-usb: schedule remote query interval to 500 msecs.
[   18.062419] dvb-usb: KWorld USB DVB-T TV Stick II (VS-DVB-T 395U) successfully initialized and connected.
[   18.071986] usbcore: registered new interface driver dvb_usb_af9015

```

The firmware I'm using came from this website :

[http://palosaari.fi/linux/v4l-dvb/firmware/af9015/5.1.0.0/]("http://palosaari.fi/linux/v4l-dvb/firmware/af9015/5.1.0.0/")

tvheadend appears to be detecting something but I'm not sure what :

[ATTACH=CONFIG]243261[/ATTACH]

[ATTACH=CONFIG]243262[/ATTACH]

And the multiplexes shown here :
[ATTACH=CONFIG]243263[/ATTACH]

match up to these :
[http://ozdigitaltv.com/transmitters/WA/402-Bickley-Carmel-Walliston]("http://ozdigitaltv.com/transmitters/WA/402-Bickley-Carmel-Walliston")

but I can't map them to any dvb services.

Thank you.

---

### Post by AshNova on 2013-06-04
bump

---

