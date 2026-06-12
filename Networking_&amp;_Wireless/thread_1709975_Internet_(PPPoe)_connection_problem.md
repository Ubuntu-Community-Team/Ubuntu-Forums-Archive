---
title: "Internet (PPPoe) connection problem"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by asifupal on 2011-03-19
hlo.
I'm having a problem in activating my pppoe connection in Ubuntu 10.10 in my dell inspiron 15R.I tried these 2 ways :
1.By writing "Sudo pppoeconf" in Terminal.
/ 
2.By adding new DSL connections from network manager.I put username,password,service name,mac address correctly.But still the connection is not getting activated.So, is there any other way for activating pppoe connection. (by using some kinda 3rd party soft or something. )
Thanks.
(sry,I'm a novice ubuntu user )

---

### Post by dineshs on 2011-03-19
1)Please follow step-1 [ here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")
2)Restart
3)run ```
sudo pon dsl-provider
```
wait for say 10 seconds
4)Now run ```
ping 4.2.2.1 -c5
```and post the result
5)Also post the result of ```
cat /etc/resolv.conf
```

---

### Post by asifupal on 2011-03-19
> **dineshs said:**
> 1)Please follow step-1 [ here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")
2)Restart
3)run ```
sudo pon dsl-provider
```
wait for say 10 seconds
4)Now run ```
ping 4.2.2.1 -c5
```and post the result
5)Also post the result of ```
cat /etc/resolv.conf
```
about step 3 -

Should I write(run) exactly what you have written (sudo pon dsl-provider) ? 
OR,
Should I write my isp's service name in the place of "dsl-provider" ? 
Thanks.

---

### Post by dineshs on 2011-03-20
While running sudo pppoeconf a file named dsl-provider will be created in /etc/ppp/peers.If you havent renamed it ,do sudo pon dsl-provider.(there is no harm in trying this code).I do not know if service name is so important.BTW how do you connect in windows?

---

