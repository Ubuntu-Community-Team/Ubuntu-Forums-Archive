---
title: "Cannot see transmission via Hauppauge USB2 DVB-T"
date: 2009-06-14
forum: Multimedia Software
---

### Post by Philip Whitton on 2009-06-14
I am a new and inexperienced user. I installed Ubuntu 9.04 on a separate hard drive on my PC. Windows XP is installed on another disk.

I have tried to get the Hauppauge USB2 DVB-T TV tuner to work with Ubuntu. The Firmware is not built in. I believe that I have found and installed the correct Firmware. I tried:
                          dmesg | grep -i 'dvb'
and got the following messages:
                                   	 	 	 	 	 	  [   10.257075] dvb-usb: found a 'Hauppauge WinTV-NOVA-T usb2' in warm state.
 

 [   10.258487] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
 

 [   10.261147] DVB: registering new adapter (Hauppauge WinTV-NOVA-T usb2)
 

 [   10.262269] dvb-usb: MAC address: f603c918
 

 [   10.264856] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
 

 [   10.425350] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:10.3/usb2/2-1/input/input6
 

 [   10.456810] dvb-usb: schedule remote query interval to 100 msecs.
 

 [   10.456824] dvb-usb: Hauppauge WinTV-NOVA-T usb2 successfully initialized and connected.
 

 [   10.456867] usbcore: registered new interface driver dvb_usb_nova_t_usb2
 

 [  233.259041] DVB: adapter 0 frontend 0 frequency 0 out of range (44250000..858000000)
 

 [ 1362.970853] dvb-usb: Hauppauge WinTV-NOVA-T usb2 successfully deinitialized and disconnected.
 

 [ 1386.739915] dvb-usb: found a 'Hauppauge WinTV-NOVA-T usb2' in cold state, will try to load a firmware
 

 [ 1386.739922] usb 2-6: firmware: requesting dvb-usb-nova-t-usb2-02.fw
 

 [ 1386.806399] dvb-usb: downloading firmware from file 'dvb-usb-nova-t-usb2-02.fw'
 

 [ 1386.892568] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
 

 [ 1388.778473] dvb-usb: found a 'Hauppauge WinTV-NOVA-T usb2' in warm state.
 

 [ 1388.778636] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
 

 [ 1388.818441] DVB: registering new adapter (Hauppauge WinTV-NOVA-T usb2)
 

 [ 1388.819603] dvb-usb: MAC address: cf636918
 

 [ 1388.857984] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
 

 [ 1388.862889] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:10.3/usb2/2-6/input/input8
 

 [ 1388.900244] dvb-usb: schedule remote query interval to 100 msecs.
 

 [ 1388.900256] dvb-usb: Hauppauge WinTV-NOVA-T usb2 successfully initialized and connected.
 

 [ 1406.889930] DVB: adapter 0 frontend 0 frequency 0 out of range (44250000..858000000)
 

 [ 1469.795865] DVB: adapter 0 frontend 0 frequency 0 out of range (44250000..858000000)
 

 [ 1656.117274] DVB: adapter 0 frontend 0 frequency 0 out of range (44250000..858000000)
 

 [ 1783.785039] DVB: adapter 0 frontend 0 frequency 0 out of range (44250000..858000000)
 
There is a red light glowing on the device: it seems to be working and connected

I tried:
                                  w_scan version 20081106 
 Channels were sought and found.

In VLC I get the following messages in Terminal:
                                 [00000425] dvb access error: DVB-T: setting frontend failed (-1): Invalid argument
 

 [00000425] dvb access error: DVB-T: tuning failed
 

 [00000423] main input error: open of `dvb://' failed: could not create access


In MPlayer I get:
                                  Totem is missing a channels listing to be able to tune the receiver. And Please follow the instructions provided in the link to create a channels listing.


- I could not see any link to follow


In TV Time Television Viewer i am told that I get no signal.


Can anyone please help?

---

### Post by anthonyJC on 2009-08-10
I use one. Have not used either  VLC or Mplayer to open a DVB stream.

Kaffeine (for KDE3, the current Jaunty version of Kaffeine) does work;  current Kaffeine, for KDE4, currently in Karmic does not currently work (with this tuner. ) Mythtv works. Also the firmware is buggy, to the point it damages the kernel (usb failures, hard locks).

---

