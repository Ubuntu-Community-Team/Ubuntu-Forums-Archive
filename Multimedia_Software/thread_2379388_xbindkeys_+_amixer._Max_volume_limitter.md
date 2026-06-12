---
title: "xbindkeys + amixer. Max volume limitter"
date: 2017-12-05
forum: Multimedia Software
---

### Post by alex-two on 2017-12-05
Hey, I'm new to Linux and i've just set up my Logitech Performance Mx mouse to increase and decrease. 
I've read that you can harm your sound card by going too high over the max using amixer, is this true?
How could I prevent it?

Also using the command **amixer -c 1 sset Master 50%** doesn't set the volume to 50% of the Master bar, why is that?
And how would I run a command that would set the volume to 50% of the Master volume?

[ATTACH=CONFIG]277739[/ATTACH]

How would I get the volume indicator to show? When I press Fn + Up to increase my volume, it shows my current volume. How do I do the same with my xbindkeys on my mouse?

Thanks in advance, Alex

---

### Post by Yellow Pasque on 2017-12-06
Have you tried -c 0 ? (programmers like to start counting at 0)

---

