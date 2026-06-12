---
title: "Can't load Gmail with my Mobile Broadband connection"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by kolya_m on 2010-01-24
Hi!

I just installed Ubuntu a few days ago and am loving it so far. There is, however, one huge problem which is spoiling all my fun: I can't access my gmail.

I'm using a Huawei E220 USB modem with T-Mobile UK. Plugged it in and was very impressed when I could set up my connection with minimal fuss. When I try to load gmail though, I get stuck with the statusbar saying 'Waiting for [www.google.com]("http://www.google.com")...'. All other sites work fine (including google.com), and I don't get this problem when connecting though the Web 'n' Walk software in Windows XP.

Has anyone got any ideas on how I can start working this out?

Thanks in advance

Kolya

---

### Post by x33a on 2010-01-24
Try changing the dns servers, or try a different browser.

---

### Post by kolya_m on 2010-01-25
I tried using openDNS, Chromium and Lynx. Same thing happens though.

---

### Post by kolya_m on 2010-01-26
After some tinkering, I've discovered that I can't access ANYTHING at google.com/accounts, which explains why the Gmail login page can't finish loading. If I do (for instance) wget google.com/accounts/ServiceLogin, it responds and starts downloading (i.e. the download bar appears), but no data is ever received.

Does anyone have any idea what might be causing this? 

Kolya

---

### Post by dotdot on 2010-01-26
sounds like a port issue.

ie tmobile have locked it. ? perhaps

interestingly i'm using tmobile & a G2 & mobile on.

tethered... and can get gmail to work .. but it's not secure !
no padlock (in FF - i don't go chrome .. )

thoughts ?

---

