---
title: "Scan finds no channels on DTV1000T"
date: 2008-02-27
forum: Mythbuntu
---

### Post by moollar on 2008-02-27
Hi everyone,

I've installed Ubuntu 7.10 with mythbuntu added later. My DVB-T card is a Leadtek DTV1000T. When I go to scan for channels, none are found. I live in Sydney, Australia.

I can find all the channels with no problems in Kaffeine. Is there some special way I need to set up this card in Mythbuntu? Am I missing something (this is highly likely)?

I would love to get Mythbuntu working well so that I can convince my wife that we don't need windows for the media center (which is currently driving me nuts!).

I've used Ubuntu on and off over the last couple of years, but still consider myself quite n00bish.

Thanks in advance for your help.

---

### Post by moollar on 2008-02-27
Well, I think I may have figured it out. I made sure that I included cx88-dvb in /etc/modules (for some reason this has been missed in the newer kernels?) and deleted all capture cards and video sources in myhtbuntu setup. I then added a new card (DVB-T) and video source, configuring the frequency table to Australia. I also made sure the timeout(?) was increased from 0 to 50ms for scanning.

One of the problems was that I had selected an Analogue card instead of DVB-T. The DTV1000T does have analogue inputs and I will probably be able to configure them later, but I don't use them at the moment.

I was able to find all of the channels on the first scan except for channel 10, but it was found when I ran the scan a second time. I haven't been able to test whether it's working yet, because I had to leave for work. Will post again after running myth frontend and trying it out (hopefully tonight).

---

### Post by moollar on 2008-02-27
No Joy.

Just got a call from my wife saying that Kaffeine is no longer showing the option to watch digital tv and that Mythfronted has tv with sound, but a static, garbled picture and she is unable to change channels.

Should be interesting when I get home....

---

