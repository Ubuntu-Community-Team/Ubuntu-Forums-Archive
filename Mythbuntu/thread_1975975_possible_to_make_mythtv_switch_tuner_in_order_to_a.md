---
title: "possible to make mythtv switch tuner in order to accomplish a channel switch?"
date: 2012-05-08
forum: Mythbuntu
---

### Post by rrofes on 2012-05-08
Hello,
I installed mythbuntu 11.10 and set up mythtv. I have a dual tuner card: terratec cinergy t pcie dual. It was hard getting it to work properly, but now it is done. :)
My question is about switching channels while seeing live TV. I have observed that mythtv does not accomplish an automatic change of tuner in order to execute a change of channel requested by user. Will explain with an example:
- Tuner 1 is busy recording. I am watching this same recorded channel, in a live TV session.
- if I try to switch to a channel in the same multiplex, no problem, the tuner must not be "touched" and channel change is accomplished. I am still watching something that comes from tuner 1.
- But if I try to change to a channel in a different multiplex the order is not executed by mythtv, even if the second tuner is not in use. To switch channel I have to first switch tuner (there is a live TV menu option to do so) and after, once in the second tuner, switch to the channel I want. 

I have activated the option "use for live tv the less probable tuner to be in use by a recording" or something like that. I think that the only thing that makes this option is to use by default the "2nd tuner" when you start a live tv session, while the recordings usually use "1st tuner". Anyway, not sure. Someone able to confirm/correct? Anyway, I think this option does not prevent the situation that I explained before, only makes it less probable.

All in all, it seems to me a weird behaviour more related to hardware concepts than to usability. If there is no option I will live with it, but I am wondering how I am going to explain to my family what a multiplex is and why it is so hard to switch channels...

So my final question is: can I configure it in a way that mythtv switches the tuner automatically to accomplish a change of channel ordered by user?

---

### Post by Sctmon on 2012-05-08
Hi,
 I just got some time to test my system and it does not seem to have this  issue. I started recording a channel and then watched it as it was  recording (tuner 1). I then changed channel to another on the same  multiplex (it changed to tuner 2) and then again to a channel on a  different multiplex (tuner 3) and it seemed to work fine. All without having to manually switch tuner.
 
 I also tried scheduling 4 simultaneous recordings and as long as the 4  channels were limited to being within 2 multiplexes it worked and  recorded all 4 programs!
 If I tried to schedule 4 recording over more than 2 multiplexes it flagged the recordings on the other multiplexes as conflicted.

Could make the problem something other than hardware related.

---

### Post by nickrout on 2012-05-08
> **rrofes said:**
> Hello,
I installed mythbuntu 11.10 and set up mythtv. I have a dual tuner card: terratec cinergy t pcie dual. It was hard getting it to work properly, but now it is done. :)
My question is about switching channels while seeing live TV. I have observed that mythtv does not accomplish an automatic change of tuner in order to execute a change of channel requested by user. Will explain with an example:
- Tuner 1 is busy recording. I am watching this same recorded channel, in a live TV session.
- if I try to switch to a channel in the same multiplex, no problem, the tuner must not be "touched" and channel change is accomplished. I am still watching something that comes from tuner 1.
- But if I try to change to a channel in a different multiplex the order is not executed by mythtv, even if the second tuner is not in use. To switch channel I have to first switch tuner (there is a live TV menu option to do so) and after, once in the second tuner, switch to the channel I want. 

I have activated the option "use for live tv the less probable tuner to be in use by a recording" or something like that. I think that the only thing that makes this option is to use by default the "2nd tuner" when you start a live tv session, while the recordings usually use "1st tuner". Anyway, not sure. Someone able to confirm/correct? Anyway, I think this option does not prevent the situation that I explained before, only makes it less probable.

All in all, it seems to me a weird behaviour more related to hardware concepts than to usability. If there is no option I will live with it, but I am wondering how I am going to explain to my family what a multiplex is and why it is so hard to switch channels...

So my final question is: can I configure it in a way that mythtv switches the tuner automatically to accomplish a change of channel ordered by user?

Menu|switch cards (or wording to that effect).

Neither of you seem to mention what version of mythtv you are using!

---

### Post by Sctmon on 2012-05-09
> **nickrout said:**
> Menu|switch cards (or wording to that effect).

Neither of you seem to mention what version of mythtv you are using!

It would probably have been useful information!. This is part of a new system I am building to replace the other one at home and I installed mythbuntu 12.04 myth 0.25 with repositories activated.

---

### Post by nickrout on 2012-05-09
> **Sctmon said:**
> It would probably have been useful information!. This is part of a new system I am building to replace the other one at home and I installed mythbuntu 12.04 myth 0.25 with repositories activated.

How many physical tuners do you have? You are limited to one mux per physical tuner.

Your system seems to switch tuners in livetv when you request another mux. rrofes' system doesn't seem to. I wonder if he will tell us what version of mythtv he is using.

Incidentally this is a long standing "complaint" - the system not automagically moving to another physical tuner if needed when channel surfing. It will be interesting to know if this has been fixed in 0.25, as the dev respponse i usually to the effect "mythtv is not optimised for livetv, get a life, record what you want and watch it when you want to watch it".

---

### Post by Sctmon on 2012-05-09
It does seem that it is limited to 1 mux per physical tuners and this card has 2 tuners. It seems to be able to watch/ record 2 channels on the same mux per tuner

---

### Post by nickrout on 2012-05-09
> **Sctmon said:**
> It does seem that it is limited to 1 mux per physical tuners and this card has 2 tuners. It seems to be able to watch/ record 2 channels on the same mux per tuner

One mux per physical tuner is a given, you cannot tune more than one mux at a time. It is a limitation of the technology.

The number of virtual tuners per physical tuner is set by mythtv-setup. The myth default is 2 but I run 4 quite happily. I think there is a maximum set by the source code, maybe 5 or 8 - there is a recent thread on the -users mailing list about the maximum and whether it is needed at all. Anyway if you run mythtv-setup you can increase it.

---

### Post by Sctmon on 2012-05-09
You learn something new every day! I have been running Mythtv for a few years now with a nova T 500 card and didn't realize you could record more than one channel on a mux. There is a lesson there somewhere... Perhaps it is always read the docs!

---

### Post by rrofes on 2012-05-09
Thanks to all for your contribution to the post. In effect, the reason is that I am using mythtv 0.24. Yesterday I got feedback from mythtv mailing list, two people told me it had been that way until 0.24, but it is solved in 0.25!!! It seems that I made my first install of mythtv one week too early!

---

### Post by nickrout on 2012-05-09
> **rrofes said:**
> Thanks to all for your contribution to the post. In effect, the reason is that I am using mythtv 0.24. Yesterday I got feedback from mythtv mailing list, two people told me it had been that way until 0.24, but it is solved in 0.25!!! It seems that I made my first install of mythtv one week too early!

The upgrade is extremely easy.

---

