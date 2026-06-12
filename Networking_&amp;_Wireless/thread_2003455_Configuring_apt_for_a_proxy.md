---
title: "Configuring apt for a proxy"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by yeehi on 2012-06-14
I am connecting to the Internet through a proxy. Currently, I am unable to download updates from the repositories. I believe I have to configure apt for the proxy.

I have entered a command very similar to the following, and received no errors:

```
export http_proxy=http://thisismyusername:thisismypasasword@123.456.7.8:1234
```

Do I need to change this command in some way? For example, do I have to substitute "http_proxy=" with data?

I have tried changing the mirrors I use in the software sources. I get the same problem.

I have tried editing /etc/bash.bashrc and adding the following two lines:

> export http_proxy=http://thisismyusername:thisismypasasword@123.456.7.8:1234
export ftp_proxy=http://thisismyusername:thisismypasasword@123.456.7.8:1234

That hasn't helped either.

What about this command:

> Acquire::http::Proxy "http://proxy.Idon'tknowit.com:8080";

How do I find out what url to put in that line? I know the IP address of the proxy, but not the http url...

What do I need to do?


I tried something close to the following:

Acquire::http::Proxy "http://123.456.7.8:8080";

The output was command not found.


I tried launching Synaptic, going into settings, Network, Manual Proxy settings and put in the correct details there. Then I put in the username and password in authentication. I was sure this would work! I tried it. It failed to connect.


I tried solve this problem by editing apt.conf with the following lines:

> Acquire {
Retries "0";
HTTP {
Proxy "http://123.456.7.8:8080";
};
};


It didn't work.

Neither did editing it with these lines:

> 
Acquire::http::Proxy "http://myusernamehere:mypasswordhere@123.456.7.8:8080";
Acquire::ftp::Proxy "http://myusernamehere:mypasswordhere@123.456.7.8:8080";

I have spent ages trying to sort this out. I have looked at every tutorial on the internet I could find. I have tried the Apt manual page. I am just stuck!

Somebody please help :)

---

