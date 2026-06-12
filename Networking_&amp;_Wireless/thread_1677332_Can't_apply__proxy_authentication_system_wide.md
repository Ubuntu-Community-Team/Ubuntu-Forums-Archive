---
title: "Can't apply  proxy authentication system wide"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by sebastiaopburnay on 2011-01-28
Hi!

First of all, thank you all for keeping this forum.

I'm sorry for giving you a problem for which there are a lot of threads, but none of them helped me.

Before, I used a CentOS distro and there I would just use my own squid (proxy) server to authenticate in the corporate proxy (lets supose it is the 1.1.1.55) with my 'DOMAIN\user:password' pair.

Now, I went to System -> Preferences -> Network Proxy Preferences and chose the Proxy's  IP, entered my 'DOMAIN\user:password' pair and presed on 'Apply System-Wide..and then I enter the root password for the  «System policy prevents setting proxy settings»

Up to this point everything seems very normal,, but this Authentication window keeps there (instead of automatically closing itself), just the input box for the system root password disappears.

This is very annoying, and when I press the close window button, the same window opens and closes a few times until a new Authentication window appears: «Privileges are required to change GConf system values». In that window, not even my root password works.

This is really getting me very frustrated. I can surf the web trough firefox, but I cannot perform a simple wget command without an error message complaining about proxy authentication:

> Proxy request sent, awaiting response... 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
2011-01-28 19:40:35 ERROR 407: Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )


Well, I'm sorry for being so verbose, but I didn't want to leave any information out.

With my best regards,
sebastiaopburnay

---

### Post by sebastiaopburnay on 2011-01-31
Well, I've tried creating the file **/etc/apt/apt.conf.d/01proxy** with the line:
```
Acquire::http::Proxy http://MyDOMAIN\MyUSER:MyPASSWORD@PROXY'S-IP:8080/
```

It seems fine, but when I ran an apt-get install command I got the following error:
> E: Syntax error /etc/apt/apt.conf.d/01proxy:2: Extra junk at end of file
Which suggests that the file is not well formatted or something like that.

Any good ideas?

---

### Post by sebastiaopburnay on 2011-01-31
Well, I've now altered the **/etc/apt/apt.conf.d/01proxy** file acording to this other posts I've seen so that it's content is now:
```
Acquire::http::Proxy "http://<DOMAIN>\<USER>:<PASSWORD>@<PROXY-IP>:8080/";
```

And it was very productive, because now I have a new error running **apt-get install**. This was the new error.

  > 407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

Well, I've entered the authentication items (DOMAIN\USER:PASS) on the .conf file, so I don't know where am I failing or what/where is missing.

---

