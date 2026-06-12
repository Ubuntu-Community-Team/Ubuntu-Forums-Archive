---
title: "How to make your computer invisible to other clients on a wireless network"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by Consecrated on 2010-12-26
Hello all,

I want to make my computer invisible or hidden to the other computers connected to the same wireless network. In other words, I want to turn off network visibility or network mapping. 

I think this amounts to the ability to turn on and off the Windows Link-Layer Topology Discovery (LLTD) Responder. [http://support.microsoft.com/kb/922120](http://support.microsoft.com/kb/922120)

On windows, I believe this would be comparable to setting the wireless network as Public instead of Home. I like to share files using Ubuntu when I am connected to my Home router, but I don't want to be discoverable or visible to clients on a public wifi network.

I have already created a shared folder on my desktop which installed some sort of networking components to interact with Windows, but I don't want the public wifi network to see this folder, or my computer name at all. I want to be invisible to other clients on the same network. Right now I am visible and can see other clients connected to this public wifi router. 

(In case some ask: I do not want to disable SSID broadcasting on the router as it is a public wifi router that I do not have access to.)

Can anyone explain how to do this (preferably with a GUI method so I can reverse the steps when I connect to my Home network)?

Thank you!

---

### Post by WthIteh on 2010-12-26
Install **gufw** package. It's a GUI for ubuntu firewall.
Open it from *System>Administration>Firewall configuration* and enable the
firewall. Then you could define detailed rule to block all accesses else of your own machines (home network).

---

### Post by hugmenot on 2010-12-26
With a firewall you will be invisible to pings, etc. But on a wireless network any traffic whatsoever that goes between you and the wireless station can be picked up easily and completely uncloak your presence. There is no other way.

If somebody runs kismet or airodump they will see you.

---

### Post by Consecrated on 2010-12-26
So all I have to do is "enable" firewall with gufw and it will effectively make me invisible to other basic computer users while on a Public Wifi connection? Then when I am home I can disable the firewall to share my folders? Or do I need to create specific rules to block the pinging that maps my computer onto the network?

I am unfamiliar to how exactly a firewall works or how to set rules for a firewall. Are the network settings in MS Windows "Home" and "Public" then just options for a set of firewall rules?

Thank you for your help!

---

### Post by Boondoklife on 2010-12-26
You really should clarify what you mean by invisible. You can not be completely invisible unless the wireless connection does not bridge your traffic with other wireless clients.

If you are on a bridged connection then they will be able to pickup certain data. If you are just worried about your shared files/folders, then gufw is what you want. Just install it and enable it. Make sure you change incoming to deny and outgoing is allow and you should be good to go.

When you get home just change it to disabled and your back to being able to share files.

---

### Post by Consecrated on 2010-12-26
Yes! Thank you. All I meant by "invisible" is that other client computers couldn't see my shared folder nor my computer's name when they search using the default network browser from their Windows/Mac which is also connected to the same router. I presume that the router's IP table would tell them that I was connected, but they shouldn't have access to that.

---

