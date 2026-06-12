---
title: "Multi-TV Home Configuration"
date: 2008-06-28
forum: Mythbuntu
---

### Post by scopo911 on 2008-06-28
I'm new to Mythbuntu and considering a setup. I have some basic questions that I hope someone can answer for me.  Here's what I'd like to do, is this possible / practical?

My goals are:
1. get rid of my Verizon Fios set top boxes
2. watch TV from any one of three HD Tv's in the house
3. watch recorded programs from any one of three tv's 
4. watch stored DVD movies on any one of three tv's


I'm thinking I could set something like this up....
1. One (1) primary back-end server, with multiple (3) tuner inputs.  This would be a headless box, in the cable closet used to store and serve all TV.  

2. Set-up three (3) minimal front end, (diskless?) boxes one at each TV connected via Ethernet to the back-end server.  Each TV is a HDMI hi-def 1080i

3. from the back-end server, serve and store tv and movies.

Thoughts?  SP

---

### Post by dsbw on 2008-06-28
> **scopo911 said:**
> Thoughts?  SP

Do they make 40,000rpm disk drives?:popcorn:

---

### Post by shad0w_walker on 2008-06-28
You would need a very serious setup to run 3 independant full HD streams, bare in mind that MythTV records EVERYTHING you watch, not just the programs that are recorded, to act as a giant buffer for timeshifting and the like.

I would also suggest you put atleast small disks into the the clients, enough to run the OS off, to reduce the strain on the main server.

I'm assuming you aren't going to get Verizon to give you a magical way to access their feeds directly, so you'll have to go through a set top box of some description and output from that to the server. If that's true, you'll need 3 boxes and if the system is anything like here, 3 cables to run it from, which I imagine would turn into 3 subscriptions.

---

### Post by ian dobson on 2008-06-29
Hi,

FRONTEND
1) I would recommend using small disks in the frontends (A small 2 1/2 inch portable drive) would be enough.
2) Use NVIDIA graphic cards as the drivrs seem to have less problems.

BACKEND
1) For the backend make sure you have enough disk space for your recordings.
2) Be careful which motherboard you use for the backend. I have 3 tuners in my backend and all the PCI slots are filled. The space between the cards and the metal tuner boxes is so small that I had to wrap paper around the tuners to reduce the chance of a short circuit.
3) Tuner cards get really warm so make sure you have enough cooling.
4) Don't use wireless for your frontends, save yourself problems in the future and run cables.

Regards
Ian Dobson

---

### Post by scopo911 on 2008-06-29
Thanks for the reply's, makes sense.  Maybe one monster backend is not the way to go.  

One of my main requirements is that I want to be able to watch recorded content on any of the three TV's. Is this still the best way to do it?  Or would I be better off with three equally configured boxes, one at each TV?  If I do that is there a way to share recorded programs between them?

Thanks again for the help!  SP

---

### Post by fenian on 2008-06-29
I would take a look at the [HDHomerun]("http://www.engadgethd.com/2006/10/30/engadget-hd-review-hdhomerun/").

---

