---
title: "Cannot authenticate with my routers bios from server"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by Mistah_Transistah on 2010-05-14
it's so annoying every time i want to make changes on my router bios for my server i have to go to my windows booted laptop rather than just 192.168.1.1 right here at my server... i only have to do a 360 in my chair and i am at my laptop but i don't want to... everytime i type the gateway ip it reads off the name of my router and looks fine. but i enter my authentication info and it just returns the login window blank... something ubuntu-side?

WRT160v2 linksys wireless N router (of course i have cat 5 running to my server)

[B][SIZE=2][SIZE=1]Ubuntu 10.04 LTS running desktop ontop (because i am still learning how to navigate the console)[/SIZE]
[/SIZE][/B]

---

### Post by BoneKracker on 2010-05-14
I had a similar experience once.

My piece of crap router would not accept a password longer than 10 characters from my Linux box, but would accept up to 12 from my Windows box.

This forced me to shorten my password so I could access if from anywhere.

This may be completely unrelated, but you might try an experiment with a short alphanumeric-only password (e.g. a1b2c3d4) and see if it makes a difference.

(Also, this probably goes without saying, but check to see if enabling cookies and javascript makes any difference, since they might be required.)

---

### Post by Mistah_Transistah on 2010-05-14
> **BoneKracker said:**
> I had a similar experience once.

My piece of crap router would not accept a password longer than 10 characters from my Linux box, but would accept up to 12 from my Windows box.

This forced me to shorten my password so I could access if from anywhere.

This may be completely unrelated, but you might try an experiment with a short alphanumeric-only password (e.g. a1b2c3d4) and see if it makes a difference.

(Also, this probably goes without saying, but check to see if enabling cookies and javascript makes any difference, since they might be required.)
well before i even read this reply i changed my pw and now it works. i am not sure what went wrong. but thank you anyway! =] [SOLVED]

---

### Post by BoneKracker on 2010-05-14
> **Mistah_Transistah said:**
> well before i even read this reply i changed my pw and now it works. i am not sure what went wrong. but thank you anyway! =] [SOLVED]

Sounds like the same password-type issue.

Next time go with [Netgear]("http://www.netgear.com/Products/RoutersandGateways/WirelessNRoutersandGateways/WNR3500L.aspx").

:P

---

