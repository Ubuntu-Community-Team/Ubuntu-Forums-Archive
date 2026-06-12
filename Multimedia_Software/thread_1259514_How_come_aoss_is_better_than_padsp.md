---
title: "How come aoss is better than padsp?"
date: 2009-09-06
forum: Multimedia Software
---

### Post by CatKiller on 2009-09-06
I'm using Pulse Audio, and I was just running Starcraft. The sound through ALSA is pretty bad, so I thought I'd have a bit of a fiddle.

Just configuring Wine to use OSS didn't work (no sound at all), which isn't that surprising, since PA had control of the soundcard. I used what I thought might be a sensible plan; using padsp to route the OSS through PA. That is what it's for, after all. The sound worked fine for about 10 seconds, and then stopped. No more sounds from that game. So I tried the other way I know of to route OSS audio; aoss. This worked brilliantly; know stuttering, no cutting off sounds part way through - all the things you're familiar with from running Starcraft through Wine.

For some reason, out of 


[LIST]
[*]ALSA &#8594; Pulse Audio &#8594; ALSA
[*]OSS &#8594; Pulse Audio &#8594; ALSA
[*]OSS &#8594; ALSA &#8594; Pulse Audio &#8594; ALSA
[/LIST]
it's the third one that's far and away the best option. Which is crazy. Does anyone have any insight into why this might be, other than, "it's just the way Linux audio is; black magic?"

Is there any purpose to filing a bug report against padsp saying, essentially, "your software is crap?" I'd like the software to improve as much as the next guy, and this is clearly not behaving the way it should, but I don't really have anything constructive to say on the matter.

Maybe the Wine devs will pull their fingers out and write in some Pulse Audio output support, and then it will all be moot anyway.

---

### Post by donato roque on 2009-09-06
Hello.  This is not an apology as I'm not a dev, but I symphatize with you.  Linux sound is really bad.  I don't know why they can't agree on sounds in Linux.

---

