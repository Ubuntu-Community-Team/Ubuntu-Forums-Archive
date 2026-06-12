---
title: "Cannot see other ubuntu computer"
date: 2012-04-17
forum: Networking &amp; Wireless
---

### Post by Enkel on 2012-04-17
This is silly!  I have a small Windows network of two desktops with wired connections and one laptop with a wireless connection and a Netgear Router.  When all three are running Windows I can see them all on my local network (set up more or less as Windows standard).  When one or more is running ubuntu they disappear from the network as far as the other computers are concerned, but they can still see the Windows, but not the ubuntu computer(s).

I think I'm missing something simple here.  Any ideas, please, anyone?

Thanks

---

### Post by newbie-user on 2012-04-17
Ubuntu is generally closed off for security. There are no open ports by default. With Windows, some things are available over the network by default. If it's in your internal lan, then no problem. On a public network, though, you generally don't want your computer to be discoverable.

So, if you want your Ubuntu boxes to be visible on the network, you'll have to open up some ports or enable some sharing services on them. Actually, the Ubuntu boxes should be pingable, so they're not completely hidden from other computers on the network. So it's not silly at all. Ubuntu is just more secure by default.

---

### Post by papibe on 2012-04-17
Hi Enkel.

My guess is that your router is not working as the default router, and the Windows machines are using netbios broadcasting to discover each other.

If you install the package samba, it will include a tool called nmbd. That will broadcast its name on a 'language' that Windows will understand.

I hope that helps, and tell us how it goes.
Regards.

---

