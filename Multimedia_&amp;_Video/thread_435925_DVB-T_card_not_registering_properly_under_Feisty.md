---
title: "DVB-T card not registering properly under Feisty"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by epee_dave on 2007-05-07
Hi

My DVB card isn't working properly under Feisty. The card is a  "KWorld/VStream XPert DVB-T" 

When I run > modprobe cx88_dvb 

I get the following from dmesg

> [ 1300.398407] cx2388x dvb driver version 0.0.6 loaded
[ 1300.398418] cx8802_register_driver() ->registering driver type=dvb access=shared
[ 1300.398425] CORE cx88[0]: subsystem: 17de:08a6, board: KWorld/VStream XPert DVB-T [card=14]
[ 1300.398704] cx88[0]/2: cx2388x based dvb card
[ 1300.524675] DVB: registering new adapter (cx88[0]).
[ 1300.524773] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...


For some reason the card works fine with Xine but won't work with MythTV.
 
When I try to run the Myth setup and try to set the card type to  "DVB DTV capture card (v3.x)" myth thinks that is is a  "Zarlink MT352 DVB-T". Under all other card types myth believes that it is a Kworld, just not the one that I want to use?

Other info on the card 

> 00:0c.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: KWorld Computer Co. Ltd. KWorld/VStream XPert DVB-T
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at df000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

00:0c.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: KWorld Computer Co. Ltd. KWorld/VStream XPert DVB-T
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2


Any help would be gratefully recieved.

Dave (a Linux newbie)


edit I forgot to say dmesg also says this

> [ 2598.374351] cx88_wakeup: 2 buffers handled (should be 1)

---

### Post by newlinux on 2007-05-07
There's not necessarily anything wrong with the DVB drivers seeing it as Zarlink MT352 DVB-T. Maybe that card shares the same chipset.

Do you have errors when you apply an input source and scan for channels?

---

### Post by epee_dave on 2007-05-07
> Do you have errors when you apply an input source and scan for channels?

I did but I have just tried again and it all appears to work now.

Sorry for bothering everyone I really have no idea why it wasn't working, but now has, yay.

---

### Post by newlinux on 2007-05-07
No need for apologies :). We're glad to help here.

---

