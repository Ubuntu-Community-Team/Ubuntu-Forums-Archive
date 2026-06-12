---
title: "Strange wireless issue"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by wolfgang89 on 2011-02-23
I have Ubuntu Server 10.10 installed and working properly other than one strange occurrence. I have a dwl510 wireless adapter installed using ndiswrapper. I can connect to the internet but for some reason I can not ping my router or any of my other computers from the server nor can I ping the server from any of my other computers. If I connect a cat5 cable to the wired port, all ping functions work fine. Any ideas?

---

### Post by blakep2 on 2011-02-23
AP Isolation on your router might be enabled

---

### Post by wolfgang89 on 2011-02-23
Checked that, it's disabled. I'm trying a fresh install to see if maybe a package was corrupted somehow.

---

### Post by linuxbasiccommand on 2011-02-23
> **wolfgang89 said:**
> I have Ubuntu Server 10.10 installed and working properly other than one strange occurrence. I have a dwl510 wireless adapter installed using ndiswrapper. I can connect to the internet but for some reason I can not ping my router or any of my other computers from the server nor can I ping the server from any of my other computers. If I connect a cat5 cable to the wired port, all ping functions work fine. Any ideas?
  You configure IP Address of pc.

---

### Post by wolfgang89 on 2011-02-24
Yep, tried both static and dhcp setups neither allowed proper operation. I've abandoned that particular project computer for now and continued work on other projects. Strangest part is if I run a livecd of Ubuntu Desktop 10.10 the wireless card works fine out of the box. I can go somewhere with that, but I'll deal with it later. Thanks for the ideas.

---

### Post by wolfgang89 on 2011-02-28
Wasn't able to get wireless working on that server install, something must have been corrupted that I couldn't find. After a fresh install I was able to get the wireless working with a little trial and error. Thanks for the suggestions.

---

