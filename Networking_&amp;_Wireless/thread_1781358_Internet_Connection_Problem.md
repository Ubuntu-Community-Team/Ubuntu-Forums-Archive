---
title: "Internet Connection Problem"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by digyourpc on 2011-06-13
Hello, I am completely new to ubuntu, got fed up with windows, so thinking of switching to ubuntu :p. But, I have a problem, I don't know how to connect to internet in ubuntu.

I have a cable broadband connection, and I have to put in my user id and password which I got from my isp before each internet session on the login page. 

Please guide me how can I connect to the internet. I am using ubuntu live boot from my pen drive.

Thanks

---

### Post by JethroGillgren on 2011-06-13
Hi

Follow either this if you are using ethernet[https://help.ubuntu.com/11.04/ubuntu-help/net-wired-connect.html]("https://help.ubuntu.com/11.04/ubuntu-help/net-wired-connect.html")

or this for wireless [https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-connect.html]("https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-connect.html")

That should get it up and running, if anything dosen't work you'll have to post as much info as you can find so we're not fishing in the dark.

Good Luck!

---

### Post by superduperlinuxperson on 2011-06-13
the internet is on the top bar on your computer; it should be either a set of concave bars or four strait bars

---

### Post by digyourpc on 2011-06-13
> **JethroGillgren said:**
> Hi

Follow either this if you are using ethernet[https://help.ubuntu.com/11.04/ubuntu-help/net-wired-connect.html](https://help.ubuntu.com/11.04/ubuntu-help/net-wired-connect.html)

or this for wireless [https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-connect.html](https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-connect.html)

That should get it up and running, if anything dosen't work you'll have to post as much info as you can find so we're not fishing in the dark.

Good Luck!

Followed this tutorial, [https://help.ubuntu.com/11.04/ubuntu-help/net-wired-connect.html](https://help.ubuntu.com/11.04/ubuntu-help/net-wired-connect.html)
but still not connected to the internet:(

These are my working internet settings in windows 7
Ip address: 172.19.0.19
Subnet mask: 255.255.0.0
Default gateway: 172.19.0.1

These are the settings I put manually by following the tutorial,
Address: 172.19.0.19
Netmask: 255.255.0.0
Gateway: 172.19.0.1

Now, after saving the changes when I open my browser, the login page is not opening, so I can't start my internet session.

My connection is wired dsl cable broadband connection, I have to login with my user id each time before every internet session and it doesn't automatically assign network settings. Also, my connection don't use router/modem.

And, I am running ubuntu 11.04 from my pen drive, I still haven't installed ubuntu on my hard disk, will install it after I manage to run internet in ubuntu.

---

### Post by dineshs on 2011-06-14
Can you try this?
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)
If you run ```
ipconfig /all
```in windows what do you get?Pl post result

---

### Post by dandnsmith on 2011-06-14
I'll hazard a guess that the problem is invoking the login dialog - it's pointless manually setting the IP address and routing, as this will normally get done after you've successfully passed the logon stage (probably DHCP - look at the Win settings to verify this).

I've never had a cable connection, so am guessing, but I do know that they often recognize the MAC of the connecting interface, and there must be a script to run (which you may have had on a CD, with installation instructions). It's likely that it is geared to Windows, and that you need the parallel stuff to use linux - first line of attack is to talk to your ISP.

---

