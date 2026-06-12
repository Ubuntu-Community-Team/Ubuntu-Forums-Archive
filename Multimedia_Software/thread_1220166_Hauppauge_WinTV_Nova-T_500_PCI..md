---
title: "Hauppauge WinTV Nova-T 500 PCI."
date: 2009-07-22
forum: Multimedia Software
---

### Post by capo1949 on 2009-07-22
Hi All

I have a dell dimension 8400 running Jaunty 9.04, fitted with a Hauppauge WinTV Nova-T 500 PCI. 

When I start me tv the scan wizard appears with DiBcom 3000MC/P advised as the device and scan by location selected, but both select your country and region are greyed out.

I have followed [http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI) to the letter except that I am very nervous about changing the kernel on 9.04.

Below is the output from dmesg, which looks to me that it should be working?

graham@graham-desktop:~$ dmesg | grep -i dvb
[   13.355757] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   13.355761] usb 2-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[   13.431533] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   14.159257] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   14.159332] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   14.159614] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   14.282703] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
[   14.854775] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   14.855014] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   14.860908] DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
[   15.420916] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:04:00.2/usb2/2-1/input/input6
[   15.423503] dvb-usb: schedule remote query interval to 50 msecs.
[   15.423510] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   15.423702] usbcore: registered new interface driver dvb_usb_dib0700

I would gratefully appreciate any assistance

Graham

---

### Post by HappyFeet on 2009-07-22
Try to play it with vlc. Media>Open capture device>DVB from pull down menu>play.

---

### Post by xc3RnbFO8P on 2009-07-22
> dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected
It seems to be working.
Try Kaffeine.

---

### Post by capo1949 on 2009-07-23
Hi

Thanks for your response.

I am using gnome so cannot try kaffeine.

I downloaded the vlc and installed. on trying as advised, got an error:-

Your input can't be opened:
VLC is unable to open the MRL 'dvb://'. Check the log for details.

Looked around the application and could find no log?

graham

---

### Post by xc3RnbFO8P on 2009-07-23
> I am using gnome so cannot try kaffeine.
Yes we can :)

---

### Post by capo1949 on 2009-07-23
Hi

Thanks for your response.

HEY, downloaded Kaffeine and worked first time. Thanks for your help all


graham

---

