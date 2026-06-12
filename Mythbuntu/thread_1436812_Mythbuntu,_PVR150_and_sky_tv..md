---
title: "Mythbuntu, PVR150 and sky tv."
date: 2010-03-23
forum: Mythbuntu
---

### Post by Mykk on 2010-03-23
[B]Hi all,

How easy would it be to configure mythbuntu with Sky TV using a pvr150 TV card? Is this even possible? Do any of you nice people know of any walkthroughs or tutorials that you could refer me to? 

Ive spent a bit of time googling it now and can't seem to find anything of relevance yet. 

I'm going to be using a "not too old" Dell Dimension and i feel fairly competent to get that setup with mythbuntu without any issues. Just need to know if its actually doable before i go any further.

If you need any more details (I don't think i missed any) please don't hesitate to ask. 

Cheers,

Mykk
[/B]

---

### Post by Mykk on 2010-03-23
Hope I'm not breaking the Bump rule here,

It usually 3 hours on the other forums i go on.

---

### Post by ubunterooster on 2010-03-23
I've heard it said 24hr. but think 12 is reasonable (you get the opposite crowds). I think this thread better belongs in the video and multimedia thread, I'll ask a mod to move it

---

### Post by Mykk on 2010-03-23
Thankyou :)

---

### Post by Elfy on 2010-03-23
> **Mykk said:**
> Hope I'm not breaking the Bump rule here,

It usually 3 hours on the other forums i go on.

> **ubunterooster said:**
> I've heard it said 24hr. but think 12 is reasonable (you get the opposite crowds). I think this thread better belongs in the video and multimedia thread, I'll ask a mod to move it

24 hours please :)

moved to mythbuntu forum

---

### Post by singedwings on 2010-03-23
It is quite easy now to set pvr150 with sky, but quite time consuming. [http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php") is a good all round guide to installing myth, although it does not include specific instructions for a pvr150.

When you set up the backend you will need to use the rt_uk grabber, tell it which channels you have/want. Then when you exit the setup cancel the database fill and in a terminal```
mythfilldatabase --manual
```and fill in the channel numbers/names (this is the time consuming bit).

In the frontend you will need to set the recording profiles to the correct screen size or the edges of the screen will be chopped off and the pvr150 can be a bit flaky if this is not changed.

Good luck.

---

### Post by Mykk on 2010-03-24
Thanks for the reply :)

Now at least i know this is possible I will give it a go!

---

