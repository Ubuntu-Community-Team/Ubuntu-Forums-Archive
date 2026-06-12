---
title: "network testing"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by vandinsh on 2009-04-06
Hello!!! :)
I would like to test network performance! But I have a problem I can not find a tool, which tests UDP stream! In an output I want to see how much time ( microsekunds) is necessary for one transaction.
If you have any ideas, please, please help!!!

---

### Post by yota on 2009-04-06
Hi,

you can use the iperf command, and specifically with "-U" switch to test udp performance between two nodes of a network.

The package is homonym, so you just need a:
```

sudo aptitude install iperf

```

Hope this helps!

---

### Post by vandinsh on 2009-04-06
There is a problem, iperf shows result in sekunds, but I want to get more precise result in mikrosekunds. Do you have any ideas?

---

### Post by oobe-feisty on 2009-04-06
you can get it down to as low as 0.5 i just tried this 

iperf -i 0.1 -c host

---

### Post by yota on 2009-04-06
Hi vandinsh,

with:
```

iperf -U -n 1

```

you can test on the smallest amount of data which is 8K.

This said, woulnd't it be more meaningful to measure the mean width/time-unit of a flow? What are yo trying to look at?

---

### Post by vandinsh on 2009-04-06
I have tried your advise and got warning, have I done something wrong?
user@LC32:~$ iperf -i 0.1 -c 10.1.2.30
WARNING: interval too small, increasing from 0.10 to 0.5 seconds.
------------------------------------------------------------

---

### Post by vandinsh on 2009-04-06
I am working on a project. The aim of my project is to run iperf 1000 times in a loop, with these arguments: 
iperf -c 10.1.2.30 -n 16K -u
and in an output to get the result of each test in mikrosekunds to see whether all the results are the same.

---

### Post by oobe-feisty on 2009-04-07
> **vandinsh said:**
> I have tried your advise and got warning, have I done something wrong?
user@LC32:~$ iperf -i 0.1 -c 10.1.2.30
WARNING: interval too small, increasing from 0.10 to 0.5 seconds.
------------------------------------------------------------

i only tested it on localhost so that may be the case just change 0.1 to 0.5 as thats the minimum

---

### Post by vandinsh on 2009-04-07
Unfortunatelly in that case I get sekunds, not mikrosekunds. :(

---

### Post by TMVirginia on 2010-03-18
Is there a way to log the test result to a file for later analysis?

Thanks,

---

