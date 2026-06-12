---
title: "Create SSH Tunnel to Run Mythweb"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by brian_hayward on 2009-03-30
Here is my scenario, I just got my mythbuntu box all setup to where i want it.  I want to be able to utilize the Mythweb from afar, but I don't want a user name and password to be my only line of defense between my computer and the bad guys.  Here is what i would like to do; I want to create an SSH tunnel from Computer X to my Mythbuntu box, then i want that secure tunnel traffic forwarded on my Mythbuntu box to the correct ports for Mythweb.  On Computer x i will setup the proxy options on my web browser to connect to my Mythbuntu Box through the SSH tunnel.  From the research I've done it appears that users can add some extra scripting to the SSH command that would make the secure connection and then forward that traffic on again to another port.  I am still pretty green at using Linux, but I am learning, and my next subject is the BASH shell and scripting, but for now i need some extra help writing the script to get this part going.  Any help will be greatly appreciated.  Thanks

---

### Post by coutts99 on 2009-03-30
Try this page [http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Port_Forwarding.html]("http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Port_Forwarding.html")

---

### Post by BkkBonanza on 2009-03-30
You can probably do this with one line,

ssh -D 8080 user@mythbuntu_ip

This creates a socks proxy. Then you tell your browser your'e using a socks 5 proxy at localhost:8080 and it should work from there.

There a nice gui package in synaptics called gstm that lets you do this with no console if you prefer.
If you do this don't forget to make mythweb unavailable to public users otherwise they can still get in without using ssh. ie. mythweb needs to listen only on localhost not on your public interface - that means it will still work for ssh as it is forwarding on localhost.

---

