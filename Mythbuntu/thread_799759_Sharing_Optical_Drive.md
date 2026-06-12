---
title: "Sharing Optical Drive"
date: 2008-05-19
forum: Mythbuntu
---

### Post by jlaham on 2008-05-19
Hi,

I have just finished building a DVD storage server, that is pretty much just a PC (motherboard, memory, cpu... the works!), with all my DVD's placed in it. Through certain commands I have managed to put together a motor-based system that loads the required DVD by index (much like a car multi-disc cd changer). This PC is currently running a mythbuntu primary backend (NO frontend). My Frontend is a PC located remotely in the house. What I am planning on doing is being able to control my dvd disc changer and to stream my DVD's using MythTV.

Now, picking and loading the correct DVD is not hard, I just need to send certain commands to my backend to do so. But in order to stream a video from a DVD disc loaded on my backend, I was guessing that I would have to share my optical drive on the backend and in turn mount it at a certain mountpoint on my frontend, so maybe my frontend may be able to refer to it as an optical drive (even though it is being shared over the network).

Does this make any sense? And if so, how can I go about doing this?

How do I share my optical drive on my backend?
Can I get my frontend to see this share as a normal optical drive, so it may think of it as a local DVD (or at least something similar)???

---

### Post by grytpype on 2008-05-19
> **jlaham said:**
> 
How do I share my optical drive on my backend?
Can I get my frontend to see this share as a normal optical drive, so it may think of it as a local DVD (or at least something similar)???

You can share an optical drive the same ways you can share a regular file system.

Two ways I can think of: Use NFS (Network File System) or Samba.

---

### Post by jlaham on 2008-05-20
I was actually planning on trying that, the only thing that I need to make sure of is whether the frontend will actually recognize it as an optical drive and not just a regular share. I just gotta dabble around with it a little, but i just ran into a DHCP server problem that's driving me up the wall. So until I get that fixed I won't be doing much on this.

So once I get a chance to get back into this, I'll let you know what happened.

Meanwhile, anyone else have any suggestions, feel free to post.
:-)

---

### Post by StaticIp on 2008-06-20
I have a dvd drive shared from my wondows machine, can I make ubuntu see it as a dvd drive and write to it from ubuntu via the cd/dvd creator? Both are local, my ubuntu machine dooes not have a dvd drive and I can't switch them so it would be nice to be able to use as I requested

---

