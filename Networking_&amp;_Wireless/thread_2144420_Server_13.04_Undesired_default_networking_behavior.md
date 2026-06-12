---
title: "Server 13.04 Undesired default networking behavior for laptop"
date: 2013-05-12
forum: Networking &amp; Wireless
---

### Post by cbSSS on 2013-05-12
Hi,

I'm using Ubuntu server 13.04 on my laptop so that I can run  OpenStack Grizzly & run OpenStack nested inside itself on it. I'll  have a server & a laptop running the nested OpenStack cluster. This  laptop is the first I'm installing the system to, and I've just begun.

I  have a KDE desktop installed to this laptop too, so that when I go to  OpenStack meetups, I can take my OpenStack with me & get help with  various issues I know I'll have with my installation. I want to be able  to migrate a Windows 7 back & forth between the OpenStacks running  inside my OpenStack cluster, and reach it via an rdp connection on the  KDE desktop when its in the laptop, or from another desktop computer  when its in the server.

So my networking isn't behaving the way I  need it to in the laptop, and I'm here to get help to make it work the  way I need it to behave.

The laptop has a wired connection that I  use when its docked at home, and a WiFi connection I use on occasion  when I work on the OpenStack installation from my desktop at my desk in  the other room (and when I'm out & about in town), so I want to be able to use both of them with the  OpenStacks, in a Multi-WAN failover setup, but that's beyond the scope  of this post- configuring that's for another post, to happen at another  time. I'm not worried about that right now, my concern now is this other  behavior I see happening that I can't have happening with regard to the  presence of networking at boot.

I use the network-manager kde  taskbar applet to handle the WiFi from the desktop, and it only works if  the wired connection is plugged in at boot, otherwise, it stays idle,  and isn't populated with the interfaces when I open it- if the wired  connection is unplugged at boot. This is a problem, for when I want to  use the WiFi, the network-manager applet is what I want to use to manage  the SSIDs & their associated passwords.

Another problem I  have with the network-manager applet is that when I do leave the wired  network plugged in, and am able to use the WiFi since the interfaces are  populated inside the applet, the password isn't remembered in a profile  for my home SSID, and I have to enter it each time, which is a problem,  since I use a 20 character password with serious complexity, and I  can't remember it- I have to look it up in my Blackberry each time I log  on & use that connection, which is a problem. I'd like to solve  that by providing that SSID's password in /etc somewhere but I don't  know how WiFi works in /etc to know how to configure that- if it's in  /etc/network/interfaces, I wouldn't know how that config would look,  since I've only used that file ever for servers without WiFi.

So I  need to be able to use WiFi from the applet when the wired connection is unplugged- without having to have the wired connection plugged in at boot, and  have it remember the password for my primary WiFi connection, which it  ought to connect to automatically when its in range. And I'd like it to use  the wired connection when its available, but I don't see where to  configure a priority in the applet anywhere, either, so if someone knows  how to do that somewhere I need to do that somehow, too.

I hope someone knows how to  make this work the way I need it to work, because right now I'm feeling  rather hopeless with it the way it is. Something happens at boot where  if it doesn't detect that wired connection, its as if the whole  networking system doesn't get turned on, and the connections aren't  available for the network-manager applet to manage to use WiFi on.

I'm  also interested in learning how the network-manager works alongside  /etc/network/interfaces, and how I'm going to be configuring OpenStack  to do its thing alongside network-manager doing its thing- I'll need to  configure the wired & wireless as multi-WAN somehow, and although its not my priority, if anyone  can provide an overview of how that's going to work out I'd be  interested in getting a preview of how I'll be sorting that, too.


Many thanks in advance.


Regards,
Chris

---

