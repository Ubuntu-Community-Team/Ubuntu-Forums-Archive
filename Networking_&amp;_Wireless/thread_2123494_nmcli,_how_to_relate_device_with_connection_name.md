---
title: "nmcli, how to relate device with connection name"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by tombert on 2013-03-08
Hi, I am working on a script to automatize my 3G modem connection. I have one problem, I cannot relate the connection name to the device:

```

[FONT=courier new]#> nmcli con list
[/FONT][FONT=courier new]NAME        UUID                                   TYPE              TIMESTAMP-REAL                    [/FONT]
[FONT=courier new]3G-A1       1269a89a-31a1-4909-8835-db85cda486e0   gsm               Fri 08 Mar 2013 11:17:44 CET      [/FONT]

```


```

[FONT=courier new]#> nmcli dev status[/FONT]
[FONT=courier new]DEVICE     TYPE              STATE        [/FONT]
[FONT=courier new]ttyUSB0    gsm               connected    [/FONT]

```

So how can I relate "3G-A1" to "ttyUSB0"?

thx for your support ...

PS: I am on Ubuntu 12.1

---

### Post by steeldriver on 2013-03-08
try

```
nmcli con status
```

- should give NAME and DEVICE together

---

### Post by tombert on 2013-03-08
Yes, status prints the device ... but only if its already connected (unfort. not in the -fields option) - but I need to know in advance.
thx

---

