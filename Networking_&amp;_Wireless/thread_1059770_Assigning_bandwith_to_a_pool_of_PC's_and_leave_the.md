---
title: "Assigning bandwith to a pool of PC's and leave the rest for public use (wireless)"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by nlz on 2009-02-04
I want to share my wireless bandwith with other people, but within boundaries. So I'm thinking how I can do this. I don't know an app for this, but i can imagine that I assign 95% of my bandwith to my PC's (which i can identify by the hardware address of the network card), and the rest is free for other people.

How can I do this? I think it's important that an easy app with GUI exists for this since it's pretty cool if you can check your email everywhere.

---

### Post by callan79 on 2009-02-04
> **nlz said:**
> I want to share my wireless bandwith with other people, but within boundaries. So I'm thinking how I can do this. I don't know an app for this, but i can imagine that I assign 95% of my bandwith to my PC's (which i can identify by the hardware address of the network card), and the rest is free for other people.


Hi nlz,

This is really quite a specialised job, there's more to it than you might think.

The two ways I see you can do this :


(1) Connect to the Internet using a router (or managed switch) that supports traffic shaping and/or port throttling. Then throttle one port to, say, 128Kbps. Connect a wireles access point to that port. Then, that wireless access point is limited to 128K total. Note you can also buy "hotspot" Internet routers that support this out of the box, but they are expensive.

---or--

(2) Put a router box in between your network and the Internet. Check out IPCOP ([www.ipcop.org](www.ipcop.org)), or EBOX ([www.ebox-platform.com](www.ebox-platform.com), based on Ubuntu), which can both do traffic shaping.



Personally, I'd go option 1. It's easy, cheap, reliable. And it does not need a dedicated machine running 24x7.

Good luck,

Callan

---

### Post by quirks on 2009-02-04
I have been looking for such a thing myself for a while now. But all I could come up with is a bunch of simplistic GUIs and some more powerful command-line tools. If you search sourceforge.net for the terms "traffic shaper", you will be presented a whole list of tools, but I couldn't find any which I would recommend. You might want to have a look at them.

Alternatively, there is the Linux built-in tc (for "traffic control"), which you can do almost anything with. It is a little hard to configure, though. I can only recommend reading the "Linux Advanced Routing and Traffic Control HowTo" (to be found here: [http://lartc.org/howto/](http://lartc.org/howto/)), if you want to go that way.

If anyone else comes up with a good (GUI) traffic shaper, I would appreciate it very much.

BTW: You talk about sharing your Internet access with "other people". Do you know (or even better: trust) these other people? I highly discourage giving strangers access to your private Internet access, because they might do evil stuff (like hacking other computers on the Internet) and your address is the first to come by, when the police finds out that computers were attacked from your IP address.

---

