---
title: "Wireless sometimes disconnects and doesn't connect"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by abdusamed on 2011-03-09
hey

I facing a really annoying problem. I download regularly during the night using Wifi. The problem is that because I'm away, the wireless just disconnects and the pop window shows up asking me to into the password. The password is already saved in the windows so I just have to click 'connect'

But I don't understand why does it disconnect and when it tries to connect it asks for password again! Why doesn't it simply 'try' to connect without asking the password when it is already saved.

I have the connection set to automatically connect and password safe. 

bye

---

### Post by grahammechanical on 2011-03-10
What is causing the disconnection? I suggest that you think about that. Sometimes a connection to a web site will break and we become disconnected from that web site and have to click Reload but Network Manager is still connected to the router which is still connected to the ISP.

Something is breaking the connection to the router. Is the machine going into a power saving mode? What power saving settings do you have in the BIOS? If the computer switches off the wireless adapter to save power then it could be that the request for a password is also a request to activate the wireless adapter. And not simply to connect to the router.

Regards.

---

### Post by abdusamed on 2011-03-13
It just started happening recently with everything else the same. I have to pay attention to my notebook al the time but when I leave, after a few while the connection just disconnects and doesn't retry. All it does is ask me to enter password which is already saved!!!!!!!!! arrrg


its suppose to reconnect when it disconnects.

---

### Post by Shriner on 2011-03-13
My problem was the wireless was set to use power saving.

Check with "iwconfig"

Disable with "sudo iwconfig wlan0 power off", assuming that you are using wlan0.

---

