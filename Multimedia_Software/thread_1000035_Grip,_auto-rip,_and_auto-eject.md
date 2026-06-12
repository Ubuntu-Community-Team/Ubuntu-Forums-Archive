---
title: "Grip, auto-rip, and auto-eject"
date: 2008-12-02
forum: Multimedia Software
---

### Post by JDVyska on 2008-12-02
The Grip site seems to be a bit ... dead, so I was hoping some folks here might know what's going on.

Here's what I want to accomplish:
[LIST]
[*]Pop an audio CD in the drive
[*]Grip rips & encodes the CD
[*]When done, Grip pops out the disc
[*]I want to leave grip running all the time so I can just chuck in disc after disc, to digitize my collection over time
[/LIST]

I figured the hardest part would be the 2nd, but I'm actually battling more with 1 & 3. 

What seems to be happening is one of two things:
 - The CD drive pops open after burning, then closes immediately, starting the rip process over
 - The drive *doesn't* open, but the process starts over anyway

Here's config screenshots at the moment.  I've fiddled a lot with them.

[IMG]http://www.thedirtyhordes.com/images/grip1.png[/IMG]

I found the 'faulty eject' option was better to get the drive to open from the App.  Polling the drive is needed to get Grip to notice new discs and start the process.  10 seconds might be too long, but I wasn't sure if that was causing the problem with the drive re-closing.

[IMG]http://www.thedirtyhordes.com/images/grip2.png[/IMG]

I've tried Auto-eject delays ranging from 0-15, to see if that's the issue.





Anyone have any notion?

---

### Post by mc4man on 2008-12-02
You haven't mentioned whether using 8.10 or 8.04 which would make a difference.
8.10 has /had a bug which caused cd/dvd drives to retract immediately after ejection (since patched, in updates, udev (124-9) I believe.

I'd uncheck the faulty elect and patch on 8.10

---

### Post by JDVyska on 2008-12-03
Heya!  Thanks for the tip.  I am running 8.10 on that machine.  I made sure I had the updated udev, shut off the faulty eject.  No dice.  Turned back on faulty eject.  Still no good.


I'll tinker with it more this afternoon and see if I can give more detailed information.  For example, I'll stop Grip's 2nd go-around on ripping a CD, then the eject button (either within Grip or the front of the machine) doesn't work until I quit Grip.

---

