---
title: "Make a wireless AP and share wireless internet with it."
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by lifelike27 on 2011-03-12
Hey,

I have a Dell Studio 1558 with a Broadcom wireless adapter. It's a brilliant piece of hardware and love everything about it except some of it's overheating problems.
When I first bought it with Windows 7 pre-installed, it had an application installed on it called PeerNet, which creates a wireless network for other computers (and wifi-enabled phones) to connect to it. Simultaneously, you could also share your internet connection with these users. The internet connection could be either wired or wireless.

My question is, how do I go about finding the same functionality on Ubuntu since I know my hardware is capable of it. (I believe in Windows 7, it creates a virtual adapter that it uses)

I know there are ways to share a WIRED internet connections with some help with the terminal, but I haven't found a way to share a WIRELESS internet connection.
The network manager allows you to create a wireless network but I'm unable to connect to another wireless network at the same time.

The reason I mentioned mobile phones is because my mobile (Android 2.2) is unable to find a wireless network created by the network manager, but another laptop is (without internet access that is).
I've noticed that mobile devices and iPod's aren't able to find ad-hoc networks on Windows PCs as well.

I hope someone out there will be able to find a solution for me (and surely others as well!):D

Maybe the final release of 11.04 will help out later if nothing turns up now. :)

---

### Post by mikewhatever on 2011-03-12
You can create a new Ad-Hoc wireless AP using the network manager applet.

---

### Post by lifelike27 on 2011-03-12
> **mikewhatever said:**
> You can create a new Ad-Hoc wireless AP using the network manager applet.

How exactly would you do that? I've tried adding it through the network options but it constantly connects and disconnects until I stop it. 

My phone is also unable to find any ad-hoc networks.

---

### Post by mikewhatever on 2011-03-12
Unfortunately, I've no first hand experience with Ad-hoc networks. Supposedly, you simply create a new network and then change its mode to Ad-hoc.

---

### Post by lifelike27 on 2011-03-12
When you create a wireless network from the network manager options it becomes an ad=hoc network, and this is what gets stuck in the continuous loop of connecting and disconnecting.

---

### Post by spiky001 on 2011-03-12
Set the wireless setting ipv4 to shared with other computors

---

### Post by lifelike27 on 2011-03-12
> **spiky001 said:**
> Set the wireless setting ipv4 to shared with other computors
When you create a new wireless network is changes the settings to Shared between computers when it makes it an ad-hoc network.

---

### Post by spiky001 on 2011-03-12
Yes the pc with internet set the ipv4 to shared then the others can share it thats how mine works

---

