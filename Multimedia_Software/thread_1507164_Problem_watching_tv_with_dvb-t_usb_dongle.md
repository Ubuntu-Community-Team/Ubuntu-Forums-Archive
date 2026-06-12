---
title: "Problem watching tv with dvb-t usb dongle"
date: 2010-06-11
forum: Multimedia Software
---

### Post by mahdif62 on 2010-06-11
Hi everybody. I have a strange problem with my usb tv dongle. It's chipset is Realtek rtl2832u and I installed the driver from [http://www.turnovfree.net/~stybla/linux/v4l-dvb/lv5tdlx/linux_install_package_091207.rar](http://www.turnovfree.net/~stybla/linux/v4l-dvb/lv5tdlx/linux_install_package_091207.rar) and my dongle was detected and started working in ubuntu lucid. However when I reboot it does't work. The modules are loaded as I understand from the "lsmod | grep dvb output", but vlc and othe programs can't play live tv. Also the "scan" command fails to tune to channels, saying "tuning failed". 
The only workaround I've found is rebooting into Windows 7 and opening live tv with Windows Media Center. Afterwards when I reboot back to linux tv works! I think I need a way to "reset" the dongle so that I don't have to reboot into Windows and back into linux. can anyone please help me?

```
$ lsmod | grep dvb
dvb_usb_rtl2832u      126599  8 
dvb_usb                17567  1 dvb_usb_rtl2832u
dvb_core               85933  1 dvb_usb
```

```
$ dmesg | grep dvb
0......[   13.172804] dvb-usb: found a 'USB DVB-T Device' in warm state.
[   13.172810] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.176735] dvb-usb: USB DVB-T Device successfully initialized and connected.
[   13.176750] dvb-usb: found a 'USB DVB-T Device' in warm state.
[   13.176755] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.179271] dvb-usb: USB DVB-T Device successfully initialized and connected.
[   13.179292] usbcore: registered new interface driver dvb_usb_rtl2832u

```

---

