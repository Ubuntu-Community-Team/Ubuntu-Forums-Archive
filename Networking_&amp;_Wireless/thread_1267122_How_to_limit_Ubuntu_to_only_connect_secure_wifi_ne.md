---
title: "How to limit Ubuntu to only connect secure wifi networks"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by DevilDriverX on 2009-09-15
Hi,
 
I'm looking for a way to configure Ubuntu (Hardy) to only allow connections to secure Wifi networks only.
 
Maybe by blocking the option, I don't care if it lists the networks, but just block the option to connect to one.
Or at the very least, notify the user it's connecting /connected to an unsecure network.
Obviously the first option is the preferred one.
 
How can this be done?
 
Thanks

---

### Post by DevilDriverX on 2009-09-25
Bump
:(

---

### Post by t0mppa on 2009-09-25
Why exactly do you want to do this? Ubuntu doesn't connect to networks at random, the only time it automatically makes a connection is when it sees a network that you have defined as one that should automatically be connected to.

In any case, you can see if the network is secure or not before connecting to it and that should give clue enough. If you're worried about other users accidentally connecting to unsecured networks, it might be a wiser thing to actually teach them the differences between the two.

---

### Post by DevilDriverX on 2009-09-25
We do inform our users on the good and bad habits of computer and data security, but you can teach all you want, eventually someone will forget, or worse yet, won't care.
Anyway, I asked how to stop it in the machine level, not human. 

Even windows drops a warning on you when you try to connect to an unsecure network. 
I really didn't expect this to be such an issue.

---

### Post by t0mppa on 2009-09-26
I know you asked for software level, but it's not built in to any of the GUI applications that I've used and this has been requested before by parents not wanting their kids to use neighbors unsecured wireless to view porn without any resolution. Therefore was suggesting an easier way out.

Could always disable their wireless access for good, since weakly secured APs are just as bad as unsecured ones and I'm pretty sure you won't find a program, even for Windows, that scans the password user is trying to input and decides based on whether it's strong enough not to get easily cracked whether to allow connection to proceed.

And I was just curious in which case you'd need such a feature. And I guess the answer is ignorant folks with a work laptop taking it outside office and transferring sensitive information over an unsecured network.

---

