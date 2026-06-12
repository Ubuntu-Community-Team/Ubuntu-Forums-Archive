---
title: "Wifi auto-connect on start-up"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by n00bstradamus on 2010-01-27
How does one get the wifi to auto connect upon start up, instead of having to manually select it every time i log on? I think the following script is what i need but im not sure where i would even need to install it. Automatic WLAN Picker Script - [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo#Automatic%20WLAN%20Picker%20Script](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo#Automatic%20WLAN%20Picker%20Script)

---

### Post by adam814 on 2010-01-27
I just edited the connection preferences in NetworkManager to get mine to connect as soon as I log in.  If that's good enough it's easier than messing with scripting things manually.

---

### Post by akand074 on 2010-01-27
If I remember correctly, just right click the network manager and choose "edit connections" and go to the "wireless" tab, find the network you use and choose "edit" and it should be in a check box at the bottom I believe.

---

### Post by Light-kun on 2010-01-29
> **akand074 said:**
> If I remember correctly, just right click the network manager and choose "edit connections" and go to the "wireless" tab, find the network you use and choose "edit" and it should be in a check box at the bottom I believe.

I wish if it work..

This checkbox is marked, but wifi doesn't connects automatically.
I must click on wireless manager tray icon (no networks found), click refresh (my net found) and click to the "Connect" button.
It happens everytime after reboot.

---

### Post by akand074 on 2010-01-29
hmm, try a new network manager, I would recommend "wicd". Download it from the repositories (synaptic package manager) or type this into the terminal:

```
sudo apt-get install wicd
```

---

