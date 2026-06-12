---
title: "HD requirements for backend only"
date: 2010-12-31
forum: Mythbuntu
---

### Post by lviperz on 2010-12-31
I have a current system running for SD only. It is currently a combo BE/FE with 3 hauppauge pvr tuners. A pvr-150, 250 and 350. It has been my only system for years.

Currently it is running 10.04 and myth 0.24. It is working fine. But I wanted to do HD and this system in no way could do it. It's an old Dell 8300 with a 2.6 processor and 4gig ram. So I've been building a newer system with hardware to handle HD.

I have the new system running on it's own as a BE/FE and works well. So here is my question. Can I still use the old system as a backend only and still have it record the HD streams from my HDHomerun? 

I don't plan on using the old system for a frontend anymore and wondered what the requirements were for a backend only system that records HD. I was hoping to use the old system as a BE with it's current setup and just add the hdhr tuners. Then use the new system to playback the HD recordings.

Or should I leave the old system as is and use it as a master backend, use the new system as a secondary backend and record the HD stuff on it?

---

### Post by newlinux on 2010-12-31
> **lviperz said:**
> I have a current system running for SD only. It is currently a combo BE/FE with 3 hauppauge pvr tuners. A pvr-150, 250 and 350. It has been my only system for years.

Currently it is running 10.04 and myth 0.24. It is working fine. But I wanted to do HD and this system in no way could do it. It's an old Dell 8300 with a 2.6 processor and 4gig ram. So I've been building a newer system with hardware to handle HD.

I have the new system running on it's own as a BE/FE and works well. So here is my question. Can I still use the old system as a backend only and still have it record the HD streams from my HDHomerun? 

I don't plan on using the old system for a frontend anymore and wondered what the requirements were for a backend only system that records HD. I was hoping to use the old system as a BE with it's current setup and just add the hdhr tuners. Then use the new system to playback the HD recordings.

Or should I leave the old system as is and use it as a master backend, use the new system as a secondary backend and record the HD stuff on it?

Yes you can still use the old system, capturing HD doesn't take much processing power (no encoding or decoding necessary). Things to keep in mind are how many simultaneous recordings you will be doing and your storage groups. You may not want to record 5 things at once and commercial flag them to the same disk at the same time. I have multiple tuners and backends, and I like to record everything locally so my decision would be based on how much disk space each machine had and how much I was going to have each tuner record.

BTW, if your old system has a PCI or PCIe slot you can find a VDPAU capable card that will allow it to play back HD...

---

### Post by lviperz on 2010-12-31
Thanks for that newlinux. If I were to setup the new system as a slave backend, do I have to schedule the recordings from each backend?

Meaning, if the master has 3 sd tuners and the slave has 2 hd tuners, do I need to sechedule the sd stuff on the master and the hd stuff on the slave? Or is it possible to set the recording schedules from the master only.

As for the old system, it only has 1 agp and 3 pci. Currently all 3 pci slots are used with the pvr cards. However, I do need to pull one of the pvr cards so I can setup a remote on the new system since all it has for tuners is the hdhr. 

That would give me an empty pci slot but are there any vdpau cards for pci? I thought they were all pcie.

---

### Post by newlinux on 2010-12-31
> **lviperz said:**
> Thanks for that newlinux. If I were to setup the new system as a slave backend, do I have to schedule the recordings from each backend?

Meaning, if the master has 3 sd tuners and the slave has 2 hd tuners, do I need to sechedule the sd stuff on the master and the hd stuff on the slave? Or is it possible to set the recording schedules from the master only.

As for the old system, it only has 1 agp and 3 pci. Currently all 3 pci slots are used with the pvr cards. However, I do need to pull one of the pvr cards so I can setup a remote on the new system since all it has for tuners is the hdhr. 

That would give me an empty pci slot but are there any vdpau cards for pci? I thought they were all pcie.
Scheduling is done from the frontend or from mythweb independent of the backend (they all connect to master to do scheduling). So all the scheduling for all the tuners is the same if you are using one master backend and the rest are slave backends.

No, there are PCI VDPAU capable cards in addition to PCIe. Look for an 8400GS PCI card - I know they have a few on newegg - there are probably a couple other model VDPAU capable PCI cards. Keep in mind if you do get a PCI VDPAU card you will have to use VDPAU to play back hidef recordings because without VDPAU the PCI bus won't have enough bandwidth to play back hidef. Make sure to get a card with at least 512MB RAM.

---

### Post by lviperz on 2010-12-31
> **newlinux said:**
> Scheduling is done from the frontend or from mythweb independent of the backend (they all connect to master to do scheduling). So all the scheduling for all the tuners is the same if you are using one master backend and the rest are slave backends.

Thank you for the info. I assume I configure the tuners in each backend that they are in? So the master will have 2 tuner cards and I configure those 2 in the master. The slave will have 1 card and the 2 hdhr tuners. So I configure those 3 tuners in the slave. Is that correct?

And thanks for the video card info. I will look into a vdpau compatible pci card. I was going to build another box to play the HD content in my bedroom, but if I can make my old system play it, then I won't need the 3rd system.

---

### Post by newlinux on 2010-12-31
> **lviperz said:**
> Thank you for the info. I assume I configure the tuners in each backend that they are in? So the master will have 2 tuner cards and I configure those 2 in the master. The slave will have 1 card and the 2 hdhr tuners. So I configure those 3 tuners in the slave. Is that correct?

And thanks for the video card info. I will look into a vdpau compatible pci card. I was going to build another box to play the HD content in my bedroom, but if I can make my old system play it, then I won't need the 3rd system.

You are correct about the card configuration. Glad to help. Let us know if you have more questions.

---

### Post by lviperz on 2010-12-31
Thanks for the help. I do have one more question.

I know when you define your tuners in the backend you enter then in the order which you want the system to choose for recording.

So, my old system has 3 tuners. Encoder 1 is use first for recordings. Then encoder 2 if 1 is busy. If I watch live TV then the system will use encoder 3, basically going in reverse order.

How does that work when you have 2 backends? Do I have to define my tuners in the order I want by switching between the 2 backends?

---

### Post by williammanda on 2010-12-31
> **lviperz said:**
> Thanks for the help. I do have one more question.

I know when you define your tuners in the backend you enter then in the order which you want the system to choose for recording.

So, my old system has 3 tuners. Encoder 1 is use first for recordings. Then encoder 2 if 1 is busy. If I watch live TV then the system will use encoder 3, basically going in reverse order.

How does that work when you have 2 backends? Do I have to define my tuners in the order I want by switching between the 2 backends?

There are two ways to setup priority of tuners that I know of. 1st, which you have already done, the first card installed or recognised is encoder 1. 2nd, you can set a priority for each tuner. Enter myth backend setup > input connections > select tuner card that you want to setup > goto the 2nd page > input priority. The greater the number , the greater the priority. For example I have 3 tuner cards. DVB 1 - 3. I have DVB 1 set to 0 (only record when the other 2 are busy) and DVB 3 set to 2 (the preferred tuner card).

---

