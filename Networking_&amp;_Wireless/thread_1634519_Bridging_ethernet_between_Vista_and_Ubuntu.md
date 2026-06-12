---
title: "Bridging ethernet between Vista and Ubuntu"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by nufc365 on 2010-11-30
Hey, a little help would be greatly appreciated. I have an old desktop with Ubuntu 9.10 and Windows XP dual booting, it is connected through ethernet cable to my laptop which is running Vista and is connected wirelessly to my router. 

Now the problem is I have bridged the connection between Wireless Connection and LAN and when I boot my desktop up in XP I can connect to the internet but when I boot up Ubuntu it doesn't connect and I have no idea how to configure it. (XP connected automatically) 

Any help much appreciated :p

---

### Post by nufc365 on 2010-11-30
Nevermind. Got it to work somehow

---

### Post by nufc365 on 2010-11-30
Back again, I did have it working and was browsing the internet fine but it just drops the connections at random times, I have no idea. My laptop and desktop have the same IP address, but I figured thats what you get from bridging the connection, right? However I'm getting the IP address conflict message so do I have to assign them individual addresses? How would I do that?

---

### Post by redmk2 on 2010-11-30
> **nufc365 said:**
> Back again, I did have it working and was browsing the internet fine but it just drops the connections at random times, I have no idea. My laptop and desktop have the same IP address, but I figured thats what you get from bridging the connection, right? However I'm getting the IP address conflict message so do I have to assign them individual addresses? How would I do that?

Yes you need individual IP addresses for each machine. I'm not sure what you have done previously.  What did you do to "bridge" your laptop and desktop?  What made you think you needed to configure a bridge?

Do you have a router that both of these machines plug into?

The simplest method is to configure both machine to have the same network such as **[COLOR="Green"]192.168.1[/COLOR]**.0/24.  One of the machines could use 192.168.1.**[COLOR="Blue"]2[/COLOR]** with a subnet mask of 255.255.255.0.  The other could use 192.168.1.**[COLOR="Red"]20[/COLOR]** with a subnet mask of 255.255.255.0.

The 255.255.255.0 makes the first 3 sets of numbers the network ID (green) and the last number (red or blue) the number of the individual computer.  With the 2 computers on the same network they can talk to each other.  Now all you need is to declare the gateway that is also part of that network.  This is typically the network side of router that connects you to the internet.

Is this what you had in mind?

---

