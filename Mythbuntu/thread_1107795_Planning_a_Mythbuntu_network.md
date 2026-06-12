---
title: "Planning a Mythbuntu network"
date: 2009-03-27
forum: Mythbuntu
---

### Post by tapsevarg on 2009-03-27
Hello,
I am going to move towards Linux. I have chosen the mythbuntu distro as it suits my needs.

So I will have four items in this network. The type of network will be ad hoc. There will be an Eee Pc, a Wii, printer, and a server. The server will act as the wireless router.

So here's my issue. It may be a stupid one too.

The server will stream music and movies. But the server will not have a monitor connected to it. _So do I still need a video card for it? Likewise for an audiocard._ Mythbuntu has the requirements listed for audio and video. But it makes no mention whether those requirements are for frontend or backend. Common sense tells me that it would be frontend. But I guess it's possible each card has some function prior to streaming audio or video.

---

### Post by tapsevarg on 2009-03-28
Anybody?

Do I need a video and sound card on my backend if it is just going to be a server and nothing else?

---

### Post by Nikas on 2009-03-28
Computers does not like to start without a videocard. :)

You don't need any soundcard.

---

### Post by klc5555 on 2009-03-29
> **tapsevarg said:**
> Anybody?

Do I need a video and sound card on my backend if it is just going to be a server and nothing else?

It's hard to do configs and maintenance exclusively from a remote shell. Regardless of whether you'd prefer to run the backend headless, at least stick some $15-dollar piece of low-res junk in the machine, just for those times when you'll have to plop a monitor on it to work on the backend machine locally. Because sooner or later you'll need to. Most likely sooner.

---

### Post by dr_dred5 on 2009-03-29
My backend runs with no monitor and I do all my updates through SSH and VNC (remote desktop) and there have been no issues. 

That being said, it does still have an onboard video card.

Cheers!

---

### Post by RoboNuggie on 2009-03-30
Like what's been said above, just a cheapo video card, no sound card...

My headless backend (oo-er) sits in the spare room, all on it's own... poor thing, only occasionally getting a visit via shh. Only needed a display when setting up, but since then no problems at all for 6 months now.... watch, it will all go wonky now...

---

### Post by kpoole on 2009-04-13
Anyone else think there's something odd about the phrase "headless backend"?  :-)

That implied joke aside, as mentioned, the basic PC will not boot without some kind of video card and it's going to be useful to have it for the install but after that you can leave it monitor-less and do your maintenance remotely.

I'll be hanging out in the Mythbuntu threads for a few days now, I'm sure.  I'm finally getting around to retiring the last windows machine in my LAN in favor of a Mythbuntu 8.10 server.

---

