---
title: "gtx 570 driver install"
date: 2012-04-27
forum: Multimedia Software
---

### Post by Wickedares on 2012-04-27
are there any helpful instructions on how to install a nvidia .run file
i tried on 11.10 to do this and i think when i installed i told it to install third party stuff so it installed a bad driver and i downloaded the new driver but once i figured out how to actually install the .run file it poped up that x service is running and i found out how to cancel that then my screen whent black with text so thats what i had a problem with on 11.10

---

### Post by papibe on 2012-04-27
Hi Wickedares.

I would let the driver from the Nvidia site as the last resort.

First I would try the suggested driver. If that doesn't work I would upgrade to the version of this ppa:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

Then if that doesn't work either, there's another ppa with bleeding-edge versions:
 
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

(You would have to restart your machine after every upgrade).

I hope that helps, and tell us how it goes.
Regards.

---

### Post by Wickedares on 2012-04-27
> **papibe said:**
> Hi Wickedares.

I would let the driver from the Nvidia site as the last resort.

First I would try the suggested driver. If that doesn't work I would upgrade to the version of this ppa:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

Then if that doesn't work either, there's another ppa with bleeding-edge versions:
 
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

(You would have to restart your machine after every upgrade).

I hope that helps, and tell us how it goes.
Regards.

well the standard had a negative it sees one of my monitiors as a laptop display and the other one wont work. so i will try solution two now

EDIT: all three of those solutions had the same outcome. one monitor works wont see the other and before i messed with any drivers both monitors were working in a dual monitor setup. i guess that leaves the .run from nvidia... why dont you recommend it?

---

