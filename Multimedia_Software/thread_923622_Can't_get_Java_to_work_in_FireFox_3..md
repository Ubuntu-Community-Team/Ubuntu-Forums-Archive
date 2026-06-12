---
title: "Can't get Java to work in FireFox 3."
date: 2008-09-18
forum: Multimedia Software
---

### Post by brjoon1021 on 2008-09-18
Hi,

I am using 64 bit edition 8.04. and I installed the Java necessities via the command line after enabling the necessary repos.

I ran: "sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk"
They all installed properly as far as I can tell. However, when I go to a Java check site, I am told that Java is not working on my machine.

I actually NEED this to work properly to run my business. This the only time I have every had a problem with Java on Linux. Firefox three is the only new thing that I can think of that could be a problem.

Thanks,
B

---

### Post by gandaran on 2008-09-18
you can't use sun-java for firefox 64-bits, no sun-java plugin is provided 
what you can use is open java and the icedtea plugin for firefox. open synaptic, scroll down to icedtea, mark for install and click the apply button, the rest of java dependencies will get installed along too.

---

### Post by brjoon1021 on 2008-09-19
Are you certain ? The open source Java things do not work well, in my experience. I have tried the one you mentioned and some gcj thing. Both sucked.

---

### Post by pro003 on 2008-09-19
try this in terminal:
```

sudo aptitude update
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by gandaran on 2008-09-19
the sun-java6-plugin package is only provided for 32-bits users, this is the plugin package for firefox and as you can see it's missing in the 64-bits repositories, there is another way of making sun-java work in firefox without the plugin package, it's by making a symbolic sun java link to firefox, but again I believe only works for 32-bits systems or 32-bits firefox (you can install a 32-bits firefox) this is all because sun only makes 32-bits java for now.

---

### Post by brjoon1021 on 2008-09-19
Pro003,
thanks, I already have that though.

I guess this is a solved post because I am out of luck with 64-bit.

---

### Post by SennaRulz75 on 2008-11-07
Thanks pro003 for solution.

By default Java was not working with Firefox 32bit.

---

### Post by pro003 on 2008-11-07
> **SennaRulz75 said:**
> Thanks pro003 for solution.

By default Java was not working with Firefox 32bit.

You're welcome.

As for x64 version you can get it [here]("http://www.java.com/en/download/manual.jsp").

---

