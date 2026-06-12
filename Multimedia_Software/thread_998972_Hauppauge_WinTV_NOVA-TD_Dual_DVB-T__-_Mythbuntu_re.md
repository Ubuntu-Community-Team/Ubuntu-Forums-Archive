---
title: "Hauppauge WinTV NOVA-TD Dual DVB-T  - Mythbuntu remote"
date: 2008-12-01
forum: Multimedia Software
---

### Post by birdmanuk on 2008-12-01
I have just installed my new Asus eee box with Mythbuntu. So far most things are working well, although I am having problems with the remote control.

System config -

Mythbuntu 8.10

USB - Hauppauge WinTV NOVA-TD Dual DVB-T

dmesg | grep dvb
[   15.448264] dvb-usb: found a 'Hauppauge Nova-TD Stick (52009)' in warm state.
[   15.448450] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.899869] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.320397] dvb-usb: Hauppauge Nova-TD Stick (52009) successfully initialized and connected.
[   16.324236] usbcore: registered new interface driver dvb_usb_dib0700

I can watch and record tv, but can't get lirc to work.

Anyone got this working with the usb Hauppauge?

Thanks

---

### Post by Fungyo on 2008-12-01
See if any info here can help
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI")

---

### Post by birdmanuk on 2008-12-03
Thanks for the reply, I'm afraid I have fallen at the first hurdle, I can see the device start, but I don't see:- 

"input: IR-receiver inside an USB DVB receiver as /class/input/input4
"

I'm not sure if anyone has got this working with the USB stick model??

USB - Hauppauge WinTV NOVA-TD Dual DVB-T

dmesg | grep dvb
[   15.448264] dvb-usb: found a 'Hauppauge Nova-TD Stick (52009)' in warm state.
[   15.448450] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.899869] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.320397] dvb-usb: Hauppauge Nova-TD Stick (52009) successfully initialized and connected.
[   16.324236] usbcore: registered new interface driver dvb_usb_dib0700

---

### Post by birdmanuk on 2008-12-10
As I can't seem to find a soloution to this, can anyone recommend a remote to use?

---

### Post by birdmanuk on 2008-12-17
After a bit of searching, I found that I can use my iPhone :-)

Works a treat - just download and install MyMote from the App store.

---

### Post by Trist on 2008-12-17
Hi,
I have a WinTV NOVA-TD USB stick and mine work's out of the box. When you install mythbuntu just select the WinTV Nova-T 500 remote, its exactly the same remote as the Nova-TD.

---

### Post by gianpiero on 2009-01-22
@birdmanuk
Hello!, I bought the same card usb: Hauppauge WinTV NOVA-TD Dual DVB-T, but it doesn't work in my Mythubuntu 8.04, I receive the error:
```
you should have gotten a channel by now. 
You can continue to wait for a signal or  can change the channels with Up or down, change video sources, input 
```

When you chosed the Capture Cards which you chosed? The DVB, or MPEG-2???
Did you chose only one Capture Cards or two(Dual DVB-T)?

Thank you very much!!!!!

---

### Post by effing on 2009-02-03
Hi Everybody,

yesterday night I tried to install mythbuntu with the Nova Dual USB-Stick and I ended up with the same problem birdmanuk had: TV-Functions allright, no remote control. 

dmesg | grep dvb shows the excatly the same. I found a lot of tutorials how to integrate the ir, but they were all quite old and Im too much a newbie to decide which one is still necessary in Mythbuntu 8.10. 

Did anybody solve this problem?

Greetings,

effing

---

