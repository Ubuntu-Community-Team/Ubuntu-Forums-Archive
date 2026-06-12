---
title: "apt-get update and proxy"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by pmatos on 2012-04-20
Hi,

I am behind a proxy with authentication and apt-get update is acting strangely.

I have setup /etc/apt/apt.conf as:
```
$ cat /etc/apt/apt.conf
Acquire::http::proxy "http://cameurisa01:8080/";
Acquire::ftp::proxy "ftp://cameurisa01:8080/";
Acquire::https::proxy "https://cameurisa01:8080/";
Acquire::socks::proxy "socks://cameurisa01:8080/";
```

Then, I also have the env vars configured:
```
$ echo $http_proxy
http://user:pass@cameurisa01:8080
$ echo $https_proxy
http://user:pass@cameurisa01:8080
```

After adding the spotify-client rep to the sources list, running apt-get update returns me in the end:
```
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-proposed/main Translation-en
Hit http://gb.archive.ubuntu.com precise-proposed/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-proposed/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-proposed/universe Translation-en
Fetched 12.5 MB in 5s (2,488 kB/s)
W: Failed to fetch http://repository.spotify.com/dists/stable/non-free/binary-amd64/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://repository.spotify.com/dists/stable/non-free/binary-i386/Packages  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

What am I missing?

Cheers,

Paulo Matos

---

### Post by albandy on 2012-04-20
Is your proxy using NTLM auth?

---

### Post by pmatos on 2012-04-20
> **albandy said:**
> Is your proxy using NTLM auth?

Yes, I think so.

---

### Post by pmatos on 2012-04-20
> **albandy said:**
> Is your proxy using NTLM auth?

Btw, I love Lleida, have very good friend over there. :)

---

### Post by albandy on 2012-04-20
You can find usefull information here
[http://ubuntuforums.org/showthread.php?t=96802&page=2](http://ubuntuforums.org/showthread.php?t=96802&page=2)
but try this:

```

Acquire::http::Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT";

```

---

