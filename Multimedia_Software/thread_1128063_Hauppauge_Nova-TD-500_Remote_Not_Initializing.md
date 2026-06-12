---
title: "Hauppauge Nova-TD-500 Remote Not Initializing"
date: 2009-04-17
forum: Multimedia Software
---

### Post by fastfret79 on 2009-04-17
The card is working perfectly with MythTV apart from the IR receiver is not being initialized. 

Here's what I get from a 'dmesg | grep -i dvb':

```
[   17.754761] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[   17.754766] firmware: requesting dvb-usb-dib0700-1.10.fw
[   18.481604] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   19.192541] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   19.192624] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   19.192839] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   19.425753] DVB: registering frontend 0 (DiBcom 7000PC)...
[   19.609393] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   19.609602] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   19.761155] DVB: registering frontend 1 (DiBcom 7000PC)...
[   19.945421] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   19.945700] usbcore: registered new interface driver dvb_usb_dib0700

```

As you can see it registers each tuner correctly, but according to [http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Quick_test]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Quick_test") I should see something similar to this:

```
input: IR-receiver inside an USB DVB receiver as /class/input/input4
```

I know that the IR Receiver can be disabled in your /etc/modprobe.d/options but that isn't the case here.

I even tried the dvb-usb-dib0700-1.20.fw firmware, but that didn't make any difference so I reverted back to dvb-usb-dib0700-1.10.fw

Any ideas why it's not initializing?

---

### Post by tlight on 2009-04-19
Ditto - would like to figure out how to enable it, admittedly I don't have an IR receiver (not in packaging??) that may have something to do with it perhaps?

---

### Post by abjt on 2009-04-28
I had a similar problem (although my card starts with 52xxx instead of 8xxxx in your case).

If you are using the remote that came with the Hauppauge, then you need to download the latest firmware (1.20 - you seem to have 1.10) and recompile.

have a look at this for detailed steps...[http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#IR_Receiver](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#IR_Receiver)

it does refer to the 1.10 firmware, but same works for 1.20

hope this helps..

---

