---
title: "Network Manager not starting when booting up."
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by JCPTY on 2012-08-09
Hi Guys,

Ever since I upgrade my laptop to Ubuntu 12.04 the network manager is not starting when I boot up. I always need to do sudo service network-manager start.

Now Today I did the same command, network manager started but no connectivity to my router.

Did any of you know why this is happening? I also try running this command  sudo /etc/init.d/networking restart   but cant get the network to work properly.

Appreciate if any of you can help.

Thanks

JC

---

### Post by JCPTY on 2012-08-09
I added the line to make it start in /etc/rc.local and now the network manager is starting when booting my system. But still no network connectivity...

---

