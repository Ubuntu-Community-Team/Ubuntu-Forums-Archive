---
title: "clueless: setting up a linux network that allows for xp machines"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by originalsynthesis on 2009-02-15
Im trying to learn how to network on ubuntu. I want to set up a nw so that my ubuntu machine can be linked up to an xp laptop through my wireless router. So far, the docs i've found on the subject in the ubuntu documentation are way over my head (i haven't gone through all of them, though) Ideally, i want my linux box
to be the adminstrator/server, with the xp laptop connecting as a user. Where do i start? Im familiar with the basics of xp networking, and thats about it. 

another question that just popped into my head: since i dual boot my main machine with xp, would i need two networks to be setup depending on which OS i am using on at that moment for the other laptop to be able to connect?

---

### Post by zandman on 2009-02-15
Well, then i think i'm slightly ahead of you :): i've got 3 xp-machines and 4 Ubuntu-workstations (mix of 8-versions) connected to 2 Ubuntu servers. But it's all very basic, nothing spectacular, it just works.
How did i do it:
- on the servers there's SAMBA installed
- on the rest nothing special
The thing i found the hardest is properly configuring SAMBA.

If you're following the road above, you'll have to install samba on your Ubuntu-workstation. You can do that via the package manager  -> System, Administration, Synaptic package manager, once that is open select the main samba package, that should (if required) include any packages it depends on automatically.
Just click your way through, if you want to feel tough go via the terminal :P m sudo apt-get install <package-name> 
If you're not too worried about security (i've got 3 young kids in the house + a wife that just wants it too work, so i'm reasonably paranoid on who has write access to what) the samba configuration file shouldn't be too complex.
Since you want the linux workstation to be the server, you'd probably best give that one a fixed IP-address, so you always look for the same. Yes, there are most likely ways to have a dynamic IP-address for your server and then still always find it, but that's way over my head.  If you give the server a fixed IP-address, make sure it's outside the range of dynamic addresses that your router uses (assuming that that's the one functioning as the DHCP-server on your network....)

As far as the dual booting: never tried that, my guesstimate is that you'll need 2 sets of settings for that (from the xp-laptop point of view).

Yes, probably more questions after this then answers, :confused: but quietly dig your way through and you'll get there.

Read around this one a bit: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows%2C_Linux%2C_and_Samba](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows%2C_Linux%2C_and_Samba).
That should give you some basic help on it.
There was once a dutch site on it (Bart & David) with pretty good instructions on how to set it up, but i guess that you prefer reading the SAMBA-instruction manual over reading dutch.


Good night.

---

### Post by originalsynthesis on 2009-02-15
> Yes, probably more questions after this then answers

to put it lightly, yeah, you could say that (what?! no gui!?:shock:), then again I knew already that linux networking was going to be quite the adversary, so i kind of expected it. But this does give me a direction to follow, which is what i was looking for. thanks zandman!

---

### Post by Ocxic on 2009-02-16
install webmin ([www.webmin.com](www.webmin.com)), that'll give you  a GUI for most anything you want to setup, really great.

---

