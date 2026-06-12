---
title: "Timeserver Forwarding"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by lewiseason on 2011-10-27
Hello friends,

I have a network (10.0.49.0) which has no access to the internet. On this network I have an Ubuntu box which does have internet access through its other network interface (10.0.1.0). I'd like any UDP requests made on port 123 to the server inside the network to be passed off to a server on the internet.

I've been playing with iptables to no avail, can anyone help me?

Cheers,
Lewis

---

### Post by newbie-user on 2011-10-27
Have you enabled ip forwarding on the Ubuntu box?  

Another option might be to install install ntp on the ubuntu box and use it as a time server.

---

### Post by ratcheer on 2011-10-27
> **newbie-user said:**
> 
Another option might be to install install ntp on the ubuntu box and use it as a time server.

That is what I would do.

Tim

---

### Post by jonobr on 2011-10-27
> nstall ntp on the ubuntu box and use it as a time server.

+1 on this

NTP was designed this way to progpagate clocks down the chain.

---

### Post by 2F4U on 2011-10-27
A different way to achieve the same result would be if you configure the box that has internet access to act as your internal time server and configure that box to get the time from a ntp server on the internet.

---

