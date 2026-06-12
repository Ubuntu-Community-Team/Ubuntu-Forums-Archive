---
title: "Antec RM200 problems"
date: 2008-11-21
forum: Mythbuntu
---

### Post by fatmonk on 2008-11-21
This is the remote I have:

[IMG]http://www.antec.com/images/400/RM200_400.jpg[/IMG]

I have an Antec Fusion black case and have set up the LCD and the built in IR receiver as per these instructions:

[http://ubuntuforums.org/showthread.php?t=779674]("http://ubuntuforums.org/showthread.php?t=779674")

When I use mode2 I can see codes for all numbers, up, down, left and right movement of the direction pad, and all of the buttons directly around the direction pad.

If I press any other button on the control mode2 stops responding to all button presses until I do an lirc restart.

The same happens with irw.

If I run irrecord I can programme codes fo rthe same buttons, but when it comes to any of the others irrecord times out waiting for input.

I also have a remote that came with my Hauppage WinTV Nove-T 500 and that doesn't produce any response from mode2, irw or irrecord. I don't really want to use this one anyway, so thats no problem. But I also don;t want to use the wired plug in IR receiver that came with that card (the point of spending more on the Antec case with the internal receiver was that I wouldn't have an external IR receiver!)

All the above is using /dev/lirc0

ls /dev/lirc* reveals the following:

```
/dev/lirc0
/dev/lirc2
/dev/lircd
/dev/lircd1
```

I'm at a loss as to what to try next to be honest.

Please, someone, give me some clues here. Does anyone have that remote working under Mythbuntu / Ubuntu?

Antec's page that describes the remote is [here]("http://www.antec.com/uk/productDetails.php?ProdID=75223#"), but that doesn't look like the exact same model of receiver/LCD I have, the LCD screen is different.

-FM

---

