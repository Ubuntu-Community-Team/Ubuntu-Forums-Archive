---
title: "Xp is a pain in the rear!!"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by Ceiber Boy on 2010-02-02
Hello everyone

i'm trying to connect to an XPpro machine using terminal server, i've beem to the microsoft web sight and configured xp as they explain. which consists of "allow remote desktop connections" and "re configure the fire wall", Done.

i've obtained the ip address of the router and the user name and password of the xp machine and STILL I CAN NOT ACCESS IT!!](*,)

can anyone help

---

### Post by wsonar on 2010-02-02
Can you ping the machine?

---

### Post by Ceiber Boy on 2010-02-02
Sorry to be thick, but is pinging done from terminal server client or somewhere else?

---

### Post by lykwydchykyn on 2010-02-02
Is this a machine on the local network, or on some other network across the internet?  You mentioned the router's IP, that's why I ask.

---

### Post by wsonar on 2010-02-02
it sounds like you want to remote desktop in to your XPpc from your ubuntu box is this correct?

regardless of what type of connection you want to make the first thing to do is find out if you can communicate with the pc if you are on a ubuntu machine you want to go to applications > assesories > terminal

in the terminal window type ping followed by the ip address of the computer  you are trying to communicate with

if it replies you can communicate with it otherwise there is further investigation that needs to be done

---

### Post by Ceiber Boy on 2010-02-02
Correct, i'm trying to access my XPpc from my Ubuntu box via the internet. i did make the mistake first of all when i noted the ip address of the xp machine that it was the local address and not the router address! so when i get the router ip address i'll try and ping it as described in the previous post.

Thanks for your help.

---

### Post by lykwydchykyn on 2010-02-02
Have you forwarded RDP (port 3389) on the router?

---

