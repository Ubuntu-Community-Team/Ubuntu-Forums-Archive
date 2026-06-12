---
title: "Flash dies in firefox"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by pytheas22 on 2008-02-17
For several weeks, I've had a problem where flash videos or applications on certain sites will start to play, but then die and are replaced with a light-gray box in Firefox 2.  Firefox itself remains completely stable, but the only way to get flash to work again--on any site, not just the ones that cause problems--is to kill firefox (simply closing and restarting doesn't work) and launch it again.

I have noticed that this happens consistently when I try to view videos that include transparent advertisements at the bottom of the screen: a few seconds into the video, when the advertisement gets launched, flash disappears.  The problem also seems to occur under other conditions, but I haven't pinned anything down yet.

I am using Adobe's proprietary flash plugin on a 64-bit system.

This problem has become so frustrating that I've started using my wine installation of Firefox to view flash content, where it works fine.  Any help in figuring out why flash is doing strange things in my native browser would be very much appreciated.  I've done some research and have found plenty of documentation of instances where flash causes Firefox to crash or freeze the machine, but I can't find anyone with problems like mine, which is less extreme but still obnoxious.

Thanks in advance.

---

### Post by gandaran on 2008-02-17
> **pytheas22 said:**
> For several weeks, I've had a problem where flash videos or applications on certain sites will start to play, but then die and are replaced with a light-gray box in Firefox 2.  Firefox itself remains completely stable, but the only way to get flash to work again--on any site, not just the ones that cause problems--is to kill firefox (simply closing and restarting doesn't work) and launch it again.

I have noticed that this happens consistently when I try to view videos that include transparent advertisements at the bottom of the screen: a few seconds into the video, when the advertisement gets launched, flash disappears.  The problem also seems to occur under other conditions, but I haven't pinned anything down yet.

I am using Adobe's proprietary flash plugin on a 64-bit system.

This problem has become so frustrating that I've started using my wine installation of Firefox to view flash content, where it works fine.  Any help in figuring out why flash is doing strange things in my native browser would be very much appreciated.  I've done some research and have found plenty of documentation of instances where flash causes Firefox to crash or freeze the machine, but I can't find anyone with problems like mine, which is less extreme but still obnoxious.

Thanks in advance.

adobe's proprietary flash plugin is a 32-bit package, it won't work on a 64-bit system, so you will have to stick to the flashplugin-nonfree available on synaptic, this package is specially packaged for 64-bit, but I suppose it's still broken (not sure ), not possible to install at the moment, but you can still try, must have the updates repository's enabled and uninstall other flash first.
now how did you install the flash you are using and where (which folder)?

it is possible to make that 32-bit work but will take a bit of tricky work,
is has to be installed in the right folder along a nspluginwrapper I believe.

---

### Post by pytheas22 on 2008-02-17
Thanks for your response.  I know that I did have to go through some work to get the plugin installed; I followed a how-to somewhere which I can't find now.

The thing is, the plugin works fine usually; it's just when trying to view certain videos that it crashes.  Youtube videos are fine, for instance, but I was using a flash application to listen to music on some website the other day, and after about ten seconds it died on me.  Maybe it's just a bug with the flash player that no one will be able to fix, thanks to its being proprietary.  But if there is something that I could do to make it work, it would be great.  I've used Linux everyday for more than a year and it's only recently that I've started having these problems, so I'm thinking that there's a solution somewhere.

Or even better, maybe soon gnash will get it together and become stable enough to use as an alternative to the nonfree plugin...

---

### Post by arjanito on 2008-04-01
Hi there,2 flashapplications don't work together.Get completely rid of Gnash and flashplayers through synaptic ,then reinstall flashplayer.Worked fine for me.

---

### Post by pytheas22 on 2008-04-01
I should have reported this earlier, but actually flash has now been working fine using Adobe's plugin.  Even videos with advertisements work.  There might have been an update to it, or it could be thanks to a Firefox update.  In related news, I read on gnash's website that the first stable release of that plugin came out a few weeks ago.  I tried to compile it and gave up, but it should be in Hardy, which will be nice if it actually does work as well as the closed-source plugin.

---

