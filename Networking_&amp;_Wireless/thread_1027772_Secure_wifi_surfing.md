---
title: "Secure wifi surfing?"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by blakjesus on 2009-01-01
Is there a way i can surf the internet and check email safely on an open network without having a server at home that i can use to tunnel my traffic? I checked out stuff like vpn and ssh but they require that i have my own server setup.

I don't have one and i don't think i would be able to buy a new computer any time soon, but i would still like to have secure wifi traffic. I already have tor/privoxy but i didn't find anywhere that stated that it helped with keeping traffic secure over open wifi.

---

### Post by hambone79 on 2009-01-01
That is really the only way you can do it...you have to create an encrypted tunnel from your computer to a secure computer beyond the open network.

Have you considered asking a friend with a Linux computer to give you an account on their machine? All you need is ssh access to their computer and you can encrypt all of your traffic.

I should also point out that if you want to make a server at home it really wouldn't need to be that fast. A Pentium 3 machine is more than fast enough to handle the task of acting as a ssh proxy.

---

