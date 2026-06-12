---
title: "Connecting to my primary computer from a netbook (vnc)"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by dearingj on 2009-08-14
[using a friend's login to post]

Hi,

I just switched to ubuntu from XP early this year, so I don't have a ton of experience with ubuntu's VNC or accounts system but I've been playing around with it recently and have it working well. I'm using dyndns.com and an updating script to simulate a static ip and have setup my router to forward port 22 to my ip (which *is* static on my router). With a friend's help I setup a new user and we have vnc working over ssh so he can connect to my computer. It pops up a box and asks me for permission to allow incoming connections though. I do really like this feature since it would allow me to be more flexible when giving out my vnc info so people can connect (as still remain confident that I need to explicitly allow each connection), but my question is this: how can I setup a second account (with a different password of course) that does not ask visually for permission to connect?

I'm asking this because I'm going to be getting a new netbook in a few days and would like to be able to connect to my primary computer and use programs, transfer files, etc, freely without having to even be in the same city. I'd like to be able to connect from my netbook while on campus, in another city, or on a trip, and not be blocked by the requirement that someone click accept on the other end!

How could I get my computer setup this way? Would I need a separate program for transferring files from the main computer to my netbook?

Thanks!

---

### Post by dearingj on 2009-08-14
I've got the ssh stuff figured out. Basically i've narrowed it down to this:

Is there a way to require EITHER a password OR confirmation in vino, but not both? Checking both options has the security measures stack...

---

