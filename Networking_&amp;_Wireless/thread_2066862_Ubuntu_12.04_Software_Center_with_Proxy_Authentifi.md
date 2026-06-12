---
title: "Ubuntu 12.04 Software Center with Proxy Authentification"
date: 2012-10-05
forum: Networking &amp; Wireless
---

### Post by kunilkuda on 2012-10-05
Hi all,

Sorry if this post is mess up, coz I'm writing this with my 7" Android phone. I've just installed Ubuntu 12.04 to my new HP DM1 4019AU and stuck without internet. 

I found the reason why Ubuntu Software Center doesn't work with auth proxy.

In the /usr/share/software-center/softwarecenter/utils.py, the proxy username and password is taken from 'org.gnome.system.proxy.http use-authentication', 'org.gnome.system.proxy.http authentication-user' and 'org.gnome.system.proxy.http authentication-password'. 

These parameters are not set by Gnome Network Proxy. To check it out, run 'gsettings list-recursively org.gnome.system.proxy' in your terminal (with standard user privilege).

I hope somebody's here know how to set up these gnome settings in terminal or network proxy. I'm pretty sure once these parameters are inserted into the gnome settings, the software center will run perfectly fine with auth proxy

---

### Post by kunilkuda on 2012-10-07
I've added these to enable Software Center and Update Manager under proxy network

Open terminal, and type this in the shell
```
$ gsettings set org.gnome.system.proxy mode 'manual'
$ gsettings set org.gnome.system.proxy.http enabled true
$ gsettings set org.gnome.system.proxy.http host 'http://mycompanyproxy.com'
$ gsettings set org.gnome.system.proxy.http port 8080
$ gsettings set org.gnome.system.proxy.http use-authentication true
$ gsettings set org.gnome.system.proxy.http authentication-user 'myusername'
$ gsettings set org.gnome.system.proxy.http authentication-password 'mypassword'

```

That will enable the Software Center and Update Manager to be able to use HTTP to retrieve package info.

Then, I've also added the proxy config into apt config, to enable the apt download and install the updates / packages.
Open terminal, and type this in the shell
```
$ sudo gedit /etc/apt/apt.conf.d/20proxy
Acquire::http::Proxy "http://myusername:mypassword@mycompanyproxy.com:8080"

```

---

