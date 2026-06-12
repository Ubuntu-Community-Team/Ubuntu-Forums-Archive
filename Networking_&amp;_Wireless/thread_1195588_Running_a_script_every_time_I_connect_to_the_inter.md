---
title: "Running a script every time I connect to the internet"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by nago on 2009-06-24
Hello; I want to run a dynamic DNS update script.
It's a simple script that uses wget to fetch a certain page on zoneedit's site which in turn updates my DNS.

The problem I have is where I put it to run it.

I want the script to run every time I connect to the internet, either through wlan0 or eth0. every time a connection is established, this script should be run.

or, if you can think of a better, more reliable way to run the script, please suggest away.

I had though of putting it in /etc/network/if-up.d/ but this doesn't necessarily run when wireless connects or disconnects, so it isn't really appropriate.

---

### Post by Brandon Williams on 2009-06-24
Try putting your script in /etc/NetworkManager/dispatcher.d/. Make sure that the name of the script causes it to be run after /etc/Networkmanager/dispatcher.d/01ifupdown by giving it a name starting with 02. Take a look at /etc/Networkmanager/dispatcher.d/01ifupdown to get an idea of how to interpret the arguments that will be passed in so that you only take action on the up events.

---

### Post by geirha on 2009-06-24
You'll find [ddclient](apt://ddclient) in the repositories. When you install it, it will ask you the required information; service, domainname, username and password, and which ethernet device to use.

---

