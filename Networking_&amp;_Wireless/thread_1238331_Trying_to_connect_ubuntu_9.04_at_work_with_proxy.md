---
title: "Trying to connect ubuntu 9.04 at work with proxy"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by x86-64-Scotland on 2009-08-12
At work I've installed 9.04, configured firefox to use the proxy server (its working, I can post this:) however I can't get apt-get or synaptic to work. 

I've tried entering the same proxy details I've setup for firefox within the 'System'->'Preferences'->'Proxy' setup, however I keep getting the 'Authentication required error':

Is there an idiots guide for doing this? Has anyone else has problems like this?

TIA

---

### Post by bear24rw on 2009-08-12
try the program tsocks

what i had to do was download the .deb with firefox and than install it that way once its set up you can change the config to use your proxy (google for tutorial) than you can

sudo tsocks aptitude update

and suck im using it with through a socks ssh proxy and it works great

EDIT:

maybe this guide is helpful?

[http://www.plenz.com/tunnel-everything](http://www.plenz.com/tunnel-everything)

---

### Post by x86-64-Scotland on 2009-08-12
I think this must be a problem with out messed up corporate proxy, in sources.list I altered change the entries from http:// to ftp:// and everything sprang into life.

---

### Post by slakkie on 2009-08-12
You can use the environment variables http_proxy and ftp_proxy, eg:

```

export http_proxy=http://proxy.euronet.nl:8080
export ftp_proxy=$http_proxy

```

Now both FTP and HTTP use the same proxy, of course you can specify a different proxy. But apt and other command line tools should then know about your proxy :)

---

### Post by bear24rw on 2009-08-12
> **x86-64-Scotland said:**
> I altered change the entries from http:// to ftp:// and everything sprang into life.

thats actually a really interesting idea, never thought of doing that

---

