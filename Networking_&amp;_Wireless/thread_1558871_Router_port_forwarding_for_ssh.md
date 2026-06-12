---
title: "Router port forwarding for ssh"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by bellboa45 on 2010-08-22
Hello, I am experimenting with open ssh and I am trying to set up an ssh server at home. I have logged into my router and set up port-forwarding on port 22. I can log into the machine fine from a machine on the local network using the machines internal IP but when I try to log on from a remote machine using my router's external IP or my DyDNS host-name I get a message saying "connection refused" or "connection timed out." I have configured port-forwarding on the router and the firewall rules says that port 22 is open but when I nmap my routers external ip it says that only port 23 and 80 are open. I am very new to linux and networking, thank you to anyone who can help me or point me in the right direction.

---

### Post by gordintoronto on 2010-08-23
You have a router problem, it might help if you told us the brand and model of router. Also, what steps you took to set up the port forwarding.

It is possible your ISP (who?) is blocking the connection, you might want to read their terms of service.

---

### Post by silbak04 on 2010-08-23
What is your output of ```
sudo grep Port /etc/ssh/sshd_config
```...regardless this should not be a problem, because the default port is 22 which should be set in your sshd_config file, I just want to make sure it's not commented out or anything

---

### Post by bellboa45 on 2010-08-23
The model of the router is a siemens gigaset se567. its a dsl modem and router all together. the service provider is telus. As for port-forwarding, i followed the tutorial I found here [http://portforward.com/english/routers/port_forwarding/Siemens/Gigaset-SE567/SSH.htm](http://portforward.com/english/routers/port_forwarding/Siemens/Gigaset-SE567/SSH.htm) . I'm going to call the isp tomorrow and see if they are blocking it. Is it sense-able to think that they would be willing to unblock it?

---

### Post by amauk on 2010-08-23
Have you tried rebooting the router?
possible it needs rebooting to pick up the changes

If for some reason, port 22 is blocked by your ISP
You can also configure SSH to use a different port
anything above 1024 should be fine

---

### Post by bellboa45 on 2010-08-23
Thank you all who have responded. I have changed the sshd config file on the server to listen on port 1025 and have changed the port forwarding rules on the router set up. the firewall rules on the router set up page shows that port 1025 is open and forwarding. I run nmap localhost on the server and it shows that port 1025 is open. When I nmap my local router it still show only port 23 and 80 open, but, when I specify port 1025 (namp -p 1025) it reads that port 1025 is filtered. I have googled around but cannot find out exactly what filtered means or how to correct the issue. any ideas?

---

### Post by amauk on 2010-08-23
You need to try SSH'ing from outside your network
The port forwarding on routers routes traffic from outside to a machine on the inside

Queries to the router from inside will not be forwarded

Either nmap your external IP from a machine outside your network, or ry something like [shields-up](https://www.grc.com/x/ne.dll?bh0bkyd2) (which is just a web-based port scanner

```
                          |
                          |
               /----------|-------------\
               |        ROUTER          |       <--\ Packets from inside network are not routed
               | external | internal    +-------\  | Port 1025 will not be routed to 192.168.0.10
------->       | <ext-IP> | 192.168.0.1 |       |  | instead it'll go to router itself
Incoming       \----------|----------+--/       |  |
packets from              |          |          |    
outside are                          |  /-------+------\
routed                               |  |   internal   |
Port 1025                            |  |   machine    |
Will be routed                       |  | 192.168.0.11 |
to internal machine                  |  \--------------/
192.168.0.10                         |
                                   /-+------------\
                                   |   internal   |
                                   |   machine    |
                                   | 192.168.0.10 |
                                   \--------------/
```

---

### Post by bellboa45 on 2010-08-24
thank you amauk. your explanation was great, it was very clear. I can log on to the machine if I connect to a different router! now, my server is in the basement hooked up to my switch. lets say i am in the garage or backyard on my laptop connected to the router/modem via wifi and i want to connect to my server downstairs via ssh. is this possible? if i just want to access files is the answer to look into setting up a samba or nfs share? again, thank you to all who have answered.

---

### Post by bellboa45 on 2010-08-24
why don't you just ssh to the local (internal) ip address? derp! man i am stupid. thanks once more to all who helped! i think this issue is closed.

---

### Post by hotdoog on 2013-02-26
I had this same router and it is buggy. I would set it to forward a part to a static IP but it would never save the settings. My solution was to get the ISP to give me a different better router. In my case the ISP was Telus and that router is the cheapest one they have but they will give you a different one if you ask because they know it is a buggy unit if you try to do anything besides plug it in.

---

### Post by sandyd on 2013-02-26
**Necromancing - thread closed**
Please do not post in threads more than one year old.

Thanks!

---

### Post by QIII on 2013-02-26
Thank you for your input.

This is a very old thread.

I'm putting it back to bed.  :)

---

