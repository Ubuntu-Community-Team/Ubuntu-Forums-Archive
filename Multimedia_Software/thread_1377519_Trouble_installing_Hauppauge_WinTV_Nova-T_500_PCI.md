---
title: "Trouble installing Hauppauge WinTV Nova-T 500 PCI"
date: 2010-01-10
forum: Multimedia Software
---

### Post by DannyBoy99 on 2010-01-10
Hi all, I am an Ubuntu newbie with trouble installing my tv card on 9.10.

I am following the Myth TV install guide here:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

And also the instructions for installing my tv card here:
[http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI)

I believe the installation completed without error, yet when I come to test the card using the instructions here: [http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php) I get an error after running the command: scan /usr/share/dvb/dvb-t/uk-Rowridge > /root/.tzap/channels.conf

[I]scanning /usr/share/dvb/dvb-t/uk-Rowridge
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
[/I]

I dont have a /dev/dvb directory so this is obviously the reason it fails.

If I run grep -i dvb /var/log/messages I get a huge list of devices and messages, here's a small sample:

[I]an 10 15:27:43 HTPC kernel: [ 1215.221506] cx88_dvb: disagrees about version of symbol dvb_unregister_frontend
Jan 10 15:27:43 HTPC kernel: [ 1215.221510] cx88_dvb: Unknown symbol dvb_unregister_frontend
Jan 10 15:27:43 HTPC kernel: [ 1215.221654] cx88_dvb: Unknown symbol videobuf_dvb_dealloc_frontends
Jan 10 15:27:43 HTPC kernel: [ 1215.221741] cx88_dvb: Unknown symbol videobuf_dvb_find_frontend
Jan 10 15:27:43 HTPC kernel: [ 1215.299373] dst_ca: disagrees about version of symbol dvb_register_device
Jan 10 15:27:43 HTPC kernel: [ 1215.299379] dst_ca: Unknown symbol dvb_register_device
Jan 10 15:42:14 HTPC kernel: [  757.717459] usbcore: registered new interface driver dvb_usb_dib0700
Jan 10 15:58:05 HTPC kernel: [  736.961587] usbcore: registered new interface driver dvb_usb_ttusb2
[/I]

dmesg | grep -i dvb
[  109.013726] usbcore: registered new interface driver dvb_usb_dib0700


I'm expecting a bigger output than this, am I right? Something like: 

[I][   30.965645] dib0700: loaded with support for 5 different device-types
[   30.965925] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   31.008899] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-03-pre1.fw'
[   31.206081] dib0700: firmware started successfully.
[   31.711176] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   31.711222] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   31.711325] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   31.831535] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   31.854890] MT2060: successfully identified (IF1 = 1220)
[   32.388673] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   32.388853] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   32.394293] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   32.398790] MT2060: successfully identified (IF1 = 1220)
[   32.959607] input: IR-receiver inside an USB DVB receiver as /class/input/input4
[   32.959633] dvb-usb: schedule remote query interval to 150 msecs.
[   32.959637] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   32.959657] usbcore: registered new interface driver dvb_usb_dib0700
[/I]

Like I said, I believe the installation was successful as I didnt see any errors during the make, make install, and make load commands specified.

Can anyone give me any pointers in the right direction? Many thanks.

Dan

---

