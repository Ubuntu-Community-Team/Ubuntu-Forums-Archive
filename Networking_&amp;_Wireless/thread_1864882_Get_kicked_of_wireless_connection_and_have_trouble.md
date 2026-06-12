---
title: "Get kicked of wireless connection and have trouble reconnecting since 11.10 upgrade"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by peperomia on 2011-10-19
Since I upgraded to 11.10, I am having trouble on networks with WPA/2 Enterprise security. It does not happen on unsecured networks.

This is what happens:

I get to work, open my laptop. Wireless connection to WPA/2 Enterprise secured network happens automatically, quickly, seamlessly. I don't even notice. Maybe half an hour, an hour later, I get a popup from the wireless asking for my password. Over and over and over. I disable and reneable my wireless from the wireless menu. If I'm lucky, after I re-enable wireless, it automatically connects (doesn't ask for my password). If I'm unlucky, it asks for my password. Over and over and over. Then I have to disable wireless in the menu, do ifdown/ifup, and then re-enable in the menu before it'll reconnect. 

[Side question: What exactly does disabling the wireless in the wireless menu do? And how's that different from ifdown?]

Sometimes I seem to stay connected for awhile, 15-30 minutes before webpages slowly stop loading, I get signed out of chat, and it starts asking me for my password. Other times it only lets me online on for a minute or two.

This started happening the day after I upgraded from 11.04 to 11.10. I'd never had a problem before. I also got fed up with Unity a day after upgrading to 11.10 and started using xfce, booting into an xubuntu session now. Problem happens the same whether I boot into normal Ubuntu with Unity or Xubuntu. It also occurred before I'd installed xfce.

Any idea what's going on? Or know what logs I should poke into to figure it out? It's really freaking annoying to get kicked off the wireless 2 or 3 or 30 times an hour and have to go thru such annoying steps to get it back.

---

