---
title: "Frontend / Backend Question"
date: 2009-07-06
forum: Mythbuntu
---

### Post by browndog289 on 2009-07-06
Hello

I already have a mythbuntu backend running in our lounge which has been working well for over a year. It is set to shut down and power on automatically using the BIOS clock for recordings.

I have built another mythbuntu system for the bedroom. I would like it to function as a frontend for the lounge backend when the backend is powered on (manually) but otherwise (when the lounge system is powered off) I would just like to be able to watch TV on the bedroom system.

I can't see any way to do this as I can either choose to have the bedroom system as a frontend, backend or secondary backend.

Frontend - works fine when the lounge system is powered on but I get a load of connection errors (obviously) when the backend is off.

Standalone backend - works fine but I cannot watch any recordings from the lounge system.

Secondary backend - shares the workload with the lounge system but I get the same problems as with the front end setting when the lounge system is off.

So is there any way I can get the bedroom system to work as a frontend when the lounge system is on but as a standalone system when it isn't?

Many Thanks

---

### Post by klc5555 on 2009-07-06
> **browndog289 said:**
> Hello

I already have a mythbuntu backend running in our lounge which has been working well for over a year. It is set to shut down and power on automatically using the BIOS clock for recordings.

I have built another mythbuntu system for the bedroom. I would like it to function as a frontend for the lounge backend when the backend is powered on (manually) but otherwise (when the lounge system is powered off) I would just like to be able to watch TV on the bedroom system.

I can't see any way to do this as I can either choose to have the bedroom system as a frontend, backend or secondary backend.

Frontend - works fine when the lounge system is powered on but I get a load of connection errors (obviously) when the backend is off.

Standalone backend - works fine but I cannot watch any recordings from the lounge system.

Secondary backend - shares the workload with the lounge system but I get the same problems as with the front end setting when the lounge system is off.

So is there any way I can get the bedroom system to work as a frontend when the lounge system is on but as a standalone system when it isn't?

Many Thanks

Well, a logical way would seem to be to set up the bedroom system as the master backend, and reconfigure the lounge system as the slave. But this would require that the bedroom system be powered up at all times when the lounge system is scheduled to run.

The simplest way would be to just run the lounge master backend 24/7.

A third way would be to configure the bedroom machine as a dual boot machine. One installation standalone, the second installation slave backend. You pick the one you need at startup from the grub menu.

A fourth way might be to set up a third, small, low powered, monitorless, eco-friendlier (if eco-friendly is the concern) machine whose only function is to run 24/7 as the master backend + database, and make _both_ the lounge and bedroom machines slave backends. Then they could both power up and down indiscriminately without concern for what the other one was doing.

There are likely other ways to solve the problem, but these are the four that spring to mind first.

---

### Post by SiHa on 2009-07-06
Assuming the BIOS on the backend in the lounge supports wake on lan, you could use this to get the frontend to wake the backend. I have my system setup to do this, for those rare occasions when I want to watch TV at 03:00, and the backend is in it's daily shutdown period.

See [[COLOR="Blue"]_here_[/COLOR]](http://packages.ubuntu.com/ca/hardy/net/wakeonlan) for details of this package.

I just added a few lines of code in my mythfrontend startup script that pings the backend, and if it gets no reponse, sends the 'magic packet' via wakeonlan, waits 45s for it to boot then checks again before continuing the startup.

I did experiment with an on-screen dialogue saying 'waking backend' with a countdown, but never got anything that looked very good. I was going to experiment with the MythOSD function, but it looked to complicated for me.

---

### Post by browndog289 on 2009-07-06
Thanks for your replies - I have set it as a separate backend at the moment which seems to work.

I will have a play around with your suggestions and see if I can get it to work.

---

