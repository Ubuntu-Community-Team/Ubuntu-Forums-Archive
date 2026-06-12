---
title: "TV without myth"
date: 2009-11-15
forum: Multimedia Software
---

### Post by Sin@Sin-Sacrifice on 2009-11-15
I've used Mythtv and hate it honestly. I would rather use XBMC to organize my HDD media and watch TV through VLC or totem or something. The problem I'm having is I can't figure out how to scan for channels. Every post I've seen on the matter says to use Mythtv. Other posts show commands for European channel listings. I found one command that looks like it should work but when I run ```
scan atsc/us-Cable-Standard-center-frequencies-QAM256
``` I get ```
Killmandline:$ scan atsc/us-Cable-Standard-center-frequencies-QAM256
scanning atsc/us-Cable-Standard-center-frequencies-QAM256
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: cannot open 'atsc/us-Cable-Standard-center-frequencies-QAM256': 2 No such file or directory
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

I think the problem doesn't lie in a lack of documentation but rather waaaay too much for waaaay too many configurations. But I guess that's the nature of it considering the diversity of TV watchers. Anyone in the US using basic cable and this card know what to do? Anyone know what to do?

---

### Post by goatgonads on 2009-11-28
I have been stumbling through the problem myself. The developer of Me-TV has been working with me. Here is the link if interested  [https://answers.launchpad.net/me-tv/+question/90538](https://answers.launchpad.net/me-tv/+question/90538)

I used the command "scan /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256 > channels.conf"


I am attempting to receive an atsc/qam digital cable signal with a Hauppauge HVR-1600


There are 10 different scans that you can run, all of which are located in /usr/share/ dvb/atsc/


The scans below are the only ones that returned results for me:

us-Cable-EIA-542-HRC-center-frequencies-QAM256
us-Cable-EIA-542-IRC-center**_**frequencies-QAM256 <notice the "_" in the name

us-Cable-HRC-center-frequencies-QAM256
us-Cable-IRC-center-frequencies-QAM256
us-Cable-Standard-center-frequencies-QAM256


I see you are trying the us-ATSC-center-frequencies-8VSB above, I got zero results with it myself (comcast digital in Michigan).


/home/channels.conf file looks like this after a scan:


--cut--

[051a]:189012500:QAM_256:2304:2305:1306
[051d]:189012500:QAM_256:0:2433:1309
[0518]:189012500:QAM_256:0:1985:1304
[051e]:189012500:QAM_256:2048:2049:1310
[0516]:189012500:QAM_256:0:2113:1302
[0520]:189012500:QAM_256:2176:2177:1312
[0522]:189012500:QAM_256:2240:2241:1314
--cut--


It produced about 250 results. Windows returned about the same amount, 40-60 of which were unscrambled and viewable.


I have gotten Me-TV to work on a handful of channels, we are trying to work a bug out that keeps it from timing out when tuning certain channels.

---

