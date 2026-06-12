---
title: "Problem to Configure Network Preferences"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by j33h4d on 2010-10-06
Hey guys,

Currently, I am running Ubuntu 10.04 in my laptop. My university is using proxy to control students' activities. they use an address with port 8080. The problem is... I went to System > Preferences > Network Proxy to setup the network preferences. However, it doesn't work at all~! and i get these messages when I want to either check for updates or download any software for my ubuntu.

> The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

and

> E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory

the weird thing is, i can simply connect to the internet by using the same setting in Firefox. how to fix this?

---

### Post by surfer on 2010-10-06
the second error message has nothing to do with your proxy settings. it usually means that there is either another synaptic (or apt-get) running or that you tried to run synaptic (or apt-get) without sudo.

---

### Post by j33h4d on 2010-10-06
> **surfer said:**
> the second error message has nothing to do with your proxy settings. it usually means that there is either another synaptic (or apt-get) running or that you tried to run synaptic (or apt-get) without sudo.

hmmm... so, how to fix that? usually, it'll automatically ask for password but yeah~ it doesn't ask for it this time~! :(

---

### Post by surfer on 2010-10-06
for the proxy issue you could try:

create a file [FONT="Courier New"]/etc/apt/apt.conf.d/01proxy
[/FONT] with the following content:
```

Acquire::http::Proxy "http://<IP address or hostname of the apt-cacher server>:8080";

```

---

### Post by surfer on 2010-10-06
> **j33h4d said:**
> hmmm... so, how to fix that? usually, it'll automatically ask for password but yeah~ it doesn't ask for it this time~! :(

```

sudo apt-get update

```

---

### Post by j33h4d on 2010-10-06
> **surfer said:**
> for the proxy issue you could try:

create a file [FONT=Courier New]/etc/apt/apt.conf.d/01proxy
[/FONT] with the following content:
```

Acquire::http::Proxy "http://<IP address or hostname of the apt-cacher server>:8080";

```

surfer, it seems like your tips is working quite well. ;) I'm able to check for updates through udpdate manager. However, these came out when i wanted to install those updates.

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4.3_i386.deb)
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-24-generic_2.6.32-24.43_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-24-generic_2.6.32-24.43_i386.deb)
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu8.1_i386.deb)
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.5-4ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.5-4ubuntu0.1_i386.deb)
  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

how can i fix this?

---

### Post by surfer on 2010-10-06
your proxy seems to need authentication (username & password). you can supply it to the Acquire::http::Proxy line like this:

```
Acquire::http::Proxy http://username:password@proxyserver.net:port/
```

---

### Post by timur_ba on 2011-01-04
> **surfer said:**
> your proxy seems to need authentication (username & password). you can supply it to the Acquire::http::Proxy line like this:

```
Acquire::http::Proxy http://username:password@proxyserver.net:port/
```

Even with this, I cannot get apt-get or Synaptic to work. It is Forefront TMG proxy with username authentication.

---

### Post by timur_ba on 2011-01-27
Solution found is to use [http://sourceforge.net/projects/cntlm/files/cntlm/](http://sourceforge.net/projects/cntlm/files/cntlm/) although it's not easy nor flexible.
This should be solved in Ubuntu' proxy configuration. Now, only Firefox seems to work with TMG, while system proxy and Synaptic don't.

---

### Post by timur_ba on 2011-05-06
The same problem is also here - an old habit of opening a new thread instead of proper search: 
[http://ubuntuforums.org/showthread.php?t=1020784](http://ubuntuforums.org/showthread.php?t=1020784)
[http://ubuntuforums.org/showthread.php?t=964746](http://ubuntuforums.org/showthread.php?t=964746)
[http://ubuntuforums.org/showthread.php?t=1285745](http://ubuntuforums.org/showthread.php?t=1285745)
[http://ubuntuforums.org/showthread.php?t=1396749](http://ubuntuforums.org/showthread.php?t=1396749)

I opened a bug for this:
[https://bugs.launchpad.net/ubuntu/+bug/724849](https://bugs.launchpad.net/ubuntu/+bug/724849)

---

### Post by DnlCY on 2011-06-28
I had a similar problem, but I could solved it.

If we are behind a proxy, we have to configure apt-get to use it [/etc/apt/apt.config].

After configure our proxy we get the error: 
407 Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied. )
So I installed cntlm at my machine.

But _I didn't use .deb installer, because it doesn't work in ubuntu_, instead I used the tar installer, as described in here:
[http://iitmlug.a.wiki-site.com/index.php/Cntlm?#Ubuntu_Install](http://iitmlug.a.wiki-site.com/index.php/Cntlm?#Ubuntu_Install)

At cntlm config file [/etc/cntlm.config] I set my proxy configurations and set to listen 8100 port

So my apt.config will be set as:
Acquire::http::Proxy [http://localhost:8100/](http://localhost:8100/)

And voila, it's working :)

Similiar configurations of other applications using cntlm.

---

