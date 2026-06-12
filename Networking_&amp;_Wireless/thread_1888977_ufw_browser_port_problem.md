---
title: "ufw browser port problem"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by Ferryfromholland on 2011-11-30
Hello,
I want to use ufw as firewall.
When i allow ports in ufw for Firefox this will only work for one web page, after this page Firefox uses another port, witch i will have to allow as well, and this continues at every new page. The problem for me is that this seems endless because it keeps changing ports. On opera i have the same problem.

Is there a way to allow the program?
Or lock the program to specific ports ?

Putting open thousands of ports for internet seems a bit dangerous to me..
please advise

Thanks,
Ferry

---

### Post by Dangertux on 2011-11-30
> **Ferryfromholland said:**
> Hello,
I want to use ufw as firewall.
When i allow ports in ufw for Firefox this will only work for one web page, after this page Firefox uses another port, witch i will have to allow as well, and this continues at every new page. The problem for me is that this seems endless because it keeps changing ports. On opera i have the same problem.

Is there a way to allow the program?
Or lock the program to specific ports ?

Putting open thousands of ports for internet seems a bit dangerous to me..
please advise

Thanks,
Ferry

This shouldn't be happening. You might wish to make sure the following lines are present in /etc/ufw/before.rules

```

-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT

```

Hope this helps.

---

### Post by Ferryfromholland on 2011-11-30
both those line are present at 
# quickly process packets for which we already have a connection

I try to understand why those web browsers use Thad many different ports, is this to make browsing faster?

can this be a problem between my firewall and my router ?

---

