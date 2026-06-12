---
title: "One sound card for multiple, simultaneous uses."
date: 2010-11-05
forum: Multimedia Software
---

### Post by Dwebtron on 2010-11-05
I work for a company that uses Ubuntu exclusively. Without going too much into detail, we need a single sound-card to do up to 3 things at one time. What I mean by this, basically, is that there needs to be 3 instances listening to a card's line-in port at any one time. For example (these are made-up), Audacity listening to the line-in jack and making a recording of what it hears, a custom script that streams the input to the internet, and a third instance that listens to this input and runs different scripts based on what it hears.

Currently, our company sends out machines with 3 sound cards to do this. One card for each job. Of course, we'd like to save money and only send out one. Whenever we try to set all 3 programs to run off of one card, they error out and say something along the lines of "device already in use". Is there a way to go around this? If so, how? 

We use the command-line version of Ubuntu 8.04. It is NOT x64. The hardware may vary a bit, but is for the most part, consistent. (We order in batches of 50.) Please let me know if you need a bit more information as well, I know this might be a bit vague.

*Edit, I'm new here, so sorry if this thread is in the wrong area.

---

### Post by cchhrriiss121212 on 2010-11-05
What kind of card would you prefer? PCI, USB or firewire?
What kind of inputs would you prefer? SP/DIF, 1/4" jack, 1/8" jack?
What is your budget?

---

### Post by Dwebtron on 2010-11-07
> **cchhrriiss121212 said:**
> What kind of card would you prefer? PCI, USB or firewire?
What kind of inputs would you prefer? SP/DIF, 1/4" jack, 1/8" jack?
What is your budget?

I'm sorry if I made it seem like we NEED the sound card... We already have all of the hardware. If I remember correctly, we've got a few hundred of these: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1111756&Sku=M501-1042](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1111756&Sku=M501-1042)

We've been putting two of those into our machines, in addition to the onboard sound card. Ultimately, I'm asking for a way to use the onboard sound card (or just 1 of these, to half the cost of them for us) to do multiple jobs. Is this possible somehow?

---

### Post by cchhrriiss121212 on 2010-11-08
I know that jackd can route audio to multiple sources, but I'm not used to using it with CLI only. Usually jack only works with jack friendly apps, but it is possible to get everything working by routing ALSA through jack, see here:
[http://ubuntuforums.org/showpost.php?p=9344940&postcount=6](http://ubuntuforums.org/showpost.php?p=9344940&postcount=6)
[http://alsa.opensrc.org/index.php/Jack_%28plugin%29]("http://alsa.opensrc.org/index.php/Jack_%28plugin%29")

You would only need one card, but I'm not sure what kind of latency you would get (if that matters to you?).

---

### Post by P4man on 2010-11-08
You need an audioserver like jack or pulseaudio, and your apps need to address that sound server, not alsa directly.  AFAIK ubuntu 8.04 already came with pulseaudio installed by default.

---

### Post by Dwebtron on 2010-11-08
> **cchhrriiss121212 said:**
> I know that jackd can route audio to  multiple sources, but I'm not used to using it with CLI only. Usually  jack only works with jack friendly apps, but it is possible to get  everything working by routing ALSA through jack, see here:
[http://ubuntuforums.org/showpost.php?p=9344940&postcount=6](http://ubuntuforums.org/showpost.php?p=9344940&postcount=6)
[http://alsa.opensrc.org/index.php/Jack_%28plugin%29](http://alsa.opensrc.org/index.php/Jack_%28plugin%29)

You would only need one card, but I'm not sure what kind of latency you would get (if that matters to you?).


This sounds like something that we could do, however, there needs to be as little latency as possible. If there would be a drastic latency tax (probably close to a half second delay is our limit) we're better off without it.


> **P4man said:**
> You need an audioserver like jack or pulseaudio, and your apps need to address that sound server, not alsa directly.  AFAIK ubuntu 8.04 already came with pulseaudio installed by default.

I'll look into this, thanks. Could you recommend a guide to configure this? If not I'll google around.



Thanks for your responses, guys, I really appreciate it.

---

### Post by P4man on 2010-11-08
Perhaps you should read up a bit in general about jack and pulse and decide which is likely the best way to go. From what I read, Im inclined to say jack. Pulse will likely be a little easier. Anyway some reading that may interest you:

[http://0pointer.de/blog/projects/when-pa-and-when-not.html](http://0pointer.de/blog/projects/when-pa-and-when-not.html)
[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

---

### Post by cchhrriiss121212 on 2010-11-08
I'd agree with p4man and say that jack is preferable to pulse. Pulse will have fairly poor latency compared with jack which can run with sub 10ms even with onboard soundcards.

---

### Post by Dwebtron on 2010-11-19
I've been looking around for guide and how-to's for jack, but everythign I'm finding seems to require a gui. I'm running the 8.04 terminal-only version. I can't find any guides that will help me set it up using only terminal. Would you guys happen to know of one?


Thanks for all your help so far, by the way. :D

---

