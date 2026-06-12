---
title: "Help Starting a Minecraft Server?"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by bGonz on 2012-10-15
I have tried setting one up but i have failed. I would appreciate some help i understand it's a lot and i understand that no one can really help with port fwding.
But i have minecraft 1.3.2 and ubuntu 12.04 if that helps. 
I would really appreciate the help.

---

### Post by draucia on 2012-10-15
Are you having java issues? Or does the minecraft server start but just say "Failed to bind to port:25565" or something?

If it runs fine but can't bind to the port, you have to port forward 25565 (default on minecraft). It actually isn't ubuntu-specific, but router-specific. What router do you have? You will have to go to the router page (192.168.x.x usually) and find a section for port forwarding. Then you would add 25565, your computer's ip (not public ip, yours, so like 192.168.1.125 or similar) and TCP&UDP.

---

### Post by bGonz on 2012-10-15
sorrry for waisting your time. i figured it out. i game my friend the wrong ip.

---

### Post by bGonz on 2012-10-16
okay so my server was going fine but i decided to start a new one and now im having problems with the port binding. i can connect from my local ip but the ip that i gave my friends says it doesnt connect on my computer. i have the port fwding set up, 
Do i need to change ports?

---

