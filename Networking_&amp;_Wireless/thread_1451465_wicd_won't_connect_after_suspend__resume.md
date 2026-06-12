---
title: "wicd won't connect after suspend / resume"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by Maximus559 on 2010-04-10
I just installed Ubuntu 9.10 Netbook Remix on my Acer AspireOne AO532H netbook, and so far, it's been working beautifully. MUCH better than the Windows 7 starter edition that came with the machine. The only problem I've experienced so far had to do with the wireless connection. Initially, the connection would drop during certain types of activities (e.g. downloading updates or programs, or even streaming Youtube videos) and the network manager would freeze so completely that I'd have to hard reboot. That *seems* to have been fixed by installing wicd (following a suggestion here: [http://ubuntuforums.org/showthread.php?t=1135723&page=2](http://ubuntuforums.org/showthread.php?t=1135723&page=2)), meaning that it hasn't disconnected in the several hours since I've been using it. However, wicd has a different problem: it disconnects after a suspend / resume cycle. This requires a reboot to fix also, as not only does it disconnect, but it looses awareness of the network altogether. Obviously, this could be a real headache on a netbook that gets closed and opened frequently. Any ideas?

---

### Post by SecretCode on 2010-04-10
I have that problem with Network Manager.

Do you have a wifi/radio on-off button somewhere on the netbook? Or a key combination that turns off the wifi? If so, try pressing it, waiting a few seconds, pressing again, waiting ... 

Next thing to consider is 
```
rfkill list
```
If this command shows "Soft blocked: yes" then run
```
rfkill unblock wifi
```

If it's still not happy, kill the process. With Network Manager, this works:
```
sudo killall NetworkManager
```
A similar command should help for wicd.

Other options include:
```
sudo ifconfig wlan0 down 
sudo ifconfig wlan0 up
iwlist wlan0 scan
```

---

### Post by Maximus559 on 2010-04-10
Thanks for the reply. Turns out the solution lay in going back to Network Manager and following the instructions here: [http://ubuntuforums.org/showthread.php?t=1316126&highlight=AO532H](http://ubuntuforums.org/showthread.php?t=1316126&highlight=AO532H)

Works like a charm now.

---

