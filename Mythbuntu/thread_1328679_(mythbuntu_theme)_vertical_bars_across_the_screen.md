---
title: "(mythbuntu theme) vertical bars across the screen"
date: 2009-11-16
forum: Mythbuntu
---

### Post by aYs-Halo on 2009-11-16
Hello all,
I'm not sure whether this is mythbuntu related, but I didn't know where else to put it.

The problem is that i have vertical lines across the screen with the mythbuntu theme, starting when mythbuntu boots (see attachments). The strange thing is: the other themes (in mythtv) are working fine. And I can also watch tv and videos.


Any help is, of course, highly appreciated;) thanks

---

### Post by SiHa on 2009-11-17
I think it's just where the shaded 'hatching' is being scaled to the ouput resoution. I get it on the desktop when the box boots, but it goes when the frontend starts. Maybe playing with the resolution or GUI size might do away with it?

---

### Post by aYs-Halo on 2009-11-17
Oh yes, I forgot to mention: doing a 1024x768 resolution on my other monitor makes it look better (not sure whether it looks perfect like it should, I'll test that later when I get home).

The thing is: I don't want any other resolution but that one (it's 1360x768) on my Television... ;/

What exactly do you mean with "playing with the GUI size"?


best regards~

---

### Post by SiHa on 2009-11-17
I shouldn't worry too much about trying to match the native resolution of your TV, (which I assume is 1360 x 768) as your TV will almost certainly scale it anyway and give you some overscan (the edges are clipped).

> What exactly do you mean with "playing with the GUI size"?

You can change the size of the MythtTV Window (GUI). This is mainly to get around the above overscan problem. It allows you shrink the amount of the screen that Myth uses to within the visible portion of your TV screen. It' sin the setup -> appearances menu, you can use either the screen setup wizard, or change the GUI size manually.

I think you'll find that the only way to get rid of, or minimize these lines is by changing the resolution. The problem you are seeing is because there is an inexact match between the resolution your PC is outputting (and after the TV has scaled it) and the physical pixels on the screen. Where you have a regular pattern of light and dark lines at an angle(like the hatching on the background), you will end up with a regular pattern of 'interference' such as you are seeing.

It's hard to describe, but Google 'Moiré Pattern' for a better description than I can give, with pictures to illustrate.
[http://en.wikipedia.org/wiki/Moir%C3%A9_pattern](http://en.wikipedia.org/wiki/Moir%C3%A9_pattern) for example

---

### Post by aYs-Halo on 2009-11-17
Although that doesnt actually "solve" the problem like I hoped, this actually sounds like a realistic explanation. 
Thanks a lot for the info!

---

### Post by SiHa on 2009-11-17
Guess you figured out the wizard is pants... I ended up manually setting the GUI size in the appearance menu. Sorry, should've mentioned that.

---

