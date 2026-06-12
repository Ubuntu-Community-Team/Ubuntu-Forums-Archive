---
title: "can not access wireless router via ip address"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by iemcdoug on 2010-08-24
us robotics router, trying to access 192.168.2.1, worked on windows xp, just switched to lucid

i have tried using both firefox and chrome, neither will access my router

please help

---

### Post by sharathcshekhar on 2010-08-24
Are you able to access internet? If your answer is yes, ip address of your router is most certainly wrong. Generally it will be 192.168.1.1. How ever, it depends on router.

---

### Post by pricetech on 2010-08-24
ifconfig should give you the router's IP if you need to confirm it, but it should be the same as it was under windows.

I haven't run into one that I couldn't access via browser (or telnet) yet, but it may be they are using some proprietary pseudo code junk that keeps a standards compliant browser from working.

Do you recall having to install any software under windows to access it ??

Did it work in browser other than IE under windows ??

You might also try Opera web browser.  Download the Linux / Ubuntu version from opera dot com

---

### Post by iemcdoug on 2010-08-24
ifconfig gave me 192.168.2.3, still wouldnt connect

i have always used 192.168.2.1 before installing ubuntu, always worked

never installed anything on windows to use it, worked fine in ie, firefox, chrome

i have now tried opera, still no luck, but i will continue to use as my primary browser

---

### Post by pricetech on 2010-08-24
Oops, sorry.  I'm thinking ipconfig under windows.  I support windows boxen all day long and sometimes I forget.

If your IP ends in .3 and you're used to using .1 as your router's IP, then it should be the same.

Can you ping the router ??

---

### Post by iemcdoug on 2010-08-24
i ping .2.3 at ~.04 ms

---

### Post by sharathcshekhar on 2010-08-25
Is it the same with wired and wireless connection? Have you tried to access it via Wired network?

---

### Post by disturbio on 2011-03-20
Got the same problem today. Solved by using 192.168.1.254 IP
Also [http://home](http://home) works

---

