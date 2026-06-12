---
title: "amsn webcam; working fine in karmic; not in lucid"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by DoppyNL on 2010-05-03
Hi people,

I've been using Karmic for some time and used amsn.
In amsn I use the webcam quite often, and this all worked fine in Karmic, even without any further configuration.

I've now installed Lucid and again installed amsn.
But this time I'm having webcam problems.
The cam itself works fine, as it seems to be a network problem.
At first it didn't work at all, then I found that I seemed to be "firewalled" according to the preferences of amsn. So I forwarded the port in my router. Now I'm capable of running 1! webcam session 1! way; not both ways.

Alltough I'm a network-newbe, I suspect that in Karmic amsn was allowed to use upnp, but it can't do that in Lucid. Could also be something else, as I've got no clue.

Anyone who can help me with this? (and probably some other people who run into this same problem....)

tnx.

If you need more info, please ask.

---

### Post by DoppyNL on 2010-05-04
not being pushy or anything...

No brilliant minds here who know what might be the problem?
Am I in the wrong section?


tnx!

---

### Post by DoppyNL on 2010-05-06
1 more bump;
if no response I will try somewhere else...

If you know a more appropriate place to ask this question, please let me know.

thank you all.

---

### Post by DemonZer0 on 2010-05-08
This happend to me too, maybe it has something with the new protocol of webcam that made MS

---

### Post by DoppyNL on 2010-05-09
I don't think that is a issue at this time.

Mostly because of 1 thing I've seen changed:
previously, when testing the connection in the preferences screen of amsn, it would tell me my connection was fine.
Now it tells me I'm firewalled... That is before the actual webcam is used!

As I have not changed a thing on my router/modem, I suspect a change from Ubuntu 9.10 to 10.04. Either in amsn or another package (firewall perhaps).

But I have no clue on where to look or what to try.

---

### Post by dokurosan on 2010-05-13
Well, does your webcam assistant in amsn actually shows the image of your webcam? Because mine stopped working when 9.10 -> 10.04 .. even Cheese does not show any images, it just starts and goes down without any error messages. Let me know if any images comes up at all in your Lucid.
Hugs \o/

---

### Post by DoppyNL on 2010-05-13
Hi, thanks for your reply.

- cheese is showing images from my webcam
- amsn webcam assistant shows images from my webcam without a problem
- I can get 1-way webcam working by doing a manual port forwarding in my router. This can be done either way, but not both ways at the same time. So I can either receive webcam-video from someone else, OR send webcam-video to someone else.

The last point is what makes me think it is network related.
And no, I didn't change a thing in the router.

---

### Post by dokurosan on 2010-05-14
well... after rebooting, strangely, my webcam started working (cheese and everything else). before, not even that was wroking.. don't ask me why the f*** it worked after rebooting.
ALTHOUGH... I've tried to start both income and output webcam at the same time.. and it didn't worked out for me too... only the first or the remaining webcam stayed working...  
I'm about  to do some tests with other people, but I'm not expecting anything good... my conf is the same as 9.10... maybe something in the new protocol that 0.98.3 implements ... who knows.. in 9.10 was 0.98.2 .. 

anyway, I'll try to check and will let you know if anything comes up.. let me know too if you discover anything.
best wishes
Olavo.

---

### Post by DoppyNL on 2010-05-14
I got it working, but not completely as it was....

I allready forwarded port 6890 to the computer I wanted to use the webcam on. But that only gave me 1-way webcam.
I now forwarded port 6890-6899 to the computer, and now it works fine.

Seems to me that since lucid amsn isn't able to automaticly do that... while it could do that in karmic and before...
what has changed?
Something in the firewall? something with upnp?

---

