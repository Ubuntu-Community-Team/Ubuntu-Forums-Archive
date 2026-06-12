---
title: "eeepc 1000he/dell inspiron 6000 not connecting to WPA personal wifi network"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by joshbax on 2009-04-05
Hi guys - having a problem connecting my eeepc to my home wifi network. I am using 8.10, downloaded and with the desktop from easypeasy. I would post in their forums, but they are down, AND I have been having exactly the same problem with my dell inspiron 6000 laptop that has worked with ubuntu and wifi for years.

I surmise that it must be something with my network - the eeepc works fine with my network at university. 

basically, i click on the network manager applet, select my wifi network, type in the password, and it just fails to connect. it pops up again a minute later, as if i have spelt the password wrong.

the weird thing is, the 2nd time i tried to connect the eeepc to the wifi, it worked fine. then i tried again in the evening, and no joy. nothing since either. i even removed all encryption and had no joy.

my sister's mac (osx), my dad's thinkpad (vista business) both connect fine. and the printer. so whats in linux thats preventing it?

any suggestions?

---

### Post by joshbax on 2009-04-05
bump?

---

### Post by kreggz on 2009-04-05
What security protocol are u using at home compared to what is at the UNI?

Open
WEP
WPA-PSK
WPA2-PSK
WPA-Enterprise
WPA2-Enterprise

---

### Post by joshbax on 2009-04-06
uni is open but does MAC address filtering.

at home we have wpa2 psk TKIP.

weird thing is, the wifi on the eee worked once last night, and this morning. but also failed twice last night. seems to be so temperamental

---

### Post by kreggz on 2009-04-06
What type of wifi card do you have?

try these commands to find it

lspci
lsusb

---

### Post by joshbax on 2009-04-07
```
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

and I have an intel 2200BG in the dell.

just came to a new house and had more trouble connecting to the wifi using the eeepc. had to do a few restarts to get it connected.

---

### Post by kreggz on 2009-04-08
Is it working correctly now?

[[IMG]http://brainstorm.ubuntu.com/idea/18989/image/2/[/IMG]](http://brainstorm.ubuntu.com/idea/18989/)

---

### Post by joshbax on 2009-04-08
hasn't worked at home for at least 24 hours now. nothing. am trying xubuntu on it, just as a test.

---

### Post by Cyborganism on 2009-12-08
I don't know what the problem is, but in Karmic the problem persists. And YES it is only when using a WPA/WPA2 protected wifi signal that it does this.

What I've noticed is after playing around a lot with the network manager, it sometimes asks for the master password for the password and encryption key system. Sometimes it asks if I want to deny, allow once or allow permanently access to that same password and keys system.

My guess is that there is a bad communication between these 2 systems and the network manager cannot retrieve the wpa passphrase from the password and encryption keys system.

I guess a way around this would be to ignore the password and keys system and just keep the password stored in the network manager app by itself? But how do you do that?

---

### Post by Cyborganism on 2009-12-17
Bump?

---

