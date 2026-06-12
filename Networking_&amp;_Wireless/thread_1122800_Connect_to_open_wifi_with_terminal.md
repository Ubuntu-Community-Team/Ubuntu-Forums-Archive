---
title: "Connect to open wifi with terminal"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by BlueWolf_ on 2009-04-11
I'm trying to connect to an open wireless network with the terminal. I've searched all over the web and found all kind of solutions that all worked out for other, but not for me.

I'm already connected to an (encrypted) network, so first I did:
```
sudo ifconfig wlan1 down
sudo ifconfig wlan1 up
```
And than I tried what everybody did:
```
sudo iwconfig wlan1 mode managed essid FON_Lapetus
```
Nothing seems to happen. iwconfig shows me all the information of the previous network(Encryption key, etc), except for the ESSID(Fon_Lapetus) and Access Point(Not-Associated). I also tried to specify the ap with:
```
sudo iwconfig wlan1 ap xx:xx:xx:xx:xx:xx
```
But that results in the same 'Not-Associated'.
I searched for different commands, but this seems to work for everbody. Am I missing something?

---

### Post by BlueWolf_ on 2009-04-15
bump

---

