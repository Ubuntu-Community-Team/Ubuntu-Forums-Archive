---
title: "VNC On Ubuntu 8.10 [TightVNC Problem]"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by Max Avion on 2009-04-19
Hello,

I am having some headache getting a VNC server on my Ubuntu 8.10 Desktop. I tried to install TightVNC 

```
$ sudo apt-get install tightvncserver
``` 

When I did this I got a message like "Desktop 1 Active and then the log location" 

I also tried using the HTTP Port command as I have installed Ubuntu along side windows and from the gateway interface both sides have the same ports forwarded so wanted to use the same ports and my VNC server on Windows. 

Doing both of these thing I did not seem to accomplish what I was trying to do, instead I got Desktop 2 and then desktop 3 (could not see any of them) and then heard the Ubuntu startup sound each time. 

Anyways, I really need some help getting a VNC server on installed on Ubuntu, assume that you are instructing an complete idiot.:-) 

When I installed TightVNC I would have preferred some GUI and not the terminal to begin so I uninstalled it.   

Thank you very much in advance.

Regards,

Max

---

### Post by diablo75 on 2009-04-19
What happens if you try to install this package using synaptic (System>Administration>Synaptic Package Manager)?

---

### Post by superprash2003 on 2009-04-19
what about system->preferences->remote desktop ? from where do you want to access this PC? LAN or internet?

---

### Post by Max Avion on 2009-04-19
Thank you for the reply guys. I did not try doing this from (System > Administrations > Synaptic Package Manager) I am trying to access the VNC server via external IP address not LAN. I did not realize that the built in remote desktop feature worked. I set that one up after posting the message below and was able to access my Ubuntu desktop via VNC viewer. The reason that I wanted to install a 3rd part VNC server is because I would prefer to use Java and access my desktop via HTTP. Does anyone know if I can add the Java feature to my existing connection. 

Many thanks for the replies. I do appreciate it. 

Regards,

Max

---

