---
title: "How to optimally configure ufw?"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by nnn= on 2011-01-31
[SIZE=2]I'd like to improve my system configuration by enabling [/SIZE][SIZE=1][SIZE=2]UncomplicatedFirewall[/SIZE], but this is complicated by the fact that I'm not that clear on how things work and what's needed (and whether this is the right solution at all).

My initial guess would be to keep ports closed until an app on my pc requires one (and then to close it), or I plan to connect from outside.

However if this were to be implemented, even some undesired, installed app could request a port. So I should know what ports are required for normal operation ahead of time, when setting up ufw. If I enable tcp everything will work fine?

On the other hand, why can't that undesired app just use some regular port, like http? I'd say because that port doesn't have enough bandwidth, but then I'd counter it by saying firefox, updates and others are fine with sharing a port.

Then if I want services like ssh and telnet, I'll have to open those two-way ports. If I open a port, does it automatically start a [/SIZE][SIZE=1]listening [/SIZE][SIZE=1]daemon?

In ufw intro, other frontends to iptables are mentioned, and I wonder if something else besides ufw might be more useful to allow only a list of known apps to access net. Changing the list would require perms. Or something.

Please help me make sense of this.
[/SIZE]

---

### Post by nnn= on 2011-02-22
I need suggestions.

---

### Post by Bluesan on 2011-02-22
Here's a starting point for you to learn about UFW:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by nnn= on 2011-02-24
I read the documentation, but I don't know how to apply it in connection with what I outlined above. Those questions are crucial for my understanding.

---

### Post by benali72 on 2011-02-25
I'm with with you on this one, @nnn=.

I read the ufw doc [**here**]("https://wiki.ubuntu.com/UncomplicatedFirewall?action=show&redirect=UbuntuFirewall") and [**here**]("https://help.ubuntu.com/community/UFW").  

If I understood it correctly, users are expected create individual rules from scratch for all their apps and ports?

Why not a firewall like ZoneAlarm, where it lists all your apps in a chart. Then you just check off which ones area allowed to have IN and OUT access?

If anyone knows of a user-oriented firewall for Ubuntu please let me know.

Right now I'm just using ufw's defaults, which appear to be deny all incoming and allow all outgoing.

Thank you.

---

