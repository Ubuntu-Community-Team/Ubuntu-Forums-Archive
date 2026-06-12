---
title: "Cant seem to open port 22 for unbuntu on my router"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by onemoretime on 2009-03-13
hey i know its a stupid question cause ive done this before , but i cant seem to get my router to open port 22 to my machine so i can ssh/telnet to it. i am using a  siemens speedstream 6520 wireless router from Aliant/Bell. I opened DMZ to see if that would help incase there was a firewall. still no go though. Only option it gives me is port mapping other then this which i have choosen ftp for the name and protocol i have choosen TCP , so it shows up as ftp/21 even though i choose 22 for the port. I have clicked teh redirect selected protocol/appliciation to ip adresss too where i have put the ip address the computer has on my network. for example if this computer is 192.168.2.1 , and my linux box is 192.168.2.2 i have put 192.168.2.2 for the redirect ip. I have also attached a picture of what i can see at my options for port mapping.


Any help on this at all would be very thankful. thanks for your time.

---

### Post by onemoretime on 2009-03-13
nevermind guys figured it out. thanks anyways.

---

### Post by hiko2 on 2009-05-05
I have the same problem you had, if you please post the solution you find or a link it would be great, thanks.

---

### Post by cariboo on 2009-05-06
When setting up port forwarding, it is always best practice to set a staic ip address on the computer you are port forwarding to. To check if the port is open on your router or if your isp is blocking any ports, try [canyouseeme]("http://www.canyouseeme.org/").

---

