---
title: "Zonet troubles"
date: 2012-08-27
forum: Networking &amp; Wireless
---

### Post by kenshen on 2012-08-27
Hey so i have a marvel 88E8056 PCI-E Gigabit Ethernet Controller or a zonet zew 1602a i would like to not use ndiswrapper for as it doesn't support the functions i need can some one help?

---

### Post by chili555 on 2012-08-27
Hey so one of these is wired ethernet and the other is wireless which are you trying to set up ? ndiswrapper probably wont help your ethernet

please open a terminal and run and post```
lspci -nn | grep 0280
```

---

### Post by kenshen on 2012-08-27
> **chili555 said:**
> Hey so one of these is wired ethernet and the other is wireless which are you trying to set up ? ndiswrapper probably wont help your ethernet

please open a terminal and run and post```
lspci -nn | grep 0280
```

I Don't want to use ndiswrapper i would like to use the Linux native drivers as ndiswrapper doesn't support certain functions that i need plus I'm running ubuntu 10.04 to use software called piratebox

---

### Post by chili555 on 2012-08-27
I repeat:> which are you trying to set up ?And:> please open a terminal and run and post
```
lspci -nn | grep 0280
```I'm not trying to talk you into ndiswrapper. I'm trying to gather information so we can solve your problem.

---

### Post by kenshen on 2012-08-27
> **chili555 said:**
> Hey so one of these is wired ethernet and the other is wireless which are you trying to set up ? ndiswrapper probably wont help your ethernet

please open a terminal and run and post```
lspci -nn | grep 0280
```

> **chili555 said:**
> I repeat:And:I'm not trying to talk you into ndiswrapper. I'm trying to gather information so we can solve your problem.

oh ok lspci doesn't produce any thing and I'm trying to set up my wifi card which when sudo lshw -C network is used shows up as marvel 88w8335 [Libertas] 802.11b/g Wireless sorry for putting the wrong thing

---

### Post by chili555 on 2012-08-27
I need more specific information:```
lspci -nn
```I need the product and vendor ID for your card; it will be in the form of 1234:abcd or some such.

---

### Post by kenshen on 2012-08-27
> **chili555 said:**
> I need more specific information:```
lspci -nn
```I need the product and vendor ID for your card; it will be in the form of 1234:abcd or some such.
11ab:1faa

---

### Post by chili555 on 2012-08-27
> **kenshen said:**
> 11ab:1faaI don't believe there is a way to get it going aside from ndiswrapper.

Do you have a Zonet zew 1602a you can install and give me the same information? Maybe we'll be more successful.

---

### Post by kenshen on 2012-08-27
> **chili555 said:**
> I don't believe there is a way to get it going aside from ndiswrapper.

Do you have a Zonet zew 1602a you can install and give me the same information? Maybe we'll be more successful.

Nope sorry

---

### Post by chili555 on 2012-08-27
> **kenshen said:**
> Nope sorry> Hey so i have a marvel 88E8056 PCI-E Gigabit Ethernet Controller or a *zonet zew 1602a* :confused:

I'm not sure I can be of more help.

---

