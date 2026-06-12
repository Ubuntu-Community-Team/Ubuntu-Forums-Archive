---
title: "rtl8188su wifi dongle, cannot compile driver"
date: 2012-09-11
forum: Networking &amp; Wireless
---

### Post by Kr0nZ on 2012-09-11
Hi all, I bought a external wifi dongle a few months back but I cant seem to get the driver to compile.

I got the driver from [http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")
The windows driver from that page works fine on windows so I know its the correct driver.

But when compiling I get the message:
[COLOR="Red"]/bin/sh: 1: Syntax error: "(" unexpected
make: *** [modules] Error 2[/COLOR]

Im guessing this is because the driver is for Linux Kernel 2.6.18~2.6.38 and Kernel 3.0.2
but Im on Kernel 3.2.0-25-generic-pae

Is there anyway I can get this driver to compile properly?
I've had problems with driver source not matching my Kernel before, but in those instances the compile message was a bit more helpful and I was able to make the necessary changes to the source to get it to compile.

lsusb for my device is:
Bus 002 Device 004: ID 1740:9603 Senao

---

### Post by steeldriver on 2012-09-11
Sometimes these kind of errors from 'make' are because the author expects /bin/sh to link to a bash (or Bourne) shell - whereas in Ubuntu the default is for it to link to the dash shell - if 

```
ls -l /bin/sh
```

shows a link to `dash` for you, it might be worth trying 

```
sudo ln -sf bash /bin/sh
```before running make and then reverting after with

```
sudo ln -sf dash /bin/sh
```

---

### Post by Kr0nZ on 2012-09-11
thanks, dash was the problem.
Im now getting familiar compile messages.

---

