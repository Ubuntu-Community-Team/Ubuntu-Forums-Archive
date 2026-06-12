---
title: "how to use HUNT"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by hero1900 on 2009-05-27
hi guys i install hunt from synaptic but i don't know where is it or how to use it
any one can help

---

### Post by chili555 on 2009-05-27
It looks to me like it is designed to be run from the terminal. ```
hunt -v eth0
```I was especially interested to read this when I did:```
man hunt
```> Please make sure you KNOW what you are doing before using hunt. It is recommended that you should test how it behaves on some test connections and then use it wisely. You may want to select "options" and then "add conn policy entry" as by default only telnet connections are monitored.Not many networks have much telnet traffic these days.

---

### Post by hero1900 on 2009-05-27
thanks
but how come it only used in telnet ??

---

### Post by chili555 on 2009-05-27
> how come it only used in telnet ??It isn't the only protocol. I was only suggesting that there is a lot of reading to do to get something useful out of it. You might start with:```
less /usr/share/doc/hunt/README.gz
```The 'less' command allows you to scroll back and forth with the arrow keys.

---

