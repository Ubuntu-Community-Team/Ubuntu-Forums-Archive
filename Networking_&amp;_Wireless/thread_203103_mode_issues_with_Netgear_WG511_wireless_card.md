---
title: "mode issues with Netgear WG511 wireless card"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by anandi on 2006-06-24
Hi!

I have been trying to use the NetGear WG511 wireless card on my ibm R50 laptop. In my wireless network, i have 2 laptops, the other one is using Win XP.

Now when i connect to the wireless router, the xp laptop is not able to, and vice versa. Diagnosing the problem, it came down to the mode.

In Ubuntu, the mode is Managed, where as the mode in XP is Ad-Hoc. I tried to use

iwconfig eth3 mode Ad-Hoc 

however the above still doesn't cause the network to start working.

Can anyone please point me to the right direction and tell me how to get the network working with Ad-Hoc mode ?

Thanks.

---

### Post by kewldude606 on 2006-06-24
If you have a wireless router the mode should be managed.

---

### Post by anandi on 2006-06-25
[QUOTE=kewldude606]If you have a wireless router the mode should be managed.[/QUOTE]

Yes i do have a wireless router, its a Netgear WGR614 v4, 54Mbps.

Now i can't find any setting inside the router config to make it work in Managed/ Ad-Hoc mode.

The end result right now is that out of 10, 8 times my ubuntu doesn't have wifi working even if i remove the xp laptop from the network. I have tried to reboot the router, remove the pcmcia card and insert is again. However the problem remains as it is.

The card has 2 lights on it, Green and Orange, when the wifi is not working, both the lights go on and off. Incase its working, only the Orange light shows the activity, Green stays on. (sorry if the explanation sounds lame, however i am reallt cornered in this problem and can't think of much other than on how to get it running)

Is there a different driver perhaps which i can try and install ?

Thanks.

---

