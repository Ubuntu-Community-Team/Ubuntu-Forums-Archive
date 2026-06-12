---
title: "Newbie Network problems"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by james_r_lucas on 2010-11-30
Hello Everybody

I'm new to Ubuntu - I've decided to give Ubuntu Studio a go as an alternative to Windows :)

However, after installing it, neither of my network cards work. I have a Intel Pro Wireless 3945ABG wireless card, and a Broadcom Netlink Gigabit Wired card

Neither work, And I'm not sure how to. I've tried searching, and have come up with the .tgz file [here]("http://intellinuxwireless.org/?n=Downloads"), but I have no idea what to do with it

I'm concentrating on the wireless card for the moment, seeing as that will be the main one I use

So can anyone give me a guide as to how to get it working?

Thanks in Advance

---

### Post by Suparious on 2010-11-30
You might want to start by identifying the chipset of your network card(s) and download the windows driver.

Then you can research how to "wrap" your windows driver in linux with 'ndiswrapper'.

The reason for this, is the lack of specification of new hardware chipsets being released to the community, and/or lack of developpers to port/rewrite native linux drivers.

As an alternative, any wireless nic with the RT73 chipset is common, plug and play, and dirt cheap.

---

### Post by Suparious on 2010-11-30
Actually, that link you posted uses the 'compat-wireless' framework.

have a look at their site: 
[http://linuxwireless.org/en/users/Download/stable/]("http://linuxwireless.org/en/users/Download/stable/")

It looks like you install 'compat-wireless' and feed it that 'tgz' file from the intel site.


Good luck!

---

### Post by james_r_lucas on 2010-12-01
I've installed the compat-wireless stuff, using the guide on the website. It already has the iwl3914 file included, so I didn't have to use the tgz file I downloaded. And it seems to have worked - I now get a light on the wireless card.

However, I now get an error message when I open the network manager from the panel icon

it says "Could not find information on interface 'eth0:avahi' in /proc/net/dev"

I'm not sure if this has anything to do with the fact I tried my other USB wireless card - which again didn't do anything

Thanks for the help

---

### Post by james_r_lucas on 2010-12-01
I'm making progress - the wired network card now works, so I have internet at last :D. Don't ask me why it's started working now :D

So now just the wireless to sort out

---

