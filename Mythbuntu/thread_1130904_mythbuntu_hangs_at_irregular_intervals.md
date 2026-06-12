---
title: "mythbuntu hangs at irregular intervals"
date: 2009-04-20
forum: Mythbuntu
---

### Post by Balachmar on 2009-04-20
Hi,

I have been running mythbuntu for a while now. But since a few months my system started freezing up some times.
I thought it had something to do with me running an old kernel because I messed something up and it didn't update well.
But last weekend I upgraded to 9.04 and fixed the apt issues.
But it still froze.

Now I don't really know how to go about debugging this, because as far as I know nothing turns up in the logs. But maybe I am not looking in the right logs.
I thought it was a heat problem, but it isn't.
The only weird thing I did notice was that my load averages were up once. like 8 (and I have a single core cpu) but the largest percentage was in idle. According to top the %id (is idle right).

I hope someone can help me fix it, because at first my gf said she didn't need it, but now she really gets annoyed if it didn't record something. And I kinda liked the fact that she was wrong in thinking it was a useless machine :) So I want it to work (perfectly).

Thanks in advance!

---

### Post by Balachmar on 2009-04-21
ok, last night it hung on me again!
Now what I did was the following:
I had been watching a recording for over half an hour. Then I decided to shutdown the machine. At the question do you want to shutdown? I changed my mind. Then it hung.
Switching to another terminal using ctrl-alt-F1 etc. didn't work. Also ctrl-alt-backspace didn't work.
So I have restarted the computer and noted the time it happened. Any ideas for logs I need to check?

---

### Post by superm1 on 2009-04-21
So the most important thing to do is to check your hardware.  Memory and hard drive problems are the number 1 culprit of random/irregular freezes

---

### Post by Balachmar on 2009-04-22
Could also be because my mpeg2 card is having an irq shared with my onboard audio card?
I have heard that this could cause problems as well, although I wouldn't know how to solve the problem, except moving the cards around.

This is my lspci output
[http://pastebin.com/m55c26634](http://pastebin.com/m55c26634)

---

### Post by Balachmar on 2009-04-27
Fixed the irq issue. But it still hangs sometimes.
I now make sure mysql is logging as well.
It seems to be a graphics issue. I have graphics glitches all the time. But sometimes it really crashes. And the computer is unresponsive.
The HD I have tested with a smart long test. And everything seems fine.
The only thing left is memory or the graphics...

---

### Post by Balachmar on 2009-05-20
I switched to the normal rendering instead of openGL and now everything seems to work fine.

---

