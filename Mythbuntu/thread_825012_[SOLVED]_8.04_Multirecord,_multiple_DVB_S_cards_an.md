---
title: "[SOLVED] 8.04 Multirecord, multiple DVB_S cards and PIP issues"
date: 2008-06-10
forum: Mythbuntu
---

### Post by Verzweifler on 2008-06-10
In case you have multiple DVB-S tuner cards defined, each of them with multirecord enabled, you will probably run into the very same issues I did. But help is on the way!

But first things first:
In mythtv-setup you can define how many simultaneous recordings are allowed for each card (i.e. multirecord). The card is then "cloned" and the settings of the card and its clone are stored to the database. Fine so far.

Let's assume, you define four DVB-S cards like I did from scratch each of them defined with a maximum of two recordings. You will end up with a total of eight cards in table *capturecard* of the database (which BTW I browse with phpmyadmin because I prefer graphical interfaces to command lines) numbered 1 to 8. Because you defined the cards one other the other, the card IDs 1 and 2 belong to the first physical card you set up and so on. 3/4 => card 2, 5/6 => card 3, 7/8 => card 4...
Still fine so far.

When you now look at the entries in table *cardinputs* you'll notice that also here, you have input 1 assigned to card 1 and input 2 assigned to card 2 both belonging to the very same physical card (see above, yes, it's card 1) with multirecord enabled. Still no problem here...

**BUT**

Let's turn over to actually watching TV (most probably with your wife sitting close to you). Just start it and switch on "picture-in-picture" (PIP) in the OSD. Once you did it, you will realize that you can no longer tune to all channels but that you are restricted to the channels sitting on the very same DVB-bouquet... Damn! Your wife won't like it, I promise.

The reason for that: 
Due to the setup made above, mythtv for PIP choses the input next to the one you used for watching TV. In my case, LiveTV always starts with input #8 (the last one) and then choses #7 for PIP, which is on the same card. This just locks on the same DVB-bouquet and you're busted...

My solution for that:
In the database I manually modified the cardinput-IDs in table *cardinput*. I selected all odd IDs (see example above) and changed the ID to 10+ID, i.e. 1 => 11, 3 => 13, 5 => 15, 7 => 17.
By doing so, I managed to break the strict order of inputs in that table, so my LiveTV now starts at input #17 (again: the last one) and choses #15 for PIP. Since #17 and #15 belong to different physical cards, you are safe and switching to any other channel should be possible. 
The only problem: in case there is a recording running on the physical card selected for PIP, you are restricted to that cards bouquet... 

Just be sure to have selected option "avoid conflicts between Live TV and scheduled shows" in "Setup->TV->Playback" in order to maintain a gap between the LiveTV card and cards selected for recording...


Hope this helped

---

### Post by ebike on 2008-06-10
Hi there,

I have a similar problem. I have two tuners and have set multirecord to 2 on each card. The trouble is that Myth doesn't seem to want to allocate resources correctly. For instance, If I am watching one multiplex on a frontend and try to watch another multiplex on a different frontend, it won't let me. i.e it behaves just like I have one tuner. I have tuned both multiplexes on each card and have them both attached to one video source.

Is this the correct way to do this? 

By the way, your statement:
> "avoid conflicts between Live TV and scheduled shows" in Setup->TV->Playback

I cannot see that setting...

---

### Post by ebike on 2008-06-10
An update ... the only way I can watch different mutiplexes on different frontends, is to set multirecord=1 for each card ..... but now I can only watch/record two things ......:confused:

Their must be a correct setup for this:mad:

---

### Post by Verzweifler on 2008-06-11
> **ebike said:**
> 
By the way, your statement:
> "avoid conflicts between Live TV and scheduled shows" in Setup->TV->Playback" 
I cannot see that setting...

Ooops, sorry for that... It is in Setup->TV->General on the first page...

---

### Post by ebike on 2008-06-11
No problem. Does anyone have a two card setup working right?

---

### Post by pssturges on 2008-06-12
I'm having a similar problem with my setup. I haven't been able to test it fully yet, so I'm  not quite sure of the exact behaviour.

I have 2 x DVB-T tuners setup with multirecord set to 2 on each. So far I have noticed that if one tuner is doing a scheduled recording, then *sometimes* you can only watch live tv on on the same multiplex as the recording. It's as if myth *forgets *that there are other tuners. BTW it would be nice if there was some feed back to the user as to the reason for not being able to change channels. ATM it just won't change.

I'll need to do some futher testing before I can pin down the exact circumstances that cause the problem.

Phil

---

### Post by ebike on 2008-06-12
Cool, I will be very interested how you get on...

---

### Post by ebike on 2008-06-14
Seems it is a problem with Mythtv ... see this thread.

--> [http://www.gossamer-threads.com/lists/mythtv/users/337494?page=unread#unread](http://www.gossamer-threads.com/lists/mythtv/users/337494?page=unread#unread)

Seems the developers see that multiple LiveTV's are not "normal" use :confused:

---

### Post by pssturges on 2008-06-15
Hmm,

That's the second significant bug I'm waiting on a fix for...:(
See here for the other.[http://ubuntuforums.org/showthread.php?t=810310]("http://ubuntuforums.org/showthread.php?t=810310") I hope we don't have to wait for a full release.

Phil

---

### Post by Verzweifler on 2008-07-02
Coming back to my first post for this issue:

Although I shuffled the cards a bit to make sure subsequent card IDs do not belong to the same physical DVB-S card, I still had an issue when watching LiveTV on one of the "cloned" cards: After a maximum of five minutes of LiveTV, the screen froze and I had to quit and restart LiveTV, which then worked for approx. another five minutes. 

After searching quite a lot, I realized that the freezes occured at fixed times, i.e. xx:01, xx:06, xx:11 ... So it was not five minutes of LiveTV that cause the freeze but something independent from that.

The only thing that "runs" on my system at fixed five minute intervalls is the EIT switch of transponder. At one time, I could verify that just before the freeze there was a "magic" channel switch, which I could associate with EIT. 

To cut it short: **If you are using multirecord on your DVB-S cards make sure that EIT is disabled for those.** If not, it appears that EIT running on one of the clones switches transponder although the other clone is busy with LiveTV, which then causes a freeze. 

My solution for that (well, it is easy if you have four physical DVB-S cards): I have multirecord enabled for cards #1 and #2 (two recordings each) and multirecord disabled for cards #3 and #4 ending up with six "virtual cards". Cards #3 and #4 have EIT enabled (which should be sufficient to get the programm info when one of them is idle and may switch around), cards #1 and #2 have EIT _disabled_. 

I positively verified that such configuration works by switching to either "clone" of physical card 2 and being able to watch LiveTV for 10 minutes each without frozen surprises. ;)

---

