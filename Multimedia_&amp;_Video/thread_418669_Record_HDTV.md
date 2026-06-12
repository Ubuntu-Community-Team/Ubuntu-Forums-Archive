---
title: "Record HDTV"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by the8thstar on 2007-04-22
Hello,

I'm looking for a TV tuner card that can record in HD and is recognized in Ubuntu. Does that exist? Any recommendations?

---

### Post by PilotJLR on 2007-04-22
Check out pcHDTV, which is made for linux:
[http://www.pchdtv.com/](http://www.pchdtv.com/)

I personally use 2 ATI HDTV Wonder cards... these do have unsupported binary-only linux drivers, and they actually work extremely well.

Overall, you are likely to have more luck with pcHDTV.

---

### Post by notanatheist on 2007-04-26
Binary drivers? Eh? Where? What? My tuner is recognized but I haven't gotten a picture yet off the HDTV.

---

### Post by PilotJLR on 2007-04-27
What indeed! :-)

What type of tuner??? Exact model please

---

### Post by psusi on 2007-04-27
Last I checked, there were no hdtv capture cards on the market that could record from anything but over the air hdtv signals because the cpu requirements are too high to encode hdtv mpeg streams in real time, which you would have to do to record from a component signal from say, a digital tv cable box.

---

### Post by Erlander on 2007-04-27
I know this doesn't apply to the original poster but for the sake of clarity for others with PAL DVB-T there is no problem recording HDTV as it is broadcast as an encoded stream and all that happens in recording is the stream is written to the hard disc.

Rob

---

### Post by notanatheist on 2007-04-28
> **PilotJLR said:**
> What indeed! :-)

What type of tuner??? Exact model please

ATI HDTV Wonder. Just as you say you are using with binary drivers. Thus I ask, where from?

---

### Post by notanatheist on 2007-04-28
> **psusi said:**
> Last I checked, there were no hdtv capture cards on the market that could record from anything but over the air hdtv signals because the cpu requirements are too high to encode hdtv mpeg streams in real time, which you would have to do to record from a component signal from say, a digital tv cable box.

The MyHD 130 has QAM support for unencrypted HD cable signals as well as OTA. Also has a hardware decoder to reduce load on the CPU. Capture as straight .TS and Mplayer will play it back later. 

Until I've paid for the transmission in my car I'm stuck with the ATI HDTV Wonder.

---

### Post by PilotJLR on 2007-04-29
> **notanatheist said:**
> ATI HDTV Wonder. Just as you say you are using with binary drivers. Thus I ask, where from?

[http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder](http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder)

Their instructions are Fedora specific, so you can google the file you need: dvb-fe-nxt2004.fw
Searching for that, you'll see that you can retrieve the file from get_dvb_firmware, which you can obtain here: [http://www.mjmwired.net/kernel/Documentation/dvb/get_dvb_firmware](http://www.mjmwired.net/kernel/Documentation/dvb/get_dvb_firmware)

Once you have the file, the MythTV documention is easy to follow.

---

### Post by notanatheist on 2007-04-29
Ah, just the dvb firmware. I got that going without a hiccup and was able to scan for channels. I thought you had a binary driver from ATI or something! 'lsmod' showed quite a few 'dvb' entries but I discovered I didn't have the firmware as I was poking through forums. Haven't tried the card in a few months and last time was with Arch or Gentoo.

---

### Post by lionsnob on 2007-04-29
> **psusi said:**
> Last I checked, there were no hdtv capture cards on the market that could record from anything but over the air hdtv signals because the cpu requirements are too high to encode hdtv mpeg streams in real time, which you would have to do to record from a component signal from say, a digital tv cable box.

I use my pcHDTV 5500 for OTA but I think it can do QAM as well.  It records with very little CPU because (I think) the content is already in MPEG-2 format and it just copies it right to disk.

---

### Post by PilotJLR on 2007-04-29
Same with my ATI HDTV Wonder cards... they encode mpeg-2 on the board, so it takes very little cpu to run. I have 2 tuners in my machine, and it can easily record 2 HDTV streams at once, with maybe 5% cpu utilization.

---

### Post by zdude on 2007-04-29
I use HDhomerun with mythtv and it rocks! It is a standalone box and is connected via ethernet. It has two tuners and does QAM as well as OTA. It costs about $170 bucks. I've been using it since first of the year.

---

### Post by superm1 on 2007-04-30
> **PilotJLR said:**
> Same with my ATI HDTV Wonder cards... they encode mpeg-2 on the board, so it takes very little cpu to run. I have 2 tuners in my machine, and it can easily record 2 HDTV streams at once, with maybe 5% cpu utilization.
It doesn't encode on board.  Its *broadcast* in mpeg2, and the card just receives this file to spit it out to disk.

---

### Post by psusi on 2007-04-30
Right... the cards just capture the mpeg stream as it is broadcast over the air.  Unfortunately, the digital cable boxes decode the mpeg stream and output the analog signal on the component video ports, and I have not seen a card on the market that can take that and encode it again in real time.  

I'm not sure what you mean when you mention QAM in addition to over the air.... QAM is a modulation technique used by over the air HDTV broadcasts... also used by cable modems, and dsl modems.

---

