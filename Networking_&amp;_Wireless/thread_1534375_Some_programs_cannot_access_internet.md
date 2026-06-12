---
title: "Some programs cannot access internet"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by rnpereira on 2010-07-19
Hello,

Im using Ubuntu 10.04 and im having problems with my proxy authentication.

I can use browser, apt-get and synaptic with no problems (once i could set them up), but there are some programs that i cannot. My gmail notifier and rhythmbox are some examples of programs that i've tested and was unable to access internet.
The apt-get problem was solved adding some lines on the /etc/apt/apt.conf:
```

Acquire::http::proxy "http://user:pass@proxy:port/";
Acquire::ftp::proxy "ftp://user:pass@proxy:port/";
Acquire::https::proxy "https://user:pass@proxy:port/";

```
The synaptics was solved adding the proxy set up into Settings>Preferences>Network

But the problem is, I cannot find a place to put the proxy conf that will work on entire system. I tried on System>Preferences>Network Proxy to apply system-wide but appears it didn't work.
I treid to put lines in the bash file ( /etc/bash.bashrc) just like on the apt conf file but changing the "acquire to export instead"

I don't know what else to do. I searched for places I could add this proxy conf, but didnt find any. All i find about proxy is related to apt-get and synaptics connection issues. And thats not my problem.

Is there any file I could do a system-wide proxy configuration since the button on Network Proxy doesnt seems to be working for me? Or do I need to install any other program that could do this?

Regards,

Ricardo

---

