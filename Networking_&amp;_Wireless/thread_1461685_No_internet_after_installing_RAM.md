---
title: "No internet after installing RAM?"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by Enlil on 2010-04-24
Today I put in two brand new RAM sticks, same brand as the two I already have in there only difference is the new ones don't have the giant heatsinks that cover the stick. I have 4 slots for RAM, and I had 2 gigs in there, 1 gig in the first, and 1 in the 3rd. I put the two new ones in the empty slots. Everything worked fine, so it seemed. I was able to boot up, log into Ubuntu. It looked like everything worked, said I had internet access by the icon up on the top panel. The only thing that was curious was my weather app  wasn't updating. So I went into a web browser, and the home page showed up fine. Which was the default, the ubuntu google search engine. I tried to go to another site though, and it kept looking for the site, for a while but never found it. I tried multiple sites, same thing. I tried to ping [www.ubuntu.com](www.ubuntu.com), and [www.yahoo.com](www.yahoo.com) and it just hung for a while, after a while it couldn't find it. I tried ifconfig eth0, and even just ifconfig. It showed that eth0 was connected, it had the ip address, the DNS address, the MAC, everythting. Only problem I could see was at the end it said something like Interupts: 18, I don't know if that's normal or not.

So I tried then to reset the router, no difference. I tried resetting the hub (at least I think it's a hub, could be a switch or something), which is connected to the router, and the hub connects to my computer. Now that, made it worse. Now the icon for my internet has disappeared, well it tried to reconnect but can't. ifconfig eth0 brings up no ip address anymore, no DNS, no nothing. I tried rebooting, didn't help.

So here I am, and I'm definatly in need of some help. I find it very hard to believe that adding new RAM would kill my ability to get online, that doesn't make any sense to me.

I am using Ubuntu 9.10 64 bit, had 2 gigs in there, and now have 4.

Edit: I tried rebooting once again, and this time when logging on Ubuntu it for some reason checked my filesystem for errors, found none as far as I can tell, then logged on. Once I logged in, it connected again to the internet, but it's doing the same thing it was before I restarted the hub. Says I'm connected, but can't visit any webpage, weather isn't updating, but homepage is showing up, etc.

Also, this is my motherboard: [http://usa.asus.com/product.aspx?P_ID=JCYhbJmty7zBzLL2](http://usa.asus.com/product.aspx?P_ID=JCYhbJmty7zBzLL2)

And this is the RAM I had bought: [http://www.amazon.com/gp/product/B000I2C80K/ref=oss_product](http://www.amazon.com/gp/product/B000I2C80K/ref=oss_product)
Which is the same RAM I had in there, minus the one in there had a giant grey incasing/heatsink on them.

---

### Post by Mewshi on 2010-04-24
Try taking the RAM out, see if that fixes it.  Or try switching the ram around within the slots.  See if either of these ideas fixes it.

---

### Post by P4man on 2010-04-24
I bet it has nothing to do with the RAM, but somehow with the fact you disconnected your machine for opening it. A bad lan cable? Or not properly inserted? Of the lan card not properly seated in the PCI or PCI express slot? Something along those lines. It might even be a glitch with your provider that just happened at the same time. Can you try another computer?

---

### Post by Enlil on 2010-04-24
Well, I did some research and it seems a lot of people are having similar problems with the mobo I'm using where if there is more than 2 Gigs of RAM installed, it screws up the onboard NIC. I took out the 2 new gigs, and it works fine now, and I ended up ordering a pci express network card. I'll be installing that, putting in the new RAM and disabling the onboard to see if that helps. I'll post back when I have some results.

One question - When installing new hardware like the card, does Ubuntu automatically search and install drivers like Windows, or will it not work when I first log on, and will have to use a different pc to find drivers?

---

### Post by P4man on 2010-04-24
So I lost my bet heh. Your motherboard link you posted doesnt work, so I have no idea what board or cpu you have, but is this on a 64 bit ubuntu? I can imagine it giving problems on a 32 bit OS, but in 64 bit its kinda weird.

Anyway, as for ubuntu and drivers; if the drivers are in the kernel, then it will just work. Everything is detected each boot. If you are unfortunate enough to buy a nic that is not supported by the kernel, then you may have to download drivers and stuff. in some cases compiling them, meaning you need among other things build-essentials.

---

### Post by cascade9 on 2010-04-24
> **P4man said:**
> So I lost my bet heh. Your motherboard link you posted doesnt work, so I have no idea what board or cpu you have, but is this on a 64 bit ubuntu? I can imagine it giving problems on a 32 bit OS, but in 64 bit its kinda weird.


Odd, the link works for me- its a Asus P5NSLI (LGA 775, Pentuim 4/D Celeron D, Core2Duo motherboard) 

Enlil is right, it does appear to be a problem with the onboard network and 3GB+ installed. *engange cynicism* I wouldnt be suprised if Asus knew about this, on teh spec page for the board it says- 

"*When installing total memory of 4GB capacity or more, Windows 32-bit operation system may only recognize less than 3GB. Hence, a total installed memory of less than 3GB is recommended." 

BTW, it doesnt just drop the network- there are more than a few reports about vista running very slowly with 3GB+ installed and te network card turn on with that baord- 

[http://social.technet.microsoft.com/Forums/en/itprovistahardware/thread/1e6a69e8-9a19-4a43-819e-c58dd43ea054](http://social.technet.microsoft.com/Forums/en/itprovistahardware/thread/1e6a69e8-9a19-4a43-819e-c58dd43ea054)

Stupid marvel network card....I swear, the only time I see marvel mentioned its cause people have problems with thier hardware....

---

### Post by Enlil on 2010-04-27
I just wanted to update everyone that it worked. Installed a new network card, disabled the on-board, logged on and the internet works, RAM's detected. Knock on wood, but it seems that solved my dilemma.

---

