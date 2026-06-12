---
title: "Cannot scan channels on any source"
date: 2009-11-01
forum: Mythbuntu
---

### Post by paulsmith99 on 2009-11-01
Quick summary of situation:
Did fresh install of mythbuntu 9.10 after having a successful running kubuntu 8.10 with mythtv 0.21 for 18 months. I've got a working database and have restored my previous program data into the new clean database so can watch previously recorded content.
I have two Haupauge cards, a HVR-3000 and HVR-4000, both working in the new 2.6.31 kernel.

Kaffeine currently works fine in that it can scan DVB-S or DVB-T and show the TV programs.
The 'scan' tool, part of dvb-apps package, finds channels and produces channels.conf files (which I use in mythtv to start scanning off).
So the problem seems to be with mythbackend for some reason...

Here's the problem:
My restored capture card/video sources/input connection from 0.21 didn't work so I deleted those and set them up again, with all the LNB settings configured correctly(?).
Scanning for channels finds nothing in myth-setup for DVB-T or DVB-S. For DVB-S I chose to scan using a fresh channels.conf, as it's worked in 0.21.
However, I get this shown in the MythTV Setup Terminal:

.... (lots of channels listed, but heres one for example)...
2009-11-01 15:53:55.136 Imported channel: BBC NEWS 6704 -1  on 11953000 auto a auto auto a a auto a h fec: auto msys: UNDEFINED rolloff: 0.35
2009-11-01 15:34:29.300 DiSEqCDevTree, Error: FE_SET_TONE failed
                        eno: Connection timed out (110)
2009-11-01 15:34:29.327 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Can not measure Signal Strength
                        eno: No such file or directory (2)
2009-11-01 15:34:37.850 DiSEqCDevTree, Error: FE_SET_TONE failed
                        eno: Connection timed out (110)
2009-11-01 15:34:47.830 DiSEqCDevTree, Error: FE_SET_TONE failed
                        eno: Connection timed out (110)
2009-11-01 15:34:56.400 DiSEqCDevTree, Error: FE_SET_TONE failed
                        eno: Connection timed out (110)
.... and so on. It shows timed out for all channels until scanning finishes.

I've run out of ideas and googling has got me no further. It'd be a shame to have to go back to mythtv 0.21 but obviously recording is vital to get working again for my myth system!

Please help - I'll provide more details if need be.

---

### Post by SiHa on 2009-11-01
If it helps, here's what I did for my DVB-S card. I assume you're you in the UK, or at least looking at Astra 28.2?

After adding the card, and enabling the LNB under recording options, I did a full scan (tuned) with the following parameters.

Frequency: 10847000
Polarisation: Vertical
Symbol Rate: 22000000
All else auto.

This is the data for the BBC-HD transport, but should find all others as well. One thing to note, after 20mins of scanning, the setup bombed out afer it had been at 100% for a while. I had to re-do, and stop the scan before this point - expect I just missed 'babestation6543', or someting equally riveting.

---

### Post by paulsmith99 on 2009-11-01
Thanks SiHa for the scanning details. Yes I do live in the UK. I have made progress...

It looks like there is something wrongly configured in the database as I noticed this in the mythtv-setup output for adapter0/frontent0 which I mentioned produced no scanning results:

2009-11-01 16:41:30.425 DiSEqCDevTree, Warning: No device tree for cardid 5

I tried the same details you gave me on adapter1/frontent0 (Frontend ID Conexant CX24123/CX24109 Subtype DVB-S) and it worked! The strange thing with this adapter is that it had fewer Full Scan (Tuned) options:
Frequency, Polarity, Symbol Rate, FEC, Inversion

... where as the problem adapter (adapter 0/frontend0, Frontend ID Conexant CX24116/CX24118 Subtype DVB-S2) had more options:
Frequency, Polarity, Symbol Rate, Mod Sys, FEC, Modulation, Inversion, Rolloff

They both use the same video source (Radio Times).

With the details you provided and the 'working' adapter, it eventually found 302 channels, which I can trim down etc. The output window showed this at the beginning but it looks like nothing to worry about:

2009-11-01 16:43:03.235 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Can not count Uncorrected Blocks
                        eno: Operation not supported (95)
2009-11-01 16:43:12.515 DTVMux, Warning: Invalid inversion, falling back to 'auto'
2009-11-01 16:43:12.517 DTVMux, Warning: Invalid inversion, falling back to 'auto'

I'll try to diagnose what is going on with my set up now and hopefully post my findings soon. If need be I'll start with a completely clean database again - get the cards scanning OK and then restore my recordings after.

Thanks again for your help. :D

---

### Post by SiHa on 2009-11-01
DVB-S2 support in Myth (Linux in general, I think) is still it's infancy. Maybe that's you'r problem with that card. It is officially supported in 0.22, but as it's new may have a few niggles.
I'd like to move to S2, but I'm going to wait until 
a) There's more than 2 HD channels to watch
b) It's been going a while in Linux

---

### Post by paulsmith99 on 2009-11-01
I think I can mark this issue as solved. The channels now exist which is what I raised the issue for.

SiHa, I think you're right about it being the card. I checked /var/log/messages and found these important entries...

[35878.910905] cx8800 0000:01:08.0: firmware: requesting dvb-fe-cx24116.fw
[35878.920720] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
firmware.sh[11908]: Cannot find  firmware file 'dvb-fe-cx24116.fw'

... which triggered my memory about having to update card's firmware to support DVB-S2. I'll google it but it involves copy a file to a certain system directory.

I've been happy with my Haupauge 4000 card with mythtv 0.21 recording BBC-HD. Looking forward to more HD channels though!

Thanks again. :D

---

### Post by paulsmith99 on 2009-11-01
Just as a final update to anyone else in a similar situation with a Hauppauge WinTV HVR-4000. The problem was related to my card not having the on-demad firmware available. I solved it 18 months ago for a fresh install of myth0.21 and now I've had to redo it as I'd forgotten all about it for 0.22.

This is what is needed:

Download the firmware file from Hauppauge. Look on Google for how to do it. The file needed is called dvb-fe-cx24116.fw. It needs to go in the directory /lib/firmware. Be careful when getting the file as I tried one lot of instructions from the web just now (incase there was a newer version out), resulting in a same-size file but one byte was different when doing a 'cmp' between my original one and the new one. The 'new' file was not recognized by the kernel. Here's the details of my one that works:

-rw-r--r-- 1 root root 32522 2009-11-01 21:57 /lib/firmware/dvb-fe-cx24116.fw
md5sum /lib/firmware/dvb-fe-cx24116.fw
417cafd3b10e207e1dba9a03ad63e405  /lib/firmware/dvb-fe-cx24116.fw

As soon as the file is in the directory, the card will work properly. No rebooting or changing run levels required.

You should see this healthy report from the kernel when a program accesses the card (such as mythtv doing a channel scan with it):

[42984.651309] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[42984.651324] cx8800 0000:01:08.0: firmware: requesting dvb-fe-cx24116.fw
[42984.661140] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[42989.799701] cx24116_load_firmware: FW version 1.20.79.0
[42989.799717] cx24116_firmware_ondemand: Firmware upload complete

My channel scanning now works perfectly. Hope this helps someone else. :KS

---

