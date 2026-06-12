---
title: "networking problem"
date: 2011-11-24
forum: Networking &amp; Wireless
---

### Post by sarahmdht on 2011-11-24
i have ubuntu on my internal server for Moodle, 
all PCs are connected through a switch, there is no internet connection nor router, each PC has its static IP, all PCs can see the server but after about 30 minutes we got the messages "connection time out - takes long time to respond" after refreshing it comes back but all data are lost

is it from Ubunto network configuration, Moodle, networking our PCs? and how to get rid of this?

thanks in advance

---

### Post by ptrakk on 2011-11-24
after it crashes try to ping the server. you can find the ip of the ubuntu server by the command "ifconfig". on another computer i am guessing you have windows. goto start>run>"cmd" then click ok run the command ping <SERVERIP>

---

### Post by sarahmdht on 2011-11-24
thanks for your fast reply,
i already know its IP (192.168.1.100) as we made it static to open Moodle by typing it in the browsers' address bar

---

