---
title: "How do I change the DEFAULT network interface"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by paul.prinsloo on 2009-09-29
I would like to be able to decide which interface should be the default (wired or modem, in my case) The reason for this is that I sometimes lose my DSL connection, which means I use a phone modem during those periods. The PC is connected to a hub, s as far as he is concerned, the wired network is available.

thanks a lot for any help.

no.. I don't want to pull out the Lan cable..  there must be a way to specify easily which interface is default.

---

### Post by Jonners59 on 2009-09-29
Me too, and also identify device details too, such as Driver, MAC/Physical Address, Make and Model.....

Seems limited or diffuicult in Ubuntu

---

### Post by i.r.id10t on 2009-09-29
When you connect via the modem it should set your default route to it...

---

### Post by paul.prinsloo on 2009-09-29
Let me try and rephrase..  the Eth0 connection to the LAN is stilla ctive and set as the default. I can establish another connection using the usb phone/modem at the same time, no problem, I can see it is connected, I can see the IP adresses and all. BUT.. the ETH0 wired connection is the default and stays the default. Only once I pull out the lan cable does the wireles connection become the active/default one.
I would like to tell the system to use the wireless connection instead of the wired conection when it suits me, without pulling out cables and stuff.
thanks

---

### Post by Iowan on 2009-09-29
Are you configured via Network Manager, or */etc/network/interfaces*... or something else? You might be able to "down" the interface via **ifconfig** or **ifdown**, but it might immediately get restarted... but give it a try.

---

### Post by paul.prinsloo on 2009-09-30
I am a newbie.. so whatever the desktop edition does by default is what happens.. anyway, I have disconnected the ETH0 from the network manager, and it restarts straight away as the default interface.
Thanks for the reply.

---

