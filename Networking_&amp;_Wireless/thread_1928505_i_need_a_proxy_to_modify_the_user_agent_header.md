---
title: "i need a proxy to modify the user agent header"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by arunharidas on 2012-02-20
hi,
I am using a gsm internet connection which allows me only one application to use internet at a time. I think they track the applications with its user agent. So please suggest me a good proxy just to modify the user agent so that i can use same useragent for all the applications. I tried CNTLM but i didnt work.

---

### Post by Perkins on 2012-02-21
Well, the first consideration would be that, by doing so, you may be violating their TOS, which is generally grounds for termination of service...


Assuming that that is not an issue, I am fairly certain that they are not actually using the user agent string to track how many programs you are using, since only web browsers will be sending one...

However, the good news is that just about any socks proxy program will crunch all of your traffic into one connection, leaving them unable to tell how many programs you are using.  Of course, you'll need a proxy server somewhere to handle the other end.  If you have another machine on a non-gsm connection, you could set one up there.  Or there are paid proxy services available for hire.  Otherwise you might have luck with TOR, assuming that they haven't blocked it, but it wouldn't surprise me if they have.

---

