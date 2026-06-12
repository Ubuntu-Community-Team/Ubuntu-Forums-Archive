---
title: "Mplayer howto turn off subs by default?"
date: 2010-03-02
forum: Multimedia Software
---

### Post by Ferrat on 2010-03-02
Something has happened to my mplayer settings, for some reason it has started showing subtitles by default when for ex. playing a MKV file, it didn't do this before, is there any way to undo this?? 

I've tried removing $HOME/.mplayer 
I've tried purging mplayer
I've tried removing /etc/mplayer
I've tried adding -noautosub
I've tried checking and unchecking the mplayer options about subs
I've tried using V and J to disable them but later they return anyway after I restart mplayer

Nothing, it still shows subtitles by default and I'm at my wits end here, the only thing I can think of is that the change happened when I updated from 9.04 to 9.10 and that mplayer is compiled with this setting active?
Is this the case? I have no problems re-building a new mplayer from sources, planing on doing that anyway but if so, what is the option to make sure subs are disabled by default??

---

### Post by andrew.46 on 2010-03-02
Hi Ferrat,

> **Ferrat said:**
> 
I've tried adding -noautosub


Sounds a little odd, try *-nosub* instead...

Andrew

---

