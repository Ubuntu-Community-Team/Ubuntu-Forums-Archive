---
title: "How to install wireless driver not on supported list"
date: 2010-08-05
forum: Networking &amp; Wireless
---

### Post by pwnjangles on 2010-08-05
I'm using a Belkin basic wireless usb adapater F7D1101 all my other belkins (diffrent models) worked without installing drivers I just had to plug it in and it worked but this one doesn't because it's a newish model and I guess windows only there has to be a way to get it to work for ubuntu right? I looked for tons of guides and cant find any for this model.
Can anyone help me out? I want to use linux again instead of crap vista and the only internet connection I have is with this wireless adapter.

inb4 buy a new one because I dont have the money right now and just bought this one.

---

### Post by pwnjangles on 2010-08-05
Found this

"Just installed ubuntu 10.04 lts. Bought a Belkin F7D1101 v1 usb n  adapter and out of the box it didn't work. After reading the forums here  and finding so many people can't make it work I began to wonder if I  made a mistake buying the thing.  But after many more hours of reading I  found that if I went to my package manager and type in "wifi" it  brought up the file ndiswrapper in which many forums stated.   ndisgtk  is the exact package This is for windows wireless drivers. After I  installed the windows driver using this it worked like a charm.  Works  great in 9.1 the same way Just to let you know"

I tried it all and still no luck.

---

### Post by bkratz on 2010-08-05
Do you have the correct windows driver file? 32bit or 64bit, and also ndiswrapper really likes the XP driver better usually. Also, do you have the xxx.inf and  xxx.sys files for your card?

---

### Post by flash63 on 2010-08-06
Hello,
checkout the USB-ID:
```
lsusb
```
it looks like this
```
Bus 001 Device 001: ID 050d:945a Belkin Components
```
Very probably it is a device with Realtek Chipset. The manufacturer provides appropriate drivers.

---

