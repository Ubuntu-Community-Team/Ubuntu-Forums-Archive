---
title: "Mythbuntu not working"
date: 2010-04-01
forum: Mythbuntu
---

### Post by Failboat88 on 2010-04-01
I don't have the full specs but my video card is nvidia and I'm using the proprietary driver's. I just got the Haup. HVR-1250 and it did not auto-detect. This isn't my full worries.

It should be logging in automatically and starting mythtv, but it doesn't. It flickers some and then goes to the log-in screen. I log in and it doesn't do much and then I see the load bar before the log-in screen and it asks me to log-in again. Eventually it goes into mythtv with enough tries. 

Please tell me the HVR-1250 works with Linux. I just returned Avermedia hdtv Duet and I don't want to do another return.

I'm thinking of just installing Ubuntu and running Mythtv off that. Does that work well? Is there some pitfalls there?

-Brian

---

### Post by jaakan on 2010-04-01
HVR-1250 works great for me with OTA and QAM.

I just updated to 10.04 b1 over the past weekend. 9.10 x64 works, 9.04 x64 works, 8.10 x64 works, 8.04+updates x64 works, setup this card on backend as DVB v3 

```
    *  Hauppauge HVR-1250 setup
          o this will not show up from a non-updated 8.04 install
          o if you install with 8.04 you need to run all the updates before it will find your card out of the box
          o pick DVB v3 - it will say Samsung ... 
```


did you upgrade from 9.04 to 9.10? that sounds like a bug I ran in to.
I ran in to a left over session file that should have been removed when you log off that was not. ~/.cache/sessions/ I think a file in here ~/.config/autostart might have been messed up too.

Do a clean install of mythbuntu with the newest version if you can

9.10 upgrade to 10.04 b1 for me was bug free

I replaced my NV8400 with a NVGT220, have not tested HDMI audio yet

---

### Post by Failboat88 on 2010-04-02
Thanks for the hvr-1250 info I'll try that later today. My mythbuntu was a full install of 9.1. I have not reformatted a lot before. Could this be from not formatting right? I didn't do anything to my winxp before I reformatted. I read that you should defrag before installing another os.

---

### Post by Failboat88 on 2010-04-08
Is 10.04 stable yet? I thought it was still in testing.

---

### Post by 4partee on 2010-05-10
> **jaakan said:**
> HVR-1250 works great for me with OTA and QAM.


I sure would like to hear how you got QAM to work! What rev is your card?  Mine is rev 04.  Is that the problem?

I recently bought an HVR-1250 that works on Antenna, but I cannot do QAM.  I have STFW and cannot find anywhere else that anyone says that this card does QAM.

I am on Cox cable in Oklahoma City. I can get OTA and QAM with my TV.  I do not have Cox digital, only enhanced, so only get channels 2-125 and unscrambled digital.

02:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 (rev 04)
	Subsystem: Hauppauge computer works Inc. Device 2211
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd600000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: <access denied>
	Kernel driver in use: cx23885
	Kernel modules: cx23885

Ubuntu 10.04 
Mythtv 0.23

John

---

### Post by colinnwn on 2010-05-10
> **4partee said:**
> I have STFW and cannot find anywhere else that anyone says that this card does QAM.

John

I have this card and it works pretty good with Clear QAM on Dallas Time-Warner. I'll try to look up the revision soon, but when I researched the purchase, I found no one claiming much difficulty getting it to work with Clear QAM in 9.04 or more recent. 

Hauppauge cards, with the possible exception of HVR-2250, seem to be very sensitive to a high quality and powerful signal for Clear QAM. From the point the cable enters my house, it goes into a high quality digital signal amplifier, and two 2 port splitters, before it hits the card. That means the signal is degraded no more than about one quarter the power after exiting the amplifier. Every connection, and poor piece of old cable attenuates the signal. Might check on this...

If my HVR-1250 tries to tune to certain channels that appear to be non-encrypted control channels for set top boxes, it will freeze mythfrontend and give that ringbuffer overrun warning. Subsequent FE starts will attempt to start from that channel, regardless of the default channel set in the backend. The failure somehow resets the starting channel in the BE to the channel it froze on. From there, I have to go into the BE and reset the starting channel before I can use the card.

After some time consuming testing, I found the 5 or so channels that did this, and hid them in mythweb channel table settings.

---

### Post by 4partee on 2010-05-10
colinnwn;

Thanks for the heads up on splitters.  

I did not suspect this could be my problem because I have two other systems with similar splitter configurations where this same model card works in windows.  I figured it was my inexperience with Mythtv.

I do have splitters and no amplifier right now. I'll swap cables and splitters around tomorrow.  If that doesn't work, then it could be a card revision and driver issue, or me and Mythtv.

John

---

### Post by 4partee on 2010-05-11
> **4partee said:**
> colinnwn;

Thanks for the heads up on splitters.  

I did not suspect this could be my problem because I have two other systems with similar splitter configurations where this same model card works in windows.  I figured it was my inexperience with Mythtv.

I do have splitters and no amplifier right now. I'll swap cables and splitters around tomorrow.  If that doesn't work, then it could be a card revision and driver issue, or me and Mythtv.


John
Update 2010-05-11:

The cables and/or splitters are not the problem.  I suspect the card/driver.  

While scanning in the BE the system freezes on channel 134.  I did a complete install of Ubuntu 10.04 + Mythtv from synaptic, and a complete install of Mythbuntu 10.04.  I don't ever get far enough to try the FE.

Does anyone know of a program other than Mythtv that could be used to at least watch QAM? If so, then the card/driver is not the problem.

---

### Post by 4partee on 2011-09-19
I resumed the project in Aug 2011.

I believe I was actually having problems with the full scan.  This time I activated schedulesdirect and edited the cable-digital lineup there.  I allowed only certain unscrambled digital channels.

QAM is working fine now.  I set up an input source named FTA(Free-To-Air) for the pvr-1250. 

HTH;
John

---

