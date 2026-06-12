---
title: "Getting ring modulation with JACK"
date: 2008-04-10
forum: Multimedia Production
---

### Post by morganpatrick on 2008-04-10
Hello,

When I start jack and then go into a sequencer, whether Rosegarden or EnergyXT2 through wineasio, and load too many plugins (which is not many at all) or move around too quickly, or sometimes for no reason, my jack will crap out and rather than die or shut down I just start getting this horrible ring modulation on the sound and I have to shut everything down and restart JACK.

I'm running a realtime kernel, have realtime checked, my frames per period are 128, periods per buffer are 4. (used to be 64 f/b 64 and p/b 3). I am a member of the audio group as a user

In /etc/security/limits.conf I have:

@audio          -       rtprio          99
@audio          -       memlock 900000

I have  1.8 Gigs of RAM according to Ubuntu (it's actually 2GB).

I'm not sure if I should also edit /etc/sysctl.conf, or if my settings above are correct.

What's causing the ring modulation and how can I fix it?

Thanks.

---

### Post by morganpatrick on 2008-04-11
Help me, people, I've got the runs!

I know a lot of people have questions about getting jack to work properly so I'm not trying to be redundant. It's just that I thought I did everything right to get jack working (see above) so I don't get it. Is there something I need to do to ensure I'm in realtime mode?

right now I've gone back down to 64 f/p and 3 p/b and this seems like the most stable configuration because jack doesn't usually crash or go grainy and when it does start to get that ring modulation it corrects itself. However, in this config I get hundreds of xruns with tens of thousands in parentheses like 430 (533260) and that can't be good.

---

### Post by Shuffle777 on 2008-04-12
I'm no guru, but I've been using JACK for some time, now. Trying many configurations to get it work fine... Not sure I can help you but I'll try.

> **morganpatrick said:**
> Is there something I need to do to ensure I'm in realtime mode?

If you're using qjackctl and it says you are going realtime (dark yellow "RT" appears between "Started" and CPU usage), then you ARE. (If it doesn't, then you're not...)

> **morganpatrick said:**
> right now I've gone back down to 64 f/p and 3 p/b
I've been using JACK with several hardware configurations (also means several sound cards), and p/b 3 never did it for me... Always been 2. And for my current card (a good old really cheap SB Live! Player 1024), the lowest stable f/p I got is 256 (@48kHz). I can go down to 128 but I get some Xruns. Anyway, this settings give me a 10ms latency, which is really enough for me. You should not try to push the f/p too low because you won't manage unless your hardware can really follow.

> **morganpatrick said:**
> I get hundreds of xruns with tens of thousands in parentheses like 430 (533260) and that can't be good.
Sure, it can't be! That means something in your configuration is wrong regarding your hardware. Once more, don't think "realtime" means "zero latency" because that's not how it works.

Moreover, you have to keep an eye on the CPU usage because JACK needs more than it (or qjackctl) says when going realtime, but it can't be monitored in any way. I don't remember the source of this, but it was on some trustable site, like linuxmao.org or so. So, if your CPU is 100% used by the other apps, either the realtime scheduler can't keep up, OR your other apps don't get enough time, which isn't better. But all this does not seem to be the case here.

So, first, try to get rid of those Xruns (some can occur, but very few, like more or less 1 to 5 per hour when you still use your computer normally). Then if that "ring modulation" still occurs, we have to find why and how to prevent it.

Hope all this helps.

EDIT: Just want to add that Rosegarden's sequencer sometimes crashes for me (segfault). But I just have to restart Rosegarden, though. No trouble with JACK.

---

