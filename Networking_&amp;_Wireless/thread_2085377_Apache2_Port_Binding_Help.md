---
title: "Apache2 Port Binding Help"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by Skullxbagel on 2012-11-18
Hey, I'm just starting to use Apache in general, and I was trying to move the host to my ip, instead of localhost(127.0.0.1). I was also looking around on the internet and tried a lot of things but it always ended in errors for apache. So, I was wondering if someone could help me switch the host ip for apache, thanks.

---

### Post by ahallubuntu on 2012-11-18
So your server with Apache2 is on your local network, right?  Say it has an IP of 192.168.1.2 .  So first try accessing Apache2 at [http://192.168.1.2](http://192.168.1.2) from another computer on your network.  Does that work?  If not, what error do you get?  Is there an error in the Apache log?

Next - are you hoping to access it externally?  If so, then you will need to forward port (probably) 80 to this IP.

Otherwise - can you explain exactly what you are trying to do?

---

### Post by SeijiSensei on 2012-11-18
By default, Apache listens on port 80 on all interfaces.  If you cannot see the server from outside your network, you haven't forwarded port 80 correctly from your router back to the server, or your ISP doesn't allow remote connections to port 80.  Since most ISPs' terms-of-service for residential users forbid running servers, blocking inbound ports 25 and 80 is a common practice.

---

### Post by Skullxbagel on 2012-11-19
What I meant though is changing it from 127.0.0.1 or localhost to my ip address so I could access it anywhere, I've googled a bit and apache just shows errors when I do what they say to do.

---

