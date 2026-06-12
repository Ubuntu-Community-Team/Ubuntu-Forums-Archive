---
title: "[SOLVED] operate win computer with ubuntu on another through network"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by captainron042 on 2008-12-14
I'm pretty new at Linux, so please keep that in mind with any advice. I had ubuntu pre-installed from Dell. This is a networking question, and I wasn't super great with networking in the windows world, either.

I still have my old computer with Windows XP. I also have a Dell Inspirion currently running Hardy heron 8.04. They are both wired into a router (Belkin G+MIMO).

I would like to:

1. share files between the two through the network.
2. Operate my win machine through my linux machine.
     My linux machine is connected to my home theater, but I cannot watch netflix on it because online movies are not compatible. If I could see my windows desktop through the linux machine, I could transfer the picture to my projector. Connecting my windows computer to the Home theater would just suck, for hardware reasons.

Any help you guys can give would be much appreciated. 
:popcorn:

---

### Post by nixscripter on 2008-12-14
Here are some places to start:

1. SMB is a way to share files over the network. Here's a start: [http://www.faqs.org/docs/Linux-HOWTO/SMB-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/SMB-HOWTO.html)

2. Controlling either machine can be done with VNC. There is a free version here: [http://www.realvnc.com/](http://www.realvnc.com/)

I'm not sure about netflix movies, because VNC can be pretty slow updating sometimes. Supposedly they will soon start supporting Linux; I suggest you wait for that.

Hope this helps.

---

### Post by captainron042 on 2008-12-17
Thanks! I'll look into that, but they've been saying they might support Linux for a while now. 

When I had a free couple of months of Canonical, they guy over the phone told me that when I get a router, he could "show me how to share the desktop". It sounded like there was something already installed or could be installed to do that for free.



I used the wizard on the Win machine to make a network folder, which worked out. My Linux computer can see it and do everything I want it to.

---

### Post by nixscripter on 2008-12-18
Glad I could help. If you can live without your Netflix for the moment, please mark the thread as solved (under the Thread Tools menu).

---

### Post by captainron042 on 2008-12-22
Ok, well, I installed the free version of VNC on the win machine. As it turned out, VNC was already installed on the Ubuntu computer. 

I followed the instructions and set up the VNC server on the win, but can't see anything with the viewer. Thier website only suggests that there is not a connection between the two computers, but a ping test comes back positive on both machines.

I wouldn't hold my breath on Netflix becoming Linux friendly. They've been saying that for a while.

---

### Post by jonobr on 2008-12-22
you may need to check that your router or firewall is accepting and forwarind connections on port number 5900

---

### Post by captainron042 on 2008-12-22
Thanks for the reply.

How do I go about doing that?

---

### Post by captainron042 on 2009-01-07
Well, I "solved the problem" by purchasing a Bluray player with netflix capability. 

Too bad I couldn't get this solution to work, though.

---

