---
title: "Open existing X-session via NX"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by bothebobo on 2010-06-06
Hi all,

My problem is conceptually simple, and I suspect it takes root in my fundamental misunderstanding of remote X-sessions.

Setup: 
Computer AA has dual X-sessions.
One X-server is attached to a local screen(AALocal) and the other to a remote screen(AARemote) in the living room.

I run Synergy via my laptops in the house to control AARemote.
For those who do not know, Synergy lets you easily share a single mouse and keyboard between multiple computers with different operating systems, each with its own display, without special hardware. It's intended for users with multiple computers on their desk since each system uses its own monitor(s). - taken from Synergy's website

Problem:
This is a temporary solution as linux/Ubuntu and software have funny tendencies when dual X servers are running, a simple example would be the notification bar cannot create two instances - thus Rhythmbox controls work odd. Firefox cannot create two instances and the list goes on. 

Proposed solution:
Run a single X-server on AA and use dual screen (or TwinView by NVidia) to combine AALocal and AARemote and then use NX to control the mouse and keyboard.
My situation is that I cannot get NX to log into an already existing X-server, and even if it could, can it handle odd resolutions, e.g. two screens with different resolutions?

You may ask why I don't just use synergy on the combined TwinView, windows have a tendency of popping up on AALocal while I'm sitting in the living room in front of AARemote. And herein lies the beauty of using NX to control the screens is that I get a screen on my laptop too so I can view both AALocal and AARemote.


Please, if anyone has a new suggestion to efficiently run a screen in the living room with no local keyboard or mouse let me know.

Thanks for any help.

---

