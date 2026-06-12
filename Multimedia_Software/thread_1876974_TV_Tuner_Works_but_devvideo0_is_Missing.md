---
title: "TV Tuner Works but /dev/video0 is Missing"
date: 2011-11-07
forum: Multimedia Software
---

### Post by ubn7 on 2011-11-07
Hello,

I have Pinnacle PCTV Nano Stick. It is a USB DVB-T tunner and I use it on Kubuntu 11.10. I think it would be the same on Ubuntu and so on.

It has made these devices:

/dev/dvb/adapter0/
&#9500;&#9472;&#9472; demux0
&#9500;&#9472;&#9472; dvr0
&#9500;&#9472;&#9472; frontend0
&#9492;&#9472;&#9472; net0

Kaffeine is OK with this structure and I can watch TV (using Kaffeine) just fine. When I try to use tvtime, it fails to find /dev/video0. I tried to use the -d command line option to point tvtime to the devices listed under /dev/dvb/ but it did not help.

As I understand it, devices listed under /dev/dvb/ are DVB devices but /dev/video0 is v4l video device and these are not intechangeable.

Like I mentioned, the TV tuner is working and Kaffeine is fine using /dev/dvb/*. My question is how to get /dev/video0 so other applications, dependant on the video0 device, can use the tunner too.

Thank you in advance.

---

### Post by ubn7 on 2011-11-08
No one knows? :(

Maybe it is a bug and the TV tuner driver should make the device? I have seen few reports of this problem but no solution or even a clarification yet. From what I saw, this problem could be related to USB tuners only but I am not sure.

---

