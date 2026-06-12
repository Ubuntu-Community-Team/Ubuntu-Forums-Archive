---
title: "INTERNET not working !!!"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by Vin the JMaster on 2011-07-30
i am new in LINUX and i have a broadband connection of Reliance.Now when i starts ubuntu ,It shows that internet is connected but when it comes to fill the credentials to access internet ,it denies and error message displays that user id is wrong .but the reality is i am connected to internet that time also.Kindly help me in solving this problem:popcorn:

---

### Post by poolet on 2011-07-30
Open up a new terminal and type the following::

```
ifconfig 
```

```
lshw -C network
```

```
lshw grep | network
```

and paste the output here:::

---

