---
title: "unable to get accurate signal info"
date: 2014-10-31
forum: Mythbuntu
---

### Post by mma8x on 2014-10-31
Have 2 of the following tuners installed:
```
Bus 002 Device 005: ID 2040:7240 Hauppauge WinTV HVR-850
```
I'm getting a choppy picture that i assumed was a poor signal. Moved the antenna to the roof, still having the same problem. Not sure whether it's the signal or something else. I'm trying to check the signal, but no matter what I do I seem to get a signal of 71% with a snr of 0%.
Here's the femon output:
```
$ femon -a 1 -H
FE: Auvitek AU8522 QAM/8VSB Frontend (ATSC)
status SCVYL | signal  71% | snr   0% | ber 0 | unc 0 | FE_HAS_LOCK
```
Is there a problem with the driver/hardware not reporting the correct values? Something else? These results are for any channel btw.

---

### Post by Bucky Ball on 2014-10-31
Is the antennae plugged directly into the dongle (not an adapter) and what kind of aerial are you using?

If you already have an aerial on the roof permanently, put a splitter on the other end of that and run a cable from that to the TV dongle. If you're using a dinky aerial that came with the card, they are fairly pointless and don't expect much.

---

### Post by mma8x on 2014-11-01
> **Bucky Ball said:**
> Is the antennae plugged directly into the dongle (not an adapter) and what kind of aerial are you using?

If you already have an aerial on the roof permanently, put a splitter on the other end of that and run a cable from that to the TV dongle. If you're using a dinky aerial that came with the card, they are fairly pointless and don't expect much.

Not sure what you mean by dongle v. adapter.  I have 2 usb dongles.  I have [this antenna]("http://www.amazon.com/Winegard-FreeVision-FV-30BB-HDTV-Antenna/dp/B003L76BJS/ref=sr_1_8?s=electronics&ie=UTF8&qid=1414851804&sr=1-8&keywords=winegard+antenna"), which is now on the roof.  The coax from the antenna is split, and each feeds one dongle.  Most of my local stations appear to be broadcast from the same location, which is only 7 miles away.  There should be relatively free line of sight from my location to the transmitters.  The problem is that I don't know whether my playback issues are signal related or not.  No matter what I do, I get a signal of 71% and snr of 0.  So I don't think that that's accurate.

---

### Post by khPWXxF on 2014-11-01
I have a Hauppauge T500 dual tuner card and a USB Hauppauge single tuner, all giving good results apart from the occasional short blip (Heathrow aircraft?).  All three give similar results to you for femon - 67% signal for the two on the card and 50% for the usb.   Zero snr, ber and unc.
I think it's  limitation (bug?) of the software.
 
After similar trauma to you I wrote a wiki page.  It has a UK bias but should be pretty universal:

[https://www.mythtv.org/wiki/DVB-T_Reception_Problems](https://www.mythtv.org/wiki/DVB-T_Reception_Problems) 

Any clues there?   Any additions to it you can suggest?
Does your tuner have an onboard amplifier?    Did you turn it on then cold boot?
If you plug the antenna lead into your TV does it have a signal strength meter?

hth
Phil

---

