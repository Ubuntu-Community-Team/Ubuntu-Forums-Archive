---
title: "need help sharing connections with ubuntu and XP"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by Hyper Tails on 2008-12-21
Hi I have an old pc running xp pro sp2 and I want to use my laptop to connect the basement pc to the internet and every time i do that it says limited or no connectivity
and it kepps failing on my laptop too

HELP.......

---

### Post by chrisinspace on 2008-12-21
Are you trying to use your laptop as a gateway for your XP desktop?  How do you have things cabled?  Or are you using wireless?

What's failing on your laptop?  Your internet connection?

---

### Post by Hyper Tails on 2008-12-21
I'm trying to connect my lptop to the internet via wifi and share that connection with the basement pc
by ethernet

---

### Post by Hyper Tails on 2008-12-21
time for a bump

---

### Post by Iowan on 2008-12-21
Probably not what you're looking for, but [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page. Toward the end is another [link]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") on wireless sharing.

---

### Post by chrisinspace on 2008-12-22
The first step will be to get the wireless on your laptop working.  Can you get to the internet from your laptop?  If not, tell us more about the problem you are having there.  Is Ubuntu seeing your wifi card?  If so, is it picking up your wireless network?  If it's seeing the network, can you connect?  If not, are you getting any error messages?

---

### Post by Hyper Tails on 2008-12-22
my laptop is getting the wireless singnal from my dad's router and My laptop has the internet and now i connected my basement pc and laptop by ethernet and giving the basement pc aucess to the internet

and yes my wireless card works on my laptop

and i keep getting disconnected from both pc's

---

### Post by Hyper Tails on 2008-12-23
Time for another bump

---

### Post by dnoyeb on 2008-12-23
Yes, your wireless is working sortof.  That message is an indication that the wireless has connected, but has not received an IP address from the DHCP server.  Probably means your laptop is not providing the proper authentication information to the wireless gateway.

---

### Post by chrisinspace on 2008-12-29
If you're connecting to the router via wireless and the desktop via ethernet, then you need to follow the instructions at the link Iowan provided to you.

If you're constantly losing the wireless connection, you could have a bad signal or the driver for the wireless card could be flaking out.  You could try to reinstall the driver, or if you haven't already, try using an ndiswrapper in conjunction with a Windows driver.

---

