---
title: "Very slow internet, suspect a failing router"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by bobnutfield on 2009-02-15
Hello Everyone,

Out of the blue, for no reason I can find, I started experiencing an extremely slow internet.  Web pages struggle to open, long intervals between connections to web servers, and generally slow connections.  I have determined that it is probably not related to anything on a particular computer as I experience this on three distros on this laptop (triple boot Ubuntu, Fedora and Slackware) as well as WinXP on a different computer.  Web broadband test sites indicate an download speed of 120kb and upload at 300kb, far different than the 3mb I was getting!

Since I experience the same thing with every computer and OS, and wired as well as wireless connections, I am suspecting my 4 year old Belkin 54g router.  I had always believed that routers either worked or didn't, I have never seen one fail slowly.  Another thing that makes me suspect the router is that when I ping another computer on the network (home), I experience about 10-20 percent packet loss.

But before I go and shell out for a new router, I was hoping someone might know something else I can check.

Any replies grreatly appreciated.

---

### Post by superprash2003 on 2009-02-15
there is a possibility of router failing.. you could try resetting your router .. also it could be an ISP issue..

---

### Post by bobnutfield on 2009-02-15
Thanks, but the ISP doesn't report any problems and suggest the problem is with my equipment.  I have reset the router numerous times.  The router page shows downstream speed of 7716 and upstream of 448.  DNS is fine, as I can find web pages, but tracert [www.google.com](www.google.com) returns and error.  Seems odd.  NAT is enabled, and no one else is using my connection as the DHCP client list shows only my computers in the house.

---

### Post by error420 on 2009-02-15
Me too! I am also having this same issue. I'm on my ubuntu 8.10 machine but im using this forum via rdesktop client to connect to my windows machine. I think something changed in the past 2-3 days that is affecting my driver. I'm using an ASUS P5N E sli motherboard. Can anyone please help? All other computers on the network including my girlfriend's lenovo s10 netbook (also running 8.10) is working fine.

---

### Post by bobnutfield on 2009-02-15
> **error420 said:**
> Me too! I am also having this same issue. I'm on my ubuntu 8.10 machine but im using this forum via rdesktop client to connect to my windows machine. I think something changed in the past 2-3 days that is affecting my driver. I'm using an ASUS P5N E sli motherboard. Can anyone please help? All other computers on the network including my girlfriend's lenovo s10 netbook (also running 8.10) is working fine.

I don't believe my issue with broadband speed is related to any particular operating system or wireless driver since it happens in Ubuntu, Fedora, Slackware and WinXP.  It is the same result on two separate laptops and my netbook.  So the problem is almost certainly either in the router or the phone line.  I am getting only 128kb download and 300 upload.  Not broadband speeds.

---

### Post by superprash2003 on 2009-02-16
well it could be your phone line.. if possible try getting a router from your friend and try setting it up on your pc and then check speeds.. if its the same then its mostly a phone line problem..

---

### Post by bobnutfield on 2009-02-17
> **superprash2003 said:**
> well it could be your phone line.. if possible try getting a router from your friend and try setting it up on your pc and then check speeds.. if its the same then its mostly a phone line problem..


Thank you, apparently the phone line is the main culprit.  I moved the line to a different location and improved speed to about 1,5mbps.  Still not quite what I was getting, but much better.  I guess the router is fine.

---

