---
title: "DNS Unable to resolve hostnames Ubuntu 10.04"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by alexis.d on 2010-05-10
Hello,

I am working behind an ISA Server proxy in a windows network. I have an Ubuntu 10.04 without have it added to windows active directory domain. 

I have configured Ubuntu network proxy, and everything works fine ..but:

I can't ping, host, nslookup & most important I can't wget (wget: unable to resolve host address) from the terminal. I have read lots of forums and I tried to resolve the issue but I failed.

Also before I had in the same network Ubuntu 9.04 (in another pc) and wget was working fine. 

Any suggestions?



****Update
I ALT+CTRL+F1 and WGET works from TTY1 ...So is it a Gnome 2.30 bug?

---

### Post by larytet on 2010-06-01
I confirm the problem.

Fresh installation of 10.04, i configured proxy in Firefox and added 
```

export http_proxy=....

```
to the /etc/bash.bashrc

Firefox and wget work fine. 
Synaptic works find after I configured HTTP proxy in the Preferences.

I do not gave apt-get, ping. I do not care about ping, but apt-get should work from the command line. 

It looks like in some cases DNS requests are not forwarded to the correct DNS server (?!)

I checked in the wireshark and, indeed, when Firefox fetches the page it does not try to resolve IP address of the server. Apt-get starts from the DSN request to the configured DNS server and gets "Unknown host".

---

### Post by larytet on 2010-06-01
Using aptitude instead of apt-get solves the problem.

```

sudo aptitude -o Acquire::http::Proxy=http://wwweuproxy.itg.ti.com:80 install hexer

```


Still, this is a bug in the apt-get. It used to work in 9.04 and 9.10

---

### Post by vikram360 on 2011-07-06
Since you're using 10.04, try this:
Go to System -> Preferences -> Network Proxy
Manual Proxy Configuaration
and type in the same configurations
Now select apply System Wide
It'll prompt for your pass.Type it in and you should be ready to go

---

