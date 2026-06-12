---
title: "Please help to trobleshoot hauppauge 850 analog cable tunning"
date: 2013-06-11
forum: Mythbuntu
---

### Post by thatrobguy on 2013-06-11
Hi I've searched high and low for days. I've found posts from people who have gotten a  hauppauge 850 tv tunner to work for analog cable but can't follow there leed. I finaly gave up and bought a ati wonder hd750 and had less luck with that. now I am feeling defeated. I feel I'm close to getting the hauppauge 850 configured in mythtv but it doesn't show any signal detection at all when scanning for channels. 

The hauppauge works in tvtime. There are no error messages in dmesg when I plug the device in. it sets up /dev/vbi0,/dev/video0, /dev/v4l, /dev/dvb

When configuring mythtv I've chosen "Anolog v4l capure card" and for video device" /dev/video0" 
in input conection when I scan for channels the signal streanth bar stays at zero.

could to point me in the next direction? what log file should I look at? or what should i test?

---

### Post by klc5555 on 2013-06-11
> **thatrobguy said:**
> Hi I've searched high and low for days. I've found posts from people who have gotten a  hauppauge 850 tv tunner to work for analog cable but can't follow there leed. I finaly gave up and bought a ati wonder hd750 and had less luck with that. now I am feeling defeated. I feel I'm close to getting the hauppauge 850 configured in mythtv but it doesn't show any signal detection at all when scanning for channels. 

The hauppauge works in tvtime. There are no error messages in dmesg when I plug the device in. it sets up /dev/vbi0,/dev/video0, /dev/v4l, /dev/dvb

When configuring mythtv I've chosen "Anolog v4l capure card" and for video device" /dev/video0" 
in input conection when I scan for channels the signal streanth bar stays at zero.

could to point me in the next direction? what log file should I look at? or what should i test?

Analog scanning is frequently broken in mythtv. But even when it works properly, unlike the case with DVB scanning, analog scanning doesn't actually scan anything --it just sets up database entries and Channel Editor entries for channels 2 through 99. Analog tuners will already know what frequencies to tune to for the channels 2-99 based on the frequency table default set in the backend setup. So, since with analog scanning there's no actual scanning going on, there will be no signal strength registered as it runs up the channel numbers 2-99. But channel entries for 2 through 99 should be set up and editable for your analog tuner's Video Source in the Channel Editor once the analog "scanning" process has finished. If these entries have been set up, then your card should be able to tune through mythtv's livetv to any of these channels, whether there's a station on them or not. If the analog "scan" is not creating database and Channel Editor entries, the necessary ones may simply be added manually, one-at-time, in Channel Editor. Where the Channel Editor add-channel form asks for "frequency or channel", you use the analog channel number.

However, how's your cable analog getting to you?  If it is direct from the wall, without a set top box (as is still the case in a few areas) then your card will still need to tune channels 2-99. But if your analog signal is coming from a cable set top box, then your card will tune to one and only one channel and frequency: the channel and frequency that your set top box is feeding you. (Or no frequency at all if the set top box is feeding a composite connection to the card.) All channel changing will be done via the set top box --the tuner card will stay tuned to the one single frequency. The card will be set up differently in this case, to always be brought up on one frequency, and the Channel Editor entries will be set up to change channels on the set top box directly by means of Linux's LIRC utility. 

Finally, I don't use the 850, and am not certain whether the analog tuner is an MPEG hardware-encoding analog tuner like so many others are that Hauppauge makes. If the 850 has a hardware-encoding MPEG tuner, then it would need to be set up in mythbackend's tuner setup as MPEG on /dev/video0, rather than V4l But as I said, I'm not familiar with the specifics of this particular Hauppauge product.

---

