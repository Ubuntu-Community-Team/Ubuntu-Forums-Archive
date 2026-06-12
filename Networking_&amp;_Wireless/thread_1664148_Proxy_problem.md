---
title: "Proxy problem"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by jgolden on 2011-01-10
I am hoping someone can help me.  I am having issues setting up Ubuntu server with our proxy.

I have set the proxy using these commands

http_proxy=http://ip:port/
export http_proxy

I also looked in the proxy file for apt-get and that is correct as well.

However, the server is still unable to reach the internet.  When I run an apt-get update it shows me this:

Cannot initiate the connection to port:80

Port in the above line is the port I put in for the proxy.  It doesn't show the IP of the proxy.  Where is it getting this info and how can I change it.

Thanks for any help.

---

### Post by sj1410 on 2011-01-10
try this

if authentication enabled

```

export http_proxy=http://username:password@proxyserverip:port/

```
if not

```

export http_proxy=http://proxyserverip:port/

```

---

### Post by PatchesTheCaveman on 2011-01-11
apt-get doesn't appear to respect the HTTP_PROXY environment variable.  Please post the name and the contents of the file you created or changed to configure apt-get for the proxy.  I suspect the problem is there.

---

### Post by sj1410 on 2011-01-11
theres not need to change or create any file. its just a environment variable to set before doing an apt-get update

have a look at

```

man sources.list

```

and verify it using

```

echo $http_proxy

```

Good Luck!!!

---

### Post by gmargo on 2011-01-11
To run apt-get and related tools through a proxy, add the following format line to **/etc/apt/apt.conf** or a new file under the **/etc/apt/apt.conf.d/** directory. (optional parts in brackets) From **apt.conf(5)** man page.
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```
Make sure to include the trailing semi-colon.

---

