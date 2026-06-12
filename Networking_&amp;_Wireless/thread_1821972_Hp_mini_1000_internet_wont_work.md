---
title: "Hp mini 1000 internet wont work"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by jesus-saves on 2011-08-09
I installed the netbook version of ubuntu 10.  Problem is no wireless networks show up.  So I have an eternet connecting.  Only problem is when I plug that in, still no internet.  I need to download drivers to make the wireless work.  Ive been trying to get this to work all day, and Im beyond my frustration level with this.  Someone please help me get my internet to work with this.

---

### Post by poolet on 2011-08-09
Open up a new terminal and type the follow:::

```
ifconfig
```

```
sudo lshw -C network
"your password"
```

```
lspci -nn 
```

```
dmesg | more
```

At the end, paste the output here!!!

---

