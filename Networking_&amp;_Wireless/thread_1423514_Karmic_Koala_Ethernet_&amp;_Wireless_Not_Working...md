---
title: "Karmic Koala Ethernet &amp; Wireless Not Working...."
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by dark3lf on 2010-03-06
Greetings.
I've had problems lately connecting to the internet via ethernet or wireless for some reason: it's just been these past few day, just two days ago wireless was working fine (although I've never figured out ethernet). I think it may have something to do with the fact that I installed some system updates right before it stopped working...

Anyway, my computer seems to recognize all wireless and wired networks, but it just keeps trying to connect without actually connecting. I've tried practically everything... Any Ideas? Thx in advance!

Regards

---

### Post by cometdog on 2010-03-06
I had exactly the same symptoms about 2 weeks ago, but almost certainly a different root cause.  Maybe my experience can help you a bit anyway.

In my case due to bug that shipped with Karmic, I had to use network-manager and network-manager-gnome from the network-manager trunk ppa.  On the 24th or 25th of Feb there was an update to that which broke my networking in exactly the way you describe, both wired and wireless.

I was able to get a working connection periodically by doing

```
sudo dhclient
```

from the terminal while nm applet was spinning away.  Sometimes had to repeat that as frequently as every minute to retain a connection.  In retrospect I might have had some luck by just setting up a fixed IP address (on my home network).

I'll assume you were broken by some kind of update.

In my case, the packages I was interested in were network-manager and network-manager-gnome.  You should try to downgrade them to a previous version to see if you can get your networking to function.  Hopefully you have an old version in

```
/var/cache/apt/archives
```

If so, you can install those with dpkg.  May have to do --force-downgrade and/or specify the specific version of the package.

Another option is to downgrade to Jaunty's version of these packages. If you can connect intermittently using dhclient, you may be able to add the Jaunty repository and downgrade these packages to the Jaunty version in Synaptic (force version).  Barring that you could download the Jaunty packages with another computer, copy them over, and install them with dpkg.

If you end up finding a version of network-manager and network-manager-gnome that function properly for you, I recommend locking these packages in Synaptic so you won't accidentally update them later.

HTH

---

