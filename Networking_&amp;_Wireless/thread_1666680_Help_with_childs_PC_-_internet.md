---
title: "Help with childs PC - internet"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by KaIIen on 2011-01-14
I gave to my 8yo daughter my old custom built PC. It's running Edubuntu 10.10. What I need to do is blacklist the entire internet, but have a whitelist of sites that are like children's educational games and her site for her school. Under parental controls (Nanny I think) I have options to control time of day or time of usage. There is a web filter that has a blacklist page and an allow page. How do I set this to ONLY allow what is on the allowed page??? I realize my router can blacklist certain words or what not, but I want to simply block everything.

Thanks!

---

### Post by sj1410 on 2011-01-14
a simple thing would be installing tinyproxy

```
sudo apt-get install tinyproxy

```
```
sudo nano /etc/tinyproxy.conf

```
uncomment the following lines

```
Filter "/etc/filter"

FilterDefaultDeny Yes
```


create a file /etc/filter with the alowed domains.

```
sudo /etc/init.d/tinyproxy restart

```

tinyproxy by default listens on port 8888, configure it in in the browers [hope she does not changes 
that]

Hope that helps. Good Luck !!!!!!!

---

