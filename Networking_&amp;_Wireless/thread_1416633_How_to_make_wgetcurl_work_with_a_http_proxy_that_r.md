---
title: "How to make wget/curl work with a http proxy that requires web login (wsso) ?"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by syraxes on 2010-02-26
Hello,

I am looking for a solution to circumvent a http proxy that works only with browsers. I need to be able to use this proxy with other programs, too : wget, curl, apt-get install . 

The problem is that 3 days ago, the 'smart' administrators of my company have deployed a new proxy server that requires authentication in a web page before accessing the internet.  As a consequence, only the web browser can have access : no wget, no curl, no apt-get install. 


This new http proxy server requires a WSSO login and works like this:
- i access for example [www.google.com](www.google.com)
- the proxy loads a web page asking for user/password
- after entering the login data, loads another webpage that tells me that i am about to go online. I have to click on a button. 
- finally, it redirects to the requested website

It seems to use both some cookies and some certificates.  

Ideally, I am hoping to find some kind of http proxy server that runs on my machine and automatically takes care of this idiotic web login.  So that i could configure any application to use the local proxy.  

So, does anyone have idea about which of the so-many http proxies available in Ubuntu could handle this kind of web authentication ? 


Thanks for any tip or advice !

---

