---
title: "Using All Surround Sound Speakers for Regular Sounds?"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by ataxicwolf on 2008-01-15
Hey guys,

So I'm trying to use all of my nice new logitech surround sound speakers for regular music and stuff (non surround) Basically, I want volume from all of the speakers rather than just the front two. How do I do this?

Thanks for the help,

Stephen

---

### Post by ataxicwolf on 2008-01-15
After doing some googling, I found a wiki telling me to make a .asoundrc file and enter the following into it:

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

After doing that, I tested my speakers, and the other ones stil don't work :(

---

### Post by ataxicwolf on 2008-01-16
Anyone care to help?

---

