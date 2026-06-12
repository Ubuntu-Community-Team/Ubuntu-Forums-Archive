---
title: "Want to span monitors on a Remote Desktop"
date: 2009-03-19
forum: Multimedia Software
---

### Post by Znode on 2009-03-19
I thought the 6 monitor setup was fantastic!!!

What I am trying to do is use a terminal client (have realVnc) where there are 3 monitors and get a session on my Ubuntu machine that spans those 3.
The terminal client is XP (just happens to be the system with the most graphics cards).
The problem seems to be that I need to actually have cards in the machine running Ubuntu before it will span (they need to match???).
I don't really need a monitor on the Ubuntu at all.

Does anyone know:
    1. Best terminal server for the Ubuntu side.
    2. Best terminal client on the XP side.

Thanks.

---

### Post by mobilediesel on 2009-03-20
> **Znode said:**
> I thought the 6 monitor setup was fantastic!!!

What I am trying to do is use a terminal client (have realVnc) where there are 3 monitors and get a session on my Ubuntu machine that spans those 3.
The terminal client is XP (just happens to be the system with the most graphics cards).
The problem seems to be that I need to actually have cards in the machine running Ubuntu before it will span (they need to match???).
I don't really need a monitor on the Ubuntu at all.

Does anyone know:
    1. Best terminal server for the Ubuntu side.
    2. Best terminal client on the XP side.

Thanks.

I think you're looking for [Synergy]("http://synergy2.sourceforge.net/").
> Synergy lets you easily share a single mouse and keyboard between multiple computers with different operating systems, each with its own display, without special hardware. It's intended for users with multiple computers on their desk since each system uses its own monitor(s).

It can be tricky to set up but it's worth it.

---

### Post by Znode on 2009-03-20
Synergy may come in handly down the road.

However I really do want to have _just one_ set of monitors.

In Remote Desktop, the user cannot be signed on to the terminal server and the terminal server creates a virtual termianl of a size requested by the client.

The client usually requests the total amount of space on the spanned monitors, and this is what it asks for.

Anyway - I want to unplug my monitor on Ubuntu and remote login from the XP, which has three monitors.

Any thoughs?

---

### Post by mobilediesel on 2009-03-20
> **Znode said:**
> Synergy may come in handly down the road.

However I really do want to have _just one_ set of monitors.

In Remote Desktop, the user cannot be signed on to the terminal server and the terminal server creates a virtual termianl of a size requested by the client.

The client usually requests the total amount of space on the spanned monitors, and this is what it asks for.

Anyway - I want to unplug my monitor on Ubuntu and remote login from the XP, which has three monitors.

Any thoughs?

I misunderstood the first post. [FreeNX]("http://freenx.berlios.de/") is what you're looking for along with [NoMachine]("http://www.nomachine.com/download.php") for the windows machine.

> [NX]("http://freenx.berlios.de/") is an exciting new technology for remote display. It provides near local speed application responsiveness over high latency, low bandwidth links. The core libraries for NX are provided by [NoMachine]("http://www.nomachine.com/download.php") under the GPL. FreeNX is a GPL implementation of the NX Server and NX Client Components. 

---

### Post by Znode on 2009-03-21
I wanted thank **_mobilediesel_** for the help.
I installed nomachine's NX and it did the trick.

Sidenote:
One thing I had to do was use my nvidea control panel on XP to change from **dual view **(monitors treated seperatly and windows streching the workspace across them) to **horizontal stretch** (windows thinks this is one big monitor).

The only iritation with this is that with 2 monitors, a dialog box will come up in the split between monitors.

When it was dual view I tried NX:
   [LIST=1]
[*]Full Screen
[*]    Use available
[*]    Custome (2560 x 1024)
[/LIST]
And all of these only showed up on the one monitor.

---

