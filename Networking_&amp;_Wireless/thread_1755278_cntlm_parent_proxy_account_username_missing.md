---
title: "cntlm parent proxy account username missing"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by jagandecapri on 2011-05-11
I have installed cntlm to configure proxy authetication through my university proxy server but everytime i run the cntlm -I -M [http://test.com](http://test.com) command I am getting the error that parent proxy account username is missing. In my university the proxy account is set such as the username that we login is like STUDENT/our_id follow by password. How to I configure cntlm to work with this? I have tried so many times but have not found the solution. Please help me to solve this problem.

---

### Post by khuevu on 2011-11-01
You need to run cntlm with the c option which point to the location of the configuration file. Without it, the program won't read the conf file. 
```

cntlm -c /etc/cntlm.conf -I -M http://test.com
```

---

