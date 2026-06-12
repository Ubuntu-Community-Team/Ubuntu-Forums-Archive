---
title: "Can you reset ubuntu networking back to original?"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by linorics on 2009-10-26
I have 9.04 on my laptop. I tried to install beta software on it(Remobo) and now my internet can't connect to my wifi router. It just keeps asking me for the password. I am also sure the password it 100% correct. 

My goal of course is to fix the problem, so my idea was to see if there is a was to "reinstall my networking" so that its back to its original state.

Any idea is welcome. I really don't want to have to reinstall the OS...

---

### Post by Iowan on 2009-10-26
Start by checking */etc/network/interfaces*. Out-of-the-box, it should have only two lines - defining "lo". Comment out anything else (#), and restart/reboot. (I usually reboot so Network Manager and networking all get resynchronized.)

---

### Post by linorics on 2009-10-26
yes inside that file there are only the 2 lines that define lo. Anywhere else?

---

### Post by linorics on 2009-10-26
I just reinstalled Net-tools and network-manager Still the same issue. I also confirmed that the lan works fine. It seems to be something with the wpa/wpa2 authentication(just a guess...)


Also something I just remembered when i installed it it asked about the DECNode name and i think. I know i gave it 6.423 for my DECnet address using my wifi's mac...

---

