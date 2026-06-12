---
title: "Satellite feed in different room to master backend"
date: 2011-01-15
forum: Mythbuntu
---

### Post by myth01 on 2011-01-15
Hi all,

I have a big noisy file server in the study storing all of my media and providing it over NFS to the master backend/main frontend in the living room.  I'm about to add 2 more frontends so would like to move the backend to the server (to prevent having to have the backend machine AND media server on to support the new frontends).  The only problem is connectivity.

Our flat has:

Bedroom with 1 satellite socket
Living room with 1 satellite socket
Kitchen with 1 satellite socket
Study with no satellite socket ](*,)

As we're renting I can't run any cabling.  I'm using homeplugs for the network (devolo one's which are really good).

So how can I run the master backend on the server when there are no satellite connections in the same room?  I'd like to keep the server in the study as it is noisy (but icy-cool).

I don't want to have a secondary backend as that won't solve the main issue of having 2 pc's on (plus the frontend being used).

I've looked at 2 solutions so far.

HDHomeRun - exactly what I need except it isn't available for DVB-S/DVB-S2.
Devolo TV Sat - has DVB-S/DVB-S2 support but not sure if it works in the same way as the HDHomeRun (ie can it be tuned by mythtv).

Any help or other ideas appreciated.

Matt

---

### Post by nickrout on 2011-01-15
> **myth01 said:**
> Hi all,

I have a big noisy file server in the study storing all of my media and providing it over NFS to the master backend/main frontend in the living room.  I'm about to add 2 more frontends so would like to move the backend to the server (to prevent having to have the backend machine AND media server on to support the new frontends).  The only problem is connectivity.

Our flat has:

Bedroom with 1 satellite socket
Living room with 1 satellite socket
Kitchen with 1 satellite socket
Study with no satellite socket ](*,)

As we're renting I can't run any cabling.  I'm using homeplugs for the network (devolo one's which are really good).

So how can I run the master backend on the server when there are no satellite connections in the same room?  I'd like to keep the server in the study as it is noisy (but icy-cool).

I don't want to have a secondary backend as that won't solve the main issue of having 2 pc's on (plus the frontend being used).

I've looked at 2 solutions so far.

HDHomeRun - exactly what I need except it isn't available for DVB-S/DVB-S2.
Devolo TV Sat - has DVB-S/DVB-S2 support but not sure if it works in the same way as the HDHomeRun (ie can it be tuned by mythtv).

Any help or other ideas appreciated.

Matt

The HDHR will not work for the reason you identify.

I don't think the devolo will work.

Slave backend - something small and cool like an atom machine, mounting storage on the master backend, is probably the way to go.. If you get something with a vdpau processor, ie an ION box, it can double as a frontend.

---

### Post by myth01 on 2011-01-15
Thanks nickrout.  Whats the reason you don't think the devolo will work?  The devolo website claims support for mythtv but I'm not sure what the implementation is like and they are far too expensive for experimenting.

[http://www.devolo.com/consumer/prs562-devolo-delivers-linux-support-for-dlan-tv-sat.html?l=en]("http://www.devolo.com/consumer/prs562-devolo-delivers-linux-support-for-dlan-tv-sat.html?l=en")

As the 3 rooms that I would want a frontend in all have satellite sockets I did consider putting the internal pci tuners I have in some mini-itx based frontends but it left me wondering how they would allocate the tuners.  Is it possible to specify the frontend/slave backend to use the local tuner first before having to wake another slave and use it's tuner?  Or is the order of tuners in the master backend used globally?

---

### Post by nickrout on 2011-01-16
> **myth01 said:**
> Thanks nickrout.  Whats the reason you don't think the devolo will work?  The devolo website claims support for mythtv but I'm not sure what the implementation is like and they are far too expensive for experimenting.

[http://www.devolo.com/consumer/prs562-devolo-delivers-linux-support-for-dlan-tv-sat.html?l=en]("http://www.devolo.com/consumer/prs562-devolo-delivers-linux-support-for-dlan-tv-sat.html?l=en")

I hadn't seen that before, and I have never seen it mentioned in connection with myth previously. I suggest you try the main mailing list, there are far more likely to be people there with knowledge of this if it works.> 

As the 3 rooms that I would want a frontend in all have satellite sockets I did consider putting the internal pci tuners I have in some mini-itx based frontends but it left me wondering how they would allocate the tuners.  Is it possible to specify the frontend/slave backend to use the local tuner first before having to wake another slave and use it's tuner?  Or is the order of tuners in the master backend used globally?

Sorry that level of detail is unknown to me.

---

### Post by myth01 on 2011-01-16
> Sorry that level of detail is unknown to me.

No worries nickrout, cheers for you help.

> I hadn't seen that before, and I have never seen it mentioned in connection with myth previously.

I was surprised by this too.  Surely someone has tried before?!

Googling for 'mythtv devolo tv sat', the first result is the press release linked above, results 3-5 are this thread!

---

### Post by ian dobson on 2011-01-16
Hi,

If your SAT settopbox has an ethernet port and can stream the video over it, then maybe it would be possible to use the iptv recorder within mythtv.

I'm using this for several paytv channels. I've set it up like this:-
1) The channel change script switches to the correct channel using the web interface on the settop box (wget).
2) vlc starts streaming from the box (http format) and outputs a udp/rstp stream that mythtv can record.

Regards
Ian Dobson

---

### Post by myth01 on 2011-01-16
Hi ian, cheers.  By settopbox are you referring to the devolo device?

I've currently got myth (hauppauge pci tuners) connected directly to f-connector face plates in the wall.  We did away with our paid-for satellite service about 12 hours after trying myth for the first time so have no other set top boxes now.

---

### Post by nickrout on 2011-01-16
> **ian dobson said:**
> Hi,

If your SAT settopbox has an ethernet port and can stream the video over it, then maybe it would be possible to use the iptv recorder within mythtv.

I'm using this for several paytv channels. I've set it up like this:-
1) The channel change script switches to the correct channel using the web interface on the settop box (wget).
2) vlc starts streaming from the box (http format) and outputs a udp/rstp stream that mythtv can record.

Regards
Ian Dobson

what settop box is that?

---

### Post by nickrout on 2011-01-16
sorry for the triple post, the forum, or my net connection, is playing up.

---

### Post by nickrout on 2011-01-16
as above.

---

### Post by ian dobson on 2011-01-16
> **nickrout said:**
> what settop box is that?

itgate tgc220 (dreambox clone), I'm using the dvb-c version but there are also dvb-s versions.

Regards
Ian Dobson

---

### Post by nickrout on 2011-01-16
> **ian dobson said:**
> itgate tgc220 (dreambox clone), I'm using the dvb-c version but there are also dvb-s versions.

Regards
Ian Dobson

I meant "what settopbox is involved in the original poster's setup?"

---

### Post by myth01 on 2011-01-25
I don't have any set top boxes.  I've just got two pci tuners in the current backend machine.

I have found this:

[http://www.elgato.com/elgato/int/mainmenu/products/tuner/netstreamsat/product1.en.html]("http://www.elgato.com/elgato/int/mainmenu/products/tuner/netstreamsat/product1.en.html")

but again I'm not sure about the linux/myth support.  Having looked at the prices though (I'd have to spend £400 to get what I needed) I am thinking a low-power atom/mini-itx machine for the pci tuners might be the way to go.  I've never used a slave backend before: is is it possible to get the master backend to entirely control the wakeup/shutdown of the slave?

---

### Post by nickrout on 2011-01-25
> **myth01 said:**
> I don't have any set top boxes.  That was my point >  I've just got two pci tuners in the current backend machine.

I have found this:

[http://www.elgato.com/elgato/int/mainmenu/products/tuner/netstreamsat/product1.en.html]("http://www.elgato.com/elgato/int/mainmenu/products/tuner/netstreamsat/product1.en.html")

but again I'm not sure about the linux/myth support.  Having looked at the prices though (I'd have to spend £400 to get what I needed) I am thinking a low-power atom/mini-itx machine for the pci tuners might be the way to go.  I've never used a slave backend before: is is it possible to get the master backend to entirely control the wakeup/shutdown of the slave?

There are ion machines that have pci or pci-e slots, eg some of the motherboards from zotac.

---

### Post by myth01 on 2011-01-25
> **nickrout said:**
> That was my point

Oh I get it.  Sorry nickrout, I was being dumb.

Do you know of any atom based boards sporting two pci slots?  I haven't been able to find one yet...

---

