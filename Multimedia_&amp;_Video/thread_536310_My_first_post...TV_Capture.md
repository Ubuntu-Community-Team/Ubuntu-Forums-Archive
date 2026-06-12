---
title: "My first post...TV Capture"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by jack.manfred on 2007-08-27
Hi,

I was wondering if anyone could point me in the right direction. I'm running 7.04 (Feisty Fawn) and am trying to get the Happuage WinTV Nova-T-USB2 external TV card to work.

I've read numerous posts about how to get similar chipsets working and managed to get the firmware working i think, heres the output of "lsusb" & cat /var/log/dmesg grep dvb

Bus 003 Device 004: ID 1516:8628
Bus 003 Device 003: ID 2040:9301 Hauppauge WinTV NOVA-T USB2 (warm) 

[   37.960794] dvb-usb: found a 'Hauppauge WinTV-NOVA-T usb2' in warm 
state.
[   37.961029] dvb-usb: will pass the complete MPEG2 transport stream to 
the software demuxer.
[   37.965910] dvb-usb: MAC address: 00:0d:fe:02:32:bf
[   38.076227] dvb-usb: schedule remote query interval to 100 msecs.
[   38.076231] dvb-usb: Hauppauge WinTV-NOVA-T usb2 successfully 
initialized and connected.
[   38.076248] usbcore: registered new interface driver 
dvb_usb_nova_t_usb2
m@m-desktop:~$ cat /var/log/dmesg | grep dvb
[   37.960794] dvb-usb: found a 'Hauppauge WinTV-NOVA-T usb2' in warm 
state.
[   37.961029] dvb-usb: will pass the complete MPEG2 transport stream to 
the software demuxer.
[   37.965910] dvb-usb: MAC address: 00:0d:fe:02:32:bf
[   38.076227] dvb-usb: schedule remote query interval to 100 msecs.
[   38.076231] dvb-usb: Hauppauge WinTV-NOVA-T usb2 successfully 
initialized and connected.
[   38.076248] usbcore: registered new interface driver 
dvb_usb_nova_t_usb2

The problem happens when i scan for any tv channels it says:

main2247: FATAL: failed to open '/dev/dvb/adapter0/fontend0': is 16 Device or resource busy

What can i try next?

Thanks

J

---

