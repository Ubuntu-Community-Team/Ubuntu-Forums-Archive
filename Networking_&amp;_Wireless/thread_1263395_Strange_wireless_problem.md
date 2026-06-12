---
title: "Strange wireless problem"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by MrSergeiMosin on 2009-09-10
A few days ago I had need to share a single internet connection. I used my laptops hardline and configured my ubuntu jaunty build to performas a wireless access point. I didn't try the internet between then and today, but now it won't load web pages.

The computer still connects to the wireless access point just fine. Iwconfig gives me the name of the access point, and all other information just as it always does. I can't find anything out of the ordinary, at least. However, when I try to use firefox or any other web browser, I get an error message similar to the one you get when you aren't connected at all (firefox can't find the server). The only thing that seems different is an additonal line in the error that says I should check my network (definitely not, other computers connect) and my DNS server settings. I followed a tutorial to share my web connection. Does doing this usually involve changing DNS settings?

Basically, the computer connects to the internet. It just doesn't realize it can browse, I guess. Any ideas?



Any ideas?

---

### Post by cariboo on 2009-09-11
Can you ping by name?

```
ping www.google.com
```

If not try by number:

```
ping 74.125.127.147
```

If you can ping by number and not name, you have a DNS problem.

---

### Post by MrSergeiMosin on 2009-09-11
Pinging [www.google.com](www.google.com) doesnt work, but pinging the IP address does.

---

### Post by Bucky Ball on 2009-09-11
If you are running a static IP on the local box you do need to have the correct DNS ips in there.

---

### Post by MrSergeiMosin on 2009-09-11
I dont remember if i set up a static ip or not. If id had any sense, I'd have backed up everything I edited. How would I go about discovering if I have a static IP?

---

### Post by Bucky Ball on 2009-09-11
System->Admin->Network, unlock, properties; but if you don't remember doing it and need to know where to find, probably didn't. Good idea to have a look in there and get familiar anyhow. :)

(Should have the correct DNS server ips there under the 'DNS' tab.)

---

### Post by MrSergeiMosin on 2009-09-11
Right on that one. When I changed what I changed, it was all done from the terminal. Definitely didnt change anything using menu links. Seems like I changed /etc/network/interfaces and /etc/dnsmasq.conf. Any way to tell if these two are configured correctly?

---

### Post by MrSergeiMosin on 2009-09-11
I'm updating this from a liveboot of the same OS I have on my 'puter. all of it worked before i changed anything. Would overwriting the related files with the ones from the install/live cd possibly solve the issue?

---

### Post by Bucky Ball on 2009-09-11
Could you post a link to the tutorial you used?

---

### Post by MrSergeiMosin on 2009-09-11
It was this tutorial:

[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

although i also had this one open and can't promise there wasnt some cross-contamination happening...

[http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html](http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html)

I should note, though, that even before I edited files my /etc/network/interfaces only contained the following:

[INDENT]auto lo
iface lo inet loopback
[/INDENT]

---

### Post by Bucky Ball on 2009-09-12
Maybe take  /etc/network/interfaces back to what it was originally and take it from there.

---

### Post by MrSergeiMosin on 2009-09-12
/etc/network/interfaces file is the same as it was before. It only contained those two lines when I opened it the first time.

Should I maybe try adding the things that the tutorial shows the /interfaces to contain, or just leave it be?

---

