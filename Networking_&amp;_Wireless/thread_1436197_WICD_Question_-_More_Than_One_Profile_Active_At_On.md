---
title: "WICD Question - More Than One Profile Active At Once?"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-03-22
I run Ubuntu on my work laptop. Typically I don't have a lot of issues, but the default network manager has been really wearing on me. I've had a few disconnects randomly here and there, no big deal. But when I travel from 1 location to another in the building and bounce from access point to access point, despite them sharing the same SSID, network manager tends to crap its pants, forcing me to delete the entry and re-connect on fresh grounds by putting in all of the credentials again. This brought on WICD.

So far, WICD hasn't failed me yet. Real solid, love it. (perhaps it should be default...) Anyways, one minor snag.

I do imaging with FOG on my laptop. I have a static IP set to the wired interface, and normally let wireless hang around as DHCP. This is nice because I can be on my laptop imaging a computer WHILE being on the wireless to check email and remote control other devices.

Thing is, each time I "connect" to my static wired interface, it drops ALL interfaces, then activates only static wired. Same goes in vice versa. If I connect to the wireless, it drops my static IP connection, which is needed for imaging.

Can I have two profiles/two interfaces activated at once with WICD? Or am I limited to only 1? Either way, not a big deal. FOG can push out an image to a single machine in less than 5 minutes, so it's hardly a set-back. But still, a nice +1 if I could...

---

### Post by 2hot6ft2 on 2010-03-22
I have been wanting dual simultaneous connections for a while now which is what it sounds like you're after.
NM wont do it and neither will WICD. Before WICD 1.6 came out there was talk of it supporting them but once it came out guess what still no support for it. Now WICD is supposed to have that support in version 2.0 according to what I read, but I'm not holding my breath since that was supposed to be the case in 1.6 and it didn't happen.
Hopefully one day they will make things easier for those of us that want it.

To sum it up you'll have to find a way of doing it without using WICD or NM. Unless someone would care to enlighten us both.

---

### Post by Roasted on 2010-03-22
I got it to work with NM, but it required a few steps.

First, I had to delete the default wired interface in NM so that entire entry was blank. I left the wireless entry alone.

Then I edited the network interface file accordingly. It seems as if NM works on top of the network interface file. Since there was no wired connection for NM, it as a result wasn't confused when it came to using wireless and wired together.

Network interface file took care of wired. (no wired entry in NM to interfere)

NM took care of wireless.

Both could work together.

This same thing in WICD doesn't work, because whenever you activate another connection (aka if I'm on wired, yet activate wireless) it brings down all connections, THEN adds the one you clicked on. In turn, this brings me offline from wired, and brings up wireless. The exact opposite happens in vice versa - Wireless gets kicked, wired gets activated.

Although I have to wonder, at one point a few weeks ago I plugged in a USB wifi adapter in my desktop and I'm pretty certain I pulled both connections accordingly. I'll have to test it later to see if I can pull a valid IP from both interfaces.

When is WICD 2.0 coming out?

---

### Post by Roasted on 2010-03-22
So I tested out my USB wifi adapter in my desktop at home while wired. I got some weird results.

While wired, I plugged in the USB adapter and tried to connect to my wifi network. 3 times it came back asking me to put the password in. The password was correct, but it was like it was "timing out" with trying to connect.

I disconnected the wire, plugged in USB adapter, connected to wifi network - blam. 10 seconds later I was wireless.

I disconnected everything, Plug in USB adapter, connected. Plug in wire, connect. Oddly, both connected then.

Either way, it'd be nice to be able to utilize both wifi and wired at the same time without issues. Despite there seeming to be some sort of a work-able thing with NM, it sounds kind of half assed. We'll see if WICD brings it to the table...

For the record, I got disconnected about 7 times this morning within a 2 hour time span. Once I installed WICD, I didn't get disconnected a single time. Oddly enough, I've been on my laptop for the last 4 hours at home and haven't had a single disconnect. I wonder if congestion on the wifi network at work (and load balancing) booted me off?? There WERE 30 laptops in the room across the hall.. I guess it's possible. Perhaps I didn't need WICD after all...

---

