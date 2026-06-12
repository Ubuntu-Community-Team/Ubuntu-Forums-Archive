---
title: "gammu could not receive SMS after Network Manager has access to Dongle Modem"
date: 2012-05-04
forum: Networking &amp; Wireless
---

### Post by Spoky on 2012-05-04
Since 12.04 I run into several troubles with Dongle Modems. My Issue here is the following. I uses gammu to send and receive SMS. All works fine until NetworkManager get access to the Dongle. A simple 
```
nmcli nm wwan on
```and after this a 
```
nmcli nm wwan off
```and gammu receive no SMS anymore. The only way is to replug the dongle. 
Any suggestions to fix it?

---

