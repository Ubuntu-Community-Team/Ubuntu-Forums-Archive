---
title: "Nova-T reporting poor signal since hw upgrade"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by mr smin on 2007-11-05
I have a Hauppauge Nova-T 90002 (Conexant chips) PCI. It has worked fine with various linuxes including Ubuntu previously.
I upgraded to a new mobo and Athlon 64 x2 and plugged the Nova-T in. 
Gutsy 64 detects it fine and there is partial success in a channel scan, however signal is reported as uselessly poor so I can't watch anything,
DVB-T signal is quite weak in my area but I had previously (old hw) got most of the available channels with decent reliability.
I am using a portable antenna and signal booster (plugging into the communal building antenna gets nothing at all and didn't before either)
The DVB card is next to a wireless network card (don't know if this is important).

Any suggestions how to get my TV working in my new hw are very welcome.

mr smin

ps - command line output from Kaffeine

Tuning to: Virgin1 / autocount: 2
Using DVB device 0:0 "Conexant CX22702 DVB-T"
tuning DVB-T to 538000000 Hz
inv:2 bw:0 fecH:3 fecL:3 mod:1 tm:0 gi:0 hier:0
.. LOCKED.
NOUT: 1
dvbEvents 0:0 started
Tuning delay: 209 ms
xine pipe opened /home/mrsmin/.kaxtv.ts
pipe opened
EIT (0:0) : buffer overflow! Rejected
Stop parsing EIT (0:0)
AFD changed from -2 to 9
Asked to stop
pipe closed
Live stopped
dvbstream::run() end
dvbEvents 0:0 ended
fdDvr closed
Frontend closed

---

