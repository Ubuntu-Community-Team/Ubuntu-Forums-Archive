---
title: "Hauppauge Nova-T-500 - No frontend attached"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by davmac on 2007-04-24
Hi folks,

I'm having problems with getting my Hauppauge Nova-T-500 dual DVB-T tuner running. If it is relevant, it is the half-height OEM version, rather than the retail version.

The box is a Dell Dimension 5000, initially running Edgy. I found out that the card needs a kernel >= 2.6.19 so I upgraded the box to feisty (2.6.20). I've found two pretty authoritative guides to getting this card working ([http://www.omskakas.se/2007/01/howto-hauppauge-nova-t-500-pci-under-linux.html](http://www.omskakas.se/2007/01/howto-hauppauge-nova-t-500-pci-under-linux.html) and [http://wiki.efficientpc.co.uk/index.php/Install_Nova-T_500_On_Ubuntu_Linux)](http://wiki.efficientpc.co.uk/index.php/Install_Nova-T_500_On_Ubuntu_Linux)). I've worked through both, carefully following all of the steps.

When I load the dvb-usb-dib0700 module, I get 

> mythtv@brianclough:~$ sudo modprobe -v dvb-usb-dib0700
insmod /lib/modules/2.6.20-15-generic/kernel/drivers/media/dvb/frontends/dib7000p.ko 
insmod /lib/modules/2.6.20-15-generic/kernel/drivers/media/dvb/frontends/dib7000m.ko 
insmod /lib/modules/2.6.20-15-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-dib0700.ko force_lna_activation=1 

which looks as expected, but I find the following in dmesg;

> [  129.916740] dib0700: loaded with support for 2 different device-types
[  130.003164] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[  130.003236] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  130.003624] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T).
[  130.090824] dvb-usb: no frontend was attached by 'Hauppauge Nova-T 500 Dual DVB-T'
[  130.090834] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  130.091231] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T).
[  130.091941] dvb-usb: no frontend was attached by 'Hauppauge Nova-T 500 Dual DVB-T'
[  130.091951] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[  130.092319] usbcore: registered new interface driver dvb_usb_dib0700

I think the relevant part here is the "no frontend was attached". When I run mythtv-setup, I can only find the one card (the twinhan).

I do have a twinhan usb DVB-T box successfully working. If I look in /dev/dvb/adapter2 I find demux0, dvr0, frontend0 and net0. If I look in /dev/dvb/adapter0 or /dev/dvb/adapter1 I only see demux0, dvr0 and net0.

If it is relevant the output of lsusb and lsmod is attached.

So what am I doing wrong? Any tips, advice or links that would help me diagnose or even solve the problem will be gratefully received.

Regards,

Dave MacLeod

---

### Post by iJebus on 2007-05-09
I too lack a frontend :( If someone can help you, maybe it will also solve my problem.

---

