---
title: "wlan does not connect (ubuntu/network-manager bug?)"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by -glow- on 2010-01-28
hi there.

so far i testet 4 wlan cards (prism, ?zytel?, realtek and another realtek)
they all work without a problem with kubuntu.

but with ubuntu they dont want to build up a connection to my router...
it looks like the passphrase is wrong..he asks me after a short time to reenter the phrase. but the phrase isnt wrong(copy pasted) the phrase has some special characters but only '=' and a few '!'. so i doubt that that could be the problem 

im pretty sure there are more people out there who have the same problem.
I hope someone knows a solution :/


edit:
i did some searching and found this... seems to be a major problem
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/379219](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/379219)

---

### Post by Comtronix on 2010-01-28
Ubuntu Bummer!
 
Ubuntu won't connect to Linksys :-((
 
Can anyone else confirm Kubuntu works with Wlan (Linksys)?????

---

### Post by -glow- on 2010-01-28
i tested some other things but so far no progress...

with debian gnome and nm-applet everthing wlan works fine...ive no clue what they did wrong by implementing the nm in ubuntu :?

---

### Post by Comtronix on 2010-01-29
Today I booted Knopix on my Gateway and it fails to run.
I moved it to my HP with the wireless off and it runs fine.
I can not easliy turn the wlan off on the Gateway but think Knopix would then run.
The Icon for wlan is identical in both versions of linux, so i'll guess that they share the same issue.
 
It seems that both Ubuntu and Knopix both fail to work properly in a wlan environment.
 
Thanks for that information, i'll try them.

---

### Post by Comtronix on 2010-03-10
The issue seems to be when useing a LiveCD. 
When I installed to a HDD the WLAN works just fine with Linksys.

---

