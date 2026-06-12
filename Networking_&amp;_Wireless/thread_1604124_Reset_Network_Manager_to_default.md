---
title: "Reset Network Manager to default"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by Strategist01 on 2010-10-23
Hey guys.

I seem to have somehow mangled my my Ethernet and wireless's connection to the outside world on my Ubuntu 10.04.1 machine. I was trying to get a static local IP, and that worked great for a few days, until I lost all Internet access completely. However, I can connect to my router on my wired connection - but not the wireless.

You can see what I did here: [http://ubuntuforums.org/showthread.php?t=1600784](http://ubuntuforums.org/showthread.php?t=1600784)

Now, I just want everything to work as it did when I installed Ubuntu 2 months ago. How can I reset Network manager back so that it just works? I realise that don't need a static IP, it can only be 2 IPs, as I have 2 PCs only.

Or is there some better way to manage my networks? I'm not the best when it comes to those. :-?

---

### Post by coffeecat on 2010-10-23
Right-click on the network manager icon and choose 'edit connections'. Go through each of the tabs and delete all the entries. You now have NM as it was.

If you did any system file edits as described in that dreadful ubuntuguide link you were given in your other thread, undo them.

Did you have problems assigning a static IP address with network manager? It's worked for me when I've tried it.

---

### Post by Strategist01 on 2010-10-24
Ok, I managed to reset the system file back to how it was before I did the edits. Then I restarted my PC and it gave me back my Internet connection. Now, I tried to set a static IP with NM, but it kept on changing the parameters, like the gateway and netmask IP to different IPs than what I had specified when I re-plugged the cable in. I just let it use DHCP, to make my life easier.

---

