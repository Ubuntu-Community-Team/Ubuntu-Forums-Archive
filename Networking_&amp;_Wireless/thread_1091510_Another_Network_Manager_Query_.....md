---
title: "Another Network Manager Query ...."
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by scoobymad555 on 2009-03-09
Running Hardy 8.04

System is a laptop with eth0 being fixed lan and eth1 being wireless. System is also connected "partially" to various networks (i.e. connected to infrastructure but not authenticating to domain) and is also about to be configured for vpn access to systems too.

Been having a couple of "issues" with network-manager ....

a) it doesn't always actually do what i expect it to in terms of enabling / disabling interfaces

b) it doesn't appear to cope too well with new encrypted wireless networks (although it's fine connecting to ones it knows)

c) it seems to absolutely guzzle cpu resources for some reason - cpu load was consistently sitting at around 40%. killed of nm-applet and load dropped to around 10% with no changes in the applications running or what they're doing.

I'm still very much learning my way around linux command line and also how the whole system ties together so i'm not necessarily aware of all the options and consequences of things that seem like a good idea! ;) The "good idea" is to basically ditch network-manager completely instead of just killing it off from a terminal once the machine has fired up.

As far as i know (this is where i may be told otherwise) there are plenty of command line tools to do all the jobs that network manager does and the only thing i can see that i'd lose out on would be the link to the keyring manager for passwords to things like encrypted networks.

Are there any other impacts from totally removing or alternatively disabling (somehow) network manager that i should consider before pushing the big red button? :D

That and obviously i'll have to learn the commands to control / configure the interfaces .... google for the win! :D lol!

cheers

---

