---
title: "OSD Signal Strength?"
date: 2009-06-27
forum: Mythbuntu
---

### Post by SeanOB on 2009-06-27
Hi!

So a loooong time ago - with a much earlier release of mythtv I used an On Screen Display (OSD) signal strength meter to aim my antenna.  (It was a team effort, with me on the roof and the wife chanting 'better, better, worse, way worse' on the talkabout.)

Anyhow - I swore that the key to get the OSD up while watching liveTV was F7 (or ALT-F7) and neither of those seem to work.

Do I have the wrong key?
Is this feature gone now?
Is there some option somewhere to enable the feature?

Recent windy days require that I reaim the thing.  

Thanks!

SeanOB

---

### Post by SeanOB on 2009-07-23
So nobody knows?  Really?

One of my digital stations went from UHF to VHF in the transition and I need to do some antenna re-aiming.

-Sean

---

### Post by ian dobson on 2009-07-23
Hi,

According to the wiki it's still alt-F7 when in liveTV.

maybe you could use tzap to tune to the channel and watch the signal strength.

Regards
Ian Dobson

---

### Post by SeanOB on 2009-09-24
So I've got some antenna aiming and improvement plans for this coming weekend.  I'll be adding an element for one of my channels that moved from UHF to VHF on the 'digital changeover' date. And I'm going to add another mast piece to raise it up over the neighbor's roof.

In order to do this well I'll need some mechanism for measuring the signal strength.  ALT-F7 doesn't seem to be working for me.

So...

1) Does ALT-F7 work for you? (if it does then maybe I've botched some config file or something)
2) Is there some config stuff associated with ALT-F7? (it used to 'just work' but its been years since I last aimed the antenna)
3) Any other ideas / tools for getting the signal strengths? I need something that will auto update somewhat quickly - so that I can aim the antenna on the roof while the wife shouts (or radios) "better / worse."  And because she's the shouter and I'm the aimer - the tool needs to be somewhat straightforward.

Thanks!

SeanOB

---

### Post by williammanda on 2009-09-24
Here is the keybindings from the wiki and it does have ALT-F7 as the OSD but it didn't work for me either.

[http://www.mythtv.org/wiki/Keybindings]("http://www.mythtv.org/wiki/Keybindings")

One suggestion: increase the OSD time so that it is on longer and have your wife toggle between stations when it fades.

---

### Post by ian dobson on 2009-09-24
Hi,

Maybe you could use tzap or s/c zap to watch the signal quality.

See [http://www.linuxtv.org/wiki/index.php/Zap](http://www.linuxtv.org/wiki/index.php/Zap)

Regards
Ian Dobson

---

### Post by Caps18 on 2009-09-25
I did the antenna alignment thing 3 weekends ago.  I bought a big antenna and put it in my attic, but the signal strength was higher when I was touching it.  When I climbed down the ladder, the signal would go under 50%.  I also had to look at the signal of three different channels to get the best signal strength ratio between them all.

I went with the OSD number you get when you first change the channel to that station.  But I didn't always trust that number (it sometimes read 0% when the picture was fine).  You have to change it to a different station, not just a different channel on the same multiplex.

I would like to have a similar feature that DirectTV uses with the audible signal when the strength is high or low.  And they also have a good on screen display of the strength percentage.

---

