---
title: "Connecting to the wireless network - problems"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by bartek.baran on 2011-05-09
Hello. I have done in your home Wifi network. The router provides internet to my notebook. I used to display a prompt to me, probably the key to it except to accept or to call. Sorry accidentally pressed the "cancel". And it's probably from that moment on I have huge problems with connecting to the Internet. 

My computer can not connect to my network, so a few moments later, disconnect. And so a few or more times. It can be written, that combined, and the Internet did not exist. Sometimes, however, to connect and the internet is all the time. 

But this is not normal that when turning on the computer displays a prompt "Please enter the password for the keyring" Default "," where I have to type the password for the keyring. By clicking below can be set to the log base was unlocked, but it apparently does not work. Often, usually several times, asking me to "authentication required in wireless networks," where I need to confirm the password for the network. How to avoid this, how to connect to without a problem? It can also display a prompt: "Connection failed: incorrect password", but it is less likely. 

I have the Network Manager and Wicd. I tried installing Wicd from scratch, as Network Manager. It did not help. Restart the router or the system does not always help. Upgrading Ubuntu from 10.10 to 11.04 did not solve the problem. 

The signal quality is OK. Rather, it is certainly not that the problem lies. Sure, it lies in some network settings. How can I get a final solution was not a disk format. 

Please help, because it is not cool when you sometimes have to struggle with a combination of several, a dozen or even dozens of minutes! It's wasting my time. 

If something is confusing, ask for forgiveness. I'm Polish and I use the translator.

---

### Post by uncaspi on 2011-05-09
Try to remove network-manager
sudo apt-get remove network-manager

---

### Post by bartek.baran on 2011-05-10
Completely? I tried once to remove and install again ... So remove the network manager and try to use only the wicd?

---

