---
title: "wineasio/JACK - How to assign more inputs than sound card actually has?"
date: 2011-02-10
forum: Multimedia Software
---

### Post by indstr on 2011-02-10
Hi. I am running Ubuntu Studio 9.10 and have been using wineasio to connect Reaper to JACK successfully for a while now. However, I am now experimenting with using multiple soundcards in JACK (via alsa_in). My main card is an M-audio delta 44 (4 inputs) and I want to route the inputs from my onboard soundcard into Reaper using JACK. No problem so far.. This all works with alsa_in. But the problem is I can't get reaper to start with more than 4 in/out. 

With wineasio, there is an environment variable "ASIO_INPUTS=" and "ASIO_OUTPUTS=" which allows you to set the number of in/out... Which I already used to bump it up to 4 when the default was 2. But when I try to set the inputs to 8, for example, Reaper still only recognizes that there are 4 inputs in its configuration. 

The problem here is I need more than 4 separate input tracks going into Reaper simultaneously. It would also be nice to just have some "virtual" in/out ports to route things around in more ways. 

Another option I have considered is the "Rearoute" drivers in Reaper, however I'm not sure if that will play well with JACK. I'll have to test it tonight and see. I guess if it doesn't connect to JACK, it may be theoretically possible to run JACK simultaneously with the Rearoute driver with Reaper, and then actually use alsa_in on the same card to bridge it to JACK (in addition to using alsa_in for the onboard soundcard inputs as well)... But if this even works, I'm not sure if the latency will be worse ... 

Does anybody have any insights on this? Am I doing something wrong or  overlooking something? Is this just a limitation of wine or wineasio  that it cannot assign more inputs than the primary sound card physically has? Would "virtual ports" help me at all in this endeavor?

Any help is appreciated.

---

### Post by indstr on 2011-02-10
Wow.... 

Easy fix...

Same problem this guy was having:

[http://webcache.googleusercontent.com/search?q=cache:4yeZoSsk_9AJ:ubuntuforums.org/showthread.php%3Ft%3D1163106+export+asio_inputs%3D&cd=1&hl=en&ct=clnk&gl=us&source=www.google.com](http://webcache.googleusercontent.com/search?q=cache:4yeZoSsk_9AJ:ubuntuforums.org/showthread.php%3Ft%3D1163106+export+asio_inputs%3D&cd=1&hl=en&ct=clnk&gl=us&source=www.google.com)


I must have forgotten about the .wineasiocfg

To fix the problem, I simply did this:

```
sudo gedit $HOME/.wineasiocfg
```

Inside it were two lines:

```
ASIO_INPUTS=4
ASIO_OUTPUTS=4
```

Which I simply changed to 8, and now they show up in Reaper.

Awesome   :)

---

