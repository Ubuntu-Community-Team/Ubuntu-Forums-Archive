---
title: "Can only connect to wireless router with EITHER XP laptop or Ubuntu PC"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by DanH860 on 2010-10-23
Hi,

I've got a network issue that someone might be able to help with - I live in a building where the internet is already provided via a LAN socket in each room. 

To allow my laptop (with xp) and PC to simultaneously through the single socket, I've been using a Netgear WGR614 wireless router that has the wireless SSID & password configured but has DHCP turned off.

This setup has been working until recently where I can now only connect with one computer. If the PC is connected, the laptop will connect to the wireless network but then there will be 'limited or no connectivity'. The same happens if I use a LAN cable between the router and laptop.

To get the laptop to connect, I need to disconnect the PC and then reset the router. Additionally, when my laptop does connect ok, my friends laptop (with XP) can simultaneously connect to the wireless and run fine.

Can anyone suggest where I'm going wrong?

Apologies for the lengthy essay-type question(!), Dan

---

### Post by zarqoon on 2010-10-23
Have you checked that both computers use a different ip Address?
Also depending on the setup in your building you may only be allowed to use a preset range of ip addresses. 
Do you only use the switch part of the router or does the traffic pass through the routers nat?
Using only the switch part could cause all kinds of problems for your whole building network if it is only set up to allow one client per lan port.

If you building Lan port is not connected to the wan/dslmodem port of your router its a safe bet you are only using the switch part.

---

