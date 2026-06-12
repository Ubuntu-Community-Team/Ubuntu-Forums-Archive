---
title: "Missing Frontend functionality"
date: 2011-02-23
forum: Mythbuntu
---

### Post by peterhocking on 2011-02-23
Hi everyone

I've built a PC as a MythTV frontend. I installed the MythTV frontend using sudo apt-get install mythtv-frontend & can now watch my recordings & live TV, but it appaers to be missing some of the frontend functionality compared to my combined backend/frontend machine that does all the recording.

Amongst the bits missing is the ability to play music, games, look at images & ply DVDs. I'm not to worried about it except that I would like to be able to play DVDs, (&blu-ray disks when thats added to MythTV). Can anyone tell me how to add in the ability to play DVDs?

TIA

Peter

---

### Post by zzztownsend on 2011-02-23
these are provided by plugins, which were probably installed by default on you backend.

just install the packages
mythmusic
mythvideo
mythweather etc

Note that these play media off your local pc, so if you have music on your backend that you want to share over the network, you'll have to set this up first (eg using samba or nfs)

cheers

matt

---

### Post by peterhocking on 2011-02-23
> **zzztownsend said:**
> these are provided by plugins, which were probably installed by default on you backend.

just install the packages
mythmusic
mythvideo
mythweather etc

Note that these play media off your local pc, so if you have music on your backend that you want to share over the network, you'll have to set this up first (eg using samba or nfs)

cheers

matt

Thanks for your reply.

So to install these, I'd use "sudo apt-get install mythmusic" etc?

Thanks,

Peter

---

### Post by zzztownsend on 2011-02-25
yes, or browse in the synaptic package manager

---

