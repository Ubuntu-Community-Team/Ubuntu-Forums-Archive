---
title: "Lucid Wireless and IPv6"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by kajer on 2010-04-30
I have finished upgrading most of my boxes to Lucid, however I have one major problem. All my boxes on wireless do not get an IPv6 address. If I plug in Ethernet, nothing. 

Wireshark can see my router advertisements, but no luck getting the adapter to bind to said address. I even turned down my RA's to every 3 seconds, no luck.

I know most of you are IPv6 haters, but I am looking for help. Trust me, I have searched, and found nothing but how to disable IPv6 and other people whining about how IPv6 is slowing their DNS queries by .00034 seconds.

I have a working IPv6 configuration, 9.10 worked and STILL works flawlessly, I would like 10.04 to do the same. Thank You

---

### Post by kajer on 2010-04-30
UFW was the problem. Turns out people who hate IPv6 turn it off by default, and inhibit functionality the rest of us are trying to use. this is why we can't have nice things.

SOLVED - UFW hates IPv6

---

### Post by inox84 on 2010-05-02
UFW is IPv6 aware firewall!

Go:

/etc/default/ufw

and set:

IPV6=yes

Then recreate your rules with gufw. V6 ports will be added automatically.

Cheers. :)

---

### Post by kajer on 2010-05-03
see, this is what I am talking about, why have a firewall that can handle BOTH v4 and v6 and NOT enable v6?

---

### Post by inox84 on 2010-05-07
Now I got the point:)

I was trying to find a solution to my problem...

[http://ubuntuforums.org/showthread.php?t=1469361](http://ubuntuforums.org/showthread.php?t=1469361)

...,but Google returned "How to disable IPv6"-only tips:P

---

