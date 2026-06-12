---
title: "Weird sound issue"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by MStublefield on 2007-09-02
Yesterday afternoon, my sound stopped working. I later discovered it was because my speakers had died, but not before spending quite some time screwing with my soundcard and drivers (I have an Audigy 4, BTW, but Linux recognizes it as an Audigy 2).

There is also onboard sound through the Nvidia motherboard.

Now, when I boot up, I get the quick drum-taps that indicate that Ubuntu is ready for me to log in. Once I log in, no sound through the Audigy. Upon loading my profile, it switches to the Nvidia for some reason, so I can switch the plug and it works... just not as well, because Creative Labs > Nvidia.

Has anyone ever heard of this? I'm going to try just reinstalling and starting over again, but to have it switch sound cards based on profile... 

Oh, also, Volume Control claims I'm using the Audigy. Alsamixer defaults to the Nvidia. I've tried "gksudo asoundconf set-default-card Audigy2" which supposedly works, but no dice.

---

### Post by MStublefield on 2007-09-02
*bump*

Anybody?

---

### Post by MStublefield on 2007-09-04
Am I not being clear enough? Do I need to post more information?

Over 60 views and no responses... just an obscure bug nobody knows anything about?

---

