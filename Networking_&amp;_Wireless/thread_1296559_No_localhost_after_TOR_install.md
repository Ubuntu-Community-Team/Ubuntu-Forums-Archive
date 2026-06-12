---
title: "No localhost after TOR install"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by sTpny on 2009-10-20
Hi all, 

Not sure if this is the right section or not, and I'm sorry if it's not, but I do need some help, desperately. I recently installed Tor and Vidalia, with Polipo rather than Privoxy, since that's what the installation instructions on TOR's website called for. Anyhow, my TOR Button finally works in firefox, which I am very happy for, however, I can no longer browse my localhost. When I try to browse [http://localhost/~tony](http://localhost/~tony), I now get a "Failed to connect" error. 

I don't want to lose Tor, but I need my localhost to work because I'm building a website. What am I missing? Or what haven't I done that I should have done? 

Thanks in Advance, 

Tony.

---

### Post by scragar on 2009-10-20
Disable the tor button when using localhost.
Also check httpd(apache/lighttp) is running.

You may want to use foxyproxy if you get annoyed switching.

---

