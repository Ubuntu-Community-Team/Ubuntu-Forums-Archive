---
title: "Hauppauge WinTV-dualHD - can't get DVB-T2 signal"
date: 2019-06-08
forum: Multimedia Software
---

### Post by SpoZen on 2019-06-08
Hi,

I have a Hauppauge WinTV-dualHD:

```
Bus 001 Device 004: ID 2040:0265 Hauppauge
```

I have downloaded the extra firmware for si2168 to /lib/firmware/:

```
wget http://palosaari.fi/linux/v4l-dvb/firmware/Si2168/Si2168-B40/4.0.25/dvb-demod-si2168-b40-01.fw
wget http://palosaari.fi/linux/v4l-dvb/firmware/Si2168/dvb-demod-si2168-01.fw
wget http://palosaari.fi/linux/v4l-dvb/firmware/Si2168/dvb-demod-si2168-02.fw
```

But I cannot get mumudvb to stream when I tune my card to a DVB-T2 frequency.
And dvbv5-scan only finds channels on the old DVB-T frequencies. Am I missing something?

---

