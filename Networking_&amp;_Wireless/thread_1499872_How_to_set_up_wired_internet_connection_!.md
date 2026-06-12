---
title: "How to set up wired internet connection ?!?"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by pan4o16 on 2010-06-02
Hello :)

I have BIG troubles trying to set up wired internet connection in Ubuntu! To be able to connect to the internet I have to enter my MAC address, 2 IPs, netmask and 2 DNS address. When I try to edit the default internet connection eth0 with my correct information, the minute I enter my MAC address and save the changes the network manager creates new internet connection with wrong data and use it instead! I can't select the correct internet connection from the top bar ( I have no idea whats the name of that bar! I am kinda new to Ubuntu) where the internet icon is, because it is just not there. The only connection that I can choice is the new default one with the wrong data! If I try to create new separate internet connection with my correct data the same thing happens! The moment I enter my MAC address and save it, the internet connection disapears from the list of internet connections in the internet area in the top bar and I can't select it. I tried googling it, but with no luck :( I think that if I set up my connection trough the terminal everything will be ok, but I have no idea how to do that :D 
PLS HELP ME!

---

### Post by leclerc65 on 2010-06-02
I hook the wired internet cable BEFORE putting the install CD in. If Ubuntu (or any distro) that doesn't get the time (from the time servers) right , I won't even bother to continue . 
As of up to now , I never failed to get connected no matter how old the hardware is .
Wireless is another matter though.:(

---

### Post by Iowan on 2010-06-02
Not a long-term solution, but try (from terminal) **sudo dhclient eth0**

---

