---
title: "Moving mythbuntu to a new home"
date: 2014-01-19
forum: Mythbuntu
---

### Post by Brian_M_Blacke on 2014-01-19
Hi everyone,
I'm moving to a new home in the next few weeks. I'm unable to just move my myth setup to the new house and leave it as is(a couple of front ends and a backend under the house).
The Landlord has told me that I'm not allowed to drill any holes in any of the floor, walls or ceilings. Which I understand but that means my myth server will have to be in the house 
and unfortunaley the place is open plan which means that there isn't anywhere to hide a loud media server. Well not really, I can put it in the kitchen
but I don't want to have run tv aerial cable through the lounge as well as a network cable. 
Can I have server hidden away in the kitchen and the tv aerial connected to the frontend. I guess the frontend will have to now be both front and backend.
But how do I set up the server, can I split them and what other things would I need to do?
Thanks in advance for any and all replies
Brian M Blacke

---

### Post by TheFu on 2014-01-19
Use an HDHR close to the antenna. That removes the need for any coax cables, just ethernet.  I have 4 tuners, 2x HDHR3 network tuners here. LOVE THEM! No signal loss over ethernet either. ;)
Use wireline networking to get connections near the TVs. 200Mbps should be possible in the real world with 500Mbps equipment.
Put your recording PC anywhere you like ... ventilated closet?

Or get a Seasonic PSU that isn't so loud, perhaps a case with better noise isolation and put the whole thing on a shag carpet. Dump the $400 GPU with dual louder-than-jet-engine fans when an aircooled $20 GPU will do what you want and be silent.

Look into a partition to block off the computer racks from the rest of the flat. Noise should be muffled by that.

You are correct to avoid thinking that wifi will work for streaming media.  It will, for 720, highly compressed stuff provided a 300Mbps wifi connection is possible, but atmospheric changes even inside a room can screw with that. If multiple front-ends are streaming 1080p stuff concurrently, wifi just doesn't work well enough.

My XBMC box is silent ... except the almost silent spinning HDD. It has a picoPSU - amazing device that is - ZERO noise and no internal cooling is needed thanks to the APU and external brick for the PSU. I suppose it could boot off the network and mount the ~/.xbmc/ area over NFS to be diskless. Hummmm.

There are lots of front-end systems these days, so a full PC isn't needed. Roku, WDTV, XBMC on low powered devices, Arm-based stuff ... all those will be relatively quiet. I have XBMC runnning on an Android tablet, for example. Don't use it too often, but there is an HDMI out, so it can drive a TV, if needed.

If the myth-back-end is transcoding, getting it really silent is harder. Transcoding needs lots of power, which leads to lots of heat. By the time you cover all this, it might be easier to just get a new back-end that is small and relatively quiet.  I have a Core i7 Shuttle box that only makes lots of noise at boot. The rest of the time it has a slight hum. No real expansion, but it is quiet AND cheap.

Anyway, hope these are some ideas you can use.

---

### Post by Brian_M_Blacke on 2014-01-20
Hey thanks for the reply.
I built the frontend to be quite, it doesn't have any fans and mythbuntu runs of a sd card. So no noise there. Obviously the server is a different matter.
I'm happy with the hardware that I'm using and the move will suck up any spare cash I'm likely to have for the next few weeks.
Can I have the frontend  handle the internal tuner card and record to the backend server or do I need to add a hhd to the frontend to handle recorded tv or nfs to the server.
Again thanks for the reply. I hope this makes a issue clearer
Brian M Blacke

---

