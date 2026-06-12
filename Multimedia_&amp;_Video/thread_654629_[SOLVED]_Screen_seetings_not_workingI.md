---
title: "[SOLVED] Screen seetings not workingI"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by MartijnNL on 2007-12-31
Hello,

I installed Xubuntu 7.10 last week. It automatically setup my videocard as a Matrox card (which is good) and  the screen was a plug and play at 1024x768 @ 85 Hz. This worked fine.

But when I was browsing through the miscellaneous settings windows today I found the Screens and Graphics Settings, which stated the info above, and I decided to see if my own monitor was listed. It was, so I selected it. I got a message stating all users should be logged out for changes to take effect. So I logged out.

And next the problems started. I got a screen (from X) saying my screen and video card couldn´t be detected and that I had to select them myself. I did so with the settings above, apart from the monitor, for which I used the CTX VL500 (my own type) as the plug and play didn´t have the right resolution anymore. But after that I only get a 800x600 resolution with a vesa card and plug & play monitor. I just won´t keep my settings.

I wish I hadn´t changed anything in the first place, but now I did, how do I get it to work properly without having to re-install the entire system?

Thanks for any help.

Martijn

---

### Post by MartijnNL on 2007-12-31
I thought earlier the problem was solved. But after another reboot, I got the low graphics mode again.

Sigh.

Anyone?

---

### Post by MartijnNL on 2008-01-02
Well I tried to rerun the autoconfiguration script as described in:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

That didn´t solve the problem, even more: after a restart by keyboard didn´t work properly anymore, so I had to reinstall after all. (I simply don´t now enough about command line stuff, to fix a thing like that without internet access to tell me how.)

But I just read the following on the same page I mentioned above:

> 
More importantly if your monitor is not detectable, the Identifier will be called Generic Monitor. In which case, don't change the Identifier to anything else otherwise X will fail to load and report that it can't find the a Monitor.

This is probably why I got the problem in the first place. Well, I learned something from all this.

So you can consider this problem solved.

Regards,

Martijn

---

