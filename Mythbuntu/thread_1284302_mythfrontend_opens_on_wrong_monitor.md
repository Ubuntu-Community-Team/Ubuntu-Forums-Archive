---
title: "mythfrontend opens on wrong monitor"
date: 2009-10-06
forum: Mythbuntu
---

### Post by scottac on 2009-10-06
alright so I have been running mythbuntu in a dual screen in twinview now for around 5 or 6 months with no real issues. yesterday I ran 

```
sudo nvidia-settings
```

and disabled my 32" HD LCD. I then saved this new configuration to my xorg.conf.

Well I only wanted to go down to the one monitor temporarily so I later changed it back, and again saved the new settings to my xorg.conf.

Well as expected the 32" HD LCD was recognized and everything works fine.

The only problem is that now when mythfrontend loads on startup it no longer opens on the 32" like it did before.  Now it opens up on my 22" monitor. 

Is there a setting somewhere that I can change to force mythfrontend to open on the 32"

Thanks for the help guys...

---

### Post by scottac on 2009-10-06
alright. well I actually just figured out what the problem was. 

I enabled desktop effects the other day and I guess that is why it was messing up.

---

