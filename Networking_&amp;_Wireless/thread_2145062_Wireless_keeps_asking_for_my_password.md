---
title: "Wireless keeps asking for my password"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by thirdeye420 on 2013-05-14
Hi everyone,

I'm fairly new to ubuntu.  I installed 12.04 yesterday.  I am able to logon to my wireless network here at work (no encryption here), but when I go home, it keeps asking for my password.  I am entering the correct password, but it won't connect to the network.  I am using the right encryption (WPA/WPA2).  Anyone have any idea what's going on?

Thanks everyone.

---

### Post by thirdeye420 on 2013-05-14
Hi everyone,

I'm fairly new to ubuntu. I installed 12.04 yesterday. I am able to logon to my wireless network here at work (no encryption here), but when I go home, it keeps asking for my password. I am entering the correct password, but it won't connect to the network. I am using the right encryption (WPA/WPA2). Anyone have any idea what's going on?

Thanks everyone.

---

### Post by grahammechanical on 2013-05-14
It is not asking for your Ubuntu login password but for the wireless key or WPA-PSK key to access the router. It is also known as the network security key or pass-phrase. For my router it is 10 characters long and any letters are capitalized. You may find this information on a sticker on the router itself. Otherwise, anyone in wireless range of your router will gain wireless access to it and use your ISP connection to access the Internet at your expense.

Regards.

---

### Post by thirdeye420 on 2013-05-14
Yes I realize that, it is asking me for my security key and won't connect.  I am putting in the correct security key, but it still keeps asking me for it.

---

### Post by thirdeye420 on 2013-05-14
No one has any idea why this is happening?

---

### Post by thirdeye420 on 2013-05-14
No one has any idea why this is happening?

---

### Post by lisati on 2013-05-14
Threads merged. Please do not start multiple threads for the same question, it dillutes the community's ability to help.

---

### Post by thirdeye420 on 2013-05-14
ok sorry...

---

### Post by steeldriver on 2013-05-14
What wireless device do you have? there are a few driver bugs e.g. the Intel cards (iwlwifi driver) sometimes do that when they try to connect to a Wireless-n network - the workaround is to disable Wireless-n mode on the router or by an optional driver parameter

But we can't really advise you without knowing what hardware

---

