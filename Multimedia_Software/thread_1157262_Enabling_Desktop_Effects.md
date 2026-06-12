---
title: "Enabling Desktop Effects"
date: 2009-05-12
forum: Multimedia Software
---

### Post by vka2b on 2009-05-12
Hi,

I am a new Ubuntu user.  I have hit a few snags hear and there, but for the most part I love it.  One thing has happened recently though that I just haven't been able to figure out.  My display was really choppy (e.g. when scrolling in a browser).  I thought it was a memory issue, so I upgraded my RAM, and it got no better.  Finally, I found out that this was likely due to my driver settings.  After doing some research, I came upon this page that had a suggested xorg configuration for my very graphics card:

[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)

However, even though after following these steps the choppiness went away, I could no longer enable Desktop Effects (I would get an error saying that this option could not be enabled).  So, I did some more poking around, and found this suggestion, this time not only for my exact card, but even for my exact laptop (IBM T30):

[http://www.thinkwiki.org/wiki/Talk:ATI_Mobility_Radeon_7500#Alternate_xorg.conf](http://www.thinkwiki.org/wiki/Talk:ATI_Mobility_Radeon_7500#Alternate_xorg.conf)

After implementing this configuration, the choppiness was fixed, and I could finally enable Desktop Effects.  However, upon enabling the effects, all of my close and minimize/maximize buttons went away, and certain windows that I would open up would just be blank (e.g. when I would try to open up a new terminal window, only a big white box with nothing in it would pop up).  I can solve this problem by changing the Depth from 16 to 24, but then the choppiness comes back!

I am so close, but I am just at a complete loss as to what all this means and therefore have no idea what do to.  If somebody could please either:

1.)  Tell me how to enable Desktop Effects in the first configuration above.

2.)  Tell me how to get rid of the white-box issue in the second configuration above

3.)  Suggest/explain any other sort of solution for having a non-choppy display but still be able to enable desktop effects.

That might be a tall order, for which I apologize, but I just don't know what to do.  I could definitely live without the Desktop Effects and just be happy with the lack of choppiness, but now that I've gotten a taste for the effects, I don't want to give up.  Any help would be greatly appreciated.  Thank you so much!

---

