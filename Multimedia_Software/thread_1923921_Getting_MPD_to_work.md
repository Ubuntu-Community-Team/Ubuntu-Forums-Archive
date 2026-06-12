---
title: "Getting MPD to work"
date: 2012-02-11
forum: Multimedia Software
---

### Post by griztown on 2012-02-11
Hi all,

I'm having trouble getting MPD to work. I first tried following the Ubuntu Community page for MPD. I then moved on to the MPD wiki. But neither has helped. I feel like I'm missing something basic.

First, under Daemon Options, what should I put for Bind to Address if I'm going to be accessing this remotely? The default is localhost but I thought I should put in the IP address of the MPD server. However, neither has worked though that could be something else.

Second, I'm running this on a Xubuntu server running 8.04 (kind of old). What audio output should I use? Pulse audio or Alsa or something different? Again, neither has seemed to work assuming I'm setting them up right.

Finally, I'm trying to get this to work by using Sonata as the front end. I can connect fine from another server if my bind to address is the ip address. I can see my library. But when I play the song, it appears briefly in the console then quickly disappears. Any thoughts?

Thanks!

---

### Post by cfhowlett on 2012-02-11
8.04 has already reached End Of Life.  I'd seriously suggest you update to 10.04...

---

### Post by griztown on 2012-02-11
> **cfhowlett said:**
> 8.04 has already reached End Of Life.  I'd seriously suggest you update to 10.04...

Fair enough, but do we think this is the source of the problem?

---

### Post by griztown on 2012-02-13
So upgrading did seem to work. Amazing! Thanks!

---

