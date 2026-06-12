---
title: "Frustrating, curious issue with wifi card..."
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by betterliving on 2006-07-14
Hello everyone, relatively new to Ubuntu/Linux and completely fresh to the forums; my issue is with the (apparently notorious) Belkin F5D7011 Wireless G card, one which I had previously thought resolved...

When I initially plugged the card the card in, I was able to solve the non-recognition issue with Linuxant's free trial (as a short term fix) after having no luck with ndiswrapper, and all was well until I removed the card when trying to slide the notebook (a Dell Latitude C840) into a rather svelte case... When I plugged the card back in, I found that I was back to square one. I attempted the same steps as before, but had no luck. After running"lspci" I found, to my great surprise, that I was reading it as an *entirely different chipset*! So, I tried to download the driver for this *new* chipset, unzipped/linuxanted it... and nothing happened. So, I'm pretty stumped here, and ready to just buy a new card that'll work out of the box, putting this one up on ebay, though I'd really like to learn how to resolve these issues! If anyone's got any advice, I'd be infinitely greatful. Thanks, in any case.

In summary: Had Belkin F5D7011 card running with Linuxant (though I'd prefer to get ndiswrapper working here), removed/replaced card, stopped working, ran "lspci", found that the chipset had *changed* from the (what I assume to be real chipset) Broadcom 94306 to the *new* BCM4306, which corresponds to a totally different series of cards.

Any help would be fantastic, again, thanks!

---

### Post by Seventh on 2006-07-15
I'm far from experienced, but since nobody helped you here it goes:

if lspci returns the wrong information, probably the wrong modules have loaded with hardware detection. You can see the list of loaded modules with "lsmod". If you see something that resembles to "BCM4306" like bcm43xx then maybe the module should be blacklisted.

If you search in these forums you will find more information on how to blacklist modules...

---

### Post by stupidkid on 2006-07-15
Add a module to /etc/modules.d/blacklist (I'm not sure if that's the correct file name, but it should be close).

---

### Post by betterliving on 2006-08-17
Although the problem continues despite blacklisting, my thanks to those who've given it a shot.

---

