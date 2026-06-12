---
title: "Printer sharing problem"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by kurotsuno on 2010-03-06
All my pc's are running ubuntu 9.10 64 bit I've got the printer installed on the pc downstairs and have set it to be shared. Incase its the firewall I've added the ips to the respective firewall's but it doesn't seem to pop up. 

Am I doing something wrong ? or missing something in regards to setting it up. I did follow the network printer guide that I found from the ubuntu help section.


Edit: To add to this I've included port 631 as well through the firestarter GUI. Still not seeing any sign of it being detected. My only guess is it could be a network issue I tried pinging the pc downstairs didn't get any response. I know I have added my ip to be allowed a connection to that pc and vice a versa so not sure what I'm neglecting to over look.

Router is a belkin N type wireless printer is a canon ip2600 force installed 32bit drivers (because there are no 64 bit ones available) I have set it to be shared and the pc upstairs is set to look for shared printers.

---

### Post by kurotsuno on 2010-03-07
Tried everything from the guides I found online and still no luck so if someone could help it really could be great.

Other than what the guide says and the port I added to the firewalls I don't know what else I could do to get this working.

I have tried searching but I keep getting topics dealing with sharing printers with windows or macs which isn't what I need but I try what they suggest with no luck.

---

### Post by kurotsuno on 2010-03-07
Just did a quick test I am able to connect to the pc downstairs through cups in a browser

[http://192.168.2.2:631/](http://192.168.2.2:631/) and it lists the printer

managed to add it as a ipp printer but it needs autentication ? what do I put in to get it to print ? the password for downstairs ?




Solved my issue you can lock this thread.

---

