---
title: "unable to run update manager through proxy"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by madhavhmk on 2009-07-30
:confused:

 
I am trying to run apt get update from my institution, connected to internet via proxy.
I have set the proxy settings for firefox browser and so internet is working fine.

But while I am trying to run apt-get from terminal, system is not able to access internet....!!!!!

I have already tried the following:

I sourced the proxyrc file, entered new proxy address and set password.

even after this, the sytem seems to connect to a different server..!!!

So I am unable to update my packages.....Anyone please help me...

Thanks

---

### Post by keplerspeed on 2009-07-30
add the proxy details in synaptic, in settings>preferences>network.

Then update via system>administration>update manager.

---

### Post by madhavhmk on 2009-07-30
I tried that....But still it is not working..!!!


Here is the problem....even if I set up the proxy there,
when the command is running, it seems to be trying to connect to another one....

eg: I have set up proxy at RRI proxy1
but while update is running in command prompt,
it is showing 'connecting to vit.@proxy1'  I dont know what vit. is..!!!

---

### Post by jamest09 on 2009-07-30
```
export http_proxy="http://server:port"

aptitude update
```

Or put the following in /etc/apt/apt.conf

```
Acquire::http::Proxy "http://server:port/";
```

---

### Post by pbateman on 2009-07-30
> **keplerspeed said:**
> add the proxy details in synaptic, in settings>preferences>network.

Then update via system>administration>update manager.

Thanks for this post, I was having the same issue and this fixed it!

---

