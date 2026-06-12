---
title: "bluetooth won't work in toshiba u400-12p"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by HazHaz on 2009-05-01
[SIZE=3]hi
bluetooth dosnt  work although wifi works fine
anyway I tried this in terminal "hcitool scan"
and what I got is:
```
$ hcitool scan
Device is not available: No such device
```

 [/SIZE]

---

### Post by HazHaz on 2009-05-01
[SIZE=3]BTW I forgot to say
I use Ubuntu 9.04 :P[/SIZE]

---

### Post by HazHaz on 2009-05-02
anybody???!!!!

---

### Post by Olnex on 2009-05-03
Hello, I used to have U400H00, I did not have bluetooth support either, I found an answer:

So installed the omnibook module (latest version) and then issued:

   1. modprobe omnibook ectype=14


Now the bluetooth device can be see in the lsusb output and is turned off and on by the wireless kill switch on the front.

and here is a link to most recent solution:

[http://docs.google.com/View?docid=dgd53r6d_36hqmmh4hn]("http://docs.google.com/View?docid=dgd53r6d_36hqmmh4hn")

---

### Post by HazHaz on 2009-05-05
> **Olnex said:**
> Hello, I used to have U400H00, I did not have bluetooth support either, I found an answer:

So installed the omnibook module (latest version) and then issued:

   1. modprobe omnibook ectype=14


Now the bluetooth device can be see in the lsusb output and is turned off and on by the wireless kill switch on the front.

and here is a link to most recent solution:

[http://docs.google.com/View?docid=dgd53r6d_36hqmmh4hn](http://docs.google.com/View?docid=dgd53r6d_36hqmmh4hn)
thanks man works fine:P

---

