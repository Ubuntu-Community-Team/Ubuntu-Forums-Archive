---
title: "Wired/Wireless Connection not working Realtek/ Broadcom"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by AdamE628 on 2009-10-04
I just installed Ubuntu 8.04 on a Compaq Presario Laptop and I can't connect to the internet through wireless or LAN.

the Hardware Testing recognizes my two network controllers:

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Then after the internet Test it says "Internet connection fully established"

But my browser can't connect with any websites.  Likewise the ping works fine, but I can't figure out what else to do.

When the computer starts up and the ethernet cable is connected, it attempts to connect, shows one blue dot, but then fails.  

Any help on this?  I'm sort of a newb at linux :/

---

### Post by Metaljaz on 2009-10-04
To get you wireless working try this:

Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. (this will extract the broadcom 43xx firmware) Mark for install and then apply.

If its not there try this from the terminal window:
(Make sure you are using a wired internet connection)

sudo apt-get update
sudo apt-get install b43-fwcutter

Then Go under System > Administration > Hardware Drivers and make sure the driver is activated. If it is activated in the top right hand corner look for the icon for wireless internet connection. Click on the connection to use it.
Make sure you unplug your wired connection.

---

### Post by AdamE628 on 2009-10-08
Thanks for your response.

My problem is that I can't get any type of internet connection at all.  I think If i could be connected at all I could fix the wireless connection.  But the even the ethernet connection is not being  recognized by the computer.

---

### Post by AdamE628 on 2009-10-08
Just for further clarification the computer is recognizing the drivers. Under the Network tools manager, it shows three network devices:

Loopback Interface (lo)

Ethernet Interface (etho0)

Ethernet Interface (eth0: avahi)

But loopback Interface (lo) is the default one and the only one that is shown to be sending and receiving packets, although the number is minimal.  (80.2 KiB sent and received).

And when I ping the network address it works fine so, I'm really confused.  But I've read that there are a lot of problems with this set of hardware so...

---

