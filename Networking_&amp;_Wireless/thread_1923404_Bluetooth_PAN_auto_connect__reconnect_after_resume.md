---
title: "Bluetooth PAN auto connect / reconnect after resume"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by fhh on 2012-02-10
Hi there,

just test driving Ubuntu 11.10 and 12.04 and I am really impressed.

However, I would like to use my netbook tethered via bluetooth PAN to my cell phone instead of wifi.

While I easily could do a pairing and create a connection, I could not find out:

1. how to configure network in a way that it connects automatically to  bluetooth PAN whenever there is no other connection and the cell is in  range.

2. how to setup Ubuntu to automatically reconnect via bluetooth after  standby. At the moment after a resume I always have to manually connect  again...

Thanks for any hints!

---

### Post by fhh on 2012-02-11
Alright - solved the issue on my own, here is how I did it:

1.) go to /etc/NetworkManager/system-connections/
```
cd /etc/NetworkManager/system-connections
```

2.) find the file for your bluetooth network, in my case it was "Nexus S Network" - this is the same name that Network Manager GUI shows you, when you manually connect.

3.) edit this file (replace with your network name):
```
sudo nano 'Nexus S Network'
```

4.) find line with "autoconnect" and set to true:
```
autoconnect=true
```[B]

Ready[/B]. Once you manually connected to your bluetooth network, from now on the system will automatically reconnect you after standby and also after shutdown/restart...

---

