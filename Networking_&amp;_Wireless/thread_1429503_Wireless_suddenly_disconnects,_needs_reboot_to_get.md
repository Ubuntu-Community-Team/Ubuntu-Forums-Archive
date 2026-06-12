---
title: "Wireless suddenly disconnects, needs reboot to get back online."
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by SimenMM on 2010-03-14
I'm running a very fresh install of Karmic, 64bit. I connect to the internet via a wireless connection and have done so from the same computer running Windows 7 as well as other Linux-based laptops in the same location in my house without any problems, so I'm sure the signal is strong enough. After being online for a while (ranges from 15 minutes to three days) my computer disconnects from the network. It then refuses to reconnect to any wireless network unless I first reboot. Ifdown + ifup does not do the trick, neither can I disable and enable networking by right clicking the network manager applet. This may or may not happen only when I run Transmission, I'm not entirely sure about that yet. Where might the problem lie?

---

### Post by helgman on 2010-03-14
This might not be a solution but the next time you loose your connection, try to open a Terminal (Applications - Accessories - Terminal) and then type
```
sudo service network-manager restart
```
I have a similar problem with one of my machines, but that computer refuses to connect to the wireless altogether without restarting the network-manager.

Regards,
Helgman

---

### Post by SimenMM on 2010-03-14
I just tried that, afraid it didn't help. Network manager still showed no available networks. Good news, though, I'm sure it's related to Transmission now. I ran it for five minutes after hours of uptime, and my network died.

---

### Post by FuManShu on 2010-03-14
I experience the same thing except only when I'm Tethering through my iPhone.  When I connect to a wireless network it works fine.  Transmission instantly kills the tethered connection.

---

### Post by SimenMM on 2010-03-15
That's a pretty silly feature for a network app to have. Any known fix?

---

### Post by SimenMM on 2010-03-15
Seems it's not entirely Transmission dependent after all, although Transmission seems to trigger it. I just had it happen again without running any BT client. Also, I saw a post on the Transmission forum stating that this is a bug somewhere outside of the client.

---

### Post by Meneldir on 2010-03-29
I'm having the same problem, but it doesn't have something to do with Transmission in my case, since I open it once or twice a week. But I have to add to the issue, that if I have Rhythmbox running, it dies faster (or so it seems -it's a guess, since I did not do any statistic analysis-). Also, a symptom that I see before death :P, is that the PC starts to do mini hangs¹ (like when the processor is being used to its maximum ), specially the music.

I'm using Karmic Koala, and:
[FONT=Courier New]$ lspci | grep Network
06:00.0 Network controller: **Atheros Communications Inc. AR928X** Wireless Network Adapter (PCI-Express) (rev 01)[/FONT]

[1] Sorry for this, but I don't know the translation to english of what I want to say, if anyone knows, it's "La PC se empieza a trabar".

---

