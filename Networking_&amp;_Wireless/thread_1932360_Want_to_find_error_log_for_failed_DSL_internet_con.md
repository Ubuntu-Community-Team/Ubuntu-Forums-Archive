---
title: "Want to find error log for failed DSL internet connection"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by bimaljr on 2012-02-27
Hello all,

I am using Ubuntu 11.04
I have inernet connection that is connected via network cable which is coming from another building. They have provided Username/ Password to connect internet.

I have configured it in DSL section. So I clicked the network icon and click on "Edit Connections.." and than click on "DSL" tab and configured here. 

**DSL Configurations:**
"IPv4 Settings" > Method > Automatic(PPPoE)
DSL > FILLED MY INTERNET USERNAME/PASSWORD
PPP Settings > all unchecked except "Send PPP echo packets"


Now I have problem with my internet connection. Sometimes the connection failed. This is not Ubuntu problem. This is the service provider's problem. The inernet provider want to know the error code so they can solve it. Under Windows, I get error code like "691" and others.  But I don't see any error code under Ubuntu.

So my question is, is there any log to get the error code? I want to know the reason why the connection failed.

---

### Post by SeijiSensei on 2012-02-27
> **bimaljr said:**
> The inernet provider want to know the error code so they can solve it. Under Windows, I get error code like "691" and others.  But I don't see any error code under Ubuntu.

Unless they have real experience with Linux, I suspect they won't be very helpful.  I don't know of any error codes like those; they sound like a Windows-only thing.  You can probably trace the connection in /var/log/syslog; you need to use sudo to read this file. Maybe it will give you some insight into why the connection fails.

---

### Post by bimaljr on 2012-02-27
Thank you SeijiSensei
This is what I want :)

---

