---
title: "Blackscreen after &quot;Waiting for network configuration.&quot;"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by LaugeGregers on 2012-12-04
Hello. 
My internet recently went wrong, so I tried to fix it various ways. At a point I decided to restart my computer. When Ubuntu was booting I got thee "Waiting for network configurations" and "Waiting up to 60 more seconds for network configuration."
It then tries to boot, but when it boots I just get a black screen.

Before trying to fix my internet, it acted like this:
I would not get any internet at all.
If I disabled networking and enabled it again, it would be active for about one minute.
It would then go back to no internet.

To fix it I tried to do these things:
I tried to set up a static IP.
I tried to delete the internet configuration, it made a new configuration called "Auto eth0".
I also tried to follow some guides, from people with the same problem.

I run Ubuntu 12.10.

I hope some of you guys out there can help me.

---

### Post by don1000 on 2012-12-05
My PC is connected by Ethernet while my wife connects via wifi (ipad). When we were both on-line I saw a gradual deterioration in my on-line activities, seemingly wifi was hogging the bandwidth. Until it got so bad that I started to get the oft complained of delays and the attendant 'waiting for network configuration' message, eventually ended up by not being able to get  on-line  at  all while  there was any wifi activity.

Tried all the software fixes I'd seen but none worked for me. Was about to give up Ubuntu altogether when the penny dropped, the fault was literally a bad hardware connection. Installed a new Ethernet cable with instant and dramatic improvement, where the fail-safe script is never invoked, boot up is  now faster than ever and the two connections now happily co-exist without any problems.

---

### Post by don1000 on 2012-12-05
> **LaugeGregers said:**
> Hello. 
My internet recently went wrong, so I tried to fix it various ways. At a point I decided to restart my computer. When Ubuntu was booting I got thee "Waiting for network configurations" and "Waiting up to 60 more seconds for network configuration."
It then tries to boot, but when it boots I just get a black screen.

Before trying to fix my internet, it acted like this:
I would not get any internet at all.
If I disabled networking and enabled it again, it would be active for about one minute.
It would then go back to no internet.

To fix it I tried to do these things:
I tried to set up a static IP.
I tried to delete the internet configuration, it made a new configuration called "Auto eth0".

I also tried to follow some guides, from people with the same problem.

I run Ubuntu 12.10.

I hope some of you guys out there can help me.


Going from my own experience you will get the same message if you  disconnect the Ehernet cable,which no amount of software tweaking would  correct. So my inclination in the future would be to check hardware  before driving myself up the wall again looking for a script/software  fix.

As a quick check I suggest that you try 'sudo eth0 | grep  "Link detected', where you will get a Yes or No answer.  Or 'ifconfig  eth0|sed -n '/running/I p'. sys/class/Net/eth0' is also usefull.

Come  to think about it I can't understand why a broken link isn't checked  for and reported to the user before any atttempt is made to configure  the network. In  fact without it the "waiting for network configuration"  message  is not all helpful.

---

### Post by don1000 on 2012-12-06
Re my previous it should have been 'sudo ethtool eth0 | grep "Link detected"'. 

Put the error down to approaching sinelity

---

