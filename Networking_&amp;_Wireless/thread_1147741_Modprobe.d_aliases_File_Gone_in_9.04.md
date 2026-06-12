---
title: "Modprobe.d aliases File Gone in 9.04"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by zeronothing on 2009-05-03
I just recently upgraded to Ubuntu 9.04, and wanted to configure network interface bonding on my desktop machine. One interesting thing I found is I cannot find the aliases configuration file that would normally be found in /etc/modprobe.d/ . As of right now in ubuntu 9.04 the file is not in /etc/modprobe.d/ directory. In all of the versions before 9.04 the file was listed in the /etc/modprobe.d/ directory. If someone can point me to where the file is or what other alternative I can use that would be great.

---

### Post by lswb on 2009-05-03
You can just make the file yourself or add your alias statements to any file in /etc/modprobe.d. All the files there are read and acted on a boot.

---

### Post by chili555 on 2009-05-03
Also, effective with 9.04, they want to be named /etc/modprobe.d/whatever[COLOR="Red"].conf[/COLOR].

---

### Post by Corin-EU on 2009-05-05
So the question is, as there is no longer an aliases file in modprobe.d directory, and there are no corresponding entries in the other files in that directory, how is the functionality that modprobe was providing with the aliases file now being executed, or were in fact all or most of the entries in the former aliases file in fact redundant?

---

### Post by chili555 on 2009-05-05
I think many, but not all of the aliases are redundant. However, if you need one, you can certainly create it. For example, here is my */etc/modprobe.d/iwl3945.conf*:```
alias wlan0 iwl3945 
options iwl3945 antenna=1
```

---

### Post by zeronothing on 2009-05-11
Ok, I eventually figured it out. I took what chili555 said in his last post and made the alias change to the interface file located in /etc/network/interfaces. Then I used the file /etc/modules to load the bonding module, which is necessary to link both of your NIC cards together. By using the alias information, I was able to create the "bond0" interface. Eveny thing is up and running. Thanks everyone for you help. Its always great to bounce questions around to figure out the answer, again thanks everyone.

---

### Post by zeronothing on 2009-05-11
Can't seem to find the "Solved" thread option. I just wanted to post, my issue is resolved.

---

### Post by santhony on 2009-12-12
Thanks for this thread..

Great INFO in remapping my Firefly in Myth

---

