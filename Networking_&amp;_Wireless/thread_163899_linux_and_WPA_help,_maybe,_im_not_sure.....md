---
title: "linux and WPA help, maybe, im not sure...."
date: 2006-04-21
forum: Networking &amp; Wireless
---

### Post by x5452 on 2006-04-21
I just replaced our old 802.11 b wireless router witha netgear 54 g router.  I enabled WPA security, ( i set it all up through windows) and i restricted access by inputting my MAC address.  got online and all good while in windows. I then reboot into linux, and my internet appears to come up.  (I am posting from my linux) but i have the little 'network monitor'icon up and it used to say signal at 99-100% always, now its like 70-80%, also, every few seconds it flashes a yellow trianlge with exclamation point in it, and the signal bar, usually 4 blue diamonds, changes to one red diamond.  Just for a second, then goes back.  Like I said, i appear to be online, but what is that?  Also, will I automatically connect to the network I want? where can i choose, like in windows, View available wireless networks?  so i cna choose the one i just set up with a new name, and enter my encryption key.... Please help a confused noob, thanks!  :mrgreen:

---

### Post by firecat53 on 2006-04-23
There's no good GUI solutions that work with WPA well, yet, that I'm aware of. You have to dive into the command line a bit. There are ways to setup your /etc/network/interfaces file so that you'll get functioning wireless/WPA on boot. I've posted some examples, as have other people.  Multiple networks also still take some work to switch between. Easy once you know how, but still a learning curve....

Good luck,
Scott

---

