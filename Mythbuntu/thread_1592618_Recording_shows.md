---
title: "Recording shows"
date: 2010-10-10
forum: Mythbuntu
---

### Post by jrd on 2010-10-10
Hey guys,

  I haven't set up my system yet but I wanted to ask a question before I did. Can I tell mythtv what tuner to use for recording if I have more than one? The reason I'm asking is I will have 2 cable boxes in my setup. One for watching tv and another for recording. I use comcast and a lot of channels are encrypted so I have to go though the cable boxes. Basically I want to be able to watch live tv on one channel while recording another channel at the same time. Can I do this? Can you guys point me to a howto on how to do this?


Thanks

---

### Post by tgm4883 on 2010-10-10
> **jrd said:**
> Hey guys,

  I haven't set up my system yet but I wanted to ask a question before I did. Can I tell mythtv what tuner to use for recording if I have more than one? The reason I'm asking is I will have 2 cable boxes in my setup. One for watching tv and another for recording. I use comcast and a lot of channels are encrypted so I have to go though the cable boxes. Basically I want to be able to watch live tv on one channel while recording another channel at the same time. Can I do this? Can you guys point me to a howto on how to do this?


Thanks


Are you hooking up both boxes to your mythtv system? Are you going to have one of your cable boxes hooked up to your TV?

MythTV will always use the first tuner first for recordings. So if you have tuner1 and tuner2, it will always try to use tuner 1 first.

There is a setting to not conflict livetv and recordings which basically makes livetv start at the last tuner and go backwards but that doesn't sound like what you are looking for.

---

### Post by jrd on 2010-10-10
Well I can set it up anyway I need to but the plan was to run both boxes through the computer so I can pause live tv etc.... As far as myth using input1 for recording and input2 for live that sounds fine. I just wanted to make sure it was simple to record once everything is set up because one of the people who will be using this is not very technical to say the least. To sum it up I want to be able to:

1. Get all my channels (I use comcast and do not have high def channels, without the box I do not get all my channels)
2. Be able to pause rewind etc live tv
3. Be able to record one channel while watching another
4. Do all this with one remote if possible

Any setup ideas or what hardware to use etc is very welcome

---

### Post by tgm4883 on 2010-10-10
Ok, so i'm a little confused by this statement then

>  I use comcast and a lot of channels are encrypted so I have to go though the cable boxes.

You will be unable to watch encrypted content in MythTV. Now I have a couple questions.

1) How do you intend to get the video from the cable box into the mythtv box?

2) How do you plan on changing the channel on the cable box?




MythTV itself can handle the scheduling of shows, so if you are watching live tv on one tuner and a recording comes up it should use the other tuner. That part shouldn't be an issue

---

### Post by itlarson on 2010-10-12
I'd like to point out that when you set up to record a show, you can set it to 'prefer' the tuner of your choice.

---

### Post by jrd on 2010-10-12
> **itlarson said:**
> I'd like to point out that when you set up to record a show, you can set it to 'prefer' the tuner of your choice.

That's what I was wondering. Thank you.

> **tgm4883 said:**
> You will be unable to watch encrypted content in MythTV. Now I have a couple questions.

1) How do you intend to get the video from the cable box into the mythtv box?

2) How do you plan on changing the channel on the cable box?

1. My plan is to run the signal from the cable box to the computer instead of the tv, this way the cable box does the decrypting for me and just sends a normal analog signal to the tuners.

2. With an IR blaster

---

