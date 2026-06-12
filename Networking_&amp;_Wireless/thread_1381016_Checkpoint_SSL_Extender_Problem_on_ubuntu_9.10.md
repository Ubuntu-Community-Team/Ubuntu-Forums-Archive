---
title: "Checkpoint SSL Extender Problem on ubuntu 9.10"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by RisingForce on 2010-01-14
Dear Friends,

I want to connect to my company network using checkpoint ssl extender. I had installed snx_install.sh properly. When I try to login it is being authenticated successfully but when it says "connecting" popup browser after some time it returns "failed to initialize" error.

I am using Ubuntu 9.10  java 6.0 and mozilla 3.5.7


I appreciate for your help.


Thanks,

---

### Post by /bin/bash on 2010-01-22
Hey,

I had the same problem like you.

Perhaps this is a solution for you.

First I download the last SSL Extender I found on the Checkpoint Website
"Check_Point_SNX_R66_HFA_01_For_Linux_800004013.sh"

Then you have to install it with

```
sudo -s -H
chmod 755 Check_Point_SNX_R66_HFA_01_For_Linux_800004013.sh
sh ./Check_Point_SNX_R66_HFA_01_For_Linux_800004013.sh
Installation successfull
```

Then install libstdc++5. In Ubuntu 9.10 it is not available.

```
sudo dpkg -i libstdc++5_3.3.6-17ubuntu1_i386.deb
```

Then

```
snx -s [server] -u [username]
```

and you have a VPN connection

I hope it will work for you and sorry for my bad english ;)

Some informations
[http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/]("http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/")

[https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk41569]("https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk41569")

---

### Post by kennedyjch on 2011-05-27
Worked for me on 10.10. Thanks!!! :)

---

