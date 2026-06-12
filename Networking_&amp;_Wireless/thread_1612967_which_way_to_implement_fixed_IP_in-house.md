---
title: "which way to implement fixed IP in-house"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by SaintDanBert on 2010-11-03
If I config a fixed IP for my laptop, I must "do different" when I am walk-about.

If I config my access point to match my laptop media access (MAC) address with a fixed IP, then I must pre-load every workstation and phone and PDA.

All I want is for my linux nodes to interact with all of the *nix file sharing tools and utilities. I'd also like my in-house win-doze and apple workstations to "play nicely."  Pure visitors -- neighbors, colleagues, game posse, etc -- would use DHCP ... details sorted out later.

I'm really tired of situations with two workstations on the same desk
that cannot talk with each other because they do not know the respective in-house IP address.

Someone please help,
~~~ 0;-Dan

---

### Post by Iowan on 2010-11-03
If the DHCP server (router) is capable, it can issue "static leases" based on MAC address. The machines get the same address each time (on the home network), but needn't be changed from static to DHCP addressing each time the machine "goes mobile".

---

### Post by SaintDanBert on 2010-11-04
I'm aware of this technique.

Your post begs an associated question:
[highlight]Q1:[/highlight] Which utility helps an Ubuntu laptop user to manage the several and varied network configurations to which the workstation might connect?

Such a utility is likely several distinct parts:
[list=1]
[*]low level parts that dance with the various network devices
[*]high level parts that manage named configurations and stores of details associated with those configurations
[*]middle level parts that accomplish interactions between the high and low levels, end-user notifications, gears and motors.
[/list]

In my case, I see the following configuration opportunities:
[list]
[*]at-home
[*]at-work without VPN
[*]at-work with VPN
[*]generic public hotspot 
[*]frequent user hotspots (school, coffee house, airport lounge, &c)
[*]network associated with each client site
[*]various wire-based configurations
[*]various developer oriented configurations
[*]various broadband (mobile phone) configurations
[/list]
*NOTE -- "at home" and "at work" might be variations onthe same network or be radically different.*

I open my laptop "somewhere" with some mission in mind.
That "somewhere" offers network connection options. Let's use the term "personality" to refer to the combination of place and net options.
I'd like to have the several and various net options stored with a name that I could call upon relative to each "somewhere" I visit. Better still, if the utility would recognize available net options and recommend a matching "personality."

Armed with such a utility, my fixed-IP request becomes straight forward. I create a wireless "personality" for use in-house with fixed IP configuration and I create alternative "personalities" for use elsewhere when I need DHCP.

I've tried to use **network-manager** without success. I'm using **wicd** because it likes my hardware better than network-manager.

On the win-doze side, my Lenovo Thinkpad has an application-utility called "Access Connections" that does a nice job along the lines that I describe. I simply have not found similar functionality for use on *-buntu linux. This might be due to my own lack of familiarity with features offered by readily available linux applications.

Merci d'avance,
~~~ 0;-Dan

---

