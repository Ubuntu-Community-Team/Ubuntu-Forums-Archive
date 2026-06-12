---
title: "TBS 6928SE Tuner card"
date: 2016-12-29
forum: Multimedia Software
---

### Post by timswait on 2016-12-29
I am having problems with a TBS 6928SE DVB-S2 tuner card that I am trying to set up on Kubuntu 16.04 under MythTV. I have downloaded, compiled and installed the latest drivers from the Turbosight website. MythTV was able to detect and set up the card and use it to scan for channels initially. I am also setting up the satellite dish, so have a Satellite Finder in line to the LNB, so I can tell when the LNB is being powered by the card. I notice that when it was working correctly the satellite finder would normally be showing no signal and would only show a signal when the card was active (e.g. scanning).
However after a scan crashed part way through I had to hard reboot the computer. Now MythTV reports it is unable to open the card. The Satellite Finder is displaying a signal to the LNB at all times when the computer is on, regardless of whether the card is being used. I think something is keeping the card active so that MythTV cannot access it. In the past I had a similar problem and solved it by removing and then reinstalling the drivers, however I have just tried this and it does not work. As soon as I turn the computer on, the satellite finder shows a signal to the LNB and MythTV is unable to open the card. Is there anything I can do to force the card to be shut down so that MythTV can be allowed to access it? Stopping the MythTV backend DOES NOT stop the signal to the LNB, so I don't think it's Myth that's holding the card open.
I think it is related to this bug:
[https://code.mythtv.org/trac/ticket/12825?cversion=1&cnum_hist=4](https://code.mythtv.org/trac/ticket/12825?cversion=1&cnum_hist=4)

---

### Post by timswait on 2016-12-29
It's getting worse! Have now tried with an older card, a Hauppauge WinTV-NOVA-HD-S2 and this is showing similar symptoms. Put card in, installed firmware, MythTV detects it (no signal to LNB on Sat Finder), do a scan- it doesn't find any channels (this in itself is a problem, as by now I'm pretty sure I have the dish aimed correctly- but maybe worry about this later!). However then after reboot the sat finder starts showing a signal to the LNB all the time and MythTV is no longer able to open the Hauppauge card!

---

