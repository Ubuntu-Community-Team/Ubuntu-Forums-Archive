---
title: "Set-up D-link DWL-650+"
date: 2012-01-17
forum: Networking &amp; Wireless
---

### Post by IdanSuper on 2012-01-17
Hey.. I need help. I need help for installing my network card driver D-link model DWL-650+. I found the project of ACX100 but it's not updated. and I don't know how it work and it confusing me... Thank you! for help

---

### Post by chili555 on 2012-01-17
Let's see what you have. Please open a terminal and post:```
lspci -nn
uname -r
```Thanks.

---

### Post by IdanSuper on 2012-01-17
> **chili555 said:**
> Let's see what you have. Please open a terminal and post:```
lspci -nn
uname -r
```Thanks.

[http://paste.ubuntu.com/807569/](http://paste.ubuntu.com/807569/)

---

### Post by chili555 on 2012-01-17
Before we wear ourselves out trying to compile an older driver that might or might not work, let's try ndiswrapper. Can you please temporarily get a wired ethernet connection and do:```
sudo apt-get install ndisgtk
```A few dependencies will also install. Now download the attached file to your desktop. Right-click it and select *Extract Here*. Now, back in the terminal, do:```
sudo ndisgtk
```Click the button to Install New Driver. Point to Desktop > WinXP > AIRPLUS.INF.

After it installs, Network Manager should see your networks. Post back if you need more help.

---

### Post by IdanSuper on 2012-01-17
> **chili555 said:**
> Before we wear ourselves out trying to compile an older driver that might or might not work, let's try ndiswrapper. Can you please temporarily get a wired ethernet connection and do:```
sudo apt-get install ndisgtk
```A few dependencies will also install. Now download the attached file to your desktop. Right-click it and select *Extract Here*. Now, back in the terminal, do:```
sudo ndisgtk
```Click the button to Install New Driver. Point to Desktop > WinXP > AIRPLUS.INF.

After it installs, Network Manager should see your networks. Post back if you need more help.

after installed the driver.. it said hardware present:yes.. is it ok? how to connect to a wifi network?

---

### Post by chili555 on 2012-01-17
Sounds OK so far. Let's have a closer look:```
ndiswrapper -l
iwconfig
sudo iwlist wlan0 scan
sudo iwlist wlan0 auth
```Do you see any networks when you click the Network Manager icon?

---

