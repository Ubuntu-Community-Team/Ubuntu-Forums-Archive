---
title: "need the network clue fairy"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by jbeiter on 2011-05-26
Ok I'm a little in the dark on how networking is supposed to work on Ubuntu 11.04.

This is a laptop with wireless and a wired network. At work, I need to assign a specific MAC so that dhcp hands me the right IP.

I try to set it in /etc/network/interfaces:
-------------------
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
hwaddr 00:0f:fe:fa:44:a3 (not my real MAC)
------------------

and the system just completely ignores it. 
- /etc/init.d/networking restart (shuts down networking.. doesn't start)
- service networking start (doesn't do **** "networking stop/waiting"???)
- clicking on the network gui, enabling "Auto Ethernet" start up networking but ignores the interface settings, MAC, and gets me the wrong dhcp assigned IP. Same thing when I reboot.

I've been doing network engineering and linux since the fidonet days, I'm not new at this. 

What the hell is going on with it? It's like the GUI and config files are completely independent of each other.

What am I doing wrong here? This should be simple.

To add to the silliness,

"service networking stop" does nothing "unknown instance"
"init.d/networking stop" says it shutdown the network, but it doesn't.
"init.d/networking start" says don't use init.d scripts anymore, but use "service networking start"... which doesn't work.

In the GUI, the "wired networking" and "Wireless networking" options are greyed out. The only one selectable is "Auto Ethernet" which ignores any custom eth0s or Auto Ethernets I created and makes a new one.

is it me or is this totally nuts?

---

### Post by chili555 on 2011-05-26
> It's like the GUI and config files are completely independent of each other.Bingo!

Essentially, they are independent. It would probably work perfectly if you removed the GUI; in this case Network Manager, entirely. It probably also would work from the GUI if you deleted all the listings in /etc/network/interfaces (except loopback, of course) and clicked the GUI > Edit Connections > Edit Auto eth0 and filled in the cloned MAC address line.

In a perfect world, NM would ***completely*** relinquish control of any interface listed in /etc/network/interfaces but it doesn't...quite...make it. NM is not yet perfect.

---

### Post by jbeiter on 2011-05-26
thank you for the reply.

If I put my MAC in that first box, NM just creates a new interface and won't activate the one I want.

If I put it into the "cloned" box, the interface comes up and "ip addr" shows the interface with the MAC I want, but dhcp is giving me a bad address.. as if the bootp request used another mac.

Deleting everything but lo in the interfaces file seem to get some progress.

Is there another place to assign the MAC before the dhcp request goes out?

---

### Post by chili555 on 2011-05-26
> **jbeiter said:**
> thank you for the reply.

If I put my MAC in that first box, NM just creates a new interface and won't activate the one I want.

If I put it into the "cloned" box, the interface comes up and "ip addr" shows the interface with the MAC I want, but dhcp is giving me a bad address.. as if the bootp request used another mac.

Deleting everything but lo in the interfaces file seem to get some progress.

Is there another place to assign the MAC before the dhcp request goes out?What kind of 'bad address'? A 'you naughty boy, you don't have credentials, go away' kind of thing? The dreaded 169.xx address?

In order to have NM recognize the changes, you probably need to do:```
sudo /etc/init.d/network-manager restart
```I think you want the "cloned box."

---

### Post by jbeiter on 2011-05-27
"bad" meaning it was just giving me a pool host address, not my "static assigned"

Had the windows guys look on the dhcp [windows] server and it was showing my MAC, but missing the first two bytes "00". That was why it was giving me the wrong address.

It was right in network-manager, right in my dhclient.conf... So had him change my MAC to the screwed up one it was reading and it started handing out my right IP address.

weirdness.

So my final working config is the legacy MAC put into the cloned box of the default Auto Ethernet adapter in Network manager. Deleted everything except for loopback in /etc/network/interfaces. The windoze dhcp server is told to assign my static IP to the system reporting my MAC (minus the first two bytes)

This network-manager setup is messed up though. It should use the system configuration files like a proper *nix system. If the development team responsible for NM could get right on it, that would be grrrrrreaaat.

---

### Post by chili555 on 2011-05-27
Weird, indeed! I am glad it's working, by whatever means.> This network-manager setup is messed up though. It should use the system configuration files like a proper *nix system. If the development team responsible for NM could get right on it, that would be grrrrrreaaat.Yes, indeed. The NM guys are notorious for doing things the way they want to do them and if your particular driver or workplace network or many other things doesn't work as expected, well, you should talk to someone else, they think they are right and the world at large is wrong. I think in 90% of cases, for instance some University student that walks his Dell over to the coffee shop, it works quite well. In The case of old retired guys who sit in their recliners and attach to but one WPA2 network, it works perfectly.

It has improved greatly in the last 3-4 years but still has a way to go. I share your optimism for further improvement.

You might look into Wicd. A lot of guys swear it trounces NM. I have tried it and it works, for me, as perfectly as NM and as perfectly as manual methods, so I can't recommend or dis-recommend it. I don't recall if it has a 'cloned MAC' feature.

---

### Post by mtrudel on 2011-06-04
> **jbeiter said:**
> 
So my final working config is the legacy MAC put into the cloned box of the default Auto Ethernet adapter in Network manager. Deleted everything except for loopback in /etc/network/interfaces. The windoze dhcp server is told to assign my static IP to the system reporting my MAC (minus the first two bytes)

This network-manager setup is messed up though. It should use the system configuration files like a proper *nix system. If the development team responsible for NM could get right on it, that would be grrrrrreaaat.

Not sure I get all what you mean in this post, but just to let you know that your post isn't "lost" (I work on NM in Ubuntu)

To clarify a few things; much of the decisions come directly from upstream and we don't change them. For most things, I don't agree that changing the settings from upstream would be a good idea, unless they go directly against Common Sense (tm) or RFCs (or clash with conscious decisions we made in how Ubuntu as a whole should work).

For configuration files, when something is set for eth0 or any device other than lo (by adding an iface <interface> line), the expected behaviour should be exactly what you want: NM will leave the device alone, seeing as you've configured it in a config file. If this didn't work properly, I'd guess /etc/NetworkManager/NetworkManager.conf is set to managed=true, I can't really think of anything else (besides bugs... those happen). If it's not configured in /e/n/i, then NM will deal with the interface directly.

As for Wired Networking/Wireless Networking, if you're talking about the headings above devices; this is on purpose, it's a heading. Moving to indicators there was no other way to display them, since I couldn't use markup, bold, or whatever. For your devices that didn't respond properly in the GUI, I'm not sure what happened there. There may have been issues due to having config in /e/n/i and all of that. If it helps, NM 0.9 moves to having all the devices configured as files in /etc/NetworkManager. It will be available in 11.10.

I don't know why the bytes were lost for your mac address. If you share the exact values you put in the dialogs, and the logs -- **as a bug report, please, instead of here**, I'll be happy to look into.

And this brings me to my one point by posting here: I don't usually post or even really read the forums so much: I can't stand the format. 

**However, I read bug reports**
So if things are broken in NetworkManager in Ubuntu, by all means please file bugs. If you're not sure if it's something someone else reported, file a new bug anyway. I don't mind setting things as duplicates when necessary. The missing bits from the Cloned MAC sounds like a bug.
I also take a look at the AskUbuntu stuff every once in a while ;)

---

