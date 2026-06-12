---
title: "Can\t add any tvcards"
date: 2007-12-15
forum: Mythbuntu
---

### Post by Scrier on 2007-12-15
I\m currently trying to add tv tuners to the setup of my first frontend and I cannot find any video using 
 ls /dev/vi* -l
ls: /dev/vi*: No such file or directory
if I grep after the hardware it seems to be installed though.
dmesg | grep dvb
[   35.641564] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   35.641599] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   36.253435] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   36.819039] dvb-usb: schedule remote query interval to 150 msecs.
[   36.819042] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   36.819446] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   36.819503] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   37.412376] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   37.978087] dvb-usb: schedule remote query interval to 150 msecs.
[   37.978091] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   37.978341] usbcore: registered new interface driver dvb_usb_dib0700

Anyone know what i\m missing here to be able to add cards? I\m guessing from what I have read that I should have 4 video channels for my 2 DVR 500 cards.

---

### Post by volkswagner on 2007-12-15
You may want to list your configuration.  Is the backend and frontend on the same machine?

From what I know tv tuners are added to the backend.  If you are using mythbuntu you can access backend setup via

applications>system>mythbuntu control center>mythtv configuration>mythtv setup

select capture cards>add new card

hope this helps not sure if you already performed the above

---

### Post by Scrier on 2007-12-15
It is a priary frontend / backend.

I\m currently at that adding spot but cannot find any cards. I choose mpeg 2 but there is nothing and probed info says failed to open.

---

### Post by volkswagner on 2007-12-15
do you see your card when the selected card type is dvb dtv capture card.  This may be more suitable for your card, not sure as I have only analog cards now.

move through all choices and see if your card pops up.

---

