---
title: "SYNC_TO_VBLANK validation"
date: 2008-04-05
forum: Mythbuntu
---

### Post by sikk on 2008-04-05
Hello,

I am using Mythbuntu 7.10.

While reading through detail on how to better optimize my display output for sport to my 50" plasma (1280x720p@50Hz via DVI native resolution) for my AGP based Nvidia 6600 I came across a mention of the use of;

```
export __GL_SYNC_TO_VBLANK="1"
```

Using glxgears from xterm before running th eexport results in very high frame rates. 
After running [COLOR="Red"]export __GL_SYNC_TO_VBLANK="1"[/COLOR] I see 50Hz frame rates, exactly as expected.

How can I ensure that mythfrontend is executing with the correct sync to vblank settings export?
I can easily do this if I know where mythfrontend is executing from on boot. 

Where does mythfrontend execute from on boot?

---

