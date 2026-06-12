---
title: "Network Manager Log."
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by syednizamudeen on 2010-07-24
I'm using NM applet to connect to the Internet.I just need to know my Internet usage details such as Connection Duration,Data sent and received.Please help..

---

### Post by iponeverything on 2010-07-24
If you add the "System Monitor" applet to panel, it will give your total network traffic. NetworkManger does not log the information. 

There is terminal application called vnstat that might be closer to what you want.

install it with:

```
sudo dpkg -i vnstat

```
do a

```
man vnstat

```or
```
vnstat --help

```
for usage, it will break down traffic by hour, day, week, month and lots of other ways.

---

### Post by syednizamudeen on 2010-07-24
> **iponeverything said:**
> If you add the "System Monitor" applet to panel, it will give your total network traffic. NetworkManger does not log the information. 

There is terminal application called vnstat that might be closer to what you want.

install it with:

```
sudo dpkg -i vnstat

```
do a

```
man vnstat

```or
```
vnstat --help

```
for usage, it will break down traffic by hour, day, week, month and lots of other ways.

Thanks Dude..vnstat gets my job done..:)

---

