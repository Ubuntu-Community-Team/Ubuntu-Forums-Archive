---
title: "Anyway to access a computer over a network"
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by Rhys_Mahabal on 2013-07-31
Hello, 

I was wondering if it's possible to have a computer in one room connected to switch and have the monitor with a wireless keyboard and mouse in another room connected to another switch. Effectively in my front room I just want a monitor (which could potentially by my tv) and a wireless keyboard and mouse. 

The big noisy machine with fans and HDDs will be hidden away with my server. 

This is closest thing I found; [http://www.eizo.co.uk/EIZO-Releases-17-inch-Network-Monitors.html](http://www.eizo.co.uk/EIZO-Releases-17-inch-Network-Monitors.html) 

Anyone do anything similar. I want to power of a very fast machine at my finger tips but none of the noise and heat generated from the HDDs anywhere near me. I could use a SSD and use my server for storage requirements but I will still have lots of noise from fans plus, I don't want a big box in my front room. 

Any thoughts

ps If you are interested this is the current build I'm thinking of [http://www.ebuyer.com/lists/list/181813](http://www.ebuyer.com/lists/list/181813)

---

### Post by Deaner13 on 2013-07-31
How far away are you talking? I have done something very similar with a REALLY long HDMI cable and a KVM switch.

Since HDMI is a digital signal buying budget cables does not affect performance.

---

### Post by Rhys_Mahabal on 2013-08-01
I did think that but, it would have to pass through two doors and across a hallway. I've already drilled holes through my walls and trunked in some cat6e cabling, so would like to go down the network route. 

Any other ideas? Another thought was around using a tablet over the network to connect to a remote machine? With maybe some kind of tablet keyboard. But I would still like a big screen monitor.

---

### Post by Quepali on 2013-08-01
I think that if you want to access your machine through switches, you will need to have at least a small machine nearby your computer, a raspberry Pi might work well. I've been using TeamViewer a lot. But I am sure there are som client-software that could be run, and then use the Pi as i thin Client??


PS. Did that make any sense?

---

### Post by ian-weisser on 2013-08-01
Depends how low-level you want to go.

KVM, which has been discussed, is a great and simple -and cheap- way to put the noisy box in another room.

Another option is SSH and X-forwarding, which is more complex...but also more flexible.

An even more complex option is LTSP (used in edubuntu), though this seems perhaps inappropriate for a single client and server.

---

### Post by The Cog on 2013-08-01
I have heard good stories about the speed of this product: [http://www.nomachine.com/](http://www.nomachine.com/)
Look for the free download on the right, and the nx free edition. 
I haven't tried it, and don't know the difference between the free and paid versions, but I have seen good write-ups in the past.

---

### Post by oregonbob on 2013-08-02
Nomachine.com version of NX is fantastic except with Unity. With most window managers it is the closest thing to Windows Remote Desktop, no latency, etc.
I still haven't got it to work right with Unity however.

---

### Post by zealibib slaughter on 2013-08-02
you could always set up a lightweight (older like maybe a P3) computer for your living room, and use SSH, FTPS, and VNC to access your other one.Thats what I do with my tablet, or as mentioned above a raspberry pi running android with ssh ftps and vnc viewers would work really good.

---

