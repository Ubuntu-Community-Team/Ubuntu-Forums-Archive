---
title: "apt-get under proxy"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by jlillywh on 2009-04-29
I've searched around a bit on this issue but it remains unsolved.

I'm running Ubuntu 9.04 and internet connection is fine under the proxy. When I open a browser, I always get this prompt:

The proxy GILMAN.ext.ch2m.com:80 is requesting a username and password. The site says: ""

So I enter my username and password and it works great.

But when I go to do apt-get or anything similar like rails gem install, etc., I get connection refused. Here is a little of what happened on sudo apt-get update:

Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)

Here is what happens when I do sudo gem update rails:

Updating installed gems
ERROR:  [http://gems.rubyforge.org/](http://gems.rubyforge.org/) does not appear to be a repository
ERROR:  While executing gem ... (Gem::RemoteFetcher::FetchError)
    Errno::ECONNREFUSED: Connection refused - connect(2) ([http://gems.rubyforge.org/yaml](http://gems.rubyforge.org/yaml))

I changed my proxy settings in Synaptic Package Manager -> Settings -> Preferences -> Network to manual proxy - [proxy_name] port 80, but when I do synaptic install for say, Python 3.0 for example, it does this:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python3.0/python3.0-minimal_3.0.1-0ubuntu13_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python3.0/python3.0-minimal_3.0.1-0ubuntu13_i386.deb)
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  ) [IP: 172.22.0.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python3.0/python3.0_3.0.1-0ubuntu13_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/python3.0/python3.0_3.0.1-0ubuntu13_i386.deb)
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  ) [IP: 172.22.0.14 80]

But I am writing this question right now while on the internet. Could someone provide some ideas? Thank you!

---

### Post by coutts99 on 2009-04-29
In the file /etc/apt/apt.conf, add the following -:

```
Acquire::http::Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT"
```

Drop the MYDOMAIN is you aint on Active Directory.

Give that whirl :)

---

### Post by jlillywh on 2009-04-30
Thank you!

I tested this by trying to do:
sudo apt-get install pptp-linux network-manager-pptp

I went to /etc/apt/apt.conf
and added
Acquire::http::proxy "http://us.archive.ubuntu.com";
to the file.

Here is the error I get doing apt get:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main pptp-linux 1.7.2-1
  Could not connect to us.archive.ubuntu.com:80 (91.189.92.45). - connect (111 Connection refused) [IP: 91.189.92.45 80]

Any ideas why I'm still not able to connect?

---

### Post by coutts99 on 2009-04-30
You need to put your proxy details in there!

E.g.

Acquire::http::Proxy "http://domain\user:password@cache.domain.com:3128"

---

### Post by zeex on 2009-04-30
> **jlillywh said:**
> Thank you!

I tested this by trying to do:
sudo apt-get install pptp-linux network-manager-pptp

I went to /etc/apt/apt.conf
and added
Acquire::http::proxy "http://us.archive.ubuntu.com";
to the file.

Here is the error I get doing apt get:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main pptp-linux 1.7.2-1
  Could not connect to us.archive.ubuntu.com:80 (91.189.92.45). - connect (111 Connection refused) [IP: 91.189.92.45 80]

Any ideas why I'm still not able to connect?

Hi, 

It looks like you want to connect to [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) . In the file /etc/apt/apt.conf you need to add something like this 
```

Acquire {
HTTP {
Proxy "http://proxy:port";
};
};

```

Where::

proxy :: is your proxy server , usually campus or corporate proxy server.
port :: is the port. is usually 80 or 8080

for example say proxy server is "campus.proxy" and port is 80 then you would enter
```

Acquire {
HTTP {
Proxy "http://campus.proxy:80";
};
};

```

And if your proxy server requires any authentication then add the line below 
```

Acquire {
HTTP {
Proxy "http://username:password@campus.proxy:80";
};
};

```

Replace the username and password with your account username and password. (This is discouraged in shared machines) 

Do not enter the site you want to connect. make sure you know your proxy server and settings.

---

### Post by jlillywh on 2009-04-30
Sorry I pasted the wrong thing. I meant to say I did this:

Acquire::https::proxy "https://domain_name\username:password@proxy.ch2m.com:80/";

but still get that error I noted. I also added this:

Acquire::http::proxy "http://domain_name\username:password@proxy.ch2m.com:80/";

I also tried with port called 80 instead of 80/. Would there be any other configuration required?

error: 

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main pptp-linux 1.7.2-1
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  ) [IP: 172.22.0.14 80]

---

### Post by coutts99 on 2009-04-30
> The ISA Server requires authorization to fulfill the request

Have you replaced the username and password bits with your username and password?

---

### Post by jlillywh on 2009-04-30
yes.

all the parameters should be correct. I guess I'll go back and double check the domain name.. just to be sure.

---

### Post by jlillywh on 2009-05-08
I have added the following to the apt.conf file:

Acquire::http::proxy "http://proxy.alpha.com:80/";
Acquire::ftp::proxy "ftp://proxy.alpha.com:80/";
Acquire::https::proxy "https://proxy.alpha.com:80/";

Acquire::http::proxy "http://alpha\jason:Secret5@proxy.alpha.com:80/";

Where the proxy name is proxy.alpha.com
domain name is alpha
username and passwords are correct.

I still get things like:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  ) [IP: 172.22.0.13 80]

when doing sudo apt-get update

I also tried changing proxy settings System->Preferences->Network Proxy and applied system-wide. Still have this problem.

Is there any other solution?

---

### Post by vineeth_vijay on 2009-09-17
Try

export http_proxy=http://username: password@proxy_address: proxy_port

You will be then able to do sudo apt-get succesfully..

---

### Post by jlillywh on 2009-11-12
I tried that:

export http_proxy="http://alpha\jason:Secret5@proxy.alpha.com:80/";

and still got the same error:

407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  ) [IP: 172.22.0.16 80]

---

### Post by udippel on 2010-05-18
> **jlillywh said:**
> I tried that:

407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  ) [IP: 172.22.0.16 80]

True. Sure. S***.
Blame *buntu or *soft. 

Here is the background, not necessarily the solution: All those *nix authentication methods out of the box (like the one proposed to you, and tried properly by you) only do basic authentication mechanism schemes. NTLMv2 isn't covered. Over. 
This is why you (if you are still waiting for a solution?) needed to install and configure cntlm. From thence onwards, you might need to use aptitude instead of apt-get, because of the latter's lousy proxy support. Meaning, together with cntlm:
sudo aptitude -o Acquire::http::Proxy=http://127.0.0.1:3128 update
and so forth. That will get you through the 'advanced' (==patronising) web filter of your organisation/provider.

HTH, late.

Uwe

---

