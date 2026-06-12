---
title: "Network connection to dsl-provider"
date: 2005-12-07
forum: Networking &amp; Wireless
---

### Post by Ruskie on 2005-12-07
I've read there's so many similar messages around, but couldn't find one that goes in the very same direction that my problem goes...
Everyone out there seems to be willing to have their dsl connection to get up at startup. Me having a non-flat billing scheme, I don't want to.
In any case, with Breezy, I run pppoeconf and set up the connection to my provider, and it works fine. After each reboot however it has to be repeated, cause a simple ```
sudo pon dsl-provider
``` does not work. I have always to repeat the pppoeconf setup to make it work.
Please help!!! How can I fix this nasty bug?

Looking through the messages, the most adherent to my situation is the one titled: "pppoe not connecting upon bootup", and my interfaces file is the one described by Felipe_U (excuse me but I don't know how to link threads), or the one titled "The RC is out, and since the pppoe issue has not solved..." for which I adopted the very same interface file that Asimon has.
I only stripped the line ```
auto dsl-provider
``` because I don't want the connection to start at boot, but for the rest the file is identical.
But it did not fix the problem. Any other ideas?

Thank you very much
Marco

---

