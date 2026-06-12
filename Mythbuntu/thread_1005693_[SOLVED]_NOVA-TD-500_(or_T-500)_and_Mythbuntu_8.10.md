---
title: "[SOLVED] NOVA-TD-500 (or T-500?) and Mythbuntu 8.10"
date: 2008-12-08
forum: Mythbuntu
---

### Post by tomashektor on 2008-12-08
Hi

I'm trying to set up at box with Mythbuntu 8.10. My capture card is a Hauppauge nova-t-500 (that's what I bought). Although, when i type
```
dmsg | grep -i dvb
```
I get the following output
```
[   20.300000] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware

```
Does this mean that I have the diversity model?
*_Edit_* Opened up the case and looked at the card. It said NOVA-TD-500. Maybe all new T-500 actually is TD-500? *_End of Edit_*

I keep getting timeouts when I try to scan for channels.

But I've heard that even the diversity model should work in 8.10. But how do I get it to work? 
-I followed the mythbuntu installation manual. 
-I chose a dvb capture card (not mpeg2 analog).
-I've increased the timeout limits
-I've activated LNA in /etc/modprobe.d/options

When I choose the dvb type in myth backend setup and switch between 0 and 1, it says something like "dibcom 7000" and "type DVB-T", should it say that.

On the tuner built in my tv, I have a signal strength of approx. 82%. When I scan for channels it's below 50% all the time, with or without LNA activation.

Needless to say, I'm new to linux and myth. =) Can someone guide me through the setup? I thought that this should be easy...

---

### Post by tomashektor on 2008-12-09
bump

---

### Post by watkin5 on 2008-12-09
I've got a different Nova T 500.

If you scroll back and look at the output of dmesg, whats just before and after "dvb-usb: found a 'Hauppauge Nova-TD-500...."

In Hardy I get
```
[   58.348461] dib0700: loaded with support for 8 different device-types
[   58.348748] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   58.700888] lirc_dev: IR Remote Control driver registered, at major 61 
[   58.848110] NET: Registered protocol family 10
[   58.848378] lo: Disabled Privacy Extensions
[   60.322282] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   60.524689] dib0700: firmware started successfully.
[   61.023622] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   61.023738] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   61.025015] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   61.135165] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
[   61.202274] MT2060: successfully identified (IF1 = 1229)
[   61.677155] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   61.677404] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   61.683026] DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
[   61.687764] MT2060: successfully identified (IF1 = 1217)
[   62.237859] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   62.238137] usbcore: registered new interface driver dvb_usb_dib0700

```

Also what do get from lsusb?

---

### Post by tomashektor on 2008-12-15
Hi watkin5

Thanks for the reply. My htpc is not yet connected to the internet so I can't post output from dmesg. I've just moved so the htpc is not first priority right now.

However, it struck me one night (these problems really occupy your whole life :p), that when I scan for channels it said "timeout -- no signal" most of the time, but it also said "Skipping Canal+" and some other non-free channels. This would indicate that the card is working but signal is too weak (even though I had over 80% signal strength on my set top box). So I bought a signal amplifier and tested...and voila! It worked!

Playback is choppy and it needs a few more tweaks before I'm satisfied, but thats another problem.

---

### Post by scary_jeff on 2008-12-15
Have you enabled the on board LNA? This made a huge difference for me. See [http://ubuntuforums.org/showthread.php?t=880830](http://ubuntuforums.org/showthread.php?t=880830) , first reply.

---

