---
title: "Audacity playback gives static cracking?"
date: 2016-03-04
forum: Multimedia Software
---

### Post by eezacque on 2016-03-04
I recorded a voice over which sounds okay through a variety of software.
However, audacity (2.1.2) on Ubuntu 15.04 gives me an awful crackling, clicking, popping, like it is playing antique vinyl.

Any clue?

---

### Post by Bucky Ball on 2016-03-04
Just a note: 15.04 is no longer supported. Advise you upgrade to a supported release, 15.10, and see if problem persists. I think you need to change the upgrade repos manually as the 15.04 ones would have been moved unless you do a clean install of 14.04 LTS or 15.10, both upgradeable to 16.04 LTS later in the year.

Sorry couldn't help with Audacity, but have bumped the thread. :)

* Hold on. You're running 2.1.2 on an EOL release? Might have something to do with it, though I don't know what. I am using 15.10 and it is 2.0.6. You have manually installed an Audacity repository to get the latest version? That is about all that would be updating at this point and the rest of your system, including security, is out of date.

---

### Post by eezacque on 2016-03-04
> **Bucky Ball said:**
> Just a note: 15.04 is no longer supported. Advise you upgrade to a supported release, 15.10, and see if problem persists. I think you need to change the upgrade repos manually as the 15.04 ones would have been moved unless you do a clean install of 14.04 LTS or 15.10, both upgradeable to 16.04 LTS later in the year.

Sorry couldn't help with Audacity, but have bumped the thread. :)

* Hold on. You're running 2.1.2 on an EOL release? Might have something to do with it, though I don't know what. I am using 15.10 and it is 2.0.6. You have manually installed an Audacity repository to get the latest version? That is about all that would be updating at this point and the rest of your system, including security, is out of date.

I know 15.04 is EOL, but previous Ubuntu upgrades were a royal pain in the ass with respect to hardware support, and in the middle of a project I have no time to waste on restoring my scanner, virtual machine, audio, whatever back to working order.

My Audacity 2.1.2 comes from Ubuntu Software Center, I have yet to see an indication that it is not compatible with 15.04.

---

### Post by Bucky Ball on 2016-03-04
All good. Just asking and just curious as to what's happeng at my end as I'm running a newer release than you and seem to have an older version of Audacity. [See here]("https://sourceforge.net/projects/audacity/files/audacity/"). :-k

I'm running a month old install of 15.10.

Anyway, back to your problem ... ;)

---

### Post by eezacque on 2016-03-05
Problem solved by switching output from pulseaudio to HDA Intel PCH: ALC1150. Looks like audacity has issues with pulse audio.

---

### Post by Bucky Ball on 2016-03-05
Play some stuff in Audacity with it routed through HDA Intel PCH: ALC1150, open PAVC and see if the Playback tab shows the stream and activity. Audacity appears to need to be manually routed through a device which is then, I would presume, routed through Pulse and out. 

Could be wrong. Check it out. Also, please mark thread as solved. See first link in my signature for how. This does not close it to further discussion.

---

### Post by eezacque on 2016-03-06
> **Bucky Ball said:**
> Play some stuff in Audacity with it routed through HDA Intel PCH: ALC1150, open PAVC and see if the Playback tab shows the stream and activity. Audacity appears to need to be manually routed through a device which is then, I would presume, routed through Pulse and out. 

Nope. When playing through HDA Intel PCH: ALC1150, according to PAVC, pulse audio is not involved.

> Could be wrong. Check it out. Also, please mark thread as solved. See first link in my signature for how. This does not close it to further discussion.

Audacity doesn't seem to work well with pulse audio. There is, fortunately, a workaround which doesn't involve pulse audio, which does not mean, however, that the issue is solved.

---

### Post by Bucky Ball on 2016-03-06
To your original question: Audacity playback gives static crackling. Do you still have crackling? No? Then solved. Your original question had nothing to do with Pulse. I brought that up.

Marking as solved will not close the thread to further discussion. If you want to delve into why or if Pulse and Audacity work together, perhaps post a new thread because that question has nothing to do with the reason you started this one or its thread title.

You have discovered a workaround that will benefit others. Unsure why you don't want to share that by marking as solved and moving on. If you want to ask another support question, post a new thread. 

Good luck.

---

