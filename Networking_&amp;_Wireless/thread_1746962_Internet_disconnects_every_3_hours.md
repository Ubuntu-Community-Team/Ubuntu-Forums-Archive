---
title: "Internet disconnects every 3 hours"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by nethompson on 2011-05-02
Hey everyone, I have a minor Internet issue. I have a static IP address with the modem acting as a gateway only to my ISP. My Ubuntu server hosts my public IP address and I use pppoeconf to connect. Every 3 hours I lose Internet. I have wrote a short script to reconnect. I doubt that it is my ISP trying to renew that often. Could anyone tell me if it is me or my ISP?

---

### Post by lz1dsb on 2011-05-02
What kind of connectivity do you use? Sorry, but it's not clear to me. You mention a modem and than PPoE. Is it some sort of xDSL connection?

---

### Post by nethompson on 2011-05-02
I apologize for not being clear. The connection is an ADSL. The modem is just there to make the line connection to the ISP. The Ubuntu server is what provides the credentials for the ISP. I hope that makes sense.

---

### Post by lz1dsb on 2011-05-02
There's always a possibility that the ADSL modem has some issues. I had such problem with my connection. So you need to check it out.
Could you give more details about the PPPoE settings. How did you configure it? Did you use the Network-Manager?
Do you see anything in the logs? For example cat /var/log/messages

---

### Post by nethompson on 2011-05-02
/var/log/messages states a modem hangup every 180.4 minutes. My connection is configured through pppoeconf.

---

### Post by lz1dsb on 2011-05-03
Could you post the conf file? Is it each time exactly the same period when your connection is dropped?
When you use your ADSL modem to authenticate you, do you experience the same issues?

---

### Post by nethompson on 2011-05-03
Which conf file do you need? It happens at the same interval every time. I haven't tried through the modem yet, i'll have to give it a shot.

---

### Post by lz1dsb on 2011-05-04
/etc/ppp/pppoe.conf
Just remove the username and passowrd from the file. 
But you should also try to terminate the PPPoE tunnel on the ADSL router directly.

---

### Post by nethompson on 2011-05-06
Anybody got anything on this? I am running Ubuntu 10.04 lts. I could really use some help on this.

---

