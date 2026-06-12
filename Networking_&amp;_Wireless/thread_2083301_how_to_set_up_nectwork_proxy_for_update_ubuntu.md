---
title: "how to set up nectwork proxy for update ubuntu"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by psudheera on 2012-11-12
hi friends, I have this problem that I can't set up my university proxy settings to update ubuntu. I can access internet through it. I set the proxy setting under the network but still update fails. Can anyone help me. thanks.

I'm getting this error : 

```
W:Failed to fetch http://ppa.launchpad.net/cscarney/unity-web-place/ubuntu/dists/quantal/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/cscarney/unity-web-place/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/cscarney/unity-web-place/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Abhinav Kumar on 2012-11-12
> **psudheera said:**
> hi friends, I have this problem that I can't set up my university proxy settings to update ubuntu. I can access internet through it. I set the proxy setting under the network but still update fails. Can anyone help me. thanks.
Hi psudheera
First enter your proxy settings in network proxy configuration and then choosing Manual Proxy Configuration. Click apply system wide and enter your root password

Now type in terminal
```
sudo gedit /etc/apt/apt.conf
```

edit this file by as 
Acquire  http:: proxy "http://username: password@ur_PROXY"
Acquire  http:: proxy "ftp://username: password@ur_PROXY"
Acquire  https:: proxy "https://username: password@ur_PROXY"
save this file and now check if you are able to update or not  .

:)
Regards,
Abhinav

---

### Post by psudheera on 2012-11-12
> **Abhinav Kumar said:**
> Hi psudheera
First enter your proxy settings in network proxy configuration and then choosing Manual Proxy Configuration. Click apply system wide and enter your root password

Now type in terminal
```
sudo gedit /etc/apt/apt.conf
```edit this file by as 
Acquire  http:: proxy "http://username: password@ur_PROXY"
Acquire  http:: proxy "ftp://username: password@ur_PROXY"
Acquire  https:: proxy "https://username: password@ur_PROXY"
save this file and now check if you are able to update or not  .

:)
Regards,
Abhinav

thanks. but my apt.conf file already has these lines, 

```
Acquire::http::proxy "http://cache.mrt.ac.lk:3128/";
Acquire::https::proxy "https://cache.mrt.ac.lk:3128/";
Acquire::ftp::proxy "ftp://cache.mrt.ac.lk:3128/";
Acquire::socks::proxy "socks://cache.mrt.ac.lk:3128/";
```what should I do.? sorry I'm new to all  this. :)

---

### Post by Abhinav Kumar on 2012-11-12
> **psudheera said:**
> thanks. but my apt.conf file already has these lines, 

```
Acquire::http::proxy "http://cache.mrt.ac.lk:3128/";
Acquire::https::proxy "https://cache.mrt.ac.lk:3128/";
Acquire::ftp::proxy "ftp://cache.mrt.ac.lk:3128/";
Acquire::socks::proxy "socks://cache.mrt.ac.lk:3128/";
```what should I do.? sorry I'm new to all of this. :)
You should have a username and password to access the network through proxy.
You insert your username and password in between the lines as shown using gedit
```

Acquire::http::proxy "http://USERNAME:PASSWORD@cache.mrt.ac.lk:3128/";
Acquire::https::proxy "https://USERNAME:PASSWORD@cache.mrt.ac.lk:3128/";
Acquire::ftp::proxy "ftp://USERNAME:PASSWORD@cache.mrt.ac.lk:3128/";
Acquire::socks::proxy "socks://USERNAME:PASSWORD@cache.mrt.ac.lk:3128/";

```
here, USERNAME and PASSWORD has to be replaced by the username and password that you use to connect to the net through the proxy server.

Then, save the file and check if you are able to update your system or not.
:)

Regards,
Abhinav

---

### Post by psudheera on 2012-11-12
> **Abhinav Kumar said:**
> You should have a username and password to access the network through proxy.
You insert your username and password in between the lines as shown using gedit
```

Acquire::http::proxy "http://USERNAME:PASSWORD@cache.mrt.ac.lk:3128/";
Acquire::https::proxy "https://USERNAME:PASSWORD@cache.mrt.ac.lk:3128/";
Acquire::ftp::proxy "ftp://USERNAME:PASSWORD@cache.mrt.ac.lk:3128/";
Acquire::socks::proxy "socks://USERNAME:PASSWORD@cache.mrt.ac.lk:3128/";

```here, USERNAME and PASSWORD has to be replaced by the username and password that you use to connect to the net through the proxy server.

Then, save the file and check if you are able to update your system or not.
:)

Regards,
Abhinav


hey abhinav, the thing is we don't use a username and a password.  When accessing internet we just change the proxy settings in network and thats all. We never knew there is a Uname and a pwd, infact our university don't provide them. :-/ . And thanks for helping. (Y)

---

### Post by psudheera on 2012-11-13
Can anyone help me out..?

---

