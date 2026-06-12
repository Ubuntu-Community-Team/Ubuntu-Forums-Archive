---
title: "no device in network manger"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by tronica on 2006-06-23
i've been using my wireless card fine since i installed dapper.  So i thought i would try network-manager applet. well it says "No network devices have been found". This is odd since my wireless card works fine. can anyone help me getting to work.

---

### Post by hod139 on 2006-06-23
Not sure if this is the best solution, but I was having similar issues and this is how I fixed it.
Go to System->Administration->Networking
For both the wireless and ethernet connections, select properties and uncheck "Enable this connection"
Restart.


If there is a better solution, I would also like to hear it.

---

### Post by tronica on 2006-06-23
ok that worked to a point. when tried to connect to my router through network manager applet it would let me connect, it would just sit there. I tried entering my hex key several times and no go.

---

### Post by hod139 on 2006-06-26
Are you using WPA or WEP security?  There seems to be lots of issues with WPA.

You can also run ```
nm-tool 
```
for debugging analysis.

---

### Post by linuxNewb on 2006-06-26
I have the same problem. I use WEP. Since it wasn't working, I tried to turn it off, but I still couldn't get wireless working again. Then I uninstalled the network-manager-gnome, and enabled the wireless connection again on the original network tool, but it won't work. I now cannot connect at all. I'm on windows right now, this sux.

It might have something to do with orinoco drivers, but I have no idea what to do. At [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware) it says:

"Supports unencrypted, WEP, WPA, and WPA2 networks. Be aware that if you have both this driver and the 'orinoco' driver installed, they may fight for control of the wireless card and render it inoperable to NetworkManager. You should either disable one of these drivers, or ensure that only one driver is able to control the card."

---

