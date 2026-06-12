---
title: "Nova-TD 500 IR Receiver not found"
date: 2009-02-19
forum: Mythbuntu
---

### Post by c-2501 on 2009-02-19
I've had my mythbuntu(8.10) system set up for a couple of weeks now and nearly everything is going fine.  The problem i am having though is that i cannot get the IR remote on the card to work.

When i looked at the dmesg output i noticed there was no mention of the IR receiver.

```

dmesg | grep -i dvb
[   10.477997] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[   10.478000] firmware: requesting dvb-usb-dib0700-1.10.fw
[   10.931350] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   11.636028] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   11.636072] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   11.636369] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   11.858149] DVB: registering frontend 0 (DiBcom 7000PC)...
[   12.032688] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.032872] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   12.177464] DVB: registering frontend 1 (DiBcom 7000PC)...
[   12.352130] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   12.352275] usbcore: registered new interface driver dvb_usb_dib0700


```

Does this mean my tv card is broken? or am i missing something?

---

### Post by scary_jeff on 2009-02-20
If your remote plugs into the TV card itself (not a USB one), then this is the same problem that I had.
First, do 'dmesg | grep -i ir', as I'm not sure the dvb search will find the line with the remote. If this still shows no remote being found, then the solution in the end is to download, build from source, and install the latest v4l-dvb.
Then you need to follow the last bit of post #7 _[here]("http://ubuntuforums.org/showthread.php?t=994447")_ (the bit about creating an fdi file).
Having done this, reinstall lirc, and select the nova-t 500 from the list of remotes.
Once this is done, run irw in the terminal, press buttons on the remote, and things should happen. If they don't, stop here and post again.
Finally, create a lircrc file; I think you can do this in the mythtv configuration utlity somewhere, if not, follow the instructions in the _[last section of the mythtv wiki novaT 500 page]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Remote_Control")_ - the example file given there allowed me to control mythtv at last. The easiest way to remap keys is probably to edit ~/.lircrc, but you could also use the 'Edit Keys' setup page in mythtv (requires mythcontrols plugin, which is in mythbunutu by default).
A bit long winded I know! Anyway, I hope this works.

---

### Post by Alfiegerner on 2009-08-21
Currently looking for a solution to this myself.  I just bought a harmony 525 remote and naively assumed it would have a ir receiver with it for the PC.

If anyone knows how to activate the ir receiver on the TD 500 please let me know.

Note that the post above refers to getting the ir receiver working for the nova T 500, i.e. the PCI card and not the TD 500 which is the dual tuner USB mode.  I've gone through those steps anyway but still can't see the ir device as an input.

Device as shown is dmesg:

dmesg | grep -i dvb
[   10.011599] dvb-usb: found a 'Hauppauge Nova-TD Stick (52009)' in cold state, will try to load a firmware
[   10.011602] usb 1-6: firmware: requesting dvb-usb-dib0700-1.20.fw
[   10.145527] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   10.852006] dvb-usb: found a 'Hauppauge Nova-TD Stick (52009)' in warm state.
[   10.852050] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.852258] DVB: registering new adapter (Hauppauge Nova-TD Stick (52009))
[   11.069444] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   11.240335] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   11.240540] DVB: registering new adapter (Hauppauge Nova-TD Stick (52009))
[   11.378097] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[   11.548362] dvb-usb: Hauppauge Nova-TD Stick (52009) successfully initialized and connected.
[   11.548508] usbcore: registered new interface driver dvb_usb_dib0700


Cheers.

---

