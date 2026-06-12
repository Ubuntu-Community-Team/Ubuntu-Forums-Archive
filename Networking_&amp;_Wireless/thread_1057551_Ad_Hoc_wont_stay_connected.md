---
title: "Ad Hoc wont stay connected"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by MasterShihoChief on 2009-02-01
What I am trying to do is take my jailbroken iphone 3g and tether it to ubuntu using a program called PDANet which is a 3rd party app for the iphone. It required me to create an ad-hoc network on my computer so the iphone can share its 3g connection. The problem is i go to create an ad hoc network on the network tab in the toolbar at the top and i type in my desired ssih and dont even bother putting in a password. It creates the network, and it sees the network it has created, as does the iphone. The only problem is ubuntu refuses to connect to the ad hoc network that it created. I say to connect to it and it just immediately say network disconnected and it sits there and does nothing, no matter how many times I try to get ubuntu to connect to the ad hoc network it will always immediately say disconnected. The Iphone can connect to it just fine, but that does me little good if the computer cant connect to pipe data through the iphone. To make sure this process even works, i booted up my massively corrupted vista partiton that i havent had time to format yet, and tried the same process. It worked perfectly fine, in fact this post is from my supposedly unusable vista parition tethered to my iphone with the same program. The program is supposed to be universal as ad-hoc is ad-hoc. Any ideas on how i can make my ubuntu stay, or even at least try to connect to the ad-hoc it created would be most appreciated, thanks.

---

### Post by Sco-Buntu on 2009-02-25
You are creating an ad-hoc network on your Ubuntu machine, then trying to connect to it with the same wireless card? That simply won't work. Ad-hoc mode, or master mode is required to create a host network. Another wireless nic can connect to that in standard mode. A single card cannot connect to itself. Attempting to will (best case scenario) revert the wireless adapter to standard mode, and it's broadcast id, etc, will disappear.

What I think you want to do, once you put your wireless card in master mode, is simply connect to that with your iphone. I don't know which way you want to forward packets over this link, I'm assuming you want to allow internet access from your pc through your iphone...

All you need to do at this point is set your default route through the wireless card, and use the iphone ip as your gateway.

You'll want to clear any existing default route first:
# route del default

Then assuming you have already defined your host device's ip, and set your iphone's ip...
#route add default <wireless interface id (eth1)> gw <iphone ip>

I haven't used route on a linux box in a while, so you might have to do a little reading in the route man page to get the syntax right.

Good luck.

If this dosn't help, please be more specific what your trying to accomplish and add the output of "ifconfig" and "route -n"

---

