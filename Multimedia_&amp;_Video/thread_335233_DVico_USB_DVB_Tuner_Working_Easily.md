---
title: "DVico USB DVB Tuner Working Easily"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by Erlander on 2007-01-10
I'm very new to Linux and had trouble getting my tuner working at first.  I didn't find much with search so feel I should document what I did.

I hope the following doesn't offend any purists but its what worked for me.

I originally installed Ubuntu and got my DVico USB2 tuner going the hard way.

I have a spare hard disc and decided to use it to see how easily I could install now that I have a bit of an idea what is needed.

First I started with the tuner connected up and a working sound card. I didn't do this the first time and as a result it was more work to get them recognised. With them there they were recognised as Ubuntu was installed

The steps then were:

1. Install Ubuntu 6.10 (Edgy)

2. Download the firmware file dvb-usb-bluebirf-01.fw from [http://www.linuxtv.org/download/dvb/firmware](http://www.linuxtv.org/download/dvb/firmware)

3. Copy the firmware file into /lib/firmware. I used sudo nautilus in the terminal to enable the copy.

4. Install automatix from [http://www.getautomatix.com](http://www.getautomatix.com)

5. Use Automatix to install the multimedia codecs

6. Install Kaffiene and scan for channels etc

That's all.

OK Mythtv isn't installed but Kaffiene is good for viewing and recording and even recognises the remote that came with the tuner.

Performance is if anything better than under Windows XP as on this machine I am only currently using a TNT2 M64 Pro Display card and can watch HD channels without stuttering. CPU usage on an Athlon XP 3200+ is near 100% but it works but I will upgrade the display card soon to improve on this.

I hope the above is of help to others.

Rob

---

